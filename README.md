# EKS TASK
# To deploy this app on your own Cluster follow this steps.
## 1 Clone the repo on your local machine using
` $ git clone https://github.com/viveksonar/ADATASK/ `
## 2 To build your own container go to Source_code directory using 
#### (you can skip to step 7 for deploying using my own pre build image)
` $ cd Source_code `
## 3 Initialise npm and see if its working properly before containerizing your app by
` $ npm server.js `
## 4 To see the out put open new terminal and type
` $ curl http://localhost:8080 ` 
## It will return 
` Hello World ` 
## 5 Containerise the app using docker build command 
#### (please use your own docker hub username instead f $YOUR_DOCKER_USERNAME)
` $ docker build -t $YOUR_DOCKER_USERNAME/nodewebapp ` 
## 6 Push this image to Docker hub to use it in Kubernetes deployment process by
` $ docker push $YOUR_DOCKER_USERNAME/nodewebapp ` 
## Now you have your container image to use it for kubernetes deployment.
## Make sure you have created a kubernetes cluster and installed KUBECTL for the deployment 
## 7 Go to manifest files by 
` $ cd Manifest_Files `
## 8 If you have made your own image for the app make sure to change the image name in deployments.yaml
## If not use kubectl create command for creating the deployments
` $ kubect create -f deployments.yaml `
## 9 Create service for Exposing the app to the world by 
 ` $ kubect create -f service.yaml `
## After few minutes loadbalancer service would be created and you can get the EXTERNAL ip adderss by using
` $ kubect get svc `
![LOADBALANCER](/images/service.png)

## Paste this IP ADDRESS in the URL and you will be able to see the output of the app immediately

### Heres a example output
![OUTPUT](/images/output.png)
