---
title: "Very high cpu, load average above 130."
date: 2014-07-12
forum: Server Platforms
---

### Post by nos09 on 2014-07-12
Hi, I am managing a server. We are load testing it with a php scripts that sends data on this server. I am looking for my options to handle very high cpu load. 

Top output : 

```
top - 09:46:37 up 22:42,  2 users,  load average: 142.95, 144.09, 144.89
Tasks: 259 total,  98 running, 161 sleeping,   0 stopped,   0 zombie
%Cpu(s): 45.0 us, 10.4 sy,  0.0 ni, 14.1 id, 29.7 wa,  0.8 hi,  0.0 si,  0.0 st
KiB Mem:  15403984 total,  5654720 used,  9749264 free,   234528 buffers
KiB Swap:        0 total,        0 used,        0 free.  3708428 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1068 mysql     20   0 3490492 398004   7624 S  78.1  2.6 171:54.06 mysqld
 2281 www-data  20   0  382764  11308   3672 D  12.0  0.1   2:20.22 apache2
 3756 root      20   0   23672   1516   1068 R  12.0  0.0   0:00.02 top
12886 www-data  20   0  384556  14732   5200 R  12.0  0.1  17:41.16 apache2
19835 www-data  20   0  386008  18196   8536 R  12.0  0.1   2:02.15 apache2
22862 www-data  20   0  384648  13972   4468 D  12.0  0.1  15:47.98 apache2
31602 www-data  20   0  384944  15232   5168 S  12.0  0.1   4:27.72 apache2
  696 www-data  20   0  382788  11428   3640 R   6.0  0.1   2:26.83 apache2
  914 www-data  20   0  382928  11204   3316 D   6.0  0.1   1:05.49 apache2
 1032 www-data  20   0  382904  11148   3316 R   6.0  0.1   2:26.39 apache2
 1306 www-data  20   0  385228  15236   6688 R   6.0  0.1   2:27.49 apache2
 1386 www-data  20   0  385816  17968   8500 R   6.0  0.1   2:26.97 apache2
 1650 www-data  20   0  382728  11444   3636 R   6.0  0.1   2:26.84 apache2
 1767 www-data  20   0  382732  11488   3660 R   6.0  0.1   2:27.36 apache2
 2080 www-data  20   0  382840  11460   3672 R   6.0  0.1   2:26.57 apache2
 2246 www-data  20   0  384428  14284   6476 R   6.0  0.1   2:27.17 apache2
 2372 www-data  20   0  386816  19584   9116 R   6.0  0.1   2:20.94 apache2
 2869 www-data  20   0  385024  15320   5180 R   6.0  0.1  20:29.38 apache2
 9402 www-data  20   0  383600  13124   4668 R   6.0  0.1   2:55.16 apache2
 9912 www-data  20   0  382816  11444   3676 R   6.0  0.1   2:26.97 apache2
10069 www-data  20   0  386004  18800   9148 R   6.0  0.1   1:26.56 apache2
10103 www-data  20   0  383672  13376   4688 D   6.0  0.1   2:48.95 apache2
10381 www-data  20   0  385144  17608   8984 R   6.0  0.1   2:55.46 apache2
10500 www-data  20   0  389252  23532  10656 R   6.0  0.2   2:53.92 apache2
10520 www-data  20   0  382624  11556   3720 R   6.0  0.1   2:19.53 apache2
10528 www-data  20   0  382656  11508   3672 S   6.0  0.1   2:25.98 apache2
10576 www-data  20   0  382788  11160   3316 R   6.0  0.1   2:26.77 apache2
10864 www-data  20   0  382792  11304   3632 S   6.0  0.1   0:15.26 apache2
10869 www-data  20   0  383000  11560   3680 S   6.0  0.1   2:26.26 apache2
10870 www-data  20   0  382648  11304   3460 D   6.0  0.1   2:26.63 apache2
10997 www-data  20   0  383784  13344   4640 R   6.0  0.1   2:55.13 apache2
13468 www-data  20   0  382608  11452   3636 R   6.0  0.1   0:55.33 apache2
13898 www-data  20   0  384624  14760   5160 R   6.0  0.1  17:29.06 apache2
15449 www-data  20   0  382724  11196   3556 R   6.0  0.1   2:07.16 apache2
18665 www-data  20   0  382748  11376   3596 R   6.0  0.1   1:07.98 apache2
20207 www-data  20   0  390536  24116  10172 D   6.0  0.2  16:19.56 apache2
22449 www-data  20   0  384512  13984   4616 R   6.0  0.1  15:59.80 apache2
22577 www-data  20   0  383700  13544   4868 R   6.0  0.1   3:20.90 apache2
29051 www-data  20   0  382624  11080   3316 R   6.0  0.1   0:55.88 apache2
30389 www-data  20   0  383576  12640   4224 R   6.0  0.1   3:13.20 apache2
31352 www-data  20   0  384992  15292   5156 D   6.0  0.1   4:29.56 apache2
31362 www-data  20   0  384392  13876   4476 R   6.0  0.1   4:29.63 apache2
31378 www-data  20   0  386708  17840   7800 D   6.0  0.1   4:19.84 apache2
31394 www-data  20   0  385024  15212   5076 D   6.0  0.1   4:27.29 apache2
31395 www-data  20   0  384668  14048   4520 R   6.0  0.1   4:27.52 apache2
31737 www-data  20   0  384228  13648   4392 S   6.0  0.1   4:26.25 apache2
    1 root      20   0   33516   2896   1476 S   0.0  0.0   0:02.29 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:22.71 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   3:14.40 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   1:07.80 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:58.47 rcuos/1
   10 root      20   0       0      0      0 S   0.0  0.0   0:57.72 rcuos/2
   11 root      20   0       0      0      0 S   0.0  0.0   0:57.83 rcuos/3
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.07 migration/0
   18 root      rt   0       0      0      0 S   0.0  0.0   0:00.50 watchdog/0
   19 root      rt   0       0      0      0 S   0.0  0.0   0:00.44 watchdog/1
   20 root      rt   0       0      0      0 S   0.0  0.0   0:00.06 migration/1
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/1
   23 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H
   24 root      rt   0       0      0      0 S   0.0  0.0   0:00.42 watchdog/2
   25 root      rt   0       0      0      0 S   0.0  0.0   0:00.06 migration/2
   26 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/2
   28 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0H
   29 root      rt   0       0      0      0 S   0.0  0.0   0:00.39 watchdog/3
   30 root      rt   0       0      0      0 S   0.0  0.0   0:00.06 migration/3
   31 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/3
   33 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0H
   34 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   35 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   36 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   37 root      20   0       0      0      0 S   0.0  0.0   0:00.00 xenwatch
   38 root      20   0       0      0      0 S   0.0  0.0   0:00.00 xenbus
   39 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   40 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   41 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   42 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u9:0
   43 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   44 root      20   0       0      0      0 S   0.0  0.0   1:34.47 kworker/1:1
   45 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   46 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khubd
   47 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
   48 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
   49 root      20   0       0      0      0 S   0.0  0.0   1:36.27 kworker/2:1
   51 root      20   0       0      0      0 S   0.0  0.0   0:00.04 khungtaskd
   52 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kswapd0
   53 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   54 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_mark
   55 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-kthrea
   56 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   68 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
   69 root      20   0       0      0      0 R   0.0  0.0   0:42.93 kworker/u8:1
   70 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khvcd
   89 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   90 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_manager
   95 root      20   0       0      0      0 S   0.0  0.0   2:42.40 kworker/0:1
  149 root      20   0       0      0      0 R   0.0  0.0   1:36.09 kworker/3:1
  191 root      20   0       0      0      0 S   0.0  0.0   0:24.97 jbd2/xvda1-8
  192 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-conver
  342 root      20   0   19472    652    452 S   0.0  0.0   0:00.16 upstart-udev-br
  348 root      20   0   49564   1524   1012 S   0.0  0.0   0:00.06 systemd-udevd
  401 www-data  20   0  382808  11584   3672 R   0.0  0.1   2:27.99 apache2
  500 root      20   0   15260    636    412 S   0.0  0.0   0:00.08 upstart-socket-
  545 root      20   0   10224   2900    608 S   0.0  0.0   0:00.00 dhclient
  715 message+  20   0   39204   1220    840 S   0.0  0.0   0:00.09 dbus-daemon
  760 root      20   0   43448   1784   1432 S   0.0  0.0   0:00.09 systemd-logind
  797 syslog    20   0  260072   5664    984 S   0.0  0.0   0:02.93 rsyslogd
  813 root      20   0   15276    680    408 S   0.0  0.0   0:00.03 upstart-file-br
  855 www-data  20   0  382724  11508   3672 R   0.0  0.1   1:00.82 apache2
  893 root      20   0   14540    952    788 S   0.0  0.0   0:00.00 getty
  901 root      20   0   14540    940    788 S   0.0  0.0   0:00.00 getty
  908 root      20   0   14540    948    788 S   0.0  0.0   0:00.00 getty
  912 root      20   0   14540    940    788 S   0.0  0.0   0:00.00 getty
  919 root      20   0   14540    940    788 S   0.0  0.0   0:00.00 getty
  978 root      20   0   61364   3084   2412 S   0.0  0.0   0:00.32 sshd
  986 root      20   0    4368    660    512 S   0.0  0.0   0:00.00 acpid
  988 root      20   0   23656   1052    788 S   0.0  0.0   0:01.39 cron
  989 daemon    20   0   19140    160      0 S   0.0  0.0   0:00.00 atd
 1030 www-data  20   0  387104  19468   8868 D   0.0  0.1   2:26.43 apache2
 1031 www-data  20   0  388484  22160  10088 R   0.0  0.1   2:19.39 apache2
 1043 www-data  20   0  382864  11532   3668 D   0.0  0.1   2:28.12 apache2
 1140 root      20   0  380920  16484  10528 S   0.0  0.1   0:07.19 apache2
 1141 www-data  20   0  382620  11468   3636 D   0.0  0.1   0:40.11 apache2
 1146 www-data  20   0  385028  16380   6204 R   0.0  0.1  26:29.83 apache2
 1189 root      20   0   14540    940    788 S   0.0  0.0   0:00.00 getty
 1247 www-data  20   0  382916  11556   3640 R   0.0  0.1   1:53.05 apache2
 1308 www-data  20   0  382776  11620   3632 S   0.0  0.1   2:27.00 apache2
 1310 www-data  20   0  385688  15728   6460 R   0.0  0.1   2:26.82 apache2
 1344 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
 1349 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u9:1
 1356 www-data  20   0  382764  11408   3672 D   0.0  0.1   2:20.99 apache2
 1437 www-data  20   0  382568  11096   3316 R   0.0  0.1   0:40.78 apache2
 1627 www-data  20   0  382828  11656   3868 R   0.0  0.1   2:27.02 apache2
 1630 www-data  20   0  382724  11444   3640 R   0.0  0.1   2:27.21 apache2
 1696 www-data  20   0  382968  11600   3676 R   0.0  0.1   2:19.97 apache2
 1710 www-data  20   0  382868  11396   3572 R   0.0  0.1   2:27.08 apache2
 1768 www-data  20   0  382664  11512   3672 R   0.0  0.1   2:26.84 apache2
 1769 www-data  20   0  387048  19068   8532 R   0.0  0.1   2:27.80 apache2
 1770 www-data  20   0  384632  14504   6440 R   0.0  0.1   2:26.87 apache2
 1773 www-data  20   0  382740  11464   3632 R   0.0  0.1   2:26.66 apache2
 2081 www-data  20   0  385636  15768   6644 D   0.0  0.1   2:27.82 apache2
 2090 www-data  20   0  384404  14388   6600 R   0.0  0.1   2:27.45 apache2
 2169 www-data  20   0  385748  18612   9220 R   0.0  0.1   1:53.52 apache2
 2237 www-data  20   0  386064  18676   8964 R   0.0  0.1   2:28.12 apache2
 2247 www-data  20   0  382780  11464   3640 R   0.0  0.1   2:26.82 apache2
 2327 www-data  20   0  382724  11256   3640 D   0.0  0.1   2:26.41 apache2
 2377 www-data  20   0  385512  15748   6656 R   0.0  0.1   2:20.36 apache2
 2401 www-data  20   0  382744  11592   3636 D   0.0  0.1   2:20.36 apache2
 2420 www-data  20   0  382724  11564   3628 R   0.0  0.1   2:27.27 apache2
 2495 www-data  20   0  382944  11264   3320 R   0.0  0.1   2:27.43 apache2
 2496 www-data  20   0  382752  11320   3680 R   0.0  0.1   2:19.48 apache2
 2499 www-data  20   0  384192  16980   9272 R   0.0  0.1   2:20.70 apache2
 2501 www-data  20   0  382724  11392   3708 D   0.0  0.1   2:27.74 apache2
 2833 www-data  20   0  382000  10300   3240 D   0.0  0.1   0:00.05 apache2
 3422 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0
 3818 www-data  20   0  387124  20492   9936 D   0.0  0.1  19:50.05 apache2
 3901 www-data  20   0  382772  11408   3640 D   0.0  0.1   2:16.61 apache2
 4209 www-data  20   0  383700  13016   4284 D   0.0  0.1   3:39.11 apache2
 4535 www-data  20   0  384720  15100   5232 D   0.0  0.1   6:19.43 apache2
 5387 www-data  20   0  384536  14008   4540 R   0.0  0.1  19:05.52 apache2
 6260 www-data  20   0  385036  15312   5124 D   0.0  0.1  18:48.90 apache2
 6319 www-data  20   0  384488  15080   5444 R   0.0  0.1  18:53.07 apache2
 7308 www-data  20   0  384416  14504   6664 D   0.0  0.1   1:12.19 apache2
 7458 www-data  20   0  384852  15240   5244 R   0.0  0.1  18:41.58 apache2
 7640 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:2
 8107 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0
 9115 www-data  20   0  383612  12600   4064 D   0.0  0.1   2:56.87 apache2
 9118 www-data  20   0  383720  13404   4712 R   0.0  0.1   2:49.76 apache2
 9119 www-data  20   0  383600  13080   4680 R   0.0  0.1   2:54.70 apache2
 9120 www-data  20   0  388052  21512   9800 R   0.0  0.1   2:56.13 apache2
 9123 www-data  20   0  385216  16104   7608 R   0.0  0.1   2:57.56 apache2
 9124 www-data  20   0  383472  13144   4648 R   0.0  0.1   2:55.51 apache2
 9401 www-data  20   0  383704  13412   4744 D   0.0  0.1   2:47.55 apache2
 9651 www-data  20   0  382872  11512   3640 R   0.0  0.1   2:26.56 apache2
 9660 www-data  20   0  383568  13268   4672 D   0.0  0.1   2:55.21 apache2
 9712 www-data  20   0  383596  13328   4708 R   0.0  0.1   2:55.30 apache2
 9914 www-data  20   0  384400  14236   6400 D   0.0  0.1   2:20.74 apache2
 9953 www-data  20   0  384360  13820   6148 R   0.0  0.1   0:43.62 apache2
10036 www-data  20   0  382896  11468   3572 R   0.0  0.1   0:29.71 apache2
10102 www-data  20   0  383884  13404   4632 D   0.0  0.1   2:53.92 apache2
10107 www-data  20   0  385316  16036   7404 R   0.0  0.1   2:55.37 apache2
10231 www-data  20   0  382836  11288   3572 R   0.0  0.1   2:27.48 apache2
10258 www-data  20   0  382888  11488   3640 R   0.0  0.1   2:26.50 apache2
10450 www-data  20   0  383476  13184   4628 D   0.0  0.1   2:54.34 apache2
10521 www-data  20   0  382688  11504   3608 R   0.0  0.1   2:25.78 apache2
10535 www-data  20   0  382804  11372   3572 R   0.0  0.1   2:19.09 apache2
10552 www-data  20   0  382916  11552   3676 D   0.0  0.1   2:26.65 apache2
10577 www-data  20   0  382744  11464   3672 D   0.0  0.1   2:27.09 apache2
10695 www-data  20   0  385292  18712  10116 R   0.0  0.1   2:46.92 apache2
10868 www-data  20   0  382716  11564   3636 D   0.0  0.1   2:27.53 apache2
10871 www-data  20   0  387064  19544   8980 D   0.0  0.1   2:26.19 apache2
10930 www-data  20   0  382800  11572   3680 D   0.0  0.1   2:26.64 apache2
10999 www-data  20   0  383640  13312   4700 R   0.0  0.1   2:55.09 apache2
11001 www-data  20   0  383728  13388   4648 R   0.0  0.1   2:55.43 apache2
12130 www-data  20   0  384856  15268   5268 R   0.0  0.1  17:46.95 apache2
12398 root      20   0  105624   4244   3264 S   0.0  0.0   0:00.02 sshd
12445 ubuntu    20   0  107040   3724   1408 S   0.0  0.0   0:02.82 sshd
12448 ubuntu    20   0   21448   3880   1752 S   0.0  0.0   0:00.11 bash
12684 root      20   0   67896   2188   1692 S   0.0  0.0   0:00.00 sudo
12685 root      20   0   63248   1772   1324 S   0.0  0.0   0:00.00 su
12686 root      20   0   19904   2268   1652 S   0.0  0.0   0:00.19 bash
13629 root      20   0  100696   2756    844 S   0.0  0.0   0:01.79 sendmail-mta
14944 root      20   0  105628   4212   3236 S   0.0  0.0   0:00.02 sshd
15517 www-data  20   0  382700  11284   3628 R   0.0  0.1   0:15.08 apache2
15808 ubuntu    20   0  105768   1896    908 S   0.0  0.0   0:00.00 sshd
15869 ubuntu    20   0   12824    896    732 S   0.0  0.0   0:00.13 sftp-server
16229 www-data  20   0  384904  14988   5196 D   0.0  0.1  16:59.57 apache2
16993 www-data  20   0  385060  15460   5256 D   0.0  0.1  16:50.35 apache2
17313 www-data  20   0  386176  20588  11100 R   0.0  0.1  16:54.37 apache2
18157 www-data  20   0  387512  21256  10240 D   0.0  0.1  16:33.65 apache2
18346 www-data  20   0  384760  15016   5112 R   0.0  0.1  16:30.36 apache2
18649 www-data  20   0  382760  11380   3660 D   0.0  0.1   0:18.99 apache2
19523 www-data  20   0  387244  20932  10576 D   0.0  0.1  16:21.19 apache2
20130 www-data  20   0  384644  14960   5160 D   0.0  0.1  16:20.18 apache2
20543 www-data  20   0  384756  15008   5112 R   0.0  0.1  16:09.03 apache2
21045 www-data  20   0  386752  18860   8488 R   0.0  0.1  16:07.26 apache2
21082 www-data  20   0  385224  15176   6628 D   0.0  0.1   2:09.60 apache2
21618 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:2
21790 www-data  20   0  384812  14916   5232 R   0.0  0.1  16:01.20 apache2
22480 root      20   0  105624   4252   3268 S   0.0  0.0   0:00.02 sshd
22527 ubuntu    20   0  105756   2392   1376 S   0.0  0.0   0:00.53 sshd
22528 root      20   0  105628   4196   3224 S   0.0  0.0   0:00.02 sshd
22529 ubuntu    20   0   21448   3884   1752 S   0.0  0.0   0:00.09 bash
22593 ubuntu    20   0  105628   1900    916 S   0.0  0.0   0:00.00 sshd
22594 ubuntu    20   0   12824    904    732 S   0.0  0.0   0:00.00 sftp-server
23135 www-data  20   0  384872  15220   5208 R   0.0  0.1  15:50.77 apache2
23143 www-data  20   0  384956  16024   5956 R   0.0  0.1  15:52.45 apache2
23492 www-data  20   0  384812  15088   5132 D   0.0  0.1  15:49.15 apache2
23738 www-data  20   0  384996  15276   5136 S   0.0  0.1  15:46.36 apache2
24200 www-data  20   0  382832  11456   3628 R   0.0  0.1   0:59.09 apache2
24382 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u8:2
25885 www-data  20   0  382724  11572   3736 R   0.0  0.1   2:05.44 apache2
26132 root      20   0   67896   2188   1692 S   0.0  0.0   0:00.00 sudo
26136 root      20   0   63248   1776   1328 S   0.0  0.0   0:00.00 su
26140 root      20   0   19904   2324   1708 S   0.0  0.0   0:00.80 bash
27438 www-data  20   0  382576  11444   3660 D   0.0  0.1   0:35.58 apache2
28172 www-data  20   0  382784  11524   3740 D   0.0  0.1   1:22.91 apache2
29053 root      20   0  105628   4216   3232 S   0.0  0.0   0:00.06 sshd
29224 ubuntu    20   0  105768   1896    908 S   0.0  0.0   0:00.11 sshd
29225 ubuntu    20   0   12824    912    736 S   0.0  0.0   0:01.37 sftp-server
30586 www-data  20   0  382716  11332   3660 R   0.0  0.1   0:49.10 apache2
31373 www-data  20   0  389136  22400   9872 D   0.0  0.1   4:22.78 apache2
31384 www-data  20   0  384804  15932   5980 R   0.0  0.1   4:26.51 apache2
31387 www-data  20   0  384604  14100   4640 D   0.0  0.1   4:26.96 apache2
31475 www-data  20   0  382688  11472   3640 R   0.0  0.1   1:29.18 apache2
31601 www-data  20   0  384628  14888   5108 R   0.0  0.1   4:25.13 apache2
31680 www-data  20   0  384888  15204   5172 R   0.0  0.1   4:19.55 apache2
31693 www-data  20   0  382768  11556   3660 R   0.0  0.1   1:39.35 apache2
31696 www-data  20   0  384620  14036   4500 D   0.0  0.1   4:27.11 apache2
31727 www-data  20   0  385004  15368   5184 R   0.0  0.1   4:18.81 apache2
31733 www-data  20   0  386972  18212   7912 R   0.0  0.1   4:20.18 apache2
31958 www-data  20   0  382908  11460   3628 R   0.0  0.1   1:39.05 apache2
32535 www-data  20   0  385224  15856   7308 R   0.0  0.1   2:12.61 apache2

```

