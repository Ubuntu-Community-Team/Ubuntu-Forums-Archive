---
title: "HDD Failing... But There's Nothing Wrong With It."
date: 2012-06-05
forum: Server Platforms
---

### Post by Bushflyr on 2012-06-05
I've had a reoccurring error on my system that I thought I had solved (not by my actions, it just went away) I'm running 12.04 Server with 1 System drive (sda), and 4 storage drives (sd[bcde]) in a 3 drive mdadm RAID 5 with 1 spare. 

The problem is that drives randomly drop out of the RAID. I've checked the SMART status and found no errors.

A couple days ago 2 drives "failed" resulting the loss of all the data on the server. I couldn't reconstruct the RAID in a way that saved it. No biggie, all my music is backed up in 2 other places and the other stuff as well. But it's SEVERELY irritating that I can't seem to figure out this issue.

Here is what I think is the important bit of syslog:

```

Jun  5 11:50:30 mars afpd[2351]: AFP3.3 Login by scot
Jun  5 11:50:30 mars afpd[2351]: afp_disconnect: trying primary reconnect
Jun  5 11:50:30 mars afpd[1283]: Reconnect: transfering session to child[2188]
Jun  5 11:50:30 mars afpd[1283]: Reconnect: killing new session child[2351] after transfer
Jun  5 11:50:32 mars afpd[2351]: afp_disconnect: primary reconnect succeeded
Jun  5 11:50:57 mars kernel: [15026.912036] ata3: SRST failed (errno=-16)
Jun  5 11:50:57 mars kernel: [15026.912072] ata3: limiting SATA link speed to 1.5 Gbps
Jun  5 11:50:57 mars kernel: [15026.912081] ata3: hard resetting link
Jun  5 11:51:02 mars kernel: [15031.922949] ata3: SRST failed (errno=-16)
Jun  5 11:51:02 mars kernel: [15031.934529] ata3: reset failed, giving up
Jun  5 11:51:02 mars kernel: [15031.934553] ata3.00: disabled
Jun  5 11:51:02 mars kernel: [15031.934557] ata3.00: device reported invalid CHS sector 0
Jun  5 11:51:02 mars kernel: [15031.934565] ata3: EH complete
Jun  5 11:51:02 mars kernel: [15031.934607] sd 2:0:0:0: [sdd] Unhandled error code
Jun  5 11:51:02 mars kernel: [15031.934609] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun  5 11:51:02 mars kernel: [15031.934613] sd 2:0:0:0: [sdd] CDB: Write(10): 2a 00 00 00 00 08 00 00 02 00
Jun  5 11:51:02 mars kernel: [15031.934633] end_request: I/O error, dev sdd, sector 8
Jun  5 11:51:02 mars kernel: [15031.934658] end_request: I/O error, dev sdd, sector 8
Jun  5 11:51:02 mars kernel: [15031.934681] md: super_written gets error=-5, uptodate=0
Jun  5 11:51:02 mars kernel: [15031.934684] md/raid:md0: Disk failure on sdd, disabling device.
Jun  5 11:51:02 mars kernel: [15031.934685] md/raid:md0: Operation continuing on 2 devices.
Jun  5 11:51:02 mars kernel: [15032.376129] RAID conf printout:
Jun  5 11:51:02 mars kernel: [15032.376133]  --- level:5 rd:3 wd:2
Jun  5 11:51:02 mars kernel: [15032.376136]  disk 0, o:1, dev:sdb
Jun  5 11:51:02 mars kernel: [15032.376138]  disk 1, o:1, dev:sdc
Jun  5 11:51:02 mars kernel: [15032.376140]  disk 2, o:0, dev:sdd
Jun  5 11:51:02 mars kernel: [15032.382835] RAID conf printout:
Jun  5 11:51:02 mars kernel: [15032.382839]  --- level:5 rd:3 wd:2
Jun  5 11:51:02 mars kernel: [15032.382842]  disk 0, o:1, dev:sdb
Jun  5 11:51:02 mars kernel: [15032.382844]  disk 1, o:1, dev:sdc
Jun  5 11:51:04 mars afpd[2188]: afp_dsi_transfer_session: succesfull primary reconnect
Jun  5 11:51:06 mars mdadm[1264]: Fail event detected on md device /dev/md0
Jun  5 11:51:09 mars mdadm[1264]: FailSpare event detected on md device /dev/md0, component device /dev/sdd
Jun  5 11:55:01 mars CRON[2362]: (root) CMD (/usr/local/sbin/continuous.sh)
Jun  5 12:00:01 mars CRON[2371]: (root) CMD (/usr/local/sbin/continuous.sh)
Jun  5 12:05:01 mars CRON[2380]: (root) CMD (/usr/local/sbin/continuous.sh)
Jun  5 12:06:01 mars CRON[2385]: (root) CMD (/usr/local/sbin/hourly.sh)
Jun  5 12:06:02 mars logger: HDTEMP for /dev/sda is 46
Jun  5 12:06:02 mars logger: HDTEMP for /dev/sdb is 44
Jun  5 12:06:02 mars logger: HDTEMP for /dev/sdc is 43
Jun  5 12:06:02 mars logger: HDTEMP for /dev/sdd is /dev/sdd: : S.M.A.R.T. not available
Jun  5 12:06:02 mars logger: HDTEMP for /dev/sde is 
Jun  5 12:06:25 mars afpd[2188]: AFP logout by scot
Jun  5 12:06:25 mars afpd[2188]: AFP statistics: 60265074.25 KB read, 53074.22 KB written
Jun  5 12:06:25 mars afpd[2188]: done
Jun  5 12:07:11 mars ata_id[2457]: HDIO_GET_IDENTITY failed for '/dev/sdd': No message of desired type
Jun  5 12:07:11 mars kernel: [16001.403458] sd 2:0:0:0: [sdd] Unhandled error code
Jun  5 12:07:11 mars kernel: [16001.403460] sd 2:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun  5 12:07:11 mars kernel: [16001.403462] sd 2:0:0:0: [sdd] CDB: Read(10): 28 00 e8 e0 88 00 00 00 08 00
Jun  5 12:07:11 mars kernel: [16001.403467] end_request: I/O error, dev sdd, sector 3907028992
Jun  5 12:07:11 mars kernel: [16001.403485] Buffer I/O error on device sdd, logical block 488378624

```

