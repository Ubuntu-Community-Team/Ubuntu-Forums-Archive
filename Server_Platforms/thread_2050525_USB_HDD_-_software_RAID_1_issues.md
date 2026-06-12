---
title: "USB HDD - software RAID 1 issues"
date: 2012-08-31
forum: Server Platforms
---

### Post by Frankincense93 on 2012-08-31
Hey guys,

I have been having some strange issues with my raid that I have recently setup using a guide in this thread that I had: 
[http://ubuntuforums.org/showthread.php?t=2038289](http://ubuntuforums.org/showthread.php?t=2038289)

Firstly for some reason every know and again It seems one of the drives removes itself from the raid, which may be due to the external hdd box, which is a Sharkoon 5 bay RAID box.

I currently have the RAID box in normal mode i.e. each hdd can be seen seperately, and it is connected to the server using usb2 to make use of port forwarding (withh upgrade to usb3 later on). I am using two seagate barracuda spinpoint 1tb HDDs in RAID 1.

I am getting the following messages:
```
The following warning/error was logged by the smartd daemon:

Device: /dev/sdc [SAT], failed to read SMART Attribute Data
```

```
A Fail event had been detected on md device /dev/md0.

It could be related to component device /dev/sdb1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[1] sdb1[0](F)
      976760400 blocks super 1.2 [2/1] [_U]

unused devices: <none>
```


Currently mdadm -D /dev/md0 returns
```
/dev/md0:
        Version : 1.2
  Creation Time : Tue Aug 28 21:31:56 2012
     Raid Level : raid1
     Array Size : 976760400 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976760400 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Fri Aug 31 06:49:05 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : fileserver:0  (local to host fileserver)
           UUID : b8320f5e:84ae6372:cd1bdd44:b366f24d
         Events : 17

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

```

But when the failure occurred, one drive was seen as 'Failed', but after a restart the raid was fine again!

syslog shows
```

Aug 29 15:07:05 SERVER kernel: [63989.747081] md: md0: resync done.
Aug 29 15:07:05 SERVER kernel: [63989.827299] RAID1 conf printout:
Aug 29 15:07:05 SERVER kernel: [63989.827308]  --- wd:2 rd:2
Aug 29 15:07:05 SERVER kernel: [63989.827315]  disk 0, wo:0, o:1, dev:sdb1
Aug 29 15:07:05 SERVER kernel: [63989.827321]  disk 1, wo:0, o:1, dev:sdc1
Aug 29 15:07:05 SERVER mdadm[1176]: RebuildFinished event detected on md device /dev/md0

Aug 29 21:29:55 SERVER smartd[3082]: Device: /dev/sdc [SAT], failed to read SMART Attribute Data

Aug 29 21:34:14 SERVER kernel: [87218.443940] md/raid1:md0: sdb1: rescheduling sector 1953520792
Aug 29 21:34:14 SERVER kernel: [87218.447987] md/raid1:md0: Disk failure on sdb1, disabling device.
Aug 29 21:34:14 SERVER kernel: [87218.447992] md/raid1:md0: Operation continuing on 1 devices.
Aug 29 21:34:14 SERVER kernel: [87218.452534] md/raid1:md0: redirecting sector 1953520792 to other mirror: sdc1
Aug 29 21:34:14 SERVER kernel: [87218.455147] Buffer I/O error on device md0, logical block 244190099
Aug 29 21:34:14 SERVER kernel: [87218.457676] Buffer I/O error on device md0, logical block 244190099
Aug 29 21:34:14 SERVER kernel: [87218.460491] md: super_written gets error=-19, uptodate=0
Aug 29 21:34:14 SERVER kernel: [87218.460533] RAID1 conf printout:
Aug 29 21:34:14 SERVER kernel: [87218.460539]  --- wd:1 rd:2
Aug 29 21:34:14 SERVER kernel: [87218.460546]  disk 0, wo:1, o:0, dev:sdb1
Aug 29 21:34:14 SERVER kernel: [87218.460565]  disk 1, wo:0, o:1, dev:sdc1
Aug 29 21:34:14 SERVER kernel: [87218.480042] RAID1 conf printout:
Aug 29 21:34:14 SERVER kernel: [87218.480049]  --- wd:1 rd:2
Aug 29 21:34:14 SERVER kernel: [87218.480055]  disk 1, wo:0, o:1, dev:sdc1
Aug 29 21:34:15 SERVER sSMTP[14718]: Creating SSL connection to host
Aug 29 21:34:15 SERVER sSMTP[14718]: SSL connection using RSA_ARCFOUR_SHA1
Aug 29 21:34:18 SERVER sSMTP[14718]: Sent mail for root@ (221 2.0.0 closing connection t8sm11950610wiy.3) uid=0 username=root outbytes=872
Aug 29 21:34:18 SERVER mdadm[1176]: Fail event detected on md device /dev/md0, component device /dev/sdb1
Aug 29 21:34:51 SERVER kernel: [87255.792229] md: super_written gets error=-19, uptodate=0
Aug 29 21:34:51 SERVER kernel: [87255.792350] Aborting journal on device md0-8.
Aug 29 21:34:51 SERVER kernel: [87255.797504] Buffer I/O error on device md0, logical block 121667584
Aug 29 21:34:51 SERVER kernel: [87255.800227] lost page write due to I/O error on md0
Aug 29 21:34:51 SERVER kernel: [87255.800304] JBD2: I/O error detected when updating journal superblock for md0-8.
Aug 29 21:34:52 SERVER kernel: [87256.000083] md: super_written gets error=-19, uptodate=0
Aug 29 21:54:19 SERVER kernel: [88423.223581] md: super_written gets error=-19, uptodate=0
Aug 29 21:54:19 SERVER kernel: [88423.223676] md: super_written gets error=-19, uptodate=0

Aug 29 21:55:03 SERVER kernel: [88467.824060] Buffer I/O error on device md0, logical block 244190099
Aug 29 21:55:12 SERVER kernel: [88475.963839] quiet_error: 27 callbacks suppressed


(a million buffer I/O errors.....)

Aug 29 22:06:13 SERVER kernel: [    9.849598]  md0: unknown partition table

```


The other problem is when writing to the disks, it will start off around 60MB/s, then goes down to 30MB/s (fine as its usb2), but then it slowly lowers to around 14MB/s and stays there. This is a bit too slow for doing backups to as I will have to leave my pc on for about two days to do one backup! Bit annoying!



Any ideas are welcome :)

