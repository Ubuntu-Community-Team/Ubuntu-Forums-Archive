---
title: "RAID failure"
date: 2013-12-21
forum: Server Platforms
---

### Post by knight8524 on 2013-12-21
Okay, my basic command line knowledge and googling/searching the forums have resulted in no success, so now I ask for the collective wisdom of the forum to help repair my RAID.

Basic background:

I am running a media server with 4 HDDs. 
/dev/sda is 1TB drive with the linux install on it
/dev/sdb, /sdc and /sdd are 2TB drives that were up until about 1 hour ago a raid 5 array for photos, videos and so on.
This array was built with 3 new HDDs about 2 months ago, and it is run maybe for 4-5 hours every couple of days.

I was copying some stuff from a portable HDD to the array, started copying fine, but partway through came up with a Read only error. Brought up the command line to check the health of the array and was greated with [U__]

(Here is my first mistake) I rebooted the computer at this point and from this point on the array of course won't start. (Lesson learnt for next time)

Got the computer dback up and was greated by this:

```
sudo mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Wed Nov 13 16:38:59 2013
     Raid Level : raid5
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sun Dec 22 13:15:33 2013
          State : active, FAILED, Not Started 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 8e5ee34c:1a0ff976:b8d63fee:79dcf685
         Events : 122

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       0        0        2      removed

```

```

sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8e5ee34c:1a0ff976:b8d63fee:79dcf685
           Name : MediaServer:0  (local to host MediaServer)
  Creation Time : Wed Nov 13 16:38:59 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : dd41d054:dbe41263:961d1702:91703ade

    Update Time : Sun Dec 22 13:15:33 2013
       Checksum : 6649f97 - correct
         Events : 122

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.. ('A' == active, '.' == missing)

```

```
sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8e5ee34c:1a0ff976:b8d63fee:79dcf685
           Name : MediaServer:0  (local to host MediaServer)
  Creation Time : Wed Nov 13 16:38:59 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : bd31d8ac:3ab9d88b:3797e5f7:df0bc6a7

    Update Time : Sun Dec 22 13:03:42 2013
       Checksum : 469375dd - correct
         Events : 89

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
```

```
sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8e5ee34c:1a0ff976:b8d63fee:79dcf685
           Name : MediaServer:0  (local to host MediaServer)
  Creation Time : Wed Nov 13 16:38:59 2013
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 8eb5ff9c:6edf5f2c:d2e0271e:3e9d62a5

    Update Time : Sun Dec 22 13:06:05 2013
       Checksum : fb1dfb87 - correct
         Events : 116

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : A.A ('A' == active, '.' == missing)

```

fdisk -l gave me this:

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f384d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1936996351   968497152   83  Linux
/dev/sda2      1936998398  1953523711     8262657    5  Extended
Partition 2 does not start on a physical sector boundary.
/dev/sda5      1936998400  1953523711     8262656   82  Linux swap / Solaris

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0007fd53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907028991  1953513472   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a504c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008dab5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   83  Linux


```

and running:
```

sudo mdadm --assemble --scan
mdadm: /dev/md/0 assembled from 1 drive - not enough to start the array
```

Achieved nothing.

My gut feeling is that the data is still there and that it is unlikely that 2 drives have failed so soon after purchase. But I'm at a loss as to where to go next.

Your assistance is very much appreciated, because I'm stuck

---

### Post by CharlesA on 2013-12-21
Judging from the fdisk output, both those drives aren't even being seen by the OS. Have you booted into the BIOS and checked to see if they are being seen?

Reseat the power and data cables for them and see if they are seen.

Once you find out if those drives are being seen or not, we can go from there.

---

### Post by knight8524 on 2013-12-22
Ran up the BIOS,

Yep definitely getting 1x1TB drive and 3x2TB drives

---

### Post by CharlesA on 2013-12-22
Boot into the OS again and see if they are being seen.

```
sudo fdisk -l
```

```
sudo blkid -c /dev/null
```

---

### Post by knight8524 on 2013-12-22
As requested,

sudo fdisk -l

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000f384d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1936996351   968497152   83  Linux
/dev/sda2      1936998398  1953523711     8262657    5  Extended
Partition 2 does not start on a physical sector boundary.
/dev/sda5      1936998400  1953523711     8262656   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008dab5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a504c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0007fd53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907028991  1953513472   83  Linux
```

and of course:

sudo blkid -c /dev/null