Oddly enough I seem to be missing my spare:

```
 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[0] sdc[1] sdd[4](F)
      3907025920 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
      
unused devices: <none>

```

but was able to add it in manually and get things rebuilding:

```
 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[0] sdc[1]
      3907025920 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
      
unused devices: <none>

```

This whole thing failed shortly after I began a TimeMachine backup from my Mac, so it was under load, but I had just successfully transfered some 600GB of music to it in one chunck and the drives don't seem too hot, so.... :confused:

---

### Post by rubylaser on 2012-06-05
Looking at your syslog /dev/sdd is reporting both bad blocks and bad sectors.  I'd remove this disk from your mdadm array and then write zeros to it.  This will allow the hard drive to map out all of the bad sectors, and could root out a failing drive.

```
mdadm /dev/md0 --fail /dev/sdd --remove /dev/sdd
```

Then, you can fill it with zeros like this (CAUTION: This will take a really long time depending on the size of your hard drive). You can watch the status of dd like [this]("http://zackreed.me/articles/43-monitor-progress-of-dd-command").
```
dd if=/dev/zero of=/dev/sdd bs=1M
```

or you can use badblocks
```
badblocks /dev/sdd > ~/bad-blocks
```
then feed this list of badblocks to fsck to mark the sectors as bad
```
fsck -l ~/bad-blocks /dev/sdd
```

---

### Post by Bushflyr on 2012-06-05
Thanks, I'll do that right now. 

Also, since the failure I've been getting a:

```
 The Disk drive for /mnt/marsraid is not ready or not present.
Continue to wait. or press S to skip mounting or M for manual recovery.
```

error. Even after rebuilding the RAID and rebooting what should have been a clean md0. :confused:

---

### Post by rubylaser on 2012-06-05
After you see this error do you skip it and then just mount the array, or do you have to assemble it first and then mount it?

---

### Post by Bushflyr on 2012-06-05
That I'm not certain of. I wound up skipping the mount. As soon as I logged in I checked and got: 

```
[~]: cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb[0](S) sdd[4](S) sdc[1](S) sde[3](S)
      7814054240 blocks super 1.2
       
unused devices: <none>
```

I'm not sure if that means it was mountable or not. I then stopped the array in order to run bad blocks. 

```
[~]: sudo mdadm /dev/md0 --fail /dev/sdd --remove /dev/sdd
mdadm: cannot get array info for /dev/md0
```

```

[~]: sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
[~]: sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 1 drive and  1 rebuilding - not enough to start the array.
[~]: cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd[4](S) sdc[1](S) sde[3](S) sdb[0](S)
      7814054240 blocks super 1.2
       
unused devices: <none>
```

Now I'm running badblocks. It may take a while, it's a 2tb disk, but nothing has shown up in the ~bad-blocks file yet.

---

### Post by Bushflyr on 2012-06-06
cat ~bad-blocks shows nothing. Which is about what I expected since I've run SMART long tests on these drives before. It's got to be something else. Maybe TimeMachine doing something?

---

### Post by rubylaser on 2012-06-06
Your syslog reports bad sectors on that disk.  Can you post the output of this?

```
smartctl --test=long /dev/sdd
```
Wait for that to finish and then post the results of this command
```
smartctl -a /dev/sdd
```

If that's still inconclusive, I'd run the dd to that drive to rule out the hard drive and SATA cable.

Finally, I noticed your mdadm array was showing all the disks as spares and was not assembled.  Can you post the output of this too?

```
mdadm -E /dev/sd[bce]
```

---

### Post by Bushflyr on 2012-06-06
```
smartctl --test=long /dev/sdd
```

