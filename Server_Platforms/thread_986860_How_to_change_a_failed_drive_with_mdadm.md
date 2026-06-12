---
title: "How to change a failed drive with mdadm"
date: 2008-11-19
forum: Server Platforms
---

### Post by qiet72 on 2008-11-19
Hi,

I have been playing around with raid 5 and mdadm and need help on a little problem.  Here is my setup:

/dev/md0: 4 disk raid5 with no hot spare
members:
/dev/sdb: sata 320GB
/dev/sdc: sata 320GB
/dev/sdd: sata 320GB
/dev/sde: sata 320GB

I create my array like this:
```

mdadm --create -l5 -n4 /dev/md0 /dev/sd[bcde]

```

Raid array starts and I let it synchronise which took about 3 hours.
Next I test how linux raid handles failed drives by unplugging the data cable from one of the drive while the system is online.

The system responds as you can see here in messages:
```

Nov 19 06:25:30 ibex32 kernel: [25933.177996] 3w-xxxx: scsi2: Command failed: status = 0xc7, flags = 0x7f, unit #3.
Nov 19 06:25:34 ibex32 kernel: [25937.006194] 3w-xxxx: scsi2: AEN: ERROR: Drive error: Port #3.
Nov 19 06:25:34 ibex32 kernel: [25937.006392] sd 2:0:3:0: WARNING: Command (0x28) timed out, resetting card.
Nov 19 06:25:50 ibex32 kernel: [25953.224176] sd 2:0:3:0: Device offlined - not ready after error recovery
Nov 19 06:25:50 ibex32 kernel: [25953.224198] sd 2:0:3:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_OK,SUGGEST_OK
Nov 19 06:25:50 ibex32 kernel: [25953.224216] __ratelimit: 3 callbacks suppressed
Nov 19 06:26:08 ibex32 kernel: [25970.694880] RAID5 conf printout:
Nov 19 06:26:08 ibex32 kernel: [25970.694888]  --- rd:4 wd:3
Nov 19 06:26:08 ibex32 kernel: [25970.694894]  disk 0, o:1, dev:sdb
Nov 19 06:26:08 ibex32 kernel: [25970.694925]  disk 1, o:1, dev:sdc
Nov 19 06:26:08 ibex32 kernel: [25970.694929]  disk 2, o:1, dev:sdd
Nov 19 06:26:08 ibex32 kernel: [25970.694933]  disk 3, o:0, dev:sde
Nov 19 06:26:08 ibex32 kernel: [25970.699107] RAID5 conf printout:
Nov 19 06:26:08 ibex32 kernel: [25970.699120]  --- rd:4 wd:3
Nov 19 06:26:08 ibex32 kernel: [25970.699124]  disk 0, o:1, dev:sdb
Nov 19 06:26:08 ibex32 kernel: [25970.699127]  disk 1, o:1, dev:sdc
Nov 19 06:26:08 ibex32 kernel: [25970.699129]  disk 2, o:1, dev:sdd

```

The raid status now shows (/proc/mdstat):
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde[4](F) sdd[2] sdc[1] sdb[0]
      949008000 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]

unused devices: <none>

```

So sde is now the failed drive.  If I plug the data cable back in again, nothing seems to happen.  No new messages in the message log and mdstat still shows sde as a failed drive.

I run fdisk -l /dev/sde, but it shows nothing.

How do I get sde back online again without rebooting the system?

qiet72

---

### Post by qiet72 on 2008-11-19
Some more interesting info:

Instead of rebooting, I now re-load the disk controller driver:
sudo mdadm --manage -S /dev/md0
sudo modprobe -r 3w_xxxx
sudo modprobe 3w_xxxx

Here is the message output:
```

