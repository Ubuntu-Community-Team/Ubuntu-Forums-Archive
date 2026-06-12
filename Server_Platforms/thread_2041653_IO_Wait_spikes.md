---
title: "IO Wait spikes"
date: 2012-08-13
forum: Server Platforms
---

### Post by scontotech on 2012-08-13
I am having a server running Ubuntu Linux 10.04.4, kernel: Linux 2.6.32-41-server

For me the system does not seem to be very busy BUT **sometimes (*actually quite often - few times in a hour*) I/O Wait jumps to 100%** (also hdds %util jumsps to 100%). It lasts for only 1-4 seconds but in that time websites and other applications running on server become inaccessible.

Maybe someone has some ideas where to search for problem?

Some useful information. If you need anything else just ask.

Server hw:
CPU: 4 x Quad-Core AMD Opteron(tm) Processor 8356
RAM: 16 x 2GB
HDD: 4 x 500GB 7200rpm RAID10

top:
```

top - 10:20:17 up 4 days,  1:40,  1 user,  load average: 1.87, 1.98, 2.24
Tasks: 728 total,   7 running, 721 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.1%us,  6.8%sy,  0.0%ni, 72.8%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:  33080224k total, 29550656k used,  3529568k free,   684568k buffers
Swap:  4095968k total,    32228k used,  4063740k free, 19076768k cached

```

iostat does not show anything useful.

iostat -x 10 10:
```

Linux 2.6.32-41-server (serveris5x16)   08/13/2012      _x86_64_        (16 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          24.32    0.00    7.88    0.88    0.00   66.93

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               1.34    57.88    4.74   29.13   434.54   686.34    33.08     9.92  292.87   4.56  15.45
sdb               0.19    15.95    0.41    7.80    47.35   187.16    28.55     4.12  501.94   6.83   5.61
sdc               0.65    56.56    3.90   18.94   276.88   594.37    38.14     3.29  144.19   5.95  13.60
md0               0.00     0.00   12.89  159.24   947.80  1273.96    12.91     0.00    0.00   0.00   0.00
sdd               0.62    56.51    1.02   18.99   189.11   594.37    39.15     1.37   68.35   4.35   8.70

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          23.30    0.00    6.82    0.01    0.00   69.87

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00    10.50    0.00   15.20     0.00   196.00    12.89     0.48   31.38   3.49   5.30
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00     3.80    0.00   13.60     0.00   129.60     9.53     0.16   11.62   4.12   5.60
md0               0.00     0.00    0.00   39.90     0.00   319.20     8.00     0.00    0.00   0.00   0.00
sdd               0.00     3.70    0.00   13.70     0.00   129.60     9.46     0.15   10.66   2.92   4.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          22.64    0.00    7.14    0.01    0.00   70.21

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     3.00    0.10    8.20     0.80    76.40     9.30     0.06    6.75   6.63   5.50
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00    10.10    0.20    8.20     4.00   133.20    16.33     0.06    6.79   6.79   5.70
md0               0.00     0.00    0.30   25.10     4.80   200.80     8.09     0.00    0.00   0.00   0.00
sdd               0.00    10.10    0.00    8.20     0.00   133.20    16.24     0.05    6.46   6.46   5.30

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          23.87    0.00    7.47    0.82    0.00   67.83

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.40    20.50    0.80   37.40   108.80   454.00    14.73    14.95  391.28   5.63  21.50
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.20    12.90    0.50   25.40    84.80   295.60    14.69     9.00  347.41   9.46  24.50
md0               0.00     0.00    2.10   92.80   219.20   742.40    10.13     0.00    0.00   0.00   0.00
sdd               0.00    12.80    0.20   25.50    25.60   295.60    12.50     4.27  166.30   6.73  17.30

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          23.56    0.00    7.33    0.07    0.00   69.04

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.10     6.50    0.60   19.60    56.80   195.00    12.47     0.20    9.85   2.67   5.40
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00    11.90    0.80   13.00    39.20   185.40    16.28     0.10    7.39   5.80   8.00
md0               0.00     0.00    1.50   46.40    96.00   371.20     9.75     0.00    0.00   0.00   0.00
sdd               0.00    11.90    0.00   13.00     0.00   185.40    14.26     0.08    6.38   4.77   6.20

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          25.40    0.00    7.60    0.41    0.00   66.60

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     9.00    0.10   27.00     0.80   272.40    10.08    14.88  260.15   5.57  15.10
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00     9.60    0.10   23.20     1.60   249.20    10.76     5.97  186.27   6.91  16.10
md0               0.00     0.00    0.30  128.70     3.20  1029.60     8.01     0.00    0.00   0.00   0.00
sdd               0.00     9.70    0.10   25.70     0.80   270.00    10.50     4.79  171.94   6.01  15.50

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          23.34    0.00    7.30    0.94    0.00   68.42

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00    22.40    0.00   86.60     0.00   865.40     9.99    44.80  607.67   4.84  41.90
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00     6.10    0.20   38.40    16.00   347.00     9.40     3.02  120.47   7.07  27.30
md0               0.00     0.00    0.20   86.20    16.00   689.60     8.17     0.00    0.00   0.00   0.00
sdd               0.00     6.10    0.00   35.80     0.00   326.20     9.11     0.50   23.77   2.43   8.70

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          23.46    0.00    7.21    0.08    0.00   69.25

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               1.30     1.80    2.10    6.50   419.20    58.00    55.49     0.05    5.70   4.53   3.90
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               1.10    15.10    1.10    7.30   363.20   170.80    63.57     0.07    7.86   5.95   5.00
md0               0.00     0.00    6.10   27.90   867.20   223.20    32.07     0.00    0.00   0.00   0.00
sdd               0.10    15.00    0.40    7.40    84.80   170.80    32.77     0.05    6.54   6.28   4.90

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          22.43    0.00    7.21    0.01    0.00   70.35

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00    11.70    0.00   20.00     0.00   244.60    12.23     0.94   46.80   3.20   6.40
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00     2.90    0.00   11.80     0.00   108.60     9.20     0.10    8.39   3.22   3.80
md0               0.00     0.00    0.00   43.40     0.00   347.20     8.00     0.00    0.00   0.00   0.00
sdd               0.00     2.90    0.00   11.80     0.00   108.60     9.20     0.12   10.17   4.92   5.80

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          22.96    0.00    7.38    0.01    0.00   69.65

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     4.90    0.00   28.60     0.00   257.80     9.01     5.87  205.31   4.65  13.30
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00    24.80    0.30   17.10    16.80   325.00    19.64     0.99   56.78   6.67  11.60
md0               0.00     0.00    0.30   72.00    16.80   576.00     8.20     0.00    0.00   0.00   0.00
sdd               0.00    24.80    0.00   17.10     0.00   325.00    19.01     0.55   32.40   3.86   6.60

```
At the moment hdd sdb has been removed from raid to check if it is not faulty.

