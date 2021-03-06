---
layout: "azurerm"
page_title: "Azure Resource Manager: azurerm_storage_queue"
sidebar_current: "docs-azurerm-resource-storage-queue"
description: |-
  Manages a Azure Storage Queue.
---

# azurerm_storage_queue

Manage an Azure Storage Queue.

## Example Usage

```hcl
resource "azurerm_resource_group" "test" {
  name     = "example-resources"
  location = "westus"
}

resource "azurerm_storage_account" "test" {
  name                     = "examplestorageacc"
  resource_group_name      = "${azurerm_resource_group.test.name}"
  location                 = "${azurerm_resource_group.test.location}"
  account_tier             = "Standard"
  account_replication_type = "LRS"
}

resource "azurerm_storage_queue" "test" {
  name                 = "mysamplequeue"
  resource_group_name  = "${azurerm_resource_group.test.name}"
  storage_account_name = "${azurerm_storage_account.test.name}"
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the storage queue. Must be unique within the storage account the queue is located.

* `resource_group_name` - (Required) The name of the resource group in which to
    create the storage queue. Changing this forces a new resource to be created.

* `storage_account_name` - (Required) Specifies the storage account in which to create the storage queue.
 Changing this forces a new resource to be created.

## Attributes Reference

The following attributes are exported in addition to the arguments listed above:

* `id` - The ID of the Storage Queue.

## Import

Storage Queue's can be imported using the `resource id`, e.g.

```shell
terraform import azurerm_storage_queue.queue1 https://example.queue.core.windows.net/queue1
```