---

### Post by darkod on 2012-08-31
It might be a stupid question, but can't you install the disks as internal? Especially since you are suspecting the external box.

Also that should raise the transfer rate by a lot.

---

### Post by Frankincense93 on 2012-08-31
I would do, but I only have two internal SATA connectors, which currently has one for the system drive and one for a CD drive. In the future I will get a mobo with more SATA connectors, but for the moment I can only use usb2/3

---

### Post by darkod on 2012-08-31
SATA cards that will give you additional ports are very cheap.

This looks like connection related, double check if the cables are connected good in the external box, etc. Run smartmontools to get the smart data from the disks.

Other than that, I have no idea.

---

### Post by Frankincense93 on 2012-08-31
```
sudo smartctl -a -d usbjmicron /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-29-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST1000DM005 HD103SJ
Serial Number:    S246J90C439832
Firmware Version: 0957
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Aug 31 12:36:43 2012 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Total time to complete Offline
data collection:                (    0) seconds.
Offline data collection
capabilities:                    (0x00)  Offline data collection not supported.
SMART capabilities:            (0x0000) Automatic saving of SMART data                           is not implemented.
Error logging capability:        (0x00) Error logging NOT supported.
                                        No General Purpose Logging support.

SMART Error Log not supported
SMART Self-test Log not supported
Device does not support Selective Self Tests/Logging

```

```
sudo smartctl -a -d usbjmicron /dev/sdc
#smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-29-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST1000DM005 HD103SJ
Serial Number:    S246J90C439834
LU WWN Device Id: 5 0004cf 2075e1b26
Firmware Version: 1AJ10001
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Fri Aug 31 12:37:39 2012 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                ( 9240) seconds.
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
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 154) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   252   252   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   071   069   025    Pre-fail  Always       -       8959
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       146
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       244
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       37
191 G-Sense_Error_Rate      0x0022   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   058   000    Old_age   Always       -       32 (Min/Max 16/42)
195 Hardware_ECC_Recovered  0x003a   252   252   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       146

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```


Hmm they seem to return different amounts of data, anything to do with the fact they are port multiplied over usb?


