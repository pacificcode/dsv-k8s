# dsv-injector

![Version: 0.2.0](https://img.shields.io/badge/Version-0.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: latest](https://img.shields.io/badge/AppVersion-latest-informational?style=flat-square)

A Helm chart for the Delinea DevOps Secrets Vault (DSV) Injector Mutating Webhook.

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Adam Migus |  |  |
| Sheldon Hull |  |  |
| Delinea DSV Team |  |  |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| containerPort | int | `18543` | containerPort is the port that the container itself listens on |
| credentialsJson | string | `"{\n  \"default\": {\n    \"credentials\": {\n      \"clientId\": \"\",\n      \"clientSecret\": \"\"\n    },\n    \"tenant\": \"example\"\n  }\n}"` | credentialsJson contains the JSON-formatted credentials file (see README.md) @default - placeholder. *REQUIRED FIELD* |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"quay.io/delinea/dsv-k8s"` |  |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| podAnnotations | object | `{}` | podAnnotations @default - Includes `dsv-filter-name` for easier log selector filter. |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` | replicate count @default - 1 |
| resources | object | No default values, user must specify to set resource limits. | We usually recommend not to specify default resources and to leave this as a conscious choice for the user. This also increases chances charts run on environments with little resources, such as Minikube. If you do want to specify resources, uncomment the following lines, adjust them as necessary, and remove the curly braces after 'resources:'. |
| securityContext | object | `{}` |  |
| service.port | int | `8543` | Default port for the injector webhook service.  @default -- port 8543 |
| service.type | string | `"ClusterIP"` | ClusterIP is typical when the webhook is running as a POD However, it can also be hosted externally, which is useful for debugging, by providing the following instead:   type: ExternalName externalName: my.fqdn So long as: - my.fqdn hosts an HTTPS endpoint on port {webhookPort} that answers URI {webhookUri} - the certificate must have a Subject Alternative Name for {name}.{namespace}.{svc}, e.g., dsv-injector.dsv.svc - the caBundle must be a base64 string containing a PEM-encoded certificate chain that validates the certifcate caBundle: ... |
| webhookPort | int | 8543 | webhookPort is the port that the webhook endpoint is listening on |
| webhookScope | string | "Namespaced" | webhookScope specifies which resources are in scope, "Cluster", "Namespaced" or "*" |
| webhookUri | string | `"/inject"` | webhookUri is path portion of the URL of the webhook endpoint |
