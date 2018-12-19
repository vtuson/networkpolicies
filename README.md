# networkpolicies

kubectl run busybox --image=vtuson/busybox --restart=Never --command -- sleep 3600
kubectl run website --image=bitnami/nginx --restart=Never
kubectl create namespace test
kubectl -n test run busybox2 --image=bitnami/nginx --restart=Never


kubectl expose po website --port=80 --target-port=8080
kubectl  exec busybox -- curl website
kubectl -n test exec busybox2 -- curl website.default

k apply -f netpol-deny

kubectl label po busybox role=client
kubectl label po website role=website
