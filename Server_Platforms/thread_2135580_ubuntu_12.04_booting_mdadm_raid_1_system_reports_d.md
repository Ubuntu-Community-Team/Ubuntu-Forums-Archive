---
title: "ubuntu 12.04 booting mdadm raid 1 system reports degraded system"
date: 2013-04-14
forum: Server Platforms
---

### Post by MgFrobozz on 2013-04-14
I have a raid 1 system set up under mdadm using /dev/sda2 and /dev/sdb2. After I recently installed ubuntu 12.04, the system issues a warning during boot of the 12.04 system:[INDENT][FONT=courier new]One or more of the following RAID devices are degraded:
md0: active raid1 sdb[0] sda[2]
[/FONT][/INDENT]
[FONT=arial]It then asks if I want to boot with the degraded set. If I do, everything behaves quite normally, and the diags look ok (details below). When I've lost a disk in the past (twice), /proc/mdstat showed issues, but not in this case.

If I reboot and choose my ubuntu 10.04 installation, there's no complaint about a degraded system.

Is the issue related to the empty slot in the array? A couple of years ago, the array used to contain 2 disks plus a spare, but the last disk failure converted the spare to a active disk. This is the first time I've run "--examine" on the raw devices, which show it as "faulty removed", vs "--detail" showing it as simply "removed". Is there something I can do to convert the "faulty removed" empty slot to an empty slot to try that theory?

Any advice much appreciated !

```

> cat /proc/mdstat
[/FONT]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb2[0] sda2[2]
      1953407488 blocks [3/2] [U_U]
      
unused devices: <none>

> sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sun May 20 15:59:20 2007
     Raid Level : raid1
     Array Size : 1953407488 (1862.91 GiB 2000.29 GB)
  Used Dev Size : 1953407488 (1862.91 GiB 2000.29 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Sun Apr 14 13:21:16 2013
          State : active, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           UUID : a0e0365b:91e5a4f3:35685d91:0cf9cb98
         Events : 0.38598007


    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       0        0        1      removed
       2       8        2        2      active sync   /dev/sda2

> sudo smartctl -t /dev/sda2
...

> sudo smartctl -Hc -l selftest /dev/sda2
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-40-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


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
data collection:         (36780) seconds.
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
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

> sudo smartctl -t /dev/sdb2
...
> sudo smartctl -Hc -l selftest /dev/sdb2
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-40-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


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
data collection:         (36600) seconds.
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
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

> sudo mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a0e0365b:91e5a4f3:35685d91:0cf9cb98
  Creation Time : Sun May 20 15:59:20 2007
     Raid Level : raid1
  Used Dev Size : 1953407488 (1862.91 GiB 2000.29 GB)
     Array Size : 1953407488 (1862.91 GiB 2000.29 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0


    Update Time : Sun Apr 14 13:27:44 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 2f17c727 - correct
         Events : 38598264




      Number   Major   Minor   RaidDevice State
this     2       8        2        2      active sync   /dev/sda2


   0     0       8       18        0      active sync   /dev/sdb2
   1     1       0        0        1      faulty removed
   2     2       8        2        2      active sync   /dev/sda2

> sudo mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a0e0365b:91e5a4f3:35685d91:0cf9cb98
  Creation Time : Sun May 20 15:59:20 2007
     Raid Level : raid1
  Used Dev Size : 1953407488 (1862.91 GiB 2000.29 GB)
     Array Size : 1953407488 (1862.91 GiB 2000.29 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0


    Update Time : Sun Apr 14 13:28:19 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 2f17c78a - correct
         Events : 38598290




      Number   Major   Minor   RaidDevice State
this     0       8       18        0      active sync   /dev/sdb2


   0     0       8       18        0      active sync   /dev/sdb2
   1     1       0        0        1      faulty removed
   2     2       8        2        2      active sync   /dev/sda2




```

---

### Post by SaturnusDJ on 2013-04-15
The first thing would indeed be removing the reference about an already removed disk.

Fix it with:
```
mdadm --manage /dev/md0 --remove detached
```

---

### Post by MgFrobozz on 2013-04-18
I tried "sudo [COLOR=#000000][FONT=Ubuntu Mono]mdadm --manage /dev/md0 --remove detached[/FONT][/COLOR]", but it didn't have any affect on the listing ("sudo mdadm --detail /md0" still shows one disk "removed", and "sudo mdadm --detail /dev/sda2" shows one disk "faulty removed"). I also tried rebooting (in case the drive had to reload to make it take effect), but no difference. I still get a warning about a degraded raid set during boot.

---

### Post by SaturnusDJ on 2013-04-19
Hmm interesting. I thought about it some minutes. The array is created as raid1 with 3 disks. However you're quite save with raid1 on 2 disks, mdadm doesn't know this because your array is in a degraded state according to the superblock information.

So the solution is to shrink the number of devices in the array making it non-degraded.
```

mdadm --grow /dev/md0 --raid-disks=2

```

---