Is running now. However, I've done that test before when other disks dropped out (Ref. [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1955490")) no errors were returned. Maybe something will pop this time.

```
mdadm -E /dev/sd[bce]
```

Gives me:

```
[~]: sudo mdadm -E /dev/sd[bce]
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 76296407:b83bc558:e03e2de9:cb5f4eed
           Name : mars:0  (local to host mars)
  Creation Time : Mon Jun  4 11:39:23 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : a692b6d9:d8d2d8e0:259f92c2:74b87f76

    Update Time : Tue Jun  5 13:29:41 2012
       Checksum : b7878d66 - correct
         Events : 8408

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 76296407:b83bc558:e03e2de9:cb5f4eed
           Name : mars:0  (local to host mars)
  Creation Time : Mon Jun  4 11:39:23 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : ad2d777d:add06582:51faba26:e1d67a96

    Update Time : Tue Jun  5 13:31:42 2012
       Checksum : 80f9a056 - correct
         Events : 8412

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AA ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : 76296407:b83bc558:e03e2de9:cb5f4eed
           Name : mars:0  (local to host mars)
  Creation Time : Mon Jun  4 11:39:23 2012
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
Recovery Offset : 30311168 sectors
          State : active
    Device UUID : e1246e14:8b9cd762:5176714b:569841d8

    Update Time : Tue Jun  5 13:31:42 2012
       Checksum : 60ae23e1 - correct
         Events : 8412

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AA ('A' == active, '.' == missing)
```

Once again, thanks for the assistance. I REALLY appreciate it.

---

### Post by rubylaser on 2012-06-06
Ah, thank you for jogging my memory, I remember your situation now.  In the past you where having problems with /dev/sdc, is this the same disk showing up in a new location?  

Your events counter is slightly lower on /dev/sdb, but re-assembling the array shouldn't be a problem when you're done.  I would do the dd to /dev/sdd as I showed previously to rule the disk out as a problem.  

If it still looks good via smart when that's all done, I'd add it back to the array.

---

### Post by Bushflyr on 2012-06-06
No, I haven't swapped disk locations or SATA cables/ports, so I'm pretty sure it's a different physical disk. Unless the system randomly reassigns drive designators. And this whole thing started with 2 drives "failing".

These are "green" disks, IDK if that matters, but I still have the feeling (from last time) that it has something to do with TimeMachine and that the drives are physically OK.

I'll definitely run dd on it as soon as smartctl finishes.

---

### Post by rubylaser on 2012-06-06
Please do.  Just so you know, I have an mdadm array (made up of Seagate Green Edition drives) at home that backs up my wife's MacBook Pro via Timemachine and it's worked flawlessly for a couple of years now.

---

### Post by Bushflyr on 2012-06-06
Good to know it's possible. :) I really want to figure this thing out and get it stable, so I trust it. Great learning experience, though.

---

### Post by Bushflyr on 2012-06-06
OK, smartctl is done. Not exactly how to read everything, but I don't see anything glaring. Running dd next.

```
[~]: sudo smartctl -a /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-24-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    6YD20Z3H
LU WWN Device Id: 5 000c50 046e0c667
Firmware Version: CC3C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Wed Jun  6 12:17:19 2012 HST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  612) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x30b7)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       530264
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       185
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   069   060   030    Pre-fail  Always       -       4302679280
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1647
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       191
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   099   099   000    Old_age   Always       -       5
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   059   050   045    Old_age   Always       -       41 (Min/Max 32/46)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       68
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       194
194 Temperature_Celsius     0x0022   041   050   000    Old_age   Always       -       41 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   036   006   000    Old_age   Always       -       530264
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       124180389430795
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1750404724
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1964272066

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1647         -
# 2  Short offline       Completed without error       00%      1512         -
# 3  Short offline       Completed without error       00%        42         -

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

### Post by rubylaser on 2012-06-06
Nope, everything looks good on that disk.  Proceed with the dd to rule out the disk.

---

### Post by Bushflyr on 2012-06-06
Did:
```
sudo dd if=/dev/zero of=/dev/sdd bs=1M
```

Got

```

.....snip.....

1907614+21 records in
1907614+21 records out
2000288026624 bytes (2.0 TB) copied, 18097.1 s, 111 MB/s
dd: writing `/dev/sdd': No space left on device
1907720+21 records in
1907719+21 records out
2000398934016 bytes (2.0 TB) copied, 18098.8 s, 111 MB/s

```

I'm assuming that means no errors. Which is good. But it still means there's a problem in there somewhere. 

What next?

---

### Post by Bushflyr on 2012-06-07
Ideas? :confused:

---

### Post by nj_peeps on 2012-06-07
Try reseating the SATA cable on both ends for that drive.  That some times can account for read/write errors.  If you are still getting errors, try another cable on that drive and see if that helps.  I had a similar problem with my RAID last year, and that helped me.

---

### Post by rubylaser on 2012-06-07
> **Bushflyr said:**
> Did:
```
sudo dd if=/dev/zero of=/dev/sdd bs=1M
```

