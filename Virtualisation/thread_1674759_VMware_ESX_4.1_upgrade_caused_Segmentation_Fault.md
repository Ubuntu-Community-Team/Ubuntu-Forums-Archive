---
title: "VMware ESX 4.1 upgrade caused Segmentation Fault"
date: 2011-01-24
forum: Virtualisation
---

### Post by SgtSavage on 2011-01-24
I have been running ubuntu 10.04 on VMWare ESXi4.0 for awhile and it has run flawlessly. This weekend i upgraded to 4.1 to gain access to a NAS device and since then I cannot boot any of my Ununtu vm's wihtout getting the Segmentatin fault error;

Segmentation Fault
Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
- check root delay ...
- check root ....
- missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/... does not exist. Dropping to a shell!

I have searched or an answer and have been unable to locate one. There are a few posts here, but no solution that I can understand (I'm a newbie to linux/ubuntu however not new to command line programming etc.). 

I have found a few posts regardin using an older kernel. Does anyone have a solution to this problem or detailed instructions as to how I can revert back to an older kernel?

Thanks

---

### Post by ishmell on 2011-02-08
I ran into this exact error with Ubuntu 10.4 on ESX 4.1 and here's what I've noticed;

- I only had issues when SAN load was high and virtual disk performance was slow

- During high SAN disk load, I was able to boot past the faults and busybox shell by disabling acceleration (Properties, Options tab, click Disable acceleration). 

Once acceleration was disabled, Ubuntu 10.4 booted normally. After the traffic on the SAN was back to normal, I re-enabled acceleration and things were fine.

From scanning other forum posts on various websites, the permanent solution may be to increase the root device detection by adding a rootdelay=90 line into the grub configuration, but I've not bothered to try it.

---

### Post by mickyg on 2011-03-30
I was having this problem too, however, enabling Paravirtualization in the VM's setting (under the 'Options' tab) did the trick for me.

I don't know if this has always been disabled or the upgrade to VMWare 4.10 disables it, which is quite likely given that the information on the properties page for this setting tells us that the next version of VMWare won't have paravirtualization and my Ubuntu VM used to work before our VMWare infrastructure was upgraded to 4.10.

I came across this after remembering that I once had to use the "noreplace-paravirt" kernel argument to get Ubuntu to boot in a VM before.

So, while this seems to get the VM booting again, the bigger problem is that the next version of VMWare won't have this option for us to re-enable and get our VM's working again!

---

### Post by oscaruc on 2011-08-23
I have the same problem after upgrading Vmware ESXi 4.0 to ESXi4.1.
I've found another work around that works for me:

In the vSphere manager, shutdown the virtual machine and edit it settings: go to the Options tab, and select "CPU/MMU Virtualization". There, change the selected option from "Automatic" (the first) to "Use Intel VT-x/AMD-V for instruction set virtualization and software for MMU virtualization" (the third). 

After that, I can boot with any 2.6.32-3x kernel.

---

