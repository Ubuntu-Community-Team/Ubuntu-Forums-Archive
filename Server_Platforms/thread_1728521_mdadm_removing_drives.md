---
title: "mdadm removing drives"
date: 2011-04-13
forum: Server Platforms
---

### Post by mn_voyageur on 2011-04-13
Question #1: Why are these drives removed?  Disk Utility say that the drives are okay and assigned to the RAID.  However, Disk Utility also says that the RAID is not running.

mark@10:~$ sudo mdadm --detail /dev/md0
```
/dev/md0:
        Version : 00.90
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 12 05:53:55 2011
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
         Events : 0.198

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       17        3      active sync   /dev/sdb1
```

From another post, I found the following command:
    mdadm -E /dev/sdc1
```
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Mon Apr 11 05:54:13 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 62e6c83 - correct
         Events : 182

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       17        3      active sync   /dev/sdb1
```

I then ran:
mark@10:~$ sudo mdadm -E /dev/sdd1
```
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Apr 12 05:53:55 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 62fbdf7 - correct
         Events : 198

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       49        0      active sync   /dev/sdd1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       17        3      active sync   /dev/sdb1
```

Then I ran:
mark@10:~$ sudo mdadm -E /dev/sda1
```
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : b40cc711:46ef5048:1178d5b1:7b4fd811 (local to host 10)
  Creation Time : Mon Feb 21 05:24:20 2011
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Mar 17 06:47:23 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 60d832d - correct
         Events : 155

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8        1        2      active sync   /dev/sda1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8        1        2      active sync   /dev/sda1
   3     3       8       17        3      active sync   /dev/sdb1
```

Why does examining different drives in the array generate different results?

Any help would be appreciated.

MarkN

---

### Post by MakOwner on 2011-04-13
I'm no expert by any means so take this as what it's worth, which is not much:

How many physical drives do you have in the array?
I had an array set up once that had drives that dropped out like that - and would even sometimes show up as a new device -- /dev/sde1 would disappear then reappear and become /dev/sdf1.

Had to do with running a SATA1 controller with SATA11 disks.  Once I jumpered all of the drives to force them to SATA1 speed, things stabalized.


Might or might not be your issue, but take a look at your hardware...

---

### Post by mn_voyageur on 2011-04-13
MakOwner,

The drive names have not changed.  What is confusing to me is that Disk Utility tells me that everything is okay.

It sees the disks and knows that the disks belong to the RAID.  

There are four drives.  Obviously running, or supposed to be running, RAID6.

I appreciate the help.

MarkN

---

### Post by disabledaccount on 2011-04-14
> **MakOwner said:**
> Had to do with running a SATA1 controller with SATA11 disks.  Once I  jumpered all of the drives to force them to SATA1 speed, things  stabalized.I suppose You mean SATA2 by writting "SATA11" - well that's quite simple - SATA2 drives tries to check/negotiate transfer speed what can confuse old controllers (f.e. causing timeouts) - so forcing SATA1 solves the problem.

> **mn_voyageur said:**
> Question #1: Why are these drives removed?
...
Why does examining different drives in the array generate different results?
Common reason is unstable SATA link due to bad cables - this is a plague in fact - check SMART for UDMA CRC errors: 
>smartctl -A /dev/sd<X>

When SATA link was broken, there was no possibility to save array state - so "good" disks have correct information (array was degraded) and "bad" disks are reporting state *before* they were dropped.

---

### Post by mn_voyageur on 2011-04-14
Checked for SMART for UDMA CRC errors.  None found on any of the disks.

Anything else I can try?

MarkN

---

### Post by rubylaser on 2011-04-14
What do you have in /etc/mdadm/mdadm.conf?
```
cat /etc/mdadm/mdadm.conf
```

And, I see this array was recently setup.  Did it work properly for you at some point?  If so, did anything happen to cause this change?

---

### Post by mn_voyageur on 2011-04-14
Yes it worked.  I moved some files onto it.  But never tried breaking it.  I was going to back up my test files ....

Output of: cat /etc/mdadm/mdadm.conf

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
ARRAY /dev/md0 level=raid6 num-devices=4 UUID=f7d66868:9ef74ca1:b0dad889:1e64a60f

# This file was auto-generated on Mon, 21 Feb 2011 04:49:14 -0600
# by mkconf $Id$

---

### Post by mn_voyageur on 2011-04-14
Should I remove and then create the array?  

I don't want to get ahead of anyone, just read that my files should remain intact.  (As I understood the post.)

MarkN

---

### Post by mn_voyageur on 2011-04-14
I ran fdisk -l.  The last row is interesting:
[INDENT]Disk /dev/md0 doesn't contain a valid partition table[/INDENT]

Below is the complete output:> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001283a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18708   150265856   83  Linux
/dev/sda2           18708       19458     6022145    5  Extended
/dev/sda5           18708       19458     6022144   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000baa15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004600b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c96e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000404348928 bytes
2 heads, 4 sectors/track, 488379968 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


Thanks,
MarkN

---

### Post by dtfinch on 2011-04-15
I think the UUID is wrong in your mdadm.conf. If that's the case, mdadm autoassembly might have gotten confused.