Got

```

.....snip.....

1907614+21 records in
1907614+21 records out
2000288026624 bytes (2.0 TB) copied, 18097.1 s, 111 MB/s
dd: writing `/dev/sdd': No space left on device
1907720+21 records in
1907719+21 records out
2000398934016 bytes (2.0 TB) copied, 18098.8 s, 111 MB/s

```

I'm assuming that means no errors. Which is good. But it still means there's a problem in there somewhere. 

What next?

That doesn't tell you anything other than the drive isn't bad.  But, it could have had some bad sectors that writing zeroes to the whole disk would have identified.  I would try a different SATA cable and a different SATA head on the motherboard. After you've done that, I'd reassemble your array, and then add /dev/sdd back into the array.

---

### Post by Bushflyr on 2012-06-07
OK, thanks very much for the help. Guess I'll order a couple cables and see how it goes. Then completely reformat all the drives and start again from scratch. Hopefully a clean slate can help.

---

### Post by Bushflyr on 2012-06-09
Update. I completely reconstructed the RAID from scratch including repartitioning all drives. Created an new ext4 file system. 

Began a TM backup which failed about ~10% of the way through. :mad:

It wound up taking down the entire Server AND ALL network connectivity on my mac.  Got the network back on my mac by unplugging the ethernet cable from the **server** to the router. MegaWTF?

Tried rebooting the server and got a "No operating system found" message. I found out previously that no number of regular reboots would fix the problem, but unplugging the server from the wall would get it up again. It takes 2 reboots then I get the standard inactive RAID message.

I skip mounting and the server is up again, but with no RAID:

```
[~]: cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[1] sde1[3] sdd1[4]
      5860534486 blocks super 1.2
       
unused devices: <none>
```

Looks like sdb went missing this time.

Then I:

```
[~]: sudo mdadm --assemble /dev/md0
mdadm: /dev/md0 is already in use.
[~]: sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Jun  8 11:47:08 2012
     Raid Level : raid5
  Used Dev Size : 1953510912 (1863.01 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Jun  8 20:41:37 2012
          State : active, degraded, Not Started 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : mars:0  (local to host mars)
           UUID : 87d38482:509a4caa:419a2314:9208d3ef
         Events : 41

    Number   Major   Minor   RaidDevice State
       3       8       65        0      spare rebuilding   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
       4       8       49        2      active sync   /dev/sdd1
[~]: cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[1] sde1[3] sdd1[4]
      5860534486 blocks super 1.2
       
unused devices: <none>

/var/log]: sudo mdadm --stop /dev/md0 
mdadm: stopped /dev/md0
[/var/log]: sudo mdadm --assemble /dev/md0
mdadm: /dev/md0 assembled from 2 drives and  1 rebuilding - not enough to start the array while not clean - consider --force.
[/var/log]: cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sde1[3] sdd1[4] sdc1[1]
      3907021824 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [_UU]
      [>....................]  resync =  0.1% (2103756/1953510912) finish=293.7min speed=110724K/sec
      
unused devices: <none>


