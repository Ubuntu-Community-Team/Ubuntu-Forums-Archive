---
title: "[KVM] Incease disk size"
date: 2009-08-05
forum: Virtualisation
---

### Post by xOrphenochx on 2009-08-05
Can't believe I'm stuck on something as elementary as this. I've become a victim of the winsxs folder on one of my servers so I need to increase the disk space and I have not been able to find any simple way of doing this. Any tips?

---

### Post by bodhi.zazen on 2009-08-07
This is not so easy to do, easiest thing would be to add a virtual disk.

Second option is to add a virtual disk and copy the first to the second , then resize the partition.

Last you can try to convert the disk :

[http://qemu-forum.ipi.fi/viewtopic.php?f=22&t=3756&start=0&st=0&sk=t&sd=a](http://qemu-forum.ipi.fi/viewtopic.php?f=22&t=3756&start=0&st=0&sk=t&sd=a)

[http://kev.coolcavemen.com/2007/04/how-to-grow-any-qemu-system-image/](http://kev.coolcavemen.com/2007/04/how-to-grow-any-qemu-system-image/)

---

### Post by xOrphenochx on 2009-08-07
Thanks. Glad it wasn't something simple and me being an idiot. This really concerns me, you'd think this would have been something worked out long ago.

---

### Post by bodhi.zazen on 2009-08-07
> **xOrphenochx said:**
> Thanks. Glad it wasn't something simple and me being an idiot. This really concerns me, you'd think this would have been something worked out long ago.

Well to be honest if it is a Linux guest it is fairly simple. Just add a new disc, boot with a live CD, copy the partition with dd or gparted, resize the new partition, shut the grues down, boot with the new disk.

The problem is with Windows Guests, Windows is designed to detect (and reject) hardware changes.

Why should it be any different with virtual vs physical guests ? The problems are in how the underlying guest OS uses hard disks (making a new larger virtual disk is the easy part).

If you are using Linux Guests take a look at LVM.

---

### Post by xOrphenochx on 2009-08-07
LVM is in my future, but I'm still trying to get atleast a 4 disk RAID array going, but actual physical space is an issue.

---

