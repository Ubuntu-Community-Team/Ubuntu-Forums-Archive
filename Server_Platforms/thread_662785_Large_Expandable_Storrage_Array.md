---
title: "Large Expandable Storrage Array"
date: 2008-01-09
forum: Server Platforms
---

### Post by colinwilson on 2008-01-09
What we want to do is create a file server that serves out one large file system over nfs.  We are able to add more hard drives to this system by plugging in more HP storage arrays and using the hardware raid controller to raid the new hard drives together and present one big hard drive to the OS.  We want to be able to then add the new big hard drive to the existing data array and extend the file system across it.

LVM is supposed to be able to do this.  We can create a Volume Group and put the hard drives presented to the os by the hardware controller in it.  Create a Logical volume and then put a XFS file system on top of that.  Then the next time we need to add hard drives we can add a new hard drive box, use the hardware controller to raid the new drives and present them to ubuntu, add them to the volume group, extend the Logical Volume, and then extend XFS fine.  LVM just seems to have a problem with anything over and inculding 4TB.  We can create an lvm group, logical volume, and file system up to 13TB and it is usable untill we reboot the system.  After the system comes up from a reboot LVM can no longer find the volume group or the physical disks for the group even though the drives and partitions are still seen by the OS.  The largest file system we were able to create was 3.7TB and have it come back at boot, our next try was a little over 5TB and that one was not seen on reboot.

Does anyone know of any better way of doing this or what could be wrong with LVM?

---

### Post by kidders on 2008-01-10
Hi there,

Afaik, the maximum size of a logical volume is limited by (among other things) the physical extent size you set when you create the volume group. Properly configured, and using an appropriate filesystem, LVM can create volumes well into the exabyte range. Having said that, since there can never be more than 65,536 PEs in a logical volume, it is possible you may have limited your expandability by making them too small.

I don't know much about LVM, but I thought this suggestion would at least be worth a shot. Unfortunately, if I turn out to be right, there is no way to resize PEs without recreating the entire volume group.

---

