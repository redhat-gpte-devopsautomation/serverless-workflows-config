
extendable-workflow
===========

A Helm chart for the extendable-workflow serverless workflow

The extendable-workflow workflow is a basic workflow without any external dependencies.
Its purpose is to demonstrate functionality of the workflows system.

# Helm Configuration

The following table lists the configurable parameters of the extendable-workflow chart and their default values.

| Parameter                | Description             | Default        |
| ------------------------ | ----------------------- | -------------- |
|                          |                         |                |


# Installation
## Persistence pre-requisites
If persistence is enabled, you must have a PostgreSQL instance running in the cluster, in the same `namespace` as the workflows.

A `secret` containing the instance credentials must exists as well. 

See https://www.parodos.dev/orchestrator-helm-chart/postgresql on how to install a PostgreSQL instance. Please follow the section detailing how to install using helm. In this document, a `secret` holding the credentials is created.

## Prerequisites 
Set `TARGET_NS` to the target namespace:
```console
TARGET_NS=sonataflow-infra
```
## Installing helm chart 

```console
helm repo add orchestrator-workflows https://parodos.dev/serverless-workflows-config
helm install extendable-workflow orchestrator-workflows/extendable-workflow -n ${TARGET_NS}
```

Verify the extendable-workflow workflow is ready:
```console
oc wait sonataflow extendable-workflow -n -n ${TARGET_NS} --for=condition=Running=True --timeout=5m
sonataflow.sonataflow.org/extendable-workflow condition met
```
