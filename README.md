# 🚀 Ingress Web App Deployment on Kubernetes

This project demonstrates how to deploy an Ingress web app on Kubernetes using YAML configuration files.

## Prerequisites
- Kubernetes cluster up and running.
- `kubectl` command-line tool installed and configured.

## Deploying the Ingress Web App

### Step 1: Deploy the Demo Applications
You can deploy two demo applications using the following Kubernetes deployment files:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: demo1
# ... (deployment configuration)
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: demo2
# ... (deployment configuration)
```

### Step 2: Create Services for the Deployments
Create Kubernetes services for the deployed applications:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: tea-svc
# ... (service configuration)
```

```yaml
apiVersion: v1
kind: Service
metadata:
  name: coffee-svc
# ... (service configuration)
```

### Step 3: Configure Ingress
Configure the Ingress resource to route traffic to the deployed services based on specific paths:

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: service-a
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /$1
spec:
  ingressClassName: nginx
  rules:
  - host: public.my-services.com
    http:
      paths:
      - path: /(.*)
        pathType: Prefix
        backend:
          service:
            name: tea-svc
            port:
              number: 80
      - path: /gift/(.*)
        pathType: Prefix
        backend:
          service:
            name: coffee-svc
            port:
              number: 80
```

## Deploying the Configuration
Apply the configuration files to your Kubernetes cluster using `kubectl apply -f <file>`.

Make sure to replace `<file>` with the actual file name.

## Accessing Your Ingress Web App
Once deployed and configured, you can access your Ingress web app using the specified host and paths.

Example:
- http://public.my-services.com/ (Demo1)
- http://public.my-services.com/gift/ (Demo2)

# Thank you! 👋

## 🔗 Connect with Me
- [LinkedIn](https://www.linkedin.com/in/your-linkedin-profile)
- [Twitter](https://twitter.com/your-twitter-profile)
```

Copy and paste this code into your `readme.md` file in your GitHub project, and it will display everything inside Markdown code blocks.
