---
title: "RAID5 disappeared"
date: 2012-09-09
forum: Server Platforms
---

### Post by The Frog on 2012-09-09
Hello,

I have the following problem, where I need advice and help.
Two years ago I set up a RAID 5 on four 1.5 TB drives, using only part of the harddisks. This worked without problems until earlier today. Suddenly the RAID had disappeared when I booted my server. I tried my Ubuntu and the Linux Mint partition and both show the same problem. The RAID partitions are sda5, sdb5, sdc5 & sdd5. No changes to the partitions were made for a long time. However, when I looked at the partitions today with gparted I noticed that the sdc5 lost its "raid" designation whereas the other three have retained it.

Here is the output of mdadm -E /dev/sd[abcd]
```
/dev/sda:
   MBR Magic : aa55
Partition[0] :     30716217 sectors at           63 (type 83)
Partition[1] :   2898527625 sectors at     31744440 (type 05)
Partition[2] :      1028160 sectors at     30716280 (type 83)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :     30716217 sectors at           63 (type 83)
Partition[1] :   2898531851 sectors at     31744501 (type 05)
Partition[2] :      1028160 sectors at     30716280 (type 83)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   2930272002 sectors at           63 (type 05)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   2930272002 sectors at           63 (type 05)

``````
/dev/sda5:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Sun Sep  9 13:28:41 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 2
Preferred Minor : 5

    Update Time : Sun Sep  9 13:36:26 2012
          State : active
 Active Devices : 0
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 2
       Checksum : 9dfc0081 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8        5        0      spare   /dev/sda5

   0     0       8        5        0      spare   /dev/sda5
   1     1       8       21        1      spare   /dev/sdb5
/dev/sdb5:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Sun Sep  9 13:28:41 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 2
Preferred Minor : 5

    Update Time : Sun Sep  9 13:36:26 2012
          State : active
 Active Devices : 0
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 2
       Checksum : 9dfc0093 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     1       8       21        1      spare   /dev/sdb5

   0     0       8        5        0      spare   /dev/sda5
   1     1       8       21        1      spare   /dev/sdb5
/dev/sdc5:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Sun Sep  9 13:41:38 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 2
Preferred Minor : 5

    Update Time : Sun Sep  9 13:58:39 2012
          State : active
 Active Devices : 0
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 2
       Checksum : 9dfc0921 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     1       8       37        1      spare   /dev/sdc5

   0     0       8       53        0      spare   /dev/sdd5
   1     1       8       37        1      spare   /dev/sdc5
/dev/sdd5:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Sun Sep  9 13:41:38 2012
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 2
Preferred Minor : 5

    Update Time : Sun Sep  9 13:58:39 2012
          State : active
 Active Devices : 0
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 2
       Checksum : 9dfc092f - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8       53        0      spare   /dev/sdd5

   0     0       8       53        0      spare   /dev/sdd5
   1     1       8       37        1      spare   /dev/sdc5

```cat /etc/mdadm/mdadm.conf
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
#ARRAY /dev/md0 UUID=00000000:00000000:00000000:00000000
#   spares=1
ARRAY /dev/md0 UUID=8a883c66:567bdb01:18a98a2e:85110466
ARRAY /dev/md5 UUID=f07da278:48145719:e368bf24:bd0fce41

# This file was auto-generated on Sat, 28 Apr 2012 09:56:43 +0200
# by mkconf $Id$

