---
title: "Help Test PowerManagementALPM for Precise"
date: 2011-12-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by geojorg on 2011-12-11
People interested in testing visit the wiki.

[https://wiki.ubuntu.com/Kernel/PowerManagementALPM](https://wiki.ubuntu.com/Kernel/PowerManagementALPM)

---

### Post by MacUntu on 2011-12-11
Interesting, will have a look after installing P on a test disk, because I don't have the b*lls to run **this** test on my productive P system. :P

---

### Post by geojorg on 2011-12-12
Is working fine for me in Oneiric and Precise.

---

### Post by MacUntu on 2011-12-12
Running fine here too, saves 2 Watts on my ThinkPad T510.

---

### Post by SushiR on 2011-12-12
Erm...call me dumb but...how can I add my stuff to the table?

---

### Post by MacUntu on 2011-12-12
Log in (Ubuntu single sign on - should work with you LP credentials I guess, but was awfully slow when I tried it), then click on the "Edit" link at the top of the wiki page and just copy the line you need to enter (||column 1||column 2||...|| - don't forget to add thesystem in alphabetic order). Preview, save, done.

---

### Post by geojorg on 2011-12-13
There is also a new test for pmutils here: [https://wiki.ubuntu.com/Kernel/PowerManagementPMUtils](https://wiki.ubuntu.com/Kernel/PowerManagementPMUtils)


Please help testing to improve power Managment in 12.04

---

### Post by MacUntu on 2011-12-13
Thanks for posting, testing now. I had to enable a bunch of devices in the BIOS first. :D

---

### Post by ventrical on 2011-12-13
So far - works great... while looking at system-monitor - this laptop is running as cool as a cucumber.
ventrical@ventrical-Extensa-4420:~$ sudo dmidecode -t 0 | grep "Version"
[sudo] password for ventrical: 
    Version: V1.17
ventrical@ventrical-Extensa-4420:~$ uname -a
Linux ventrical-Extensa-4420 3.2.0-4-generic #10-Ubuntu SMP Sat Dec 10 17:46:09 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-Extensa-4420:~$ lspci -vn |grep AHCI
00:12.0 0106: 1002:4380 (prog-if 01 [AHCI 1.0])

ventrical@ventrical-Extensa-4420:~$ sudo pm-powersave true
ventrical@ventrical-Extensa-4420:~$ powerstat
Running for 300 seconds (30 samples at 10 second intervals).
ACPI battery power measurments will start in 180 seconds time

  Time    User  Nice   Sys  Idle    IO  Run Ctxt/s  IRQ/s  Watts               
17:41:47   1.1   0.0   0.6  98.3   0.0    1   1375    270  22.13
17:41:57   4.1   0.0   1.6  94.3   0.0    1   1321    301  22.97
17:42:07   1.5   0.0   0.7  97.8   0.0    1   1267    163  23.15
17:42:17   0.3   0.0   0.4  99.4   0.0    2   1136    114  22.03
17:42:27   7.8   0.0   2.5  87.6   2.1    3   1744    630  21.66
17:42:37   6.4   0.0   3.0  90.3   0.4    1   1770    891  23.58
17:42:47   3.8   0.0   1.1  95.2   0.0    1   1210    239  23.70
17:42:57   4.6   0.0   1.0  91.7   2.7    2   1303    255  22.86
17:43:07   6.0   0.0   1.6  91.6   0.8    1   1098    342  22.49
17:43:17   7.8   0.0   1.6  90.2   0.4    1   1443    563  23.03
17:43:27   7.9   0.0   1.3  88.7   2.2    1   1278    474  23.31
17:43:37   5.2   0.0   2.0  92.7   0.0    1   1406    622  23.57
17:43:47   1.4   0.0   0.6  98.0   0.0    1   1559    326  23.94
17:43:57   2.0   0.0   1.4  90.9   5.7    1   1338    231  24.06
17:44:07   1.1   0.0   0.3  98.2   0.4    1   1178    170  22.86
17:44:17   3.6   0.0   0.5  95.7   0.3    1   1047    228  22.21
17:44:27   1.0   0.0   0.5  96.3   2.3    1   1209    186  22.18
17:44:37   1.0   0.0   0.4  98.6   0.0    1   1099    170  21.83
17:44:47   0.7   0.0   0.3  99.0   0.0    1   1177    150  21.64
17:44:57   0.9   0.0   0.6  95.3   3.3    1   1208    157  21.29
17:45:07   0.8   0.0   0.3  98.9   0.0    1   1168    139  21.01
17:45:17   0.8   0.0   0.4  98.9   0.0    1   1071    157  21.01
  Time    User  Nice   Sys  Idle    IO  Run Ctxt/s  IRQ/s  Watts
17:45:27   0.8   0.0   0.5  95.1   3.6    1   1250    168  21.75
17:45:37   2.5   0.0   1.2  96.3   0.0    1   1399    432  22.20
17:45:47   1.4   0.0   0.7  98.0   0.0    1   1435    180  22.58
17:45:57   3.8   0.0   1.5  91.5   3.2    3   1335    598  22.47
17:46:07   1.2   0.0   0.5  98.3   0.0    1   1116    235  23.00
17:46:17   4.8   0.0   2.1  93.1   0.0    1   1713    752  23.14
17:46:27   1.6   0.0   0.6  93.8   4.0    1   1222    276  23.24
17:46:37   2.2   0.0   1.2  96.6   0.0    1   1086    315  23.21
-------- ----- ----- ----- ----- ----- ---- ------ ------ ------
 Average   2.9   0.0   1.0  95.0   1.0  1.2 1298.6  324.5  22.60
  StdDev   2.4   0.0   0.7   3.4   1.6  0.5  192.4  200.0   0.83
-------- ----- ----- ----- ----- ----- ---- ------ ------ ------
 Minimum   0.3   0.0   0.3  87.6   0.0  1.0 1047.1  113.5  21.01
 Maximum   7.9   0.0   3.0  99.4   5.7  3.0 1770.0  890.7  24.06
-------- ----- ----- ----- ----- ----- ---- ------ ------ ------
Summary:
 22.60 Watts on Average with Standard Deviation 0.83  
ventrical@ventrical-Extensa-4420:~$ 

next test

---

### Post by ventrical on 2011-12-13
ventrical@ventrical-Extensa-4420:~$ sudo dmidecode -t 0 | grep "Version"
[sudo] password for ventrical: 
    Version: V1.17
ventrical@ventrical-Extensa-4420:~$ uname -a
Linux ventrical-Extensa-4420 3.2.0-4-generic #10-Ubuntu SMP Sat Dec 10 17:46:09 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-Extensa-4420:~$ lspci -vn |grep AHCI
00:12.0 0106: 1002:4380 (prog-if 01 [AHCI 1.0])



ventrical@ventrical-Extensa-4420:~$ powerstat
Running for 300 seconds (30 samples at 10 second intervals).
ACPI battery power measurments will start in 180 seconds time

  Time    User  Nice   Sys  Idle    IO  Run Ctxt/s  IRQ/s  Watts               
17:59:33   0.8   0.0   0.3  98.9   0.0    1   1349    123  20.44
17:59:43   0.6   0.0   0.5  98.9   0.0    1   1386    127  20.87
17:59:53   1.0   0.0   0.6  95.3   3.2    3   1426    150  20.82
18:00:03   0.8   0.0   0.4  98.8   0.0    1   1478    111  20.54
18:00:13   0.8   0.0   0.5  98.7   0.0    1   1378    110  20.35
18:00:23   1.0   0.0   0.4  95.2   3.4    2   1501    124  20.34
18:00:33   0.8   0.0   0.4  98.9   0.0    1   1380    111  20.27
18:00:43   0.6   0.0   0.3  99.1   0.0    1   1251     95  20.53
18:00:53   1.1   0.0   0.6  95.1   3.3    1   1404    146  20.41
18:01:03   0.8   0.0   0.3  98.9   0.0    1   1466    125  20.37
18:01:13   0.9   0.0   0.3  98.8   0.0    1   1375    127  20.30
18:01:23   0.7   0.0   0.5  95.6   3.3    1   1533    146  20.31
18:01:33   0.7   0.0   0.4  98.9   0.0    2   1372    128  20.31
18:01:43   1.1   0.0   0.6  98.4   0.0    1   1378    116  20.30
18:01:53   0.8   0.0   0.4  95.3   3.5    1   1393    129  20.27
18:02:03   0.8   0.0   0.4  98.8   0.0    2   1463    122  19.90
18:02:13   1.0   0.0   0.3  98.7   0.0    1   1182    119  19.61
18:02:23   0.8   0.0   0.5  95.2   3.6    1   1455    112  19.87
18:02:33   0.9   0.0   0.5  98.7   0.0    1   1467    116  20.07
18:02:43   6.3   0.0   0.8  92.9   0.0    1   1160    139  20.00
18:02:53   0.9   0.0   0.7  96.1   2.3    1   1522    148  20.92
18:03:03   0.9   0.0   0.4  98.8   0.0    1   1365    115  20.65
  Time    User  Nice   Sys  Idle    IO  Run Ctxt/s  IRQ/s  Watts
18:03:13   0.9   0.0   0.5  98.6   0.0    1   1379    122  20.41
18:03:23   0.8   0.0   0.4  95.4   3.4    1   1390    119  20.39
18:03:33   0.8   0.0   0.4  98.8   0.0    1   1460    118  20.31
18:03:43   0.8   0.0   0.4  98.9   0.0    1   1254    115  20.27
18:03:53   1.0   0.0   0.5  95.1   3.5    1   1519    135  20.24
18:04:03   0.9   0.0   0.4  98.7   0.0    1   1368    114  20.23
18:04:13   0.7   0.0   0.6  96.8   2.0    1   1496    123  20.24
18:04:23   0.8   0.0   0.4  96.4   2.4    2   1393    117  20.31
-------- ----- ----- ----- ----- ----- ---- ------ ------ ------
 Average   1.0   0.0   0.4  97.4   1.1  1.2 1398.2  123.3  20.33
  StdDev   1.0   0.0   0.1   1.8   1.5  0.5   91.1   12.6   0.27
-------- ----- ----- ----- ----- ----- ---- ------ ------ ------
 Minimum   0.6   0.0   0.3  92.9   0.0  1.0 1160.0   94.6  19.61
 Maximum   6.3   0.0   0.8  99.1   3.6  3.0 1533.2  150.2  20.92
-------- ----- ----- ----- ----- ----- ---- ------ ------ ------
Summary:
 20.33 Watts on Average with Standard Deviation 0.27  
ventrical@ventrical-Extensa-4420:~$ 

Better than 2 watts.

---

