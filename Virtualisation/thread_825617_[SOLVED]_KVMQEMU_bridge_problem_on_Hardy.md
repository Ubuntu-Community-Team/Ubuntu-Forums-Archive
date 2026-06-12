---
title: "[SOLVED] KVM/QEMU bridge problem on Hardy"
date: 2008-06-11
forum: Virtualisation
---

### Post by kreismeister on 2008-06-11
Hi,

I installed a fresh Hardy server yesterday for hosting some virtual machines. I followed the docs/tutorials but I'm getting an error when starting the virtual machine.

[https://help.ubuntu.com/8.04/serverguide/C/ubuntu-vm-builder.html](https://help.ubuntu.com/8.04/serverguide/C/ubuntu-vm-builder.html)
[https://help.ubuntu.com/community/KVM#head-68cb9c2386043619c68b4825b446472190d06b1e](https://help.ubuntu.com/community/KVM#head-68cb9c2386043619c68b4825b446472190d06b1e)

I've attached the complete log of ubuntu-vm-builder. Here is the error I receive:

```

user@hostmachine:/var/opt/vms$ virsh start ubuntu
Connecting to uri: qemu:///system
libvir: QEMU error : Network 'br0' not found
error: Failed to start domain ubuntu

```

Update: Yikes! That happens if you execute a tutorial late at night. ;) When editing /usr/share/ubuntu-vm-builder/templates/libvirt.tmpl make sure to set interface type to 'bridge'.

---

### Post by chaozh on 2008-06-11
Are you bridging on wireless interface or ethernet interface?
I failed bridge with my wireless interface.:KS

---

