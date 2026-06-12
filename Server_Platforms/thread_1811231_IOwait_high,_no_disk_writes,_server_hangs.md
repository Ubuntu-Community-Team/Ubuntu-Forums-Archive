---
title: "IOwait high, no disk writes, server hangs"
date: 2011-07-24
forum: Server Platforms
---

### Post by bottler on 2011-07-24
I run a website that a very steady flow of traffic and Im seeing recent issues that I just dont like.  

Server is 10.04.2 on a supermicro i7-950/6gb RAM with two 500gb Samsung F3 drives in a software RAID1 (1x5400, 1x7200) and for several weeks, its been running very well.  Recently, Im seeing the server hang for 5-20 seconds.  IOwait goes through the roof, nothing can write to the disk.  Apache logs stop, redis fails to rebuild caches, mysql errors and then it continues and moves back to normal operation

/ is ext4, the kernel was 2.6.32-server-x64 but since updating to 2.6.38-server-x64, the issue has dropped from maybe once per 10 minutes to once per 15 minutes. 

3 IOstat copy/pastes show this when it hangs. 

```
Total DISK READ: 0.00 B/s | Total DISK WRITE: 0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                                                                                                                                                                          
11811 be/4 redis       0.00 B/s    0.00 B/s  0.00 % 99.99 % redis-server /etc/redis/redis.conf
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init

Total DISK READ: 0.00 B/s | Total DISK WRITE: 0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                                                                                                                                                                          
  273 be/3 root        0.00 B/s    0.00 B/s  0.00 % 97.39 % [jbd2/md2-8]
13149 be/4 redis       0.00 B/s    0.00 B/s  0.00 % 97.34 % redis-server /etc/redis/redis.conf
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init

Total DISK READ: 0.00 B/s | Total DISK WRITE: 0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                                                                                                                                                                          
  260 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [md2_raid1]
 4053 be/4 mysql       0.00 B/s    0.00 B/s  0.00 % 99.99 % mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --~l/error.log --pid-file=/var/lib/mysql/server3.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]

```

No smart errors or smart diags show any issues with any of the disks and kernel.log shows near nothing other than a process hang, 120 seconds about 5 days ago.
Does anyone have any tips?  Im open to reverting the FS back to ext3 if I really have to.

---

### Post by Gyokuro on 2011-07-24
Hi,

can you please post a vmstat during this spikes? 

cat /proc/mdstat should be interesting too

but I think the biggest problem with your current setup is the use of two different drive speeds. As usual the write/read speed depends on the slowest drive. So I suggest that you maybe should replace your 5400 rpm drive with a second 7200 rpm drive and you should see a nice performance boost.

---

### Post by bottler on 2011-07-24
Ive never really had an issue with mixed speed spindles before, as much as I have tried to keep them in sync.  Ill see if I can get the host to replace one of them.  The site is 99.9% read only as its serving an user API out of redis, memory based.  Ill try anything you suggest apart from rm -fr / :)

it should be writing several kb per second, as the webserver is continually writing logs.

