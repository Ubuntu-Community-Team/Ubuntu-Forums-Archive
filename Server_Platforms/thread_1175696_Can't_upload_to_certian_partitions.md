---
title: "Can't upload to certian partitions"
date: 2009-06-01
forum: Server Platforms
---

### Post by janthes on 2009-06-01
Hi folks,

I installed Ubuntu Server 9.04 and I'm attempting to back up my files via ssh using Tunnelier.  I can upload to the disk with the installation on it, but not my two other disks. Searching though Google, it seems to be a permission issue.  

I'm not to keen on Linux ownership commands and editing fstab yet, and I need assistance so I don't break my system. My fstab is:


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e6ce8279-bcc4-40bf-b857-e81219e81d49 /               ext3    relatime,errors=remount-ro 0       1
# /storage00 was on /dev/sdb1 during installation
UUID=f416c670-9ce2-4c4e-a748-5863a139e328 /storage00      ext3    relatime        0       2
# /storage01 was on /dev/sdc1 during installation
UUID=b8518169-ff88-4065-b8a6-778c67f445d8 /storage01      ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=b527763f-d610-452c-99a4-c778336aa5d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Thanks!

---

### Post by milton1 on 2009-06-01
linux file permissions can be easily modified using the 'chmod' and 'chown' commands in a terminal. Details on both commands can be found using the following commands:
```
man chmod
man chown
```

---

### Post by janthes on 2009-06-01
I know the chmod and chown commands loosely, but how do I use the with fstab?

---

