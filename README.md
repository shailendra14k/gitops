# gitops

A. Create 2 ns cicd and gitops

B. Deploy ArgoCD/Openshift-gitops on OCP

C. Add the apps-of-apps(https://github.com/shailendra14k/gitops/tree/main/apps-of-apps) project to the ArgoCD(This will perform all the deploymnet of ACS/pipeline/Sonarqube/Nexus)

-----------_##Manual task-------------------

0. For deploying ACS secure cluster.. generate the init secret bundle. 

1. oc adm policy add-cluster-role-to-user  cluster-admin -z openshift-gitops-argocd-application-controller

2. oc create sa image-puller -n openshift-config |  oc create token image-puller -n openshift-config

3. oc describe sa image-puller -n openshift-config

4. oc adm policy add-cluster-role-to-user  cluster-admin -z image-puller -n openshift-config

5. generate the token from github and update the pipeline

6. add webhook trigger to the getotp sorcecode repo.

7. Sonarqube.. 
    a. Adminstration ---> Security .. Disable Fore user 
    b. Security --> Gobal permision -- enable for anyone

8. Nexus
    a. Repository ---> maven-release --> enable redeploy


9. ACS 
    a. Disable the build for policy for Fixable Severity
    b. Generate the API token and pass this to the pipeline
    c. Add the internal registry to the ACS. 
    d. Enable log4j policy

Note the pipeline needs to be updated with 3 Token.
