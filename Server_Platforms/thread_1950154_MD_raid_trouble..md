---
title: "MD raid trouble."
date: 2012-03-31
forum: Server Platforms
---

### Post by rcastberg on 2012-03-31
Hi,

I am having a problem with my RAID array. After going on vacation for a couple of weeks I have come back unable to access any of the data. I would appreciate it if anybody can help as i don't want to loose my data by rebuiling the array incorrectly.
I am not sure why the problem happened and help in understanding why would also be appreciated.

I used to have a ZFS filesystem on 3 of the 5 drives.
After setting up the mdraid i formated the filesystem with btrfs. (I realize this is my next problem if i can get as far as loading up the array). But my hope is to be able to extracted media so i don't have to rerip everything.

The drives should be set up in a RAID-6 setup.

Hope i included the most usefull data

Thanks for reading this far.

René

```
$ uname -a
Linux Asgard 3.0.0-16-server #29-Ubuntu SMP Tue Feb 14 13:08:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```


```
$ sudo mdadm --examine /dev/sd*
mdadm: No md superblock detected on /dev/sda.
mdadm: No md superblock detected on /dev/sda1.
mdadm: No md superblock detected on /dev/sda2.
mdadm: No md superblock detected on /dev/sda5.
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0db0c336:f56bd888:2f9e92e4:c1d64c09
           Name : Asgard:0  (local to host Asgard)
  Creation Time : Sat Jan 28 14:29:36 2012
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721077760 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8e861931:6f7448ec:6f2c6cd2:74cb06a2

    Update Time : Tue Mar 27 18:25:33 2012
       Checksum : a4305a9b - correct
         Events : 315451

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : ..A.A ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0db0c336:f56bd888:2f9e92e4:c1d64c09
           Name : Asgard:0  (local to host Asgard)
  Creation Time : Sat Jan 28 14:29:36 2012
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721077760 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ef9d6881:b31e81b4:9403e07a:4280392d

    Update Time : Tue Mar 27 18:25:33 2012
       Checksum : f05ad7f8 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : ..A.A ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0db0c336:f56bd888:2f9e92e4:c1d64c09
           Name : Asgard:0  (local to host Asgard)
  Creation Time : Sat Jan 28 14:29:36 2012
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721077760 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 387de195:c966497f:f7fad598:cfc7fb10

    Update Time : Tue Mar 27 18:25:33 2012
       Checksum : d1543e47 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : ..A.A ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0db0c336:f56bd888:2f9e92e4:c1d64c09
           Name : Asgard:0  (local to host Asgard)
  Creation Time : Sat Jan 28 14:29:36 2012
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721077760 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8e1a4400:e00d30d2:faf68bb0:99e13cb1

    Update Time : Tue Mar 27 18:25:33 2012
       Checksum : 46949882 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : ..A.A ('A' == active, '.' == missing)
/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0db0c336:f56bd888:2f9e92e4:c1d64c09
           Name : Asgard:0  (local to host Asgard)
  Creation Time : Sat Jan 28 14:29:36 2012
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 11721077760 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 418fe563:d3c6d16b:54762ab7:8b6aced2

    Update Time : Tue Mar 27 18:25:33 2012
       Checksum : 6c0b9ead - correct
         Events : 315451

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : ..A.A ('A' == active, '.' == missing)

```


```

Output of parted:
# parted -l /dev/sd[bcdef]
Error: The primary GPT table is corrupt, but the backup appears OK, so that will
be used.
OK/Cancel? ok                                                             
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB               zfs
 9      2000GB  2000GB  8389kB


Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
OK/Cancel? ok                                                             
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB               zfs
 9      2000GB  2000GB  8389kB


Error: /dev/sdd: unrecognised disk label                                  

Error: /dev/sde: unrecognised disk label                                  

Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
OK/Cancel? ok                                                             
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB               zfs
 9      2000GB  2000GB  8389kB

```




Build:
```
#created a raid 5 array with 3 disks. Don't have the precise commands anymore.
sudo mdadm --add /dev/md127 /dev/sdc /dev/sdd
sudo mdadm --grow --level=6 --raid-devices=5 /dev/md127 --backup-file=/home/renec/raid.backup

```

---

### Post by rubylaser on 2012-03-31
Boy, this is a mess, and a fairly convoluted setup.  If you get this remounted, you'll want to back up your data, and write zeroes over all of these disks to remove all traces of ZFS and mdadm, and then start over.  Also, I wouldn't use btrfs at this point because it's still be developed.  

What's in your /etc/mdadm/mdadm.conf file?
```
cat /etc/mdadm/mdadm.conf
```

What do these show?

```
cat /proc/mdstat
mdadm --detail --scan
```

---

### Post by rcastberg on 2012-04-01
Yeah, i plan on doing something like that. I wasn't aware zfs would still be visible after the raid initialization.

I am aware of the status of btrfs but wanted something with checksumming so was willing to take that risk.

The mdadm.conf is still in its original state. (Mostly commented out) Forgot to add the relavent info.

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdf[3](S) sdb[4](S) sdd[5](S)
      5860540680 blocks super 1.2

```

```
sudo mdadm --detail --scan
mdadm: md device /dev/md/0 does not appear to be active.

```

---

### Post by rubylaser on 2012-04-01
It looks like you just need to try to force assemble the array and then put a proper mdadm.conf file back in place.

```
mdadm --assemble --force /dev/md0 /dev/sd[bcdef]
```

If that assemblies properly, then you'll want to recreate your mdadm.conf file.
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST <system>" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

I'm assuming that you didn't update your mdadm.conf after changing to a RAID6 and that was the cause of this situation.  Let me know how this assemble goes.

---

### Post by rcastberg on 2012-04-01
Cheers, tried that, no luck.

```
$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
$ lsof /dev/sde 
$ lsof /dev/sdd
$sudo mdadm --assemble --force /dev/md0 /dev/sd[bcdef]
mdadm: failed to add /dev/sdd to /dev/md0: Device or resource busy
mdadm: failed to add /dev/sde to /dev/md0: Device or resource busy
mdadm: /dev/md0 assembled from 2 drives and 1 spare - not enough to start the array.
$mdadm --stop  /dev/md0
mdadm: stopped /dev/md0

```

Gives me:
```
$ sudo mdadm --detail /dev/md0 
mdadm: md device /dev/md0 does not appear to be active.
$ sudo cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]                                                                        
md0 : inactive sdf[3](S) sdc[5](S) sdb[4](S)
      5860540680 blocks super 1.2
       
unused devices: <none>

```


Not sure why i am getting the device or resource busy... Especially as these devies seem to be the clean ones from the mdadm .--examine line. Do you have any idea why one of the drives comes up as spare, as technically i only need 3 of the 5 discs to get at the data.

Thanks for your help so far.

Rene

---

### Post by rubylaser on 2012-04-01
Those drives aren't the clean one's, they're just the ones that don't have any event counter value.  That's not a good sign as their event counters should be the same as the other disks, or very close.

It appears that the dmraid driver is controlling these two drives.  It appears that mdadm is confused and assembling incorrectly because of the lack of a proper mdadm.conf file.  Can you post what you have here even if it's commented out?
```
cat /etc/mdadm/mdadm.conf
```

Have you verified these disks are healthy via smartmontools?
```
smartctl -d ata -a /dev/sdd
smartctl -d ata -a /dev/sde
```

---

### Post by rcastberg on 2012-04-02
```
$ cat /etc/mdadm/mdadm.conf
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
MAILADDR rene-sysadm@castberg.org

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=7c88ffa3:9ae1da97:856c4418:84634b4a

```

For the smartctl selftests i get: 
SMART overall-health self-assessment test result: PASSED
for both drives.

---

### Post by rubylaser on 2012-04-02
Here's what I would do next.  The first step is to get a proper mdadm.conf file in place so mdadm knows how to correctly assemble the array on bootup.  Yours should be like this based off of what you've posted so far.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST <system>" >> /etc/mdadm/mdadm.conf
echo "MAILADDR rene-sysadm@castberg.org" >> /etc/mdadm/mdadm.conf
echo "ARRAY /dev/md0 metadata=1.2 name=Asgard:0 UUID=0db0c336:f56bd888:2f9e92e4:c1d64c09" >> /etc/mdadm/mdadm.conf
```

Then I'd update initramfs.
```
update-initramfs -u
```

Finally, reboot.
```
reboot
```

---

### Post by rcastberg on 2012-04-02
Right, adjust the mdadm.conf like you recommended and rebooted. I ended up in initramfs boot console and tried a couple of the recommendations that you came with earlier, no luck. I was still getting the error message about device or resource busy so rebooted using the nodmraid kernel command and it still results in the same error message. 

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
MAILADDR rene-sysadm@castberg.org

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=7c88ffa3:9ae1da97:856c4418:84634b4a
ARRAY /dev/md0 metadata=1.2 name=Asgard:0 UUID=0db0c336:f56bd888:2f9e92e4:c1d64c09

```

```
[2012-04-02 21:44:54]  Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-server root=UUID=65041921-457e-4790-acde-79864823fe5f ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7 nodmraid