[27785.642399] md: md0 stopped.
[27785.643389] md: unbind<sde>
[27785.657036] md: export_rdev(sde)
[27785.657307] md: unbind<sdd>
[27785.657986] md: export_rdev(sdd)
[27785.658175] md: unbind<sdc>
[27785.660023] md: export_rdev(sdc)
[27785.660186] md: unbind<sdb>
[27785.664021] md: export_rdev(sdb)
[27807.093461] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[27807.101487] sd 2:0:1:0: [sdc] Synchronizing SCSI cache
[27807.102305] sd 2:0:2:0: [sdd] Synchronizing SCSI cache
[27807.103019] sd 2:0:3:0: [sde] Synchronizing SCSI cache
[27807.103538] 3w-xxxx: Shutting down host 2.
[27807.224035] 3w-xxxx: Shutdown complete.
[27807.228264] 3w-xxxx 0000:02:0a.0: PCI INT A disabled
[27828.934473] 3ware Storage Controller device driver for Linux v1.26.02.002.
[27828.934544] 3w-xxxx 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[27835.204022] scsi8 : 3ware Storage Controller
[27835.204184] 3w-xxxx: scsi8: Found a 3ware Storage Controller at 0xe400, IRQ: 22.
[27835.206333] scsi 8:0:0:0: Direct-Access     3ware    Logical Disk 0   1.2  PQ: 0 ANSI: 0
[27835.216049] scsi 8:0:1:0: Direct-Access     3ware    Logical Disk 1   1.2  PQ: 0 ANSI: 0
[27835.216307] scsi 8:0:2:0: Direct-Access     3ware    Logical Disk 2   1.2  PQ: 0 ANSI: 0
[27835.216532] scsi 8:0:3:0: Direct-Access     3ware    Logical Disk 3   1.2  PQ: 0 ANSI: 0
[27835.220316] sd 8:0:0:0: [sdb] 632672208 512-byte hardware sectors (323928 MB)
[27835.220373] sd 8:0:0:0: [sdb] Write Protect is off
[27835.220381] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[27835.221242] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.221901] sd 8:0:0:0: [sdb] 632672208 512-byte hardware sectors (323928 MB)
[27835.221945] sd 8:0:0:0: [sdb] Write Protect is off
[27835.221951] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[27835.222295] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.222305]  sdb: unknown partition table
[27835.231347] sd 8:0:0:0: [sdb] Attached SCSI disk
[27835.231589] sd 8:0:0:0: Attached scsi generic sg2 type 0
[27835.232884] sd 8:0:1:0: [sdc] 632672208 512-byte hardware sectors (323928 MB)
[27835.232941] sd 8:0:1:0: [sdc] Write Protect is off
[27835.232947] sd 8:0:1:0: [sdc] Mode Sense: 00 00 00 00
[27835.233312] sd 8:0:1:0: [sdc] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.235057] sd 8:0:1:0: [sdc] 632672208 512-byte hardware sectors (323928 MB)
[27835.235120] sd 8:0:1:0: [sdc] Write Protect is off
[27835.235127] sd 8:0:1:0: [sdc] Mode Sense: 00 00 00 00
[27835.235488] sd 8:0:1:0: [sdc] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.235499]  sdc: unknown partition table
[27835.254453] sd 8:0:1:0: [sdc] Attached SCSI disk
[27835.254644] sd 8:0:1:0: Attached scsi generic sg3 type 0
[27835.255615] sd 8:0:2:0: [sdd] 632672208 512-byte hardware sectors (323928 MB)
[27835.255678] sd 8:0:2:0: [sdd] Write Protect is off
[27835.255686] sd 8:0:2:0: [sdd] Mode Sense: 00 00 00 00
[27835.256029] sd 8:0:2:0: [sdd] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.256459] sd 8:0:2:0: [sdd] 632672208 512-byte hardware sectors (323928 MB)
[27835.256505] sd 8:0:2:0: [sdd] Write Protect is off
[27835.256512] sd 8:0:2:0: [sdd] Mode Sense: 00 00 00 00
[27835.256843] sd 8:0:2:0: [sdd] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.256854]  sdd: unknown partition table
[27835.261214] sd 8:0:2:0: [sdd] Attached SCSI disk
[27835.261462] sd 8:0:2:0: Attached scsi generic sg4 type 0
[27835.264788] sd 8:0:3:0: [sde] 632672208 512-byte hardware sectors (323928 MB)
[27835.264858] sd 8:0:3:0: [sde] Write Protect is off
[27835.264864] sd 8:0:3:0: [sde] Mode Sense: 00 00 00 00
[27835.265229] sd 8:0:3:0: [sde] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.265701] sd 8:0:3:0: [sde] 632672208 512-byte hardware sectors (323928 MB)
[27835.265750] sd 8:0:3:0: [sde] Write Protect is off
[27835.265757] sd 8:0:3:0: [sde] Mode Sense: 00 00 00 00
[27835.266125] sd 8:0:3:0: [sde] Write cache: enabled, read cache: disabled, supports DPO and FUA
[27835.266135]  sde: unknown partition table
[27835.274482] sd 8:0:3:0: [sde] Attached SCSI disk
[27835.274701] sd 8:0:3:0: Attached scsi generic sg5 type 0
[27836.262028] md: bind<sdc>
[27836.262252] md: bind<sdd>
[27836.262485] md: bind<sde>
[27836.262731] md: bind<sdb>
[27836.262796] md: kicking non-fresh sde from array!
[27836.262809] md: unbind<sde>
[27836.268041] md: export_rdev(sde)
[27836.319676] raid5: device sdb operational as raid disk 0
[27836.319686] raid5: device sdd operational as raid disk 2
[27836.319692] raid5: device sdc operational as raid disk 1
[27836.320795] raid5: allocated 4214kB for md0
[27836.320802] raid5: raid level 5 set md0 active with 3 out of 4 devices, algorithm 2
[27836.320810] RAID5 conf printout:
[27836.320814]  --- rd:4 wd:3
[27836.320820]  disk 0, o:1, dev:sdb
[27836.320824]  disk 1, o:1, dev:sdc
[27836.320829]  disk 2, o:1, dev:sdd