```


Does this shed any further light on my issue?

---

### Post by Gompa on 2012-06-10
what brand disks are we talking about ?
i know there is a problem with WD green disks and head-parking that can severely shorten the life time.
when these disks fail they dont show smart errors only very slow speeds <512kbs
apart form that these disks are missing some functions to run in raid reliable

edit : oh just spotted its about a Seagate drive, you could try to set your sata port to sata 2

---

### Post by linkageless on 2012-06-10
Just a thought, how's the power supply? Is it possible that the PSU isn't sufficiently rated to supply all the drives. I've seen similar symptoms in the past with underrated or ailing PSUs.

I would check the rated peak power consumption of the drives, add them all together with what the rest of the system should use and see if it comes close to what the PSU is rated for. You may find that it's perfectly adequate to supply a couple of drives plus CPU etc, but extended periods of intense activity on all disks (like during backups) might cause a brown-out situation.

You may be able to prove this by doing large simultaneous dd reads on all, until you have a failure, then by removing (or shutting down) one or two drives and trying again for a similar time.

You may be able to alleviate the situation by putting disks in separate arrays (2x RAID-1 I suppose) and having multiple mount points. Not always convenient, but depending on the workload may mean that you have less disks busy at once.

Also, as you're no doubt aware there's all kinds of software tweaks that can be done to save power on the disks and elsewhere in various ways, these may be worth considering.

Hope that helps!

---

### Post by Vegan on 2012-06-10
Could also be a PSU has decided to go flaky. I recently bought a new Corair TX850V2 for the gaming rig.

A good PSU can often be more stable. A cheap PSU may not last long.

[http://www.hardcore-games.tk/wp/psu.php](http://www.hardcore-games.tk/wp/psu.php)

---

### Post by jmore9 on 2012-06-10
I have 4 drives in my system none are server or raid but i had some read write errors and figured out it was the power supply.  Went and bought a brand new 500 watter and it was doa.  Took it back and exchanged it for another one and that solved my problem,  I think the heat inside the case was a major factor in the failure.  Installed 2 case fans at the same time.

---

### Post by Bushflyr on 2012-06-10
> **Gompa said:**
> edit : oh just spotted its about a Seagate drive, you could try to set your sata port to sata 2

How do I do that? Is it a BIOS setting? I currently have the BIOS set to IDE, the only other option I have is AHCI and that, from what read, shouldn't make a difference. Could it? 

> **linkageless said:**
> Just a thought, how's the power supply? Is it possible that the PSU isn't sufficiently rated to supply all the drives. I've seen similar symptoms in the past with underrated or ailing PSUs.

PSU is a brand new Cooler Master Elite 460W. The calculators show the system only drawing 177W and recommending a 227W PSU, so I've got plenty of overhead there. 


> **jmore9 said:**
> I have 4 drives in my system none are server or raid but i had some read write errors and figured out it was the power supply.

How did you test that? Is there a program or something I can use to verify power quality?

> I think the heat inside the case was a major factor in the failure.  Installed 2 case fans at the same time.

Shouldn't be an issue for me, the case is a [Lian Li PCQ08A]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811112266") with a 140mm fan in front blowing directly through the drive rack and a 120mm on top venting the case. Plus the PSU has its own separate airflow channel in through the side and out the back. I've got them all running on high to eliminate any possibility od heat buildup. Even on low the drives stay below ~45 degrees all the time.

Thanks for the replies and ideas. I really appreciate them.

---

### Post by linkageless on 2012-06-10
> PSU is a brand new Cooler Master Elite 460W. The calculators show the system only drawing 177W and recommending a 227W PSU, so I've got plenty of overhead there.

Glad to hear you have that aspect covered. It would be good also to rule out an ailing PSU somehow.

If you are able to reliably repeat the problems with all drives but not with less, even the most suspect ones, that will give you something to go on. Another possible common factor is the controller, but these tend to be a little more reliable assuming your internal temperatures are reasonable.

---

### Post by Bushflyr on 2012-06-10
There is no controller per se, they're all plugged directly into the motherboard. 

The drive failures seem to be random between sdb, sdc, and sdd. I don't actually recall if I've had sde drop out. I'm taking better notes now. 

Before this most recent failure it was running solidly for over a month. I thought I had the problem licked.

**AFAICT the only common thread has to do with Time Machine on my iMac.** I'm not 100% certain about the previous problems, but the last two failures happened while TM was in the middle of a back up. I've dropped my entire 600GB music folder on the RAID multiple times and it copies it without a hiccup. TM, for some reason seems to give crashes.

---

### Post by linkageless on 2012-06-11
> There is no controller per se, they're all plugged directly into the motherboard.

Absolutely, I'm referring to the controller as 'function' as opposed to separate hardware. It's still possible for it to have issues that don't affect the rest of the motherboard.

> AFAICT the only common thread has to do with Time Machine on my iMac.

Interesting.... is TM multi-threaded and how does it get at your data? (Sorry if I missed that in the thread.)

---

### Post by Bushflyr on 2012-06-11
> **linkageless said:**
> Absolutely, I'm referring to the controller as 'function' as opposed to separate hardware. It's still possible for it to have issues that don't affect the rest of the motherboard.

OK. I see. I wonder if maybe it could be, not necessarily a 'bad' mobo, but that it can't handle a full load on 4 drives concurrently.

> Interesting.... is TM multi-threaded and how does it get at your data? (Sorry if I missed that in the thread.)

Sorry, I shouldn't have used the term 'thread' in this sense. I meant the only common factor, but looks like it's a moot point as I managed to kill the RAID again last night.

I rebuilt it as RAID6 just for giggles: 

```
[~]: cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdb1[0] sdc1[1] sdd1[2] sde1[3]
      3907021824 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

Then I dropped my 500GB music folder into 3 separate directories on the RAID to test it. That got  it. Killed sdc and sde. Note that it's two different drives than failed last time.