```What is wrong here? What can I do? Any help is appreciated.

---

### Post by SaturnusDJ on 2012-09-09
I don't know what command gave the first block of code.

What does ```
sfdisk -d /dev/sd[a-d]
``` gives?
I assume it will be similar, but just want to be sure.

---

### Post by The Frog on 2012-09-09
Thanks for the reply. The result for 
sfdisk -d /dev/sd[a-d] 
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 30716217, Id=83
/dev/sda2 : start= 31744440, size=2898527625, Id= 5
/dev/sda3 : start= 30716280, size=  1028160, Id=83, bootable
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 31744503, size=2827873692, Id=fd
/dev/sda6 : start=2859618258, size= 70653807, Id=83
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 30716217, Id=83
/dev/sdb2 : start= 31744501, size=2898531851, Id= 5
/dev/sdb3 : start= 30716280, size=  1028160, Id=83, bootable
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start= 31744503, size=2827873692, Id=fd
/dev/sdb6 : start=2859618304, size= 63324160, Id=83
/dev/sdb7 : start=2922944512, size=  7331840, Id=82
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=2930272002, Id= 5
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0
/dev/sdc5 : start=102398373, size=2827873692, Id=83
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
# partition table of /dev/sdd
unit: sectors

/dev/sdd1 : start=       63, size=2930272002, Id= 5
/dev/sdd2 : start=        0, size=        0, Id= 0
/dev/sdd3 : start=        0, size=        0, Id= 0
/dev/sdd4 : start=        0, size=        0, Id= 0
/dev/sdd5 : start=102398373, size=2827873692, Id=fd

```

---

### Post by rubylaser on 2012-09-09
None of your disks have a mdadm UUID in their superblock, so you are going to need to re-create the array with the --assume-clean flag to even have a chance of putting this back together. I've only seen this in the case of corruption, so I hope that's not the case with yours.  You have to reassemble in the same order with the same chunk size for this to work.

```
mdadm --create /dev/md5 --assume-clean --metadata=0.90 --level=5 --raid-devices=4 /dev/sd[abcd]5

```
This will use the default chunk size and the order that I assume you used when you created the array.  You have to use the assume clean flag, or you will case a resync a potentially lose all your data.

---

### Post by darkod on 2012-09-09
rubylaser, did you notice in the OP last post that sdc5 really doesn't have the raid flag? It's id=83, not id=fd for linux raid autodetect.

Would your command still work?

It's like the whole sdc5 partition is gone, I would like to see what parted says, Idon't understand the sfdisk results much.
sudo parted /dev/sdc print

Is the partition really missing or just lost the raid flag.

---

### Post by SaturnusDJ on 2012-09-09
All other partitions work like expected?


To fix the flag:
```

sfdisk -d /dev/sdc > sdc.sfdisk

```

Backup the file.

Edit it, and change "83" to "fd".

Upload the edited file:
```

sfdisk --force /dev/sdc < sdc.sfdisk

```

---

### Post by rubylaser on 2012-09-09
> **darkod said:**
> rubylaser, did you notice in the OP last post that sdc5 really doesn't have the raid flag? It's id=83, not id=fd for linux raid autodetect.

Would your command still work?

It's like the whole sdc5 partition is gone, I would like to see what parted says, Idon't understand the sfdisk results much.
sudo parted /dev/sdc print

Is the partition really missing or just lost the raid flag.

I did notice that the partition had a different label, but that would not stop mdadm from working.  It doesn't require the paritions to be labeled "fd" to be used in an array.  That label just makes the partition easier for the user to identify in cases like this.

---

### Post by The Frog on 2012-09-10
> **SaturnusDJ said:**
> All other partitions work like expected?
Yes.

[QUOTE=rubylaser]None of your disks have a mdadm UUID in their superblock, so you are  going to need to re-create the array with the --assume-clean flag to  even have a chance of putting this back together. I've only seen this in  the case of corruption, so I hope that's not the case with yours.  You  have to reassemble in the same order with the same chunk size for this  to work.[/QUOTE]
Would it be more prudent to use just the three that still have the flag (sda,sdb,sbd), assuming that sdc might have failed? Are there any clues in the old dmesg (or other) logs that may help?

Thanks for your help.

---

### Post by SaturnusDJ on 2012-09-10
```
smartctl -a /dev/sdc
```
Will make Rubylaser happy. :p

---

### Post by The Frog on 2012-09-10
> **SaturnusDJ said:**
> ```
smartctl -a /dev/sdc
```Will make Rubylaser happy. :p