I am not completely new to linux but still need some suggestions.
thanks.

---

### Post by patsev-anton on 2014-07-12
[LIST]
[*]iotop (showing I/O on the system)
[*]netstat -t (showing connections)
[*]lsof -p 3672, 5200, 5200
[/LIST]

[Thread: Troubleshooting high server loads on Linux servers]("http://forums.cpanel.net/f34/troubleshooting-high-server-loads-linux-servers-319352.html")

---

### Post by nos09 on 2014-07-12
iotop
```
Total DISK READ :       0.00 B/s | Total DISK WRITE :       0.00 B/s
Actual DISK READ:       0.00 B/s | Actual DISK WRITE:       0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND
20964 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  9.09 % apache2 -k start
22528 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % sshd: ubuntu [priv]
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/0:0H]
15878 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
    7 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcu_sched]
    8 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/0]
    9 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/1]
   10 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/2]
   11 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/3]
   12 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcu_bh]
   13 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/0]
   14 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/1]
   15 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/2]
   16 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/3]
   17 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/0]
   18 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/0]
   19 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/1]
   20 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/1]
   21 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/1]
   23 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:0H]
   24 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/2]
   25 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/2]
   26 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/2]
   28 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/2:0H]
   29 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/3]
   30 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/3]
   31 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/3]
   33 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/3:0H]
   34 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khelper]
   35 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kdevtmpfs]
   36 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [netns]
   37 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [xenwatch]
   38 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [xenbus]
   39 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [writeback]
   40 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kintegrityd]
   41 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [bioset]
   42 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u9:0]
   43 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kblockd]
   44 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:1]
   45 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ata_sff]
   46 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khubd]
   47 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [md]
   48 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [devfreq_wq]
   49 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/2:1]
21042 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
   51 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khungtaskd]
   52 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kswapd0]
   53 be/5 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksmd]
   54 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [fsnotify_mark]
   55 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ecryptfs-kthrea]
   56 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [crypto]
21049 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21050 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
   95 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/0:1]
32428 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21055 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21056 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
22593 be/4 ubuntu      0.00 B/s    0.00 B/s  0.00 %  0.00 % sshd: ubuntu@notty
22594 be/4 ubuntu      0.00 B/s    0.00 B/s  0.00 %  0.00 % sftp-server
   68 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthrotld]
   69 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u8:1]
   70 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khvcd]
16173 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
11447 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  525 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
26296 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16224 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
   89 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [deferwq]
   90 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [charger_manager]
 8287 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
10113 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 1123 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1124 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1125 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1126 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
23655 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 1128 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1129 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1130 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1127 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1132 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 5742 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u8:0]
 6255 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16200 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
16147 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
 1140 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 4213 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16233 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
26132 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % sudo su
23163 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
26140 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % bash
 1152 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1153 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1154 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1131 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
15980 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
20619 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16218 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
20623 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16180 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 5265 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5267 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 6804 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  149 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/3:1]
 5270 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5271 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5272 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
14326 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/3:0]
 5274 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20079 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16188 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
21149 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21150 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5279 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5281 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5285 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5286 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5287 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
15900 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 8362 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21046 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  500 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % upstart-socket-bridge --daemon
25885 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5296 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21169 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 5299 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  693 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16054 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
 5303 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16056 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
 5305 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
24251 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21182 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  191 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [jbd2/xvda1-8]
  192 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ext4-rsv-conver]
16027 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
  545 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % dhclient -1 -v -pf /run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases eth0
16220 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
  715 be/4 messageb    0.00 B/s    0.00 B/s  0.00 %  0.00 % dbus-daemon --system --fork
18639 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21027 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21208 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21028 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16176 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
25295 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 1349 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u9:1]
16098 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
22529 be/4 ubuntu      0.00 B/s    0.00 B/s  0.00 %  0.00 % -bash
21030 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 1205 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
21031 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  893 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % getty -8 38400 tty4
21032 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16114 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
21238 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21033 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  760 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % systemd-logind
 5290 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21034 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
17662 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 3712 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 7426 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21035 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
10500 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16135 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
21036 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16215 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 7947 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16137 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
12333 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/2:0]
16144 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
 5905 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 1155 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
21038 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21252 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16089 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
26136 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % su
16175 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16156 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
  797 be/4 syslog      0.00 B/s    0.00 B/s  0.00 %  0.00 % rsyslogd
21278 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16159 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
  800 be/4 syslog      0.00 B/s    0.00 B/s  0.00 %  0.00 % rsyslogd [in:imuxsock]
21040 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  802 be/4 syslog      0.00 B/s    0.00 B/s  0.00 %  0.00 % rsyslogd [rs:main Q:Reg]
16164 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
21041 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  988 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % cron
16170 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
  813 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % upstart-file-bridge --daemon
 5278 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21295 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21296 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16177 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
 6962 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21043 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20788 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 6965 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16182 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
16183 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16184 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % python /usr/sbin/iotop -n 1 -b
21044 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
13854 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20796 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:2]
20797 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16191 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1344 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kauditd]
16193 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16194 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
20803 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20804 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20805 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
27974 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20807 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 7427 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16201 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
14666 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16204 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16206 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 1068 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16208 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
21048 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 6994 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 6995 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16212 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
16213 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
  342 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % upstart-udev-bridge --daemon
16185 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16216 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16214 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16219 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
  348 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % systemd-udevd --daemon
16186 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
 7006 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16223 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
26464 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20833 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16226 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16174 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16229 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16230 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16231 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
16232 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
 5297 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16234 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
16235 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16236 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
16237 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
13629 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % sendmail: MTA: rejecting connections on daemon MSP-v4: load average: 148
 5268 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20860 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
14717 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16021 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
 1189 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % getty -8 38400 tty1
16158 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
20867 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  901 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % getty -8 38400 tty5
20871 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20875 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  908 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % getty -8 38400 tty2
20877 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  912 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % getty -8 38400 tty3
27026 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  919 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % getty -8 38400 tty6
 7191 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 2855 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20891 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20892 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
21317 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20896 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20899 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20900 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20905 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20906 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16023 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
20910 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  986 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % acpid -c /etc/acpi/events -s /var/run/acpid.socket
20913 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20915 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
28614 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20917 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20918 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20919 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20920 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20921 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20922 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20924 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20926 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20928 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 6081 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20930 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20931 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
17654 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20934 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16033 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
20939 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 8652 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/0:2]
20941 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20942 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20943 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
22480 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % sshd: ubuntu [priv]
  978 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % sshd -D
20951 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20953 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20954 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16178 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
20956 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
  989 be/4 daemon      0.00 B/s    0.00 B/s  0.00 %  0.00 % atd
 4575 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20960 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20962 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20963 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20965 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16209 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
20968 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20969 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
23018 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16210 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
20975 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
20977 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16211 ?err {none}      0.00 B/s    0.00 B/s  0.00 %  0.00 % {no such process}
20980 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
 8182 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
12280 be/4 www-data    0.00 B/s    0.00 B/s  0.00 %  0.00 % apache2 -k start
16130 be/4 mysql       0.00 B/s    0.00 B/s  0.00 %  0.00 % mysqld
  801 be/4 syslog      0.00 B/s    0.00 B/s  0.00 %  0.00 % rsyslogd [in:imklog]
22527 be/4 ubuntu      0.00 B/s    0.00 B/s  0.00 %  0.00 % sshd: ubuntu@pts/2

```

