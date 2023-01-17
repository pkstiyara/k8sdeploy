# k8sdeploy


Deployment code
apiVersion: apps/v1
kind: Deployment
metadata:
  name: cloudknowledges
spec:
  selector:
    matchLabels:
      app: cloudknowledges
  replicas: 2
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1

    template:
      metadata:
        lables:
          app: cloudknowledges

      spec:
        containers:
        - name: cloudknowledges
          image: pkstiyara.kuberentesproject
          imagePullPolicy: Always
          ports:
          - containerPort: 80