```

---

### Post by rubylaser on 2012-04-02
Have you tried to assemble this from the LiveCD to see if you can get it assembled and mounted?  Just download and burn the livecd, and boot from the cd.  Once, running just apt-get install mdadm, and then try to assemble the array.

```
mdadm --assemble /dev/md0 /dev/sd[bcdef]
```

If you can get this assembled, then you should be able to mount the array, and then backup your data.

---

### Post by rcastberg on 2012-04-03
Same error messages, first it complains about decice or resource busy, for two fo the disks, and then i get a message about 2 acitve and one spare device.

I assume the my options are starting to become limited?

---

### Post by rubylaser on 2012-04-03
Did you make sure that mdadm didn't have a partially assembled array by stopping it first?  About the only option you'll have is to try to re-run mdadm create with the assume clean with the same values as you had before.  The beginning portion of [this]("http://unix.stackexchange.com/questions/34720/recovery-of-data-on-raid5lvm-reiserfs-partition-after-raid5-problems") will give you an idea. 

First, have you tried swapping the SATA cables on those drives or putting them on different SATA heads on your motherboard to try to rule out hardware.  Also, can you please paste the whole output of smartctl on both of those drives.  Passing a smart test without running at least short test on them first doesn't mean they're working as they should. 

Here's how to run a long SMART test.
```
smartctl -s on -t long /dev/sdd
smartctl -s on -t long /dev/sde
```

 This might take a few hours to finish, but you can check the drive's test status like this. If the status of a disk reports not completed because of read errors, those disks need to be replaced.
```
smartctl -l selftest /dev/sdd
smartctl -l selftest /dev/sde
```

Finally, I'd like to see the whole SMART output for each of the drives.
```
smartctl -d ata -a /dev/sdd
smartctl -d ata -a /dev/sde
```

I'd be very interested to see some of the values like reallocated sectors and UDMA error count.

---

### Post by rcastberg on 2012-04-04
I haven't swapped the cables yet. Will look into that this evening.
I was looking at your website and came across the article of multiple disk failure and the command: 
```
mdadm --create --assume-clean /dev/md0 /dev/sd[abcdefg]1
```
Is there any point in trying this ? Or will it just overwrite any data the might have been there? And i assume that i will have to get the order right in the command above?

Smartctl test:
```
smartctl -d ata -a /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-16-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD1W8E8
LU WWN Device Id: 5 000c50 02fbeebc9
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Wed Apr  4 17:18:16 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  623) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       229912144
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       26
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       262889320
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6332
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       27
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       6
189 High_Fly_Writes         0x003a   094   094   000    Old_age   Always       -       6
190 Airflow_Temperature_Cel 0x0022   067   060   045    Old_age   Always       -       33 (Min/Max 31/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       18
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       26
194 Temperature_Celsius     0x0022   033   040   000    Old_age   Always       -       33 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   024   009   000    Old_age   Always       -       229912144
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       278489974446231
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       310312786
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2466526807

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      6331         -

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

root@Asgard:/home/renec/R-Studio# smartctl -d ata -a /dev/sde
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-16-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    6YD1JP7R
LU WWN Device Id: 5 000c50 046199c58
Firmware Version: CC3C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Wed Apr  4 17:18:18 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  602) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   120   099   006    Pre-fail  Always       -       243225248
  3 Spin_Up_Time            0x0003   093   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       9
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       61510937
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       946
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       9
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   097   000    Old_age   Always       -       3
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   062   045    Old_age   Always       -       34 (Min/Max 32/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       9
194 Temperature_Celsius     0x0022   034   040   000    Old_age   Always       -       34 (0 22 0 0)
195 Hardware_ECC_Recovered  0x001a   024   013   000    Old_age   Always       -       243225248
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       198131136332722
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3081786388
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3311031373

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       944         -

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

### Post by rubylaser on 2012-04-04
Both of those disks are very healthly looking.  If you look at that link that I sent the post before, it basically details recreating the mdadm array with the assume clean option.  For it to work, you have to use the same creation options that you used to create the array and your disks need to be in the same order.  It won't overwrite your data if you use assume clean, because it won't cause a resync.  You'll only be recreating the superblock info.

---

### Post by rcastberg on 2012-04-04
Right this looks like it is getting some where. 
I am able to start mdadm with 4 of the 5 disks, when the 5th disk is added there are problems, i am running smartctl on it right now.

It seems that this disk had problems ealier: 
```
[1468403.073910] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
```
Not sure what the error message means, but it will be interesting to see what happens with smartctl tool.

btrfs won't mount yet, but i am able to get hold of some files using a recovery tool.

rubylaser thanks a lot for all your advice. It is very much appreciated.

I will post an update when i am done/give up.

---

### Post by rubylaser on 2012-04-04
So, your array is assembled and working now, in a degraded state?  That's great!  Did you recreate the array with the assume clean option?
What's the output of ```
cat /proc/mdstat
```

This [thread]("http://ubuntuforums.org/showthread.php?t=1470970") seems to cover the same error.  Do you have any USB devices that you could unhook to see if it's an IRQ problem?  Also, did you try a different SATA cable?

---

### Post by rcastberg on 2012-04-05
My goal is now to copy as much off the disk to an external disk. When the data is safe i will try to see if i can get some life into sdd. (I have many usb disks which i could unplug)

And then i will try again... Starting with zeroing out the first part of each drive to get rid of zfs and mdadm.

Self test on disk /dev/sdd completed without errors.

For others who might run into similar problems with btrfs, i was unable to use the btrfsck check succesfully and am now using btrfs-restore. This utility is able to use the file structure (unlike restore programs which only fine files without names) and copy the files to another drive.

```
 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdc[4] sda[2] sde[1] sdf[0]
      5860538880 blocks super 1.2 level 6, 512k chunk, algorithm 2 [5/4] [UUU_U]
      
md127 : inactive sdd[3](S)
      1953513560 blocks super 1.2
       
unused devices: <none>

```


I noticed that the labels of the disks are moving around sda and sdb are swapping names every now and then but i assume mdadm is smart enough to firgure this out when the pc boots.

---

### Post by rubylaser on 2012-04-05
> **rcastberg said:**
> 
I noticed that the labels of the disks are moving around sda and sdb are swapping names every now and then but i assume mdadm is smart enough to firgure this out when the pc boots.

Yes it is, mdadm assembles the array based on the UUIDs in the superblock on each disk.  So, the disk order really doesn't matter.  Glad to hear you where able to recover your data.

---

### Post by darkod on 2012-04-05
But wouldn't a disk name moving around point to a faulty cable or connection? If you are not touching anything, they would only move if the order of discovery of disks is different, in other words if one is disconnected.

Could this be in the wider picture of your problems?

Yes, mdadm can work with the UUID but you can't ignore if one of the disks has good or bad connection.

---

### Post by rubylaser on 2012-04-05
It could, but the SMART data would show a bad SATA cable by looking at this line
```
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
```

Since the count is at zero, it's very unlikely that it's that.

---

### Post by darkod on 2012-04-05
Sorry to be a pain, but where did you get that from? Because the OP has many disks, are we talking about the same?

I see only SMART info about sdd and sde posted, while the OP said that sda and sdb are switching places in the mdadm array.

So we would need the smart info of sda and/or sdb, right?

It's definitely weird. If a disk gets disconnected (even temporarily), shouldn't all of them change device names? Why would only sda and sdb switch places?

It seems like they are both detected OK, but not in the same order on every boot. Or something like that.

---

### Post by rcastberg on 2012-04-05
To be honest, sda and sdb are the only ones that i am sure are switching places and that is because sda is a different disk. (a smaller 200Gb and a larger 2000Gb disk)

I have tried to work my way back from some logs when the array was good, and have only been able to estabilish a rough idea of which disk was which. I then had to experiment with 3 disks at a time to dtermine the order that they were in the array. I was helped a bit by the fact that two of the disks were attached to an external controller. Otherwise in the dmesg.log and kern.log the disks are only reffered to by model and not by thier id, so i was only able to tell the difference between the newest 2 and the oldest 3 disks.

I'll make sure to run a smartclt long test on all the disks when i have recovered all the data. (Only at 25% at the moment)

---

### Post by rubylaser on 2012-04-05
> **darkod said:**
> Sorry to be a pain, but where did you get that from? Because the OP has many disks, are we talking about the same?

I see only SMART info about sdd and sde posted, while the OP said that sda and sdb are switching places in the mdadm array.

So we would need the smart info of sda and/or sdb, right?

It's definitely weird. If a disk gets disconnected (even temporarily), shouldn't all of them change device names? Why would only sda and sdb switch places?

It seems like they are both detected OK, but not in the same order on every boot. Or something like that.

You are right, I was getting the disks confused.  I'd need to see the SMART reports to say that with confidence.  One reason that the devices can switch places is that they get presented in a different order from the motherboard, but you'd normally only see this behavior with external disks connected via USB.

---

### Post by rcastberg on 2012-04-07
Right, managed to get all the important data back with btrfs-restore. A couple of mp3 files were corrupt but i can rerip them.
I did a smartctl test on all the drives and they all seem good. (See details below)

I was able to assemble the complete array, but the filesystem was still unaccessable so i will wipe everything anyway and reinstiallize the array.

```
$ sudo smartctl -d ata -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-16-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD24GMK
LU WWN Device Id: 5 000c50 02faa3c4f
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Apr  8 00:34:04 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  612) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       35634224
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       24
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       309210756
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7309
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       24
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       5
189 High_Fly_Writes         0x003a   096   096   000    Old_age   Always       -       4
190 Airflow_Temperature_Cel 0x0022   066   062   045    Old_age   Always       -       34 (Min/Max 31/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       18
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       24
194 Temperature_Celsius     0x0022   034   040   000    Old_age   Always       -       34 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   015   008   000    Old_age   Always       -       35634224
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       93205085297779
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1364094888
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       855062218

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      7305         -

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

$ sudo smartctl -d ata -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-16-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD1WTP2
LU WWN Device Id: 5 000c50 02fc15f6c
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Apr  8 00:34:08 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  623) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       66600080
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       25
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       315143833
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7326
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       25
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       1
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       146
190 Airflow_Temperature_Cel 0x0022   064   055   045    Old_age   Always       -       36 (Min/Max 33/42)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       17
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       25
194 Temperature_Celsius     0x0022   036   045   000    Old_age   Always       -       36 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   018   009   000    Old_age   Always       -       66600080
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       18661632908442
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2964606625
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2959907756

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      7323         -

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

