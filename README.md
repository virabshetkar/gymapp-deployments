# Gym Application Deployment

## Requirements

1. Minikube / Docker Desktop with Kubernetes enabled

## How to deploy

### 1. Deploy the Ingress Nginx Controller

The documentation for deploying the Ingress Nginx Controller can be found [here](https://kubernetes.github.io/ingress-nginx/deploy/).

For minikube enter the following command:

```cmd
minikube addons enable ingress
```

For Docker Desktop enter the following command:

```cmd
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.12.2/deploy/static/provider/cloud/deploy.yaml
```

### 2. Apply the databases

Following command creates the Deployments and ClusterIPs for the databases:

```cmd
kubectl apply -f dbs/
```

### 3. Apply the deployments

Following command creates the Deployments and ClusterIPs for the microservices in the GymApplication:

```cmd
kubectl apply -f depl/
```

### 4. Apply the ingress services

Following command creates the service responsible for redirecting HTTP requests to the correct microservices:

```cmd
kubectl apply -f srv/
```