```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-24-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F2 EG
Device Model:     SAMSUNG HD154UI
Serial Number:    S1XWJ90Z207367
LU WWN Device Id: 5 0024e9 201ed29a1
Firmware Version: 1AG01118
User Capacity:    1.500.301.910.016 bytes [1,50 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Mon Sep 10 17:34:27 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (19142) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (  33) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   071   071   011    Pre-fail  Always       -       9390
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       50
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   085   085   015    Pre-fail  Offline      -       20209
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       19328
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       50
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   069   064   000    Old_age   Always       -       31 (Min/Max 29/31)
194 Temperature_Celsius     0x0022   069   063   000    Old_age   Always       -       31 (Min/Max 29/31)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       4350
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     15970         -
# 2  Extended offline    Completed without error       00%      1199         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

---

### Post by rubylaser on 2012-09-10
You have a couple UDMA CRC errors on that disk which are typically related to a bad SATA cable, otherwise that disk looks healthy.  I would replace the cable on that drive with a new one. Then, you should be able to safely continue with my previous directions.

---

### Post by The Frog on 2012-09-11
> **rubylaser said:**
> You have a couple UDMA CRC errors on that disk which are typically related to a bad SATA cable, otherwise that disk looks healthy.  I would replace the cable on that drive with a new one. Then, you should be able to safely continue with my previous directions.
Ah, great info. I didn't think of that. Thanks very much. I will report back as soon as my aching back allows me to change the cable.

---

### Post by The Frog on 2012-09-13
> **rubylaser said:**
> None of your disks have a mdadm UUID in their superblock, so you are going to need to re-create the array with the --assume-clean flag to even have a chance of putting this back together. I've only seen this in the case of corruption, so I hope that's not the case with yours.  You have to reassemble in the same order with the same chunk size for this to work.

```
mdadm --create /dev/md5 --assume-clean --metadata=0.90 --level=5 --raid-devices=4 /dev/sd[abcd]5

```This will use the default chunk size and the order that I assume you used when you created the array.  You have to use the assume clean flag, or you will case a resync a potentially lose all your data.

When I try your suggestion (with the slight deviation to leave out sdc5 and consequently adjusting --raid-devices=3 since I fear that sdc5 might have dropped from the array prior to its failure) I get the following message:
```
mdadm: /dev/sda5 appears to contain an ext2fs file system
    size=-53156992K  mtime=Thu Jul  5 18:08:23 2012
mdadm: /dev/sda5 appears to be part of a raid array:
    level=-unknown- devices=0 ctime=Sun Sep  9 13:28:41 2012
mdadm: /dev/sdb5 appears to be part of a raid array:
    level=-unknown- devices=0 ctime=Sun Sep  9 13:28:41 2012
mdadm: /dev/sdd5 appears to contain an ext2fs file system
    size=-321592448K  mtime=Sun Jul 29 12:03:35 2029
mdadm: /dev/sdd5 appears to be part of a raid array:
    level=-unknown- devices=0 ctime=Sun Sep  9 13:41:38 2012

```Is this normal and shall I continue? I don't want to do anything silly. 
Or would it be safer to add all 4 disks?

---

### Post by rubylaser on 2012-09-13
No, mdadm is just telling you it can see the old superblock metadata from the now defunct array.  If you are concerned about //dev/sdc5, just leave it out for right now like this.

```
mdadm --create /dev/md5 --assume-clean --metadata=0.90 --level=5 --raid-devices=4 /dev/sda5 /dev/sdb5 missing /dev/sdd5
```

---

### Post by The Frog on 2012-09-13
Hmmm....

```

mount -r -t ext4 /dev/md5 /media/S_Tolot/
mount: wrong fs type, bad option, bad superblock on /dev/md5,
       missing codepage or helper program, or other error
       Manchmal liefert das Syslog wertvolle Informationen &#8211; versuchen
       Sie  dmesg | tail  oder so