```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0  12972 1401100 151628 1081172    0    0     0     0 1604 3304  2  1 98  0
 0  0  12972 1401140 151628 1081212    0    0     4     0 1499 3404  1  1 98  0
 0  0  12972 1400552 151628 1081220    0    0     0    80 1354 2710  5  1 93  1
 1  0  12972 1400752 151628 1081224    0    0     0    12 1354 2903  1  1 99  0
 0  0  12972 1399724 151628 1081300    0    0     0    24 1381 3158  1  1 98  0
 0  0  12972 1400148 151628 1081304    0    0     0     0 1158 2378  1  1 99  0
 0  0  12972 1399912 151628 1081308    0    0     0     0 1532 3347  1  1 97  0
 0  0  12972 1399712 151628 1081312    0    0     0   128 1675 4167  1  1 97  1
 0  0  12972 1400048 151628 1081320    0    0     0    44 1512 3746  2  0 97  1
 1  0  12972 1399784 151628 1081328    0    0     0    44 1353 3010  1  1 97  1
 0  1  12972 1399784 151648 1081320    0    0     0   556 1334 2870  0  0 88 12
 1  1  12972 1327360 151652 1151516    0    0     0   804 1353 2864 11  2 75 12
 1  0  12972 1245876 151652 1230520    0    0     0   592 1432 3252 12  1 74 12
 1  0  12972 1164756 151652 1308392    0    0    16    36 1333 3581 13  1 86  0
 1  2  12972 1100296 151656 1354512    0    0    20 122896 1352 15412  9  1 84  6
 0  2  12972 1077836 151660 1354440    0    0     4 150156 1249 2797  1  1 85 12
 0  3  12972 1077828 151660 1354452    0    0     4     0 1296 2914  1  1 78 20
 0  3  12972 1077720 151660 1354460    0    0     0     0 1190 2659  1  0 74 26
 0  3  12972 1077720 151660 1354464    0    0     0     0  679  820  1  0 75 23
 0  3  12972 1077976 151660 1354464    0    0     0     0  607  556  0  0 75 25
 0  3  12972 1078248 151660 1354464    0    0     0     0  475  315  0  0 74 26
 0  3  12972 1078844 151660 1354464    0    0     0     0  492  312  0  0 75 25
 2  3  12972 1066876 151660 1354464    0    0     0     0  578  726  1  0 74 24
 0  3  12972 1060724 151660 1354464    0    0     0     0  580  557  1  1 72 26
 0  3  12972 1060784 151660 1354464    0    0     0     0  333  279  0  0 74 25
 2  3  12972 1063312 151660 1354472    0    0     0   100  893 2467  3  1 74 22
 0  3  12972 1064452 151660 1354492    0    0     0     0  458  407  0  0 74 26
 0  3  12972 1066428 151660 1354492    0    0     0     0  540  380  0  0 71 28
 0  3  12972 1067644 151660 1354492    0    0     0     0  466  431  0  0 71 29
 0  3  12972 1068932 151660 1354492    0    0     0     0  412  317  0  0 80 20
 0  3  12972 1071300 151660 1354492    0    0     0     0  376  313  0  0 74 25
 0  3  12972 1077720 151660 1354460    0    0     0     0 1190 2659  1  0 74 26
 0  3  12972 1077720 151660 1354464    0    0     0     0  679  820  1  0 75 23
 0  3  12972 1077976 151660 1354464    0    0     0     0  607  556  0  0 75 25
 0  3  12972 1078248 151660 1354464    0    0     0     0  475  315  0  0 74 26
 0  3  12972 1078844 151660 1354464    0    0     0     0  492  312  0  0 75 25
 2  3  12972 1066876 151660 1354464    0    0     0     0  578  726  1  0 74 24
 0  3  12972 1060724 151660 1354464    0    0     0     0  580  557  1  1 72 26
 0  3  12972 1060784 151660 1354464    0    0     0     0  333  279  0  0 74 25
 2  3  12972 1063312 151660 1354472    0    0     0   100  893 2467  3  1 74 22
 0  3  12972 1064452 151660 1354492    0    0     0     0  458  407  0  0 74 26
 0  3  12972 1066428 151660 1354492    0    0     0     0  540  380  0  0 71 28
 0  3  12972 1067644 151660 1354492    0    0     0     0  466  431  0  0 71 29
 0  3  12972 1068932 151660 1354492    0    0     0     0  412  317  0  0 80 20
 0  3  12972 1071300 151660 1354492    0    0     0     0  376  313  0  0 74 25
 0  3  12972 1072832 151660 1354492    0    0     0     0  481  326  0  0 72 28
 1  3  12972 1074924 151660 1354492    0    0     0     0  489  362  0  0 70 30
 0  3  12972 1076064 151660 1354492    0    0     0     0  457  339  0  0 82 18
 0  3  12972 1077220 151660 1354492    0    0     0     0  423  315  0  0 73 27
 0  3  12972 1079508 151660 1354492    0    0     0     0  465  348  0  0 72 27
 1  3  12972 1080584 151660 1354492    0    0     0     0  462  307  0  0 71 29
 1  3  12972 1081684 151660 1354492    0    0     0     0  492  321  0  0 82 18
 1  3  12972 1083028 151660 1354492    0    0     0     0  448  403  0  0 70 30
 1  3  12972 1083888 151660 1354492    0    0     0     0  392  303  0  0 75 24
 1  2  12972 1085316 151660 1354492    0    0     0     0  437  335  0  0 74 26
 1  2  12972 1086984 151660 1354492    0    0     0     0  465  348  0  0 77 22
 1  2  12972 1088320 151660 1354492    0    0     0     0  473  340  0  0 74 26
 1  2  12972 1089388 151660 1354492    0    0     0     0  412  325  0  0 76 24
 1  2  12972 1090496 151660 1354492    0    0     0     0  398  310  0  0 75 24
 1  2  12972 1091800 151660 1354492    0    0     0     0  431  336  0  0 75 25
 1  2  12972 1094668 151660 1354492    0    0     0     0  452  312  0  0 75 25
 1  2  12972 1096408 151660 1354492    0    0     0     0  502  322  0  0 75 25
 1  2  12972 1097364 151660 1354492    0    0     0     0  380  306  0  0 74 25
 1  1  12972 1100144 151660 1354492    0    0     0     0  427  261  0  0 90 10
 2  2  12972 1383392 151660 1081764    0    0     0   172 1005 3221  3  1 82 14
 0  0  12972 1383936 151660 1081492    0    0    56   328 2568 6640  8  2 73 18
 1  0  12972 1383920 151660 1081516    0    0    48    68 2275 6482  2  2 93  3
 6  0  12972 1363340 151660 1081572    0    0    16  1348 2465 7004 29  5 65  1
 8  0  12972 1365796 151660 1081612    0    0     4  2828 2373 5550 71  8 21  0
 6  0  12972 1374260 151660 1081544    0    0     0  4272 2411 4584 69  8 21  1
 1  1  12972 1386444 151660 1081664    0    0     0  1212 1871 4888 14  3 81  3
 1  1  12972 1385900 151664 1081652    0    0     0  2180 1703 4538 13  3 73 11
 0  1  12972 1397828 151668 1081636    0    0     4  1920 1538 3736  9  3 73 14
 0  1  12972 1397824 151668 1081692    0    0     0   976 1550 3533  1  1 84 14
 0  1  12972 1397948 151668 1081700    0    0     0   656 1458 3250  1  1 84 14
 0  1  12972 1397576 151668 1081704    0    0     0   504 1575 3625  1  0 90 10
 1  0  12972 1397452 151668 1081708    0    0     0   396 1403 3001  1  1 88 11
 0  0  12972 1397700 151668 1081720    0    0     4    52 1308 3118  2  1 97  1
 1  0  12972 1397700 151668 1081724    0    0     0     8 1284 2528  1  0 99  0
 0  0  12972 1397948 151668 1081732    0    0     0    44 1222 2489  1  1 97  1
 3  0  12972 1393384 151668 1081740    0    0     4    84 1207 3125  2  1 96  1

```It happens about 1/3 of the way down and then stops near the end, from a vmstat 1

