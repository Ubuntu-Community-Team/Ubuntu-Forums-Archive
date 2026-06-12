---
title: "NAS raid5 restore/repair - SOS"
date: 2018-01-17
forum: Server Platforms
---

### Post by kmarat on 2018-01-17
[COLOR=#494949][FONT=&quot]Hello,[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot] [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]We have Iomega StorCenter px12-350r with 4 X 3TB drives on raid5[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]We've got one failed drive at first, the day after the second drive becames unrecognizable.[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]So their are 2 drives out of service now.

Please have a look at this that i managed to get from the server using Putty :

[/FONT][/COLOR]
root@iomega:/# cat /proc/mdstat
Personalities : [raid0] [raid1] [raid10] [raid6] [raid5] [raid4]
md1 : active raid5 sda2[0](F) sdc2[3] sdb2[2]
8727856128 blocks super 1.0 level 5, 512k chunk, algorithm 2 [4/2] [__UU]

md0 : active raid1 sdb1[0] sdc1[3]
20980816 blocks super 1.0 [4/2] [U__U]

 

 

root@iomega:/# fdisk -l | head -50

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/sda: 3000.5 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49f56d30

Device Boot Start End Blocks Id System
/dev/sda1 1 267350 2147483647+ ee EFI GPT

Disk /dev/sdb: 3000.5 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c37f46c

Device Boot Start End Blocks Id System
/dev/sdb1 1 267350 2147483647+ ee EFI GPT

Disk /dev/sdc: 3000.5 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dd6479e

Device Boot Start End Blocks Id System
/dev/sdc1 1 267350 2147483647+ ee EFI GPT

Disk /dev/sdd: 1031 MB, 1031798784 bytes
32 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdd1 1 980 972129 83 Linux

Disk /dev/md0: 21.4 GB, 21484355584 bytes
2 heads, 4 sectors/track, 5245204 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md1: 8937.3 GB, 8937324675072 bytes
2 heads, 4 sectors/track, -2113003264 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000
[COLOR=#494949][FONT=&quot]

[/FONT][/COLOR][COLOR=#494949][FONT=&quot]I'm tring to find any support help to proceed the restore or repair of drives...

Please advise any suggestions 

Thanks in advance!

[/FONT][/COLOR]

---

### Post by kmarat on 2018-01-17
[B]root@iomega:/# mdadm --detail /dev/md1
[/B]/dev/md1:
        Version : 1.00
  Creation Time : Tue Feb 28 02:56:39 2012
     Raid Level : raid5
     Array Size : 8727856128 (8323.53 GiB 8937.32 GB)
  Used Dev Size : 2909285376 (2774.51 GiB 2979.11 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Fri Jan 12 09:43:44 2018
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : px12-BNZUA4:1
           UUID : 9bb8f551:87a2fa74:32bdcaa0:8a503a74
         Events : 322914


    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       8       18        2      active sync   /dev/sdb2
       3       8       34        3      active sync   /dev/sdc2


       0       8        2        -      faulty spare   /dev/sda2

[/QUOTE]

---

### Post by kmarat on 2018-01-17
**root@iomega:/# mdadm -E /dev/sda2**
mdadm: No md superblock detected on /dev/sda2.

**root@iomega:/# mdadm -E /dev/sdd2**
mdadm: cannot open /dev/sdd2: No such device or address

**root@iomega:/# mdadm -E /dev/sdb2**
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 9bb8f551:87a2fa74:32bdcaa0:8a503a74
           Name : px12-BNZUA4:1
  Creation Time : Tue Feb 28 02:56:39 2012
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5818570976 (2774.51 GiB 2979.11 GB)
     Array Size : 17455712256 (8323.53 GiB 8937.32 GB)
  Used Dev Size : 5818570752 (2774.51 GiB 2979.11 GB)
   Super Offset : 5818571232 sectors
          State : clean
    Device UUID : 50eb5a67:92e51153:22ba8961:f9b7b2b2


    Update Time : Fri Jan 12 11:37:25 2018
       Checksum : d3dcb834 - correct
         Events : 322916


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : ..AA ('A' == active, '.' == missing)




**root@iomega:/# mdadm -E /dev/sdc2**
/dev/sdc2:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 9bb8f551:87a2fa74:32bdcaa0:8a503a74
           Name : px12-BNZUA4:1
  Creation Time : Tue Feb 28 02:56:39 2012
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5818570976 (2774.51 GiB 2979.11 GB)
     Array Size : 17455712256 (8323.53 GiB 8937.32 GB)
  Used Dev Size : 5818570752 (2774.51 GiB 2979.11 GB)
   Super Offset : 5818571232 sectors
          State : clean
    Device UUID : 8bedd61c:c9ecbdd9:e5472040:689440c5


    Update Time : Fri Jan 12 11:37:25 2018
       Checksum : 1292bda - correct
         Events : 322916


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : ..AA ('A' == active, '.' == missing)



**root@iomega:/# mdadm -E /dev/sde2**
mdadm: cannot open /dev/sde2: No such device or address

---

### Post by darkod on 2018-01-17
Hmmm... You have serious problem it seems.

First, sdd is not even detected any more. Not sure if we can consider it completely gone.

sdb and sdc seem to be fine, lets see if we can do anything with sda.

And also, don't use fdisk. Use parted because it supports gpt disks too.

```
sudo parted /dev/sda unit MiB print
sudo blkid
```

Lets see the output of that first before we go forward.

PS. I just saw you are running as root. In such case don't put the sudo in front, just run the commands...

---

### Post by kmarat on 2018-01-18
Thanks Darkod,

yes hope the seconde one is still ON.. 
here you are the results :
i will also insert smartctl results in a moment)
[B]
root@iomega:/# parted /dev/sda unit MiB print[/B]
Model: ATA HUA723030ALA640 (scsi)
Disk /dev/sda: 2861588MiB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
 
Number  Start     End         Size        File system  Name     Flags
 1      0.04MiB   20489MiB    20489MiB                 primary
 2      20489MiB  2861588MiB  2841099MiB               primary
 
**root@iomega:/# blkid**
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="e1ce7e2b-7eb1-4f79-abda-91094f05541a" TYPE="ext2"
/dev/loop2: LABEL="Compressed" TYPE="cramfs"
/dev/sda1: UUID="UvbdJp-vUQI-anKL-delx-nSbt-UAzK-3Vuw6E" TYPE="lvm2pv"
/dev/sda2: UUID="ep2qyG-tp9H-dPrL-hPwS-2yZS-Ccyk-sd3r2I" TYPE="lvm2pv"
/dev/sdb1: UUID="UvbdJp-vUQI-anKL-delx-nSbt-UAzK-3Vuw6E" TYPE="lvm2pv"
/dev/sdc1: UUID="UvbdJp-vUQI-anKL-delx-nSbt-UAzK-3Vuw6E" TYPE="lvm2pv"
/dev/sdc2: UUID="ep2qyG-tp9H-dPrL-hPwS-2yZS-Ccyk-sd3r2I" TYPE="lvm2pv"
/dev/sdd1: UUID="1a7ac3b1-a9a5-461b-85d2-bfc3e71c9395" TYPE="ext2"
/dev/md0: UUID="UvbdJp-vUQI-anKL-delx-nSbt-UAzK-3Vuw6E" TYPE="lvm2pv"
/dev/md1: UUID="ep2qyG-tp9H-dPrL-hPwS-2yZS-Ccyk-sd3r2I" TYPE="lvm2pv"
/dev/mapper/76b8b2fc_vg-lv5c072add: UUID="cd92bdf5-a585-4030-abba-75610b796f3f" TYPE="xfs"
/dev/mapper/1a70b391_vg-vol1: UUID="5989f98e-90a5-49c2-82b3-cd3804114bb1" TYPE="xfs"

---

### Post by darkod on 2018-01-18
Weird... This says LVM, not mdadm raid. On the other hand it does look like you have mdadm raid too.

Can you now post this:
```
cat /etc/mdadm/mdadm.conf
pvdisplay
lsblk
```

And please post the results inside CODE tags, they are easier to read...

---

### Post by kmarat on 2018-01-18
here it is 
```
smartctl -Hc /dev/sda2

```
```
**=== START OF INFORMATION SECTION ===**
Device Model:     HUA723030ALA640
Serial Number:    YHGV9YTA
Firmware Version: MKAOA690
User Capacity:    3,000,592,982,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Jan 18 12:55:11 2018 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
 
**=== START OF READ SMART DATA SECTION ===**
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.
 
**General SMART Values:**
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
 
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
 
Total time to complete Offline
data collection:                 (28081) seconds.
 
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
 
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
 
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
 
Short self-test routine
recommended polling time:        (   1) minutes.
 
Extended self-test routine
recommended polling time:        ( 255) minutes.
 
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
 
**SMART Attributes Data Structure revision number: 16**
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate       0x000b   059   059   016    Pre-fail  Always       -       579209661
  2 Throughput_Performance                  0x0005   134   134   054    Pre-fail  Offline      -       87
  3 Spin_Up_Time                    0x0007   124   124   024    Pre-fail  Always       -       620 (Average 621)
  4 Start_Stop_Count              0x0012   100   100   000    Old_age   Always       -       47
**  5 Reallocated_Sector_Ct      0x0033   001   001   005    Pre-fail  Always   FAILING_NOW 2001**
  7 Seek_Error_Rate                0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance                   0x0005   135   135   020    Pre-fail  Offline      -       26
  9 Power_On_Hours               0x0012   093   093   000    Old_age   Always       -       49390
 10 Spin_Retry_Count             0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count         0x0032   100   100   000    Old_age   Always       -       47
192 Power-Off_Retract_Count                0x0032   099   099   000    Old_age   Always       -       1553
193 Load_Cycle_Count           0x0012   099   099   000    Old_age   Always       -       1553
194 Temperature_Celsius       0x0002   171   171   000    Old_age   Always       -       35 (Min/Max 9/50)
196 Reallocated_Event_Count               0x0032   001   001   000    Old_age   Always       -       3421
197 Current_Pending_Sector                 0x0022   100   100   000    Old_age   Always       -       4
198 Offline_Uncorrectable     0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count                 0x000a   200   200   000    Old_age   Always       -       0
 
SMART Error Log Version: 1
ATA Error Count: 185 (device log contains only the most recent five errors)
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
 
Error 185 occurred at disk power-on lifetime: 49390 hours (2057 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 a8 40 b2 73 09
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 18 50 68 b9 73 40 00      00:32:33.060  READ FPDMA QUEUED
  60 a8 00 d8 b4 73 40 00      00:32:33.059  READ FPDMA QUEUED
  60 f8 48 e0 b3 73 40 00      00:32:31.142  READ FPDMA QUEUED
  60 f8 40 e8 b2 73 40 00      00:32:31.142  READ FPDMA QUEUED
  60 f8 38 f0 b1 73 40 00      00:32:31.142  READ FPDMA QUEUED
 
Error 184 occurred at disk power-on lifetime: 49390 hours (2057 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 70 f8 ea d0 0b
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 02 20 60 a3 50 40 00      00:31:32.486  WRITE FPDMA QUEUED
  60 58 18 60 ec d0 40 00      00:31:22.511  READ FPDMA QUEUED
  60 f8 10 68 eb d0 40 00      00:31:22.511  READ FPDMA QUEUED
  60 f0 08 78 ea d0 40 00      00:31:22.511  READ FPDMA QUEUED
  60 f8 00 80 e9 d0 40 00      00:31:22.511  READ FPDMA QUEUED
 
Error 183 occurred at disk power-on lifetime: 49389 hours (2057 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 b0 90 03 ab 0d
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 02 00 60 a3 50 40 00      00:28:13.488  WRITE FPDMA QUEUED
  60 d0 50 70 03 ab 40 00      00:28:06.379  READ FPDMA QUEUED
  60 f8 48 78 02 ab 40 00      00:28:06.379  READ FPDMA QUEUED
  60 f8 40 80 01 ab 40 00      00:28:06.379  READ FPDMA QUEUED
  60 20 38 60 71 b8 40 00      00:28:06.378  READ FPDMA QUEUED
 
Error 182 occurred at disk power-on lifetime: 49389 hours (2057 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 18 80 cd 85 03
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 28 f8 68 e0 85 40 00      00:23:51.862  READ FPDMA QUEUED
  60 f8 78 70 df 85 40 00      00:23:51.862  READ FPDMA QUEUED
  60 f8 70 78 de 85 40 00      00:23:51.862  READ FPDMA QUEUED
  60 f8 68 80 dd 85 40 00      00:23:51.862  READ FPDMA QUEUED
  60 20 60 60 dd 85 40 00      00:23:51.862  READ FPDMA QUEUED
 
Error 181 occurred at disk power-on lifetime: 49389 hours (2057 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 e8 80 bf 85 03
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 f0 b0 90 c8 85 40 00      00:22:30.182  READ FPDMA QUEUED
  60 20 a8 70 c8 85 40 00      00:22:30.182  READ FPDMA QUEUED
  60 00 a0 70 c7 85 40 00      00:22:30.182  READ FPDMA QUEUED
  60 f8 98 78 c6 85 40 00      00:22:30.181  READ FPDMA QUEUED
  60 f8 90 80 c5 85 40 00      00:22:30.181  READ FPDMA QUEUED
 
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

---

### Post by darkod on 2018-01-18
It definitely doesn't look good... Maybe best is to buy new 3TB disk and clone sda to it, hoping that you can save most of the data (there will probably be some small corrupted part).

I would still like to see the output of the commands in my previous post. But sda definitely looks like failing too, so you can't count too much on it.

---

### Post by kmarat on 2018-01-18
yes not good at all:
```

SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
...
...
5 Reallocated_Sector_Ct 0x0033 001 001 005 Pre-fail Always FAILING_NOW 2001
```

clone its a good idea, i will propose it and will provide you the rest of outputs tomorrow 


thnaks!

---

### Post by kmarat on 2018-01-19
ok, here your are, lsblk isnt on

```
[COLOR=#000000][FONT=&amp]root@iomega:/# lsblk-sh: lsblk: command not foundroot@iomega:/#[/FONT][/COLOR]
```

pvdisplay :
```
[COLOR=#000000][FONT=&amp]/dev/sda1: read failed after 0 of 2048 at 0: Input/output error[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  /dev/sda2: read failed after 0 of 2048 at 0: Input/output error[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  --- Physical volume ---[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PV Name               /dev/md1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  VG Name               76b8b2fc_vg[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PV Size               8.13 TiB / not usable 3.50 MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Allocatable           yes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PE Size               4.00 MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Total PE              2130823[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Free PE               850823[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Allocated PE          1280000[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PV UUID               ep2qyG-tp[/FONT][/COLOR][9H]("https://www.facebook.com/messages/t/aurelie.willems#")[COLOR=#000000][FONT=&amp]-dPrL-hPwS-2yZS-Ccyk-sd3r2I[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]  --- Physical volume ---[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PV Name               /dev/md0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  VG Name               1a70b391_vg[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PV Size               20.01 GiB / not usable 1.08 MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Allocatable           yes (but full)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PE Size               4.00 MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Total PE              5122[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Free PE               0[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Allocated PE          5122[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  PV UUID               UvbdJp-vUQI-anKL-delx-nSbt-UAzK-3Vuw6E[/FONT][/COLOR]
```


and cat /etc/mdadm/mdadm.conf
```
# mdadm.conf#
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


# This file was auto-generated on Wed, 11 Mar 2009 08:21:21 +0000
# by mkconf $Id$
root@iomega:/#
```

---

### Post by darkod on 2018-01-19
This doesn't look like standard mdadm raid5. Or at least the info is not in mdadm.conf. Since this is manufacturer firmware, not ubuntu OS, things are not like in standard linux OS.

In some way they might have used sda1/2 directly into the LVM, with /dev/md0 and /dev/md1 being something like intermediary devices. Or simply their config is not in mdadm.conf.

In any case, honestly I think you have very low chance to save the data. Cloning to new disk will work only if the old disk is sufficiently good enough. In your case it seems quite failed. To be able to clone it it still needs to be read, all of it (during the cloning). I don't think a disk with that many failures will manage that...

Out of interest, how long is sdd failed for? Raid5 is very fragile and you should replace a failed disk right away without risking another one to fail.

---

### Post by kmarat on 2018-01-19
on 21 dec.2017 first ERROR in NAS logs

yes it seems to be LVM but... i dont know
i'm getting too much confused with this:)) ok i have to "dot the i's " clearly on all of this and will back ! seems to me the seconde one is still recovable.. have to check it well

Thanks Darko!

---

### Post by darkod on 2018-01-19
Yeah, you need to look around for more specific commands for your device/manufacturer. Maybe even someone posted online notes how to try to save failed array. The whole setup is little strange but any manufacturer can do what they want and design their device as they wish.

---

### Post by kmarat on 2018-01-25
Hi Darkod,

we've saved up to 90% of datas so far.. by rebooting eahc time and copying as much as possible..
therefor we stoped investigating the issue and will pass to another backup system

thanks to you for your help!

---

### Post by darkod on 2018-01-25
OK. Please mark the thread as Solved if you don't need more help. You can do that in Thread Tools above the first post.

---

