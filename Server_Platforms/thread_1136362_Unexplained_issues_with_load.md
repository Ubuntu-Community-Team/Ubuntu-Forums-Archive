---
title: "Unexplained issues with load"
date: 2009-04-24
forum: Server Platforms
---

### Post by Wonslung on 2009-04-24
hello.  I've been trying to help a friend of mine lower the load on his server.  It's a seedbox running torrentflux-b4rt and pure-ftpd.
Intel E8400 core2Duo 2 GB ram 100Mbit/sec internet.

The load on the server is unreal....i've done everything i know to do....set up shorewall firewall to block everything but the services listed above plus ssh....

The load is around 30 average but after watching the server for a week or so i'm convinced someone is causing this load intentionally somehow.  Every so often it'll drop down to normal levels, stay there for 2-3 hours then build back up.  I haven't been able to correlate this to any one user action.....I'm going crazy trying to figure out what's causing it...Top never shows anything using much of the cpu and the memory is under 40%

It seems it's spending a lot of time "waiting" according to top...what i'm looking for is some diagnostic tools to figure out what EXACTLY is causing the load....does anything like this exist?
i run a similar server on less hardware that never goes over 1.0 server load...i cannot figure it out for the life of me.


any help would be appreciated


oh, if it's important....i'm using Ubuntu server 8.10 NGINX 0.6.36 PHP 5.2.8 (patched for php-fmp)  mysql 5.0.67 pure-ftpd 1.0.21 and the current svn version of torrentflux-b4rt

this is a cap of top
```
top - 21:50:00 up 1 day, 18:18,  1 user,  load average: 33.23, 32.51, 34.46
Tasks: 178 total,   1 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us,  3.7%sy,  0.0%ni, 20.4%id, 64.6%wa,  0.2%hi,  2.2%si,  0.0%st
Mem:   2062388k total,  2012196k used,    50192k free,    14232k buffers
Swap:  2931852k total,     7192k used,  2924660k free,  1468952k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                           
 1265 www-data  20   0 31992 9976 2348 S    2  0.5   2:12.85 transmissioncli                                                                                                                                   
13301 www-data  20   0 37612  16m 2348 S    2  0.8  23:28.93 transmissioncli                                                                                                                                   
17503 www-data  20   0 16516 3516 2160 S    2  0.2   0:28.74 transmissioncli                                                                                                                                   
27707 www-data  20   0 27404 6340 2344 S    2  0.3   0:07.25 transmissioncli                                                                                                                                   
29330 root      20   0  2544 1100  792 R    2  0.1   0:00.01 top                                                                                                                                               
    1 root      20   0  3056 1900  576 S    0  0.1   0:02.37 init                                                                                                                                              
    2 root      15  -5     0    0    0 S    0  0.0   0:00.13 kthreadd                                                                                                                                          
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/0                                                                                                                                       
    4 root      15  -5     0    0    0 S    0  0.0   2:07.43 ksoftirqd/0                                                                                                                                       
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                        
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.03 migration/1                                                                                                                                       
    7 root      15  -5     0    0    0 S    0  0.0   0:15.47 ksoftirqd/1                                                                                                                                       
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                        
    9 root      15  -5     0    0    0 S    0  0.0   0:04.14 events/0                                                                                                                                          
   10 root      15  -5     0    0    0 S    0  0.0   0:00.87 events/1                                                                                                                                          
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                           
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                                                                     
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                                                                     
   54 root      15  -5     0    0    0 S    0  0.0   0:01.21 kblockd/0                                                                                                                                         
   55 root      15  -5     0    0    0 S    0  0.0   0:00.12 kblockd/1                                                                                                                                         
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                                            
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                      
  131 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                                                                                                            
  135 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                                           
  181 root      15  -5     0    0    0 S    0  0.0   2:41.20 kswapd0                                                                                                                                           
  223 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                             
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                             
  476 www-data  20   0 33824  11m 2348 S    0  0.6   3:35.26 transmissioncli                                                                                                                                   
 1114 www-data  20   0 27816 5784 2364 S    0  0.3   0:13.29 transmissioncli                                                                                                                                   
 1215 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                                     
 1216 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                                             
 1244 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                                                                             
 1245 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                                                                             
 1246 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                           
 1261 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                                                          
 1991 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                                                                       
 1996 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                                                         
 1997 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                                                         
 2066 root      15  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_2                                                                                                                                         
 2067 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                                                                         
 2080 root      15  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_4                                                                                                                                         
 2081 root      15  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_5                                                                                                                                         
 2179 root      15  -5     0    0    0 S    0  0.0   1:12.35 kjournald                                                                                                                                         
 2297 root      16  -4  2304  724  404 S    0  0.0   0:00.24 udevd                                                                                                                                             
 2471 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                                                                         
 2756 www-data  20   0 63764  44m 2556 D    0  2.2   9:56.12 python                                                                                                                                            
 3065 www-data  20   0 33356  11m 2348 S    0  0.6   2:30.99 transmissioncli                                                                                                                                   
 3631 root      15  -5     0    0    0 S    0  0.0   0:53.54 kjournald                                                                                                                                         
 3986 root      20   0  1780  524  456 S    0  0.0   0:00.00 getty                                                                                                                                             
 3987 root      20   0  1780  520  456 S    0  0.0   0:00.00 getty   
```


