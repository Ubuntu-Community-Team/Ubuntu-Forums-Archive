---
title: "How to extend '/' partition ???"
date: 2011-03-01
forum: Server Platforms
---

### Post by somchai on 2011-03-01
Hi, I am new for Ubuntu.  this is the first I buid an Ubuntu server.  I use Ubuntu 10.10 x86 server because I need to use the ntop with free license.  I installed the ntop then I try to install some more componets but I cannot.  it shows not enough disk space error.  I check the disk free space the result is below.
 
[FONT=courier]root@CNXD-GGLNTOP1:/# df
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/mapper/CNXD--GGLNTOP1-root
            1773912 1766676 0 100% /
none 502040 252 501788 1% /dev
none 508012 0 508012 0% /dev/shm
none 508012 36 507976 1% /var/run
none 508012 0 508012 0% /var/lock
/dev/sda1 233191 38218 182532 18% /boot
[/FONT]
[FONT=courier]--- But my server has 250 GB hard drive !!  then I check the volume group.[/FONT]
[FONT=courier][/FONT] 
[FONT=courier][FONT=courier]root@CNXD-GGLNTOP1:/# vgdisplay
--- Volume group ---
VG Name CNXD-GGLNTOP1
System ID
Format lvm2
Metadata Areas 1
Metadata Sequence No 4
VG Access read/write
VG Status resizable
MAX LV 0
Cur LV 2
Open LV 2
Max PV 0
Cur PV 1
Act PV 1
VG Size 232.64 GiB
PE Size 4.00 MiB
Total PE 59557
Alloc PE / Size 26076 / 101.86 GiB
Free PE / Size 33481 / 130.79 GiB
VG UUID lf04vC-f0lO-Z72L-MCGq-80Dw-yL9k-ObRTHl[/FONT]
[/FONT]
[FONT=courier]--- The volume group is 250GB !!   Then I try check the partition allocation.[/FONT]
[FONT=courier][/FONT] 
[FONT=courier][FONT=courier]root@CNXD-GGLNTOP1:/# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093b60

Device Boot Start End Blocks Id System
/dev/sda1 * 1 32 248832 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2 32 30402 243947521 5 Extended
/dev/sda5 32 30402 243947520 8e Linux LVM

Disk /dev/dm-0: 1845 MB, 1845493760 bytes
255 heads, 63 sectors/track, 224 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 150 MB, 150994944 bytes
255 heads, 63 sectors/track, 18 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table[/FONT]
[/FONT]
[FONT=courier]--- The sda1 is too small.  why ???   I check the logical volume then.[/FONT]
[FONT=courier][/FONT] 
[FONT=courier][FONT=courier]root@CNXD-GGLNTOP1:/# lvdisplay
--- Logical volume ---
LV Name /dev/CNXD-GGLNTOP1/root
VG Name CNXD-GGLNTOP1
LV UUID cFu6np-fjre-QIjC-Puma-agI0-zkuh-QL01NF
LV Write Access read/write
LV Status available
# open 1
LV Size 1.72 GiB
Current LE 440
Segments 1
Allocation inherit
Read ahead sectors auto
- currently set to 256
Block device 251:0

--- Logical volume ---
LV Name /dev/CNXD-GGLNTOP1/swap_1
VG Name CNXD-GGLNTOP1
LV UUID DbSn3E-G66l-Q8sU-CcCl-k3jq-P4Dh-qr1V6L
LV Write Access read/write
LV Status available
# open 1
LV Size 144.00 MiB
Current LE 36
Segments 1
Allocation inherit
Read ahead sectors auto
- currently set to 256
Block device 251:1
[/FONT][/FONT]
[FONT=courier][FONT=courier][/FONT][/FONT] 
[FONT=courier][FONT=courier]So I try to extend the LV - /dev/CNXD-GGLNTOP1/root  but not work.  'df' command still show 100% usage.[/FONT][/FONT]
[FONT=courier][FONT=courier][/FONT][/FONT] 
[FONT=courier][FONT=courier][FONT=courier]root@CNXD-GGLNTOP1:/# df
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/mapper/CNXD--GGLNTOP1-root
            1773912 1766676 0 100% /
none 502040 252 501788 1% /dev
none 508012 0 508012 0% /dev/shm
none 508012 36 507976 1% /var/run
none 508012 0 508012 0% /var/lock
/dev/sda1 233191 38218 182532 18% /boot
[/FONT][/FONT][/FONT]
[FONT=courier][FONT=courier][FONT=courier][/FONT][/FONT][/FONT] 
[FONT=courier][FONT=courier][FONT=courier]So......  Question[/FONT][/FONT][/FONT]
[FONT=courier][FONT=courier][FONT=courier]==>  How to extend the /dev/mapper/CNXD--GGLNTOP1-root ???[/FONT][/FONT][/FONT]
[FONT=courier][FONT=courier][FONT=courier][/FONT][/FONT][/FONT] 
[FONT=courier][FONT=courier][FONT=courier][/FONT][/FONT][/FONT] 
[FONT=courier][FONT=courier][FONT=courier]Thank you.
[/FONT][/FONT][/FONT]

---

