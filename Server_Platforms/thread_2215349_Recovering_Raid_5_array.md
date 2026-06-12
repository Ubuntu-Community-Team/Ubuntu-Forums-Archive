---
title: "Recovering Raid 5 array"
date: 2014-04-06
forum: Server Platforms
---

### Post by minh3 on 2014-04-06
I was able to assemble my raid 5 array yesterday that died a few days ago (I believe because of a power outage). I pulled this from an LG N4B2N enclosure and put them into my desktop for recovery. Everything was going fine and transferred about 400 GB then I wake up this morning to find I could no longer access the raid. 

When doing mdadm --detail --scan it outputs
```
ARRAY /dev/md/0 metadata=1.2 name=ubuntu:0 UUID=71a3d1c2:6e88fe2f:3b7421b2:00f047e5
ARRAY /dev/md/0_0 metadata=0.90 UUID=df8e4334:9cf8c232:a1396284:b66cd2d0
```

I tried remounting and found that 1 drive would not remount... however:

```
root@ubuntu:~# mdadm --assemble --run --force /dev/md0 /dev/sd[bcde]3    
mdadm: no RAID superblock on /dev/sdc3
mdadm: /dev/sdc3 has no superblock - assembly aborted
```

When I assemble without "sdc3" from the following

        mdadm --assemble --force --run /dev/md0 /dev/sd[bde]3

mdadm.conf shows this:
```

ARRAY /dev/md0 UUID=df8e4334:9cf8c232:a1396284:b66cd2d0
ARRAY /dev/md1 UUID=f60c2cf1:e1e219d5:08efab1b:91be7490
ARRAY /dev/md0 UUID=a47359a9:1a1574eb:58685b67:0d16a8bc
```

mdadm --misc --examine /dev/sd[bcde]3 shows this:

