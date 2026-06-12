---
title: "extend2fs"
date: 2011-05-09
forum: Server Platforms
---

### Post by scopedial on 2011-05-09
Hello -
I have extended a logical volume from a partition on one disk into a entirely seperate
disk.
I wish to extend the file system from the original partition onto the newly extend volume.
I attempted this using extend2fs but it did not work, and did not mention why.
 
The command I used was -
 
*$ sudo resize2fs /dev/glab1/glab-share1/*
 
 
I attempted this on ubuntu server 10.04.
 
Any advice is appreciated...
 
:confused:

---

### Post by ian dobson on 2011-05-09
Hi,

Did you u(n)mount the file system before trying to extend it?

Regards
Ian Dobson

---

### Post by scopedial on 2011-05-09
Yes -
according to *umount* it wasn't mounted...

---

### Post by ian dobson on 2011-05-09
Hi,

What do you see when you do a fdisk -l? Could it be that the filesystem is in a partition, you've grown the block device, but not the partition containing the fs? So resize2fs did work, it's just that it had nothing to do.

Regards
Ian Dobson

---

### Post by scopedial on 2011-05-11
Current State -
 
I now have the file system resized on the logical volume.
Unfortunately I can only mount it manually!
When I attempt to mount the volume from fstab I get an error saying the partiition
is not availabe. Upon further investigation I have discovered that LVM does not start
before fstab is executed. Could this be the problem?
 
I have seen solutions calling for an LVM init script that performs the mounting and not fstab. Is this necessary?
 
Thanks for your input,
 
Lou:confused:

---

### Post by ian dobson on 2011-05-11
Hi,

So what was the problem, that you couldn't resize the partition.

You could start lvm/mount the partition through the /etc/rc.local

Regards
Ian Dobson

---