$ sudo smartctl -d ata -a /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-16-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD1W8E8
LU WWN Device Id: 5 000c50 02fbeebc9
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Apr  8 00:34:10 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  623) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       230019088
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       26
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       262889512
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6412
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       27
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       6
189 High_Fly_Writes         0x003a   094   094   000    Old_age   Always       -       6
190 Airflow_Temperature_Cel 0x0022   067   060   045    Old_age   Always       -       33 (Min/Max 31/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       18
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       26
194 Temperature_Celsius     0x0022   033   040   000    Old_age   Always       -       33 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   023   009   000    Old_age   Always       -       230019088
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       196954315299042
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       310312834
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2466541276

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      6408         -
# 2  Extended offline    Completed without error       00%      6346         -
# 3  Extended offline    Completed without error       00%      6331         -

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

$ sudo smartctl -d ata -a /dev/sde
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-16-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    6YD1JP7R
LU WWN Device Id: 5 000c50 046199c58
Firmware Version: CC3C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Apr  8 00:34:12 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  602) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   099   006    Pre-fail  Always       -       174438584
  3 Spin_Up_Time            0x0003   093   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       9
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       61815160
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1026
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       9
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   097   000    Old_age   Always       -       3
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   062   045    Old_age   Always       -       34 (Min/Max 31/38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       9
194 Temperature_Celsius     0x0022   034   040   000    Old_age   Always       -       34 (0 22 0 0)
195 Hardware_ECC_Recovered  0x001a   022   013   000    Old_age   Always       -       174438584
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       187097365349377
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3081786508
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1511665227

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1022         -
# 2  Extended offline    Completed without error       00%       944         -

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

$sudo smartctl -d ata -a /dev/sdf
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-16-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD6P1D2
LU WWN Device Id: 5 000c50 046663f0c
Firmware Version: CC3C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Apr  8 00:34:13 2012 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  623) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       32727864
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       12
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   071   060   030    Pre-fail  Always       -       13366411
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       767
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       12
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       3
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   067   063   045    Old_age   Always       -       33 (Min/Max 30/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       12
194 Temperature_Celsius     0x0022   033   040   000    Old_age   Always       -       33 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   015   010   000    Old_age   Always       -       32727864
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       15543486644987
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1032912234
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3938478452

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       764         -

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

For those interested i used the following command to restore all my data.

```
sudo ./btrfs-restore /dev/md0p1 /mnt/temp1/ -v -t 4049822273536 -i

```

Where -v tells me which file it is working on.
-t was a number found using btrfs-find-root. 
-i ignores errors, i parsed the log afterwards to find the corrupt/incomplete files.
When you restart btrfs-restore it will not overwrites files it previously recoverd and will just add the files that don't exist from beforehand.

---

### Post by rubylaser on 2012-04-07
Glad to hear you were able to recover almost all of your data :)  I'd write zeroes to each of those disks and start from scratch.

---

### Post by rcastberg on 2012-04-20
Right one week later and two of the disks have failed already... 

I am checking with seagate if i can return them, but am hoping that somebody can help me confirm that its the disks that have the issues and not the controller/pc

The bigest concern is that the disks seem to be different drives than the problems i had earlier. (smartctl command fails)

If someone has a moment and can confirm my suspisions i will send both these drives to seagate warrenty repair.

The first disk isn't even showing up as a drive anymore, and running Seagate st tools:
```
sudo ./st -t 10 /dev/sda
Drive /dev/sda does not support DST - generic short test will be run
Starting 10 % Generic Short Test on drive /dev/sda (^C will abort test)
        test FAILED - sense data = 00/00/00
Generic Short Test FAILED on drive /dev/sda  cat

```

It failed with:
```
dmesg:
[2012-04-18 01:15:12]  ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[2012-04-18 01:15:12]  ata1.01: failed command: FLUSH CACHE EXT
[2012-04-18 01:15:12]  ata1.01: cmd ea/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[2012-04-18 01:15:12]           res 40/00:01:00:00:00/00:00:00:00:00/50 Emask 0x4 (timeout)
[2012-04-18 01:15:12]  ata1.01: status: { DRDY }
[2012-04-18 01:15:17]  ata1: link is slow to respond, please be patient (ready=0)
[2012-04-18 01:15:22]  ata1: device not ready (errno=-16), forcing hardreset
[2012-04-18 01:15:22]  ata1: soft resetting link
[2012-04-18 01:15:28]  ata1: link is slow to respond, please be patient (ready=0)
[2012-04-18 01:15:32]  ata1: SRST failed (errno=-16)
[2012-04-18 01:15:32]  ata1: soft resetting link
[2012-04-18 01:15:38]  ata1: link is slow to respond, please be patient (ready=0)
[2012-04-18 01:15:42]  ata1: SRST failed (errno=-16)
[2012-04-18 01:15:42]  ata1: soft resetting link
[2012-04-18 01:15:48]  ata1: link is slow to respond, please be patient (ready=0)
[2012-04-18 01:16:17]  ata1: SRST failed (errno=-16)
[2012-04-18 01:16:17]  ata1: soft resetting link
[2012-04-18 01:16:23]  ata1: SRST failed (errno=-16)
[2012-04-18 01:16:23]  ata1: reset failed, giving up
[2012-04-18 01:16:23]  ata1.00: disabled
[2012-04-18 01:16:23]  ata1.01: disabled
[2012-04-18 01:16:23]  ata1.01: device reported invalid CHS sector 0
[2012-04-18 01:16:23]  ata1: EH complete
[2012-04-18 01:16:23]  sd 1:0:1:0: [sda] Unhandled error code
[2012-04-18 01:16:23]  sd 1:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-18 01:16:23]  sd 1:0:1:0: [sda] CDB: Write(10): 2a 00 00 00 08 08 00 00 02 00
[2012-04-18 01:16:23]  end_request: I/O error, dev sda, sector 2056
[2012-04-18 01:16:23]  end_request: I/O error, dev sda, sector 2056
[2012-04-18 01:16:23]  md: super_written gets error=-5, uptodate=0
[2012-04-18 01:16:23]  md/raid:md0: Disk failure on sda1, disabling device.
[2012-04-18 01:16:23]  md/raid:md0: Operation continuing on 4 devices.
[2012-04-18 01:16:23]  sd 1:0:1:0: [sda] Unhandled error code
[2012-04-18 01:16:23]  sd 1:0:1:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-18 01:16:23]  sd 1:0:1:0: [sda] CDB: Read(10): 28 00 6c 1d 03 18 00 00 20 00
[2012-04-18 01:16:23]  end_request: I/O error, dev sda, sector 1813840664
[2012-04-18 01:16:23]  RAID conf printout:
[2012-04-18 01:16:23]   --- level:6 rd:5 wd:4
[2012-04-18 01:16:23]   disk 0, o:1, dev:sdc1
[2012-04-18 01:16:23]   disk 1, o:1, dev:sdd1
[2012-04-18 01:16:23]   disk 2, o:1, dev:sde1
[2012-04-18 01:16:23]   disk 3, o:1, dev:sdf1
[2012-04-18 01:16:23]   disk 4, o:0, dev:sda1
[2012-04-18 01:16:23]  RAID conf printout:
[2012-04-18 01:16:23]   --- level:6 rd:5 wd:4
[2012-04-18 01:16:23]   disk 0, o:1, dev:sdc1
[2012-04-18 01:16:23]   disk 1, o:1, dev:sdd1
[2012-04-18 01:16:23]   disk 2, o:1, dev:sde1
[2012-04-18 01:16:23]   disk 3, o:1, dev:sdf1

```

