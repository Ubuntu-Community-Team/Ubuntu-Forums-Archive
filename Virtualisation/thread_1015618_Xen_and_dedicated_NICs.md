---
title: "Xen and dedicated NICs"
date: 2008-12-19
forum: Virtualisation
---

### Post by djbon2112 on 2008-12-19
Well I'm back for my second help request in 3 days, fresh off getting Xen up and working, and it runs great. Now, I've run into a problem with networking.

First off, my plan was to use my two physical gigabit Ethernet interfaces as a bond, but so far the performance hasn't been that great (my switch only supports mode 5), and apparently from what I've read bonding doesn't work well with virtualization. I'd much rather have a setup where one NIC is used by the Dom0, and 2 of my 3 DomUs, and the second NIC is used exclusively by the third DomU. However, the only guide (I can't read mailing lists for the life of me) I've been able to find is [this one]("http://www.novell.com/communities/node/2880/assign-dedicated-network-card-or-pci-device-xen-virtual-machine") from Novell, but it's tailored (of course) to SuSE. Does anyone have a similar guide for Ubuntu/Debian?

---

### Post by djbon2112 on 2008-12-20
Forgive my bump, but I've been searching almost endlessly for a solution to this problem and everything is about CentOS or Red Hat or SuSE. Does anyone know how to do this (blacklist/disable/whatever the device in the Dom0, and add it manually to the DomU) with Ubuntu Server 8.04?

---

### Post by Xepra on 2008-12-22
There are two ways to do this:

1.  Use PCI pass through:
[http://wiki.xensource.com/xenwiki/Assign_hardware_to_DomU_with_PCIBack_as_module](http://wiki.xensource.com/xenwiki/Assign_hardware_to_DomU_with_PCIBack_as_module)

2.  Set up eth1 as a bridge (xenbr1) and only connect your dom3 to it:
[http://wiki.xensource.com/xenwiki/XenNetworking](http://wiki.xensource.com/xenwiki/XenNetworking)

You probably would prefer the first method, but it requires that your dom0 kernel be compiled with PCI Passthrough enabled, and your DomU to have pci frontend drivers.  Unfortunately, it doesn't look like the latest stable linux on kernel.org has pci frontend drivers.  I managed to get mine to work using the first method with the suse 2.6.27.5 kernel, but it is not being very stable (dhclient crashes it).

If I get sometime I may try to elaborate on this more, but I prob won't until after Christmas.

---

### Post by djbon2112 on 2008-12-24
> **Xepra said:**
> There are two ways to do this:

1.  Use PCI pass through:
[http://wiki.xensource.com/xenwiki/Assign_hardware_to_DomU_with_PCIBack_as_module](http://wiki.xensource.com/xenwiki/Assign_hardware_to_DomU_with_PCIBack_as_module)

2.  Set up eth1 as a bridge (xenbr1) and only connect your dom3 to it:
[http://wiki.xensource.com/xenwiki/XenNetworking](http://wiki.xensource.com/xenwiki/XenNetworking)

You probably would prefer the first method, but it requires that your dom0 kernel be compiled with PCI Passthrough enabled, and your DomU to have pci frontend drivers.  Unfortunately, it doesn't look like the latest stable linux on kernel.org has pci frontend drivers.  I managed to get mine to work using the first method with the suse 2.6.27.5 kernel, but it is not being very stable (dhclient crashes it).

If I get sometime I may try to elaborate on this more, but I prob won't until after Christmas.
Thank you for your help! I'll probably try out the second method since I'd rather stay away from compiling kernels on this machine right now. ;)

---