```
/dev/sda1: UUID="15a6baa5-9692-4f56-8654-e715d4d1d4d4" TYPE="ext4" 
/dev/sda5: UUID="dea126ee-1593-4fb1-99bf-8a3aad94c1aa" TYPE="swap" 
/dev/sdb1: UUID="8e5ee34c-1a0f-f976-b8d6-3fee79dcf685" UUID_SUB="dd41d054-dbe4-1263-961d-170291703ade" LABEL="MediaServer:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="8e5ee34c-1a0f-f976-b8d6-3fee79dcf685" UUID_SUB="bd31d8ac-3ab9-d88b-3797-e5f7df0bc6a7" LABEL="MediaServer:0" TYPE="linux_raid_member" 
/dev/sdd1: UUID="8e5ee34c-1a0f-f976-b8d6-3fee79dcf685" UUID_SUB="8eb5ff9c-6edf-5f2c-d2e0-271e3e9d62a5" LABEL="MediaServer:0" TYPE="linux_raid_member" 
```

thpughts? (I'm also interested in what you saw that made you think it wasn't seeing the HDDs to start with)

---

### Post by CharlesA on 2013-12-22
The drives weren't listed in fdisk and mdadm showed them as being 'removed.'

Is that still the case?

---

### Post by rubylaser on 2013-12-22
Have you tried to stop the array and force assemble?
```

sudo -i
mdadm --stop /dev/md127
mdadm --assemble --force /dev/md0 /dev/sd[bcd]1

```

Note, this will set the array up as /dev/md0 instead of /dev/md127.  What are the contents of your mdadm.conf file?
```

cat /etc/mdadm/mdadm.conf

```

---

### Post by knight8524 on 2013-12-24
Sorry, with the lead up to Christmas I haven't been able to action any of the suggestions. In answer to rubylaser's question, no I haven't tried that. I will make an attempt to do that on Boxing Day, and I will also post the answers to the other two questions. Thankyou for your help thus far everyone.

---

### Post by knight8524 on 2013-12-26
/etc/mdadm/mdadm.conf

```
MAILADDR root@localhost
ARRAY /dev/md/0 metadata=1.2 name=MediaServer:0 UUID=8e5ee34c:1a0ff976:b8d63fee:79dcf685
```

sudo mdadm --detail /dev/md127

```
        Version : 1.2
  Creation Time : Wed Nov 13 16:38:59 2013
     Raid Level : raid5
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sun Dec 22 13:15:33 2013
          State : active, FAILED, Not Started 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 8e5ee34c:1a0ff976:b8d63fee:79dcf685
         Events : 122

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       0        0        2      removed
```

I'll try doing the stop and force assemble now, I'll post the results in a moment

---

### Post by knight8524 on 2013-12-26
doing the force assemble produced this result:

```
david@MediaServer:~$ sudo mdadm --stop /dev/md127
mdadm: stopped /dev/md127
david@MediaServer:~$ sudo mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: forcing event count in /dev/sdd1(2) from 116 upto 122
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdd1
mdadm: Marking array /dev/md0 as 'clean'
mdadm: /dev/md0 has been started with 2 drives (out of 3).
```

so I take it thats a good thing, now mdadm -- detail shows this:

```

david@MediaServer:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Nov 13 16:38:59 2013
     Raid Level : raid5
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sun Dec 22 13:15:33 2013
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 8e5ee34c:1a0ff976:b8d63fee:79dcf685
         Events : 122

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       3       8       49        2      active sync   /dev/sdd1
```

and for what its worth this is mdadm.conf post the force assemble

```
MAILADDR root@localhost
ARRAY /dev/md/0 metadata=1.2 name=MediaServer:0 UUID=8e5ee34c:1a0ff976:b8d63fee:79dcf685
```

I've also had the array show up as a mount point, and can access the files, so I assume my next step is to tell the array to assume sdc1 is degraded and rebuild that drive, or do I just force add it?

---

### Post by CharlesA on 2013-12-26
Can you post the output of this again?
```
sudo blkid -c /dev/null
```

I would suggest letting it rebuild, but if the drives keep dropping off, I would look into replacing the drives.

---

