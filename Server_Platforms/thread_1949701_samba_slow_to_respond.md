---
title: "samba slow to respond"
date: 2012-03-30
forum: Server Platforms
---

### Post by talz13 on 2012-03-30
So I've had my ubuntu 10.04 server installed for about 2 years now, and just recently have noticed that the samba response is not good suddenly.  Before, I would open a mapped drive from my win7 desktop and it would load almost immediately.  Now, there is an 8-15 second delay while the mouse cursor is spinning, waiting for the network share to respond.

This happens on first connecting to the share, but also when navigating through folders on the share.

Is there anything I can do to help troubleshoot and find out what the issue is?

It also takes about 5 seconds to log in with putty to my server, with the login name pre-populated and using ssh public key authentication.

The server hardware is fine, and the performance is degraded compared to what I normally observe.  The server specs are:

intel E6300 @ 2.80GHz, 2 cores
gigabyte eg43m-s2h mobo
4gb ddr2 ram
1x640gb wd6400aacs green drive - ext3 format
4x1tb wd1001fals-0 black drive in raid 5 - XFS format
intel integrated video (it's a headless server, what do I care? :))

The desktop specs are:

intel q6600 @ 3.00GHz, 4 cores
gigabyte ep45-ds3l mobo
8gb ddr2 ram
1x128gb crucial SSD
AMD 5850 1GB GPU

It's networked with my desktop via an asus rt-n16 running tomatoUSB firmware.  I have an 8 port d-link gigabit switch hanging off of the asus to provide ports for my streaming boxes, VoIP phone, etc, but the PCs are home runs directly to the asus.

---

### Post by HermanAB on 2012-04-01
htop
ntop
ps -e

---

### Post by headvampyre@hotmail.co.uk on 2012-04-01
Have you made any changes to the Samba configuration lately?

Posting the global section and/or slow shares of smb.conf could help.

cheers.

---

### Post by talz13 on 2012-04-01
I just ran testparm as I noticed in the smb.conf comments and got:```

jeff@server:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[apps]"
Processing section "[video]"
Processing section "[music]"
Processing section "[pictures]"
Processing section "[games]"
Processing section "[pic]"
Processing section "[backup]"
Processing section "[books]"
Processing section "[house]"
Loaded services file OK.
Server role: ROLE_STANDALONE
```


> **HermanAB said:**
> htop
ntop
ps -e

output of htop:```
jeff@server:~$ htop

  1  [|                                1.3%]     Tasks: 276 total, 1 running
  2  [                                 0.0%]     Load average: 0.06 0.21 0.17
  Mem[||||||||||||||||||||||||||1320/3929MB]     Uptime: 8 days, 04:45:47
  Swp[|                          101/4095MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
18466 jeff      20   0 13440  1524  1044 R  1.0  0.0  0:00.82 htop
 1660 jeff      20   0  610M  160M  3504 S  0.0  4.1  0:28.50 /usr/bin/python -OO /usr/bin/sabn
12908 root      39  19  994M  496M  5456 S  0.0 12.6  1h01:27 /usr/bin/java -Dfile.encoding=UTF
12886 root      39  19  994M  496M  5456 S  0.0 12.6  0:06.44 /usr/bin/java -Dfile.encoding=UTF
12904 root      39  19  994M  496M  5456 S  0.0 12.6 12:59.18 /usr/bin/java -Dfile.encoding=UTF
    1 root      20   0 57628  1568  1032 S  0.0  0.0  0:07.21 /sbin/init
  368 root      20   0 17040   732   568 S  0.0  0.0  0:07.41 upstart-udev-bridge --daemon
  396 root      16  -4 10964   480   324 S  0.0  0.0  0:08.07 udevd --daemon
  911 root      20   0 92332  1564  1120 S  0.0  0.0  0:01.02 smbd -F
  913 syslog    20   0  199M  1424   944 S  0.0  0.0  0:00.80 rsyslogd -c4
  931 syslog    20   0  199M  1424   944 S  0.0  0.0  0:05.46 rsyslogd -c4
  932 syslog    20   0  199M  1424   944 S  0.0  0.0  0:00.01 rsyslogd -c4
  933 syslog    20   0  199M  1424   944 S  0.0  0.0  0:00.11 rsyslogd -c4
  981 root      20   0  6080   488   484 S  0.0  0.0  0:00.01 /sbin/getty -8 38400 tty4
  983 root      20   0  6556   584   448 S  0.0  0.0  0:00.02 dhclient3 -e IF_METRIC=100 -pf /v
  989 root      20   0  6080   488   484 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty5
 1010 root      20   0  6080   488   484 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty2
 1011 root      20   0  6080   488   484 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty3
 1013 root      20   0  6080   488   484 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty6
 1016 root      20   0  4032   444   440 S  0.0  0.0  0:00.00 acpid -c /etc/acpi/events -s /var
 1023 daemon    20   0 12556   292   272 S  0.0  0.0  0:00.01 atd
 1024 root      20   0 55132  1748  1240 S  0.0  0.0  0:02.14 cron
 1036 messageb  20   0 55348   788   556 S  0.0  0.0  0:00.04 dbus-daemon --system --fork
 1061 avahi     20   0 65876  1144   980 S  0.0  0.0  0:02.12 avahi-daemon: running [server.loc
 1062 avahi     20   0 65720   268   236 S  0.0  0.0  0:00.00 avahi-daemon: chroot helper
 1191 root      20   0 45084  1064   952 S  0.0  0.0  0:00.07 /usr/sbin/sshd -D
 1230 root      20   0 35456  3644  1100 S  0.0  0.1  0:29.35 /usr/sbin/munin-node
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit
```

output of ntop:```
jeff@server:~$ ntop
Sun Apr  1 16:03:02 2012  NOTE: Interface merge enabled by default
Sun Apr  1 16:03:02 2012  Initializing gdbm databases
Sun Apr  1 16:03:02 2012  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Sun Apr  1 16:03:02 2012  Possible solution: please use '-P <directory>'
Sun Apr  1 16:03:02 2012  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Sun Apr  1 16:03:02 2012  CLEANUP[t140707631310592]: ntop caught signal 2
Sun Apr  1 16:03:02 2012  THREADMGMT[t140707631310592]: ntop RUNSTATE: SHUTDOWN(7)
Sun Apr  1 16:03:02 2012  CLEANUP[t140707631310592] catching thread is unknown
Sun Apr  1 16:03:02 2012  CLEANUP: Running threads
Sun Apr  1 16:03:02 2012  CLEANUP: Locking purge mutex (may block for a little while)
Sun Apr  1 16:03:02 2012  CLEANUP: Locked purge mutex, continuing shutdown
Sun Apr  1 16:03:02 2012  CLEANUP: Continues
Sun Apr  1 16:03:02 2012  PLUGIN_TERM: Unloading plugins (if any)
Sun Apr  1 16:03:02 2012  CLEANUP: Clean up complete
Sun Apr  1 16:03:02 2012  THREADMGMT[t140707631310592]: ntop RUNSTATE: TERM(8)
Sun Apr  1 16:03:02 2012  ===================================
Sun Apr  1 16:03:02 2012          ntop is shutdown...
Sun Apr  1 16:03:02 2012  ===================================
```

output of ps -e:```
jeff@server:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:07 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:01 migration/0
    4 ?        00:00:07 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:01 migration/1
    7 ?        00:00:18 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:03 events/0
   10 ?        00:00:16 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 pm
   17 ?        00:00:00 sync_supers
   18 ?        00:00:01 bdi-default
   19 ?        00:00:00 kintegrityd/0
   20 ?        00:00:00 kintegrityd/1
   21 ?        00:00:07 kblockd/0
   22 ?        00:00:04 kblockd/1
   23 ?        00:00:00 kacpid
   24 ?        00:00:00 kacpi_notify
   25 ?        00:00:00 kacpi_hotplug
   26 ?        00:00:00 ata/0
   27 ?        00:00:00 ata/1
   28 ?        00:00:00 ata_aux
   29 ?        00:00:00 ksuspend_usbd
   30 ?        00:00:00 khubd
   31 ?        00:00:00 kseriod
   32 ?        00:00:00 kmmcd
   35 ?        00:00:00 khungtaskd
   36 ?        00:01:18 kswapd0
   37 ?        00:00:00 ksmd
   38 ?        00:00:00 aio/0
   39 ?        00:00:00 aio/1
   40 ?        00:00:00 ecryptfs-kthrea
   41 ?        00:00:00 crypto/0
   42 ?        00:00:00 crypto/1
   46 ?        00:00:00 scsi_eh_0
   47 ?        00:00:00 scsi_eh_1
   50 ?        00:00:00 scsi_eh_2
   52 ?        00:00:00 scsi_eh_3
   56 ?        00:00:00 kstriped
   57 ?        00:00:00 kmpathd/0
   58 ?        00:00:00 kmpathd/1
   59 ?        00:00:00 kmpath_handlerd
   60 ?        00:00:00 ksnapd
   61 ?        00:01:42 kondemand/0
   62 ?        00:04:48 kondemand/1
   63 ?        00:00:00 kconservative/0
   64 ?        00:00:00 kconservative/1
  223 ?        00:00:00 usbhid_resumer
  266 ?        00:00:00 khpsbpkt
  295 ?        00:00:00 knodemgrd_0
  325 ?        00:00:19 kjournald
  331 ?        01:28:47 md0_raid5
  368 ?        00:00:07 upstart-udev-br
  394 ?        00:00:20 flush-8:0
  396 ?        00:00:08 udevd
  741 ?        00:00:00 kpsmoused
  763 ?        00:00:00 i915
  841 ?        00:00:00 xfs_mru_cache
  842 ?        00:00:21 xfslogd/0
  843 ?        00:00:06 xfslogd/1
  844 ?        00:00:25 xfsdatad/0
  845 ?        00:00:07 xfsdatad/1
  846 ?        00:00:00 xfsconvertd/0
  847 ?        00:00:00 xfsconvertd/1
  848 ?        00:00:05 xfsbufd
  850 ?        00:00:02 xfsaild
  856 ?        00:00:03 xfssyncd
  865 ?        00:00:19 kjournald
  872 ?        00:00:00 kjournald
  911 ?        00:00:01 smbd
  913 ?        00:00:18 rsyslogd
  981 tty4     00:00:00 getty
  983 ?        00:00:00 dhclient3
  989 tty5     00:00:00 getty
 1010 tty2     00:00:00 getty
 1011 tty3     00:00:00 getty
 1013 tty6     00:00:00 getty
 1016 ?        00:00:00 acpid
 1023 ?        00:00:00 atd
 1024 ?        00:00:02 cron
 1036 ?        00:00:00 dbus-daemon
 1061 ?        00:00:02 avahi-daemon
 1062 ?        00:00:00 avahi-daemon
 1191 ?        00:00:00 sshd
 1230 ?        00:00:29 munin-node
 1231 ?        00:00:06 nmbd
 1232 ?        00:00:00 smbd
 1257 ?        00:00:17 ntpd
 1261 ?        00:00:02 freshclam
 1281 ?        00:20:20 python
 1291 ?        01:29:40 deluged
 1589 ?        00:07:55 deluge-web
 1641 ?        02:45:15 sabnzbdplus
 1687 ?        00:00:00 iprt/0
 1688 ?        00:00:00 iprt/1
 1722 ?        00:00:04 winbindd
 1725 ?        00:00:01 winbindd
 1784 ?        00:00:15 sendmail-mta
 1820 ?        00:00:01 mdadm
 1826 ?        00:00:47 apcupsd
 1869 ?        00:02:04 fail2ban-server
 1887 ?        00:00:00 inotifywait
 1888 ?        00:00:00 S99fileWatch
 1889 ?        00:00:00 inotifywait
 1890 ?        00:00:00 S99fileWatch
 1891 ?        00:00:00 inotifywait
 1892 ?        00:00:00 S99fileWatch
 1893 ?        00:00:00 inotifywait
 1894 ?        00:00:00 S99fileWatch
 1977 ?        00:00:21 miniserv.pl
 1980 tty1     00:00:00 getty
 2022 ?        00:00:00 console-kit-dae
 2214 ?        00:00:03 winbindd
 2217 ?        00:00:00 winbindd
 4411 ?        00:00:00 cron
 4416 ?        00:00:00 sh
 4660 ?        00:00:01 flexget
 6645 ?        00:00:02 smbd
 9166 ?        00:00:40 udevd
 9306 ?        00:00:00 udevd
10057 ?        00:01:46 smbd
12625 ?        00:01:55 smbd
12860 ?        07:51:40 java
13431 ?        00:00:00 cron
13438 ?        00:00:00 sh
13685 ?        00:00:01 flexget
15516 ?        00:00:00 smbd
17400 ?        00:00:00 flush-9:0
17819 ?        00:00:00 flush-8:16
17820 ?        00:00:00 flush-8:48
18128 ?        00:00:00 flush-8:32
18132 ?        00:00:00 sshd
18240 ?        00:00:00 sshd
18241 pts/0    00:00:00 bash
18391 ?        00:00:00 smbd
18463 pts/0    00:00:00 ps
20934 ?        00:00:00 cron
20937 ?        00:00:00 sh
21165 ?        00:00:01 flexget
22011 ?        00:09:31 python
```

---

### Post by HermanAB on 2012-04-02
OK, so smbd, nmbd and winbindd are all running and the machine is not overloaded - basically doing nothing.

So, I'm wondering whether the issue is a lame DNS or ethernet errors?

Look at the name servers in /etc/resolv.conf and do something like:
$ dig @nameserveripaddress [www.google.com](www.google.com)

to see how long the DNS takes to respond.

Also look at the ethernet card statistics:
$ sudo ifconfig

The card should not be dropping packets.

---

### Post by talz13 on 2012-08-23
Looks like I may have solved my issue.  I went into webmin's Samba settings, to the Windows Networking Options page, and changed "WINS mode" from "Neither" to "Be WINS Server".

I cycled the samba process, and haven't noticed the delay since then.

---

