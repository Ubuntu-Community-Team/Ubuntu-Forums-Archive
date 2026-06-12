---
title: "Disabling unnecessary processes permanently"
date: 2011-11-25
forum: Server Platforms
---

### Post by sirgad on 2011-11-25
Hi,

I've just performed an install of Ubuntu Server 11.10 64-bit on a Dell E5400 laptop.  It currently offers the following services to my local network: SAMBA file-sharing; SSH; Privoxy.  I manage it entirely from my MacBook Pro over the LAN and non-root SSH.  The display is disabled manually when I boot the machine using the "vbetool dpms off" command.  I have removed the keyboard from the laptop to prevent unauthorised local access.  The only storage is the built-in 80GB SATA HDD, the home directory does not use encryption, and I have a small swap partition.

In the interests of security, performance and power-saving, I'd like to disable permanently any and all processes not required for this laptop's headless operation as a server of the aforementioned services.

Here is the output of the "ps aux" command:

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  24048  2108 ?        Ss   Nov24   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Nov24   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Nov24   0:01 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Nov24   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Nov24   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        S    Nov24   0:00 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S<   Nov24   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   Nov24   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   Nov24   0:00 [netns]
root        15  0.0  0.0      0     0 ?        S    Nov24   0:00 [sync_supers]
root        16  0.0  0.0      0     0 ?        S    Nov24   0:00 [bdi-default]
root        17  0.0  0.0      0     0 ?        S<   Nov24   0:00 [kintegrityd]
root        18  0.0  0.0      0     0 ?        S<   Nov24   0:00 [kblockd]
root        19  0.0  0.0      0     0 ?        S<   Nov24   0:00 [ata_sff]
root        20  0.0  0.0      0     0 ?        S    Nov24   0:00 [khubd]
root        21  0.0  0.0      0     0 ?        S<   Nov24   0:00 [md]
root        23  0.0  0.0      0     0 ?        S    Nov24   0:00 [khungtaskd]
root        24  0.0  0.0      0     0 ?        S    Nov24   0:00 [kswapd0]
root        25  0.0  0.0      0     0 ?        SN   Nov24   0:00 [ksmd]
root        26  0.0  0.0      0     0 ?        SN   Nov24   0:00 [khugepaged]
root        27  0.0  0.0      0     0 ?        S    Nov24   0:00 [fsnotify_mark]
root        28  0.0  0.0      0     0 ?        S    Nov24   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   Nov24   0:00 [crypto]
root        37  0.0  0.0      0     0 ?        S<   Nov24   0:00 [kthrotld]
root       221  0.0  0.0      0     0 ?        S    Nov24   0:00 [scsi_eh_0]
root       222  0.0  0.0      0     0 ?        S    Nov24   0:00 [scsi_eh_1]
root       223  0.0  0.0      0     0 ?        S    Nov24   0:00 [scsi_eh_2]
root       224  0.0  0.0      0     0 ?        S    Nov24   0:00 [scsi_eh_3]
root       225  0.0  0.0      0     0 ?        S    Nov24   0:00 [scsi_eh_4]
root       226  0.0  0.0      0     0 ?        S    Nov24   0:00 [scsi_eh_5]
root       228  0.4  0.0      0     0 ?        S    Nov24   7:38 [kworker/u:4]
root       229  0.4  0.0      0     0 ?        S    Nov24   7:53 [kworker/u:5]
root       246  0.0  0.0      0     0 ?        S    Nov24   0:00 [jbd2/sda1-8]
root       247  0.0  0.0      0     0 ?        S<   Nov24   0:00 [ext4-dio-unwrit]
root       306  0.0  0.0  17096   636 ?        S    Nov24   0:00 upstart-udev-bridge --daemon
root       311  0.0  0.0  21452  1308 ?        Ss   Nov24   0:00 udevd --daemon
root       368  0.0  0.0  21448   780 ?        S    Nov24   0:00 udevd --daemon
root       369  0.0  0.0  21448   780 ?        S    Nov24   0:00 udevd --daemon
syslog     420  0.0  0.0  52732  1416 ?        Sl   Nov24   0:00 rsyslogd -c5
102        426  0.0  0.0  24152   964 ?        Ss   Nov24   0:00 dbus-daemon --system --fork --activation=upstart
root       466  0.0  0.0      0     0 ?        S<   Nov24   0:00 [kpsmoused]
root       553  0.0  0.2  93860  4960 ?        Ss   Nov24   0:00 smbd -F
root       561  0.0  0.0  15048   392 ?        S    Nov24   0:00 upstart-socket-bridge --daemon
root       564  0.0  0.0  93772  1528 ?        S    Nov24   0:00 smbd -F
root       635  0.0  0.0      0     0 ?        S<   Nov24   0:00 [hd-audio0]
root       704  0.0  0.0   7124  1020 ?        Ss   Nov24   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth
root       720  0.0  0.1  49684  2780 ?        Ss   Nov24   0:00 /usr/sbin/sshd -D
root       731  0.0  0.0  63736  2000 ?        Ss   Nov24   0:01 nmbd -D
privoxy    790  0.0  0.0  58908  1804 ?        Ss   Nov24   0:01 /usr/sbin/privoxy <REDACTED>
root       791  0.0  0.0   4180   636 tty4     Ss+  Nov24   0:00 /sbin/getty -8 38400 tty4
root       794  0.0  0.0   4180   636 tty5     Ss+  Nov24   0:00 /sbin/getty -8 38400 tty5
root       797  0.0  0.0   4180   636 tty2     Ss+  Nov24   0:00 /sbin/getty -8 38400 tty2
root       798  0.0  0.0   4180   636 tty3     Ss+  Nov24   0:00 /sbin/getty -8 38400 tty3
root       800  0.0  0.0   4180   640 tty6     Ss+  Nov24   0:00 /sbin/getty -8 38400 tty6
root       807  0.0  0.0  15848   632 ?        Ss   Nov24   0:17 /usr/sbin/irqbalance
root       814  0.0  0.0  18976   916 ?        Ss   Nov24   0:00 cron
daemon     815  0.0  0.0  16776   388 ?        Ss   Nov24   0:00 atd
root       843  0.0  0.1  68116  2096 ?        Ss   Nov24   0:00 /usr/sbin/winbindd
root       846  0.0  0.0  68036  1868 ?        S    Nov24   0:00 /usr/sbin/winbindd
root       893  0.0  0.0   4180   636 tty1     Ss+  Nov24   0:00 /sbin/getty -8 38400 tty1
root       899  0.0  0.0  68116  1860 ?        S    Nov24   0:00 /usr/sbin/winbindd
root       930  0.0  0.0  68112  1388 ?        S    Nov24   0:00 /usr/sbin/winbindd
root      1573  0.0  0.0      0     0 ?        S    16:03   0:00 [flush-8:0]
root      1616  3.8  0.0      0     0 ?        S    16:58   3:13 [kworker/0:1]
root      1649  0.0  0.2 103828  4452 ?        Ss   17:54   0:00 sshd: standard [priv]
standard  1676  0.0  0.0 103828  1860 ?        S    17:54   0:00 sshd: standard@pts/0
standard  1677  0.0  0.1  24768  3960 pts/0    Ss   17:54   0:00 -bash
root      1724  0.0  0.2  94324  4684 ?        S    17:55   0:00 smbd -F
root      1750  2.6  0.0      0     0 ?        S    18:12   0:15 [kworker/1:0]
root      1752  0.0  0.0      0     0 ?        S    18:13   0:00 [kworker/0:0]
root      1758  0.0  0.0      0     0 ?        S    18:17   0:00 [kworker/1:1]
root      1761  0.0  0.0      0     0 ?        S    18:18   0:00 [kworker/0:2]
root      1764  0.0  0.0      0     0 ?        S    18:22   0:00 [kworker/1:2]
standard  1765  0.0  0.0  18028  1256 pts/0    R+   18:22   0:00 ps aux

```

The list includes 75 processes; on boot, the server reports between 75 and 78 process running, so this is normal.

I would very much appreciate advice regarding the following.

A) Which of the listed processes can safely be permanently disabled without affecting the services I require, or reducing the performance and security of the running server?  In my own opinion, it seems I could safely kill [kpsmoused], [hd-audio0], [crypto] and [ecryptfs-kthrea] - but I'm by no means 100% confident, nor know how to go about it.  Also, according to statistics so far, I have no need for the swap partition (all my activity is comfortably conducted in RAM) so if it's possible to disable the process required for that, that would be ideal.

B) What are the recommended practices for disabling (any) services suggested in (A)?

I do apologise in advance, as I'm sure this question has been asked many times before; however, I've failed to find any answers that deal directly with 11.10, 11.10 64-bit or 11.10 Server 64-bit, or that offer an appropriate level of information to allow me to make informed decisions.

Thanks in advance to all who choose to respond constructively. :)

---

