---
title: "Higher Load Than Expected"
date: 2011-01-24
forum: Server Platforms
---

### Post by Nextraztus on 2011-01-24
Hello -

Recently (Saturday at 1am) I rebooted my Ubuntu Server 10.04 for updates and such; prior to this reboot, my server load (all three averages) were rarely over figures ~0.10 except during some cron jobs that do some heavy-duty processing.

I noticed today that I've been averaging 1.00+. I looked at my cacti graphs and it's been this way since almost exactly when I rebooted. This server is a quad-core xenon (2.33Ghz) so I find it hard to believe that one core is at capacity.

Thanks in advance!
-Nex

```
user@WEB02:~$ sudo uptime
 10:22:46 up 2 days,  9:22,  2 users,  load average: 0.99, 0.98, 0.92
```

I've dug through as many logs as I can and I see nothing unusual. I can't find anything unusual in ps/vmstat/top as well.  I've scheduled another reboot for tonight in hopes it will fix the issues, but in the meantime I'm extremely curious in what other tools I can use to figure out the higher-than-usual load.

Output of sudo ps aux
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23712  1956 ?        Ss   Jan22   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Jan22   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Jan22   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    Jan22   0:01 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    Jan22   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    Jan22   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    Jan22   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    Jan22   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    Jan22   0:00 [migration/2]
root        10  0.0  0.0      0     0 ?        S    Jan22   0:03 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S    Jan22   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S    Jan22   0:00 [migration/3]
root        13  0.0  0.0      0     0 ?        S    Jan22   0:12 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S    Jan22   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S    Jan22   0:00 [events/0]
root        16  0.0  0.0      0     0 ?        S    Jan22   0:00 [events/1]
root        17  0.0  0.0      0     0 ?        S    Jan22   0:00 [events/2]
root        18  0.0  0.0      0     0 ?        S    Jan22   0:00 [events/3]
root        19  0.0  0.0      0     0 ?        S    Jan22   0:00 [cpuset]
root        20  0.0  0.0      0     0 ?        S    Jan22   0:00 [khelper]
root        21  0.0  0.0      0     0 ?        S    Jan22   0:00 [netns]
root        22  0.0  0.0      0     0 ?        S    Jan22   0:00 [async/mgr]
root        23  0.0  0.0      0     0 ?        S    Jan22   0:00 [pm]
root        25  0.0  0.0      0     0 ?        S    Jan22   0:00 [sync_supers]
root        26  0.0  0.0      0     0 ?        S    Jan22   0:00 [bdi-default]
root        27  0.0  0.0      0     0 ?        S    Jan22   0:00 [kintegrityd/0]
root        28  0.0  0.0      0     0 ?        S    Jan22   0:00 [kintegrityd/1]
root        29  0.0  0.0      0     0 ?        S    Jan22   0:00 [kintegrityd/2]
root        30  0.0  0.0      0     0 ?        S    Jan22   0:00 [kintegrityd/3]
root        31  0.0  0.0      0     0 ?        S    Jan22   0:00 [kblockd/0]
root        32  0.0  0.0      0     0 ?        S    Jan22   0:00 [kblockd/1]
root        33  0.0  0.0      0     0 ?        S    Jan22   0:00 [kblockd/2]
root        34  0.0  0.0      0     0 ?        S    Jan22   0:00 [kblockd/3]
root        35  0.0  0.0      0     0 ?        S    Jan22   0:00 [kacpid]
root        36  0.0  0.0      0     0 ?        S    Jan22   0:00 [kacpi_notify]
root        37  0.0  0.0      0     0 ?        S    Jan22   0:00 [kacpi_hotplug]
root        38  0.0  0.0      0     0 ?        S    Jan22   0:00 [ata/0]
root        39  0.0  0.0      0     0 ?        S    Jan22   0:00 [ata/1]
root        40  0.0  0.0      0     0 ?        S    Jan22   0:00 [ata/2]
root        41  0.0  0.0      0     0 ?        S    Jan22   0:00 [ata/3]
root        42  0.0  0.0      0     0 ?        S    Jan22   0:00 [ata_aux]
root        43  0.0  0.0      0     0 ?        S    Jan22   0:00 [ksuspend_usbd]
root        44  0.0  0.0      0     0 ?        S    Jan22   0:00 [khubd]
root        45  0.0  0.0      0     0 ?        S    Jan22   0:00 [kseriod]
root        46  0.0  0.0      0     0 ?        S    Jan22   0:00 [kmmcd]
root        51  0.0  0.0      0     0 ?        S    Jan22   0:00 [khungtaskd]
root        52  0.0  0.0      0     0 ?        S    Jan22   0:01 [kswapd0]
root        53  0.0  0.0      0     0 ?        SN   Jan22   0:00 [ksmd]
root        54  0.0  0.0      0     0 ?        S    Jan22   0:00 [aio/0]
root        55  0.0  0.0      0     0 ?        S    Jan22   0:00 [aio/1]
root        56  0.0  0.0      0     0 ?        S    Jan22   0:00 [aio/2]
root        57  0.0  0.0      0     0 ?        S    Jan22   0:00 [aio/3]
root        58  0.0  0.0      0     0 ?        S    Jan22   0:00 [ecryptfs-kthrea]
root        59  0.0  0.0      0     0 ?        S    Jan22   0:00 [crypto/0]
root        60  0.0  0.0      0     0 ?        S    Jan22   0:00 [crypto/1]
root        61  0.0  0.0      0     0 ?        S    Jan22   0:00 [crypto/2]
root        62  0.0  0.0      0     0 ?        S    Jan22   0:00 [crypto/3]
root        65  0.0  0.0      0     0 ?        S    Jan22   0:00 [scsi_eh_0]
root        66  0.0  0.0      0     0 ?        S    Jan22   0:00 [scsi_eh_1]
root        69  0.0  0.0      0     0 ?        S    Jan22   0:00 [kstriped]
root        70  0.0  0.0      0     0 ?        S    Jan22   0:00 [kmpathd/0]
root        71  0.0  0.0      0     0 ?        S    Jan22   0:00 [kmpathd/1]
root        72  0.0  0.0      0     0 ?        S    Jan22   0:00 [kmpathd/2]
root        73  0.0  0.0      0     0 ?        S    Jan22   0:00 [kmpathd/3]
root        74  0.0  0.0      0     0 ?        S    Jan22   0:00 [kmpath_handlerd]
root        75  0.0  0.0      0     0 ?        S    Jan22   0:00 [ksnapd]
root        76  0.0  0.0      0     0 ?        S    Jan22   0:00 [kondemand/0]
root        77  0.0  0.0      0     0 ?        S    Jan22   0:00 [kondemand/1]
root        78  0.0  0.0      0     0 ?        S    Jan22   0:00 [kondemand/2]
root        79  0.0  0.0      0     0 ?        S    Jan22   0:00 [kondemand/3]
root        80  0.0  0.0      0     0 ?        S    Jan22   0:00 [kconservative/0]
root        81  0.0  0.0      0     0 ?        S    Jan22   0:00 [kconservative/1]
root        82  0.0  0.0      0     0 ?        S    Jan22   0:00 [kconservative/2]
root        83  0.0  0.0      0     0 ?        S    Jan22   0:00 [kconservative/3]
root       251  0.0  0.0      0     0 ?        S    Jan22   0:00 [cciss_scan]
root       278  0.0  0.0      0     0 ?        S    Jan22   0:00 [usbhid_resumer]
root       282  0.0  0.0      0     0 ?        S    Jan22   0:02 [jbd2/cciss!c0d0]
root       283  0.0  0.0      0     0 ?        S    Jan22   0:00 [ext4-dio-unwrit]
root       284  0.0  0.0      0     0 ?        S    Jan22   0:00 [ext4-dio-unwrit]
root       285  0.0  0.0      0     0 ?        S    Jan22   0:00 [ext4-dio-unwrit]
root       286  0.0  0.0      0     0 ?        S    Jan22   0:00 [ext4-dio-unwrit]
root       328  0.0  0.0  16904   828 ?        S    Jan22   0:00 upstart-udev-bridge --daemon
root       342  0.0  0.0  17280  1104 ?        S<s  Jan22   0:00 udevd --daemon
root       597  0.0  0.0      0     0 ?        S    Jan22   0:02 [flush-104:0]
root       625  0.0  0.0      0     0 ?        S    Jan22   0:00 [edac-poller]
root       626  0.0  0.0      0     0 ?        S    Jan22   0:00 [kpsmoused]
syslog     648  0.0  0.0 191516  1716 ?        Sl   Jan22   0:02 rsyslogd -c4
107        657  0.0  0.0  23524   928 ?        Ss   Jan22   0:00 dbus-daemon --system --fork
root       660  0.0  0.0      0     0 ?        SN   Jan22   2:50 [kipmi0]
avahi      743  0.0  0.0  34052  1652 ?        S    Jan22   0:00 avahi-daemon: running [WEB02.local]
avahi      746  0.0  0.0  33928   576 ?        Ss   Jan22   0:00 avahi-daemon: chroot helper
root       841  0.0  0.2 116512  5296 ?        Ss   08:27   0:00 sshd: user [priv]
root       892  0.0  0.0  17276  1052 ?        S<   Jan22   0:00 udevd --daemon
user       921  0.0  0.1 116512  2232 ?        S    08:27   0:00 sshd: user@pts/0 
user       924  0.0  0.2  21328  4152 pts/0    Ss   08:27   0:00 -bash
root       934  0.0  0.0   6080   648 tty4     Ss+  Jan22   0:00 /sbin/getty -8 38400 tty4
root       939  0.0  0.0   6080   644 tty5     Ss+  Jan22   0:00 /sbin/getty -8 38400 tty5
root       947  0.0  0.0   6080   644 tty2     Ss+  Jan22   0:00 /sbin/getty -8 38400 tty2
root       948  0.0  0.0   6080   648 tty3     Ss+  Jan22   0:00 /sbin/getty -8 38400 tty3
root       951  0.0  0.0   6080   644 tty6     Ss+  Jan22   0:00 /sbin/getty -8 38400 tty6
daemon     959  0.0  0.0  18884   464 ?        Ss   Jan22   0:00 atd
root       960  0.0  0.0  21076  1016 ?        Ss   Jan22   0:00 cron
root       971  0.0  0.0  11284   624 ?        Ss   Jan22   0:09 /usr/sbin/irqbalance
mysql      996  0.0  2.9 260792 60984 ?        Ssl  Jan22   1:41 /usr/sbin/mysqld
root      1112  0.0  0.1  37208  2252 ?        Ss   Jan22   0:00 /usr/lib/postfix/master
snmp      1135  0.0  0.2  47644  4956 ?        S    Jan22   0:21 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1
root      1152  0.0  0.0  65792  1888 ?        Ss   Jan22   0:00 /usr/sbin/winbindd
root      1167  0.0  0.0  65900  1688 ?        S    Jan22   0:00 /usr/sbin/winbindd
root      1176  0.0  0.1  75408  3200 ?        Ss   Jan22   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1246  0.0  0.0   6080   644 tty1     Ss+  Jan22   0:00 /sbin/getty -8 38400 tty1
root      1261  0.0  0.0  49260  1080 ?        Ss   Jan22   0:00 /usr/sbin/sshd
postfix   1282  0.0  0.1  39432  2360 ?        S    Jan22   0:00 qmgr -l -t fifo -u
www-data  1451  0.1  0.2  99416  5836 ?        S    08:47   0:06 /usr/sbin/lighttpd -f /etc/lighttpd/lighttpd.conf
www-data  1453  0.0  0.4 152888  9936 ?        Ss   08:47   0:00 /usr/bin/php-cgi
www-data  1455  0.0  1.3 171836 26772 ?        S    08:47   0:02 /usr/bin/php-cgi
www-data  1456  0.0  1.3 171572 26960 ?        S    08:47   0:01 /usr/bin/php-cgi
www-data  1457  0.0  1.2 170616 25628 ?        S    08:47   0:01 /usr/bin/php-cgi
www-data  1458  0.0  1.2 173724 25460 ?        S    08:47   0:00 /usr/bin/php-cgi
www-data  1459  0.0  0.4 152888  9936 ?        Ss   08:47   0:00 /usr/bin/php-cgi
www-data  1461  0.4  1.3 175424 27408 ?        S    08:47   0:28 /usr/bin/php-cgi
www-data  1462  0.5  1.3 174748 27060 ?        S    08:47   0:30 /usr/bin/php-cgi
www-data  1463  0.5  1.2 173724 25688 ?        S    08:47   0:29 /usr/bin/php-cgi
www-data  1464  0.5  1.3 175136 27664 ?        S    08:47   0:30 /usr/bin/php-cgi
root      1549  0.0  0.0  17184   952 ?        S<   Jan22   0:00 udevd --daemon
root      1550  0.0  0.0      0     0 ?        S<   Jan22   0:00 [kslowd000]
root      1553  0.0  0.0      0     0 ?        S<   Jan22   0:00 [kslowd001]
root      1561  0.0  0.0      0     0 ?        S    Jan22   0:00 [cifsd]
root      1652  0.0  0.0  65912  2052 ?        S    Jan22   0:00 /usr/sbin/winbindd
root      1654  0.0  0.1 120464  3628 ?        Sl   Jan22   0:00 /usr/sbin/console-kit-daemon --no-daemon
postfix   2097  0.0  0.1  39272  2176 ?        S    09:40   0:00 pickup -l -t fifo -u -c
root      2369  0.0  0.0  16280  1136 pts/0    S+   10:02   0:00 shutdown -r 23:59
root      2373  0.0  0.2 116512  5260 ?        Ss   10:03   0:00 sshd: user [priv]
user      2447  0.0  0.1 116512  2112 ?        S    10:03   0:00 sshd: user@pts/1 
user      2448  0.0  0.2  21316  4120 pts/1    Ss   10:03   0:00 -bash
root      3568  0.0  0.0  15256  1208 pts/1    R+   10:25   0:00 ps aux
lp       18774  0.0  0.0  12508   608 ?        Ss   Jan23   0:00 /usr/sbin/lpd -s

