---
title: "Getting Xen to run on Ubuntu Server 16.04.1"
date: 2016-11-22
forum: Virtualisation
---

### Post by arewm on 2016-11-22
[FONT=arial]I am sorry if this has been discussed before. I found some similar posts but nothing that really relates to my issue.

I am trying to install Ubuntu Server on a new machine to host VMs. I have no problem installing Ubuntu or creating VMs using KVM.

My problems have arisen, however, when I try and install Xen so that I can access those machines from the network. I have reinstalled Ubuntu and Xen multiple times to make sure that I wasn't doing something silly in the setup.

```
sudo apt-get install xen-hypervisor-amd64
sudo reboot
```

I have disabled secure boot and enabled the legacy options so that my computer tries to boot into Xen, but it just hangs when trying to load the initial ramdisk...

[/FONT][FONT=arial]```
Loading Xen 4.6-amd64 ...
WARNING: no console will be available to the OS
Loading Linux 4.4.0-47-generic ...
Loading initial ramdisk ...
```[/FONT][FONT=arial]

The computer is a new Dell Precision 7810.

Any help would be appreciated![/FONT]

---

