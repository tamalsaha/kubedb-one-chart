# kubedb-one-chart

## How to build

```bash
$ rm -rf kubedb-one/charts/*
$ rm -rf kubedb-one/Chart.lock

$ helm dependency build kubedb-one
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "appscode" chart repository
...Successfully got an update from the "stable" chart repository
Update Complete. ⎈Happy Helming!⎈
Saving 4 charts
Downloading kubedb from repo https://charts.appscode.com/stable
Downloading kubedb-catalog from repo https://charts.appscode.com/stable
Downloading kubedb-enterprise from repo https://charts.appscode.com/stable
Downloading kubedb-autoscaler from repo https://charts.appscode.com/stable
Deleting outdated charts

$ helm package kubedb-one/
Successfully packaged chart and saved it to: /home/tamal/go/src/github.com/tamalsaha/kubedb-one-chart/kubedb-one-v0.1.0.tgz
```

## How to install

```bash
$ kubectl version --short
Client Version: v1.17.0
Server Version: v1.20.2

$ helm install kubedb kubedb-one \
  --set kubedb.license=path_license_file.txt \
  --set kubedb-enterprise.license=path_license_file.txt \
  --set kubedb-autoscalerlicense=path_license_file.txt

W0208 12:01:38.957989 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 MutatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 MutatingWebhookConfiguration
W0208 12:01:39.113308 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 MutatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 MutatingWebhookConfiguration
W0208 12:01:39.124282 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 MutatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 MutatingWebhookConfiguration
W0208 12:01:39.288756 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 MutatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 MutatingWebhookConfiguration
W0208 12:01:39.300683 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 ValidatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 ValidatingWebhookConfiguration
W0208 12:01:39.423734 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 ValidatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 ValidatingWebhookConfiguration
W0208 12:01:39.456566 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 ValidatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 ValidatingWebhookConfiguration
W0208 12:01:39.615618 1411310 warnings.go:67] admissionregistration.k8s.io/v1beta1 ValidatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 ValidatingWebhookConfiguration

NAME: kubedb
LAST DEPLOYED: Mon Feb  8 12:01:31 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
1. Get the application pods by running the following command:

kubectl --namespace default get pods

$ helm ls
NAME  	NAMESPACE	REVISION	UPDATED                                	STATUS  	CHART            	APP VERSION
kubedb	default  	1       	2021-02-08 12:01:31.915277898 -0800 PST	deployed	kubedb-one-v0.1.0	v0.1.0     

$ kubectl get pods
NAME                                        READY   STATUS              RESTARTS   AGE
kubedb-57986bdd59-pgp2r                     0/1     ContainerCreating   0          17s
kubedb-kubedb-autoscaler-56cdc76685-489hw   0/1     ContainerCreating   0          17s
kubedb-kubedb-enterprise-c4cfb9769-tdcsf    0/1     ContainerCreating   0          17s
```
