---
title: "Replace raid5 disk"
date: 2014-09-08
forum: Server Platforms
---

### Post by guillaume8 on 2014-09-08
Hello all,

I have a problem with one of my hard drive and I can't figure it out.
As I have no experience with hard drive I list everything I did until now, 
if you can find out how I can fix my problem or if I did something wrong it will be awesome !!

The following event may not be totaly acurate, I write as I can recall them.


At the office we have an Ubuntu server (10.04 server) with an SVN, suddently, I couldn't commit anything as the SVN had a problem to write
on the media "/media/md3/SVN..." . After a little research I found that their was a problem with hard drives,
so I decided to reboot the server.

But the server did not want to reboot corectly : "The disk drive /media/md3 is not ready yet or not present". 
As the server rebooted one of the hard drive made horrible sounds. 
So I assumed that there was an hardware problem with one of our hard drive.

I looked on internet and found that mdX drive are raid disk. 
The "/proc/mdstat" give me the folowing results :
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : inactive sdb4[1](S) sdc4[2](S)
      XXXXX blocks
       
md0 : active raid1 sdb1[1] sdc1[0]
      9767424 blocks [2/2] [UU]
      
md2 : active raid1 sdb3[1] sdc3[0]
      9767424 blocks [2/2] [UU]
      
md1 : active raid1 sdb2[1] sdc2[0]
      3903680 blocks [2/2] [UU]
      
unused devices: <none>

```    
So, if I understant this file correclty there are 4 partitions. 3  with raid1 which seems fine
and an inactive one.
By opening the server I found only 3 disks so I assume that only one disk (sda) is missing.

I saw that 
/dev/md0 is for /
/dev/md1 is for the swap
/dev/md1 is for /home
/dev/md3 is for other stuff (SVN ...)

I check the raid confiration by reading "/etc/mdadm/mdadm.conf"
```
...
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=49735139:366257fa:a5779236:921be48a
   spares=1
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=a2c293ad:48665869:d6cbf604:0332693a
   spares=1
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=babfb377:80fbc55e:b4941712:9acab322
   spares=1
ARRAY /dev/md3 level=raid5 num-devices=3 UUID=417439cd:4ae223bb:160a0374:db61e1ab
...

```

*I know that this file may not correspond to reality because it as to be generated but it seems logical so I continue as it was the good configuration.*

So, now that I have the server's raid configuration, I need to figure out which disk broke.
So I plug/unplug disks to test wich one is good.
*At this point i forget which cable was connected to the different Sata ports, I hope it is not important ...*

Then I plug a new hard drive (same brand aproximatively same characteristics but 1TB instead of 500GB).
With a liveCD and Gparted I partition the new hard drive. I chose the same size for the three first partition (for raid1)
and I let the remaining space for the last partition.
I saw that the 2 other have a 'msdos' partition table and a ~1MB unallocated space at the end of the hard drive.
So I did the same configuration with my new disk. I also chosed the same flags.
The only things different is that the two other disk have no file system on their sdx3 partition and with Gparted I am forced to chose something,
so I selected "ext3".

sda
[ATTACH=CONFIG]256248[/ATTACH]

sdb (new disk)
[ATTACH=CONFIG]256249[/ATTACH]

Now that everything is prepared I reboot the server and nothing changed. 
So I manually add the 3 first partitions :
    ```
mdadm --manage /dev/mdX --add /dev/sdbY 
```
The partition are added as spare disks ... cool !

```
$ : cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : inactive sda4[1](S) sdc4[2](S)
      XXXXX blocks
       
md0 : active raid1 sda1[1] sdc1[0] sdb1[2](S)
      9767424 blocks [2/2] [UU]
      
md2 : active raid1 sda3[1] sdc3[0] sdb3[2](S)
      9767424 blocks [2/2] [UU]
      
md1 : active raid1 sda2[1] sdc2[0] sdb2[2](S)
      3903680 blocks [2/2] [UU]
      