The main problem is the write speeds im having. I would love to try them on a windows pc, but as they are in a software RAID and have no idea if there is a Windows equivalent thats out of the question.

Do you think its just because its over usb2?

---

### Post by darkod on 2012-08-31
I have no idea to be honest. Having two disks connected to your computer over usb cable, I'm not sure what that could do or not do.

I would consider that type of connection to be very unreliable, especially if you are planning this for some type of file server/storage or similar.

---

### Post by Frankincense93 on 2012-08-31
I would like to avoid buying a sata controller card at all costs, as buying the sharkoon box cost quite a bit of money that I dont want to waste., but cheers anyway :)

Does anyone have any other ideas?

---

### Post by Frankincense93 on 2012-09-21
When doing a write test, one hdd just decided to remove itself from the raid. This was in the syslog:

```
Sep 21 10:55:38 SERVER kernel: [ 6614.726584] scsi 7:0:0:0: Direct-Access     ST1000DM 005 HD103SJ           PQ: 0 ANSI: 2 CCS
Sep 21 10:55:38 SERVER kernel: [ 6614.733393] scsi 7:0:0:1: Direct-Access     ST1000DM 005 HD103SJ           PQ: 0 ANSI: 2 CCS
Sep 21 10:55:38 SERVER kernel: [ 6614.742074] sd 7:0:0:0: Attached scsi generic sg1 type 0
Sep 21 10:55:38 SERVER kernel: [ 6614.742827] sd 7:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Sep 21 10:55:38 SERVER kernel: [ 6614.743326] sd 7:0:0:0: [sdb] Write Protect is off
Sep 21 10:55:38 SERVER kernel: [ 6614.743336] sd 7:0:0:0: [sdb] Mode Sense: 28 00 00 00
Sep 21 10:55:38 SERVER kernel: [ 6614.743824] sd 7:0:0:0: [sdb] No Caching mode page present
Sep 21 10:55:38 SERVER kernel: [ 6614.743832] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 10:55:38 SERVER kernel: [ 6614.785251] sd 7:0:0:0: [sdb] No Caching mode page present
Sep 21 10:55:38 SERVER kernel: [ 6614.785859] sd 7:0:0:1: Attached scsi generic sg2 type 0
Sep 21 10:55:38 SERVER kernel: [ 6614.797780] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 10:55:41 SERVER sSMTP[2574]: Sent mail for root@ (221 2.0.0 closing connection eu4sm37059171wib.2) uid=0 username=root outbytes=805
Sep 21 10:55:41 SERVER mdadm[1249]: Fail event detected on md device /dev/md0
Sep 21 10:55:41 SERVER sSMTP[2587]: Creating SSL connection to host
Sep 21 10:55:41 SERVER sSMTP[2587]: SSL connection using RSA_ARCFOUR_SHA1
Sep 21 10:55:42 SERVER kernel: [ 6618.268322] usb 9-4: USB disconnect, device number 3
Sep 21 10:55:44 SERVER sSMTP[2587]: Sent mail for root@ (221 2.0.0 closing connection l5sm15753131wix.5) uid=0 username=root outbytes=858
Sep 21 10:55:44 SERVER mdadm[1249]: FailSpare event detected on md device /dev/md0, component device /dev/sdb
Sep 21 10:56:09 SERVER kernel: [ 6645.824607] sd 7:0:0:0: Device offlined - not ready after error recovery
Sep 21 10:56:09 SERVER kernel: [ 6645.831191] sd 7:0:0:1: [sdd] READ CAPACITY failed
Sep 21 10:56:09 SERVER kernel: [ 6645.837462] sd 7:0:0:1: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep 21 10:56:09 SERVER kernel: [ 6645.843766] sd 7:0:0:1: [sdd] Sense not available.
Sep 21 10:56:09 SERVER kernel: [ 6645.850125] sd 7:0:0:0: [sdb] Unhandled error code
Sep 21 10:56:09 SERVER kernel: [ 6645.856369] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep 21 10:56:09 SERVER kernel: [ 6645.856987] sd 7:0:0:1: [sdd] Write Protect is on
Sep 21 10:56:09 SERVER kernel: [ 6645.857002] sd 7:0:0:1: [sdd] Mode Sense: e1 93 bb fb
Sep 21 10:56:09 SERVER kernel: [ 6645.857051] sd 7:0:0:1: [sdd] No Caching mode page present
Sep 21 10:56:09 SERVER kernel: [ 6645.857059] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:09 SERVER kernel: [ 6645.887225] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Sep 21 10:56:09 SERVER kernel: [ 6645.893166] end_request: I/O error, dev sdb, sector 0
Sep 21 10:56:09 SERVER kernel: [ 6645.893415] sd 7:0:0:1: [sdd] READ CAPACITY failed
Sep 21 10:56:09 SERVER kernel: [ 6645.893429] sd 7:0:0:1: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep 21 10:56:09 SERVER kernel: [ 6645.893439] sd 7:0:0:1: [sdd] Sense not available.
Sep 21 10:56:09 SERVER kernel: [ 6645.893542] sd 7:0:0:1: [sdd] Write Protect is off
Sep 21 10:56:09 SERVER kernel: [ 6645.893552] sd 7:0:0:1: [sdd] Mode Sense: 00 00 00 00
Sep 21 10:56:09 SERVER kernel: [ 6645.893598] sd 7:0:0:1: [sdd] Asking for cache data failed
Sep 21 10:56:09 SERVER kernel: [ 6645.893605] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:09 SERVER kernel: [ 6645.893613] sd 7:0:0:1: [sdd] Attached SCSI disk
Sep 21 10:56:09 SERVER kernel: [ 6645.893986] sd 7:0:0:1: [sdd] READ CAPACITY failed
Sep 21 10:56:09 SERVER kernel: [ 6645.893993] sd 7:0:0:1: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep 21 10:56:09 SERVER kernel: [ 6645.894001] sd 7:0:0:1: [sdd] Sense not available.
Sep 21 10:56:09 SERVER kernel: [ 6645.894073] sd 7:0:0:1: [sdd] Asking for cache data failed
Sep 21 10:56:09 SERVER kernel: [ 6645.894080] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:09 SERVER kernel: [ 6645.894209] sd 7:0:0:1: [sdd] READ CAPACITY failed
Sep 21 10:56:09 SERVER kernel: [ 6645.894215] sd 7:0:0:1: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep 21 10:56:09 SERVER kernel: [ 6645.894224] sd 7:0:0:1: [sdd] Sense not available.
Sep 21 10:56:09 SERVER kernel: [ 6645.894294] sd 7:0:0:1: [sdd] Asking for cache data failed
Sep 21 10:56:09 SERVER kernel: [ 6645.894302] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:09 SERVER kernel: [ 6645.894215] sd 7:0:0:1: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep 21 10:56:09 SERVER kernel: [ 6645.894224] sd 7:0:0:1: [sdd] Sense not available.
Sep 21 10:56:09 SERVER kernel: [ 6645.894294] sd 7:0:0:1: [sdd] Asking for cache data failed
Sep 21 10:56:09 SERVER kernel: [ 6645.894302] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:09 SERVER ata_id[2592]: HDIO_GET_IDENTITY failed for '/dev/sdd': Invalid argument
Sep 21 10:56:10 SERVER kernel: [ 6645.993284] Buffer I/O error on device sdb, logical block 0
Sep 21 10:56:10 SERVER kernel: [ 6645.998704] ldm_validate_partition_table(): Disk read failed.
Sep 21 10:56:10 SERVER kernel: [ 6646.003214] Dev sdb: unable to read RDB block 0
Sep 21 10:56:10 SERVER kernel: [ 6646.007534]  sdb: unable to read partition table
Sep 21 10:56:10 SERVER ata_id[2603]: HDIO_GET_IDENTITY failed for '/dev/sdd': Invalid argument
Sep 21 10:56:10 SERVER kernel: [ 6646.016264] sd 7:0:0:0: [sdb] READ CAPACITY failed
Sep 21 10:56:10 SERVER kernel: [ 6646.020472] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Sep 21 10:56:10 SERVER kernel: [ 6646.024692] sd 7:0:0:0: [sdb] Sense not available.
Sep 21 10:56:10 SERVER ata_id[2602]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Sep 21 10:56:10 SERVER kernel: [ 6646.031267] sd 7:0:0:0: [sdb] Asking for cache data failed
Sep 21 10:56:10 SERVER kernel: [ 6646.035531] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 10:56:10 SERVER kernel: [ 6646.039728] sd 7:0:0:0: [sdb] Attached SCSI disk
Sep 21 10:56:10 SERVER kernel: [ 6646.288848] usb 9-4: new SuperSpeed USB device number 4 using xhci_hcd
Sep 21 10:56:10 SERVER kernel: [ 6646.313016] scsi8 : usb-storage 9-4:1.0
Sep 21 10:56:11 SERVER kernel: [ 6647.318741] scsi 8:0:0:0: Direct-Access     ST1000DM 005 HD103SJ           PQ: 0 ANSI: 2 CCS
Sep 21 10:56:11 SERVER kernel: [ 6647.324754] scsi 8:0:0:1: Direct-Access     ST1000DM 005 HD103SJ           PQ: 0 ANSI: 2 CCS
Sep 21 10:56:11 SERVER kernel: [ 6647.333426] sd 8:0:0:0: Attached scsi generic sg1 type 0
Sep 21 10:56:11 SERVER kernel: [ 6647.342276] sd 8:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Sep 21 10:56:11 SERVER kernel: [ 6647.347609] sd 8:0:0:1: Attached scsi generic sg2 type 0
Sep 21 10:56:11 SERVER kernel: [ 6647.353824] sd 8:0:0:0: [sdb] Write Protect is off
Sep 21 10:56:11 SERVER kernel: [ 6647.357986] sd 8:0:0:0: [sdb] Mode Sense: 28 00 00 00
Sep 21 10:56:11 SERVER kernel: [ 6647.362226] sd 8:0:0:1: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Sep 21 10:56:11 SERVER kernel: [ 6647.367103] sd 8:0:0:0: [sdb] No Caching mode page present
Sep 21 10:56:11 SERVER kernel: [ 6647.367489] sd 8:0:0:1: [sdd] Write Protect is off
Sep 21 10:56:11 SERVER kernel: [ 6647.367501] sd 8:0:0:1: [sdd] Mode Sense: 28 00 00 00
Sep 21 10:56:11 SERVER kernel: [ 6647.368138] sd 8:0:0:1: [sdd] No Caching mode page present
Sep 21 10:56:11 SERVER kernel: [ 6647.368150] sd 8:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:11 SERVER kernel: [ 6647.384692] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 10:56:11 SERVER kernel: [ 6647.390885] sd 8:0:0:1: [sdd] No Caching mode page present
Sep 21 10:56:11 SERVER kernel: [ 6647.394923] sd 8:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:11 SERVER kernel: [ 6647.396475] sd 8:0:0:0: [sdb] No Caching mode page present
Sep 21 10:56:11 SERVER kernel: [ 6647.396487] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 10:56:11 SERVER kernel: [ 6647.403895]  sdb: unknown partition table
Sep 21 10:56:11 SERVER kernel: [ 6647.411338] sd 8:0:0:0: [sdb] No Caching mode page present
Sep 21 10:56:11 SERVER kernel: [ 6647.416336] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep 21 10:56:11 SERVER kernel: [ 6647.421316] sd 8:0:0:0: [sdb] Attached SCSI disk
Sep 21 10:56:11 SERVER kernel: [ 6647.433012]  sdd: sdd1
Sep 21 10:56:42 SERVER kernel: [ 6677.937158] usb 9-4: reset SuperSpeed USB device number 4 using xhci_hcd
Sep 21 10:56:42 SERVER kernel: [ 6677.957394] xhci_hcd 0000:01:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801232cdc00
Sep 21 10:56:42 SERVER kernel: [ 6677.962511] xhci_hcd 0000:01:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801232cdc40
Sep 21 10:56:42 SERVER kernel: [ 6677.973659] sd 8:0:0:1: [sdd] No Caching mode page present
Sep 21 10:56:42 SERVER kernel: [ 6677.978691] sd 8:0:0:1: [sdd] Assuming drive cache: write through
Sep 21 10:56:42 SERVER kernel: [ 6677.983620] sd 8:0:0:1: [sdd] Attached SCSI disk
Sep 21 10:56:50 SERVER kernel: [ 6685.937162] usb 9-4: reset SuperSpeed USB device number 4 using xhci_hcd
Sep 21 10:56:50 SERVER kernel: [ 6685.957325] xhci_hcd 0000:01:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801232cdc00
Sep 21 10:56:50 SERVER kernel: [ 6685.962403] xhci_hcd 0000:01:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801232cdc40
Sep 21 10:57:06 SERVER kernel: [ 6702.361504] md: super_written gets error=-19, uptodate=0

```

