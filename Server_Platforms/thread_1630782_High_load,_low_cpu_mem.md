---
title: "High load, low cpu mem"
date: 2010-11-25
forum: Server Platforms
---

### Post by ChrisWiegman on 2010-11-25
Hi all,

I'm perplexed. I upgraded my 10.04 LAMP stack to PHP 5.3 a few weeks ago (it had previously been downgraded to 5.2). Since about that time I've been have excessively high load numbers with almost 0 CPU/Mem usage. Any thoughts on a reason for this?

This is a dell quad core server with 8GB of ram. Prior to a few weeks ago high server load was .2 - .4. Now it never drops below .6. I'm not sure if this is related to the PHP upgrade or coincidental. Here's some output below. Any thoughts would be greatly appreciated.

output from top:

> top - 15:47:15 up 19 min,  1 user,  load average: 0.78, 0.68, 0.46
Tasks: 128 total,   1 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.2%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8189552k total,  1041584k used,  7147968k free,    30804k buffers
Swap: 11595768k total,        0k used, 11595768k free,   449660k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 4202 adminofs  20   0 19224 1424 1064 R    1  0.0   0:01.11 top                                                                                                                 
 1438 root      20   0 31696 1024  636 D    0  0.0   0:00.18 apcupsd    

output from free -m

> adminofsite@ws199144:/var/log$ free -m
             total       used       free     shared    buffers     cached
Mem:          7997       1021       6976          0         30        442
-/+ buffers/cache:        548       7448
Swap:        11323          0      11323
adminofsite@ws199144:/var/log$ 

output of ps -aux

> USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23712  1940 ?        Ss   15:27   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    15:27   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    15:27   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    15:27   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    15:27   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    15:27   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    15:27   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    15:27   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    15:27   0:00 [migration/2]
root        10  0.0  0.0      0     0 ?        S    15:27   0:00 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S    15:27   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S    15:27   0:00 [migration/3]
root        13  0.0  0.0      0     0 ?        S    15:27   0:00 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S    15:27   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S    15:27   0:00 [events/0]
root        16  0.0  0.0      0     0 ?        S    15:27   0:00 [events/1]
root        17  0.0  0.0      0     0 ?        S    15:27   0:00 [events/2]
root        18  0.0  0.0      0     0 ?        S    15:27   0:00 [events/3]
root        19  0.0  0.0      0     0 ?        S    15:27   0:00 [cpuset]
root        20  0.0  0.0      0     0 ?        S    15:27   0:00 [khelper]
root        21  0.0  0.0      0     0 ?        S    15:27   0:00 [netns]
root        22  0.0  0.0      0     0 ?        S    15:27   0:00 [async/mgr]
root        23  0.0  0.0      0     0 ?        S    15:27   0:00 [pm]
root        25  0.0  0.0      0     0 ?        S    15:27   0:00 [sync_supers]
root        26  0.0  0.0      0     0 ?        S    15:27   0:00 [bdi-default]
root        27  0.0  0.0      0     0 ?        S    15:27   0:00 [kintegrityd/0]
root        28  0.0  0.0      0     0 ?        S    15:27   0:00 [kintegrityd/1]
root        29  0.0  0.0      0     0 ?        S    15:27   0:00 [kintegrityd/2]
root        30  0.0  0.0      0     0 ?        S    15:27   0:00 [kintegrityd/3]
root        31  0.0  0.0      0     0 ?        S    15:27   0:00 [kblockd/0]
root        32  0.0  0.0      0     0 ?        S    15:27   0:00 [kblockd/1]
root        33  0.0  0.0      0     0 ?        S    15:27   0:00 [kblockd/2]
root        34  0.0  0.0      0     0 ?        S    15:27   0:00 [kblockd/3]
root        35  0.0  0.0      0     0 ?        S    15:27   0:00 [kacpid]
root        36  0.0  0.0      0     0 ?        S    15:27   0:00 [kacpi_notify]
root        37  0.0  0.0      0     0 ?        S    15:27   0:00 [kacpi_hotplug]
root        38  0.0  0.0      0     0 ?        S    15:27   0:00 [ata/0]
root        39  0.0  0.0      0     0 ?        S    15:27   0:00 [ata/1]
root        40  0.0  0.0      0     0 ?        S    15:27   0:00 [ata/2]
root        41  0.0  0.0      0     0 ?        S    15:27   0:00 [ata/3]
root        42  0.0  0.0      0     0 ?        S    15:27   0:00 [ata_aux]
root        43  0.0  0.0      0     0 ?        S    15:27   0:00 [ksuspend_usbd]
root        44  0.0  0.0      0     0 ?        S    15:27   0:00 [khubd]
root        45  0.0  0.0      0     0 ?        S    15:27   0:00 [kseriod]
root        46  0.0  0.0      0     0 ?        S    15:27   0:00 [kmmcd]
root        51  0.0  0.0      0     0 ?        S    15:27   0:00 [khungtaskd]
root        52  0.0  0.0      0     0 ?        S    15:27   0:00 [kswapd0]
root        53  0.0  0.0      0     0 ?        SN   15:27   0:00 [ksmd]
root        54  0.0  0.0      0     0 ?        S    15:27   0:00 [aio/0]
root        55  0.0  0.0      0     0 ?        S    15:27   0:00 [aio/1]
root        56  0.0  0.0      0     0 ?        S    15:27   0:00 [aio/2]
root        57  0.0  0.0      0     0 ?        S    15:27   0:00 [aio/3]
root        58  0.0  0.0      0     0 ?        S    15:27   0:00 [ecryptfs-kthrea]
root        59  0.0  0.0      0     0 ?        S    15:27   0:00 [crypto/0]
root        60  0.0  0.0      0     0 ?        S    15:27   0:00 [crypto/1]
root        61  0.0  0.0      0     0 ?        S    15:27   0:00 [crypto/2]
root        62  0.0  0.0      0     0 ?        S    15:27   0:00 [crypto/3]
root        65  0.0  0.0      0     0 ?        S    15:27   0:00 [scsi_eh_0]
root        66  0.0  0.0      0     0 ?        S    15:27   0:00 [scsi_eh_1]
root        68  0.0  0.0      0     0 ?        S    15:27   0:00 [kstriped]
root        69  0.0  0.0      0     0 ?        S    15:27   0:00 [kmpathd/0]
root        70  0.0  0.0      0     0 ?        S    15:27   0:00 [kmpathd/1]
root        71  0.0  0.0      0     0 ?        S    15:27   0:00 [kmpathd/2]
root        72  0.0  0.0      0     0 ?        S    15:27   0:00 [kmpathd/3]
root        73  0.0  0.0      0     0 ?        S    15:27   0:00 [kmpath_handlerd]
root        74  0.0  0.0      0     0 ?        S    15:27   0:00 [ksnapd]
root        75  0.0  0.0      0     0 ?        S    15:27   0:00 [kondemand/0]
root        76  0.0  0.0      0     0 ?        S    15:27   0:00 [kondemand/1]
root        77  0.0  0.0      0     0 ?        S    15:27   0:00 [kondemand/2]
root        78  0.0  0.0      0     0 ?        S    15:27   0:00 [kondemand/3]
root        79  0.0  0.0      0     0 ?        S    15:27   0:00 [kconservative/0]
root        80  0.0  0.0      0     0 ?        S    15:27   0:00 [kconservative/1]
root        81  0.0  0.0      0     0 ?        S    15:27   0:00 [kconservative/2]
root        82  0.0  0.0      0     0 ?        S    15:27   0:00 [kconservative/3]
root       219  0.0  0.0      0     0 ?        S    15:27   0:00 [scsi_eh_2]
root       254  0.0  0.0      0     0 ?        S    15:27   0:00 [kdmflush]
root       257  0.0  0.0      0     0 ?        S    15:27   0:00 [kdmflush]
root       271  0.0  0.0      0     0 ?        S    15:27   0:00 [jbd2/dm-0-8]
root       272  0.0  0.0      0     0 ?        S    15:27   0:00 [ext4-dio-unwrit]
root       273  0.0  0.0      0     0 ?        S    15:27   0:00 [ext4-dio-unwrit]
root       274  0.0  0.0      0     0 ?        S    15:27   0:00 [ext4-dio-unwrit]
root       275  0.0  0.0      0     0 ?        S    15:27   0:00 [ext4-dio-unwrit]
root       318  0.0  0.0  17036   972 ?        S    15:27   0:00 upstart-udev-bridge --daemon
root       339  0.0  0.0  17148  1008 ?        S<s  15:27   0:00 udevd --daemon
root       350  0.0  0.0      0     0 ?        S    15:27   0:00 [kjournald]
root       554  0.0  0.0      0     0 ?        S    15:27   0:00 [usbhid_resumer]
root       569  0.0  0.0      0     0 ?        S    15:27   0:00 [kpsmoused]
root       591  0.0  0.0      0     0 ?        S    15:27   0:00 [edac-poller]
root       605  0.0  0.0  17144   900 ?        S<   15:27   0:00 udevd --daemon
root       612  0.0  0.0  17144   864 ?        S<   15:27   0:00 udevd --daemon
syslog     725  0.0  0.0 126100  1752 ?        Sl   15:27   0:00 rsyslogd -c4
106        745  0.0  0.0  23524   896 ?        Ss   15:27   0:00 dbus-daemon --system --fork
root       860  0.0  0.0   6080   648 tty4     Ss+  15:27   0:00 /sbin/getty -8 38400 tty4
root       864  0.0  0.0   6080   648 tty5     Ss+  15:27   0:00 /sbin/getty -8 38400 tty5
root       875  0.0  0.0   6080   648 tty2     Ss+  15:27   0:00 /sbin/getty -8 38400 tty2
root       876  0.0  0.0   6080   648 tty3     Ss+  15:27   0:00 /sbin/getty -8 38400 tty3
root       879  0.0  0.0   6080   648 tty6     Ss+  15:27   0:00 /sbin/getty -8 38400 tty6
root       885  0.0  0.0  21076  1032 ?        Ss   15:27   0:00 cron
daemon     886  0.0  0.0  18884   460 ?        Ss   15:27   0:00 atd
root       887  0.0  0.0   4032   684 ?        Ss   15:27   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       910  0.0  0.0  11284   628 ?        Ss   15:27   0:00 /usr/sbin/irqbalance
root       959  0.0  0.2 102500 17624 ?        Ss   15:27   0:00 /usr/sbin/apache2 -k start
www-data   976  0.0  0.0 101596  3436 ?        S    15:27   0:00 /usr/sbin/apache2 -k start
root       977  0.0  0.0      0     0 ?        S    15:27   0:00 [bond0]
www-data   984  0.0  0.1 448956  8352 ?        Sl   15:27   0:00 /usr/sbin/apache2 -k start
www-data   985  0.0  0.1 448868  8296 ?        Sl   15:27   0:00 /usr/sbin/apache2 -k start
root      1058  0.0  0.0      0     0 ?        S    15:27   0:00 [flush-251:0]
root      1415  0.0  0.0  37208  2248 ?        Ss   15:27   0:00 /usr/lib/postfix/master
postfix   1430  0.0  0.0  39272  2184 ?        S    15:27   0:00 pickup -l -t fifo -u -c
postfix   1431  0.0  0.0  39432  2228 ?        S    15:27   0:00 qmgr -l -t fifo -u
root      1432  0.0  0.0  49260  1092 ?        Ss   15:27   0:00 /usr/sbin/sshd
root      1438  0.0  0.0  31696  1024 ?        Ssl  15:27   0:00 /sbin/apcupsd
root      1472  0.0  0.0   6080   648 tty1     Ss+  15:27   0:00 /sbin/getty -8 38400 tty1
1003      2311  0.8  1.2 1269500 100648 ?      S    15:27   0:10 /usr/lib/cgi-bin/php5
root      2531  0.0  0.0 120460  3560 ?        Sl   15:27   0:00 /usr/sbin/console-kit-daemon --no-daemon
wpadmin   2776  0.0  0.6 1254088 51196 ?       S    15:27   0:00 /usr/lib/cgi-bin/php5
1003      2801  0.1  1.1 1281212 97368 ?       S    15:27   0:01 /usr/lib/cgi-bin/php5
1003      2819  0.1  0.9 1264844 81384 ?       S    15:29   0:01 /usr/lib/cgi-bin/php5
1013      2830  0.0  0.5 1249288 47868 ?       S    15:30   0:00 /usr/lib/cgi-bin/php5
crmadmin  2831  0.0  0.3 1239896 30388 ?       S    15:30   0:00 /usr/lib/cgi-bin/php5
mysql     2845  0.2  0.7 1014712 63632 ?       Ssl  15:31   0:02 /usr/sbin/mysqld
phpadmin  4014  0.0  0.2 1236152 24496 ?       S    15:32   0:00 /usr/lib/cgi-bin/php5
arcadmin  4020  0.0  0.5 1249244 47828 ?       S    15:33   0:00 /usr/lib/cgi-bin/php5
root      4022  0.0  0.0  79108  3476 ?        Ss   15:35   0:00 sshd: adminofsite [priv]
1000      4096  0.0  0.0  79108  1680 ?        S    15:35   0:00 sshd: adminofsite@pts/0
1000      4097  0.0  0.0  21144  3968 pts/0    Ss   15:35   0:00 -bash
ddawg     4145  0.0  0.6 1246204 50288 ?       S    15:38   0:00 /usr/lib/cgi-bin/php5
1000      4210  0.0  0.0  15256  1208 pts/0    R+   15:48   0:00 ps -aux

