---
title: "KVM + Windows 7"
date: 2010-09-07
forum: Server Platforms
---

### Post by michalurban on 2010-09-07
Hallo, first time poster... :)

I try to use KVM on my Ubuntu 10.04 x64 but I have a problem running (installing) Windows 7. When in virt-manager, I manage to complete the installation, but afterwards, i receive a "Interactive logon initialization process has failed" and then the system reboots - and hangs up when trying to run again.

I realized thats because there is a missing parameter which tells windows the drive is bootable ... when running kvm from the command line, its   -boot=on. But when testing the PS command, I found out virt-manager is not posting this parameter. It runs /usr/bin/kvm for me, btw ...

Unfortunately, I was unable to find this parameter in the virt-manager GUI and the VMs created in kvm are not visible for virt-manager.

So, I ask you for your help ... :)

PS: When completed installation in VM started from the shell, windows boot but hang up with virtio driver missing (viostor.sys), but thats a future story ...

---

