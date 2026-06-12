---
title: "MDADM reshape really slow"
date: 2016-01-16
forum: Server Platforms
---

### Post by Okeur on 2016-01-16
Hello everyone,

_To sum up :_ My raid reshape from raid5 to raid6 with mdadm is really slow.

_The complete story :_ 5 days ago I realized that one of my disks from a raid 5 array was faulty. I removed it and replaced it with a brand new one. The rebuild took approximately 8 hours for a 12TB array at 120Mb/s, everything was fine. At the same time I bought another disk to update my raid 5 to raid 6. When the rebuild finished I started a reshape, but mdadm is reeeaaaally slow and I didn't figure out why that's why I'm here. The recently added drive (sdf) is writting fitfully. It writes for 0.5s, then stop, then writes for 0.5s, then stop etc. I read a lot on google about similar issue, and it seems that you can't  really do something about it. A lot of people ran into this problem and  eventually wait for the reshape to complete. But I can't stand there is  no exaplanation about this behaviour, and if unfortunately there is no  solution I would like to understand why it's happening, why my hdd are  not writing at full speed, why my CPU is not computing, why my RAM is  not busy...
Moreover, as time passed, the speed is decreasing (from 8Mb/s to 6Mb/s now), and the finish time is still about 8000min, I'm afraid that the speed will continue to decrease and the reshape will never finish...

```
root@debian-srv:/home/debian-srv/forum# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid6 sde[5] sdd1[4] sdb1[0] sdc1[3] sdf1[1]
      11720658432 blocks super 1.2 level 6, 512k chunk, algorithm 18 [5/4] [UUUU_]
      [===>.................]  reshape = 17.1% (671791104/3906886144) finish=8119.0min speed=6640K/sec

unused devices: <none>
```

