# aws-tekton-canary-testing-deployment

This repository contains the deployment Helm chart used in the blog post Canary Testing with AWS App Mesh and Open Source Tekton.

The code provided is for demo purposes only and not ready for production.

## Getting started

Please refer to the demo section of the blog post mentioned above and follow the outlined instructions. 

In order to release a new canary version, update the values.yaml file. Please find below an updated version of this file, which contains the snippet in order to release version 2 of the backend microservice and shows how to split the traffic between the two versions equally.

```yaml
detail:
  replicaCount: 2
  namespace: apps
  name: backend-service
  serviceAccount: backend-service
  image:
    pullPolicy: Always
  service:
    type: ClusterIP
    targetPort: 3000

canaryConfig:
  - name: "backend-v1"
    tag: "v1.0.0"
    weight: 50
    ### NEW VERSION OF BACKEND SERVICE ###
  - name: "backend-v2"
    tag: "v2.0.0"
    weight: 50
    ### NEW VERSION OF BACKEND SERVICE ###
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more 
information.

## License

This code is licensed under the MIT-0 License. See the LICENSE file.