### Post by knight8524 on 2013-12-26
```
/dev/sda1: UUID="15a6baa5-9692-4f56-8654-e715d4d1d4d4" TYPE="ext4" 
/dev/sda5: UUID="dea126ee-1593-4fb1-99bf-8a3aad94c1aa" TYPE="swap" 
/dev/sdb1: UUID="8e5ee34c-1a0f-f976-b8d6-3fee79dcf685" UUID_SUB="dd41d054-dbe4-1263-961d-170291703ade" LABEL="MediaServer:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="8e5ee34c-1a0f-f976-b8d6-3fee79dcf685" UUID_SUB="bd31d8ac-3ab9-d88b-3797-e5f7df0bc6a7" LABEL="MediaServer:0" TYPE="linux_raid_member" 
/dev/sdd1: UUID="8e5ee34c-1a0f-f976-b8d6-3fee79dcf685" UUID_SUB="8eb5ff9c-6edf-5f2c-d2e0-271e3e9d62a5" LABEL="MediaServer:0" TYPE="linux_raid_member" 
/dev/md0p1: UUID="082e57b7-e658-4922-b7c7-46f15981e9b6" TYPE="ext4"
```

I also tried to --re-add sdc1 to the array but got the response "mdadm: --re-add for /dev/sdc to /dev/md0 is not possible"

Looking at the examines for all the drives, sdc1 thinks it is part of the array, but nothing else does....

And I really hope I shouldn't have to replace the drives, I only bought them a month ago

---

### Post by CharlesA on 2013-12-26
You might have to zero out the super blocks on sdc1 and add it to the array again, but I think you should wait to hear back from rubylaser before doing anything.

---

### Post by rubylaser on 2013-12-26
You should do as CharlesA suggests.  Zero /dev/sdc1's superblock, and then add it to the array.

```

mdadm --zero-superblock /dev/sdc1
mdadm --manage /dev/md0 --add /dev/sdc1

```

You can view the sync process like this.
```

watch cat /proc/mdstat

```

Also, this is normally an indicator that a disk is failing.  What's the SMART data look like on /dev/sdc?
```
apt-get install smartmontools
smartctl -a /dev/sdc
```

---

### Post by knight8524 on 2013-12-30
Well thankyou both for your help, the raid is back in one piece and is working as expected and has done so for the past few days.

As requested here is the smartctrl output.

```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.8.0-29-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA DT01ACA200
Serial Number:    83CWVNUKS
LU WWN Device Id: 5 000039 ff3dac1a5
Firmware Version: MX4OABB0
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Dec 31 08:55:18 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (15396) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   140   140   054    Pre-fail  Offline      -       68
  3 Spin_Up_Time            0x0007   131   131   024    Pre-fail  Always       -       292 (Average 286)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       32
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   124   124   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       102
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       32
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       32
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       32
194 Temperature_Celsius     0x0002   250   250   000    Old_age   Always       -       24 (Min/Max 19/55)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       5

SMART Error Log Version: 1
ATA Error Count: 5
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 5 occurred at disk power-on lifetime: 97 hours (4 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 42 ee b0 2b 0b  Error: ICRC, ABRT at LBA = 0x0b2bb0ee = 187412718

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 00 30 b0 2b 40 00      19:23:24.163  WRITE FPDMA QUEUED
  61 00 00 30 ac 2b 40 00      19:23:24.158  WRITE FPDMA QUEUED
  61 00 00 30 a8 2b 40 00      19:23:24.150  WRITE FPDMA QUEUED
  61 00 00 30 a4 2b 40 00      19:23:24.146  WRITE FPDMA QUEUED
  61 00 00 30 a0 2b 40 00      19:23:24.138  WRITE FPDMA QUEUED

Error 4 occurred at disk power-on lifetime: 95 hours (3 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 c2 a6 9c dc 01  Error: ICRC, ABRT at LBA = 0x01dc9ca6 = 31235238

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 00 68 9b dc 40 00      17:49:36.997  WRITE FPDMA QUEUED
  61 00 00 68 97 dc 40 00      17:49:36.990  WRITE FPDMA QUEUED
  61 00 00 68 93 dc 40 00      17:49:36.985  WRITE FPDMA QUEUED
  61 00 00 68 8f dc 40 00      17:49:36.978  WRITE FPDMA QUEUED
  61 00 00 68 8b dc 40 00      17:49:36.973  WRITE FPDMA QUEUED

Error 3 occurred at disk power-on lifetime: 95 hours (3 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 97 b9 56 6f 0a  Error: ICRC, ABRT at LBA = 0x0a6f56b9 = 175068857

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 97 b9 56 6f 4a ff      17:37:27.445  WRITE FPDMA QUEUED
  61 00 00 50 53 6f 40 00      17:37:27.434  WRITE FPDMA QUEUED
  61 00 00 50 4f 6f 40 00      17:37:27.426  WRITE FPDMA QUEUED
  61 00 00 50 4b 6f 40 00      17:37:27.422  WRITE FPDMA QUEUED
  61 00 00 50 47 6f 40 00      17:37:27.414  WRITE FPDMA QUEUED

Error 2 occurred at disk power-on lifetime: 95 hours (3 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 1f aa 39 08  Error: ICRC, ABRT at LBA = 0x0839aa1f = 137996831

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 00 20 a7 39 40 00      17:07:39.791  WRITE FPDMA QUEUED
  61 00 00 20 a3 39 40 00      17:07:39.787  WRITE FPDMA QUEUED
  61 00 00 20 9f 39 40 00      17:07:39.779  WRITE FPDMA QUEUED
  61 00 00 20 9b 39 40 00      17:07:39.775  WRITE FPDMA QUEUED
  61 00 00 20 97 39 40 00      17:07:39.768  WRITE FPDMA QUEUED

Error 1 occurred at disk power-on lifetime: 93 hours (3 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 f1 57 12 7d 05  Error: ICRC, ABRT at LBA = 0x057d1257 = 92082775

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 00 48 0f 7d 40 00      14:52:21.139  WRITE FPDMA QUEUED
  61 00 00 48 0b 7d 40 00      14:52:21.131  WRITE FPDMA QUEUED
  61 00 00 48 07 7d 40 00      14:52:21.127  WRITE FPDMA QUEUED
  61 00 00 48 03 7d 40 00      14:52:21.119  WRITE FPDMA QUEUED
  61 00 00 48 ff 7c 40 00      14:52:21.115  WRITE FPDMA QUEUED

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

I'll wait for your advice over this drive, but for arguements sake here are the other two drives in the array as well

SDB
```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.8.0-29-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA DT01ACA200
Serial Number:    83CWVNPKS
LU WWN Device Id: 5 000039 ff3dac1a1
Firmware Version: MX4OABB0
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Dec 31 08:58:20 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (15013) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 251) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   140   140   054    Pre-fail  Offline      -       68
  3 Spin_Up_Time            0x0007   132   132   024    Pre-fail  Always       -       286 (Average 286)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       32
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   124   124   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       102
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       32
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       32
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       32
194 Temperature_Celsius     0x0002   230   230   000    Old_age   Always       -       26 (Min/Max 19/58)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

