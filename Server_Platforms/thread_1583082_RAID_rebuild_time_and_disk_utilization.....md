---
title: "RAID rebuild time and disk utilization...."
date: 2010-09-27
forum: Server Platforms
---

### Post by bishoptf on 2010-09-27
So I'm in the process of building and testing a raid setup and it appeared to take along time to build I came across some settings for setting the min amount of time and that helped but it appears that one of the disks is struggling  (100 utilization) vs the other one...I was wondering if anyone else has seen this and if so, is their a solution for it...my 2 disks are 1 Samsung F3 1tb /dev/sdb and 1 Seagate 7200.12 1Tb /dev/sdc...smartctl looks good on both..../dev/sdb is the one that is struggling...see below...Thanks :)


```
sar -dbpqu -P ALL 60 1

10:09:41 AM       CPU     %user     %nice   %system   %iowait    %steal     %idle
10:10:41 AM       all      0.03      0.00      1.11      0.00      0.00     98.86
10:10:41 AM         0      0.00      0.00      0.00      0.00      0.00    100.00
10:10:41 AM         1      0.10      0.00      1.25      0.00      0.00     98.65
10:10:41 AM         2      0.00      0.00      3.18      0.02      0.00     96.80
10:10:41 AM         3      0.00      0.00      0.02      0.00      0.00     99.98

10:09:41 AM       tps      rtps      wtps   bread/s   bwrtn/s
10:10:41 AM    838.27    836.41      1.87 107059.98     32.54

10:09:41 AM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
10:10:41 AM       sda      0.93      0.00     16.27     17.43      0.00      2.12      0.29      0.03
10:10:41 AM      sda1      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
10:10:41 AM      sda2      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
10:10:41 AM      sda3      0.93      0.00     16.27     17.43      0.00      2.12      0.29      0.03
10:10:41 AM       sdb    209.10  26764.99      0.00    128.00     30.90    148.02      4.78    100.02
10:10:41 AM      sdb1    209.10  26764.99      0.00    128.00     30.90    148.02      4.78    100.02
10:10:41 AM       sdc    209.10  26764.99      0.00    128.00      0.41      1.94      0.60     12.57
10:10:41 AM      sdc1    209.10  26764.99      0.00    128.00      0.41      1.94      0.60     12.57
10:10:41 AM       md0      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00

10:09:41 AM   runq-sz  plist-sz   ldavg-1   ldavg-5  ldavg-15
10:10:41 AM         0       167      1.02      1.03      1.00
```

---

