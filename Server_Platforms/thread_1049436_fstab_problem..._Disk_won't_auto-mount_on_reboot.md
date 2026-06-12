---
title: "fstab problem... Disk won't auto-mount on reboot"
date: 2009-01-24
forum: Server Platforms
---

### Post by Rhiknow on 2009-01-24
I've added the following line to my fstab:

"/dev/sda6       /mnt/mnt_point        ext3    user,auto,exec.rw,relatime    0       0"

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=afcfb118-30cc-4b62-b2e8-41ba779bca12 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=aceb14bf-2231-4020-12d9-33554c98c82c /boot           ext3    relatime        0       2
# /dev/sda5
UUID=4ca2bac1-1986-4f42-a935-6c5a444665c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda6       /mnt/mnt_point     ext3    user,auto,exec.rw,relatime      0       0
```

But this doesn't seem to work!?

If I type "sudo mount /dev/sda6 /mnt/mnt_point", it mounts perfectly fine. I want this to be automated on re-boot though -- I don't want to have to type this in every time I start the computer!!!

My disk is partitioned as follows:
/dev/sda1: NTFS, running Vista (40GB)
/dev/sda2: ext3, /boot (200MB)
/dev/sda3: ext3, / (40GB)
/dev/sda4: (extended partition)
/dev/sda5: swap (4GB)
/dev/sda6: ext3, (no fixed mount point) (100GB)

---

### Post by gombadi on 2009-01-24
> 
/dev/sda6 /mnt/mnt_point ext3 user,auto,exec.rw,relatime 0 0


Between exec and rw is that a comma, full stop or a typo?

---

### Post by sully101 on 2009-01-24
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

I had the best results by using UUID method. Also [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

Is the folder already created where you want to mount it? It should be.

---

### Post by Rhiknow on 2009-01-24
> **gombadi said:**
> Between exec and rw is that a comma, full stop or a typo?

[img]http://www.clipartof.com/images/thumbnail/1892.gif[/img]

Thanks man. 

(I think I'm overdue a confession...)

---