[http://pastebin.com/3T2sbURL](http://pastebin.com/3T2sbURL)

It says it's been started with 3 drives out of 4. However, my linux/raid skills are limited and I'm not sure what to do from here or if I"m doing anything right at all.

Also did a smartctl on /dev/sdc3

```
root@ubuntu:~# smartctl -d ata -a /dev/sdc
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-12-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA3211428
LU WWN Device Id: 5 0014ee 6561c5396
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun Apr  6 13:55:48 2014 UTC
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
data collection:         (37200) seconds.
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
recommended polling time:      ( 359) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   198   198   051    Pre-fail  Always       -       981
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       1000
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       61
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       9
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   063   063   000    Old_age   Always       -       27235
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       59
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       25
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       738186
194 Temperature_Celsius     0x0022   112   084   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   191   191   000    Old_age   Always       -       9
197 Current_Pending_Sector  0x0032   196   196   000    Old_age   Always       -       1390
198 Offline_Uncorrectable   0x0030   199   197   000    Old_age   Offline      -       346
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   001   001   000    Old_age   Offline      -       195149

SMART Error Log Version: 1
ATA Error Count: 313 (device log contains only the most recent five errors)
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

Error 313 occurred at disk power-on lifetime: 26913 hours (1121 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  e0 00 00 00 00 00 a0 08  45d+21:49:37.136  STANDBY IMMEDIATE
  ec 00 00 00 00 00 a0 08  45d+21:49:37.106  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  45d+21:49:37.106  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  45d+21:49:37.101  IDENTIFY DEVICE

Error 312 occurred at disk power-on lifetime: 26913 hours (1121 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 08  45d+21:49:37.106  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  45d+21:49:37.101  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  45d+21:49:37.062  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  45d+21:49:37.062  SET FEATURES [Set transfer mode]

Error 311 occurred at disk power-on lifetime: 26913 hours (1121 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 08  45d+21:49:37.062  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  45d+21:49:37.057  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  45d+21:49:37.018  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  45d+21:49:37.018  SET FEATURES [Set transfer mode]

Error 310 occurred at disk power-on lifetime: 26913 hours (1121 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 08  45d+21:49:37.018  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  45d+21:49:37.014  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  45d+21:49:36.975  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  45d+21:49:36.975  SET FEATURES [Set transfer mode]

Error 309 occurred at disk power-on lifetime: 26913 hours (1121 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 08  45d+21:49:36.975  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 08  45d+21:49:36.970  IDENTIFY DEVICE
  ec 00 00 00 00 00 a0 08  45d+21:49:36.931  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08  45d+21:49:36.931  SET FEATURES [Set transfer mode]


```

---

### Post by rubylaser on 2014-04-07
sdc has failed based on your SMART data.  I know it says that it passed, but you have a number of uncorrectable errors and pending sectors, so you won't want to trust your data to it.  If the drive is still in warranty, I would RMA it.  In the meantime, pick yourself up another drive and add it back to the array so that one more disk failure doesn't wipe you out.  

If your array is started with 3 out of 4 drives, have you tried to mount it to verify your data is intact? Finally, if it is mountable and if any of this data is important to you, I'd make sure you have a good backup of it.

---

### Post by frostschutz on 2014-04-07
sdc is a failed drive

examine output is wrong. sdc shows a 0.90 superblock, creation date Sat Oct  6 12:00:16 2012; the others see a 1.2 superblock, creation date Sun Apr  6 12:40:34 2014. That was yesterday so it seems you did a mdadm --create at some point?

If you did, and let it sync, you killed your data with it. If it did not sync, some data may still be recoverable, but since 1.2 header is at the start vs. 0.90 at the end, the superblock or whatever stored at the start of the md will be damaged.

---

### Post by minh3 on 2014-04-07
Crap, I did do a create at some point because I thought that was what I was suppose to do. :(

So I guess I'm screwed on this data? 

When I do

mdadm --assemble --force --run /dev/md0 /dev/sd[bde]3 

The array assembles, but I don't know how to accses the data from there. As it does nothing, before it would pop up at that point. Does that mean it's bad? or did I not put it in the right order?

---

### Post by rubylaser on 2014-04-07
If you ran --create without the --assume-clean flag and the disks being in the proper order, your data is gone unfortunately :(

---

### Post by frostschutz on 2014-04-07
> **minh3 said:**
> So I guess I'm screwed on this data?

Pretty much.

It depends on many things, like, what was the exact create command you used. Did you use it along with --assume-clean, missing. If it synced, how far did it sync since you have a defective drive. Etc. What was on the raid; lvm, crypt, filesystem (which), ...

In theory, it's possible to roll back a single botched sync. parity data of new[wrong] raid is defective data in the old[correct] raid which can be restored by using parity of the old[correct] raid. However, there are no tools for it.

---

### Post by minh3 on 2014-04-07
Damn. 

I'm 50/50 if I used the --assume-clean,missing. I think I didn't let it sync long, but I could be wrong. I think it was ext2. So I guess me repairing the array is not worth my time?

---

### Post by frostschutz on 2014-04-08
Well, it's possible you did use missing, since one drive still shows old metadata. You might be able to salvage something then, if you can come up with the correct create command and drive order. Your drive letters seem to have changed at some point, so I can't provide you with an exact command, it's something like this:

Note: ideally you'd make a 1:1 copy of every disk before making such experiments

```
mdadm --create /dev/md42 --metadata=0.90 --level=5 --chunk=64 --raid-devices=4 --assume-clean missing /dev/sdb3 /dev/sdd3 /dev/sde3
mdadm --readonly /dev/md42
```

the --readonly is important so no matter what you do, you won't write anything to the raid. writing at this point would only cause further damage.

missing is the placeholder for /dev/sdc3 which has those reallocated/pending sectors (I hope your other drives are okay). according to the metadata on sdc3, it was also the first drive, so missing is first in that command. That much we know. However, I do not know the correct order for sdb3 sdd3 sde3 since your drive letters changed and the old metadata is gone; and that's a problem since as long as this order is wrong, you won't get anything useful from it. You'll have to permutate these three until you find the correct order. I.e. create the raid, run testdisk/photorec on it. If it find some file larger than 256k that is intact, you have the correct order; otherwise it's the wrong order, and you have to stop the raid, and re-create it with /dev/sdb3 /dev/sdd3 /dev/sde3 in a different order. With three drives in question there are not that many possibilities.

```
mdadm --stop /dev/md42
mdadm ... missing /dev/sdb3 /dev/sdd3 /dev/sde3
mdadm ... missing /dev/sdb3 /dev/sde3 /dev/sdd3
mdadm ... missing /dev/sdd3 /dev/sdb3 /dev/sde3
mdadm ... missing /dev/sdd3 /dev/sde3 /dev/sdb3
mdadm ... missing /dev/sde3 /dev/sdb3 /dev/sdd3
mdadm ... missing /dev/sde3 /dev/sdd3 /dev/sdb3
```

If there was a filesystem on it directly (w/o partitions, lvm, ...) you most likely won't be able to mount it in either order since the filesystem superblock was overwritten by the 1.2 mdadm metadata.

If it was LUKS encrypted, you won't be able to get any data back since the 1.2 mdadm metadata would have killed your LUKS header.

---

