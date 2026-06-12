---
title: "Why won't my (external/USB) drive mount?"
date: 2010-03-07
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-07
Output of blkid:
 ```
/dev/mapper/Tsunami_LVG1-LV_home: LABEL="home" UUID="cad22752-aca8-49c7-94b1-f08423819705" TYPE="xfs" 
/dev/mapper/Tsunami_LVG1-LV_swap: TYPE="swap" UUID="5e1918d5-3a07-4dc5-8216-c4c0f4d1e341" 
/dev/mapper/Tsunami_LVG1-LV_root: LABEL="root" UUID="cb276fc0-ced3-4926-81b8-757e5b68c4e5" TYPE="ext3" 
/dev/sda1: LABEL="boot" UUID="d00cac4f-6873-4188-b6e2-902740454ba1" TYPE="ext2" 
/dev/sda5: UUID="T2wwpd-lG9L-IrHz-BfAx-pVse-3C9a-rBjT1R" TYPE="lvm2pv" 
/dev/sdc1: UUID="504A0C654A0C4A64" LABEL="SEAGATE300" TYPE="ntfs" 
[COLOR=Red]/dev/sdd1: UUID="F8C85616C855D38A" LABEL="Expansion Drive" TYPE="ntfs" [/COLOR]

```/etc/fstab contents:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/Tsunami_LVG1-LV_root
UUID=cb276fc0-ced3-4926-81b8-757e5b68c4e5 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda1
UUID=d00cac4f-6873-4188-b6e2-902740454ba1 /boot           ext2    relatime      
  0       2
# /dev/mapper/Tsunami_LVG1-LV_home
 UUID=cad22752-aca8-49c7-94b1-f08423819705 /home           xfs     relatime      
  0       2
# /dev/mapper/Tsunami_LVG1-LV_swap
UUID=5e1918d5-3a07-4dc5-8216-c4c0f4d1e341 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/store ntfs-3g defaults 0 0
# 1.5TB USB
[COLOR=Red]UUID=F8C85616C855D38A /media/tb1 ntfs-3g defaults 0 0[/COLOR]
# 300GB Seagate-3 USB 
UUID=504A0C654A0C4A64 /media/3cg3 ntfs-3g defaults 0 0
```mount -a returns:
```
fuse: failed to access mountpoint /media/tb1: Input/output error
```Help?

---

### Post by HermanAB on 2010-03-08
Howdy, /media is used for transcient mounts.  Fixed mounts controlled by fstab should be in /mnt.  You need to create the mount point before you use it.

---

### Post by Donny Bahama on 2010-03-08
Thanks for the response, Herman! I didn't understand (obviously) the difference between /mnt and /media, but if the mount point was, in fact, created (as /media/tb1), should it really make that much difference? (I'll go ahead and create/use mountpoints under /mnt, but I'm curious as to why it maters so much.)

---