any help would be greatly appreciated

---

### Post by gombadi on 2009-04-25
High load and high wait time on a torrent server so my guess -

Running a large torrent server means a lot of work for the disks. Remote users are asking for sections of the files from all over the disk so the heads are busy moving all over the place.

Install sysstat and htop packages to see if you can get a better picture of what is going on.

Run htop instead of top (well I think it gives a better view of what is going on) and then run these commands for a while to see what the system is doing -
```

iostat -xt 5
vmstat 5

```

The above should give you a better idea of what the server is doing.

---

### Post by Wonslung on 2009-04-25
> **gombadi said:**
> High load and high wait time on a torrent server so my guess -

Running a large torrent server means a lot of work for the disks. Remote users are asking for sections of the files from all over the disk so the heads are busy moving all over the place.

Install sysstat and htop packages to see if you can get a better picture of what is going on.

Run htop instead of top (well I think it gives a better view of what is going on) and then run these commands for a while to see what the system is doing -
```

iostat -xt 5
vmstat 5

```

The above should give you a better idea of what the server is doing.
will do

but heres the thing, i've set up a bunch of these torrentflux servers and the load is NEVER like this.....it's unusually high....it's so odd

but THANKS
i will absolutely add those programs...hopefully i can figure it out...could be bad hardware i guess....


edit
well after checking a couple different servers against the problem server, it's obvious that it's I/O issues.....so you were probably right....but heres the thing...even when i have almost NO torrents running
i get these kind of numbers.

