# scratch

deploy any manifests via values

### Usage

example of values
```yaml
tpl:
  - apiVersion: v1
    kind: ConfigMap
    metadata:
      release-name: "{{ .Release.Name }}"

raw:
  - apiVersion: v1
    kind: Service
    metadata:
      labels:
        app: test
      name: test
    spec:
      ports:
        - port: 80
      selector:
        app: test
```

helm template
```yaml
---
# Source: scratch/templates/tpl.yaml
# .Values.tpl[0]
apiVersion: v1
kind: ConfigMap
metadata:
  release-name: 'release-name'
---
# Source: scratch/templates/raw.yaml
# .Values.raw[0]
apiVersion: v1
kind: Service
metadata:
  labels:
    app: test
  name: test
spec:
  ports:
  - port: 80
  selector:
    app: test
```