Today the another drive failed, what confuses me a bit is what looks like a segfault :
```
[2012-04-20 08:30:45]  EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[2012-04-20 08:31:12]  EXT4-fs (md0): re-mounted. Opts: commit=0
[2012-04-20 08:47:56]  ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[2012-04-20 08:47:56]  ata4.00: failed command: FLUSH CACHE EXT
[2012-04-20 08:47:56]  ata4.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[2012-04-20 08:47:56]           res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[2012-04-20 08:47:56]  ata4.00: status: { DRDY }
[2012-04-20 08:47:56]  ata4: hard resetting link
[2012-04-20 08:48:06]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:48:06]  ata4: hard resetting link
[2012-04-20 08:48:16]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:48:16]  ata4: hard resetting link
[2012-04-20 08:48:51]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:48:51]  ata4: limiting SATA link speed to 3.0 Gbps
[2012-04-20 08:48:51]  ata4: hard resetting link
[2012-04-20 08:48:57]  ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[2012-04-20 08:48:57]  ata4.00: link online but device misclassifed
[2012-04-20 08:49:02]  ata4.00: qc timeout (cmd 0xec)
[2012-04-20 08:49:02]  ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[2012-04-20 08:49:02]  ata4.00: revalidation failed (errno=-5)
[2012-04-20 08:49:02]  ata4: hard resetting link
[2012-04-20 08:49:10]  INFO: task jbd2/md0-8:1264 blocked for more than 120 seconds.
[2012-04-20 08:49:10]  "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[2012-04-20 08:49:10]  jbd2/md0-8      D 0000000000000001     0  1264      2 0x00000000
[2012-04-20 08:49:10]   ffff88031b6f7be0 0000000000000046 ffff88031b6f7b80 ffffffff81032a69
[2012-04-20 08:49:10]   ffff88031b6f7fd8 ffff88031b6f7fd8 ffff88031b6f7fd8 0000000000012a40
[2012-04-20 08:49:10]   ffff8802f48c4560 ffff88031b63ae40 ffff88031b6f7bc0 ffff88032fc532c0
[2012-04-20 08:49:10]  Call Trace:
[2012-04-20 08:49:10]   [<ffffffff81032a69>] ? default_spin_lock_flags+0x9/0x10
[2012-04-20 08:49:10]   [<ffffffff81196700>] ? __wait_on_buffer+0x30/0x30
[2012-04-20 08:49:10]   [<ffffffff8160599f>] schedule+0x3f/0x60
[2012-04-20 08:49:10]   [<ffffffff81605a4f>] io_schedule+0x8f/0xd0
[2012-04-20 08:49:10]   [<ffffffff8119670e>] sleep_on_buffer+0xe/0x20
[2012-04-20 08:49:10]   [<ffffffff8160626f>] __wait_on_bit+0x5f/0x90
[2012-04-20 08:49:10]   [<ffffffff81196700>] ? __wait_on_buffer+0x30/0x30
[2012-04-20 08:49:10]   [<ffffffff8160631c>] out_of_line_wait_on_bit+0x7c/0x90
[2012-04-20 08:49:10]   [<ffffffff81081890>] ? autoremove_wake_function+0x40/0x40
[2012-04-20 08:49:10]   [<ffffffff811966fe>] __wait_on_buffer+0x2e/0x30
[2012-04-20 08:49:10]   [<ffffffff812488d5>] jbd2_journal_commit_transaction+0x10f5/0x1250
[2012-04-20 08:49:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:49:10]   [<ffffffff8124c89b>] kjournald2+0xbb/0x220
[2012-04-20 08:49:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:49:10]   [<ffffffff8124c7e0>] ? commit_timeout+0x10/0x10
[2012-04-20 08:49:10]   [<ffffffff81080dac>] kthread+0x8c/0xa0
[2012-04-20 08:49:10]   [<ffffffff81610da4>] kernel_thread_helper+0x4/0x10
[2012-04-20 08:49:10]   [<ffffffff81080d20>] ? flush_kthread_worker+0xa0/0xa0
[2012-04-20 08:49:10]   [<ffffffff81610da0>] ? gs_change+0x13/0x13
[2012-04-20 08:49:10]  INFO: task rdiff-backup:32302 blocked for more than 120 seconds.
[2012-04-20 08:49:10]  "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[2012-04-20 08:49:10]  rdiff-backup    D ffffffff81805120     0 32302  32245 0x00000000
[2012-04-20 08:49:10]   ffff88031c34de38 0000000000000082 ffff88031c34ddd8 0000000300000001
[2012-04-20 08:49:10]   ffff88031c34dfd8 ffff88031c34dfd8 ffff88031c34dfd8 0000000000012a40
[2012-04-20 08:49:10]   ffffffff81c0b020 ffff88031ca92e40 ffff88031c34de48 ffff88031b1ba800
[2012-04-20 08:49:10]  Call Trace:
[2012-04-20 08:49:10]   [<ffffffff8160599f>] schedule+0x3f/0x60
[2012-04-20 08:49:10]   [<ffffffff8124c675>] jbd2_log_wait_commit+0xb5/0x130
[2012-04-20 08:49:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:49:10]   [<ffffffff81200af0>] ext4_sync_file+0x1c0/0x260
[2012-04-20 08:49:10]   [<ffffffff8119452f>] vfs_fsync_range+0x5f/0xa0
[2012-04-20 08:49:10]   [<ffffffff811945dc>] vfs_fsync+0x1c/0x20
[2012-04-20 08:49:10]   [<ffffffff811948f3>] sys_fsync+0x33/0x50
[2012-04-20 08:49:10]   [<ffffffff8160fc82>] system_call_fastpath+0x16/0x1b
[2012-04-20 08:49:10]  INFO: task flush-9:0:32311 blocked for more than 120 seconds.
[2012-04-20 08:49:10]  "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[2012-04-20 08:49:10]  flush-9:0       D 0000000000000001     0 32311      2 0x00000000
[2012-04-20 08:49:10]   ffff88011b96f540 0000000000000046 ffffffff81607d0e ffff88011b96f620
[2012-04-20 08:49:10]   ffff88011b96ffd8 ffff88011b96ffd8 ffff88011b96ffd8 0000000000012a40
[2012-04-20 08:49:10]   ffff880038480000 ffff88031c3e5c80 ffff88011b96f530 ffff8803181a87a0
[2012-04-20 08:49:10]  Call Trace:
[2012-04-20 08:49:10]   [<ffffffff81607d0e>] ? common_interrupt+0xe/0x13
[2012-04-20 08:49:10]   [<ffffffff8160599f>] schedule+0x3f/0x60
[2012-04-20 08:49:10]   [<ffffffffa01685ba>] get_active_stripe+0x31a/0x400 [raid456]
[2012-04-20 08:49:10]   [<ffffffff810574b0>] ? try_to_wake_up+0x200/0x200
[2012-04-20 08:49:10]   [<ffffffffa016c069>] make_request+0x199/0x440 [raid456]
[2012-04-20 08:49:10]   [<ffffffff81153582>] ? kmem_cache_alloc+0x112/0x120
[2012-04-20 08:49:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:49:10]   [<ffffffff814a4956>] md_make_request+0xc6/0x200
[2012-04-20 08:49:10]   [<ffffffff8119bfa8>] ? bvec_alloc_bs+0x68/0x100
[2012-04-20 08:49:10]   [<ffffffff812ce55a>] generic_make_request.part.51+0x24a/0x510
[2012-04-20 08:49:10]   [<ffffffff8119b8e3>] ? bio_add_page+0x53/0x60
[2012-04-20 08:49:10]   [<ffffffff812ce865>] generic_make_request+0x45/0x60
[2012-04-20 08:49:10]   [<ffffffff812ce907>] submit_bio+0x87/0x110
[2012-04-20 08:49:10]   [<ffffffff8120d159>] ext4_io_submit+0x29/0x60
[2012-04-20 08:49:10]   [<ffffffff81207335>] mpage_da_submit_io+0x315/0x570
[2012-04-20 08:49:10]   [<ffffffff8120783b>] ? ext4_mark_iloc_dirty+0x6b/0x90
[2012-04-20 08:49:10]   [<ffffffff81207982>] ? ext4_mark_inode_dirty+0x82/0x210
[2012-04-20 08:49:10]   [<ffffffff8120b5ce>] mpage_da_map_and_submit+0x1ce/0x360
[2012-04-20 08:49:10]   [<ffffffff81245433>] ? jbd2_journal_start+0x13/0x20
[2012-04-20 08:49:10]   [<ffffffff8120bfe6>] ext4_da_writepages+0x346/0x5e0
[2012-04-20 08:49:10]   [<ffffffff81114bf1>] do_writepages+0x21/0x40
[2012-04-20 08:49:10]   [<ffffffff8118fdd3>] writeback_single_inode+0x103/0x280
[2012-04-20 08:49:10]   [<ffffffff811901e1>] writeback_sb_inodes+0xe1/0x1b0
[2012-04-20 08:49:10]   [<ffffffff81190546>] writeback_inodes_wb+0xa6/0xf0
[2012-04-20 08:49:10]   [<ffffffff811908df>] wb_writeback+0x34f/0x450
[2012-04-20 08:49:10]   [<ffffffff81048408>] ? hrtick_update+0x38/0x40
[2012-04-20 08:49:10]   [<ffffffff81190a78>] wb_check_old_data_flush+0x98/0xa0
[2012-04-20 08:49:10]   [<ffffffff81190bd1>] wb_do_writeback+0x151/0x1f0
[2012-04-20 08:49:10]   [<ffffffff81607a8e>] ? _raw_spin_lock_irqsave+0x2e/0x40
[2012-04-20 08:49:10]   [<ffffffff8106df10>] ? usleep_range+0x50/0x50
[2012-04-20 08:49:10]   [<ffffffff81190cf3>] bdi_writeback_thread+0x83/0x2a0
[2012-04-20 08:49:10]   [<ffffffff81190c70>] ? wb_do_writeback+0x1f0/0x1f0
[2012-04-20 08:49:10]   [<ffffffff81080dac>] kthread+0x8c/0xa0
[2012-04-20 08:49:10]   [<ffffffff81610da4>] kernel_thread_helper+0x4/0x10
[2012-04-20 08:49:10]   [<ffffffff81080d20>] ? flush_kthread_worker+0xa0/0xa0
[2012-04-20 08:49:10]   [<ffffffff81610da0>] ? gs_change+0x13/0x13
[2012-04-20 08:49:12]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:49:12]  ata4: hard resetting link
[2012-04-20 08:49:22]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:49:22]  ata4: hard resetting link
[2012-04-20 08:49:57]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:49:57]  ata4: limiting SATA link speed to 1.5 Gbps
[2012-04-20 08:49:57]  ata4: hard resetting link
[2012-04-20 08:50:02]  ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[2012-04-20 08:50:02]  ata4.00: link online but device misclassifed
[2012-04-20 08:50:12]  ata4.00: qc timeout (cmd 0xec)
[2012-04-20 08:50:12]  ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[2012-04-20 08:50:12]  ata4.00: revalidation failed (errno=-5)
[2012-04-20 08:50:12]  ata4: hard resetting link
[2012-04-20 08:50:22]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:50:22]  ata4: hard resetting link
[2012-04-20 08:50:32]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:50:32]  ata4: hard resetting link
[2012-04-20 08:51:07]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:51:07]  ata4: hard resetting link
[2012-04-20 08:51:10]  INFO: task jbd2/md0-8:1264 blocked for more than 120 seconds.
[2012-04-20 08:51:10]  "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[2012-04-20 08:51:10]  jbd2/md0-8      D 0000000000000001     0  1264      2 0x00000000
[2012-04-20 08:51:10]   ffff88031b6f7be0 0000000000000046 ffff88031b6f7b80 ffffffff81032a69
[2012-04-20 08:51:10]   ffff88031b6f7fd8 ffff88031b6f7fd8 ffff88031b6f7fd8 0000000000012a40
[2012-04-20 08:51:10]   ffff8802f48c4560 ffff88031b63ae40 ffff88031b6f7bc0 ffff88032fc532c0
[2012-04-20 08:51:10]  Call Trace:
[2012-04-20 08:51:10]   [<ffffffff81032a69>] ? default_spin_lock_flags+0x9/0x10
[2012-04-20 08:51:10]   [<ffffffff81196700>] ? __wait_on_buffer+0x30/0x30
[2012-04-20 08:51:10]   [<ffffffff8160599f>] schedule+0x3f/0x60
[2012-04-20 08:51:10]   [<ffffffff81605a4f>] io_schedule+0x8f/0xd0
[2012-04-20 08:51:10]   [<ffffffff8119670e>] sleep_on_buffer+0xe/0x20
[2012-04-20 08:51:10]   [<ffffffff8160626f>] __wait_on_bit+0x5f/0x90
[2012-04-20 08:51:10]   [<ffffffff81196700>] ? __wait_on_buffer+0x30/0x30
[2012-04-20 08:51:10]   [<ffffffff8160631c>] out_of_line_wait_on_bit+0x7c/0x90
[2012-04-20 08:51:10]   [<ffffffff81081890>] ? autoremove_wake_function+0x40/0x40
[2012-04-20 08:51:10]   [<ffffffff811966fe>] __wait_on_buffer+0x2e/0x30
[2012-04-20 08:51:10]   [<ffffffff812488d5>] jbd2_journal_commit_transaction+0x10f5/0x1250
[2012-04-20 08:51:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:51:10]   [<ffffffff8124c89b>] kjournald2+0xbb/0x220
[2012-04-20 08:51:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:51:10]   [<ffffffff8124c7e0>] ? commit_timeout+0x10/0x10
[2012-04-20 08:51:10]   [<ffffffff81080dac>] kthread+0x8c/0xa0
[2012-04-20 08:51:10]   [<ffffffff81610da4>] kernel_thread_helper+0x4/0x10
[2012-04-20 08:51:10]   [<ffffffff81080d20>] ? flush_kthread_worker+0xa0/0xa0
[2012-04-20 08:51:10]   [<ffffffff81610da0>] ? gs_change+0x13/0x13
[2012-04-20 08:51:10]  INFO: task rdiff-backup:32302 blocked for more than 120 seconds.
[2012-04-20 08:51:10]  "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[2012-04-20 08:51:10]  rdiff-backup    D ffffffff81805120     0 32302  32245 0x00000000
[2012-04-20 08:51:10]   ffff88031c34de38 0000000000000082 ffff88031c34ddd8 0000000300000001
[2012-04-20 08:51:10]   ffff88031c34dfd8 ffff88031c34dfd8 ffff88031c34dfd8 0000000000012a40
[2012-04-20 08:51:10]   ffffffff81c0b020 ffff88031ca92e40 ffff88031c34de48 ffff88031b1ba800
[2012-04-20 08:51:10]  Call Trace:
[2012-04-20 08:51:10]   [<ffffffff8160599f>] schedule+0x3f/0x60
[2012-04-20 08:51:10]   [<ffffffff8124c675>] jbd2_log_wait_commit+0xb5/0x130
[2012-04-20 08:51:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:51:10]   [<ffffffff81200af0>] ext4_sync_file+0x1c0/0x260
[2012-04-20 08:51:10]   [<ffffffff8119452f>] vfs_fsync_range+0x5f/0xa0
[2012-04-20 08:51:10]   [<ffffffff811945dc>] vfs_fsync+0x1c/0x20
[2012-04-20 08:51:10]   [<ffffffff811948f3>] sys_fsync+0x33/0x50
[2012-04-20 08:51:10]   [<ffffffff8160fc82>] system_call_fastpath+0x16/0x1b
[2012-04-20 08:51:10]  INFO: task flush-9:0:32311 blocked for more than 120 seconds.
[2012-04-20 08:51:10]  "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[2012-04-20 08:51:10]  flush-9:0       D 0000000000000001     0 32311      2 0x00000000
[2012-04-20 08:51:10]   ffff88011b96f540 0000000000000046 ffffffff81607d0e ffff88011b96f620
[2012-04-20 08:51:10]   ffff88011b96ffd8 ffff88011b96ffd8 ffff88011b96ffd8 0000000000012a40
[2012-04-20 08:51:10]   ffff880038480000 ffff88031c3e5c80 ffff88011b96f530 ffff8803181a87a0
[2012-04-20 08:51:10]  Call Trace:
[2012-04-20 08:51:10]   [<ffffffff81607d0e>] ? common_interrupt+0xe/0x13
[2012-04-20 08:51:10]   [<ffffffff8160599f>] schedule+0x3f/0x60
[2012-04-20 08:51:10]   [<ffffffffa01685ba>] get_active_stripe+0x31a/0x400 [raid456]
[2012-04-20 08:51:10]   [<ffffffff810574b0>] ? try_to_wake_up+0x200/0x200
[2012-04-20 08:51:10]   [<ffffffffa016c069>] make_request+0x199/0x440 [raid456]
[2012-04-20 08:51:10]   [<ffffffff81153582>] ? kmem_cache_alloc+0x112/0x120
[2012-04-20 08:51:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:51:10]   [<ffffffff814a4956>] md_make_request+0xc6/0x200
[2012-04-20 08:51:10]   [<ffffffff8119bfa8>] ? bvec_alloc_bs+0x68/0x100
[2012-04-20 08:51:10]   [<ffffffff812ce55a>] generic_make_request.part.51+0x24a/0x510
[2012-04-20 08:51:10]   [<ffffffff8119b8e3>] ? bio_add_page+0x53/0x60
[2012-04-20 08:51:10]   [<ffffffff812ce865>] generic_make_request+0x45/0x60
[2012-04-20 08:51:10]   [<ffffffff812ce907>] submit_bio+0x87/0x110
[2012-04-20 08:51:10]   [<ffffffff8120d159>] ext4_io_submit+0x29/0x60
[2012-04-20 08:51:10]   [<ffffffff81207335>] mpage_da_submit_io+0x315/0x570
[2012-04-20 08:51:10]   [<ffffffff8120783b>] ? ext4_mark_iloc_dirty+0x6b/0x90
[2012-04-20 08:51:10]   [<ffffffff81207982>] ? ext4_mark_inode_dirty+0x82/0x210
[2012-04-20 08:51:10]   [<ffffffff8120b5ce>] mpage_da_map_and_submit+0x1ce/0x360
[2012-04-20 08:51:10]   [<ffffffff81245433>] ? jbd2_journal_start+0x13/0x20
[2012-04-20 08:51:10]   [<ffffffff8120bfe6>] ext4_da_writepages+0x346/0x5e0
[2012-04-20 08:51:10]   [<ffffffff81114bf1>] do_writepages+0x21/0x40
[2012-04-20 08:51:10]   [<ffffffff8118fdd3>] writeback_single_inode+0x103/0x280
[2012-04-20 08:51:10]   [<ffffffff811901e1>] writeback_sb_inodes+0xe1/0x1b0
[2012-04-20 08:51:10]   [<ffffffff81190546>] writeback_inodes_wb+0xa6/0xf0
[2012-04-20 08:51:10]   [<ffffffff811908df>] wb_writeback+0x34f/0x450
[2012-04-20 08:51:10]   [<ffffffff81048408>] ? hrtick_update+0x38/0x40
[2012-04-20 08:51:10]   [<ffffffff81190a78>] wb_check_old_data_flush+0x98/0xa0
[2012-04-20 08:51:10]   [<ffffffff81190bd1>] wb_do_writeback+0x151/0x1f0
[2012-04-20 08:51:10]   [<ffffffff81607a8e>] ? _raw_spin_lock_irqsave+0x2e/0x40
[2012-04-20 08:51:10]   [<ffffffff8106df10>] ? usleep_range+0x50/0x50
[2012-04-20 08:51:10]   [<ffffffff81190cf3>] bdi_writeback_thread+0x83/0x2a0
[2012-04-20 08:51:10]   [<ffffffff81190c70>] ? wb_do_writeback+0x1f0/0x1f0
[2012-04-20 08:51:10]   [<ffffffff81080dac>] kthread+0x8c/0xa0
[2012-04-20 08:51:10]   [<ffffffff81610da4>] kernel_thread_helper+0x4/0x10
[2012-04-20 08:51:10]   [<ffffffff81080d20>] ? flush_kthread_worker+0xa0/0xa0
[2012-04-20 08:51:10]   [<ffffffff81610da0>] ? gs_change+0x13/0x13
[2012-04-20 08:51:10]  INFO: task rsync:369 blocked for more than 120 seconds.
[2012-04-20 08:51:10]  "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[2012-04-20 08:51:10]  rsync           D ffffffff81805120     0   369    368 0x00000000
[2012-04-20 08:51:10]   ffff8801b86c7328 0000000000000082 ffff8801b86c7328 ffffffff812d14d7
[2012-04-20 08:51:10]   ffff8801b86c7fd8 ffff8801b86c7fd8 ffff8801b86c7fd8 0000000000012a40
[2012-04-20 08:51:10]   ffffffff81c0b020 ffff88023d749720 ffff8801b86c7318 ffff8803181a87a0
[2012-04-20 08:51:10]  Call Trace:
[2012-04-20 08:51:10]   [<ffffffff812d14d7>] ? blk_flush_plug_list+0xa7/0x250
[2012-04-20 08:51:10]   [<ffffffff8160599f>] schedule+0x3f/0x60
[2012-04-20 08:51:10]   [<ffffffffa01685ba>] get_active_stripe+0x31a/0x400 [raid456]
[2012-04-20 08:51:10]   [<ffffffff810574b0>] ? try_to_wake_up+0x200/0x200
[2012-04-20 08:51:10]   [<ffffffffa016c069>] make_request+0x199/0x440 [raid456]
[2012-04-20 08:51:10]   [<ffffffff81081850>] ? add_wait_queue+0x60/0x60
[2012-04-20 08:51:10]   [<ffffffff814a4956>] md_make_request+0xc6/0x200
[2012-04-20 08:51:10]   [<ffffffff8119bfa8>] ? bvec_alloc_bs+0x68/0x100
[2012-04-20 08:51:10]   [<ffffffff812ce55a>] generic_make_request.part.51+0x24a/0x510
[2012-04-20 08:51:10]   [<ffffffff8119b8e3>] ? bio_add_page+0x53/0x60
[2012-04-20 08:51:10]   [<ffffffff812ce865>] generic_make_request+0x45/0x60
[2012-04-20 08:51:10]   [<ffffffff812ce907>] submit_bio+0x87/0x110
[2012-04-20 08:51:10]   [<ffffffff8120d159>] ext4_io_submit+0x29/0x60
[2012-04-20 08:51:10]   [<ffffffff81207335>] mpage_da_submit_io+0x315/0x570
[2012-04-20 08:51:10]   [<ffffffff8120783b>] ? ext4_mark_iloc_dirty+0x6b/0x90
[2012-04-20 08:51:10]   [<ffffffff81207982>] ? ext4_mark_inode_dirty+0x82/0x210
[2012-04-20 08:51:10]   [<ffffffff8120b5ce>] mpage_da_map_and_submit+0x1ce/0x360
[2012-04-20 08:51:10]   [<ffffffff81245433>] ? jbd2_journal_start+0x13/0x20
[2012-04-20 08:51:10]   [<ffffffff8120bfe6>] ext4_da_writepages+0x346/0x5e0
[2012-04-20 08:51:10]   [<ffffffff81197467>] ? __find_get_block+0x87/0xe0
[2012-04-20 08:51:10]   [<ffffffff81114bf1>] do_writepages+0x21/0x40
[2012-04-20 08:51:10]   [<ffffffff8118fdd3>] writeback_single_inode+0x103/0x280
[2012-04-20 08:51:10]   [<ffffffff811901e1>] writeback_sb_inodes+0xe1/0x1b0
[2012-04-20 08:51:10]   [<ffffffff81190546>] writeback_inodes_wb+0xa6/0xf0
[2012-04-20 08:51:10]   [<ffffffff815f44ee>] balance_dirty_pages.isra.14+0x217/0x34e
[2012-04-20 08:51:10]   [<ffffffff8111491a>] balance_dirty_pages_ratelimited_nr+0x6a/0x70
[2012-04-20 08:51:10]   [<ffffffff81109d72>] generic_perform_write+0x152/0x1c0
[2012-04-20 08:51:10]   [<ffffffff8120c640>] ? ext4_dirty_inode+0x50/0x60
[2012-04-20 08:51:10]   [<ffffffff81109e3d>] generic_file_buffered_write+0x5d/0x90
[2012-04-20 08:51:10]   [<ffffffff8110b7a9>] __generic_file_aio_write+0x229/0x440
[2012-04-20 08:51:10]   [<ffffffff8110ba2f>] generic_file_aio_write+0x6f/0xe0
[2012-04-20 08:51:10]   [<ffffffff812005df>] ext4_file_write+0xbf/0x260
[2012-04-20 08:51:10]   [<ffffffff81167e62>] do_sync_write+0xd2/0x110
[2012-04-20 08:51:10]   [<ffffffff812834ec>] ? security_file_permission+0x2c/0xb0
[2012-04-20 08:51:10]   [<ffffffff811682b1>] ? rw_verify_area+0x61/0xf0
[2012-04-20 08:51:10]   [<ffffffff81168613>] vfs_write+0xb3/0x180
[2012-04-20 08:51:10]   [<ffffffff8116893a>] sys_write+0x4a/0x90
[2012-04-20 08:51:10]   [<ffffffff8160fc82>] system_call_fastpath+0x16/0x1b
[2012-04-20 08:51:12]  ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[2012-04-20 08:51:12]  ata4.00: link online but device misclassifed
[2012-04-20 08:51:42]  ata4.00: qc timeout (cmd 0xec)
[2012-04-20 08:51:42]  ata4.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[2012-04-20 08:51:42]  ata4.00: revalidation failed (errno=-5)
[2012-04-20 08:51:42]  ata4.00: disabled
[2012-04-20 08:51:42]  ata4.00: device reported invalid CHS sector 0
[2012-04-20 08:51:42]  ata4: hard resetting link
[2012-04-20 08:51:52]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:51:52]  ata4: hard resetting link
[2012-04-20 08:52:02]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:52:02]  ata4: hard resetting link
[2012-04-20 08:52:37]  ata4: softreset failed (1st FIS failed)
[2012-04-20 08:52:37]  ata4: hard resetting link
[2012-04-20 08:52:42]  ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[2012-04-20 08:52:42]  ata4.00: link online but device misclassifed
[2012-04-20 08:52:42]  ata4: EH complete
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] Unhandled error code
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 66 85 b4 00 00 04 00 00
[2012-04-20 08:52:42]  end_request: I/O error, dev sdc, sector 1720038400
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] Unhandled error code
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 66 85 b8 00 00 00 e8 00
[2012-04-20 08:52:42]  end_request: I/O error, dev sdc, sector 1720039424
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] Unhandled error code
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 66 85 b8 e8 00 03 18 00
[2012-04-20 08:52:42]  end_request: I/O error, dev sdc, sector 1720039656
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] Unhandled error code
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] CDB: Write(10): 2a 00 66 85 b4 00 00 04 00 00
[2012-04-20 08:52:42]  end_request: I/O error, dev sdc, sector 1720038400
[2012-04-20 08:52:42]  md/raid:md0: Disk failure on sdc1, disabling device.
[2012-04-20 08:52:42]  md/raid:md0: Operation continuing on 3 devices.
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] Unhandled error code
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] CDB: Write(10): 2a 00 66 85 b8 00 00 00 e8 00
[2012-04-20 08:52:42]  end_request: I/O error, dev sdc, sector 1720039424
[2012-04-20 08:52:42]  raid5_end_read_request: 9 callbacks suppressed
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037608 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037616 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037624 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037632 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037640 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037648 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037656 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037664 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037672 on sdc1).
[2012-04-20 08:52:42]  md/raid:md0: read error not correctable (sector 1720037680 on sdc1).
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] Unhandled error code
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 6c ee a1 08 00 00 a8 00
[2012-04-20 08:52:42]  end_request: I/O error, dev sdc, sector 1827578120
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] Unhandled error code
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[2012-04-20 08:52:42]  sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 6d b7 35 88 00 00 40 00
[2012-04-20 08:52:42]  end_request: I/O error, dev sdc, sector 1840723336
[2012-04-20 08:52:42]  RAID conf printout:
[2012-04-20 08:52:42]   --- level:6 rd:5 wd:3
[2012-04-20 08:52:42]   disk 0, o:1, dev:sdb1
[2012-04-20 08:52:42]   disk 1, o:0, dev:sdc1
[2012-04-20 08:52:42]   disk 2, o:1, dev:sdd1
[2012-04-20 08:52:42]   disk 3, o:1, dev:sde1
[2012-04-20 08:52:42]  RAID conf printout:
[2012-04-20 08:52:42]   --- level:6 rd:5 wd:3
[2012-04-20 08:52:42]   disk 0, o:1, dev:sdb1
[2012-04-20 08:52:42]   disk 2, o:1, dev:sdd1
[2012-04-20 08:52:42]   disk 3, o:1, dev:sde1


```

