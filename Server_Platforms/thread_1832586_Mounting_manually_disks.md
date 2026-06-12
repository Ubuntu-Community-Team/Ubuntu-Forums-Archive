---
title: "Mounting manually disks"
date: 2011-08-24
forum: Server Platforms
---

### Post by silveringking on 2011-08-24
Hello, I am trying to mount manually 2 disks in my ubuntu server (10.04 lucyd linx).

Anyway, this appears to me:

> root@ns353440:~# sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

root@ns353440:~# sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000774aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10238976+  fd  Linux raid autodetect
/dev/sda2            1276       90946   720282307+  fd  Linux raid autodetect
/dev/sda3           90947       91201     2046879+  82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e613

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10238976+  fd  Linux raid autodetect
/dev/sdb2            1276       90946   720282307+  fd  Linux raid autodetect
/dev/sdb3           90947       91201     2046879+  82  Linux swap / Solaris

Disk /dev/md2: 1475.1 GB, 1475138027520 bytes
2 heads, 4 sectors/track, 360141120 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 10.5 GB, 10484645888 bytes
2 heads, 4 sectors/track, 2559728 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7694a755

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       77825   625129312    c  W95 FAT32 (LBA)
root@ns353440:~# sudo mkdir /media/external
root@ns353440:~# sudo mount -t vfat /dev/sdc1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I am trying to use this guide [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) , yes my disks (one pen and one pen are both usb). If you could help me I would be please! Thank you!

---

### Post by oldfred on 2011-08-25
I do not see difference either. 

Did you make the mount point first?

sudo mkdir /media/external

Have you run chkdsk on fat partition recently. Or why such a large FAT partition, generally NTFS is better unless you have to have compatibility with other devices like an Xbox. FAT has a max of 4GB and no journal. So large files just get truncated or destroyed and recovery of issues with chkdsk is not reliable without a journal. FAT is ok for a small flash drive as then the journal does not add much and you cannot store huge files anyway.

---

### Post by silveringking on 2011-08-25
> carlos@carlos:~$ ssh root@91.121.95.96
root@91.121.95.96's password: 
Linux ns353440.ovh.net 2.6.38.2-xxxx-std-ipv6-64 #1 SMP Tue Apr 12 17:19:35 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.3 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
Ubuntu 10.04.3 LTS

server    : 33115
ip        : 91.121.95.96
hostname  : ns353440.ovh.net


4 packages can be updated.
3 updates are security updates.

Last login: Thu Aug 25 05:52:52 2011 from a213-22-219-157.cpe.netcabo.pt
root@ns353440:~# sudo mkdir /media/external
mkdir: cannot create directory `/media/external': File exists
root@ns353440:~# sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000774aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10238976+  fd  Linux raid autodetect
/dev/sda2            1276       90946   720282307+  fd  Linux raid autodetect
/dev/sda3           90947       91201     2046879+  82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e613

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10238976+  fd  Linux raid autodetect
/dev/sdb2            1276       90946   720282307+  fd  Linux raid autodetect
/dev/sdb3           90947       91201     2046879+  82  Linux swap / Solaris

Disk /dev/md2: 1475.1 GB, 1475138027520 bytes
2 heads, 4 sectors/track, 360141120 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 10.5 GB, 10484645888 bytes
2 heads, 4 sectors/track, 2559728 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7694a755

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       77825   625129312    c  W95 FAT32 (LBA)
root@ns353440:~# sudo mount -t vfat /dev/sdc1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ns353440:~# 


Just to make sure here is a new log...

No I didn't do such thing... This one is specifically a server that I bought. Myself I prefer to use Linux Mint on the desktop...

---