unu
```sed devices: <none>

For the raid5 disk I follow instructions here :
[http://globalblindspot.blogspot.fr/2011/06/how-to-replace-failed-disk-of-raid-5.html](http://globalblindspot.blogspot.fr/2011/06/how-to-replace-failed-disk-of-raid-5.html)
Everything seems fine and the recovery began
```
$ : cat /proc/mdstat
...          
md3 : active raid5 sda4[1] sdb4[3] sdc4[2]
      929890176 blocks level 5, 64k chunk, algorithm 2 [3/2] [_UU]
      [>....................]  recovery =  0.8% (3802496/464945088) finish=93.6min speed=82056K/sec
...

```    
But merely at the end the recovery crashed.

I read somewhere that the different raid5 algorithme order data in different ways. 
As the initialy missing 'sda' disk re-appers as 'sdb' it may be the cause of my probleme.
*Remenber, I played with cables and I may have inverted the two first disks*

So I change the two first disks. Unfortunately, with this configuration 
the server cannot boot and stop at "Verifying DMI Pool Data ....".

I thought that the computer cannot boot because the partition with boot
information (/dev/md0) is empty on the new disk as it is only a spare disque 
in a raid1 configuration.
So I plug back the disks as they were before and I set faulty the first 
partition of the third disk (/dev/sdc1), so everything from the third disk was
copied on the new one.

I inverte again the two first disk and ... the boot is stuck again at 
"Verifying DMI Pool Data ....".




I do not know waht I can do next, If you have any idea how I can make the
server boot again properly it will be great.

---

### Post by nerdtron on 2014-09-08
Might have better chance of answering if an admin moves this to Server Platforms.

---

### Post by guillaume8 on 2014-09-09
So I posted in the wrong place ...

If nobody moves my thread can I close it and open it again in the good subforum ?

---

### Post by nerdtron on 2014-09-09
> As the initialy missing 'sda' disk re-appers as 'sdb' it may be the cause of my probleme.
*Remenber, I played with cables and I may have inverted the two first disks*

Bad...really bad...

> 
I inverte again the two first disk and ... the boot is stuck again at 
"Verifying DMI Pool Data ....".

Seems like problems arise the more you fiddle with it. You can't even boot on the OS, you can't do anything.

Do you have any backups of the files from the server?

---

### Post by coffeecat on 2014-09-09
> **guillaume8 said:**
> So I posted in the wrong place ...

If nobody moves my thread can I close it and open it again in the good subforum ?

I've moved it to ***Server Platforms**.*

If you ever want a thread moving, it's quite OK to send a request to the staff area by clicking on the "report post" button in your own post. It'll be acted on quicker than hoping a member of forum staff happens to notice the need. Don't worry about using the report button - we use it for more than just problematic posts here. It's an effective and quick way of sending a message/request to forum staff.

---

### Post by guillaume8 on 2014-09-10
> **nerdtron said:**
> Seems like problems arise the more you fiddle with it. You can't even boot on the OS, you can't do anything.

Do you have any backups of the files from the server?

No, We only have old saves.


Do you know how disk are named ? Are they named according to the port they are pluged in ?
For exemple, the disk pluged in the port0 will be sda, the one in the port1 sdb ...
If yes, I should be abble to find how the diks were pluged before the incident.


Because the new disk seems to be at fault is there a way to make the computer boot on an other disk even if it's not the first one (sdb) ?


PS: Thanks coffeecat for the explanation

---

### Post by nerdtron on 2014-09-11
> Do you know how disk are named ? Are they named according to the port they are pluged in ?
For exemple, the disk pluged in the port0 will be sda, the one in the port1 sdb ...

I think this is correct. but...

> If yes, I should be abble to find how the diks were pluged before the incident

You said you changed the disk port order before you build the raid? Also, Verifying DMI Pool  means no data is detected on this, even the boot loader can be found. So I guess when you build up the raid using the wrong configuration you messed with the order of parity algorithm of raid 5.

I'm sorry but I can't offer any more solution in this situation.

---

### Post by guillaume8 on 2014-09-12
Thanks for your replies !

Is the "boot loader" something for each raid disk or is it for the OS ?
If it is for the OS it should be place on the raid disk marked as "boot" with gparted, isn't it ?

By rebuilding the raid5 disk with a wrong order it may have mix the data in the wrong order like you said.

I do not know how the rebuilding of a raid5 works but it should only modified the new disk.
If I set it faulty then plug it back in the good order the two others should be intact, isn't it ?

---

### Post by rubylaser on 2014-09-12
Putting a filesystem on each partition and then causing a sync by adding the disk was not a good idea.  It would have been better to remove the disk (if it was in fact failing) with mdadm and then replace the failed disk with the new one.  What you did very likely overwrote any data on that partition.  Instead of trying to get the OS to boot, I would start by trying to recover your data.  I would boot a live Ubuntu cd, run apt-get install mdadm. And then try to use mdadm to examine the metadata info on each disk like this. 

```