SDD
```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.8.0-29-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA DT01ACA200
Serial Number:    83CWXZEKS
LU WWN Device Id: 5 000039 ff3daca51
Firmware Version: MX4OABB0
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Dec 31 08:59:33 2013 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (14726) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 246) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   140   140   054    Pre-fail  Offline      -       68
  3 Spin_Up_Time            0x0007   134   134   024    Pre-fail  Always       -       286 (Average 278)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       32
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   124   124   020    Pre-fail  Offline      -       33
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       102
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       32
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       32
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       32
194 Temperature_Celsius     0x0002   230   230   000    Old_age   Always       -       26 (Min/Max 19/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

I havn't yet tried to do a large data copy to the array, as that was what 
I was doing when the array failed. If you can't shed any light on it, I'll just go ahead and continue the copy.

Again, thankyou so much for your help

---

### Post by rubylaser on 2013-12-30
Gad you got it working.  The one thing that pops out is your [COLOR=#000000][FONT=Ubuntu Mono]UDMA_CRC_Error_Count [/FONT][/COLOR]on the first disk.  That should be zero and usually points to a bad SATA cable or SATA head on the motherboard.  I would swap the cable for that disk. Other than that your disks look okay, but it doesn't look like they have ever had a short or long test run on them.  I would look into setting up [SMART to monitor]("http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing") your disks in the future, and [setup email]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp") so that mdadm can email you in the future. Those two tutorials are how I do it.

---

### Post by CharlesA on 2013-12-30
> **rubylaser said:**
> Gad you got it working.  The one thing that pops out is your [COLOR=#000000][FONT=Ubuntu Mono]UDMA_CRC_Error_Count [/FONT][/COLOR]on the first disk.  That should be zero and usually points to a bad SATA cable or SATA head on the motherboard.  I would swap the cable for that disk. Other than that your disks look okay, but it doesn't look like they have ever had a short or long test run on them.  I would look into setting up [SMART to monitor]("http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing") your disks in the future, and [setup email]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp") so that mdadm can email you in the future. Those two tutorials are how I do it.

Just giving a +1 to those two tutorials. I had a nasty time trying to get smartd to detect the drives in my MegaRAID setup, but that was due to the version of smartmontools in the repos, so I just run everything manually via cron.

---

### Post by knight8524 on 2014-02-08
So it turns out that everything is not solved. 

Leave the server running for a while, no issues. Decide that eventually it is stable enough to try adding more files, so select everything that didn't get over to the array the first time and select copy.

To start with all good, everything copies fine, go away to make dinner and suddenly i have an email from my server telling me its fallen in a great huge heap again.

Followed the same steps, resynced the array and it was all good, files still intact and so on.

Is there a bug with the raid array software I don't know about to do with large files, or is there something I am doing wrong. 

I'm about to try copy some stuff over again, but in smaller chuncks and I'm going to copy it from the local hardrive to the array rather than the USB harddrive to the array to see if that makes a difference, but if anyone can think of anything else to try, I'm all ears.

---

### Post by CharlesA on 2014-02-08
Unsure. Are you copying files across the network or locally?

---

### Post by knight8524 on 2014-02-09
> **CharlesA said:**
> Unsure. Are you copying files across the network or locally?

All the copying is done locally. 

To add to the confusion I've got another report.
Copied about 60gb of files in 3 groups of about 20gb last night, all good. Used the server for several hours last night without issue. 
Used it this morning to watch the media on my tablet via plex, no issues. 
Download finished this morning as I was walking out of the door, and my tablet email alert went off with an email from the server indicating a fail event and then almost straight away a second email for a fail spare event (Note I do not actually have a spare). 

I'm decidedly confused. My understanding is that ubuntu software raid should be more reliable than this.

---

### Post by CharlesA on 2014-02-09
I don't get it. Have you tried the same drives in a different machine? Mdadm should detect them if you do a scan.

---

### Post by knight8524 on 2014-02-09
No, I don't have a spare ubuntu machine to test them in. However I wonder if you are on the right track with a hardware issue. It seems to be the center drive sdc1 that seems to fail first, it has gone down every time the array has crashed and it was the one that died this time. 

Is there an easy way to determine which port of  the motherboard sdc is plugged into?

EDIT:

So just to keep you updated on the process of the array, stopped, unmounted and tried to reassemble, it started with two disks....not quite what I was hoping for.
Did a manage md0 --add sdc1 and success, it is now in the process of readding the device to the array.

```
Every 2.0s: cat /proc/mdstat                                              Mon Feb 10 17:49:44 2014

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[4] sdb1[0] sdd1[3]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      [>....................]  recovery =  1.3% (25940492/1953381888) finish=234.9min speed=136720
K/sec

