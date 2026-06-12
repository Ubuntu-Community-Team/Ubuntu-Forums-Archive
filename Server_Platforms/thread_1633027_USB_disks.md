---
title: "USB disks"
date: 2010-11-28
forum: Server Platforms
---

### Post by Vegan on 2010-11-28
I have lots of USB disks, so given say a bunch of PCI USB cards any problems attaching a bunch of disks?

How about if all the disks are yanked and reattached at different ports, Ubuntu smart enough to see what goes where?

---

### Post by HermanAB on 2010-11-29
If the volume has a label, then that is used to create the mount point and then the mount point should remain the same when you yank and replug.  If no label, then Ubuntu uses a generic mount point like /media/disk_1.

---

### Post by Vegan on 2010-12-01
So what do I need to do to label disks?

---

### Post by Sazhen86 on 2010-12-02
Hi

Renaming a disk depends on the format.  This page should help:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Also, Ubuntu uses UUIDs for mounting disks from the fstab:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I use the UUID method to mount a USB ext4 disk on Ubuntu Server and it works for me.

Cheers

---