sudo -i
apt-get update && apt-get install mdadm smartmontools -y

```

```

mdadm --examine /dev/sd[ab]1
mdadm --examine /dev/sd[ab]2
mdadm --examine /dev/sd[ab]3
mdadm --examine /dev/sd[ab]4

```

Also, I would check the SMART data on each disk.
```

smartctl -a /dev/sda
smartctl -a /dev/sdb

```

Please run these and report back.

---

### Post by guillaume8 on 2014-09-15
Hi,

Here the results :

```
root@ubuntu:~# mdadm --examine /dev/sd[ab]1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 49735139:366257fa:a5779236:921be48a
  Creation Time : Wed Oct 22 15:04:45 2008
     Raid Level : raid1
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
     Array Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0


    Update Time : Mon Sep 15 09:01:57 2014
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : fe4c5064 - correct
         Events : 423262




      Number   Major   Minor   RaidDevice State
this     1       8        1        1      active sync   /dev/sda1


   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8        1        1      active sync   /dev/sda1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 49735139:366257fa:a5779236:921be48a
  Creation Time : Wed Oct 22 15:04:45 2008
     Raid Level : raid1
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
     Array Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0


    Update Time : Mon Sep 15 09:01:57 2014
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : fe45db14 - correct
         Events : 423263




      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1


   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8        1        1      active sync   /dev/sda1

