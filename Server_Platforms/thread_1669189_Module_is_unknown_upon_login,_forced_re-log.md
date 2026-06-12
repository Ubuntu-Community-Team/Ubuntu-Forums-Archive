---
title: "Module is unknown upon login, forced re-log"
date: 2011-01-17
forum: Server Platforms
---

### Post by techonokios on 2011-01-17
I have an issue where if I log in locally on the machine, the server will post the normal login information, but then say 'module is unknown' and then drop me back to the log in prompt.

I can, however, log in remotely.  I can only imagine it has something to do with x11, but I'm not sure.

I'm sorry for the lack of better information, but this is all I have right now..

I am running 10.04.1 LTS, if that helps.

Here is the output from ps


```
root@hermes:~# ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2796  1644 ?        Ss   10:20   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    10:20   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    10:20   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    10:20   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    10:20   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    10:20   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    10:20   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    10:20   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    10:20   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    10:20   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    10:20   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    10:20   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    10:20   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    10:20   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    10:20   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    10:20   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    10:20   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    10:20   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    10:20   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    10:20   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    10:20   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    10:20   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    10:20   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    10:20   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    10:20   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    10:20   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    10:20   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    10:20   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    10:20   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    10:20   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    10:20   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    10:20   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    10:20   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   10:20   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    10:20   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    10:20   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    10:20   0:00 [ecryptfs-kthrea]
root        41  0.0  0.0      0     0 ?        S    10:20   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    10:20   0:00 [crypto/1]
root        46  0.0  0.0      0     0 ?        S    10:20   0:00 [scsi_eh_0]
root        47  0.0  0.0      0     0 ?        S    10:20   0:00 [scsi_eh_1]
root        50  0.0  0.0      0     0 ?        S    10:20   0:00 [kstriped]
root        51  0.0  0.0      0     0 ?        S    10:20   0:00 [kmpathd/0]
root        52  0.0  0.0      0     0 ?        S    10:20   0:00 [kmpathd/1]
root        53  0.0  0.0      0     0 ?        S    10:20   0:00 [kmpath_handlerd]
root        54  0.0  0.0      0     0 ?        S    10:20   0:00 [ksnapd]
root        55  0.0  0.0      0     0 ?        S    10:20   0:00 [kondemand/0]
root        56  0.0  0.0      0     0 ?        S    10:20   0:00 [kondemand/1]
root        57  0.0  0.0      0     0 ?        S    10:20   0:00 [kconservative/0]
root        58  0.0  0.0      0     0 ?        S    10:20   0:00 [kconservative/1]
root       234  0.0  0.0      0     0 ?        S    10:20   0:00 [jbd2/sda1-8]
root       235  0.0  0.0      0     0 ?        S    10:20   0:00 [ext4-dio-unwrit]
root       236  0.0  0.0      0     0 ?        S    10:20   0:00 [ext4-dio-unwrit]
root       294  0.0  0.0   2316   908 ?        S    10:20   0:00 upstart-udev-bridge --daemon
root       297  0.0  0.0   2500   912 ?        S<s  10:20   0:00 udevd --daemon
root       530  0.0  0.0      0     0 ?        S    10:20   0:00 [usbhid_resumer]
root       559  0.0  0.0      0     0 ?        S    10:21   0:00 [radeon/0]
root       560  0.0  0.0      0     0 ?        S    10:21   0:00 [radeon/1]
root       561  0.0  0.0      0     0 ?        S    10:21   0:00 [ttm_swap]
root       566  0.0  0.0   2496   808 ?        S<   10:21   0:00 udevd --daemon
root       576  0.0  0.0      0     0 ?        S    10:21   0:00 [hd-audio0]
root       577  0.0  0.0   2496   788 ?        S<   10:21   0:00 udevd --daemon
root       633  0.0  0.2  15312  3964 ?        Ss   10:21   0:00 smbd -F
syslog     645  0.0  0.1  34688  1640 ?        Sl   10:21   0:00 rsyslogd -c4
105        649  0.0  0.0   2664   872 ?        Ss   10:21   0:00 dbus-daemon --system --fork
root       672  0.0  0.0  15312  1196 ?        S    10:21   0:00 smbd -F
root       731  0.0  0.0   1792   564 tty4     Ss+  10:21   0:00 /sbin/getty -8 38400 tty4
root       735  0.0  0.0   1792   564 tty5     Ss+  10:21   0:00 /sbin/getty -8 38400 tty5
root       738  0.0  0.0   1792   564 tty2     Ss+  10:21   0:00 /sbin/getty -8 38400 tty2
root       739  0.0  0.0   1792   564 tty3     Ss+  10:21   0:00 /sbin/getty -8 38400 tty3
root       742  0.0  0.0   1792   560 tty6     Ss+  10:21   0:00 /sbin/getty -8 38400 tty6
daemon     749  0.0  0.0   2248   432 ?        Ss   10:21   0:00 atd
root       750  0.0  0.0   2376   900 ?        Ss   10:21   0:00 cron
root       793  0.0  0.4  36112  7456 ?        Ss   10:21   0:00 /usr/sbin/apache2 -k start
mysql      797  0.0  1.2 146064 18784 ?        Ssl  10:21   0:03 /usr/sbin/mysqld
root       840  0.0  0.0   1792   564 tty1     Ss+  10:21   0:00 /sbin/getty -8 38400 tty1
root       925  0.0  0.0   2232   400 ?        Ss   10:21   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth
root       942  0.0  0.0   5552   936 ?        Ss   10:21   0:00 /usr/sbin/sshd
root       957  0.0  0.1   8640  1636 ?        Ss   10:21   0:00 nmbd -D
root       972  0.0  0.2   8864  3140 ?        Ss   10:29   0:00 sshd: tcraig [priv]
root       976  0.0  0.1  20464  3072 ?        Sl   10:30   0:00 /usr/sbin/console-kit-daemon --no-daemon
tcraig    1112  0.0  0.1   8864  1692 ?        S    10:30   0:00 sshd: tcraig@pts/0
tcraig    1113  0.0  0.2   6224  3628 pts/0    Ss+  10:30   0:00 -bash
root      1732  0.0  0.0      0     0 ?        S    10:46   0:00 [flush-8:0]
www-data  1735  0.0  0.4  36848  6628 ?        S    10:55   0:00 /usr/sbin/apache2 -k start
www-data  1738  0.0  0.3  36748  5228 ?        S    10:55   0:00 /usr/sbin/apache2 -k start
www-data  1745  0.0  0.4  36840  6656 ?        S    10:58   0:00 /usr/sbin/apache2 -k start
www-data  1759  0.0  0.4  36976  6656 ?        S    11:00   0:00 /usr/sbin/apache2 -k start
www-data  1764  0.0  0.4  37044  6664 ?        S    11:02   0:00 /usr/sbin/apache2 -k start
www-data  1791  0.0  0.4  36780  6484 ?        S    11:31   0:00 /usr/sbin/apache2 -k start
www-data  2318  0.0  0.4  37036  6468 ?        S    11:45   0:00 /usr/sbin/apache2 -k start
www-data  2320  0.0  0.4  36804  6488 ?        S    11:45   0:00 /usr/sbin/apache2 -k start
www-data  2321  0.0  0.4  36804  6568 ?        S    11:45   0:00 /usr/sbin/apache2 -k start
www-data  2393  0.0  0.4  36804  6452 ?        S    11:51   0:00 /usr/sbin/apache2 -k start
root      2526  0.1  0.1   8788  3044 ?        Ss   12:05   0:00 sshd: tcraig [priv]
tcraig    2602  0.0  0.1   8788  1636 ?        S    12:05   0:00 sshd: tcraig@pts/1
tcraig    2603  0.6  0.2   6224  3604 pts/1    Ss   12:05   0:00 -bash
root      2626  1.2  0.2   6324  3708 pts/1    S    12:06   0:00 /bin/bash
root      2646  0.0  0.0   2716  1072 pts/1    R+   12:06   0:00 ps -aux

```

---

