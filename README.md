
# GitOps with ArgoCD

GitOps
practices, utilizing Argo CD for continuous deployment and Argo Rollouts for advanced
deployment strategies within a local Kubernetes environment (using kind)


## Roadmap

- Task 1: Setup and Configuration

Install Argo CD and Argo Rollouts on Your Kubernetes Cluster using helm. If you want configurations as per your use case then edit given values.yaml then apply.

```bash
  kubectl create namespace argocd, argorollout
  helm repo add argo https://argoproj.github.io/argo-helm
  helm install argocd argo/argo-cd -ns argocd
  helm install my-release argo/argo-rollouts -ns argorollout

```



- Task 2: Creating the GitOps Pipeline

    1. Dockerize the application
    2. Deploy the Application Using Argo CD:

( application.yaml :- creates ArgoCD pipeline to automatically sync modified manifest files in /dev folder to target k8s cluster. )


- Task 3: Implementing a Canary Release with Argo Rollouts
     1. Define Canary Release configuration in ArgoCD manifest file. i.e., ( application-canary.yaml :- creates ArgoCD pipeline for canary release of modified manifest files in /rollout-canary folder to target k8s cluster. Rollout requires manual promotion after 20% rollout completion.)
     2. Moniter the rollout in Argorollout UI. Rollback if rollout was not successful.



- Task 4 : Cleanup Strategy
Use background deletion with a cascading propagation policy when deleting applications.



## Challenges & Solution

- Challenge 1 : k8s manifest files with comments throws error "cannot unmarshal deployment.yaml file" when creating argoCD pipeline.
Solution: Remove all the comments in k8s manifest files.



 
