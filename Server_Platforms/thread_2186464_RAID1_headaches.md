---
title: "RAID1 headaches"
date: 2013-11-07
forum: Server Platforms
---

### Post by brandonmiller21 on 2013-11-07
I'm a complete novice when it comes to RAID configuration and I'm struggling with this one.  I recently installed Ubuntu 12.04.3 Server 32bit on an old PC with one primary HDD for /, /boot, swap, and /Home  then I have two 1TB drives that I had intended on using as RAID1 storage for an Owncloud installation.  I'm not having any luck with getting the drives to be usable as a RAID1 storage location...I've tried googling and reading through different forum posts, but nothing has got me in the right direction as far as I can tell.

```
mrblue@Windoge:~$ sudo mdadm --examine /dev/sdb1/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6221e2b3:d4c03fb4:a8bee426:22045b4c
           Name : Windoge:0  (local to host Windoge)
  Creation Time : Wed Nov  6 21:33:11 2013
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 976629568 (931.39 GiB 1000.07 GB)
  Used Dev Size : 1953259136 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1c9642eb:80059df4:e10ee634:4bee06a9


    Update Time : Thu Nov  7 10:55:51 2013
       Checksum : 6ec2ecc8 - correct
         Events : 44


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
```
```
mrblue@Windoge:~$ sudo mdadm --examine /dev/sdc1/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6221e2b3:d4c03fb4:a8bee426:22045b4c
           Name : Windoge:0  (local to host Windoge)
  Creation Time : Wed Nov  6 21:33:11 2013
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 976629568 (931.39 GiB 1000.07 GB)
  Used Dev Size : 1953259136 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5851d78f:c1b911cf:ecf5a69b:be350fc6


    Update Time : Thu Nov  7 10:55:51 2013
       Checksum : 71958ac4 - correct
         Events : 44


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing)
```
```
mrblue@Windoge:~$ sudo mdadm --assemble --scan -vmdadm: looking for devices for /dev/md/0
mdadm: no RAID superblock on /dev/md0
mdadm: no RAID superblock on /dev/dm-0
mdadm: /dev/sdc1 is busy - skipping
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sda5
mdadm: no RAID superblock on /dev/sda4
mdadm: no RAID superblock on /dev/sda3
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdb1 is busy - skipping
mdadm: no RAID superblock on /dev/sdb
```
```
mrblue@Windoge:~$ sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b3f2d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   fd  Linux raid autodetect


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db9c5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    39063551    19530752   83  Linux
/dev/sda2   *    39063552    39454719      195584   83  Linux
/dev/sda3        39454720    43360255     1952768   82  Linux swap / Solaris
/dev/sda4        97771518   488396799   195312641    5  Extended
/dev/sda5        97771520   488396799   195312640   83  Linux


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0007e095


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832   fd  Linux raid autodetect


Disk /dev/mapper/cryptswap1: 1999 MB, 1999634432 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3905536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ec916bb


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table


Disk /dev/md0: 1000.1 GB, 1000068677632 bytes
2 heads, 4 sectors/track, 244157392 cylinders, total 1953259136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table
```

Please point me in the right direction as to what I need to do. Should I blow it away and start over, or am I just missing a final step or two?

Thanks in advance!

---

### Post by brandonmiller21 on 2013-11-07
Trying to work through this myself...here's the next thing I've done so far:
```
mrblue@Windoge:~$ sudo mdadm --stop /dev/md0mdadm: stopped /dev/md0
mrblue@Windoge:~$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
mdadm: /dev/md0 has been started with 2 drives.
```
```
mrblue@Windoge:~$ sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.
```
```
mrblue@Windoge:~$ sudo cat /proc/mdstatPersonalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[0] sdc1[1]
      976629568 blocks super 1.2 [2/2] [UU]


unused devices: <none>
```
```
mrblue@Windoge:~$ cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=82483c62-8c1c-4bb6-8177-baccaa24e107 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=ceadd6af-9503-4faa-bf18-43693444dd82 /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=0e495155-eaa7-4fc3-b66c-9c5fbde68340 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=d9f61be9-aa01-4261-a0ac-3b690508b8cc none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```
```
mrblue@Windoge:~$ sudo mount -t auto /dev/md0/ /mnt/
mount: you must specify the filesystem type
```
```
mrblue@Windoge:~$ sudo mount -t ext4 /dev/md0/ /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by brandonmiller21 on 2013-11-07
THIS: [http://geekscrap.com/2010/02/linux-raid-disk-wipeout/](http://geekscrap.com/2010/02/linux-raid-disk-wipeout/)

THEN THIS LINK: [https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

I had to wipeout my current partitions with cfdisk (can be found in 2nd link) and then reboot the system before proceeding with adding new partitions and moving forward from there.

---