---

### Post by Habitual on 2012-08-13
terminal > 
```
cat /proc/mdstat
``` and 
```
df -hT
```

output please.

---

### Post by scontotech on 2012-08-13
Raid seems to be fine
cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid10 sdb2[1] sda3[0] sdd2[3] sdc2[2]
      973696000 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]

unused devices: <none>

```(added back sdb to raid)

df -hT:
```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/md0      ext4    915G  577G  291G  67% /
none      devtmpfs     16G  224K   16G   1% /dev
none         tmpfs     16G     0   16G   0% /dev/shm
none         tmpfs     16G  148K   16G   1% /var/run
none         tmpfs     16G     0   16G   0% /var/lock
none         tmpfs     16G     0   16G   0% /lib/init/rw
none       debugfs    915G  577G  291G  67% /var/lib/ureadahead/debugfs
/dev/sda1     ext4    485M   72M  389M  16% /boot

```

---

### Post by ian dobson on 2012-08-13
Hi,

Maybe run iotop -o -P to see who's causing the seeks on the drives.

Regards
Ian Dobson

---

### Post by d4m1r on 2012-08-13
Could be the beginning of hardware failure...Sometimes you get I/O spikes where everything stops for a few seconds (lag) means you have too many bad sectors or there is a mechanical issue with the harddrive coming...I'd check them all for bad sectors and their smart status.

Are they Seagate drives perhaps?

---

### Post by scontotech on 2012-08-13
> **ian dobson said:**
> Hi,

Maybe run iotop -o -P to see who's causing the seeks on the drives.

Regards
Ian Dobson
As I mentioned before, iotop does not show anything useful. Maybe it is just too small period of time (that lag moment) to show anything worthful. 

> **d4m1r said:**
> Could be the beginning of hardware  failure...Sometimes you get I/O spikes where everything stops for a few  seconds (lag) means you have too many bad sectors or there is a  mechanical issue with the harddrive coming...I'd check them all for bad  sectors and their smart status.

Are they Seagate drives perhaps?
Server is brand new just EOL. Also hard drives are new - aprox. 4-5 months. SMART status does not show any reallocated sectors or other problems.

_Yes, they are Seagate drives. What is wrong with that?_ 
P.S. At the moment I bought them, it was not possible to get any WD.

For example, "iostat -t -dx 1" sometimes shows 
```

08/13/2012 03:09:33 PM
Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     2.00    0.00  160.00     0.00  1288.00     8.05    89.72  729.94   6.25 100.00
sdb               0.00     2.00    0.00   66.00     0.00   528.00     8.00   151.28  886.36  15.15 100.00
sdc               0.00     0.00    0.00   79.00     0.00   632.00     8.00    28.07  518.73  10.13  80.00
md0               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdd               0.00     0.00    0.00   70.00     0.00   560.00     8.00    14.47  351.29   7.00  49.00
```
Because of that it [%util] seems like i/o wait problem.

BUT

I have not seen that "dstat -df" even shows 1MB or more at any time.

---

### Post by d4m1r on 2012-08-13
> **scontotech said:**
> 

_Yes, they are Seagate drives. What is wrong with that?_ 
P.S. At the moment I bought them, it was not possible to get any WD.


I knew it because I have an old Seagate drive in one of my servers and it has the exact same issue....I had the OS on it so everything occasionally froze for a few seconds so I knew its was dying...Recently switched it to storage only duty.

---

### Post by scontotech on 2012-08-13
> **d4m1r said:**
> I knew it because I have an old Seagate drive in one of my servers and it has the exact same issue....I had the OS on it so everything occasionally froze for a few seconds so I knew its was dying...Recently switched it to storage only duty.

Ok, thank you for the info. I will keep checking hdds (removing 1 at the time from raid) and hope that not all 4 are going to die..

---

### Post by d4m1r on 2012-08-14
> **scontotech said:**
> Ok, thank you for the info. I will keep checking hdds (removing 1 at the time from raid) and hope that not all 4 are going to die..

My guess is it's only 1 HDD causing that issue, but if you have many, now you have to go through them all and figure out which is causing the IO waits....

---