output from iostat
> Linux 2.6.32-26-server (ws199144)       11/25/2010      _x86_64_        (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.57    0.00    0.17    0.35    0.00   98.91

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
scd0              0.02         0.15         0.00        304          0
sda               8.30       267.34        75.07     533412     149780
dm-0             18.46       266.08        75.05     530898     149752
dm-1              0.06         0.45         0.00        904          0

---

### Post by Vegan on 2010-11-25
Reboot the server and see if that helps

I have seen a high load and a reboot cleared that right up

---

### Post by ChrisWiegman on 2010-11-25
Tried it first ;) 

I'm suspecting part of the RAID array might be failing, but, due to the infinite wisdom of my employer, I have no access to confirm my suspicion until Monday.

---

### Post by NightwishFan on 2010-11-25
I always have high loads like that on Ubuntu and Fedora. Debian on some releases does as well, though usually it is around 0.00 0.00 0.00. I am quite sure the real load is not this high, as my machine is near idle and my current load is: 0.35, 0.34, 0.26 (usually higher) so I suspect a kernel option such as optimize for size?

---

### Post by SeijiSensei on 2010-11-26
Why are you running PHP5 as a cgi-bin rather than using the Apache module?  I suspect the module does a better job managing shared resources across its children.

@NightwishFan
Any machine running X Windows has a non-zero load most of the time, but I don't see any GUI running in the OP's task list.  

In general, machines with a load average under 2 or 3 perform fine.  (Running a GUI on an older machine will often display an average > 1, with nearly all of that being X and related software.)  It's when the load average goes above 10 or 12 that things really bog down.  I've had machines hit the twenties when something "bad" happens.  Usually it's the result of massive disk thrashing.

---

