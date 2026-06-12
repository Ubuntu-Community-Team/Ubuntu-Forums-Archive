---
title: "Unable to find mdadm file"
date: 2014-05-15
forum: Server Platforms
---

### Post by konnn2 on 2014-05-15
Hi, I built a raid 1 system on ubuntu 14.04 server. When I try to find the  **/etc/initramfs-tools/conf.d/mdadm**,  in order to set "BOOT_DEGRADED=true",  that file does not exist. 
The result of the the  ```
fdisk -l
```  is :

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

    Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x000a53ac

       Device Boot      Start         End      Blocks   Id  System
    /dev/sdb1            2048     3905535     1951744   fd  Linux raid autodetect
    /dev/sdb2   *     3905536  1953523711   974809088   fd  Linux raid autodetect

    Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00013ecd

       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1            2048     3905535     1951744   fd  Linux raid autodetect
    /dev/sda2   *     3905536  1953523711   974809088   fd  Linux raid autodetect

    Disk /dev/md1: 998.1 GB, 998070091776 bytes
    2 heads, 4 sectors/track, 243669456 cylinders, total 1949355648 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00000000

    Disk /dev/md1 doesn't contain a valid partition table

    Disk /dev/md0: 1997 MB, 1997471744 bytes
    2 heads, 4 sectors/track, 487664 cylinders, total 3901312 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x00000000

    Disk /dev/md0 doesn't contain a valid partition table
```

and I am concerned about the invalid of the partition table, also.

Thank you.

---

### Post by kosmokramer314 on 2014-05-15
I just checked on my system and the file is very basic..  

```
# mdadm boot_degraded configuration
#
# You can run 'dpkg-reconfigure mdadm' to modify the values in this file, if
# you want. You can also change the values here and changes will be preserved.
# Do note that only the values are preserved; the rest of the file is
# rewritten.
#
# BOOT_DEGRADED:
# Do you want to boot your system if a RAID providing your root filesystem
# becomes degraded?
#
# Running a system with a degraded RAID could result in permanent data loss
# if it suffers another hardware fault.
#
# However, you might answer "yes" if this system is a server, expected to
# tolerate hardware faults and boot unattended.

BOOT_DEGRADED=false

```

and here are the permissions:

```
-rw-r--r-- 1 root root 654 Nov 11  2013 mdadm

```

what is the output of 
```
$sudo cat /proc/mdstat
```

---

### Post by konnn2 on 2014-05-15
the output is 
```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]
      1950656 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sda2[0] sdb2[1]
      974677824 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  4.3% (41948288/974677824) finish=114.0min speed=136311K/sec
      
unused devices: <none>


```

---

### Post by kosmokramer314 on 2014-05-15
your MD1 raid is rebuilding. I don't know anything about the memory leak..what's your actual question here??

---

### Post by konnn2 on 2014-05-16
Well in order to fix the memory leak I reconfigured the mdadm so that is why it is seen rebuilt.
The main problem now is the invalid partition table of the md.Somewhere I  read that the fdisk normaly cannot see the partition table of the md.  May that be  correct?

---

### Post by konnn2 on 2014-05-16
Well in order to fix the memory leak I reconfigured the mdadm so that is why it is seen rebuilt.
The main problem now is the invalid partition table of the md.Somewhere I read that the fdisk normaly cannot see the partition table of the md. May that be  correct?

---

### Post by steeldriver on 2014-05-16
Yes "doesn't contain a valid partition table" is most likely just fdisk not understanding the format - try parted instead

```

sudo parted -l

```

---

### Post by konnn2 on 2014-05-16
Thank you,I will check it.

---

### Post by konnn2 on 2014-06-09
So 
parted -l 

was ok but unfortunatelly or fortunatelly I switched to 12.04.4 server due to other issues , too.

Thank you.

---