```
Jun 10 23:24:55 mars afpd[1562]: transmit: Request to dbd daemon (db_dir /mnt/marsraid/users/scot) timed out.
Jun 10 23:25:01 mars CRON[1758]: (root) CMD (/usr/local/sbin/continuous.sh)
Jun 10 23:25:27 mars kernel: [ 4622.972757] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 frozen
Jun 10 23:25:27 mars kernel: [ 4622.972801] ata2.01: failed command: FLUSH CACHE EXT
Jun 10 23:25:27 mars kernel: [ 4622.972833] ata2.01: cmd ea/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Jun 10 23:25:27 mars kernel: [ 4622.972834]          res 40/00:01:00:4f:c2/00:00:00:00:00/10 Emask 0x4 (timeout)
Jun 10 23:25:27 mars kernel: [ 4622.972902] ata2.01: status: { DRDY }
Jun 10 23:25:27 mars kernel: [ 4622.972931] ata2.00: hard resetting link
Jun 10 23:25:28 mars kernel: [ 4624.000504] ata2.00: failed to resume link (SControl 0)
Jun 10 23:25:28 mars kernel: [ 4624.000512] ata2.01: hard resetting link
Jun 10 23:25:34 mars kernel: [ 4629.515292] ata2.00: link is slow to respond, please be patient (ready=-19)
Jun 10 23:25:37 mars kernel: [ 4632.986527] ata2.00: SRST failed (errno=-16)
Jun 10 23:25:37 mars kernel: [ 4632.986561] ata2.00: hard resetting link
Jun 10 23:25:38 mars kernel: [ 4634.014293] ata2.00: failed to resume link (SControl 0)
Jun 10 23:25:38 mars kernel: [ 4634.014300] ata2.01: hard resetting link
Jun 10 23:25:44 mars kernel: [ 4639.529082] ata2.00: link is slow to respond, please be patient (ready=-19)
Jun 10 23:25:47 mars kernel: [ 4643.000319] ata2.00: SRST failed (errno=-16)
Jun 10 23:25:47 mars kernel: [ 4643.000357] ata2.00: hard resetting link
Jun 10 23:25:48 mars kernel: [ 4644.028085] ata2.00: failed to resume link (SControl 0)
Jun 10 23:25:48 mars kernel: [ 4644.028093] ata2.01: hard resetting link
Jun 10 23:25:54 mars kernel: [ 4649.542890] ata2.00: link is slow to respond, please be patient (ready=-19)
Jun 10 23:26:23 mars kernel: [ 4678.040583] ata2.00: SRST failed (errno=-16)
Jun 10 23:26:23 mars kernel: [ 4678.040619] ata2.00: limiting SATA link speed to 1.5 Gbps
Jun 10 23:26:23 mars kernel: [ 4678.040625] ata2.01: limiting SATA link speed to 1.5 Gbps
Jun 10 23:26:23 mars kernel: [ 4678.040633] ata2.00: hard resetting link
Jun 10 23:26:24 mars kernel: [ 4679.068362] ata2.00: failed to resume link (SControl 0)
Jun 10 23:26:24 mars kernel: [ 4679.068369] ata2.01: hard resetting link
Jun 10 23:26:28 mars kernel: [ 4683.071471] ata2.00: SRST failed (errno=-16)
Jun 10 23:26:28 mars kernel: [ 4683.071519] ata2.00: reset failed, giving up
Jun 10 23:26:28 mars kernel: [ 4683.071543] ata2.01: disabled
Jun 10 23:26:28 mars kernel: [ 4683.071547] ata2.01: device reported invalid CHS sector 0
Jun 10 23:26:28 mars kernel: [ 4683.071557] ata2: EH complete
Jun 10 23:26:28 mars kernel: [ 4683.071589] sd 1:0:1:0: [sdc] Unhandled error code
Jun 10 23:26:28 mars kernel: [ 4683.071591] sd 1:0:1:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 10 23:26:28 mars kernel: [ 4683.071595] sd 1:0:1:0: [sdc] CDB: Read(10): 28 00 73 80 99 40 00 00 08 00
Jun 10 23:26:28 mars kernel: [ 4683.071606] end_request: I/O error, dev sdc, sector 1937807680
Jun 10 23:26:28 mars kernel: [ 4683.071663] sd 1:0:1:0: [sdc] Unhandled error code
Jun 10 23:26:28 mars kernel: [ 4683.071666] sd 1:0:1:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 10 23:26:28 mars kernel: [ 4683.071669] sd 1:0:1:0: [sdc] CDB: Write(10): 2a 00 0d 86 e0 08 00 04 00 00
Jun 10 23:26:28 mars kernel: [ 4683.071677] end_request: I/O error, dev sdc, sector 226942984
Jun 10 23:26:28 mars kernel: [ 4683.071757] md/raid:md0: Disk failure on sdc1, disabling device.
Jun 10 23:26:28 mars kernel: [ 4683.071759] md/raid:md0: Operation continuing on 3 devices.
Jun 10 23:26:28 mars kernel: [ 4683.071786] sd 1:0:1:0: [sdc] Unhandled error code
Jun 10 23:26:28 mars kernel: [ 4683.071787] sd 1:0:1:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 10 23:26:28 mars kernel: [ 4683.071789] sd 1:0:1:0: [sdc] CDB: Write(10): 2a 00 0d 86 e0 00 00 00 08 00
Jun 10 23:26:28 mars kernel: [ 4683.071794] end_request: I/O error, dev sdc, sector 226942976
Jun 10 23:26:28 mars kernel: [ 4683.071813] sd 1:0:1:0: [sdc] Unhandled error code
Jun 10 23:26:28 mars kernel: [ 4683.071814] sd 1:0:1:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 10 23:26:28 mars kernel: [ 4683.071816] sd 1:0:1:0: [sdc] CDB: Write(10): 2a 00 0d 86 e4 08 00 03 f8 00
Jun 10 23:26:28 mars kernel: [ 4683.071821] end_request: I/O error, dev sdc, sector 226944008
Jun 10 23:26:28 mars kernel: [ 4683.465906] RAID conf printout:
Jun 10 23:26:28 mars kernel: [ 4683.465910]  --- level:6 rd:4 wd:3
Jun 10 23:26:28 mars kernel: [ 4683.465913]  disk 0, o:1, dev:sdb1
Jun 10 23:26:28 mars kernel: [ 4683.465914]  disk 1, o:0, dev:sdc1
Jun 10 23:26:28 mars kernel: [ 4683.465916]  disk 2, o:1, dev:sdd1
Jun 10 23:26:28 mars kernel: [ 4683.465918]  disk 3, o:1, dev:sde1
Jun 10 23:26:28 mars kernel: [ 4683.465973] RAID conf printout:
Jun 10 23:26:28 mars kernel: [ 4683.465977]  --- level:6 rd:4 wd:3
Jun 10 23:26:28 mars kernel: [ 4683.465987]  disk 0, o:1, dev:sdb1
Jun 10 23:26:28 mars kernel: [ 4683.465990]  disk 2, o:1, dev:sdd1
Jun 10 23:26:28 mars kernel: [ 4683.465992]  disk 3, o:1, dev:sde1
Jun 10 23:26:31 mars mdadm[1209]: Fail event detected on md device /dev/md/0, component device /dev/sdc1

Jun 11 00:06:01 mars CRON[1834]: (root) CMD (/usr/local/sbin/hourly.sh)
Jun 11 00:06:02 mars logger: HDTEMP for /dev/sda is 43
Jun 11 00:06:02 mars logger: HDTEMP for /dev/sdb is 41
Jun 11 00:06:02 mars logger: HDTEMP for /dev/sdc is /dev/sdc: : S.M.A.R.T. not available
Jun 11 00:06:02 mars logger: HDTEMP for /dev/sdd is 41
Jun 11 00:06:02 mars logger: HDTEMP for /dev/sde is 41
Jun 11 00:17:01 mars CRON[1897]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 11 00:41:40 mars afpd[1562]: transmit: Request to dbd daemon (db_dir /mnt/marsraid/media) timed out.
Jun 11 00:42:08 mars afpd[1562]: transmit: Request to dbd daemon (db_dir /mnt/marsraid/media) timed out.
Jun 11 00:42:14 mars kernel: [ 9228.036320] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Jun 11 00:42:14 mars kernel: [ 9228.036356] ata4.00: failed command: FLUSH CACHE EXT
Jun 11 00:42:14 mars kernel: [ 9228.036382] ata4.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jun 11 00:42:14 mars kernel: [ 9228.036383]          res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 11 00:42:14 mars kernel: [ 9228.036441] ata4.00: status: { DRDY }
Jun 11 00:42:14 mars kernel: [ 9228.036467] ata4: hard resetting link
Jun 11 00:42:19 mars kernel: [ 9233.551087] ata4: link is slow to respond, please be patient (ready=0)
Jun 11 00:42:24 mars kernel: [ 9238.086073] ata4: SRST failed (errno=-16)
Jun 11 00:42:24 mars kernel: [ 9238.086107] ata4: hard resetting link
Jun 11 00:42:29 mars kernel: [ 9243.600855] ata4: link is slow to respond, please be patient (ready=0)
Jun 11 00:42:34 mars kernel: [ 9248.135853] ata4: SRST failed (errno=-16)
Jun 11 00:42:34 mars kernel: [ 9248.135892] ata4: hard resetting link
Jun 11 00:42:36 mars afpd[1562]: transmit: Request to dbd daemon (db_dir /mnt/marsraid/media) timed out.
Jun 11 00:42:39 mars kernel: [ 9253.650634] ata4: link is slow to respond, please be patient (ready=0)
Jun 11 00:43:04 mars afpd[1562]: transmit: Request to dbd daemon (db_dir /mnt/marsraid/media) timed out.
Jun 11 00:43:09 mars kernel: [ 9283.156126] ata4: SRST failed (errno=-16)
Jun 11 00:43:09 mars kernel: [ 9283.156163] ata4: limiting SATA link speed to 1.5 Gbps
Jun 11 00:43:09 mars kernel: [ 9283.156171] ata4: hard resetting link
Jun 11 00:43:14 mars kernel: [ 9288.167016] ata4: SRST failed (errno=-16)
Jun 11 00:43:14 mars kernel: [ 9288.178545] ata4: reset failed, giving up
Jun 11 00:43:14 mars kernel: [ 9288.178569] ata4.00: disabled
Jun 11 00:43:14 mars kernel: [ 9288.178574] ata4.00: device reported invalid CHS sector 0
Jun 11 00:43:14 mars kernel: [ 9288.178581] ata4: EH complete
Jun 11 00:43:14 mars kernel: [ 9288.178640] sd 3:0:0:0: [sde] Unhandled error code
Jun 11 00:43:14 mars kernel: [ 9288.178642] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 11 00:43:14 mars kernel: [ 9288.178646] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 17 47 a7 f8 00 03 f8 00
Jun 11 00:43:14 mars kernel: [ 9288.178654] end_request: I/O error, dev sde, sector 390572024
Jun 11 00:43:14 mars kernel: [ 9288.181326] sd 3:0:0:0: [sde] Unhandled error code
Jun 11 00:43:14 mars kernel: [ 9288.181330] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 11 00:43:14 mars kernel: [ 9288.181335] sd 3:0:0:0: [sde] CDB: Write(10): 2a 00 17 47 a3 f8 00 04 00 00
Jun 11 00:43:14 mars kernel: [ 9288.181345] end_request: I/O error, dev sde, sector 390571000
Jun 11 00:43:14 mars kernel: [ 9288.181424] md/raid:md0: Disk failure on sde1, disabling device.
Jun 11 00:43:14 mars kernel: [ 9288.181426] md/raid:md0: Operation continuing on 2 devices.
Jun 11 00:43:14 mars kernel: [ 9288.181453] sd 3:0:0:0: [sde] Unhandled error code
Jun 11 00:43:14 mars kernel: [ 9288.181454] sd 3:0:0:0: [sde]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jun 11 00:43:14 mars kernel: [ 9288.181457] sd 3:0:0:0: [sde] CDB: Write(10): 2a 00 17 47 a7 f8 00 03 f8 00
Jun 11 00:43:14 mars kernel: [ 9288.181461] end_request: I/O error, dev sde, sector 390572024
Jun 11 00:43:14 mars kernel: [ 9288.569033] RAID conf printout:
Jun 11 00:43:14 mars kernel: [ 9288.569037]  --- level:6 rd:4 wd:2
Jun 11 00:43:14 mars kernel: [ 9288.569040]  disk 0, o:1, dev:sdb1
Jun 11 00:43:14 mars kernel: [ 9288.569042]  disk 2, o:1, dev:sdd1
Jun 11 00:43:14 mars kernel: [ 9288.569045]  disk 3, o:0, dev:sde1
Jun 11 00:43:14 mars kernel: [ 9288.574931] RAID conf printout:
Jun 11 00:43:14 mars kernel: [ 9288.574935]  --- level:6 rd:4 wd:2
Jun 11 00:43:14 mars kernel: [ 9288.574938]  disk 0, o:1, dev:sdb1
Jun 11 00:43:14 mars kernel: [ 9288.574940]  disk 2, o:1, dev:sdd1
Jun 11 00:43:16 mars mdadm[1209]: Fail event detected on md device /dev/md/0, component device /dev/sde1

```

