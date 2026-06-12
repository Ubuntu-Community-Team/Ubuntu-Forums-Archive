---
title: "Raid5 Disk Failure Nightmare"
date: 2014-07-09
forum: Server Platforms
---

### Post by thufirhawat2 on 2014-07-09
I have tried to search the internet as much as possible, but I cannot find a solution to my problem. I have a 12.04 server with two radi5 arrays, each with 6 disks. I use samba to tie it to a windows domain and perform Symantec system recovery backups of my production servers to it. md0 is fine, and it is mounted in /home/user. 

md1 is normally mounted in /home/user/backups2 and it had a hard drive crap out a few days ago. Last night I replaced the drive (sdi), and added it back into the array. The array started recovering which said it would take about 30 hours. I got an e-mail in the wee hours of the morning today stating that another drive had failed (sdj) and a mdadm --detail /dev/md1 stated the array was failed. I do not suppose I have a way of determining whether the array finished recovering before the second drive failed or not, presumably not since it has failed. If it didn't, then I guess I am just SOL. I tried stopping the array, and unmounting it to see if I could reassemble it and get it running again as the first failed drive was now listed as a spare, and the newly failed drive was listed as a faulty spare. When I type the command:```
sudo mdadm --assemble -v /dev/md1
``` response I get: ```
mdadm: looking for devices for /dev/md1
mdadm: no RAID superblock on /dev/md/0
mdadm: /dev/sdm1 is busy - skipping
mdadm: no RAID superblock on /dev/sdm
mdadm: /dev/sdl1 is busy - skipping
mdadm: no RAID superblock on /dev/sdl
mdadm: /dev/sdk1 is busy - skipping
mdadm: no RAID superblock on /dev/sdk
mdadm: /dev/sdi1 is busy - skipping
mdadm: no RAID superblock on /dev/sdi
mdadm: /dev/sdj1 is busy - skipping
mdadm: no RAID superblock on /dev/sdj
mdadm: /dev/sdh1 is busy - skipping
mdadm: no RAID superblock on /dev/sdh
mdadm: /dev/sdg1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdg
mdadm: /dev/sdf1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdf
mdadm: /dev/sde1 has wrong uuid.
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/umema
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda

```

I am nervous that it is looking ar devices like sdc1 which are member of MD0 which is working fine and I do NOT want to lose what is on it. I tried ```
sudo mdadm --zero-superblock /dev/sdi1

``` and received: ```
mdadm: Couldn't open /dev/sdi1 for write - not zeroing
```
This is consistent with every device in the array that I have tried to zero out. I tried manually unmounting each member device as well in case they were auto mounted somewhere for some reason, but it showed that they were all unmounted. I basically cannot get the array restarted by any means to even see if the data is salvageable. 

Here is cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdh1[0](S) sdi1[6](S) sdm1[5](S) sdl1[4](S) sdk1[3](S) sdj1[2](S)
      11720294928 blocks super 1.2
md0 : active raid5 sdg1[5] sdd1[2] sdf1[4] sde1[3] sdc1[1] sdb1[0]
      9766909440 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/6] [UUUUUU]
unused devices: <none>
```

Here is fdisk -lu

```

Disk /dev/sda: 4000 MB, 4000317440 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ae21
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     1953791      975872   82  Linux swap / Solaris
/dev/sda2   *     1953792     7811071     2928640   83  Linux
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba2c0
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   fd  Linux raid autodetect
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8e60
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   fd  Linux raid autodetect
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000789bc
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907028991  1953513472   fd  Linux raid autodetect
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000650f
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907028991  1953513472   fd  Linux raid autodetect
Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000323a3
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  3907028991  1953513472   fd  Linux raid autodetect
Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1fca
   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907028991  1953513472   fd  Linux raid autodetect
Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1438a3c6
   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdj: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c341a89
   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5342d48
   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdk: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x917b229a
   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8f93207
   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdm: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79dd3641
   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/md0: 10001.3 GB, 10001315266560 bytes
2 heads, 4 sectors/track, -1853239936 cylinders, total 19533818880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 2621440 bytes
Disk identifier: 0x00000000
Disk /dev/md0 doesn't contain a valid partition table
```

Here is my mdadm.conf

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#
# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes
# automatically tag new arrays as belonging to the local system
HOMEHOST <system>
# instruct the monitoring daemon where to send mail alerts
MAILADDR root
# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=b8f8d23b:c8434077:6d73ec29:bed5b21a name=osb3:0
ARRAY /dev/md/1 metadata=1.2 UUID=c4271c6d:e415531e:f994e0a7:475b875a name=osb3:1
# This file was auto-generated on Thu, 05 Jun 2014 15:53:28 -0400
# by mkconf $Id$
```

I have practiced replacing failed array devices on test machines and never had any such problems, but those tests were all RAID1 environments. Any help would be greatly appreciated, thank you.

---

### Post by thufirhawat2 on 2014-07-09
Ok, so I tried rebooting the machine and even though the RAID array does not have the OS installed on it (the OS is installed on a compact flash card that is built into the motherboard) it would not allow me to boot while this array was degraded. So in the recovery shell, I managed to zero out the superblocks on each disk and then remove the array. When I got the server booted up again, I was able to create the array with the --assume-clean option and it succeeded, I was able to mount it, and now I can access the data again. The second drive that failed is now showing as fine and is in the array and functioning, which makes me wonder just what the hell has happened, and if I can trust that drive now.. Anyone have any advice on how I should proceed, other than the obvious move of getting that backup data moved to another machine for now?

---

### Post by lukeiamyourfather on 2014-07-09
A lot of things could go wrong ranging from physical connection problems with the drives to firmware bugs or read timeouts from bad sectors (Linux normally resets the device bus after 30 seconds but some drives ignore this request). For what it's worth RAID 6 is the new RAID 5 because of the dramatically increased likelihood of a second disk failure during rebuild with such long rebuild times. Drives have gotten much bigger but their performance has hardly improved. What drives are used in the array?

It won't help in this particular case but in the future you might consider ZFS instead of RAID, it's a lot smarter and the rebuild times are much faster since only actual blocks of data are rebuilt (instead of everything including zeroed blocks). There's also up to triple parity stripes among many other great features.

---

### Post by SaturnusDJ on 2014-07-22
Look at SMART using smartctl.

---

### Post by thufirhawat2 on 2014-07-23
> **SaturnusDJ said:**
> Look at SMART using smartctl.

Yeah, after this debacle, I found an article discussing the use of this program, so I downloaded it to all my NASs and tested all the drives with it. After rebuilding the array, I have had no further problems with this machine, so it may have just been some kind of fluke.  Everything is thankfully back to normal. Thanks again to the community for the help and suggestions!

---

