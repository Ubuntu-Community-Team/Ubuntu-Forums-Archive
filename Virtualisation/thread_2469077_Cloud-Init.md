---
title: "Cloud-Init"
date: 2021-11-18
forum: Virtualisation
---

### Post by fe80cc1e on 2021-11-18
I am using Terraform and a VMware OVA (latest imphish version Nov 4 2012). I want to set the ip as static - can I do that using the userdata.tpl? Seems to be the only option when passing forcing VMware to pass configuration data to the VM

---

### Post by Irihapeti on 2021-11-18
*Thread moved to **Virtualisation** for a better fit.*

---

### Post by MAFoElffen on 2021-11-23
Well for VMware OVA and terraform.... I thought if, in your Teraform directory you created a copy of the network configuration  file.   Name it <guest_name>-metadata.cfg. Example  being "vmstatic01-metadata.cfg" ... that that would work for cloud-inii to set it...

But if you set the static address in the terraform deployment config file directly, in that config file under the resource section, network_interface(?)  Am I wrong with that? Something like:
```

variable "vsphere_user" {}
variable "vsphere_server" {}
variable "vsphere_password" {}
variable "resource_pool" {}

variable "machine_name" {
  default = "dns"
}

variable "template_name" {
  default = "ubuntu"
}

provider "vsphere" {
  user           = "${var.vsphere_user}"
  password       = "${var.vsphere_password}"
  vsphere_server = "${var.vsphere_server}"

  allow_unverified_ssl = true
}

resource "vsphere_virtual_machine" "dns" {
  name          = "${var.machine_name}"
  vcpu          = 1
  memory        = 2048
  datacenter    = "ThisExample"
  resource_pool = "${var.resource_pool}"
  time_zone     = "US/Pacific"
  dns_servers   = ["10.0.121.21", "10.0.121.22"]

  network_interface {
    label              = "VM Network"
    ipv4_address       = "10.0.121.90"
    ipv4_prefix_length = "16"
    ipv4_gateway       = "10.0.121.1"
  }

  disk {
    template  = "${var.template_name}"
    datastore = "Datastore_"
  }
}
```
But since you mentioned userdata.tpl, that hints that maybe you areusing AWS,which for terraform, I think you are more looking for:
[https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance#network-interfaces](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance#network-interfaces)

and search on that page for "network_interface"... Where you can set that option as static from there.

---

