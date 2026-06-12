---
title: "virt-install won't import existing kvm vm"
date: 2009-05-26
forum: Virtualisation
---

### Post by HDave on 2009-05-26
I am trying to put an existing kvm virtual machine under the control of libvirt by way of the virt-install program in the repos.

The command I am using is:

```
virt-install --file=kvmtest.qcow2 --name virt-kvm-test1-winxp --ram=2048 --vcpus=2 --os-type=windows --os-variant=winxp
```

I got the idea of doing this from several forums on libvirt/virt-install.  However virt-install keeps complaining:

```
ERROR    One of --pxe, --location, or cdrom media must be specified.

```

But that's just the point -- I don't want pxe or cdrom, and location is only used for init ramdisks for linux guests.  Anybody have any success with this?

---

### Post by maple03 on 2009-05-27
You should specify from where to install this VM. If you want to install from os_image.iso just add to your line:
```
-c /path/to/os_image.iso
```

---

