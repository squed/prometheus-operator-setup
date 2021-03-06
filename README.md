<p align="center">Prometheus Operator Setup</p>


### Tools validation
- Decrypting files
```bash
git-crypt unlock getup.pem
```
- Kubectl setup
```bash
export  KUBECONFIG=$KUBECONFIG:kubeconfig.yaml
```
- Grafana dashboard:
```bash
kubectl -n monitoring port-forward deployment/getup-grafana 3000:3000
```
- Alertmanager panel:
```bash
kubectl -n monitoring port-forward alertmanager-getup-prometheus-operator-alertmanager-0 9093:9093
```
- Prometheus operator panel:
```bash
kubectl -n monitoring port-forward prometheus-getup-prometheus-operator-prometheus-0 9090:9090
```

### About

#### Requirements

- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) (^v1.14.0)
- [git-crypt](https://github.com/AGWA/git-crypt/blob/master/INSTALL.md) (^0.6.0)
- [Terraform](https://www.terraform.io/downloads.html) (^v0.11.13)

#### References
- [Prometheus Operator](https://github.com/coreos/prometheus-operator/tree/v0.29.0)
- [Prometheus Operator - User guides](https://github.com/coreos/prometheus-operator/tree/v0.29.0/Documentation/user-guides)
- [Kubernetes monitoring with Prometheus – Prometheus operator tutorial (part 3)](https://sysdig.com/blog/kubernetes-monitoring-prometheus-operator-part3/)
- [cAdvisor](https://github.com/google/cadvisor)
- [Node exporter](https://github.com/prometheus/node_exporter)
- [Kube State Metrics](https://github.com/kubernetes/kube-state-metrics)
- [Prometheus Operator - Helm Chart](https://github.com/helm/charts/tree/master/stable/prometheus-operator)


#### Files to review
```bash
prometheus-operator-setup/
├── backend
│   ├── firewall
│   │   ├── main.tf
│   │   └── variables.tf
│   ├── subnet
│   │   ├── main.tf
│   │   ├── outputs.tf
│   │   └── variables.tf
│   └── vpc
│       ├── main.tf
│       └── outputs.tf
├── credentials
│   └── getup.json
├── gke
│   ├── main.tf
│   ├── outputs.tf
│   └── variables.tf
├── helm
│   ├── alertmanager.values.yaml
│   ├── main.tf
│   └── prometheus-operator.tf
├── kubeconfig.yaml
├── kubernetes
│   ├── cluster-role-bindings.tf
│   ├── namespaces.tf
│   ├── outputs.tf
│   └── service-accounts.tf
├── LICENSE
├── main.tf
├── README.md
├── terraform.tfstate
├── terraform.tfstate.backup
└── variables.tf
```

#### Submitting bugs and feature requests

Bugs and feature request are tracked on [GitHub](https://github.com/hermeto/prometheus-operator-setup/issues)

### Author

Hermeto Romano - <hermeto.romano@gmail.com>
