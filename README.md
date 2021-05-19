# kubernetes-admin-dashboard
Pasos para crear un el dashboard de Kubernetes, un rol de administración y creación de token para acceso


Creamos el dashboard:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.2.0/aio/deploy/recommended.yaml
```

Aplicamos los yaml de creación de rol y binding del mismo:

```
kubectl apply -f dashboard-adminuser.yml
kubectl apply -f admin-role-binding.yml
```

Obtenemos el token:
```
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
```
Y con ese token accedemos al dashboard
