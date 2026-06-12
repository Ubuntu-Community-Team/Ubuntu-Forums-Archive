---
title: "Not able to use SMART on Seagate NAS Drives"
date: 2015-06-25
forum: Server Platforms
---

### Post by Luke_Higgs on 2015-06-25
Good afternoon,

I have ubuntu server 14.04 running a mdadm RAID5 array using Seagate SATA NAS drives (ST4000VN000), I have smartmontools installed and am trying to check my raid disks with it. Running ```
mdadm --detail /dev/md0
``` I get this output:
[INDENT]/dev/md0:[/INDENT]
[INDENT]        Version : 1.2[/INDENT]
[INDENT]  Creation Time : Wed Jan 21 15:58:40 2015[/INDENT]
[INDENT]     Raid Level : raid5[/INDENT]
[INDENT]     Array Size : 23441310720 (22355.38 GiB 24003.90 GB)[/INDENT]
[INDENT]  Used Dev Size : 3906885120 (3725.90 GiB 4000.65 GB)[/INDENT]
[INDENT]   Raid Devices : 7[/INDENT]
[INDENT]  Total Devices : 8[/INDENT]
[INDENT]    Persistence : Superblock is persistent[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    Update Time : Thu Jun 25 10:48:10 2015[/INDENT]
[INDENT]          State : clean[/INDENT]
[INDENT] Active Devices : 7[/INDENT]
[INDENT]Working Devices : 8[/INDENT]
[INDENT] Failed Devices : 0[/INDENT]
[INDENT]  Spare Devices : 1[/INDENT]
[INDENT]
[/INDENT]
[INDENT]         Layout : left-symmetric[/INDENT]
[INDENT]     Chunk Size : 512K[/INDENT]
[INDENT]
[/INDENT]
[INDENT]           Name : ubuntu:0[/INDENT]
[INDENT]           UUID : 597722a0:75484701:5e3b8b0f:eede151e[/INDENT]
[INDENT]         Events : 1949[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    Number   Major   Minor   RaidDevice State[/INDENT]
[INDENT]       0       8       33        0      active sync   /dev/sdc1[/INDENT]
[INDENT]       1       8       49        1      active sync   /dev/sdd1[/INDENT]
[INDENT]       2       8       65        2      active sync   /dev/sde1[/INDENT]
[INDENT]       3       8       81        3      active sync   /dev/sdf1[/INDENT]
[INDENT]       4       8       97        4      active sync   /dev/sdg1[/INDENT]
[INDENT]       5       8      113        5      active sync   /dev/sdh1[/INDENT]
[INDENT]       6       8      129        6      active sync   /dev/sdi1[/INDENT]
[INDENT]
[/INDENT]
[INDENT]       7       8      145        -      spare   /dev/sdj1[/INDENT]


running ```
smartctl -i /dev/sdc
``` I get this: 
[INDENT]smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)[/INDENT]
[INDENT]Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")[/INDENT]
[INDENT]
[/INDENT]
[INDENT]/dev/sdc: Unknown USB bridge [0x152d:0x3562 (0x310)][/INDENT]
[INDENT]Please specify device type with the -d option.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Use smartctl -h to get a usage summary[/INDENT]

Modifying the command to this ```
smartctl -i -d ata -T permissive /dev/sdc

``` I get:[INDENT]smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)[/INDENT]
[INDENT]Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Read Device Identity failed: Invalid argument[/INDENT]
[INDENT]
[/INDENT]
[INDENT]=== START OF INFORMATION SECTION ===[/INDENT]
[INDENT]Device Model:     [No Information Found][/INDENT]
[INDENT]Serial Number:    [No Information Found][/INDENT]
[INDENT]Firmware Version: [No Information Found][/INDENT]
[INDENT]Device is:        Not in smartctl database [for details use: -P showall][/INDENT]
[INDENT]ATA Version is:   [No Information Found][/INDENT]
[INDENT]Local Time is:    Thu Jun 25 11:23:19 2015 EDT[/INDENT]
[INDENT]SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.[/INDENT]
[INDENT]SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.[/INDENT]
[INDENT]SMART support is: Unknown - Try option -s with argument 'on' to enable it.[/INDENT]


I've tried to enable it using: ```
smartctl -s on -d ata -T permissive /dev/sdc

``` I get: 
[INDENT]smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)[/INDENT]
[INDENT]Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Read Device Identity failed: Invalid argument[/INDENT]
[INDENT]
[/INDENT]
[INDENT]SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.[/INDENT]
[INDENT]SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.[/INDENT]
[INDENT]A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
[/INDENT]

**Device is: Not in smartctl database [for details use: -P showall] **&#8203;makes me think I need to add my drives somewhere to make smartmontools aware of them? According to Seagate these drives have SMART support. The drives are sdc through sdj, I can get smart info from /dev/sda but it's a western digital hard drive and not part of a mdadm raid. Any help would be greatly appreciated. 

Thanks!
Luke

---

### Post by TheFu on 2015-06-25
Check the BIOS settings - SMART needs to be enabled there too for each drive.

---