```

Output of top
```
top - 10:29:05 up 2 days,  9:28,  2 users,  load average: 1.00, 1.01, 0.94
Tasks: 139 total,   1 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2055340k total,  2006952k used,    48388k free,   133688k buffers
Swap:  5861368k total,        0k used,  5861368k free,  1443644k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      20   0 23712 1956 1272 S    0  0.1   0:01.02 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0
    4 root      20   0     0    0    0 S    0  0.0   0:01.92 ksoftirqd/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1
    7 root      20   0     0    0    0 S    0  0.0   0:00.71 ksoftirqd/1
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      RT   0     0    0    0 S    0  0.0   0:00.06 migration/2
   10 root      20   0     0    0    0 S    0  0.0   0:03.36 ksoftirqd/2
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2
   12 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/3
   13 root      20   0     0    0    0 S    0  0.0   0:12.09 ksoftirqd/3
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/3
   15 root      20   0     0    0    0 S    0  0.0   0:00.84 events/0
   16 root      20   0     0    0    0 S    0  0.0   0:00.48 events/1
   17 root      20   0     0    0    0 S    0  0.0   0:00.51 events/2
   18 root      20   0     0    0    0 S    0  0.0   0:00.49 events/3
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper
   21 root      20   0     0    0    0 S    0  0.0   0:00.00 netns
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 pm
   25 root      20   0     0    0    0 S    0  0.0   0:00.09 sync_supers
   26 root      20   0     0    0    0 S    0  0.0   0:00.13 bdi-default
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/2
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/3
   31 root      20   0     0    0    0 S    0  0.0   0:00.01 kblockd/0
   32 root      20   0     0    0    0 S    0  0.0   0:00.02 kblockd/1
   33 root      20   0     0    0    0 S    0  0.0   0:00.01 kblockd/2
   34 root      20   0     0    0    0 S    0  0.0   0:00.02 kblockd/3
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpid
   36 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_notify

