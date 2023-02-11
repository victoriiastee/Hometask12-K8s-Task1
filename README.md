# Hometask12-K8s-Task1

## Execution: 

### 1. Get information about worker node and save it in file: 

`kubectl describe nodes kubernode` >>> [worker_description.txt file](worker_description.txt)  

### 2. Create a new namespace: 

```
kubectl create ns my-ns
``` 

![image](https://user-images.githubusercontent.com/102364456/218265779-652047fb-3f49-4f29-9784-0f67afb9af29.jpg) 

![image](https://user-images.githubusercontent.com/102364456/218265801-09efebd4-62a1-4080-84b0-f4a5dfea03db.jpg)
### 3. Create [deployment.yaml](deployment.yaml) file with 3 pods of Apache and service for access to these pods via ClusterIP and NodePort: 
```
kubectl apply -f deployment.yaml -n my-ns
``` 
![image](https://user-images.githubusercontent.com/102364456/218265973-85c9cfd0-76e6-444e-a568-e6a160e6700f.jpg) 

Get a list of deployments: 
```
kubectl get deployment -n my-ns
```
![image](https://user-images.githubusercontent.com/102364456/218266004-753cdde2-a70e-47f8-abdf-301e4496d437.jpg) 

Get a list of pods: 
```
kubectl get pods -n my-ns
``` 
![image](https://user-images.githubusercontent.com/102364456/218266031-ae11523f-3f3f-4d7a-b635-b57e0e081e26.jpg) 

Get a list of services:
```
kubectl get services -n my-ns
``` 
 
![image](https://user-images.githubusercontent.com/102364456/218266051-fbaecbc1-7e68-4c41-a8c1-bf41bb2698fe.jpg) 

Get a description of the deployment: 
```
kubectl describe deploy my-web-apache -n my-ns
``` 
![image](https://user-images.githubusercontent.com/102364456/218266070-4898cc43-b915-491d-99f1-6947238d68e4.jpg) 

Get a description of the service:
```
kubectl describe service nodeport -n my-ns
```
![image](https://user-images.githubusercontent.com/102364456/218266125-ae6bf908-460e-463b-9ad6-d5370688ac87.jpg)
```
kubectl describe service clusterip -n my-ns
```
![image](https://user-images.githubusercontent.com/102364456/218266162-04de2ff5-c87e-429b-bb5c-1cfab921d163.jpg) 

 Get a log of one pod: 
 ```
 kubectl logs my-web-apache-6b87997db9-jgv6d -n my-ns
 ``` 
![image](https://user-images.githubusercontent.com/102364456/218266186-de7ad7d9-f40c-442c-967d-85b3b7fe8452.jpg) 

 

### 4. Create two jobs with ***yaml*** files:
Run [clusterip-job.yaml](clusterip-job.yaml) file: 
```
kubectl apply -f clusterip-job.yaml -n my-ns
```
![image](https://user-images.githubusercontent.com/102364456/218266207-80d916f0-45dd-41cf-928a-52368a204ff6.jpg) 

Get a log of the job: 
```
kubectl logs job.batch/cluster-ip -n my-ns
``` 
![image](https://user-images.githubusercontent.com/102364456/218266239-6d95a5e1-d887-4c5f-83c1-1b045a21d0a5.jpg) 

Get a description of the job:
```
kubectl describe job cluster-ip -n my-ns
```
![image](https://user-images.githubusercontent.com/102364456/218266272-ff081311-9eaa-4f4f-a9b6-b344dd67fcf6.jpg) 

Run [node-port.yaml](nodeport-job.yaml) file: 
```
kubectl apply node-port.yaml -n my-ns
``` 

Get a log of the job: 
```
kubectl logs job.batch/node-port -n my-ns
```
![image](https://user-images.githubusercontent.com/102364456/218266301-87ae03ab-ed97-41eb-8348-ab8e0cde9a10.jpg) \

 Get a description of the job: 
 ```
 kubectl describe job node-port -n my-ns
 ```
![image](https://user-images.githubusercontent.com/102364456/218266345-94cdc2fd-128e-4cef-9f94-0a3c672c3dea.jpg) 

### 5. Create Cronjob.yaml file which will test the connection to Apache service every 3 minutes:
Run [cronjob.yaml](cronjob.yaml) file: 
```
kubectl apply -f cronjob.yaml -n my-ns
``` 
 Get a list of cronjob: 
 ```
 kubectl get CronJob -n k8s
 ``` 
![image](https://user-images.githubusercontent.com/102364456/218266386-8b7231c7-54a1-48af-af49-6802fa33a25c.jpg) 

 Get a list of job created by cronjob: 
 ```
 kubectl get job -n my-ns
 ```
![image](https://user-images.githubusercontent.com/102364456/218266409-84039a42-b576-4489-bcb2-690a30674fd2.jpg) 

 Get pods: 
 ```
 kubectl get pods -n my-ns
 ``` 
![image](https://user-images.githubusercontent.com/102364456/218266428-f95eee77-6057-4680-b9b7-5f764ca7239b.jpg) 

Get a description of the cronjob: 
```
kubectl describe cj cronjob -n my-ns
``` 
![image](https://user-images.githubusercontent.com/102364456/218266443-330f897f-80d4-412a-bf3f-a4b84a190ca0.jpg) 
### Thank You!

