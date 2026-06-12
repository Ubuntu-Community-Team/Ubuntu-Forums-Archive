---
title: "Raid stops after restart"
date: 2009-07-28
forum: Server Platforms
---

### Post by ViPeRaY on 2009-07-28
Hey folks,
 
I am testing Ubuntu Server with raid to understand how exactly raid works on ubuntu. So far it has been good. I understood the applications (fdisk, mdadm etc.) I not new to Ubuntu but i am not a pro neither.
 
I set up a raid1 wit two HD. So far everything works fine, no errors. However after every restart, the array stops working. Please see /proc/mdstat output before and after the restart below.
```

MDSTAT BEFORE RESTART
 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 
md1 : active raid1 sdb1[0] sdc1[1]
      16771712 blocks [2/2] [UU]
 
unused devices: <none>

``````

MDSTAT AFTER RESTART
 
 Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 
md_d1 : inactive sdc1[1](S)
      16771712 blocks
 
unused devices: <none>

```To make raid usable after restart, i try assemble them with the command below.
 
mdadm --assemble --scan --uuid=3b1a2915:d91c9a66:a31daec1:a2180fa4
 
But some reason, raid only picks up one hard drive. The second hard drive does not seem UP, please see below.
 
```

MDSTAT AFTER THE ASSEMBLE COMMAND
 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
 
md1 : active raid1 sdb1[0]
      16771712 blocks [2/1] [U_]
 
md_d1 : inactive sdc1[1](S)
      16771712 blocks
 
unused devices: <none>

``````

THIS IS THE OUTPUT OF COMMAND BELOW AFTER I ASSEMBLE THE RAID.
 
viper@UServerTST:/mnt/md1$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Mon Jul 27 20:46:40 2009
     Raid Level : raid1
     Array Size : 16771712 (15.99 GiB 17.17 GB)
  Used Dev Size : 16771712 (15.99 GiB 17.17 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent
    Update Time : Mon Jul 27 21:30:21 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
           UUID : 3b1a2915:d91c9a66:a31daec1:a2180fa4 (local to host UServerTST)
         Events : 0.8
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed

```As you see after restart raid does not come online. If i try to assemble them manually, the second HD shows as removed. Do you have any idea what is wrong?
 
Also if i try below to add the HD to the array manually:
```

viper@UServerTST:/mnt/md1$ sudo mdadm /dev/md1 -a /dev/sdc1 
mdadm: Cannot open /dev/sdc1: Device or resource busy

```I get the busy error as you see. Well I will be building a file server this week and I need to figure out what is going on. Also this is a test environment. Everything is on vmware. Do you think raid is failing because it is not running on real hardware?
 
I appriciate your help. Thanks,

---

### Post by grantemsley on 2009-07-28
I had this exact same problem.

I believe the solution was that the array wasn't listed in /etc/mdadm/mdadm.conf

---

### Post by fjgaude on 2009-07-28
See if this gets you our of the issue:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Let us know how things go. Thanks!

---

### Post by ViPeRaY on 2009-07-28
Thanks for the replies. I tried the command, here is the result.
 
```

[EMAIL="viper@UServerTST:~$"]viper@UServerTST:~$[/EMAIL] sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf

-bash: /etc/mdadm/mdadm.conf: Permission denied


```

---

### Post by ViPeRaY on 2009-07-28
Guys, thanks for directing me to mdadm.conf. I fixed the problem by editing the file manually. Please see below my mdadm.conf file before and after I edited the file. Now my raid comes online after the restart automatically. Thanks a lot.
 
```

_Original MDADM.CONF_ 
 
viper@UServerTST:~$ cat /etc/mdadm/mdadm.conf
 
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
# This file was auto-generated on Mon, 27 Jul 2009 20:09:22 -0500
# by mkconf $Id$

```
 
```

_MANUALLY EDITED MDADM.CONF_
 
viper@UServerTST:~$ cat /etc/mdadm/mdadm.conf
 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#
# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
 
DEVICE /dev/sdb1 /dev/sdc1
 
ARRAY /dev/md1 uuid=3b1a2915:d91c9a66:a31daec1:a2180fa4
           auto=yes
 
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes
 
# automatically tag new arrays as belonging to the local system
HOMEHOST <system>
 
# instruct the monitoring daemon where to send mail alerts
MAILADDR root
 
# definitions of existing MD arrays
# This file was auto-generated on Mon, 27 Jul 2009 20:09:22 -0500
# by mkconf $Id$

```

---

### Post by grantemsley on 2009-07-29
I had this exact problem when I upgraded my server to the latest distro.  Is this a known bug that arrays aren't getting added to mdadm.conf?

---

### Post by fjgaude on 2009-07-29
From what I know 9.04 changes the UUID of the array, so a new mdadm.conf has to be created. There are several ways to re-create that file, I gave only one.

Normally there is an ARRAY line in the file:

```
ARRAY /dev/md32 level=raid5 num-devices=4 UUID=e7a804a6:30bd2cfd:f9346e8d:a51a8587
```

I never add the device names in the DEVICE line.

---

### Post by DirtDart on 2010-12-08
> **fjgaude said:**
> See if this gets you our of the issue:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```



This seems to still be an issue in Ubuntu Server 10.10 too.

Thanks for the info, this just bailed me out of reloading a ton of stuff off backups.

---

### Post by brettg on 2010-12-08
The problem here is that when you first built the raid it was "md1" but after reboot this changes to md_d1.

I have no idea why it does that but [this post]("http://tuxnetworks.blogspot.com/search?q=mdadm.conf") describes how to fix it.

---

### Post by Zroxer on 2012-11-14
We have trawled the internet for a solution to this. And finially it worked! Thanks alot!!

Tried with mdadm --scan --detail instead. -.-

---

