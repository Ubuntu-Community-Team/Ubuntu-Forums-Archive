---
title: "/dev/md/0 has been started with 3 drives (out of 4)."
date: 2010-06-16
forum: Server Platforms
---

### Post by nrooy on 2010-06-16
I installed mdadm and created an array of 4 drives in RAID 5

the problem I'm having is after I rebooted my machine and tried to mount my array it forget's to add 1 drive to the array

**[nrooy@sniper-wolf ~]sudo mdadm --assemble --scan --verbose**
```

mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/block/251:1: Device or resource busy
mdadm: cannot open device /dev/root: Device or resource busy
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdb
mdadm: cannot open device /dev/sdc5: Device or resource busy
mdadm: no RAID superblock on /dev/sdc2
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sde1 is identified as a member of /dev/md/0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md/0, slot 1.
mdadm: no uptodate device for slot 0 of /dev/md/0
mdadm: added /dev/sdd1 to /dev/md/0 as 2
mdadm: added /dev/sde1 to /dev/md/0 as 3
mdadm: added /dev/sdb1 to /dev/md/0 as 1
mdadm: /dev/md/0 has been started with 3 drives (out of 4).
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdc2
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/block/9:0
mdadm: cannot open device /dev/block/251:1: Device or resource busy
mdadm: cannot open device /dev/root: Device or resource busy
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sdc5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdc2
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy

```**[nrooy@sniper-wolf ~]cat /proc/mdstat **
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[1] sde1[3] sdd1[2]
      4395404736 blocks level 5, 64k chunk, algorithm 2 [4/3] [_UUU]
      
md_d0 : inactive sda1[0](S)
      1465134912 blocks
       
unused devices: <none>

```**[nrooy@sniper-wolf ~]sudo mdadm --detail /dev/md0**
```

/dev/md0:
        Version : 00.90
  Creation Time : Thu Jun  3 19:29:34 2010
     Raid Level : raid5
     Array Size : 4395404736 (4191.78 GiB 4500.89 GB)
  Used Dev Size : 1465134912 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jun 16 19:01:39 2010
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 186b89c1:80289ee3:26df7fd9:3ab68377 (local to host sniper-wolf)
         Events : 0.4920

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```for some reason /dev/sda1 does not get added to /dev/md0 array

---

### Post by BobVila on 2010-06-17
Have you run smartctl tests on sda to see if it's reporting that it's healthy?

---

### Post by nrooy on 2010-06-20
Sorry for the long delay, but I was out this weekend.

the long test is running, but so far I don't see any errors
```

sudo smartctl --all /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD154UI
Serial Number:    S1XWJDWZ300684
Firmware Version: 1AG01118
User Capacity:    1,500,301,910,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Sun Jun 20 22:37:37 2010 CEST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection:          (18600) seconds.
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
recommended polling time:      (  32) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   071   071   011    Pre-fail  Always       -       9360
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       15
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       314
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       15
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   080   076   000    Old_age   Always       -       20 (Lifetime Min/Max 20/23)
194 Temperature_Celsius     0x0022   080   075   000    Old_age   Always       -       20 (Lifetime Min/Max 20/24)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       5609
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   253   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

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

---

### Post by nrooy on 2010-06-21
today I had to move My server, so I had to shut it down.
after starting up the server 3 drives are detected but I am unable to mount /dev/md0, I get the error;

**sudo mount /dev/md0 /data/**
```

mount: you must specify the filesystem type

```

**sudo mount /dev/md0 /data/ -t ext4**
```

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

does anyone know of a way I can get my 3TB of data back?

as soon as I can get to my data I'm dumping md.

---

### Post by bertmanphx on 2010-06-22
nrooy,
Please see the two links below.  Hopefully this helps.

bertmanphx

[http://ubuntuforums.org/archive/index.php/t-42087.html](http://ubuntuforums.org/archive/index.php/t-42087.html)

[http://www.linuxquestions.org/questions/linux-software-2/recovering-data-from-remaining-raid-1-disk-723225/](http://www.linuxquestions.org/questions/linux-software-2/recovering-data-from-remaining-raid-1-disk-723225/)

---

### Post by philsalkie on 2010-07-12
I've had almost this exact occurrence - just upgraded Karmic to Lucid, have an sda1 with /, and a raid of four 1TB drives as sdb1, sdc1, sdd1, and sde1 which should present as /dev/md0.
First reboot into Lucid was fine - next reboot had /dev/md0 show up as an inactive raid of sdb1, sdc1, and sdd1, and /dev/md/0 show up as an inactive raid of /dev/sde1.

mdadm --stop /dev/md0
mdadm --stop /dev/md/0
mdadm --assemble --scan

produced a warning that /dev/md0 already existed and that the array was being built on /dev/md/0.  

mdadm --stop /dev/md/0
rm /dev/md*
mdadm --assemble --scan

produced the same result - I wound up changing /etc/fstab to reference /dev/md/0 instead of /dev/md0, did an fsck which came back clean, and mounted the drive - no rebuild required, no data loss, a clear misbehavior of the software raid system on Lucid.  Circumstances are such that I have to wait for a quiet time to shutdown and see if the workaround survives the reboot.

I'm off to check to see if anybody's filed a bug against this...

Back!  Turns out there are several, but none in particular look _quite_ like this.  I went and checked my
/etc/mdadm/mdadm.conf
and found that the Lucid upgrade had changed that file like this:

#ARRAY /dev/md0 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1
ARRAY /dev/md0 devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1

for no apparent reason.  So, that's got to be the source of the problem - mdadm is looking to build an array using three parts of my array plus the boot/root partition, then finding /dev/sde1 floating all by itself, and makes another raid disk out of it.

I've changed that back, put back my /dev/md0 in /etc/fstab, and run
 
update-initramfs -k all -u

and will have to wait and see if it will all reboot properly now.

---

### Post by nrooy on 2010-07-13
Hi when I look at my '/etc/mdadm/mdadm.conf' it does not contain any drives.

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
MAILADDR REMOVED

# definitions of existing MD arrays

# This file was auto-generated on Thu, 03 Jun 2010 18:23:16 +0200
# by mkconf $Id$

```when I look at 'sudo blkid
```

/dev/sdc1: UUID="AzVxfg-Y0WH-Og1p-i6nw-MUID-g4q7-0ZQpaO" TYPE="LVM2_member" 
/dev/sdc5: UUID="ccff09d3-c265-4c4b-9d9d-dd527bd37993" TYPE="ext4" 
/dev/sdb1: UUID="186b89c1-8028-9ee3-26df-7fd93ab68377" TYPE="linux_raid_member" 
/dev/sdd1: UUID="186b89c1-8028-9ee3-26df-7fd93ab68377" TYPE="linux_raid_member" 
/dev/sde1: UUID="186b89c1-8028-9ee3-26df-7fd93ab68377" TYPE="linux_raid_member" 
/dev/mapper/sniper--wolf-root: UUID="5c56646c-1458-42ca-83cb-9cfaac398f14" TYPE="ext4" 
/dev/mapper/sniper--wolf-swap_1: UUID="bac56aba-252e-4032-b101-e1f331c5e1a5" TYPE="swap" 
/dev/md0: UUID="b9738884-21ab-413a-8247-0e03d2810ac1" TYPE="ext4" 

```I'm missing my /dev/sda1
So I think i'll remove the partition on my /dev/sda1 and re-add it

could you post your entire '/etc/mdadm/mdadm.conf' file?

Tnx

---

