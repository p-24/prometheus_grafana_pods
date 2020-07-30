# Prometheus_grafana_pods
> Kubernetes Cluster to monitor internet urls and provide Prometheus metrics via Grafana

This Project is extension from https://github.com/p-24/prometheus_api_metrics


## Getting started

Clone this repository to build and deploy this application

```
    git clone https://github.com/p-24/prometheus_grafana_pods.git
    cd prometheus_grafana_pods
```
## Contents of prometheus_api_metrics

1. docs - Reference Images
2. k8s/config-map.yml - Create a Prometheus config map with all the scrape config and alerting rules
3. k8s/deployment.yml - Deployment file used to create Python-flask-app deployment
4. k8s/grafana-claim-persistentvolumeclaim.yml -
5. k8s/grafana-deployment.yml -
6. k8s/grafana-service.yml -
7. k8s/ingress-service.yml - Traffic routing is controlled by rules defined in this Ingress resource. (prometheus.local, grafana.local URLs created)
8. k8s/prometheus-server.yml - In this configuration, we are mounting the Prometheus config map as file inside /etc/prometheus and also exposing Prometheus dashboard as Kubernetes service
9. k8s/service.yml - Service file used to create Kubernetes deployment. Here NodePort.


### Building And Deploying

## Create Deployment and Service for both Prometheus and Grafana.
   ```kubectl apply -f k8s/deployment.yml
      kubectl apply -f k8s/service.yml
      kubectl apply -f k8s/ingress-service.yml
      kubectl apply -f k8s/config-map.yml
      kubectl apply -f k8s/prometheus-server.yml
      kubectl apply -f k8s/grafana-claim-persistentvolumeclaim.yml
      kubectl apply -f k8s/grafana-deployment.yml
      kubectl apply -f k8s/grafana-service.yml
   ```

Verify pods, services created for that respective deployment.
<img width="1023" alt="svc_ingress_pods" src="https://user-images.githubusercontent.com/11732564/88911511-cb489f80-d212-11ea-807e-a3c73957c2c2.png">


## Verify the url for custom metrics
  ```
  http://<HOST IP>:30000/metrics
  ```

##Verify the url for prometheus dashboard
 ```
   http://prometheus.local
  ```   
##Verify the url for grafana dashboard
  ```
  http://grafana.local
  ```


### Metrics view From
# Prometheus  
<img width="1637" alt="Prometheus_pod" src="https://user-images.githubusercontent.com/11732564/88911495-c84daf00-d212-11ea-8c10-218ac3738127.png">

# Grafana
<img width="1634" alt="Grafana_pod" src="https://user-images.githubusercontent.com/11732564/88911504-c97edc00-d212-11ea-9dc3-4e7d6f32ae09.png">