dmesg:
[351196.481118] md/raid:md5: allocated 4280kB
[351196.482858] md/raid:md5: raid level 5 active with 3 out of 4 devices, algorithm 2
[351196.482869] RAID conf printout:
[351196.482873]  --- level:5 rd:4 wd:3
[351196.482879]  disk 0, o:1, dev:sda5
[351196.482884]  disk 1, o:1, dev:sdb5
[351196.482888]  disk 3, o:1, dev:sdd5
[351196.482979] md5: detected capacity change from 0 to 4343613358080
[351196.484256]  md5: unknown partition table
[352323.241324] EXT4-fs (md5): bad geometry: block count 1060452576 exceeds size of device (1060452480 blocks)
```Doesn't look good. Any ideas?

---

### Post by rubylaser on 2012-09-13
The only other thing you can try is to create with a different disk order.   The good thing is by using the --assume-clean flag, you aren't impacting your data at all, so you can try to recreate the array many times with no risk to your data.  But, as I said originally when I saw all of the info wiped out in your superblocks, it looks like something caused corruption and really messed up your array, and as result the filesystem.

---

### Post by The Frog on 2012-09-13
Researching the matter further I stumbled across some information where I'd like to hear your comments if that could resolve my problem.
I tried **fsck -fn /dev/md5** and got the result
```
fsck.ext4: Gruppen-Deskriptoren scheinen defekt zu sein... versuche es mit Backup-Blöcken...
fsck.ext4: Ungültige magische Zahl im Superblock when using the backup blocks
SuperBlock hat ein defektes Journal (Inode 8).

```which translates to 
Group descriptors look bad... trying backup blocks...
invalid magic number in superblock when using the backup blocks
Superblock has an invalid journal (inode8 )

In [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/) I found some info to this problem but it seems to me that that solution won't work here as the backup blocks are already tested by the command. Or will manually selecting a backup superblock be better?


**dumpe2fs /dev/md5** gives the following information
```
dumpe2fs 1.42 (29-Nov-2011)
Journal superblock magic number invalid!
Filesystem volume name:   <none>
Last mounted on:          /media/Tolot
Filesystem UUID:          54f6f5ba-65fa-480f-adb9-610d0f0f4bb1
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent fle
x_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              265117696
Block count:              1060452576
Reserved block count:     53022628
Free blocks:              67657230
Free inodes:              264971735
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      771
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Fri Jul 17 18:08:11 2009
Last mount time:          Thu Jul  5 18:08:23 2012
Last write time:          Thu Jul  5 18:08:23 2012
Mount count:              14
Maximum mount count:      29
Last checked:             Sun Apr 22 12:04:57 2012
Check interval:           15552000 (6 months)
Next check after:         Fri Oct 19 12:04:57 2012
Lifetime writes:          7402 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      292c7a0d-0211-4d83-95c7-90a3b14cc35e
Journal backup:           inode blocks

```Output of **mke2fs -n /dev/md5**
```
mke2fs 1.42 (29-Nov-2011)
Dateisystem-Label=
OS-Typ: Linux
Blockgröße=4096 (log=2)
Fragmentgröße=4096 (log=2)
Stride=128 Blöcke, Stripebreite=384 Blöcke
265117696 Inodes, 1060452480 Blöcke
53022624 Blöcke (5.00%) reserviert für den Superuser
Erster Datenblock=0
Maximale Dateisystem-Blöcke=4294967296
32363 Blockgruppen
32768 Blöcke pro Gruppe, 32768 Fragmente pro Gruppe
8192 Inodes pro Gruppe
Superblock-Sicherungskopien gespeichert in den Blöcken: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544

```

---

### Post by rubylaser on 2012-09-13
Unfortunately, it looks like your array is assembled correctly now, but your filesystem is screwed up.  If you can't mount with an alternate superblock, you're going to need the help of someone more intimately familiar with ext4 to help you out.  If I was faced with this situation, I'd be restoring from backup if I had one :(

---

### Post by SaturnusDJ on 2012-09-23
Maybe the Testdisk tool is usefull.

---

