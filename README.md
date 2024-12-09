# Helm Commands and Use Cases

This repository demonstrates various Helm commands and workflows for managing Kubernetes applications. Below, you'll find step-by-step examples, explanations, and tips to help you effectively use Helm for deploying, upgrading, and managing your applications.

---

## Table of Contents
1. [Introduction to Helm](#introduction-to-helm)
2. [Helm Hub Search](#helm-hub-search)
3. [Adding and Listing Helm Repositories](#adding-and-listing-helm-repositories)
4. [Searching for Charts](#searching-for-charts)
5. [Installing Charts](#installing-charts)
6. [Listing and Managing Releases](#listing-and-managing-releases)
7. [Upgrading a Release](#upgrading-a-release)
8. [Rolling Back a Release](#rolling-back-a-release)
9. [Packaging Custom Charts](#packaging-custom-charts)

---

## Introduction to Helm
[Helm](https://helm.sh/) is a package manager for Kubernetes that simplifies the deployment and management of applications. It enables you to:
- Install predefined application configurations (charts).
- Upgrade or roll back releases.
- Package your own Kubernetes manifests into reusable charts.

---

## Helm Hub Search
Search for charts on Artifact Hub:
```bash
helm search hub consul
```
Output:
```
URL                                                     CHART VERSION  APP VERSION  DESCRIPTION
https://artifacthub.io/packages/helm/warjiang/consul     1.3.0          1.17.0       Official HashiCorp Consul Chart
https://artifacthub.io/packages/helm/wener/consul        1.6.1          1.20.1       Official HashiCorp Consul Chart
```

---

## Adding and Listing Helm Repositories
Add a repository:
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```
Output:
```
"bitnami" has been added to your repositories
```

List repositories:
```bash
helm repo list
```
Output:
```
NAME        URL
bitnami     https://charts.bitnami.com/bitnami
puppet      https://puppetlabs.github.io/puppetserver-helm-chart
hashicorp   https://helm.releases.hashicorp.com
```

---

## Searching for Charts
Search within repositories:
```bash
helm search repo wordpress
```
Output:
```
NAME                    CHART VERSION   APP VERSION   DESCRIPTION
bitnami/wordpress       24.0.9          6.7.1         WordPress is the world's most popular blogging platform...
bitnami/wordpress-intel 2.1.31          6.1.1         DEPRECATED WordPress for Intel...
```

---

## Installing Charts
Install a chart from a repository:
```bash
helm install amaze-surf bitnami/apache
```
Output:
```
NAME: amaze-surf
LAST DEPLOYED: <timestamp>
STATUS: deployed
NOTES:
1. Get the Apache URL by running:
   kubectl get svc --namespace default amaze-surf-apache
```

---

## Listing and Managing Releases
List installed releases:
```bash
helm list
```
Output:
```
NAME            NAMESPACE   REVISION  STATUS    CHART           APP VERSION
amaze-surf      default     1         deployed  apache-11.2.22  2.4.62
```

Uninstall a release:
```bash
helm uninstall amaze-surf
```
Output:
```
release "amaze-surf" uninstalled
```

Remove a repository:
```bash
helm repo remove hashicorp
```
Output:
```
"hashicorp" has been removed from your repositories
```

---

## Upgrading a Release
Upgrade a deployed release:
```bash
helm upgrade dazzling-web bitnami/nginx --version 13
```
Output:
```
Release "dazzling-web" has been upgraded. Happy Helming!
```

---

## Rolling Back a Release
Rollback a release to a previous revision:
```bash
helm rollback dazzling-web
```
Output:
```
Rollback was a success! Happy Helming!
```

---

## Packaging Custom Charts
Package a custom chart:
```bash
helm package ./webapp-color/
```
Output:
```
Successfully packaged chart and saved it to: ./webapp-color-0.1.0.tgz
```

---

## Conclusion
This guide outlines essential Helm commands for managing Kubernetes applications. By leveraging these commands, you can simplify deployment workflows, ensure consistency, and make your DevOps processes more efficient.

For more information, refer to the [Helm Documentation](https://helm.sh/docs/).
