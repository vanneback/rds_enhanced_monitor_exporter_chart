# RDS enhanced monitoring exporter
A prometheus exporter for rds enhanced monitoring.

This helm chart provides an easier way to export these metrics from a kubernetes cluster
and export it into prometheus.

## TL;DR;

1. Download repo
2. `helm install -n rds-exporter --set kube2iam.role=<role arn> .`

## Links

* <https://github.com/mtanda/rds_enhanced_monitoring_exporter>

## Configuration

The following table lists the configurable parameters of the chart and their default values.

Parameter | Description | Default
--------- | ----------- | -------
`namespace` | the namespace to create the resources in | `default`
`replicas` | number of replicas to run | `1`
`region` | region of aws-rds instance | `us-east-1`
`kube2iam.enabled` | enable for kube2iam to handle credentials to aws. Mutual exclusive with env | `true`
`kube2iam.role` | arn of the aws role with access to rds | `""`
`env.enabled` | enable to authenticate with env variables. Mutual exclusive with kube2iam | `false`
`env.secretName` | name of the secret with credentials. Need to be created seperately | `aws-cred`
`image.repository` | image repository | `vanneback/ebpf-exporter`
`image.tag` | image tag | `ubuntu`
`image.pullPolicy` |  image pull policy | `IfNotPresent`
`service.type` | service type | `ClusterIP`
`service.port` | service port | `80`
`service.annotations` | service annotations | `prometheus.io/scrape: \"true\"`
`ingress.enabled` | set to true if the service should be backed by an ingress | `false`
`ingress.annotations` | ingress annotations | `{}`
`ingress.paths` | list of available paths to ingress | `[]`
`ingress.hosts` | list of hosts to ingress | `chart-example.local`
`ingress.tls` | tls config of ingress | `[]`
`resources` | resource requests of the pods in the daemonset | `{}`
`podAnnotations` | annotations of pods in daemonset | `{}`
`nodeSelector` | node selector rules | `{}`
`tolerations` | node tolerations | `[]`
`affinity` | pod affinity rules | `{}`

## Docker file
A docker file can be built from https://github.com/vanneback/rds_enhanced_monitor_exporter_dockerfile
