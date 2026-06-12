---
title: "Memory usage high 14.04"
date: 2014-05-08
forum: Server Platforms
---

### Post by trevor_allett on 2014-05-08
I am seeing a lot of memory "taken" up with not much...
I have two severs at the moment; differences are:
[COLOR=#800000]ONE[/COLOR]: 13.10 real hardware (Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz, 2 cores) running Apache2, Mysql, PHP, sshd, SAMBA Providing one general file share to local network
```
root@svr:~# free -h
             total       used       free     shared    buffers     cached
Mem:          3.7G       926M       2.8G         0B       210M       463M
-/+ buffers/cache:       252M       3.5G
Swap:         3.8G         0B       3.8G
root@svr:~#
```
[COLOR=#800000]TWO[/COLOR]: 14.04 virtual VMware Box (Intel(R) Xeon(R) CPU X3320 @ 2.50GHz, 4 cores) running Apache2, Mysql, PHP, sshd, SAMBA Providing one general file share to local network
```
vlad@server:/$ free -h
             total       used       free     shared    buffers     cached
Mem:          3.9G       3.3G       552M       6.7M        77M       541M
-/+ buffers/cache:       2.7G       1.1G
Swap:         4.0G         0B       4.0G
```
Apart from some "loosening up" of the sudo restrictions on the 13.10 (attempted import of the live system into VMware) they are standard server installs.

The reported memory use in webmin is more like I'd expect after a reboot but after a while I'm back to all the ram gone.
thanks for listening-

---

### Post by Gyokuro on 2014-05-08
Hi

Thank you but could you please post an output of:

top -d1 and hit the M key (now the sorting is by RAM usage)

- HTH

---

### Post by trevor_allett on 2014-05-08
```
vlad@server:~$ top -d1
top - 21:24:47 up 1 day, 13:17,  1 user,  load average: 0.00, 0.01, 0.05
Tasks: 114 total,   1 running, 113 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.2 sy,  0.0 ni, 99.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4048076 total,  3521356 used,   526720 free,    81928 buffers
KiB Swap:  4193276 total,        0 used,  4193276 free.   588324 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 3941 mysql     20   0  484436  48272   6668 S   0.0  1.2   2:27.57 mysqld
 1008 root      20   0   86432  24784   1736 S   0.0  0.6   0:34.63 miniserv.pl
 3723 root      20   0  276352  15136   9732 S   0.0  0.4   0:14.78 apache2
  489 root      20   0  273088   7812   5944 S   0.0  0.2   0:13.35 smbd
 3728 www-data  20   0  276608   7064   1340 S   0.0  0.2   0:00.65 apache2
 3727 www-data  20   0  276576   6900   1252 S   0.0  0.2   0:00.77 apache2
 7071 www-data  20   0  276568   6852   1228 S   0.0  0.2   0:00.02 apache2
 6977 www-data  20   0  276576   6848   1228 S   0.0  0.2   0:00.07 apache2
 7073 www-data  20   0  276576   6844   1228 S   0.0  0.2   0:00.06 apache2
 6978 www-data  20   0  276568   6840   1228 S   0.0  0.2   0:00.10 apache2
 6979 www-data  20   0  276568   6840   1228 S   0.0  0.2   0:00.01 apache2
 7074 www-data  20   0  276568   6836   1228 S   0.0  0.2   0:00.01 apache2
 9220 www-data  20   0  276568   6808   1208 S   0.0  0.2   0:00.00 apache2
    1 root      20   0   36680   6008   1516 S   0.0  0.1   0:09.90 init
 9221 www-data  20   0  276376   5840    428 S   0.0  0.1   0:00.00 apache2
  728 root      20   0  231332   5720   4212 S   0.0  0.1   0:01.10 winbindd
21244 root      20   0  105628   4308   3240 S   0.0  0.1   0:00.08 sshd
  837 root      20   0  231332   3956   2420 S   0.0  0.1   0:03.30 winbindd
21293 vlad      20   0   22468   3744   1876 S   0.0  0.1   0:00.16 bash
 4326 root      20   0  231332   3648   2112 S   0.0  0.1   0:01.29 winbindd
  847 root      20   0  273096   3164   1296 S   0.0  0.1   0:02.02 smbd
 4325 root      20   0  231332   3116   1584 S   0.0  0.1   0:01.38 winbindd
  917 root      20   0   61364   3068   2392 S   0.0  0.1   0:00.65 sshd
  848 root      20   0  191448   2780   1484 S   0.0  0.1   0:13.61 nmbd
21292 vlad      20   0  105628   2232   1164 S   0.0  0.1   0:00.33 sshd
  663 root      20   0   43448   1840   1476 S   0.0  0.0   0:01.47 systemd-logind
21387 vlad      20   0   25000   1684   1176 R   1.0  0.0   0:00.59 top
  626 syslog    20   0  255840   1596    984 S   0.0  0.0   0:03.28 rsyslogd
  301 root      20   0   51212   1564    996 S   0.0  0.0   0:00.89 systemd-udevd
  552 message+  20   0   39212   1216    828 S   0.0  0.0   0:02.07 dbus-daemon
 1097 root      20   0   23044   1124    756 S   0.0  0.0   0:00.28 ntpd
 1098 ntpd      20   0   18816   1040    700 S   0.0  0.0   0:04.43 ntpd
  910 root      20   0   23656   1028    776 S   0.0  0.0   0:01.53 cron
  884 root      20   0   15820    944    784 S   0.0  0.0   0:00.00 getty
  887 root      20   0   15820    944    784 S   0.0  0.0   0:00.00 getty
  892 root      20   0   15820    940    784 S   0.0  0.0   0:00.00 getty
  893 root      20   0   15820    940    784 S   0.0  0.0   0:00.00 getty
  895 root      20   0   15820    940    784 S   0.0  0.0   0:00.00 getty
 1012 root      20   0   15820    940    784 S   0.0  0.0   0:00.00 getty
  919 root      20   0    4368    660    516 S   0.0  0.0   0:00.01 acpid
 5314 root      20   0   19472    652    452 S   0.0  0.0   0:00.30 upstart-udev-br
 5321 root      20   0   15260    628    408 S   0.0  0.0   0:00.27 upstart-socket-
 5317 root      20   0   15276    400    196 S   0.0  0.0   0:00.33 upstart-file-br
  909 daemon    20   0   19140    160      0 S   0.0  0.0   0:00.09 atd
    2 root      20   0       0      0      0 S   0.0  0.0   0:04.09 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.57 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   0:17.07 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:04.44 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:04.18 rcuos/1
   10 root      20   0       0      0      0 S   0.0  0.0   0:03.86 rcuos/2
   11 root      20   0       0      0      0 S   0.0  0.0   0:03.89 rcuos/3
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh


```

---

