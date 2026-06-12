---
title: "iotop"
date: 2012-05-09
forum: Server Platforms
---

### Post by Catalyph on 2012-05-09
Since updating / upgrading my 11.10 ubuntu server 2 days ago, the network write speed have been killed to about 2MBPS where previously they were 60+MBPS. I noticed a Process in iotop peaking at 99% whenever i make a write to the server called jbd2/dm-0-8 along with smbd -F.

Read speeds are perfectly fine with speed of 80+MBPS
where both those processes hit only MAX 5% io process

any idea's ?

it is a LVM with 3 500GB drives 

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdf1             5.6G  2.4G  2.9G  45% /
udev                  804M  4.0K  804M   1% /dev
tmpfs                 326M  904K  325M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  813M     0  813M   0% /run/shm
/dev/mapper/VolGrp00-LogVol00
                      1.4T  1.1T  215G  84% /NAS

fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table



Disk /dev/mapper/VolGrp00-LogVol00: 1500.3 GB, 1500310929408 bytes
255 heads, 63 sectors/track, 182402 cylinders, total 2930294784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


$uname -a
Linux MediaVault 3.0.0-19-server #33-Ubuntu SMP Thu Apr 19 20:32:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux



Any Ideas?

---