```

Output of vmstat:
```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0  42024 133732 1450500    0    0     5     6   18   22  0  0 100  0

```

---

### Post by arrrghhh on 2011-01-24
That number is **extremely** decieving IMHO.  If you look at processor utilization, it's 100% idle.  That's what I would concern myself with - is the proc util, not the load.  Here's some articles on that CPU load metric:

[Load (Wikipedia)](http://en.wikipedia.org/wiki/Load_%28computing%29)

[Unix Load Average - How it Works](http://www.teamquest.com/resources/gunther/display/5/index.htm)

[Understanding Linux CPU Load - when should you be worried?](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages)

Enjoy!

---

### Post by Nextraztus on 2011-01-24
Normally I would agree. The server is handling requests no problem, it "shows" idle, etc.

But, whether the load metric itself is useful or not doesn't change the fact that the overall "state" of my server has changed with no apparent reason.

My biggest fear is that I somehow got rooted and some ghostly process is eating one of my cores. I had to fight to get this server at my organization and I really don't want to lose it.

I guess if it doesn't go away after tonights reboot, I'll start to worry.

---

### Post by arrrghhh on 2011-01-24
> **Nextraztus said:**
> Normally I would agree. The server is handling requests no problem, it "shows" idle, etc.

But, whether the load metric itself is useful or not doesn't change the fact that the overall "state" of my server has changed with no apparent reason.

My biggest fear is that I somehow got rooted and some ghostly process is eating one of my cores. I had to fight to get this server at my organization and I really don't want to lose it.

I guess if it doesn't go away after tonights reboot, I'll start to worry.

Read thru those articles.  They mention that 1.00 isn't necessarily pegged for a mutli-core system... if you have a quad-core system, 4.00 is technically running at full tilt.  Also, if you have an i7 proc that hyperthreads each core, 8.00 would be full tilt.  Gets even more skewed the more cores you have, as you can see...

---

### Post by Nextraztus on 2011-01-24
I've read those links, all three, many times lol. They were the first things I found before I finally broke down and asked for help. Please don't take this the wrong way that I don't appreciate the help.

The thing is, I'm used to seeing numbers (all three averages) a tenth of this. I understand that my server is not pegged-- but, it is doing *something* that it isn't showing me it's doing. THAT is the problem. Also, this is a QuadCore Xenon -- it's actually an HP-branded 1U server (not some home-built thing).

Here is the rrd from cacti. The spike near 4:00am is expected and accouted for. Also, I understand that this is a stacked chart and it's not saying my load is "3". It's saying that the sum of all my averages are 3 -- which I understand isn't the best way to look at it. It doesn't change that fact that the kernel is saying something is going on (it started when I rebooted) and I have no tools showing me correlating data.

As you can see from the Weekly averages, something unusual is going on. THAT is what I'm asking. What other tools can I use to try and figure it out, or is my scheduled reboot good enough?

[IMG]http://img23.imageshack.us/img23/9213/clipboard01he.png[/IMG]

---

### Post by arrrghhh on 2011-01-24
Holy cow... Ok, that changes things and I didn't understand that was the case from your first post.  I apologize.  After re-reading your post, not sure how I missed that!

So nothing was installed on that day other than updates?  You can certainly see a large spike from when you rebooted.  I'd say something definitely changed with the system then...

As far as tracking it down, PS should show it.  I'm not sure historically how you can look at it other than looking at the various logs to see what was installed, what happened on that day!

---

### Post by Nextraztus on 2011-01-24
The change was at 1am. Right after I rebooted from updates (I only reboot when there are security updates, which when I check when I shell in in the morning for work and the MOTD says a reboot is required.

I can't find anything strange. All I can figure is this version of the kernel has a phantom load issue. I'm running "2.6.32-27-server #49-Ubuntu SMP Thu Dec 2 02:05:21 UTC 2010 x86_64 GNU/Linux"

Or there's some weird glitch and I just need a reboot...

Or I'm rooted...

I guess I'll reboot tonight during my maintenance window and see what happens.

I did look at the apt logs and I just see the usual updates, things like apache mod-php, php, mysql, a kernel, fuse, some stuff like that. Besides, anything that comes through apt ought to show up proper in ps. I installed chkrootkit today to see if it would find anything and it didn't find anything of note either.

---

### Post by arrrghhh on 2011-01-24
I doubt you're rooted - not that it's impossible, it's just doubtful.

If you did do a kernel upgrade, perhaps there's something not playing nice.  You should still have the old kernel in GRUB, so when you reboot in that maint window can you try an older kernel?  You'll need physical access (or a DRAC, iLO, etc) so you can intervene in the boot process, but that would rule out the new kernel - which is probably the #1 culprit for odd issues such as this!

---

### Post by Nextraztus on 2011-01-24
That's not a bad suggestion (good ol' iLO).  I'll try the current one first, if it has the same problem I'll do as you suggest.

Thanks again, I forgot that it keeps the last few.

---

### Post by Nextraztus on 2011-01-25
Problem fixed itself during the reboot (still using the new kernel).

Of interesting note, on the root console there was some CIFS errors; my guess is there was something wrong with that.

---

### Post by arrrghhh on 2011-01-25
> **Nextraztus said:**
> Problem fixed itself during the reboot (still using the new kernel).

Of interesting note, on the root console there was some CIFS errors; my guess is there was something wrong with that.

Ha, well I guess I'm glad it's solved.  Always bugs me when I don't know the actual root cause of the issue, but perhaps CIFS was the culprit.  Glad it's fixed tho!

---

