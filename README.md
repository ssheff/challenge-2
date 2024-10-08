

0. Push the docker container to a Docker registry
0. 1. 
docker tag python-webserver-secure:latest sshevchenko/challenge-1:latest

0. 2. 
docker push sshevchenko/challenge-1:latest

0. 5. 
minikube image load sshevchenko/challenge-1:latest
minikube cache reload
minikube cache list

0. 6. Start minikube
minikube start --driver=docker --force
kubectl create deployment my-app --image=sshevchenko/challenge-1:latest

0. 7. Run acontainer
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
kubectl create deployment my-app --image=sshevchenko/challenge-1:latest
kubectl expose deployment my-app --type=NodePort --port=8000
minikube service my-app --url
curl http://192.168.49.2:30662

1. Deploy EC2 instance

2. istall HELM:

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh


3. Install Minikube: (for local Kubernetes deployment)

sudo install minikube-linux-amd64 /usr/local/bin/minikube

4. Install Docker
yum install docker -y

4. 1. Optional (for better security)
	- Add your user to the docker group (to avoid using sudo for Docker commands):
sudo usermod -aG docker $USER
    - Log out and back in for the group change to take effect, or run:
newgrp docker


5. Enable and start docker service
systemctl enable docker.service
systemctl start docker.service

6. Start Minikube with the Docker driver:
minikube start --driver=docker --force

7. Install NGINX Ingress Controller on Kubernetes
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update

# Install NGINX Ingress
# Once the Kubernetes cluster is ready need to install the NGINX Ingress controller. NGINX will handle routing external traffic to the application.
helm install nginx-ingress ingress-nginx/ingress-nginx \
  --set controller.publishService.enabled=true

8. Creating Helm Chart
helm create my-k8s-app
cd my-k8s-app

9. Deploy the Application Using Helm
# Now that Helm chart is ready, we can go ahead and deploy the application to the Kubernetes cluster using Helm.

9. 1.	Install the application:
cd ../.. 
helm install my-k8s-app ./my-k8s-app


