---
title: "Linux md RAID, bizarre md_d1 device"
date: 2009-08-07
forum: Server Platforms
---

### Post by Ellixis on 2009-08-07
Hi all,

_**Here is my problem :**_
Each time I reboot, and I do **cat /proc/mdstat**, I got a /dev/md_d1 device with /dev/sdb3 as a spare drive.
But I've never created a /dev/md_d1, and altough I stop the raid and reset the superblock, it still re-appears after a reboot.
```
# mdadm --stop /dev/md_d1
mdadm: /dev/md_d1 stopped

# mdadm --zero-superblock /dev/sdb3
```

I've also tried the following after a reboot :
```
mdadm: set /dev/sdb3 faulty in /dev/md_d1
mdadm: hot remove failed for /dev/sdb3: Device or resource busy
```

It seems there is a rogue superblock somewhere on /dev/sdb3 that makes it detected as a RAID member on boot. How can I really reset this partition or drive ?

_**My system is :**_
[LIST]
[*]Ubuntu 9.04
[*]2 * 1TB Hard Drives (sda, sdb)
[*]Partition layout on sda & sdb :
[LIST=1]
[*]sda1: boot+system
[*]sda2: swap
[*]sda3: data
[/LIST]
[*] /dev/md1 (RAID1) : /dev/sda3, /dev/sdb3
[/LIST]

More detail on partitions sda :
```
# sfdisk -l /dev/sda

Disque /dev/sda : 121601 cylindres, 255 têtes, 63 secteurs/piste
Unités= cylindres de 8225280 octets, blocs de 1024 octets, décompte à partir de 0

   Périph Amor Début     Fin   #cyls    #blocs    Id  Système
/dev/sda1   *      0+  13054   13055- 104864256   83  Linux
/dev/sda2      13055   13303     249    2000092+  82  Linux swap / Solaris
/dev/sda3      13304  121600  108297  869895652+  fd  Linux raid autodetect
/dev/sda4          0       -       0          0    0  Vide
```

More details on raid :
```
# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d1 : inactive sdb3[1](S)
      869895552 blocks
       
unused devices: <none>
```

```
# mdadm --query /dev/sdb3
/dev/sdb3: is not an md array
/dev/sdb3: device 1 in 2 device undetected raid1 /dev/md1.  Use mdadm --examine for more detail.
```

```
# mdadm --examine /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 05b3734c:afb4771e:fd8bbc22:8698eb7e (local to host zhong)
  Creation Time : Wed Aug  5 22:39:04 2009
     Raid Level : raid1
  Used Dev Size : 869895552 (829.60 GiB 890.77 GB)
     Array Size : 869895552 (829.60 GiB 890.77 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Fri Aug  7 05:24:06 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : ab89198b - correct
         Events : 69380


      Number   Major   Minor   RaidDevice State
this     1       8       19        1      active sync   /dev/sdb3

   0     0       8        3        0      active sync   /dev/sda3
   1     1       8       19        1      active sync   /dev/sdb3
```

```
# mdadm --examine --scan
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=05b3734c:afb4771e:fd8bbc22:8698eb7e
```

I have created my /dev/md1 using this command :
```
# mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sda3 /dev/sdb3
```

mdadm.conf :
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Thu, 19 Mar 2009 01:47:50 +0100
# by mkconf $Id$
```

---

### Post by grantemsley on 2009-08-07
Many people have had this issue, I believe after a kernel upgrade.  Searching for md_d1 on the forum should find it.

I believe the solution is to regenerate mdadm.conf...it's missing the array settings.

---

### Post by fjgaude on 2009-08-07
Try doing this and then rebooting:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Let us know what happens. Thanks!

---

### Post by Ellixis on 2009-08-12
> **fjgaude said:**
> Try doing this and then rebooting:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Let us know what happens. Thanks!

It works now after rebooting, thanks ! It seems to be a bug since Jaunty, a shame :(

---

### Post by fjgaude on 2009-08-13
It's amazing how Ubuntu takes two steps forward and a half-step backward with each release, yes!

Glad you are up and running.

---