See if "cat /proc/mdstat" lists any md devices you didn't manually create, containing those disks. If so, fixing the mdadm.conf uuid, maybe running "update-initramfs -u -k `uname -r`" to update mdadm.conf to your boot ramdisk, then rebooting (or stopping the other devices and reassembling, but rebooting is probably quicker) might be enough to fix the problem.

---

### Post by mn_voyageur on 2011-04-15
lisahill,

All of the drives, according to Disk Utility, are fine.  The partitions are still there.  And the drives are "healthy."

dtfinch,

optuput of:cat /proc/mdstat
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sde1[0] sdc1[3]
      1953519872 blocks level 6, 64k chunk, algorithm 2 [4/2] [U__U]

      
I went to Disk Utility and tried to "Start RAID Array":
One or more block devices are holding /dev/sdc1

sdc appears to be okay.  I don't know what would be "blocking" or "holding."

MarkN

---

### Post by rubylaser on 2011-04-15
As dtfinch said, your UUID is incorrect in your /etc/mdadm/mdadm.conf file.  Autoassembly will not work properly if that file has the incorrect UUID.  The detail from the individual disks should match your mdadm.conf file like this...
```
root@fileserver:~# cat /etc/mdadm/mdadm.conf | grep UUID
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41

root@fileserver:~# mdadm -E /dev/sdc1 | grep UUID
UUID : d4e58776:640274d8:e368bf24:bd0fce41
```

You'll want to modify your /etc/mdadm/mdadm.conf to look like this...
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
ARRAY /dev/md0 level=raid6 num-devices=4 UUID=b40cc711:46ef5048:1178d5b1:7b4fd811

# This file was auto-generated on Mon, 21 Feb 2011 04:49:14 -0600
# by mkconf $Id$
```

You'll want to reboot for this to take effect.

---

### Post by mn_voyageur on 2011-04-16
Changing the UUID worked. No data was lost.  

During my search I noticed people were commenting about optimizing arrays of larger disks to reduce the overhead. (Disk error checking and such.)

Are there any posts that I should read about optimizing my array?

I appreciate all the help.

Thanks, 
MarkN

---

### Post by rubylaser on 2011-04-16
Error checking won't reduce overhead, but it will verify that your data is consistent.  Luckily, you don't have to setup anything to enable checking, it's enabled by default in the cron script that runs from /etc/cron.d/mdadm.  This is what it looks like...

```
#
# cron.d/mdadm -- schedules periodic redundancy checks of MD devices
#
# Copyright © martin f. krafft <madduck@madduck.net>
# distributed under the terms of the Artistic Licence 2.0
#

# By default, run at 00:57 on every Sunday, but do nothing unless the day of
# the month is less than or equal to 7. Thus, only run on the first Sunday of
# each month. crontab(5) sucks, unfortunately, in this regard; therefore this
# hack (see #380425).
57 0 * * 0 root if [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ]; then /usr/share/mdadm/checkarray --cron --all --idle --quiet; fi
```

The best way to reduce overhead is to choose a RAID type that doesn't need to do parity calculations like RAID 0,1, or 10. None of these really are efficient for large, inexpensive storage though.  I use RAID6 at home like you are with 8 disks, and unless the check action is happening, mdadm never uses a large portion of my system's resources.

Most people actually end up trying to use a little bit more resources to squeeze more performance out of mdadm, by tuning the readahead of the array, and setting blockdev parameters for the individual disks.

---

### Post by dtfinch on 2011-04-16
I wouldn't depend solely on built-in scripts like checkarray for monitoring.

As far as I know, at least in 10.04, the only result of the monthly checkarray, which checks every block of every disk in every raid, is that the number of mismatched blocks found can be read from /sys/block/md*/md/mismatch_cnt. Apart from that, it does not report errors or attempt to correct them, unless you've set up something to monitor the result. And a non-zero count doesn't necessarily mean corruption, if heavy writes took place during the check.

---

### Post by rubylaser on 2011-04-16
Good point, but daemonized mdadm will take care of alerting you of a failed disk, or anything wrong with the raid set.  Also, you can easily check more frequently if you want.  Also, the daemonized mdadm will alert you if a check returns errors, and a repair is necessary (at least with the 3.1.4 version of mdadm that I'm running).

---

### Post by mn_voyageur on 2011-04-17
mdadm - v2.6.7.1 - 15th October 2008

I was under the impression that Synaptic and Update Manager would take care of this.  

Is there a method of knowing when a new stable version is available?  (Short of visiting a web site.)

I appreciate all the help.

MarkN

---

### Post by rubylaser on 2011-04-17
Even though that version is really old, you don't need to upgrade, unless you need some of the newer functionality (you probably don't).  The main problem with the mdadm bundled with Ubuntu is that it doesn't require a MTA, so without email setup properly, you won't get alerts.
[http://packages.ubuntu.com/lucid/mdadm]("http://packages.ubuntu.com/lucid/mdadm")
I install postfix, and configure it to send email through Gmail's SMTP server. Finally, you need to make sure you have a line like this in your /etc/mdadm/mdadm.conf file.
```
echo "MAILADDR user@emailaddress.com" >> /etc/mdadm/mdadm.conf
```

You can verify that it works by having mdadm send you a test email.
```
mdadm --monitor -m user@gmail.com /dev/md0 -t
```

---