unused devices: <none>
```

I'll try swapping the cables around once the array is rebuilt and see what happens

---

### Post by CharlesA on 2014-02-10
You could try getting the serial number and comparing it to the physical drive.

See here:
[http://www.cyberciti.biz/faq/linux-getting-scsi-ide-harddisk-information/](http://www.cyberciti.biz/faq/linux-getting-scsi-ide-harddisk-information/)

---

### Post by knight8524 on 2014-02-10
Well got the serial number and changed things around....all to no success, unfortunatly the array failed again this morning, badly.

Both sdc and sdd failed out of the array and no matter what I tried, i was completly unable to rebuild the array.

I've zeroed everything, and am now followinbg rubylasers setup tutorial to the letter. Fortunatly all important stuff (photos and so forth) are backed up on other machines. Most of the media is gone, but thats an annoyance not a serious problem. 

Rang the people who run the computer store I got the HDD from originally, since it is greater than 7 days, they won't just swap it for a new one, it has to go off to the manufacturer for testing, which given the numbers it is showing will probably say its fine. For the moment I'm rebuilding it with what I have on hand, and we will see if it is any more stable after this.

Thanks for the help thus far and I'll keep you informed of my progress

---

### Post by CharlesA on 2014-02-10
Good luck. For what it is worth, I used Ruby's guide when I built the array in my backup server, so it should work fine.

I'm not really sure if the problem is the drives or something else, which was why I suggested trying another machine.

Hopefully the new build won't give you any problems.

---

### Post by rubylaser on 2014-02-10
Two things before wasting any more of your time:
[LIST=1]
[*]Replace the SATA cable on the drive with the serial of [COLOR=#000000][FONT=Ubuntu Mono]83CWVNUKS[/FONT][/COLOR].  Based on your previous SMART report, you have UDMA_CRC_ERRORS which is almost always a bad SATA cable, or unlikely, a bad SATA head on your motherboard.  Try to replace the cable on that drive with a known good one.
[*] Before you rebuild the array again, I would try to stress test each disk, so you can confirm that they are all working and that SMART values remain the same throughout the tests. It takes a long time on large disks, but it's worth it to weed out any problems upfront.  I have a modified version of UnRAID's preclear script that does a good job of testing disks.  You can view it [here]("http://zackreed.me/articles/80-new-disk-stress-test").
[/LIST]

---

### Post by knight8524 on 2014-04-12
And I'm back again.

For an update of where I currently am:
I rebuilt the array before rubylaser posted, and as a result DIDN'T run the stress test.
I did however get three new SATA cables and replaced all of the cables.
I then commenced coping my backups (patchy as they are but at least I've got something :P) something in the order of 900gb worth of videos/photos/music/etc

Throughout the day I switched the monitor on and off a few times, and it seemed to be going well. Went to bed and got up the next morning to find that at about 90% completed (give or take) of the copy the raid array had failed out in the same way as before.

I got rather frustrated at this point so wiped the data and deleted the array, and commenced the stress test from Rubylaser on all 3 of the drives. 30 hours later the results are in....and all three of the drives passed.....I decided to check if this was a error and ran it again....all three of the drives passed again (I've included the emails with the results below, just for completness)

I'm now rather confused, why would it fail coping and then pass the stress tests. Is there a known issue with coping large ammounts of data? My current plan is to build the array and then copy the files in smaller chunks (ie: it got past 500gb so I'll try coping the data in 500gb chunks - To be honest, I don't expect this to make a difference)

I'm going to commence the array build as soon as I hit post on this post, but if you have any more ideas (I'm wondering if the issue is an intermitant issue with the MOBO itself and that it might be worth replacing that) I'm all ears.

Thanks for the help thus far, you have stopped me throwing the server through a window :P

[EDIT: The array is currently rebuilding, we will see how it goes]

---

### Post by frostschutz on 2014-04-12
> **knight8524 said:**
> I'm now rather confused, why would it fail coping and then pass the stress tests.

Well, why did it fail? When something like this happens, the kernel is usually verbose about it. So check your kernel logs and dmesg. Without logs you're left with blind guesswork and that's not particularly useful.

---

### Post by knight8524 on 2014-04-13
As requested my kernal logs have been uploaded [here]("https://www.dropbox.com/s/d5xqzmelane1cx4/MediaSeverLog.pdf") (on dropbox due size)

I believe the failure occured around 2308 April 5 as the logs indicate that the array was remounted as a read only file system at that point, and there are a lot of I/O failures at that point.

I don't know specifically what I'm looking for so I havn't been able to find the exact line that explains why it failed - I don't think my skills give me much more than blind guesswork even with the logs, but thankyou for everyone's help so far, I have learnt a lot through this thread, even if we havn't been able to solve the problem yet.

---

### Post by frostschutz on 2014-04-13
My guess is that you have a bad SATA controller on that board, or a bad PSU, or bad cables or something. You can't get reliable storage with all those link resets going on. There should be no link resets in normal operation...

---

### Post by knight8524 on 2014-04-15
Is there any way to narrow this down any further?

I've already replaced the SATA cables so unless I'm very very unlucky I think I can rule them out. Do I just bite the bullet and buy a new motherboard or can I narrow it down to definetly be the motherboard, etc. Or can I make the assumption that it is the motherboard due to ata1, 2, 3 and 4 all reporting errors and hard resetting the SATA link? (I'm making the assumption that if it was the sata controller on the hard drive it would only be ata2 (for example) with all the errors - or am I completly wrong?)

---

### Post by CharlesA on 2014-04-15
Got another machine you can put the drives in? Swap it out and see if it still throws errors. I don't think there is going to be another way to test it without replacing your existing hardware.

---

### Post by frostschutz on 2014-04-16
Another machine would rule out the drives as the culprit. But that's unlikely in the first place, drive failure just doesn't look like this normally.

Before the board, I'd try another PSU first if you have one available (even temporarily from another machine). Bad PSU and other electrical problems (like something in the case shorting the back of the board, or an odd pci card) can cause all sorts of trouble. Also if you have any cheap power adapter cables (like a Y-Cable to get more sata power ports). You should also always try the very latest kernel, just in case there was an odd driver issue at some point.

If nothing helps, it's the board or cpu...

---

