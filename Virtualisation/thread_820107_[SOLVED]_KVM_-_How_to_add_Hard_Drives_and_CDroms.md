---
title: "[SOLVED] KVM - How to add Hard Drives and CDroms?"
date: 2008-06-05
forum: Virtualisation
---

### Post by hopelessone on 2008-06-05
Hi all,

I managed to follow the guide at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Now i go to add a whole hard drive and it's looking for a file...

I tried to add with no luck...sniff...sniff...

the source Normal Disk Partition is greyed out...how to fix this?

Thanks for helping me... :)

---

### Post by hopelessone on 2008-06-06
In the tutorial (i'm a noob) it says..

**Install on a raw block device**

Ubuntu-vm-builder doesn't allow you to create the VM on a raw block device yet (like a standalone partition, or a iSCSI share). You can use ubuntu-vm-builder to create the qcow2 image and then move the VM to the block device with qemu-img though; if /dev/sdb is the disk device on which you want to move the virtual machine:

sudo qemu-img convert root.qcow2 -O raw /dev/sdb

Edit the XML definition file for the VM in /etc/libvirt/qemu/, and set the source file to be:

<source file='/dev/sdb'/>

Redefine the VM and start it; it is now running from /dev/sdb. [COLOR="Red"]<<-- is this meaning it's adding the /dev/sdb Hard Drive? or Booting from /dev/sdb?[/COLOR]

can someone tell me what this means?

Thanks a bunch...

---

### Post by hopelessone on 2008-06-06
works after re-install...selected use entire disk now instead of grow partition...area no longer grayed...

---

