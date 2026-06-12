---
title: "RAID-1: sychro problem"
date: 2011-07-14
forum: Server Platforms
---

### Post by sploutch on 2011-07-14
Hello,

I have a ubuntu-server 8.04 whit RAID-1 :
```
% sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008613e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123         244      979965   82  Linux swap / Solaris
/dev/sda3             245        2068    14651280   fd  Linux raid autodetect
/dev/sda4            2069      121601   960148822+  fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008a22d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  83  Linux
/dev/sdb2             123         244      979965   82  Linux swap / Solaris
/dev/sdb3             245        2068    14651280   fd  Linux raid autodetect
/dev/sdb4            2069      121601   960148822+  fd  Linux raid autodetect

Disk /dev/md0: 15.0 GB, 15002828800 bytes
2 heads, 4 sectors/track, 3662800 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 983.1 GB, 983192305664 bytes
2 heads, 4 sectors/track, 240037184 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```

The /dev/md1 works well, but the /dev/md0 didnt sychronize when I run command :

```
% sudo mdadm --manage /dev/md0 -a /dev/sda3

% cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda4[0] sdb4[1]
      960148736 blocks [2/2] [UU]
      
md0 : active raid1 sda3[2] sdb3[1]
      14651200 blocks [2/1] [_U]
      [==>..................]  recovery = 13.1% (1925312/14651200) finish=2.5min speed=83709K/sec
      
unused devices: <none>
```

when the syc almost finish 99.9%, it start again and again... To stop the process I have to put the /dev/sda3 partition as "faulty" :

```
% sudo mdadm --manage /dev/md0 -f /dev/sda3
mdadm: set /dev/sda3 faulty in /dev/md0

% sudo mdadm --manage /dev/md0 -r /dev/sda3
mdadm: hot removed /dev/sda3
```

After remove, I tried to check, create and format the /dev/sda3 partition but nothing change... RAID doesn't like the partition! :cry:

More informations :

```
% sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Aug  6 17:43:18 2008
     Raid Level : raid1
     Array Size : 14651200 (13.97 GiB 15.00 GB)
  Used Dev Size : 14651200 (13.97 GiB 15.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jul 13 16:22:01 2011
          State : active, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 8% complete

           UUID : 366b30bb:525392dc:3ae1e9e5:6db1d9f7
         Events : 0.4662531

    Number   Major   Minor   RaidDevice State
       2       8        3        0      spare rebuilding   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
```

Maybe someone has any idea?

