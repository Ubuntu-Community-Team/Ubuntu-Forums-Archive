---
title: "RAID Healthcheck - anyone care to offer an opinion on results?"
date: 2013-12-02
forum: Server Platforms
---

### Post by Chris of Arabia on 2013-12-02
Recently, my home server has been playing up a little and has shut itself down unexpectedly. It has subsequently had difficulties re-booting, but has got there eventually, though not before displaying some boot sequence messages that indicate all is not well (link degraded?).

I've just run a couple of checks to try and understand what the health state of the RAID1 array is, with the following results.

> [EMAIL="chris@PIGLET2:~$"]chris@PIGLET2:~$[/EMAIL] sudo cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda5[1]
      8383424 blocks super 1.2 [2/1] [_U]
md0 : active raid1 sda1[1]
      304049984 blocks super 1.2 [2/1] [_U]
unused devices: <none>


> [EMAIL="chris@PIGLET2:~$"]chris@PIGLET2:~$[/EMAIL] sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sat Jul 27 14:24:22 2013
     Raid Level : raid1
     Array Size : 8383424 (8.00 GiB 8.58 GB)
  Used Dev Size : 8383424 (8.00 GiB 8.58 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent
    Update Time : Sun Dec  1 00:57:06 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
           Name : PIGLET2:1  (local to host PIGLET2)
           UUID : dc4cf14b:c9cadd29:5759e0bf:42d05c49
         Events : 134
    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        5        1      active sync   /dev/sda5


As I'm not overly familiar with the output of these two commands, could someone confirm what I'm seeing for me? Do I have a failed disk in the array here, and if so, is there anything I should try next to confirm the problem? Do I have any options to recover the disk, other than replacing it?

---

### Post by rubylaser on 2013-12-02
You have a degraded array. In the case of a RAID1 array, that means that one disk is not present or has been removed for some reason.  Can you install smartmontools and then post the output of these commands?
```

sudo -i
apt-get update && apt-get install smartmontools -y

```

```

smartctl -a /dev/sda
smartctl -a /dev/sdb

```

```

fdisk -l

```

```

dmesg | grep sdb

```

---

### Post by Chris of Arabia on 2013-12-02
Thanks for the help. Output as follows:

```
root@PIGLET2:~# apt-get update && apt-get install smartmontools -y
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en_GB
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgcr-3-1 linux-image-3.8.0-29-generic linux-image-extra-3.8.0-29-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  heirloom-mailx
Suggested packages:
  exim4 mail-transport-agent gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed
  heirloom-mailx smartmontools
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 868 kB of archives.
After this operation, 2,167 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/universe heirloom-mailx amd64 12.5-2 [247 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/main smartmontools amd64 6.1+svn3812-1 [621 kB]
Fetched 868 kB in 2s (306 kB/s)
Selecting previously unselected package heirloom-mailx.
(Reading database ... 194111 files and directories currently installed.)
Unpacking heirloom-mailx (from .../heirloom-mailx_12.5-2_amd64.deb) ...
Selecting previously unselected package smartmontools.
Unpacking smartmontools (from .../smartmontools_6.1+svn3812-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up heirloom-mailx (12.5-2) ...
update-alternatives: using /usr/bin/heirloom-mailx to provide /usr/bin/mailx (mailx) in auto mode
Setting up smartmontools (6.1+svn3812-1) ...
Processing triggers for ureadahead ...
```

---

### Post by Chris of Arabia on 2013-12-02
Next...
```
root@PIGLET2:~# smartctl -a /dev/sda
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-13-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD3200AAKS-00YGA0
Serial Number:    WD-WCASF0012463
LU WWN Device Id: 5 0014ee 155e78a05
Firmware Version: 12.01C02
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Mon Dec  2 18:56:11 2013 AST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                ( 8760) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 104) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   179   173   021    Pre-fail  Always       -       6041
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       111
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   067   067   000    Old_age   Always       -       24504
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       110
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       73
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       111
194 Temperature_Celsius     0x0022   115   099   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0
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

### Post by Chris of Arabia on 2013-12-02
...
```
[EMAIL="root@PIGLET2"]root@PIGLET2[/EMAIL]:~# smartctl -a /dev/sdb
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-13-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")
Smartctl open device: /dev/sdb failed: No such device

```

---

### Post by Chris of Arabia on 2013-12-02
...
```
[EMAIL="root@PIGLET2"]root@PIGLET2[/EMAIL]:~# fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050f22
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   608364543   304181248   fd  Linux RAID autodetect
/dev/sda2       608366590   625141759     8387585    5  Extended
/dev/sda5       608366592   625141759     8387584   fd  Linux RAID autodetect
Disk /dev/md0: 311.3 GB, 311347183616 bytes
2 heads, 4 sectors/track, 76012496 cylinders, total 608099968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/md1: 8584 MB, 8584626176 bytes
2 heads, 4 sectors/track, 2095856 cylinders, total 16766848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Disk /dev/md1 doesn't contain a valid partition table

```

---

### Post by Chris of Arabia on 2013-12-02
This one appeared to do nothing and just dropped me onto the next cmd prompt

> [EMAIL="root@PIGLET2"]root@PIGLET2[/EMAIL]:~# dmesg | grep sdb
[EMAIL="root@PIGLET2"]root@PIGLET2[/EMAIL]:~#

---

### Post by rubylaser on 2013-12-02
Based off your fdisk output, it appears that only one hard drive is recognized by Ubuntu.  I would power of your machine, and try to reseat the cables to both hard drives and try that again.  If this doesn't correct the "missing" drive, it is likely that the drive has failed and needs to be replaced.  Also, for future reference, setting up smartctl to monitor your drive health, and mdadm to email you in the event of a hardware failure should be two other things you setup as well.  I have links in my signature that cover all of these topics for mdadm.

---

### Post by Chris of Arabia on 2013-12-02
OK, thanks. I crack it open and see what occurs. :)

---

### Post by Chris of Arabia on 2013-12-03
Well there were no issues with the connections. And I've identified the problem disk, which I've now disconnected and rebooted back into the remaining good disk.

I've got a couple of spare 500GB disks lying around, but know that they have old Windows installation data sitting on them. I'm assuming this needs to be wiped/formatted before I put them into the Ubuntu box. I just need to understand the best state to get them into before I fit them - anyone care to advise what that would be?

---

### Post by CharlesA on 2013-12-03
> **Chris of Arabia said:**
> Well there were no issues with the connections. And I've identified the problem disk, which I've now disconnected and rebooted back into the remaining good disk.

I've got a couple of spare 500GB disks lying around, but know that they have old Windows installation data sitting on them. I'm assuming this needs to be wiped/formatted before I put them into the Ubuntu box. I just need to understand the best state to get them into before I fit them - anyone care to advise what that would be?

Was the disk completely dead, or just not being detected?

The drive will need to be wiped, so you will have to partition and format it like usual before adding it back to the array.

---

### Post by Chris of Arabia on 2013-12-03
Looking at the results of this post - [http://ubuntuforums.org/showthread.php?t=2191351&p=12863208#post12863208](http://ubuntuforums.org/showthread.php?t=2191351&p=12863208#post12863208) - it's definitely not being detected. I'm not sure whether I can tell whether the disk is actually dead. I'll have a dig into the BIOS and see if appears to be showing up in there as a functioning disk.

---

### Post by Chris of Arabia on 2013-12-03
I've checked in the BIOS and it appears to be seeing both disks. The boot sequence also appears to be showing two disks as being good, though it's shooting through a little quick to pick up every nuance being reported there. One thing I did notice whilst in the BIOS, was that the CD/DVD drive was set as the 1st boot device (there's nothing in the drive), so I changed that to be one of the two HDDs (SATA: PS-WDC WD3). Interestingly, this time it booted, it ended up dropping me into a ***grub rescue>*** prompt. Going back into BIOS, I swapped the 1st boot device over to the other HDD (SATA: SS-WDC WD3), but the boot sequence went nowhere and just left me with a blank screen.

I've just now reversed the HDD boot sequence back, and am now left with the message ***Read Error_*** on the screen. Rebooted again, and this time, I'm back to the ***grub rescue>*** prompt

Edit: Actually, what it says on the screen is as follows...
[INDENT][I] 
error: attempt to read or write outside of disk 'hd0' .
Entering rescue mode...
grub rescue>[/I][/INDENT]

---

### Post by Chris of Arabia on 2013-12-16
In the end, I put a couple of different disks in it and did a scratch rebuild. Looking at a repeat of the first couple of checks I did, all now seems well and I think we can consider this closed.

> Last login: Mon Dec 16 19:17:21 2013 from eeyore2.local
[EMAIL="chris@PIGLET2:~$"]chris@PIGLET2:~$[/EMAIL] sudo cat /proc/mdstat
[sudo] password for chris:
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[1] sda1[0]
      16006016 blocks super 1.2 [2/2] [UU]
md1 : active raid1 sdb2[1] sda2[0]
      472238912 blocks super 1.2 [2/2] [UU]
unused devices: <none>


> [EMAIL="chris@PIGLET2:~$"]chris@PIGLET2:~$[/EMAIL] sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sat Dec 14 22:36:56 2013
     Raid Level : raid1
     Array Size : 472238912 (450.36 GiB 483.57 GB)
  Used Dev Size : 472238912 (450.36 GiB 483.57 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent
    Update Time : Mon Dec 16 21:51:25 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
           Name : PIGLET2:1  (local to host PIGLET2)
           UUID : 6c66e0b5:0ba8efd6:d4249152:3f3512d0
         Events : 44
    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2



---