```

root@server3:/root# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]
      1052160 blocks [2/2] [UU]
      
md2 : active raid1 sdb3[1] sda3[0]
      479178688 blocks [2/2] [UU]
      
unused devices: <none>

```also, this is the same for both disks

```

cat /sys/block/sda/queue/scheduler 
noop [deadline] cfq 

```and the disks

```

[    2.942401] ata1.00: ATA-8: SAMSUNG HD503HI, 1AJ10001, max UDMA/133
[    2.942475] ata2.00: ATA-8: SAMSUNG HD502HJ, 1AJ10001, max UDMA/133
[    2.962578] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD503HI  1AJ1 PQ: 0 ANSI: 5
[    2.962920] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5

```

---

### Post by Gyokuro on 2011-07-24
Don't be worry as it's not allowed to post fancy commands and it's not funny at all to do so.  I assume you have benchmarked your workload as you are using the deadline scheduler as otherwise cfq should do the job. 

try to change  /proc/sys/vm/dirty_background_ratio from 10 to 25 via

sudo sysctl vm.dirty_background_ratio=25 (which means do the flush after 25% system memory got used, delays the frequent flushes)

and you can change read ahead buffer for each disk from 128 to something like 512 (number will you find in 
/sys/block/sdX/queue/read_ahead_kb )

---

### Post by bottler on 2011-07-25
Ill give that a go, thanks.  Im using deadline as I was trying about anything and came across a post , Nov 2010, about ext4 filesystem bugs and a change of scheduler fix.  The benchmarking was done 2 months ago.  The same code was loading a dual core pentium 4 @1.8ghz to 1.4 and this box is a quad core/HT @ 3ghz and until a week ago was loading to 0.4

---

### Post by bottler on 2011-07-26
Back to cfq and disabled sata disk write cache and still nothing.

This keeps catching my attention

```

1  2  12972 1100296 151656 1354512    0    0    20 122896 1352 15412  9  1 84  6
 0  2  12972 1077836 151660 1354440    0    0     4 150156 1249 2797  1  1 85 12
 0  3  12972 1077828 151660 1354452    0    0     4     0 1296 2914  1  1 78 20
 0  3  12972 1077720 151660 1354460    0    0     0     0 1190 2659  1  0 74 26
 0  3  12972 1077720 151660 1354464    0    0     0     0  679  820  1  0 75 23
 0  3  12972 1077976 151660 1354464    0    0     0     0  607  556  0  0 75 25



```massive read/write followed by iowait death.  Any idea how to mitigate that a little more?

---

### Post by Gyokuro on 2011-07-27
I reread your posting and realized that you are using Lucid Lynx but with kernel 2.6.38 (is that a backport kernel from maverick)?. Is it possible that you test again with latest lucid server kernel (2.6.32-33-server) as I have a similiar system but with more RAM. Check also the disks whether they are ok (badblocks, smart) and 
cables.

Can you show us:

iostat -d 5

---

### Post by bottler on 2011-07-27
The same happened with 2.6.32-33 from lucid distro and yes, you are correct, thats a backprt from maverick to see if a newer kernel would fix it (it didnt).  We badblocks/smartd the disks are the disks showed no issue at all.  When I get home, Ill do the iostat, thanks :)

---

### Post by bottler on 2011-07-28
Its only hung once in the last 12 hours and I missed it :(  Ive enabled write caching on the disks and moved it back to deadline.  Still some issues there but it gives me time to look further.  Thanks for the help so far, Ill setup the iostat and watch it like a hawk tonight, hopefully not face planting my keyboard.

---

### Post by Gyokuro on 2011-07-28
No problem - a lot of ideas can by tried but in my experience such high IOWaits are results of hardware problems but maybe even your mysql and apache setup can be tweaked. Have fun with your keyboard :P

---

### Post by bottler on 2011-07-29
I missed its recent hangs.  Apache isnt running, Im using nginx and percona mysql 5.5

---