---

### Post by rubylaser on 2012-06-11
This is looking like a hardware problem (I'd guess the motherboard SATA controller).  Do you have any different hardware you could try this out on?  Also, you will want to run your drives in AHCI mode rather than IDE, because that will allow the Native Command Queuing on your drives to work.  But, that is not what is causing the problem here.

---

### Post by Bushflyr on 2012-06-11
Thanks, I'll fire off a nastygram to Jetway and see if they can help me test it somehow.

---

### Post by Bushflyr on 2012-06-11
Possible problem found!!! (hopefully) I took the whole machine apart and started futzing around. I had the SATA cables beautifully routed and bundled but when I started wiggling them they looked sort of loose in their sockets on the MOBO. Not because they were loose per se, but because they don't fit that well. I cut all the ties and ran them loose to try and alleviate any stress on the sockets. Rebooted and /dev/md127 came up clean. :guitar:

Stopped md127 and did a quick:

```
sudo mdadm --create --verbose --assume-clean /dev/md0 --level=raid6 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

and it seemed to work. 

Back to stress test again. And order some good locking SATA cables.

I'm hopeful.

---

### Post by rubylaser on 2012-06-11
Geez, cable management is a great thing... except when it makes your connections inconsistent :)  I really hope this solves your problem.

---

### Post by Bushflyr on 2012-06-12
Well. Crap. :( I can drop a single instance of my music directory on it and it seems to do OK, but when I drop it into 2 separate directories at the same time the RAID starts failing disks. Back to the drawing board. New cables should be here in a couple days in any case.

---

### Post by rubylaser on 2012-06-12
Can you setup a partition and filesystem on each disk and mount them individually and copy to them (or better, try out timemachine on each) and see if you see the disks become unavailable?

---

### Post by linkageless on 2012-06-12
Also, try a RAID-1 on just a couple of those disks and the other two removed. I know it's no use capacity-wise for you, but at least you'll have an idea what's reliable and what isn't.

If two disks (plus system drive) work ok, then try adding another and test again.

---

### Post by Bushflyr on 2012-06-12
Both excellent suggestions. Thanks. Considering how many times I've rebuilt this thing already doing individual disks will be simple. After that 2x raid 1 then add in more disks and see what happens. And migrate to AHCI while I'm at it.

The only saving grace through this whole thing is that the OS is on a separate drive that's been stable. I would have shot this box a month ago if I had to redo the OS every time.

---