maybe a bad hard drive?```
Time: 12:24:09 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.67    0.77    7.40   77.21    0.00   13.94

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               4.60  6068.20   61.20   66.60  2428.80 43168.00   356.78   141.49 1105.68   7.82 100.00
sda1              0.00  6068.00    2.20   62.40    57.60 43107.20   668.19   110.58 1693.47  15.48 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              4.60     0.20   59.00    4.20  2371.20    60.80    38.48    30.91  504.87  15.82 100.00

Time: 12:24:14 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.67    1.25    7.41   90.66    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              11.40  4710.00   59.40   64.80  3544.00 41936.00   366.18   150.93 1146.70   8.05 100.00
sda1              1.60  4695.00    3.40   62.80    73.60 41902.40   634.08   131.82 1883.26  15.11 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              9.80    15.00   56.00    2.00  3470.40    33.60    60.41    19.12  306.00  17.24 100.00

Time: 12:24:19 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.45    0.96    9.55   78.40    0.00    9.64

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              11.60  7621.20   50.20   82.20  4126.40 67648.00   542.10   152.97 1262.72   7.55 100.00
sda1              0.00  7606.00    4.60   79.40    57.60 67521.60   804.51   131.68 1735.40  11.90 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3             11.60    15.20   45.60    2.80  4068.80   126.40    86.68    21.30  442.36  20.66 100.00

Time: 12:24:24 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.68    0.97    6.96   73.43    0.00   17.97

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              13.20  5221.80   54.40   65.80  4886.40 46721.60   429.35   126.02  962.45   8.32 100.00
sda1              0.00  5206.40    4.80   62.20    97.60 46470.40   695.04   108.54 1459.61  14.93 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3             13.20    15.40   49.60    3.60  4788.80   251.20    94.74    17.48  336.32  18.80 100.00

Time: 12:24:29 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.19    1.26    3.96   65.12    0.00   29.47

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               8.20  4243.00   69.60   53.60  3705.60 27408.00   252.55   155.20 1273.18   8.12 100.00
sda1              0.00  4243.00    4.00   51.20    52.80 27368.00   496.75   133.18 2445.22  18.12 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              8.20     0.00   65.60    2.40  3652.80    40.00    54.31    22.02  321.76  14.71 100.00

Time: 12:24:34 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.57    0.57    5.03   86.81    0.00    7.02

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              10.60  3526.80   64.00   52.40  4516.80 27044.80   271.15   127.38  949.02   8.59 100.00
sda1              0.00  3524.40    0.80   49.00    14.40 26998.40   542.43   104.99 1784.46  20.08 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3             10.60     2.40   63.20    3.40  4502.40    46.40    68.30    22.39  324.32  15.02 100.00

Time: 12:24:39 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.38    0.38    5.39   50.90    0.00   42.95

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               6.80  3732.20   52.00   48.80  3411.20 29843.20   329.90   163.50 1821.11   9.92 100.00
sda1              0.00  3732.00    0.00   47.60     0.00 29832.00   626.72   134.77 3252.52  21.01 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              6.80     0.20   52.00    1.20  3411.20    11.20    64.33    28.73  540.38  18.80 100.00

Time: 12:24:44 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.87    0.58    6.73   89.33    0.00    2.50

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               6.20  3582.80   56.40   60.80  3324.80 40244.80   371.75   142.39 1194.13   8.53 100.00
sda1              0.00  3579.80    0.00   58.20     0.00 40200.00   690.72   114.90 1928.63  17.18 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              6.20     3.00   56.40    2.60  3324.80    44.80    57.11    27.49  469.59  16.95 100.00

Time: 12:24:49 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.38    0.48    3.63   95.52    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              12.60  2516.20   65.60   45.20  4892.80 18064.00   207.19   155.23 1314.87   9.03 100.00
sda1              0.00  2513.60    0.20   43.60     1.60 18049.60   412.13   134.86 2879.54  22.83 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3             12.60     2.60   65.40    1.60  4891.20    14.40    73.22    20.37  292.00  14.93 100.00

Time: 12:24:54 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.77    0.57    4.69   93.97    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              19.60  3514.20   76.60   58.20  7225.60 26620.80   251.09   160.44 1213.89   7.42 100.00
sda1              0.00  3513.80    0.00   55.60     0.00 26577.60   478.01   139.80 2542.12  17.99 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3             19.60     0.40   76.60    2.60  7225.60    43.20    91.78    20.63  281.44  12.63 100.00

Time: 12:24:59 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.67    0.48    4.47   94.39    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               5.40  2849.40   52.80   43.40  2979.20 20950.40   248.75   128.21 1524.43  10.40 100.00
sda1              0.00  2835.60    0.00   39.40     0.00 20830.40   528.69    92.73 2891.42  25.38 100.00
sda2              0.00     0.00    0.00    0.40     0.00     3.20     8.00     1.35 3380.00 1705.00  68.20
sda3              5.40    13.80   52.80    3.60  2979.20   116.80    54.89    34.13  556.31  17.73 100.00

Time: 12:25:04 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.05    1.24    8.42   83.06    0.00    6.22

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               8.00  6576.60   51.20   64.60  3865.60 47692.80   445.24   150.74 1236.44   8.64 100.00
sda1              0.00  6550.80    2.20   61.80    17.60 47544.00   743.15   130.75 1898.41  15.62 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              8.00    25.80   49.00    2.80  3848.00   148.80    77.16    19.99  418.57  19.31 100.00

Time: 12:25:09 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.44    1.25    8.34   70.57    0.00   18.41

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              13.60  6277.40   62.40   69.80  3539.20 46739.20   380.32   139.16 1055.54   7.56 100.00
sda1              5.40  6248.40   11.40   65.20   380.80 46480.00   611.76   117.19 1517.65  13.05 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              8.20    29.00   51.00    4.60  3158.40   259.20    61.47    21.97  418.88  17.99 100.00

Time: 12:25:14 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.01    0.29    9.66   88.05    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              14.00  5984.20   45.80   70.80  3774.40 57296.00   523.76   146.29 1226.59   8.58 100.00
sda1              3.40  5970.20    4.00   67.80    94.40 57048.00   795.86   128.35 1738.83  13.93 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3             10.60    14.00   41.80    3.00  3680.00   248.00    87.68    17.94  405.62  22.32 100.00

Time: 12:25:19 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          15.87    0.88   10.81   69.43    0.00    3.02

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               8.00  7042.80   54.40   65.60  3115.20 45910.40   408.55   125.42 1075.48   8.33 100.00
sda1              0.00  7026.80    0.00   63.40     0.00 45787.20   722.20   101.79 1680.44  15.77 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              8.00    16.00   54.40    2.20  3115.20   123.20    57.22    23.63  397.84  17.67 100.00

Time: 12:25:24 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          10.34    0.59   11.41   70.63    0.00    7.02

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               7.40  3754.80   63.80   60.80  4070.40 34920.00   312.92   129.89 1015.86   8.03 100.00
sda1              0.00  3754.40    1.20   57.40    14.40 34867.20   595.25   109.35 1799.22  17.06 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              7.40     0.40   62.60    3.40  4056.00    52.80    62.25    20.54  320.33  15.15 100.00

Time: 12:25:29 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          43.70    1.00   21.40   33.60    0.00    0.30

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               5.00  5173.40   45.80   56.20  2084.80 40888.00   421.30   160.28 1491.84   9.80 100.00
sda1              0.00  5158.60    0.40   54.20     3.20 40843.20   748.10   135.13 2360.11  18.32 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              5.00    14.80   45.40    2.00  2081.60    44.80    44.86    25.15  491.69  21.10 100.00

Time: 12:25:34 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          32.41    0.00   16.45   51.14    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda              11.60  4841.20   50.40   68.60  3240.00 50966.40   455.52   163.47 1419.01   8.40 100.00
sda1              0.00  4837.60    0.40   62.80     3.20 50801.60   803.87   127.16 2068.23  15.82 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3             11.60     3.60   50.00    5.80  3236.80   164.80    60.96    36.31  683.69  17.92 100.00

Time: 12:25:39 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          22.20    1.08   14.93   61.79    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               8.20  7412.60   55.20   67.80  2992.00 47753.60   412.57   146.90 1241.84   8.13 100.00
sda1              0.00  7402.00    0.00   64.60     0.00 47643.20   737.51   121.59 1999.26  15.48 100.00
sda2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sda3              8.20    10.60   55.20    3.20  2992.00   110.40    53.12    25.30  404.01  17.12 100.00


```

---