After restart, everything is fine again! This type of problem seems to keep occurring. The SMART program fails to read, it cant open a device, it cant enumerate the usb port, the device needs a resync or the drive just removes itself.

Could this be a chipset/JMicron problem?

---

### Post by Frankincense93 on 2012-09-21
I have now installed a new motherboard, a usb 3 pcie card and using a new usb 3 cable, and the problem still persists.


The whole reason I got the sharkoon 5 bay box was because I wanted a small server with external hdds, and when using its raid function they were incredibly slow, so change it to 'clear raid' mode i.e JBOD. RAID created ok, but it randomly dies, and doesn't like being told to sleep ( this thread - [http://ubuntuforums.org/showthread.php?t=2060425](http://ubuntuforums.org/showthread.php?t=2060425) ).

Is there anything I can try (new kernal/driver) to stop this annoying disconnection/enumeration problem?

Or is it worth trying to return and getting a different raid box?

---

### Post by darkod on 2012-09-21
As I said earlier, in my experience (which might be limited) I think your problem is not in your computer or the sharkoon box.

It's the way you are trying to use the disks in the box as separate disks (JBOD) but over one single usb cable. I have never ever seen anyone trying to make a sustained connection like that.

If you used the sharkoon raid, that would be fine since the array is created on level of the sharkoon firmware and over the usb you see one device, like any plain external usb hdd. But you say you are not happy with the sharkoon raid performance and are trying to use multiple disks over single usb cable.