netstat -t #there are 22983 lines like these 

```

tcp6       0      0 ip-myip.ec2:http ec2-remoteip:53280 TIME_WAIT

```


as for lsof - there are no pids by that number. (?)

---

### Post by Doug S on 2014-07-13
Please note that load average includes pending processes. I think your very high load average includes the large queue of requests, typical with these load type tests. Your extremely large connection table is also due to the same thing. Notice that it becomes more reasonable about a minute or two after your test. If you want to do some performance tuning on your apache web server perhaps [the apache documentation]("http://httpd.apache.org/docs/2.2/misc/perf-tuning.html") on the subject can help.

---

### Post by SeijiSensei on 2014-07-13
Do you have any evidence that this server will face the same high loads in production?  Those load averages are absurdly high.  To give some context, sendmail stops accepting mail when the load average breaks 12.  

Also, since this looks like a web application with an SQL backend, have you analyzed all the queries the application uses to make sure you have all the correct indexes created in the database?  Nothing slows down SQL queries faster than complex joins with poor indexing.  Use the DB's ANALYZE function to see where the bottlenecks might lay.

---

### Post by tgalati4 on 2014-07-13
It could be an IP4 versus IP6 issue.  Is your router set up correctly to handle IP6?  I would turn off IP6 and rerun your tests and see if the load changes.  If it does, then start to look at IP6 configuration.

---

### Post by nos09 on 2014-07-13
IP6 is turned off. And its an amazon instance. 
I am looking at the documentation of apache as Doug S mentioned. 
And then will try sql tuning.
will report soon.

Thank you guys for quick replays.

---

