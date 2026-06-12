---
title: "mdadm with new os"
date: 2020-11-03
forum: Server Platforms
---

### Post by bmarlet on 2020-11-03
Hi,
I've installed a storage server at home using ubuntu 18.04 on a 32GB SSD 2 years ago.
My storage device are in Raid mirroring :
[LIST]
[*]md0 using sdb and sdc
[*]md1 using sde and sdf.
[/LIST]

If my memory is not too bad, I think I 've created this raid with command like
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb2 /dev/sdc2

Here are the mkconf result :

```

[FONT=Arial]# mdadm.conf[/FONT]
[FONT=Arial]#[/FONT]
[FONT=Arial]# Please refer to mdadm.conf(5) for information about this file.[/FONT]
[FONT=Arial]#[/FONT]

[FONT=Arial]# by default (built-in), scan all partitions (/proc/partitions) and all[/FONT]
[FONT=Arial]# containers for MD superblocks. alternatively, specify devices to scan, using[/FONT]
[FONT=Arial]# wildcards if desired.[/FONT]
[FONT=Arial]#DEVICE partitions containers[/FONT]

[FONT=Arial]# auto-create devices with Debian standard permissions[/FONT]
[FONT=Arial]CREATE owner=root group=disk mode=0660 auto=yes[/FONT]

[FONT=Arial]# automatically tag new arrays as belonging to the local system[/FONT]
[FONT=Arial]HOMEHOST <system>[/FONT]

[FONT=Arial]# instruct the monitoring daemon where to send mail alerts[/FONT]
[FONT=Arial]MAILADDR root[/FONT]

[FONT=Arial]# definitions of existing MD arrays[/FONT]
[FONT=Arial]ARRAY /dev/md/0  metadata=1.2 UUID=5fde5081:3c130182:[/FONT][FONT=Arial]75cca3b9:a4ca2360 name=nas-ubuntu:0[/FONT]
[FONT=Arial]ARRAY /dev/md/1  metadata=1.2 UUID=33732136:ac68b7bf:[/FONT][FONT=Arial]27eac9e1:ee990b46 name=nas-ubuntu:1[/FONT]

```
[FONT=Arial]
mdadm --detail /dev/md0

[/FONT]```
[FONT=Arial]/dev/md0:[/FONT]
[FONT=Arial]        Version : 1.2[/FONT]
[FONT=Arial]  Creation Time : Sun Jan 19 18:44:30 2014[/FONT]
[FONT=Arial]     Raid Level : raid1[/FONT]
[FONT=Arial]     Array Size : 1953382336 (1862.89 GiB 2000.26 GB)[/FONT]
[FONT=Arial]  Used Dev Size : 1953382336 (1862.89 GiB 2000.26 GB)[/FONT]
[FONT=Arial]   Raid Devices : 2[/FONT]
[FONT=Arial]  Total Devices : 2[/FONT]
[FONT=Arial]    Persistence : Superblock is persistent[/FONT]

[FONT=Arial]    Update Time : Sun Nov  1 18:08:59 2020[/FONT]
[FONT=Arial]          State : clean[/FONT]
[FONT=Arial] Active Devices : 2[/FONT]
[FONT=Arial]Working Devices : 2[/FONT]
[FONT=Arial] Failed Devices : 0[/FONT]
[FONT=Arial]  Spare Devices : 0[/FONT]

[FONT=Arial]           Name : nas-ubuntu:0  (local to host nas-ubuntu)[/FONT]
[FONT=Arial]           UUID : 5fde5081:3c130182:75cca3b9:[/FONT][FONT=Arial]a4ca2360[/FONT]
[FONT=Arial]         Events : 1550[/FONT]

[FONT=Arial]    Number   Major   Minor   RaidDevice State[/FONT]
[FONT=Arial]       0       8       17        0      active sync   /dev/sdb1[/FONT]
[FONT=Arial]       1       8       33        1      active sync   /dev/sdc1
[/FONT]
```[FONT=Arial]

[/FONT][FONT=Arial]mdadm --detail /dev/md1

[/FONT]```
[FONT=Arial]/dev/md1:[/FONT]
[FONT=Arial]        Version : 1.2[/FONT]
[FONT=Arial]  Creation Time : Mon Sep 30 20:10:57 2019[/FONT]
[FONT=Arial]     Raid Level : raid1[/FONT]
[FONT=Arial]     Array Size : 3906887488 (3725.90 GiB 4000.65 GB)[/FONT]
[FONT=Arial]  Used Dev Size : 3906887488 (3725.90 GiB 4000.65 GB)[/FONT]
[FONT=Arial]   Raid Devices : 2[/FONT]
[FONT=Arial]  Total Devices : 2[/FONT]
[FONT=Arial]    Persistence : Superblock is persistent[/FONT]

[FONT=Arial]  Intent Bitmap : Internal[/FONT]

[FONT=Arial]    Update Time : Sun Nov  1 18:08:59 2020[/FONT]
[FONT=Arial]          State : clean[/FONT]
[FONT=Arial] Active Devices : 2[/FONT]
[FONT=Arial]Working Devices : 2[/FONT]
[FONT=Arial] Failed Devices : 0[/FONT]
[FONT=Arial]  Spare Devices : 0[/FONT]

[FONT=Arial]           Name : nas-ubuntu:1  (local to host nas-ubuntu)[/FONT]
[FONT=Arial]           UUID : 33732136:ac68b7bf:27eac9e1:[/FONT][FONT=Arial]ee990b46[/FONT]
[FONT=Arial]         Events : 7832[/FONT]

[FONT=Arial]    Number   Major   Minor   RaidDevice State[/FONT]
[FONT=Arial]       0       8       48        0      active sync   /dev/sdd[/FONT]
[FONT=Arial]       1       8       64        1      active sync   /dev/sde[/FONT][FONT=Arial]
[/FONT]
```[FONT=Arial]
[/FONT]
I've bought a new larger ssd (120GB) to install ubuntu 20.04.

How do I parametrize mdadm to get my storage device on my new ubuntu installation (I'm really scared about loosing all my personnal photos)

Thank you for your help !

bmarlet

---

### Post by darkod on 2020-11-03
You shouldn't have used disk devices as members of md1. Use partitions always, not the disk name. But it can continue to work like this, now that you already have much data on it.

Basically you have two options. If I remember correctly the OS installation will detect the current arrays and you can specify a mount point for them during the installation.

Or you can temporarily disconnect the array disks, do the OS installation without telling it anything about mdadm. Then you connect the disks, assemble the arrays once manually, run the update-initramfs and add the ARRAY lines in mdadm.conf. Then after a reboot the arrays get auto-assembled.

It's a personal preference which option you choose. With the second one you have little more manual work but you control the process better.

---

### Post by bmarlet on 2020-11-03
I ve already install my ubuntu with all storage disks disconnected to avoid mistakes.
Could you explain what you mean by "[COLOR=#000000]assemble the arrays once manually" ?

Thank you[/COLOR]

---

### Post by darkod on 2020-11-03
I meant using 'sudo mdadm --assemble' to assemble the arrays. There is also a way to auto-scan disks and assemble, I think the command was:
```
sudo mdadm --assemble --scan
```

Or instead of --scan you use the necessary parameter to tell it what to assemble exactly.

But anyway, if you already achieved the reinstall you can mark the thread as SOLVED.

---