---

### Post by Frankincense93 on 2012-09-21
> **darkod said:**
> As I said earlier, in my experience (which might be limited) I think your problem is not in your computer or the sharkoon box.

It's the way you are trying to use the disks in the box as separate disks (JBOD) but over one single usb cable. I have never ever seen anyone trying to make a sustained connection like that.

If you used the sharkoon raid, that would be fine since the array is created on level of the sharkoon firmware and over the usb you see one device, like any plain external usb hdd. But you say you are not happy with the sharkoon raid performance and are trying to use multiple disks over single usb cable.

But surely someone has tried it before successfully? Its not like  im asking for much, just the drives to stay connected over usb.

I have no idea what I will do if I can't get this working. I don't want to buy a full sized box just so I can fit 6 internal hdds in, and all the external RAID boxes are probably going to be too slow

---

### Post by darkod on 2012-09-21
I assume (and this is only my assumption) that you will always have problems with the order of the disks.

When connected to your motherboard, the BIOS scans them in order of the SATA ports starting at SATA0 or SATA1 depending on the board. And they get assigned device names /dev/sda, /dev/sdb, etc in that order.

With many disks over usb cable, you do you expect the computer to decide to order them every single time in the same order? I wouldn't expect that.

When these types of boxes are used usually you use the built-in raid function and the whole device is like a single disk/device attached through usb. In that case there is nothing really to order because it's only one device so your computer doesn't have issues with it. And the array and disk order internally in the sharkoon is done by its own firmware which is linux based and creates mdadm array from the physical disks.