St tools. (I am planning on power cycling the pc when i get home to see if they become responsive again.
```
Drive /dev/sdc1 does not support DST - generic short test will be run
Starting 10 % Generic Short Test on drive /dev/sdc1 (^C will abort test)
        test FAILED - sense data = 00/00/00
Generic Short Test FAILED on drive /dev/sdc1  
```


Regards

Rene Castberg

---

### Post by rubylaser on 2012-04-20
Run these
```
smartctl -t long /dev/sda
smartctl -t long /dev/sdc
```

Wait a few hours for them to complete, and then post the entire output of these two commands when they're done.

```
smartctl -a /dev/sda
smartctl -a /dev/sdc
```

---

### Post by rcastberg on 2012-04-20
A 3rd disk failed today. I was unable to gain access to two of the disks until i powered down and restarted the computer. I have attached the long tests from each drive and there are no fails.
(Listed them by serial as that is easier to follow, they correspond to sda/sdc/sdd) 

I have so far run a short test with seagate tools and it also doesn't find any problems.

Power, doesn't seem likely to be the culprit as the drives are behind a UPS and the system is only drawing 180W out of a possible of 650W.

The failed disks are all on the same controller (motherboard), and were purchased at the same time.

Rene 

Syslog
```
Apr 20 11:08:28 Asgard kernel: [153318.880079] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr 20 11:08:28 Asgard kernel: [153318.881052] ata7.00: failed command: FLUSH CACHE EXT
Apr 20 11:08:28 Asgard kernel: [153318.882033] ata7.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Apr 20 11:08:28 Asgard kernel: [153318.882036]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Apr 20 11:08:28 Asgard kernel: [153318.884215] ata7.00: status: { DRDY }
Apr 20 11:08:28 Asgard kernel: [153318.880079] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr 20 11:08:28 Asgard kernel: [153318.881052] ata7.00: failed command: FLUSH CACHE EXT
Apr 20 11:08:28 Asgard kernel: [153318.882033] ata7.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Apr 20 11:08:28 Asgard kernel: [153318.882036]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Apr 20 11:08:28 Asgard kernel: [153318.884215] ata7.00: status: { DRDY }
Apr 20 11:08:28 Asgard kernel: [153318.885358] ata7: hard resetting link
Apr 20 11:08:28 Asgard kernel: [153318.885358] ata7: hard resetting link
Apr 20 11:08:38 Asgard kernel: [153328.884068] ata7: softreset failed (1st FIS failed)
Apr 20 11:08:38 Asgard kernel: [153328.885312] ata7: hard resetting link
Apr 20 11:08:38 Asgard kernel: [153328.884068] ata7: softreset failed (1st FIS failed)
Apr 20 11:08:38 Asgard kernel: [153328.885312] ata7: hard resetting link
Apr 20 11:08:48 Asgard kernel: [153338.888077] ata7: softreset failed (1st FIS failed)
Apr 20 11:08:48 Asgard kernel: [153338.889322] ata7: hard resetting link
Apr 20 11:08:48 Asgard kernel: [153338.888077] ata7: softreset failed (1st FIS failed)
Apr 20 11:08:48 Asgard kernel: [153338.889322] ata7: hard resetting link
Apr 20 11:09:23 Asgard kernel: [153373.888077] ata7: softreset failed (1st FIS failed)
Apr 20 11:09:23 Asgard kernel: [153373.889317] ata7: limiting SATA link speed to 3.0 Gbps
Apr 20 11:09:23 Asgard kernel: [153373.889324] ata7: hard resetting link
Apr 20 11:09:23 Asgard kernel: [153373.888077] ata7: softreset failed (1st FIS failed)
Apr 20 11:09:23 Asgard kernel: [153373.889317] ata7: limiting SATA link speed to 3.0 Gbps
Apr 20 11:09:23 Asgard kernel: [153373.889324] ata7: hard resetting link
Apr 20 11:09:29 Asgard kernel: [153379.076043] ata7: softreset failed (device not ready)
Apr 20 11:09:29 Asgard kernel: [153379.077304] ata7: reset failed, giving up
Apr 20 11:09:29 Asgard kernel: [153379.078553] ata7.00: disabled
Apr 20 11:09:29 Asgard kernel: [153379.078562] ata7.00: device reported invalid CHS sector 0
Apr 20 11:09:29 Asgard kernel: [153379.078579] ata7: EH complete
Apr 20 11:09:29 Asgard kernel: [153379.078654] sd 7:0:0:0: [sdd] Unhandled error code
Apr 20 11:09:29 Asgard kernel: [153379.078660] sd 7:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Apr 20 11:09:29 Asgard kernel: [153379.078670] sd 7:0:0:0: [sdd] CDB: Write(10): 2a 00 00 00 08 08 00 00 02 00
Apr 20 11:09:29 Asgard kernel: [153379.078688] end_request: I/O error, dev sdd, sector 2056
Apr 20 11:09:29 Asgard kernel: [153379.080048] end_request: I/O error, dev sdd, sector 2056
Apr 20 11:09:29 Asgard kernel: [153379.077304] ata7: reset failed, giving up
Apr 20 11:09:29 Asgard kernel: [153379.078553] ata7.00: disabled
Apr 20 11:09:29 Asgard kernel: [153379.078562] ata7.00: device reported invalid CHS sector 0
Apr 20 11:09:29 Asgard kernel: [153379.078579] ata7: EH complete
Apr 20 11:09:29 Asgard kernel: [153379.078654] sd 7:0:0:0: [sdd] Unhandled error code
Apr 20 11:09:29 Asgard kernel: [153379.078660] sd 7:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Apr 20 11:09:29 Asgard kernel: [153379.078670] sd 7:0:0:0: [sdd] CDB: Write(10): 2a 00 00 00 08 08 00 00 02 00
Apr 20 11:09:29 Asgard kernel: [153379.078688] end_request: I/O error, dev sdd, sector 2056
Apr 20 11:09:29 Asgard kernel: [153379.080048] end_request: I/O error, dev sdd, sector 2056
Apr 20 11:09:29 Asgard kernel: [153379.081373] md: super_written gets error=-5, uptodate=0
Apr 20 11:09:29 Asgard kernel: [153379.081383] md/raid:md0: Disk failure on sdd1, disabling device.
Apr 20 11:09:29 Asgard kernel: [153379.081387] md/raid:md0: Operation continuing on 2 devices.
Apr 20 11:09:29 Asgard kernel: [153379.084259] sd 7:0:0:0: [sdd] Unhandled error code
Apr 20 11:09:29 Asgard kernel: [153379.084265] sd 7:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Apr 20 11:09:29 Asgard kernel: [153379.084273] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 6c 9f fb 00 00 01 00 00
Apr 20 11:09:29 Asgard kernel: [153379.084290] end_request: I/O error, dev sdd, sector 1822423808
Apr 20 11:09:29 Asgard kernel: [153379.081373] md: super_written gets error=-5, uptodate=0
Apr 20 11:09:29 Asgard kernel: [153379.081383] md/raid:md0: Disk failure on sdd1, disabling device.
Apr 20 11:09:29 Asgard kernel: [153379.081387] md/raid:md0: Operation continuing on 2 devices.
Apr 20 11:09:29 Asgard kernel: [153379.084259] sd 7:0:0:0: [sdd] Unhandled error code
Apr 20 11:09:29 Asgard kernel: [153379.084265] sd 7:0:0:0: [sdd]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Apr 20 11:09:29 Asgard kernel: [153379.084273] sd 7:0:0:0: [sdd] CDB: Read(10): 28 00 6c 9f fb 00 00 01 00 00
Apr 20 11:09:29 Asgard kernel: [153379.084290] end_request: I/O error, dev sdd, sector 1822423808
Apr 20 11:09:30 Asgard kernel: [153380.073912] RAID conf printout:
Apr 20 11:09:30 Asgard kernel: [153380.073921]  --- level:6 rd:5 wd:2
Apr 20 11:09:30 Asgard kernel: [153380.073928]  disk 0, o:1, dev:sdb1
Apr 20 11:09:30 Asgard kernel: [153380.073933]  disk 2, o:0, dev:sdd1
Apr 20 11:09:30 Asgard kernel: [153380.073938]  disk 3, o:1, dev:sde1
Apr 20 11:09:30 Asgard kernel: [153380.073912] RAID conf printout:
Apr 20 11:09:30 Asgard kernel: [153380.073921]  --- level:6 rd:5 wd:2
Apr 20 11:09:30 Asgard kernel: [153380.073928]  disk 0, o:1, dev:sdb1
Apr 20 11:09:30 Asgard kernel: [153380.073933]  disk 2, o:0, dev:sdd1
Apr 20 11:09:30 Asgard kernel: [153380.073938]  disk 3, o:1, dev:sde1
Apr 20 11:09:30 Asgard kernel: [153380.088039] RAID conf printout:
Apr 20 11:09:30 Asgard kernel: [153380.088047]  --- level:6 rd:5 wd:2
Apr 20 11:09:30 Asgard kernel: [153380.088061]  disk 0, o:1, dev:sdb1
Apr 20 11:09:30 Asgard kernel: [153380.088066]  disk 3, o:1, dev:sde1
Apr 20 11:09:30 Asgard kernel: [153380.088460] quiet_error: 124 callbacks suppressed
Apr 20 11:09:30 Asgard kernel: [153380.088039] RAID conf printout:
Apr 20 11:09:30 Asgard kernel: [153380.088047]  --- level:6 rd:5 wd:2
Apr 20 11:09:30 Asgard kernel: [153380.088061]  disk 0, o:1, dev:sdb1
Apr 20 11:09:30 Asgard kernel: [153380.088066]  disk 3, o:1, dev:sde1
Apr 20 11:09:30 Asgard kernel: [153380.088460] quiet_error: 124 callbacks suppressed
Apr 20 11:09:30 Asgard kernel: [153380.088466] Buffer I/O error on device md0, logical block 698844029
Apr 20 11:09:30 Asgard kernel: [153380.090076] lost page write due to I/O error on md0
Apr 20 11:09:30 Asgard kernel: [153380.090090] Buffer I/O error on device md0, logical block 698844030
Apr 20 11:09:30 Asgard kernel: [153380.091681] lost page write due to I/O error on md0
Apr 20 11:09:30 Asgard kernel: [153380.091689] Buffer I/O error on device md0, logical block 698844158
Apr 20 11:09:30 Asgard kernel: [153380.093293] lost page write due to I/O error on md0
Apr 20 11:09:30 Asgard kernel: [153380.088466] Buffer I/O error on device md0, logical block 698844029
Apr 20 11:09:30 Asgard kernel: [153380.090076] lost page write due to I/O error on md0
......etc



```

---

### Post by rubylaser on 2012-04-20
All three of those drives look very healthy.  I'd be suspecting the SATA controller on the motherboard at this point.  Do you have a PCI-Express HBA that you can attach the drives to rule out the motherboard?

---

### Post by rcastberg on 2012-04-21
Got hold of pci sata controller today.

I rezeroed the drives and set up partitioning again (As i have all data backed up)

but when i create the array (Disk sda = 5YD24GMK): 
```
mdadm --create --verbose /dev/md0 --level=6 --raid-devices=5 /dev/sd[aihcf]1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 1953511936K
mdadm: Defaulting to version 1.2 metadata
mdadm: A**DD_NEW_DISK for /dev/sda1 failed: Device or resource busy**

```

Although the array goes on to  resync (with sda1 in the group)

Syslog from point when the partition was created.
```
Apr 21 18:34:50 Asgard kernel: [ 2374.434486] scsi_verify_blk_ioctl: 402 callbacks suppressed
Apr 21 18:34:50 Asgard kernel: [ 2374.434494] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434501] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434934] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434940] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435244] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435249] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435655] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435660] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434486] scsi_verify_blk_ioctl: 402 callbacks suppressed
Apr 21 18:34:50 Asgard kernel: [ 2374.434494] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434501] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434934] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434940] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435244] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435249] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435655] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435660] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447142] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447151] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447142] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447151] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.629142] md: could not open unknown-block(8,1).
Apr 21 18:34:50 Asgard kernel: [ 2374.629231] md: md_import_device returned -16
Apr 21 18:34:50 Asgard kernel: [ 2374.629142] md: could not open unknown-block(8,1).
Apr 21 18:34:50 Asgard kernel: [ 2374.629231] md: md_import_device returned -16
Apr 21 18:34:50 Asgard kernel: [ 2374.654839] md: bind<sda1>
Apr 21 18:34:50 Asgard kernel: [ 2374.654839] md: bind<sda1>
Apr 21 18:34:50 Asgard kernel: [ 2374.696994] md: bind<sdf1>
Apr 21 18:34:50 Asgard kernel: [ 2374.696994] md: bind<sdf1>
Apr 21 18:34:50 Asgard kernel: [ 2374.718340] md: bind<sdc1>
Apr 21 18:34:50 Asgard kernel: [ 2374.718340] md: bind<sdc1>
Apr 21 18:34:50 Asgard kernel: [ 2374.751766] md: bind<sdh1>
Apr 21 18:34:50 Asgard kernel: [ 2374.751766] md: bind<sdh1>
Apr 21 18:34:50 Asgard kernel: [ 2374.801788] md: bind<sdi1>
Apr 21 18:34:50 Asgard kernel: [ 2374.801788] md: bind<sdi1>
Apr 21 18:34:50 Asgard kernel: [ 2374.841492] md/raid:md0: not clean -- starting background reconstruction
Apr 21 18:34:50 Asgard kernel: [ 2374.841526] md/raid:md0: device sdi1 operational as raid disk 4
Apr 21 18:34:50 Asgard kernel: [ 2374.841533] md/raid:md0: device sdh1 operational as raid disk 3
Apr 21 18:34:50 Asgard kernel: [ 2374.841539] md/raid:md0: device sdc1 operational as raid disk 1
Apr 21 18:34:50 Asgard kernel: [ 2374.841544] md/raid:md0: device sdf1 operational as raid disk 2
Apr 21 18:34:50 Asgard kernel: [ 2374.841549] md/raid:md0: device sda1 operational as raid disk 0
Apr 21 18:34:50 Asgard kernel: [ 2374.842777] md/raid:md0: allocated 5334kB
Apr 21 18:34:50 Asgard kernel: [ 2374.842842] md/raid:md0: raid level 6 active with 5 out of 5 devices, algorithm 2
Apr 21 18:34:50 Asgard kernel: [ 2374.842847] RAID conf printout:
Apr 21 18:34:50 Asgard kernel: [ 2374.842851]  --- level:6 rd:5 wd:5
Apr 21 18:34:50 Asgard kernel: [ 2374.842856]  disk 0, o:1, dev:sda1
Apr 21 18:34:50 Asgard kernel: [ 2374.842860]  disk 1, o:1, dev:sdc1
Apr 21 18:34:50 Asgard kernel: [ 2374.842864]  disk 2, o:1, dev:sdf1
Apr 21 18:34:50 Asgard kernel: [ 2374.842868]  disk 3, o:1, dev:sdh1
Apr 21 18:34:50 Asgard kernel: [ 2374.842872]  disk 4, o:1, dev:sdi1
Apr 21 18:34:50 Asgard kernel: [ 2374.842934] md0: detected capacity change from 0 to 6001188667392
Apr 21 18:34:50 Asgard kernel: [ 2374.843215] md: resync of RAID array md0
Apr 21 18:34:50 Asgard kernel: [ 2374.843220] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Apr 21 18:34:50 Asgard kernel: [ 2374.843225] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Apr 21 18:34:50 Asgard kernel: [ 2374.843238] md: using 128k window, over a total of 1953511936k.
Apr 21 18:34:50 Asgard kernel: [ 2374.841492] md/raid:md0: not clean -- starting background reconstruction
Apr 21 18:34:50 Asgard kernel: [ 2374.841526] md/raid:md0: device sdi1 operational as raid disk 4
Apr 21 18:34:50 Asgard kernel: [ 2374.841533] md/raid:md0: device sdh1 operational as raid disk 3
Apr 21 18:34:50 Asgard kernel: [ 2374.841539] md/raid:md0: device sdc1 operational as raid disk 1
Apr 21 18:34:50 Asgard kernel: [ 2374.841544] md/raid:md0: device sdf1 operational as raid disk 2
Apr 21 18:34:50 Asgard kernel: [ 2374.841549] md/raid:md0: device sda1 operational as raid disk 0
Apr 21 18:34:50 Asgard kernel: [ 2374.842777] md/raid:md0: allocated 5334kB
Apr 21 18:34:50 Asgard kernel: [ 2374.842842] md/raid:md0: raid level 6 active with 5 out of 5 devices, algorithm 2
Apr 21 18:34:50 Asgard kernel: [ 2374.842847] RAID conf printout:
Apr 21 18:34:50 Asgard kernel: [ 2374.842851]  --- level:6 rd:5 wd:5
Apr 21 18:34:50 Asgard kernel: [ 2374.842856]  disk 0, o:1, dev:sda1
Apr 21 18:34:50 Asgard kernel: [ 2374.842860]  disk 1, o:1, dev:sdc1
Apr 21 18:34:50 Asgard kernel: [ 2374.842864]  disk 2, o:1, dev:sdf1
Apr 21 18:34:50 Asgard kernel: [ 2374.842868]  disk 3, o:1, dev:sdh1
Apr 21 18:34:50 Asgard kernel: [ 2374.842872]  disk 4, o:1, dev:sdi1
Apr 21 18:34:50 Asgard kernel: [ 2374.842934] md0: detected capacity change from 0 to 6001188667392
Apr 21 18:34:50 Asgard kernel: [ 2374.843215] md: resync of RAID array md0
Apr 21 18:34:50 Asgard kernel: [ 2374.843220] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Apr 21 18:34:50 Asgard kernel: [ 2374.843225] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Apr 21 18:34:50 Asgard kernel: [ 2374.843238] md: using 128k window, over a total of 1953511936k.
Apr 21 18:34:50 Asgard kernel: [ 2374.871632]  md0: unknown partition table
Apr 21 18:34:50 Asgard kernel: [ 2374.871632]  md0: unknown partition table
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildFinished event detected on md device /dev/md0
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildFinished event detected on md device /dev/md0
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildStarted event detected on md device /dev/md0
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildStarted event detected on md device /dev/md0

```

---

### Post by rubylaser on 2012-04-21
> **rcastberg said:**
> Got hold of pci sata controller today.

I rezeroed the drives and set up partitioning again (As i have all data backed up)

but when i create the array (Disk sda = 5YD24GMK): 
```
mdadm --create --verbose /dev/md0 --level=6 --raid-devices=5 /dev/sd[aihcf]1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 1953511936K
mdadm: Defaulting to version 1.2 metadata
mdadm: A**DD_NEW_DISK for /dev/sda1 failed: Device or resource busy**

```

Although the array goes on to  resync (with sda1 in the group)

Syslog from point when the partition was created.
```
Apr 21 18:34:50 Asgard kernel: [ 2374.434486] scsi_verify_blk_ioctl: 402 callbacks suppressed
Apr 21 18:34:50 Asgard kernel: [ 2374.434494] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434501] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434934] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434940] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435244] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435249] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435655] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435660] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434486] scsi_verify_blk_ioctl: 402 callbacks suppressed
Apr 21 18:34:50 Asgard kernel: [ 2374.434494] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434501] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434934] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.434940] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435244] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435249] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435655] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.435660] mdadm: sending ioctl 1261 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447142] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447151] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447142] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.447151] mdadm: sending ioctl 800c0910 to a partition!
Apr 21 18:34:50 Asgard kernel: [ 2374.629142] md: could not open unknown-block(8,1).
Apr 21 18:34:50 Asgard kernel: [ 2374.629231] md: md_import_device returned -16
Apr 21 18:34:50 Asgard kernel: [ 2374.629142] md: could not open unknown-block(8,1).
Apr 21 18:34:50 Asgard kernel: [ 2374.629231] md: md_import_device returned -16
Apr 21 18:34:50 Asgard kernel: [ 2374.654839] md: bind<sda1>
Apr 21 18:34:50 Asgard kernel: [ 2374.654839] md: bind<sda1>
Apr 21 18:34:50 Asgard kernel: [ 2374.696994] md: bind<sdf1>
Apr 21 18:34:50 Asgard kernel: [ 2374.696994] md: bind<sdf1>
Apr 21 18:34:50 Asgard kernel: [ 2374.718340] md: bind<sdc1>
Apr 21 18:34:50 Asgard kernel: [ 2374.718340] md: bind<sdc1>
Apr 21 18:34:50 Asgard kernel: [ 2374.751766] md: bind<sdh1>
Apr 21 18:34:50 Asgard kernel: [ 2374.751766] md: bind<sdh1>
Apr 21 18:34:50 Asgard kernel: [ 2374.801788] md: bind<sdi1>
Apr 21 18:34:50 Asgard kernel: [ 2374.801788] md: bind<sdi1>
Apr 21 18:34:50 Asgard kernel: [ 2374.841492] md/raid:md0: not clean -- starting background reconstruction
Apr 21 18:34:50 Asgard kernel: [ 2374.841526] md/raid:md0: device sdi1 operational as raid disk 4
Apr 21 18:34:50 Asgard kernel: [ 2374.841533] md/raid:md0: device sdh1 operational as raid disk 3
Apr 21 18:34:50 Asgard kernel: [ 2374.841539] md/raid:md0: device sdc1 operational as raid disk 1
Apr 21 18:34:50 Asgard kernel: [ 2374.841544] md/raid:md0: device sdf1 operational as raid disk 2
Apr 21 18:34:50 Asgard kernel: [ 2374.841549] md/raid:md0: device sda1 operational as raid disk 0
Apr 21 18:34:50 Asgard kernel: [ 2374.842777] md/raid:md0: allocated 5334kB
Apr 21 18:34:50 Asgard kernel: [ 2374.842842] md/raid:md0: raid level 6 active with 5 out of 5 devices, algorithm 2
Apr 21 18:34:50 Asgard kernel: [ 2374.842847] RAID conf printout:
Apr 21 18:34:50 Asgard kernel: [ 2374.842851]  --- level:6 rd:5 wd:5
Apr 21 18:34:50 Asgard kernel: [ 2374.842856]  disk 0, o:1, dev:sda1
Apr 21 18:34:50 Asgard kernel: [ 2374.842860]  disk 1, o:1, dev:sdc1
Apr 21 18:34:50 Asgard kernel: [ 2374.842864]  disk 2, o:1, dev:sdf1
Apr 21 18:34:50 Asgard kernel: [ 2374.842868]  disk 3, o:1, dev:sdh1
Apr 21 18:34:50 Asgard kernel: [ 2374.842872]  disk 4, o:1, dev:sdi1
Apr 21 18:34:50 Asgard kernel: [ 2374.842934] md0: detected capacity change from 0 to 6001188667392
Apr 21 18:34:50 Asgard kernel: [ 2374.843215] md: resync of RAID array md0
Apr 21 18:34:50 Asgard kernel: [ 2374.843220] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Apr 21 18:34:50 Asgard kernel: [ 2374.843225] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Apr 21 18:34:50 Asgard kernel: [ 2374.843238] md: using 128k window, over a total of 1953511936k.
Apr 21 18:34:50 Asgard kernel: [ 2374.841492] md/raid:md0: not clean -- starting background reconstruction
Apr 21 18:34:50 Asgard kernel: [ 2374.841526] md/raid:md0: device sdi1 operational as raid disk 4
Apr 21 18:34:50 Asgard kernel: [ 2374.841533] md/raid:md0: device sdh1 operational as raid disk 3
Apr 21 18:34:50 Asgard kernel: [ 2374.841539] md/raid:md0: device sdc1 operational as raid disk 1
Apr 21 18:34:50 Asgard kernel: [ 2374.841544] md/raid:md0: device sdf1 operational as raid disk 2
Apr 21 18:34:50 Asgard kernel: [ 2374.841549] md/raid:md0: device sda1 operational as raid disk 0
Apr 21 18:34:50 Asgard kernel: [ 2374.842777] md/raid:md0: allocated 5334kB
Apr 21 18:34:50 Asgard kernel: [ 2374.842842] md/raid:md0: raid level 6 active with 5 out of 5 devices, algorithm 2
Apr 21 18:34:50 Asgard kernel: [ 2374.842847] RAID conf printout:
Apr 21 18:34:50 Asgard kernel: [ 2374.842851]  --- level:6 rd:5 wd:5
Apr 21 18:34:50 Asgard kernel: [ 2374.842856]  disk 0, o:1, dev:sda1
Apr 21 18:34:50 Asgard kernel: [ 2374.842860]  disk 1, o:1, dev:sdc1
Apr 21 18:34:50 Asgard kernel: [ 2374.842864]  disk 2, o:1, dev:sdf1
Apr 21 18:34:50 Asgard kernel: [ 2374.842868]  disk 3, o:1, dev:sdh1
Apr 21 18:34:50 Asgard kernel: [ 2374.842872]  disk 4, o:1, dev:sdi1
Apr 21 18:34:50 Asgard kernel: [ 2374.842934] md0: detected capacity change from 0 to 6001188667392
Apr 21 18:34:50 Asgard kernel: [ 2374.843215] md: resync of RAID array md0
Apr 21 18:34:50 Asgard kernel: [ 2374.843220] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Apr 21 18:34:50 Asgard kernel: [ 2374.843225] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Apr 21 18:34:50 Asgard kernel: [ 2374.843238] md: using 128k window, over a total of 1953511936k.
Apr 21 18:34:50 Asgard kernel: [ 2374.871632]  md0: unknown partition table
Apr 21 18:34:50 Asgard kernel: [ 2374.871632]  md0: unknown partition table
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildFinished event detected on md device /dev/md0
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildFinished event detected on md device /dev/md0
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildStarted event detected on md device /dev/md0
Apr 21 18:34:50 Asgard mdadm[1835]: RebuildStarted event detected on md device /dev/md0

```

Does it finish resyncing correctly, and survive a reboot (not rebuilding after reboot)?

---

### Post by rcastberg on 2012-04-23
Sorry took a while to answer, had to let it finish the filesystem initialization.
And no it didn't trigger a resync after reboot.

---

