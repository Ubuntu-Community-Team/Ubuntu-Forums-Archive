---
title: "Convert VMware to QEMU"
date: 2011-08-19
forum: Virtualisation
---

### Post by mastermindg on 2011-08-19
I'm running Ubuntu 10.04 x64 with Virtual Machine Manger 0.8.2 (libvirt). I've got a Vmware instance running Windows XP SP3. I used vmwrae-vdiskmanager to convert 2GB split vmdk's to one single vmdk. I used Virtual Machine Manger to open up this new vmdk. I can boot up the drive but I get a blue screen loop.  I'm unable determine what the error is.

Any ideas?

---

### Post by mastermindg on 2011-08-19
I figured out that it only even attempts to load if acpi is enabled. Without it enabled it fails to load period.

---

### Post by mastermindg on 2011-08-19
Might virtio drivers solve the issue?

---

### Post by mastermindg on 2011-08-20
I found this article:

[http://pve.proxmox.com/wiki/Migration_of_servers_to_Proxmox_VE#Prepare_the_Windows_operating_system_2](http://pve.proxmox.com/wiki/Migration_of_servers_to_Proxmox_VE#Prepare_the_Windows_operating_system_2)

I needed to remove VMWare Tools and reset IDE. Once that was done the disk came up fine.

---