I can't really see a way out of this. Not without using some sort of small computer/server like the HP Proliant Microserver for example, but that has only 4 slots for disks. You set up mdadm array on it and connect it in your LAN so all computers can use it, not only one.

Even though usb specs mentioned high theoretical transfer speeds, I wouldn't say usb, even USB3, is faster than a small server on your Gigabit LAN. I might be wrong with the new USB3 though, haven't used it.

---

### Post by Frankincense93 on 2012-09-21
Ok, so unless someone can think of a brilliant idea to fix this my choices are: 
[LIST]
[*]Buy a port multiplier so I can plug in the esata cable and do the same thing but over sata.
[*]Live with it and have to fix it everytime it disconnects.
[*]Buy a new case that can fit all the necessary drives.
[*]Setup the in-box raid again and live with the speed.
[/LIST]

Hmmmmmm

---

### Post by darkod on 2012-09-21
I am not sure esata card/connection can help. Basically it's the same like usb only over different protocol. It's still single cable for multiple disks and I have no idea how they will be seen by the computer.

If we were talking about internal 4-port sata card for example, to enlarge number of disks inside, then yes, in that case they receive unique /dev/sdX device name and keep it unless you move the connection to another sata port.

But just changing the way the sharkoon box connects, whether usb or esata, I don't think you can expect much difference.

