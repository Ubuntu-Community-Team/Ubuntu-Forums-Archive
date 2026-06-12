---
title: "KVM/Qemu- How to get images onto Virtual Host/ LVM pool question"
date: 2015-08-07
forum: Virtualisation
---

### Post by Anthony_Kay on 2015-08-07
Hi Guys,

Recently setup KVM and LVM on my PC (Running Ubuntu 14.04 in software Raid1) and LVM installation seems to have went OK. 

Installed KVM and then on an Ubuntu Desktop I have installed libvirt so I connect to my host machine and went to create a new machine.

1. First question is what Logical Volumes/ Volume Groups do I need to create in order to have multiple OS running on my server? (Ideally Windows 7, Ubuntu Server and Windows Server)

I have 2 HDD running in Raid1 with one PV and one LV 

2. Second question is how do I get the images from my local Ubuntu desktop machine onto the Ubuntu Server machine?

Any help appreciated! New to virtualisation and can't seem to find the questions for my above scenarios :(

Thanks guys

---

### Post by TheFu on 2015-08-08
You do not **need** LVM at all.  Storage choices are separate from VM choices.  However, there are reasons to have an LV assigned to an OS. OTOH, that is completely up to you and your needs.  Many organizations do fine without using LVM at all (as far as the VMs are concerned).  Under some situations, NFS storage is actually faster than local storage.  There is lots of reading about this at the "libvirt storage" page. [https://libvirt.org/storage.html](https://libvirt.org/storage.html)  Some of  the more advanced storage options are NOT available through the GUI yet.  For a small set of VMs, manually creating qcow2 storage for a VM is probably best. There are some advanced storage features provided with qcow2, without the hassles.

How to get ISO files to the server?  scp, sftp, cifs, nfs, whatever you would do to transfer files. Nothing is "built-in" - use normal network transfer methods.  In the "Storage" tab of the VM-host you may want to add other network storage locations for ISO files. Be certain to "Refresh" if any files are added and you don't want to restart libvirt.

---

### Post by Anthony_Kay on 2015-08-17
Thanks! thats great :)

---

