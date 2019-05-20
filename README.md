# Example: Terraform and Packer with Azure
Example repository using Terraform and Packer with Azure

## Packer - Automate VM Image creation

```
# Login using Azure Cli
az login

# Create resource group for packer images
az group create -n packer-images --location westeurope

# Set environment variables
tenant_id=$(az account show -o tsv --query 'tenantId')
subscription_id=$(az account show -o tsv --query 'id')

# Validate packer definition
packer validate cluster-vm.json

# Build packer image
packer build \
    -var "tenant_id=$tenant_id" \
    -var "subscription_id=$subscription_id" \
    -force \
    cluster-vm.json
```

## Terraform - Infrastructure as Code

```
az login

terraform init

terraform plan

terraform apply

terraform destroy
```