---

### Post by Frankincense93 on 2012-09-21
Well this project has turned out to be a lot harder that I thought. Looks like either a larger case, feed backplane sata cables through the back or actually using the raid box are my only options :(

I will give the raid box another go and see what speeds I get over usb 3 first

---

### Post by Frankincense93 on 2012-09-22
Ok I have re-build the RAID 1 using the raid box itself, and the speeds seemed to be pretty darn good (hovers around 55MB/s which is easily quick enough for what I want.


BUUUT massive problems, as it will randomly disconnect itself and cause a mass of errors (I got about 35% of a backup done)

This are the errors:
```

Sep 22 12:01:00 SERVER kernel: [ 9843.598651] EXT4-fs error (device sdb1): ext4_find_entry:935: inode #2: comm smbd: reading directory lblock 0
Sep 22 12:01:28 SERVER kernel: [ 9871.848373] hub 9-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
Sep 22 12:01:28 SERVER kernel: [ 9871.848530] usb 9-4: USB disconnect, device number 4
Sep 22 12:01:39 SERVER kernel: [ 9882.836859] usb 9-4: new SuperSpeed USB device number 5 using xhci_hcd

sd 9:0:0:0: Device offlined - not ready after error recovery

Buffer I/O error on device sdc1, logical block 69007438

EXT4-fs warning (device sdc1): ext4_end_bio:251: I/O error writing to inode 39059464 (offset 805273600 size 12288 starting block 69007695)

JBD2: Detected IO errors while flushing file data on sdc1-8

EXT4-fs error (device sdc1): ext4_journal_start_sb:327: Detected aborted journal

previous I/O error to superblock detected

JBD2: Detected IO errors while flushing file data on sdc1-8

journal commit I/O error

EXT4-fs error (device sdc1): ext4_find_entry:935: inode #2: comm sshd: reading directory lblock 0

USB core suspending device not in U0/U1/U2.

xhci_hcd 0000:01:00.0: ERROR no room on ep ring
```

Also alot of:

```

[24459.952297] xhci_hcd 0000:01:00.0: USB core suspending device not in U0/U1/U2.
[24459.953780] xhci_hcd 0000:01:00.0: ERROR no room on ep ring
[24459.959438] hub 8-1:1.0: activate --> -12

```

And after this all happens I get:

```

ls: reading directory /media/RAID: Input/output error

```

---

### Post by Frankincense93 on 2012-09-24
I have no Idea why this is happening, unless it related to the box in some way, as I have changed the motherboard, the cable, and tried both usb 2 and 3 :/

---

### Post by darkod on 2012-09-24
If the raid of the box doesn't work either actually it might be a faulty box or one of the disks.

---

### Post by Frankincense93 on 2012-09-24
Im not sure how I can test this without getting a new box though? Is there anyway of making a windows machine report a usb disconnect? As my main pc is windows 7 which could be used to test it if needed.

---

### Post by darkod on 2012-09-24
You can try attaching the sharkoon to another computer (ubuntu or windows) and see how it goes. If it also drops the usb connection, it would point to the box I guess. If it works perfectly fine on another machine, it's something in the way you are connecting it and using it on the first machine.

I don't know what else to suggest. You are trying to use the sharkoon as storage connected to a ubuntu server machine, right? Does it have ethernet port so you can use the box directly in the network?

---

### Post by Frankincense93 on 2012-09-24
Unfortunately the only connects are USB3 and eSATA, so I guess my next tests are try eSATA again to see if it drops/test the speed, and also try the same on my windows PC. I shall report back my findings

---

### Post by Frankincense93 on 2012-09-25
Ok, well firstly I plugged in view USB 3 to my windows PC and copied a 45GB file from/to the box over and over to see if it dropped. And it didn't which clearly suggests a system problem on my servers side.

Then I tried to connect the box to my server over esata via a sata > esata connector. The speed in local transfer for reading was around 35MB/s and writing was near 60MB/s which is ok for what I want. (and as far as I know it hasn't dropped yet).

So I will keep it as esata for the moment, but I really would like to fix the usb3 problem still (as I think it gave better speeds which I may need in the future).

What can I check/change to test what seems to be failing with the USB connection?

---