_What I tried/checked :_

    
[LIST]
[*]echo 50000 > /proc/sys/dev/raid/speed_limit_min 
[*]echo 200000 > /proc/sys/dev/raid/speed_limit_max 
[*]echo 4096 > /sys/bloc/md0/md/stripe_cache_size 
[*]blockdev --setra 65535 /dev/md0 
[*]smartctl -a for all drives 
[*]smartctl -t short for all drives 
[*]smartctl -t conveyance for all drives 
[*]hdparm -tT for all drives 
[*]S.M.A.R.T test with the GUI for all drives -> everything is OK but the number of Raw_Read_Error_Rate is extremely high (details below) 
[*]This script ([http://ubuntuforums.org/showthread.php?t=1494846)]("http://ubuntuforums.org/showthread.php?t=1494846") 
[/LIST]
 
_What I didn't do:_

    
[LIST]
[*]Stop the reshape 
[*]Perform a hdd performance test with the gui (device busy) 
[*]Change SATA cable (I read I shouldn't stop the reshape) 
[/LIST]
 
_The technical part:_ Here is all the technical informations you may need.

Blockdev:

```
root@debian-srv:/home/debian-srv/forum# blockdev --getra /dev/md0
65536
root@debian-srv:/home/debian-srv/forum# blockdev --report /dev/sdb1
RO    RA   SSZ   BSZ  1er sect.          Taille   Périphérique
rw   256   512   512       2048   4000785964544   /dev/sdb1
root@debian-srv:/home/debian-srv/forum# blockdev --report /dev/sdc1
RO    RA   SSZ   BSZ  1er sect.          Taille   Périphérique
rw   256   512   512       2048   4000785964544   /dev/sdc1
root@debian-srv:/home/debian-srv/forum# blockdev --report /dev/sdd1
RO    RA   SSZ   BSZ  1er sect.          Taille   Périphérique
rw   256   512   512       2048   4000785964544   /dev/sdd1
root@debian-srv:/home/debian-srv/forum# blockdev --report /dev/sde1
RO    RA   SSZ   BSZ  1er sect.          Taille   Périphérique
rw   256   512   512       2048   4000785964544   /dev/sde1
root@debian-srv:/home/debian-srv/forum# blockdev --report /dev/sdf1
RO    RA   SSZ   BSZ  1er sect.          Taille   Périphérique
rw   256   512   512       2048   4000785964544   /dev/sdf1
```

Hdparm -tT:

```
root@debian-srv:/home/debian-srv/forum# hdparm -tT /dev/sdb1
/dev/sdb1:
 Timing cached reads:   2284 MB in  2.00 seconds = 1142.10 MB/sec
 Timing buffered disk reads: 416 MB in  3.00 seconds = 138.61 MB/sec

root@debian-srv:/home/debian-srv/forum# hdparm -tT /dev/sdc1
/dev/sdc1:
 Timing cached reads:   2318 MB in  2.00 seconds = 1158.86 MB/sec
 Timing buffered disk reads: 422 MB in  3.01 seconds = 140.31 MB/sec

root@debian-srv:/home/debian-srv/forum# hdparm -tT /dev/sdd1
/dev/sdd1:
 Timing cached reads:   2228 MB in  2.00 seconds = 1114.15 MB/sec
 Timing buffered disk reads: 406 MB in  3.02 seconds = 134.46 MB/sec

root@debian-srv:/home/debian-srv/forum# hdparm -tT /dev/sde1
/dev/sde1:
 Timing cached reads:   2238 MB in  2.00 seconds = 1117.17 MB/sec
 Timing buffered disk reads: 326 MB in  3.00 seconds = 108.53 MB/sec

root@debian-srv:/home/debian-srv/forum# hdparm -tT /dev/sdf1
/dev/sdf1:
 Timing cached reads:   2290 MB in  2.00 seconds = 1144.44 MB/sec
 Timing buffered disk reads: 240 MB in  3.01 seconds =  79.70 MB/sec
```

Dmesg:

```
[  568.432282] md/raid:md0: raid level 5 active with 3 out of 4 devices, algorithm 2
[  568.432287] RAID conf printout:
[  568.432291]  --- level:5 rd:4 wd:3
[  568.432295]  disk 0, o:1, dev:sdb1
[  568.432299]  disk 1, o:1, dev:sdf1
[  568.432303]  disk 2, o:1, dev:sdc1
[  568.432376] md0: detected capacity change from 0 to 12001954234368
[  568.437054]  md0: unknown partition table
[  942.055088]  sde: sde1
[  943.061844]  sde: sde1
[  954.016396]  sde: sde1
[  954.096613]  sde: sde1
[  954.339219]  sde:
[  956.007038]  sde:
[  956.897606]  sde:
[ 1084.011243]  sdd: sdd1
[ 1090.191545] md: bind<sdd1>
[ 1090.994243] RAID conf printout:
[ 1090.994254]  --- level:5 rd:4 wd:3
[ 1090.994261]  disk 0, o:1, dev:sdb1
[ 1090.994266]  disk 1, o:1, dev:sdf1
[ 1090.994270]  disk 2, o:1, dev:sdc1
[ 1090.994274]  disk 3, o:1, dev:sdd1
[ 1090.994533] md: recovery of RAID array md0
[ 1090.994562] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[ 1090.994567] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[ 1090.994583] md: using 128k window, over a total of 3906886144k.
[34484.341520] **perf interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 50000**
[37107.251863] md: md0: recovery done.
[37107.335417] RAID conf printout:
[37107.335425]  --- level:5 rd:4 wd:4
[37107.335431]  disk 0, o:1, dev:sdb1
[37107.335435]  disk 1, o:1, dev:sdf1
[37107.335439]  disk 2, o:1, dev:sdc1
[37107.335443]  disk 3, o:1, dev:sdd1
[39462.786459]  sde:
[39463.780907]  sde:
[39549.892683]  sde:
[39550.012102]  sde: sde1
[39550.457721]  sde: sde1
[39564.176984]  sde: sde1
[39583.200701]  sde: sde1
[39583.389783]  sde:
[39584.746260]  sde:
[39585.685914]  sde:
[39599.583805]  sde:
[39688.406254]  sde: sde1
[39689.551676]  sde: sde1
[39731.259332]  sde: sde1
[39731.292927] md: bind<sde>
[39732.115520] RAID conf printout:
[39732.115530]  --- level:5 rd:4 wd:4
[39732.115537]  disk 0, o:1, dev:sdb1
[39732.115542]  disk 1, o:1, dev:sdf1
[39732.115547]  disk 2, o:1, dev:sdc1
[39732.115551]  disk 3, o:1, dev:sdd1
[40062.994054] md/raid:md0: device sdd1 operational as raid disk 3
[40062.994065] md/raid:md0: device sdb1 operational as raid disk 0
[40062.994070] md/raid:md0: device sdc1 operational as raid disk 2
[40062.994075] md/raid:md0: device sdf1 operational as raid disk 1
[40062.994908] md/raid:md0: allocated 0kB
[40062.997006] md/raid:md0: raid level 6 active with 4 out of 5 devices, algorithm 18
[40062.997012] RAID conf printout:
[40062.997016]  --- level:6 rd:5 wd:4
[40062.997021]  disk 0, o:1, dev:sdb1
[40062.997025]  disk 1, o:1, dev:sdf1
[40062.997029]  disk 2, o:1, dev:sdc1
[40062.997033]  disk 3, o:1, dev:sdd1
[40063.938537] RAID conf printout:
[40063.938548]  --- level:6 rd:5 wd:4
[40063.938555]  disk 0, o:1, dev:sdb1
[40063.938560]  disk 1, o:1, dev:sdf1
[40063.938564]  disk 2, o:1, dev:sdc1
[40063.938568]  disk 3, o:1, dev:sdd1
[40063.938572]  disk 4, o:1, dev:sde
[40063.939415] md: reshape of RAID array md0
[40063.939420] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[40063.939425] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for reshape.
[40063.939444] md: using 128k window, over a total of 3906886144k.
```

In bold in dmesg I have : **perf interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 50000**

Iostat :

```
root@debian-srv:/home/debian-srv/forum# iostat -k 1 2
Linux 3.16.0-4-686-pae (debian-srv)     15/01/2016  _i686_  (1 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1,57    0,01   16,86   62,84    0,00   18,71

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sdc              97,10      7314,85      5138,04  955775539  671347807
sde              23,55         9,64      5140,51    1259429  671671477
sdb              97,44      7338,30      5138,04  958839263  671348371
sdd             105,10     10284,96      2169,18 1343857318  283429894
sdf             178,44      7311,34      5138,03  955317427  671347771
sda              34,57         9,86     15444,98    1288209 2018077322
md0               5,84        23,40         0,12    3057188      15908

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1,01    0,00   17,17   81,82    0,00    0,00

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sdc              56,57     14480,81      8277,27      14336       8194
sde              37,37         0,00      8277,27          0       8194
sdb              55,56     14480,81      8277,27      14336       8194
sdd              56,57     14480,81      8277,27      14336       8194
sdf              92,93     14480,81      8277,27      14336       8194
sda              37,37         0,00     16072,73          0      15912
md0               0,00         0,00         0,00          0          0

```
Mdadm :

```
root@debian-srv:/home/debian-srv/forum# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Dec 11 18:42:03 2014
     Raid Level : raid6
     Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 3906886144 (3725.90 GiB 4000.65 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Fri Jan 15 13:06:29 2016
          State : clean, degraded, reshaping 
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric-6
     Chunk Size : 512K

 Reshape Status : 17% complete
     New Layout : left-symmetric

           Name : debian-srv:0  (local to host debian-srv)
           UUID : f223d47d:882f9fdc:be7c8169:864feca4
         Events : 718531

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       81        1      active sync   /dev/sdf1
       3       8       33        2      active sync   /dev/sdc1
       4       8       49        3      active sync   /dev/sdd1
       5       8       64        4      spare rebuilding   /dev/sde
```

/proc/sys/dev/raid/speed_limit_* and /sys/block/md0/md/sync_speed_*:

```
root@debian-srv:/home/debian-srv/forum# cat /proc/sys/dev/raid/speed_limit_max
200000
root@debian-srv:/home/debian-srv/forum# cat /proc/sys/dev/raid/speed_limit_min
50000
root@debian-srv:/home/debian-srv/forum# cat /sys/block/md0/md/sync_speed_min
200000 (local)
root@debian-srv:/home/debian-srv/forum# cat /sys/block/md0/md/sync_speed_max
200000 (system)
```

Stripe_cache_size:

```
root@debian-srv:/home/debian-srv/forum# cat /sys/block/md0/md/stripe_cache_size
4096
```

Device queue:

```
root@debian-srv:/home/debian-srv/forum# cat /sys/block/sdb/device/queue_*
31
120000
simple

root@debian-srv:/home/debian-srv/forum# cat /sys/block/sdc/device/queue_*
31
120000
simple

root@debian-srv:/home/debian-srv/forum# cat /sys/block/sdd/device/queue_*
31
120000
simple

root@debian-srv:/home/debian-srv/forum# cat /sys/block/sde/device/queue_*
1
none

root@debian-srv:/home/debian-srv/forum# cat /sys/block/sdf/device/queue_*
1
none
```

Smartctl -a:

```
root@debian-srv:/home/debian-srv/forum# smartctl -a /dev/sdc
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Desktop HDD.15
Device Model:     ST4000DM000-1F2168
Serial Number:    Z301XYMT
LU WWN Device Id: 5 000c50 067546e57
Firmware Version: CC52
User Capacity:    4 000 787 030 016 bytes [4,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5900 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Jan 15 12:05:29 2016 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
...
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       214628264
  3 Spin_Up_Time            0x0003   091   091   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       15
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   071   060   030    Pre-fail  Always       -       13940971
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       8769
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       15
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 0
189 High_Fly_Writes         0x003a   097   097   000    Old_age   Always       -       3
190 Airflow_Temperature_Cel 0x0022   066   057   045    Old_age   Always       -       34 (Min/Max 31/36)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       6
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       18
194 Temperature_Celsius     0x0022   034   043   000    Old_age   Always       -       34 (0 15 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       8769h+51m+55.474s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       27801843844
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       68841105748

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      8768         -
# 2  Conveyance offline  Completed without error       00%      8728         -
# 3  Short offline       Completed without error       00%      8728         -
# 4  Short offline       Completed without error       00%         0         -
```

I ran smartctl -a on all devices but I can't show you the full results (body length limit). Ask for it if needed. Any help is appreciated !

Conclusion:
Any help is appreciated, I hope there is something to do about this.
Feel free to ask for any other information that may be relevant.

Thank you all !

Edit 18/01: Ok so of course since Murphy is my friend I had a power failure during the reshape. I succeeded in starting the reshape with the backup-file, but the reshape speed is stuck to 0ko/s. I'll open another thread on this problem.

---

### Post by Okeur on 2016-02-02
Ok guys, so for the next one facing the same problem here is the solution :

**There is no solution !**

That's all. It's slow, ok deal with it, that's all.

However, as I said at the end of my first post, I had a power failure during the reshape (Murrrphyyyyyyy), but thanks to that I can confirm that **it's safe to stop a reshape.**
If you encounter the same problem, you can stop the reshaping process and **check your cable**.
In fact, I read on another post that someone faced the same issue and it was a SATA cable, so I took the opportunity of the power failure to check my cables, and one of them was actually in bad shape (plastic part broken). I replaced it, restarted the reshape and it went quicker (around 40Mb/s)

---