root@ubuntu:~# mdadm --examine /dev/sd[ab]2
/dev/sda2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a2c293ad:48665869:d6cbf604:0332693a
  Creation Time : Wed Oct 22 15:05:33 2008
     Raid Level : raid1
  Used Dev Size : 3903680 (3.72 GiB 4.00 GB)
     Array Size : 3903680 (3.72 GiB 4.00 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 126


    Update Time : Thu Sep  4 15:44:31 2014
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : b9604c6 - correct
         Events : 1824




      Number   Major   Minor   RaidDevice State
this     1       8        2        1      active sync   /dev/sda2


   0     0       8       34        0      active sync
   1     1       8        2        1      active sync   /dev/sda2
   2     2       8       18        2      spare   /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a2c293ad:48665869:d6cbf604:0332693a
  Creation Time : Wed Oct 22 15:05:33 2008
     Raid Level : raid1
  Used Dev Size : 3903680 (3.72 GiB 4.00 GB)
     Array Size : 3903680 (3.72 GiB 4.00 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 126


    Update Time : Thu Sep  4 15:43:01 2014
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : b960478 - correct
         Events : 1824




      Number   Major   Minor   RaidDevice State
this     2       8       18        2      spare   /dev/sdb2


   0     0       8       34        0      active sync
   1     1       8        2        1      active sync   /dev/sda2
   2     2       8       18        2      spare   /dev/sdb2

root@ubuntu:~# mdadm --examine /dev/sd[ab]3
/dev/sda3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : babfb377:80fbc55e:b4941712:9acab322
  Creation Time : Wed Oct 22 15:05:44 2008
     Raid Level : raid1
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
     Array Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 2


    Update Time : Thu Sep  4 16:00:03 2014
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : d1e5c3ae - correct
         Events : 109694




      Number   Major   Minor   RaidDevice State
this     1       8        3        1      active sync   /dev/sda3


   0     0       8       35        0      active sync
   1     1       8        3        1      active sync   /dev/sda3
   2     2       8       19        2      spare   /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : babfb377:80fbc55e:b4941712:9acab322
  Creation Time : Wed Oct 22 15:05:44 2008
     Raid Level : raid1
  Used Dev Size : 9767424 (9.31 GiB 10.00 GB)
     Array Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 2


    Update Time : Thu Sep  4 16:00:03 2014
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : d1e5c3ba - correct
         Events : 109694




      Number   Major   Minor   RaidDevice State
this     2       8       19        2      spare   /dev/sdb3


   0     0       8       35        0      active sync
   1     1       8        3        1      active sync   /dev/sda3
   2     2       8       19        2      spare   /dev/sdb3

root@ubuntu:~# mdadm --examine /dev/sd[ab]4
/dev/sda4:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 417439cd:4ae223bb:160a0374:db61e1ab
  Creation Time : Wed Oct 22 15:05:53 2008
     Raid Level : raid5
  Used Dev Size : 464945088 (443.41 GiB 476.10 GB)
     Array Size : 929890176 (886.81 GiB 952.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 3


    Update Time : Thu Sep  4 17:15:22 2014
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : dfc30c50 - correct
         Events : 724278


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     1       8        4        1      active sync   /dev/sda4


   0     0       0        0        0      removed
   1     1       8        4        1      active sync   /dev/sda4
   2     2       0        0        2      faulty removed
   3     3       8       20        3      spare   /dev/sdb4
/dev/sdb4:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 417439cd:4ae223bb:160a0374:db61e1ab
  Creation Time : Wed Oct 22 15:05:53 2008
     Raid Level : raid5
  Used Dev Size : 464945088 (443.41 GiB 476.10 GB)
     Array Size : 929890176 (886.81 GiB 952.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 3


    Update Time : Thu Sep  4 17:15:22 2014
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : dfc30c5e - correct
         Events : 724278


         Layout : left-symmetric
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     3       8       20        3      spare   /dev/sdb4


   0     0       0        0        0      removed
   1     1       8        4        1      active sync   /dev/sda4
   2     2       0        0        2      faulty removed
   3     3       8       20        3      spare   /dev/sdb4

```


```
root@ubuntu:~# smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500320AS
Serial Number:    5QM2ZL78
LU WWN Device Id: 5 000c50 011563ae4
Firmware Version: SD1A
User Capacity:    500,106,780,160 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Sep 15 09:46:59 2014 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  634) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 117) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103b)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   099   006    Pre-fail  Always       -       190665705
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       21
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   082   060   030    Pre-fail  Always       -       4468748299
  9 Power_On_Hours          0x0032   042   042   000    Old_age   Always       -       51414
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       73
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   094   000    Old_age   Always       -       36
189 High_Fly_Writes         0x003a   085   085   000    Old_age   Always       -       15
190 Airflow_Temperature_Cel 0x0022   064   053   045    Old_age   Always       -       36 (Min/Max 24/36)
194 Temperature_Celsius     0x0022   036   047   000    Old_age   Always       -       36 (0 17 0 0)
195 Hardware_ECC_Recovered  0x001a   035   021   000    Old_age   Always       -       190665705
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0


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


root@ubuntu:~# smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     ST1000DM003-1ER162
Serial Number:    Z4Y0GLDM
LU WWN Device Id: 5 000c50 0675d2291
Firmware Version: CC43
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   9
ATA Standard is:  Not recognized. Minor revision code: 0x001f
Local Time is:    Mon Sep 15 09:47:04 2014 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (   80) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 110) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x1085)    SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   100   006    Pre-fail  Always       -       69712880
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       16
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       743060
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       172
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       16
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   066   062   045    Old_age   Always       -       34 (Min/Max 24/34)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       47
194 Temperature_Celsius     0x0022   034   040   000    Old_age   Always       -       34 (0 20 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       187891934298282
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2284470464
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       34502039


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

### Post by Just1 on 2015-01-17
Hi all!
I am a new colleague of guillaume8. I don't want to bother in re-activating this topic, only giving more information that may help others about the data rescue, and trying to move a step ahead (_see the end of the post_).

(I tell you a bit of context to explain why I am so insistent.)
When I arrived at the company, I understood that the main -and only- server has crashed since 4 months, that the data on it were certainly gone, that the Subversion server are out of order and nobody work with version control any more, and that we lost some more services that are important for us: an internal wiki, a bug-tracker, and others.
I can't understand how we could work without a version control system in the today's world (we do some electronics and software development) so I wanted to rebuild a new server from the files contained in the working copies. Of course this assumes that we would lose all the history of all the development done to date. Well, I didn't have any other option...
But what to do with the wiki, the bug-tracker, ... ? That's where I wanted to go deeply in trying to rebuild the RAID-5 array (/dev/md3), even if it has "failed" before.

Of course I started with simple things :

```
cat /proc/mdstat
```
=> the md3 (RAID5) array is inactive

```
sudo mdadm --assemble
```
=> the RAID cannot be assembled (I don't remember the exact error)

```
sudo mdadm --assemble --run
```
=> even in degraded mode, the RAID cannot be assembled (I don't remember the exact error)

Seems to be bad.
A deeper examination showed me that we **lost an other drive**! (When guillaume8 manipulated the RAID, there were still 2 original disks running.) I didn't notice it while doing cat /proc/mdstat; this was my first time playing with RAID, blame on me. Unfortunately re-assembling a 3-disk RAID5 array with only 1 disk is impossible.
I was so desperate that I was ready to open the second failed disk to replace the heads with some from an other disk. But I did not want to proceed without knowing what data reside on the new disk -the fourth one, which aim to replace the first failing disk.

A this time I said to myself: I can't afford an other failure, I absolutely need to backup the two remaining disks before trying anything else! So I did. I took two HDD and executed some dd copies.
```
sudo dd if=/dev/sda of=/dev/sdb bs=512 conv=noerror,sync
```

**From that point, I only did my operations on the copied disks.**

guillaume8 may had inverted the cables while searching the first failing disk, and I thought like him that it was the original problem of the RAID rebuild failure. I also thought that the new (reconstructed) disk had been filled with the same data as an existing one, because of the cable inversion. That's why I did not pay attention to the new disk (the 4th one) partially rebuilt.
I read and read again the notes taken by guillaume8, read a lot from other websites and forums, read, read, and read more.

I took a paper and tried to trace [the job done by guillaume8 with the disks]("http://ubuntuforums.org/showthread.php?t=2243347&p=13117593#post13117593"):
1) Finding the RAID5 not working:
```
md3 : inactive sda4[1](S) sdc4[2](S)
```
2) Trying to rebuild it with an "added" disk:
```
md3 : active raid5 sda4[1] sdb4[3] sdc4[2]
```
So the new disk (/dev/sdb) took the "role" [3]. But apparently, it replaces the formerly role [0] which did no longer exist at step 1! So what did the RAID controller do? Did it reconstruct the data of the first failing disk? Probably, yes, because [it worked for others than us]("http://globalblindspot.blogspot.fr/2011/06/how-to-replace-failed-disk-of-raid-5.html"). But there were the problem of the cable inversion...

Well, let's assume that I have the original disk [1], the (partial) copy of the disk [0] (now [3]), and the [2]nd that had failed. So what? I must try to re-start the array!
```
=> "/dev/sdb4 has no superblock"
```
Ouch! I was sinking.

Some more inversion of the disk order showed me that the RAID role is kept, whatever the disk physical position. That was a very good point.
Very risky but last thing to try, because I was really out of ideas: re-write fresh superblocks to the disk [3]. That meant in fact recreating the RAID array, taking into account the original RAID options (given by *sudo mdadm --examine /dev/sda4*):
```
mdadm --verbose --create /dev/md3 --assume-clean --level=5 --chunk=64 --metadata=0.9 --layout=left-symmetric --raid-devices=3 /dev/sdb4 /dev/sda4 missing
```
I used the *--assume-clean* option to avoid any RAID rebuild, I did not want to lose more data!
I also wanted to use the *--array-size* option but it gave me an error: *mdadm: unrecognized option '--array-size=929890176'*.
[COLOR=#ff0000]And you know what? The array re-started! HURRAY![/COLOR]

```
mdadm: /dev/sdb4 appears to contain an ext2fs file system
    size=929890176K  mtime=Thu Jan 15 23:44:22 2015
mdadm: /dev/sdb4 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Thu Jan 15 19:14:12 2015
mdadm: /dev/sda4 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Thu Jan 15 19:14:12 2015
mdadm: size set to 464945088K
mdadm: largest drive (/dev/sdb4) exceed size (464945088K) by more than 1%
Continue creating array? y
mdadm: array /dev/md3 started.
```

Thanks to those who tried to help us ;-)

----------------------------------------

Ressources that helped me:

[http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5)
[http://fr.wikipedia.org/wiki/RAID_%28informatique%29#RAID_5_:_volume_agr.C3.A9g.C3.A9_par_bandes_.C3.A0_parit.C3.A9_r.C3.A9partie](http://fr.wikipedia.org/wiki/RAID_%28informatique%29#RAID_5_:_volume_agr.C3.A9g.C3.A9_par_bandes_.C3.A0_parit.C3.A9_r.C3.A9partie)

[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)
[https://raid.wiki.kernel.org/index.php/Mdstat](https://raid.wiki.kernel.org/index.php/Mdstat)

[https://raid.wiki.kernel.org/index.php/RAID_setup](https://raid.wiki.kernel.org/index.php/RAID_setup)
[https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)
[https://raid.wiki.kernel.org/index.php/RAID_superblock_formats](https://raid.wiki.kernel.org/index.php/RAID_superblock_formats)

[http://globalblindspot.blogspot.fr/2011/06/how-to-replace-failed-disk-of-raid-5.html](http://globalblindspot.blogspot.fr/2011/06/how-to-replace-failed-disk-of-raid-5.html)

[http://blog.al4.co.nz/2011/03/recovering-a-raid5-mdadm-array-with-two-failed-devices/](http://blog.al4.co.nz/2011/03/recovering-a-raid5-mdadm-array-with-two-failed-devices/)
[http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/](http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/)
[http://kevin.deldycke.com/2008/07/heroic-journey-to-raid-5-data-recovery/](http://kevin.deldycke.com/2008/07/heroic-journey-to-raid-5-data-recovery/)

[http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using/347786#347786](http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using/347786#347786)
[http://superuser.com/questions/516844/degraded-raid5-and-no-md-superblock-on-one-of-remaining-drive](http://superuser.com/questions/516844/degraded-raid5-and-no-md-superblock-on-one-of-remaining-drive)

----------------------------------------

Now that I have access to the data, I notice some corruption. This was predictable because the RAID rebuild was only partial.
Of course I plan to backup right now everything that I have recovered. But I have a question for RAID experts:
[U]
What I have:[/U]
- The disk [0] which contains corrupted data, from a partial RAID rebuild. The original disk [0] is definitely dead given the horrible noise it makes.
- The disk [1] which is the original one.
- The disk [2] which is not running any more (clicking noises).

_What I plan to do:_
I wish to open the disk [2] and replace the heads by the ones from a 4th identical disk.
I precise that even if there is no chance in getting more data back, I  will probably still try to do the heads replacement, just for fun :-)
*Ressources:*
[Seagate Barracuda 7200 10 head fault]("https://www.youtube.com/watch?v=0cV32qNyulw")
[How I replaced the headstack in a multiplatter Hard drive]("https://www.youtube.com/watch?v=PzRiKoD4nL8") ; [Hard Drive Head Replacement Tools for 50 Cents]("https://www.youtube.com/watch?v=uIPZtJyrVPw") ; [Click of Death - Head Stack Replacement / Swap How-to]("https://www.youtube.com/watch?v=DDWXZJPgbHM") ; [HddSurgery - How to replace heads on new 3.5" Seagate hard drives]("https://www.youtube.com/watch?v=x-8K0RdZNYA")
[How to Make a Clean Air Enclosure (for HDD repair etc)]("https://www.youtube.com/watch?v=xPEa0Wc9iUc")

_What I expect:_
If I successfully get access to the disk [2], I expect some file corruption again. It means that I will have an array with 2 disks containing corrupted data.
[B]
_What I don't know:_[/B]
Is there a way to get back "the best of both disks"? What can I expect if I use "mdadm --create" without the --assume-clean option?

Thanks for your help.

---

### Post by darkod on 2015-01-17
Be very careful with mdadm --create. As far as I know that is used only for creating new blank array. The --asume-clean is an exception from that, to force it to create new array without the initial sync assuming the data is clean. But if you run it without that option I think it will simply create new blank array, wiping all your data.

Since you have only one disk from three, I see it difficult to get the data back.

So is the array running now with two disks and one missing? Are the events counters equal on both disks (partitions members)? I think the examine option is giving the counters in its output.

---

### Post by Just1 on 2015-01-18
> **darkod said:**
> But if you run [mdadm --create] without [the --asume-clean] option I think it will simply create new blank array, wiping all your data.
Are you absolutely sure?

> **darkod said:**
> So is the array running now with two disks and one missing? Are the  events counters equal on both disks (partitions members)? I think the  examine option is giving the counters in its output.
Yes it is running. The disks are probably out of sync, so the event counters are probably not the same. I cannot check for the moment, I will post back the results tomorrow.

> **darkod said:**
> Since you have only one disk from three, I see it difficult to get the data back.
Actually no. For the moment I have 1 disk + 1 partially corrupted disk and I can access my data. I plan to have 1 disk + 2 partially corrupted disks.
The question is: Can my data be "less corrupted" by inserting a new corrupted disk? I mean, how does the RAID deal with 2 sources of corruption?
Second question: If I insert a new fresh disk and let the RAID rebuild it from the 2 others, do I have a chance do get more data back?

---

### Post by MAFoElffen on 2015-01-18
> **Just1 said:**
> Are you absolutely sure?
The code is kept at Linux kernel... For main comment in create.c
> 
    /*     * Create a new raid array.
     *
     * First check that necessary details are available
     * (i.e. level, raid-disks)
     *
     * Then check each disk to see what might be on it
     * and report anything interesting.
     *
     * If anything looks odd, and runstop not set,
     * abort.
     *
     * SET_ARRAY_INFO and ADD_NEW_DISK, and
     * if runstop==run, or raiddisks disks were used,
     * RUN_ARRAY
     */

It does have a check-to-error if the named array exists already... which can be overridden. So yes. (With a few exceptions.)

--create is not one of the options you want to recommend to someone, who is not familiar with mdadm, when they are trying to *recover* something.

---

### Post by Just1 on 2015-01-19
> **darkod said:**
> Are the events counters equal on both disks (partitions members)? I think the examine option is giving the counters in its output.
Bad news:
The events counters were both at 724278, but came down to both 6 after the array (re)creation.
Well, it is not really a bad news since the 2 disks were in sync BEFORE the creation, and they are still in sync AFTER.

Any idea of advanced recovery with 2 disks containing corrupted files? Assuming that the corruption is different over the 2 disks, I hope I could recover everything that is not corrupted from the "best" side. But it may involve some RAID reconstruction, and that's where I need a solid help.

---

### Post by rubylaser on 2015-01-19
> **Just1 said:**
> Bad news:
The events counters were both at 724278, but came down to both 6 after the array (re)creation.
Well, it is not really a bad news since the 2 disks were in sync BEFORE the creation, and they are still in sync AFTER.

Any idea of advanced recovery with 2 disks containing corrupted files? Assuming that the corruption is different over the 2 disks, I hope I could recover everything that is not corrupted from the "best" side. But it may involve some RAID reconstruction, and that's where I need a solid help.

Assuming corruption to be in a certain order doesn't make sense unless you have verified that this is the case.  With RAID5, because of striping, if you have corruption, the data is corrupt period, because it is striped across all disks in the RAID set vs. a RAID1 where it is mirrored and you can end up with "sides" in the case of a kicked out disk.  The best thing to do would have been to use gddrescue at the beginning to try to salvage as much data off each disk to new disks (you can take multiple attempts at the recovery this way), so that you could do your re-assembly without working on the original disks.  Unfortunately, what data you have is probably all you are going to get because you have done so many things with the array.

---

### Post by darkod on 2015-01-19
rubylaser is much bigger expert for raid than me, so I wouldn't have anything to add.

One suggestion would have been to simply add new member disk (partition) to the array you have assembled with --assume-clean and just let it sync. That way you get a working raid5 array. Of course that means the data that is readable right now, is all you will get. Further more it's probably bad idea to leave the semi-corrupt disk part of the array. So I guess best is to copy the data you saved off, create new blank array with disks you can depend on, and put the data back.

If you feel like playing, one idea that popped into my mind is to separate --create --assume-clean with the good disk and each of the semi-corrupt ones (assuming you can get the other one working with changing the head etc). Leaving the third member as missing. That should show you the data that the combination good disk + semi corrupt can recover for you. Doing it twice for each different semi corrupt disk might allow you to recover different files, and maximize recovery...

Then you can combine the two sets later to get the full set.

Assembling with both semi corrupt disks at once is probably worthless as far as I see it. The above suggestion for two separate assembliesmight help a bit, in theory.

---

### Post by Just1 on 2015-01-20
> **rubylaser said:**
> The best thing to do would have been to use gddrescue at the beginning to try to salvage as much data off each disk to new disks.
Rubylaser, I must say that I don't understand your point with gddrescue. The original "failing" disk drives both have hardware problems and cannot be read back **at all** (they are even not seen by the BIOS).
I have 1 original disk out of 3 that is running. I also have a disk that was the result of the RAID array reconstruction when only 1 drive had failed (I was not part of the company at that time), but the process had stopped before the end. Now I have a dd copy of each of those 2 disks, but since the first is in good health, and the second has never contain the data that I am trying to get back, in my opinion gddrescue would not give me more result than dd.

I take this opportunity to ask a conceptual RAID5 question:
When a drive has failed, the array continues to be accessible. **Are the "lost" files of the failing disk being reconstructed "on-the-fly" from the parity bits each time a user tries to access them?**

> **darkod said:**
> One suggestion would have been to simply add new member disk (partition)  to the array you have assembled with --assume-clean and just let it  sync. That way you get a working raid5 array.
That's what I just did yesterday.

> **darkod said:**
> Of course that means the  data that is readable right now is all you will get.
Sadly, yes.

> **darkod said:**
> Further more it's  probably bad idea to leave the semi-corrupt disk part of the array. So I  guess best is to copy the data you saved off, create new blank array  with disks you can depend on, and put the data back.
That's what is planned to be done. I don't want a production server to run such an array!

> **darkod said:**
> If you feel like playing, one idea that popped into my mind is to  separate --create --assume-clean with the good disk and each of the  semi-corrupt ones (assuming you can get the other one working with  changing the head etc). Leaving the third member as missing. That should  show you the data that the combination good disk + semi corrupt can  recover for you. Doing it twice for each different semi corrupt disk  might allow you to recover different files, and maximize recovery...
That's exactly what I thought about yesterday evening, and I'll probably give it a try. But for now I must do an other dd backup of the one and only original working drive: 1 backup, and 1 copy for each RAID recreation expirement. If I use the same first disk, the synchronization would be lost with the recreation of the array in the first try, and I fear that it gives me more data loss on the second try (or at least less chance in data recovery).

> **darkod said:**
> Then you can combine the two sets later to get the full set.
That's where I don't know how to proceed. This is a huge work if it must be done manually...

---

