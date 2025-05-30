# convert-kubeconfig

This subcommand converts kubeconfig to [Exec plugin](../concepts/exec-plugin.md) using `kubelogin get-token` with specified [login mode](../concepts/login-modes.md).

Note that when `--context` is specified, only the matching kubeconfig context will be converted. Otherwise, every kubeconfig context that uses azure auth or Exec plugin will be converted.

## Usage

```sh
kubelogin convert-kubeconfig -h
convert kubeconfig to use exec auth module

Usage:
  kubelogin convert-kubeconfig [flags]

Flags:
      --authority-host string                Workload Identity authority host. It may be specified in AZURE_AUTHORITY_HOST environment variable
      --azure-config-dir string              Azure CLI config path
      --cache-dir string                     directory to cache authentication record (default "/home/weinongw/.kube/cache/kubelogin/")
      --client-certificate string            AAD client cert in pfx. Used in spn login. It may be specified in AAD_SERVICE_PRINCIPAL_CLIENT_CERTIFICATE or AZURE_CLIENT_CERTIFICATE_PATH environment variable
      --client-certificate-password string   Password for AAD client cert. Used in spn login. It may be specified in AAD_SERVICE_PRINCIPAL_CLIENT_CERTIFICATE_PASSWORD or AZURE_CLIENT_CERTIFICATE_PASSWORD environment variable
      --client-id string                     AAD client application ID. It may be specified in AAD_SERVICE_PRINCIPAL_CLIENT_ID or AZURE_CLIENT_ID environment variable
      --client-secret string                 AAD client application secret. Used in spn login. It may be specified in AAD_SERVICE_PRINCIPAL_CLIENT_SECRET or AZURE_CLIENT_SECRET environment variable
      --context string                       The name of the kubeconfig context to use
      --disable-environment-override         Enable or disable the use of env-variables. Default false
      --disable-instance-discovery           set to true to disable instance discovery in environments with their own simple Identity Provider (not AAD) that do not have instance metadata discovery endpoint. Default false
  -e, --environment string                   Azure environment name (default "AzurePublicCloud")
      --federated-token-file string          Workload Identity federated token file. It may be specified in AZURE_FEDERATED_TOKEN_FILE environment variable
  -h, --help                                 help for convert-kubeconfig
      --identity-resource-id string          Managed Identity resource id.
      --kubeconfig string                    Path to the kubeconfig file to use for CLI requests.
      --legacy                               set to true to get token with 'spn:' prefix in audience claim
  -l, --login string                         Login method. Supported methods: devicecode, interactive, spn, ropc, msi, azurecli, azd, workloadidentity. It may be specified in AAD_LOGIN_METHOD environment variable (default "devicecode")
      --password string                      password for ropc login flow. It may be specified in AAD_USER_PRINCIPAL_PASSWORD or AZURE_PASSWORD environment variable
      --pop-claims key=val,key2=val2         contains a comma-separated list of claims to attach to the pop token in the format key=val,key2=val2. At minimum, specify the ARM ID of the cluster as `u=ARM_ID`
      --pop-enabled                          set to true to use a PoP token for authentication or false to use a regular bearer token
      --redirect-url string                  The URL Microsoft Entra ID will redirect to with the access token. This is only used for interactive login. This is an optional parameter.
      --server-id string                     AAD server application ID
  -t, --tenant-id string                     AAD tenant ID. It may be specified in AZURE_TENANT_ID environment variable
      --timeout duration                     Timeout duration for Azure CLI token requests. It may be specified in AZURE_CLI_TIMEOUT environment variable (default 30s)
      --use-azurerm-env-vars                 Use environment variable names of Terraform Azure Provider (ARM_CLIENT_ID, ARM_CLIENT_SECRET, ARM_CLIENT_CERTIFICATE_PATH, ARM_CLIENT_CERTIFICATE_PASSWORD, ARM_TENANT_ID)
      --username string                      user name for ropc login flow. It may be specified in AAD_USER_PRINCIPAL_NAME or AZURE_USERNAME environment variable

Global Flags:
      --logtostderr   log to standard error instead of files (default true)
  -v, --v Level       number for the log level verbosity
```