```

So now I am able to see sde again.  Here is what "mdadm --misc -E /dev/sd[bcde] show:

```

/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7eef055:c2bb3185:6b06e671:90bd14cc (local to host ibex32)
  Creation Time : Tue Nov 18 23:19:39 2008
     Raid Level : raid5
  Used Dev Size : 316336000 (301.68 GiB 323.93 GB)
     Array Size : 949008000 (905.04 GiB 971.78 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Nov 19 06:28:21 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 4bc3896 - correct
         Events : 8

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7eef055:c2bb3185:6b06e671:90bd14cc (local to host ibex32)
  Creation Time : Tue Nov 18 23:19:39 2008
     Raid Level : raid5
  Used Dev Size : 316336000 (301.68 GiB 323.93 GB)
     Array Size : 949008000 (905.04 GiB 971.78 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Nov 19 06:28:21 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 4bc38a8 - correct
         Events : 8

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7eef055:c2bb3185:6b06e671:90bd14cc (local to host ibex32)
  Creation Time : Tue Nov 18 23:19:39 2008
     Raid Level : raid5
  Used Dev Size : 316336000 (301.68 GiB 323.93 GB)
     Array Size : 949008000 (905.04 GiB 971.78 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Nov 19 06:28:21 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 4bc38ba - correct
         Events : 8

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f7eef055:c2bb3185:6b06e671:90bd14cc (local to host ibex32)
  Creation Time : Tue Nov 18 23:19:39 2008
     Raid Level : raid5
  Used Dev Size : 316336000 (301.68 GiB 323.93 GB)
     Array Size : 949008000 (905.04 GiB 971.78 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Nov 19 02:29:47 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4bc00cf - correct
         Events : 4

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       64        3      active sync   /dev/sde

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde


```

Now that I can see sde again, how do I put it back in the array as a member?

qiet72

---

### Post by qiet72 on 2008-11-19
After a bit of research, I found out how to re-add the device to the raid array.  Here is the command to do it:

```

mdadm --manage --re-add /dev/md0 /dev/sde

```

Am I correct in saying that you need a hardware raid in order for hotswapping to work correctly?  It looks like that if you use software raid, you have to reload the disk controller driver in order for linux to see the new replaced drive.

Another question: If I understand the AHCI specification, one should be able to hotplug sata devices.  This is exactly what I tried to test. Here is the controller that I am using to test with:

02:0a.0 RAID bus controller: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID

Does anybody know if 3ware uses the AHCI spec/protocol on there sata controllers?

qiet72

---

### Post by obg123 on 2008-11-19
Just a minor comment on this issue: In the Linux Software Raid HOWTO, they strongly advice against any kind of hot-swapping without power down. The argument being the risk of damaging the hardware (disk or controller or both) permanently. Of course, this might be "one of those" warnings/disclaimers, but I would never dare to pull out one of my disks on the fly just like that.

---

### Post by qiet72 on 2008-11-19
I agree with you on that - especially regarding PATA drives.  But from what I understand, sata drives should be able to handle hot swapping.
Correct me if I am wrong.

qiet72

---

### Post by fjgaude on 2008-11-19
Last-model SATA drives can be hot removed if the controller is also modern.

Here's what the man pages suggest:

For Manage mode:
       -a, --add
              hot-add listed devices.

       --re-add
              re-add a device that was recently removed from an array.

       -r, --remove
              remove  listed  devices.   They  must  not be active.  i.e. they
              should be failed or spare devices.  As well as  the  name  of  a
              device  file (e.g.  /dev/sda1) the words failed and detached can
              be given to --remove.  The first causes all failed device to  be
              removed.   The  second causes any device which is no longer con&#8208;
              nected to the  system  (i.e  an  &#8217;open&#8217;  returns  ENXIO)  to  be
              removed.   This will only succeed for devices that are spares or
              have already been marked as failed.

That three hours was for putting the filesystem onto the array, eh?

---

### Post by qiet72 on 2008-11-19
The three hours was for it to resynchronise.  Look at /proc/mdstat - it will tell you the speed and time for synchronisation (only valid for arrays with parity information, eg raid 1 and 5).

qiet72

---

### Post by fjgaude on 2008-11-19
I don't understand, 3 hours after you created the array, not is not re-sync.

Usually takes a long time to place a filesystem on a newly created array, not to actually create it for the first time.

---

### Post by qiet72 on 2008-11-20
There is a difference.  Resynchronisation writes zeros to every sector of the disk.  I can write at max 70MB/sec to each disk.  There are four disks, so that is 280MB/sec, but since I cannot send more than 133MB/sec over a standard 32-bit pci bus (actually 120MB/sec because of overhead) then I am limited to around 30MB/sec (120MB/sec divided by 4).  At 30MB/sec it would take about 177 mins or around 3 hours (320G or 320000MB / 30MB/sec / 60secs).

Creating a filesystem is different depending on what you do.  If you are checking for bad sectors at the same time your are creating a filesystem then the bad sector check would require that it reads every sector of the disk before it writes a file system structure on it so it can map out any bad sectors it finds.  So the time it would take for this would be about the same time as the synchronisation process above.  But normally most people just create the filesystem without checking for bad sectors and that normally only takes a couple of minutes.

qiet72

---

### Post by fjgaude on 2008-11-20
You do the resync by using the mdadm --create command?

If memory serves, creating a fresh array usually took less than a minute, but putting the filesystem on a big array, four 320GB drives, took about two hours, using my PCI-E controller bus.

I used to use PCI bus and got that bottleneck of 112MB/sec because of it. With the PCI-E I get about 210MB/sec.

This re-sync business sounds like you a using drives that have already been used in an array and adding more and that is where the re-sync comes in. I try only to use fresh drives when using the --create command. Use other commands when adding, removing, faulting drives.

Long live software raid.

---

### Post by wheniwork on 2009-06-01
I had a heat problem over the weekend with my MDADM RAID5. One of the drives supposedly failed. 

I think the controller just shut the HD down and now MDADM thinks its failed. 

How do I know for sure? Should I just do mdadm --assemble --force /dev/md0

Here is what SMART Tools gave me when scanned. Is it truly a dead drive?

```
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3500630AS
Serial Number:    6QG16BKS
Firmware Version: 3.AAK
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jun  1 12:46:25 2009 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 163) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   106   093   006    Pre-fail  Always       -       77490784
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       141
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   072   054   030    Pre-fail  Always       -       69010122065
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       13209
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       133
187 Unknown_Attribute       0x0032   094   094   000    Old_age   Always       -       6
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   064   038   045    Old_age   Always   In_the_past 707002404
194 Temperature_Celsius     0x0022   036   062   000    Old_age   Always       -       36 (Lifetime Min/Max 0/16)
195 Hardware_ECC_Recovered  0x001a   062   058   000    Old_age   Always       -       129785447
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       4
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 10 (device log contains only the most recent five errors)
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

Error 10 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 97 28 8d 32 e1  Error: ICRC, ABRT 151 sectors at LBA = 0x01328d28 = 20090152

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 d8 e7 8c 32 e1 00      07:16:11.293  READ DMA
  c8 00 a8 3f 8c 32 e1 00      07:16:11.238  READ DMA
  c8 00 08 8f 8f 59 ee 00      07:16:11.160  READ DMA
  c8 00 80 bf e4 2c e1 00      07:16:11.695  READ DMA
  c8 00 08 b7 e4 2c e1 00      07:16:11.672  READ DMA

Error 9 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 27 98 58 0c eb  Error: ICRC, ABRT 39 sectors at LBA = 0x0b0c5898 = 185358488

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 58 67 58 0c eb 00      07:16:00.647  READ DMA
  c8 00 28 3f 58 0c eb 00      07:16:00.607  READ DMA
  c8 00 80 bf 4a 0c eb 00      07:16:00.587  READ DMA
  c8 00 48 3f 4e 0c eb 00      07:16:00.581  READ DMA
  c8 00 80 3f 36 0c eb 00      07:16:00.560  READ DMA

Error 8 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 3f 80 4c 0c eb  Error: ICRC, ABRT 63 sectors at LBA = 0x0b0c4c80 = 185355392

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 80 3f 4c 0c eb 00      07:15:59.596  READ DMA
  c8 00 80 bf 4b 0c eb 00      07:15:59.582  READ DMA
  c8 00 80 3f 4b 0c eb 00      07:15:59.572  READ DMA
  c8 00 80 bf b0 0d eb 00      07:15:59.532  READ DMA
  c8 00 80 3f e3 08 eb 00      07:15:59.456  READ DMA

Error 7 occurred at disk power-on lifetime: 13174 hours (548 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 9f 20 5d 0c eb  Error: ICRC, ABRT 159 sectors at LBA = 0x0b0c5d20 = 185359648

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 bf 5c 0c eb 00      07:15:57.114  READ DMA
  c8 00 80 3f 5c 0c eb 00      07:15:57.052  READ DMA
  c8 00 80 3f 3b 0e eb 00      07:15:57.032  READ DMA
  c8 00 48 f7 3a 0e eb 00      07:15:57.000  READ DMA
  c8 00 20 d7 3a 0e eb 00      07:15:56.996  READ DMA

Error 6 occurred at disk power-on lifetime: 631 hours (26 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ce 92 64 e0  Error: UNC at LBA = 0x006492ce = 6591182

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 3f 91 64 e0 00      04:26:20.329  READ DMA EXT
  27 00 00 00 00 00 e0 00      04:26:20.314  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 02      04:26:20.255  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 02      04:26:20.239  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      04:26:18.186  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     13208         -
# 2  Short offline       Aborted by host               60%     13206         -
# 3  Extended offline    Completed without error       00%       920         -
# 4  Short offline       Completed without error       00%       918         -
# 5  Short offline       Interrupted (host reset)      40%       914         -

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

