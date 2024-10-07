## Erasme instructions

```bash 
helm repo add browsertrix https://docs.browsertrix.com/helm-repo/
helm upgrade --install btrix browsertrix/browsertrix --version 1.11.7 -f ./chart/erasme.yaml --namespace browsertrix
```

## Update Helm dependencies

* It needs to update Helm charts after changing its dependencies (e.g. logging)

```
$ helm dependency update .
```

### Update metacontroller

```
#!/bin/bash

# intall metacontroller
git clone --depth=1 https://github.com/metacontroller/metacontroller.git
cd metacontroller
helm package deploy/helm/metacontroller --destination deploy/helm
cd ..

# update dependency
helm dependency update
```

* Bump up the metacontroller version in `Chart.yaml`
