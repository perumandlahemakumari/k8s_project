# k8s_project

### 🚀 Refer to the repository docker-project for steps to build and push the image to Docker Hub. After that, follow the steps below.

# 🚀 Kubernetes & ArgoCD Setup Guide with Helm 🎯

## 🔧 Installation Steps

```bash
1. sudo su -
2. curl -LO "https://dl.k8s.io/release/$(curl -L -shttps://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
3. wget https://github.com/kubernetes/kops/releases/download/v1.24.1/kops-linux-amd64
4. chmod +x kops-linux-amd64 kubectl
5. mv kubectl /usr/local/bin/kubectl
6. mv kops-linux-amd64 /usr/local/bin/kops
7. sudo curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
8. sudo curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
9. sudo echo "$(cat kubectl.sha256) kubectl" | sha256sum --check
10. sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
11. kubectl version
12. kops version
13. export KOPS_STATE_STORE=s3://hema.kops.v1
14. kops create cluster --name hema.k8s.local --zones ap-south-1a --control-plane-size t2.large --node-size t2.medium
15. kops update cluster --name hema.k8s.local --yes --admin
16. kubectl get nodes
17. curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
18. chmod 700 get_helm.sh
19. ./get_helm.sh
20. helm version
21. helm repo add twomartens https://repo.2martens.de/charts
22. helm install my-argocd twomartens/argocd --version 0.1.1
23. helm repo update
24. kubectl create namespace argocd
```

## 🌐 Access ArgoCD with LoadBalancer DNS

### 🔹 In ArgoCD UI:
- **Click on Create App**  
- **App Name**: `hema`  
- **Default**: `k8s_project`  
- **Type**: `manual`  

### 📦 Source:
- Repo: `https://github.com/perumandlahemakumari/k8s_project.git`  
- Revision: `head`  
- Path: `./`  

### 🎯 Destination:
- **Cluster URL**: `http://kubernetes.default.svc`

```bash
25. kubectl get all
```

### 🔁 Sync the App
- Go to ArgoCD → App → Click on Sync → Force → Sync → Click OK

```bash
26. kubectl get all
```

### 🛠️ Update Deployment
- Change **replicas** to 2 in Git repo
- Commit changes

- In ArgoCD: App → Refresh → Sync → Force → Sync → OK

```bash
27. kubectl get po
```
