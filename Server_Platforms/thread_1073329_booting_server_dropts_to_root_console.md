---
title: "booting server dropts to root console"
date: 2009-02-18
forum: Server Platforms
---

### Post by Mr.Carramba on 2009-02-18
hi,

When booting server the ubuntu drops to root console. the following error is displayed
Log of fsck -C -R -A -a 
Wed Feb 18 12:48:51 2009

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
fsck died with exit status 8

system is set up on hardware RAID 1, and disks created with ubuntu LVM

what is the problem?
how do I fix it?

Thank you for taking time
L

---

### Post by Mr.Carramba on 2009-02-18
hum, fstab was :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/sm--comnet-root
UUID=022c7cf3-bec8-41d9-938f-548738f0bd41 /               ext3    relatime,errors=remount-ro 1       
# /dev/mapper/ddf1_4c53492020202020808626820000000036cd4072000014505
UUID=da7bb270-1203-4aa9-80d1-36e54167d69b /boot           ext3    relatime        0       2
# /dev/mapper/sm--comnet-swap_1
UUID=bc583d84-62f9-4e74-b935-7fd8c3c8cc67 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I changed 
UUID=022c7cf3-bec8-41d9-938f-548738f0bd41 /               ext3    relatime,errors=remount-ro 1  <- to 0
and
     UUID=da7bb270-1203-4aa9-80d1-36e54167d69b /boot           ext3    relatime        0       2 <- to 0

but Im not shore if it is so good idea do shut fsck off completely .

---