---------
I dont speak very well English so I also wrote a French version of this post here : [http://forum.ubuntu-fr.org/viewtopic.php?id=571101](http://forum.ubuntu-fr.org/viewtopic.php?id=571101)

---

### Post by ian dobson on 2011-07-14
Hi,

What do you see in the system log (dmesg) when the resync restarts?

Regards
Ian Dobson

---

### Post by sploutch on 2011-07-14
> **ian dobson said:**
> What do you see in the system log (dmesg) when the resync restarts?

dmesg says :

```
[89373.689057] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89373.689065] ata2.00: BMDMA stat 0x24
[89373.689073] ata2.00: cmd 25/00:00:f4:db:fa/00:04:01:00:00/e0 tag 0 dma 524288 in
[89373.689075]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e0 Emask 0x9 (media error)
[89373.689080] ata2.00: status: { DRDY ERR }
[89373.689083] ata2.00: error: { UNC }
[89374.679521] ata2.00: configured for UDMA/133
[89374.679538] ata2: EH complete
[89375.645892] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89375.645900] ata2.00: BMDMA stat 0x24
[89375.645908] ata2.00: cmd 25/00:00:f4:db:fa/00:04:01:00:00/e0 tag 0 dma 524288 in
[89375.645910]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e0 Emask 0x9 (media error)
[89375.645915] ata2.00: status: { DRDY ERR }
[89375.645917] ata2.00: error: { UNC }
[89376.649219] ata2.00: configured for UDMA/133
[89376.649238] ata2: EH complete
[89377.660776] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89377.660783] ata2.00: BMDMA stat 0x24
[89377.660791] ata2.00: cmd 25/00:00:f4:db:fa/00:04:01:00:00/e0 tag 0 dma 524288 in
[89377.660794]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e0 Emask 0x9 (media error)
[89377.660798] ata2.00: status: { DRDY ERR }
[89377.660801] ata2.00: error: { UNC }
[89378.658914] ata2.00: configured for UDMA/133
[89378.658932] ata2: EH complete
[89379.625906] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89379.625914] ata2.00: BMDMA stat 0x24
[89379.625923] ata2.00: cmd 25/00:00:f4:db:fa/00:04:01:00:00/e0 tag 0 dma 524288 in
[89379.625925]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e0 Emask 0x9 (media error)
[89379.625929] ata2.00: status: { DRDY ERR }
[89379.625932] ata2.00: error: { UNC }
[89380.621118] ata2.00: configured for UDMA/133
[89380.621138] ata2: EH complete
[89381.640788] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89381.640796] ata2.00: BMDMA stat 0x24
[89381.640804] ata2.00: cmd 25/00:00:f4:db:fa/00:04:01:00:00/e0 tag 0 dma 524288 in
[89381.640806]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e0 Emask 0x9 (media error)
[89381.640811] ata2.00: status: { DRDY ERR }
[89381.640813] ata2.00: error: { UNC }
[89382.640812] ata2.00: configured for UDMA/133
[89382.640831] ata2: EH complete
[89383.605920] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89383.605928] ata2.00: BMDMA stat 0x24
[89383.605935] ata2.00: cmd 25/00:00:f4:db:fa/00:04:01:00:00/e0 tag 0 dma 524288 in
[89383.605938]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e0 Emask 0x9 (media error)
[89383.605942] ata2.00: status: { DRDY ERR }
[89383.605945] ata2.00: error: { UNC }
[89384.598012] ata2.00: configured for UDMA/133
[89384.598042] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[89384.598048] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[89384.598055] Descriptor sense data with sense descriptors (in hex):
[89384.598058]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[89384.598073]         01 fa dd bc 
[89384.598079] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[89384.598088] end_request: I/O error, dev sdb, sector 33217980
[89384.598103] ata2: EH complete
[89384.634549] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[89384.639844] sd 1:0:0:0: [sdb] Write Protect is off
[89384.639850] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[89384.643598] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[89384.648229] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[89384.726777] sd 1:0:0:0: [sdb] Write Protect is off
[89384.726786] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[89384.727258] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[89385.694475] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89385.694483] ata2.00: BMDMA stat 0x24
[89385.694491] ata2.00: cmd c8/00:08:bc:dd:fa/00:00:00:00:00/e1 tag 0 dma 4096 in
[89385.694493]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e1 Emask 0x9 (media error)
[89385.694498] ata2.00: status: { DRDY ERR }
[89385.694500] ata2.00: error: { UNC }
[89386.687696] ata2.00: configured for UDMA/133
[89386.687709] ata2: EH complete
[89387.651313] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89387.651321] ata2.00: BMDMA stat 0x24
[89387.651329] ata2.00: cmd c8/00:08:bc:dd:fa/00:00:00:00:00/e1 tag 0 dma 4096 in
[89387.651331]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e1 Emask 0x9 (media error)
[89387.651336] ata2.00: status: { DRDY ERR }
[89387.651339] ata2.00: error: { UNC }
[89388.667400] ata2.00: configured for UDMA/133
[89388.667418] ata2: EH complete
[89389.666198] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89389.666206] ata2.00: BMDMA stat 0x24
[89389.666214] ata2.00: cmd c8/00:08:bc:dd:fa/00:00:00:00:00/e1 tag 0 dma 4096 in
[89389.666216]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e1 Emask 0x9 (media error)
[89389.666220] ata2.00: status: { DRDY ERR }
[89389.666223] ata2.00: error: { UNC }
[89390.657102] ata2.00: configured for UDMA/133
[89390.657120] ata2: EH complete
[89391.623038] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89391.623046] ata2.00: BMDMA stat 0x24
[89391.623054] ata2.00: cmd c8/00:08:bc:dd:fa/00:00:00:00:00/e1 tag 0 dma 4096 in
[89391.623057]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e1 Emask 0x9 (media error)
[89391.623061] ata2.00: status: { DRDY ERR }
[89391.623064] ata2.00: error: { UNC }
[89392.616796] ata2.00: configured for UDMA/133
[89392.616814] ata2: EH complete
[89393.637920] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89393.637928] ata2.00: BMDMA stat 0x24
[89393.637936] ata2.00: cmd c8/00:08:bc:dd:fa/00:00:00:00:00/e1 tag 0 dma 4096 in
[89393.637938]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e1 Emask 0x9 (media error)
[89393.637943] ata2.00: status: { DRDY ERR }
[89393.637946] ata2.00: error: { UNC }
[89394.638996] ata2.00: configured for UDMA/133
[89394.639014] ata2: EH complete
[89395.603053] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[89395.603061] ata2.00: BMDMA stat 0x24
[89395.603069] ata2.00: cmd c8/00:08:bc:dd:fa/00:00:00:00:00/e1 tag 0 dma 4096 in
[89395.603071]          res 51/40:00:bc:dd:fa/40:00:01:00:00/e1 Emask 0x9 (media error)
[89395.603075] ata2.00: status: { DRDY ERR }
[89395.603078] ata2.00: error: { UNC }
[89396.606189] ata2.00: configured for UDMA/133
[89396.606208] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[89396.606214] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[89396.606221] Descriptor sense data with sense descriptors (in hex):
[89396.606224]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[89396.606238]         01 fa dd bc 
[89396.606244] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[89396.606253] end_request: I/O error, dev sdb, sector 33217980
[89396.606268] ata2: EH complete
[89396.606289] raid1: sdb: unrecoverable I/O read error for block 29298048
[89396.636120] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[89396.636224] sd 1:0:0:0: [sdb] Write Protect is off
[89396.636227] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[89396.636384] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[89396.636411] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[89396.636477] sd 1:0:0:0: [sdb] Write Protect is off
[89396.636480] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[89396.636722] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[89397.668227] md: md0: recovery done.
[89397.688984] RAID1 conf printout:
[89397.688988]  --- wd:1 rd:2
[89397.688992]  disk 0, wo:1, o:1, dev:sda3
[89397.688995]  disk 1, wo:0, o:1, dev:sdb3
[89397.728196] RAID1 conf printout:
[89397.728202]  --- wd:1 rd:2
[89397.728205]  disk 1, wo:0, o:1, dev:sdb3
[89397.728221] RAID1 conf printout:
[89397.728223]  --- wd:1 rd:2
[89397.728225]  disk 0, wo:1, o:1, dev:sda3
[89397.728228]  disk 1, wo:0, o:1, dev:sdb3
[89397.728267] md: recovery of RAID array md0
[89397.728270] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[89397.728274] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[89397.728279] md: using 128k window, over a total of 14651200 blocks.
```

---

### Post by psusi on 2011-07-14
Your "good drive" appears to be failing.  It may be time to back up your data, replace both disks, and rebuild the system.

You might check the SMART status of the drive with the smartctl utility in the smartmontools package.

---

### Post by ian dobson on 2011-07-14
Hi,

or maybe the sata cables aren't the best, try replacing them. The problem appears to be with the second drive ATA2.00 not with the first drive. sda=ATA1.00 and sdb=ATA2.00

Regards
Ian Dobson

---

### Post by psusi on 2011-07-14
"media error" means the drive is saying it is screwed, not a cable problem.

---

### Post by ian dobson on 2011-07-14
Hi,

I would still try different cables, on my large RAID system (7 x 2Tb drives) I got all sorts of "random" errors from the drives until I replaced the cabling. I would imagine the drive is screwed but it's worth a try.

Regards
Ian Dobson

---

### Post by rubylaser on 2011-07-15
Replacing the cables won't hurt, but psusi is correct, a media error is a warning that the physical disk is having problems.  What does the SMART data look like on this drive?

---

### Post by sploutch on 2011-07-15
> **rubylaser said:**
> Replacing the cables won't hurt, but psusi is correct, a media error is a warning that the physical disk is having problems.  What does the SMART data look like on this drive?

You're right! Change the cables didn't works better...

```
% sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD103UJ
Serial Number:    S13PJ1MQ601211
Firmware Version: 1AA01112
User Capacity:    1,000,204,886,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Fri Jul 15 13:51:25 2011 CEST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (11742) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 197) minutes.
Conveyance self-test routine
recommended polling time: 	 (  21) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       11
  3 Spin_Up_Time            0x0007   077   077   011    Pre-fail  Always       -       7810
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       40
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       25430
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       40
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       11
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   100   100   099    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       31
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   075   071   000    Old_age   Always       -       25 (Lifetime Min/Max 25/25)
194 Temperature_Celsius     0x0022   074   071   000    Old_age   Always       -       26 (Lifetime Min/Max 25/26)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       25482
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 6 (device log contains only the most recent five errors)
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

Error 6 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 06 e7 fa e1  Error: UNC at LBA = 0x01fae706 = 33220358

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 74 e6 fa e1 08  37d+16:48:05.104  READ DMA
  ec 00 00 00 00 00 a0 08  37d+16:48:04.884  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  37d+16:48:04.884  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  37d+16:48:03.944  IDENTIFY DEVICE

Error 5 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 06 e7 fa e1  Error: UNC at LBA = 0x01fae706 = 33220358

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 74 e6 fa e1 08  37d+16:48:02.934  READ DMA
  ec 00 00 00 00 00 a0 08  37d+16:48:02.724  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  37d+16:48:02.724  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  37d+16:48:01.794  IDENTIFY DEVICE

Error 4 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 06 e7 fa e1  Error: UNC at LBA = 0x01fae706 = 33220358

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 74 e6 fa e1 08  37d+16:48:00.794  READ DMA
  ec 00 00 00 00 00 a0 08  37d+16:48:00.564  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  37d+16:48:00.564  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  37d+16:47:59.624  IDENTIFY DEVICE

Error 3 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 06 e7 fa e1  Error: UNC at LBA = 0x01fae706 = 33220358

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 74 e6 fa e1 08  37d+16:47:58.614  READ DMA
  ec 00 00 00 00 00 a0 08  37d+16:47:58.394  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  37d+16:47:58.394  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  37d+16:47:57.464  IDENTIFY DEVICE

Error 2 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 06 e7 fa e1  Error: UNC at LBA = 0x01fae706 = 33220358

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 74 e6 fa e1 08  37d+16:47:56.454  READ DMA
  ec 00 00 00 00 00 a0 08  37d+16:47:56.224  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  37d+16:47:56.224  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  37d+16:47:55.244  IDENTIFY DEVICE

SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
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

I anderstand nothing...

---

### Post by psusi on 2011-07-15
Strange... it does not show any bad sectors, but does show that there was an uncorrectable error trying to read sector 33220358.  Try reading that sector with dd and see if you get the error again:

sudo dd if=/dev/sda bs=512 count=1 skip=33220358 of=/dev/null

That will confirm that is the bad sector.  You can then try to write zeros to the unreadable sector and that might fix it:

sudo dd if=/dev/zero bs=512 count=1 seek=33220358 of=/dev/sda

Then try the read again and see if it's happy.  Then run the long SMART selftest on the drive:

sudo smartctl -t long /dev/sda

Check the SMART values again when it finishes and see if the test passed, or found another bad sector.  If it passes, then the raid should be able to finish resyncing, but you should force a fsck of the filesystem as you obviously have lost the contents of a sector, so you might have some damage to the fs, or a corrupted file somewhere.

---

### Post by sploutch on 2011-10-25
Hi!
Always the same problem... I have add a new HDD with a new cable SATA, but the RAID did't work better :
```
% sudo mdadm --detail /dev/md0                       
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Aug  6 17:43:18 2008
     Raid Level : raid1
     Array Size : 14651200 (13.97 GiB 15.00 GB)
  Used Dev Size : 14651200 (13.97 GiB 15.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Oct 25 09:04:40 2011
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 2
  Spare Devices : 0

           UUID : 366b30bb:525392dc:3ae1e9e5:6db1d9f7
         Events : 0.5577049

    Number   Major   Minor   RaidDevice State
       0       8       35        0      active sync   /dev/sdc3
       1       0        0        1      removed
       2       0        0        2      removed

       3       8        3        -      faulty spare   /dev/sda3
       4       8       19        -      faulty spare   /dev/sdb3

```
I dont know what to do with this RAID partition... Please (try to) help me !!!

---

