---
title: "Something is taking screenshot of my desktop"
date: 2016-03-26
forum: Security
---

### Post by Jahidul_Hamid on 2016-03-26
Something is taking screenshot of my desktop at a fixed interval of time. I can't find the program/process that is responsible for this. Can someone help me.

System: Xubuntu 14.04.1

```
~ >>> ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 kworker/0:0H
    7 ?        00:00:02 rcu_sched
    8 ?        00:00:01 rcuos/0
    9 ?        00:00:00 rcuos/1
   10 ?        00:00:01 rcuos/2
   11 ?        00:00:00 rcuos/3
   12 ?        00:00:00 rcuos/4
   13 ?        00:00:00 rcuos/5
   14 ?        00:00:00 rcuos/6
   15 ?        00:00:00 rcuos/7
   16 ?        00:00:00 rcu_bh
   17 ?        00:00:00 rcuob/0
   18 ?        00:00:00 rcuob/1
   19 ?        00:00:00 rcuob/2
   20 ?        00:00:00 rcuob/3
   21 ?        00:00:00 rcuob/4
   22 ?        00:00:00 rcuob/5
   23 ?        00:00:00 rcuob/6
   24 ?        00:00:00 rcuob/7
   25 ?        00:00:00 migration/0
   26 ?        00:00:00 watchdog/0
   27 ?        00:00:00 watchdog/1
   28 ?        00:00:00 migration/1
   29 ?        00:00:00 ksoftirqd/1
   31 ?        00:00:00 kworker/1:0H
   32 ?        00:00:00 watchdog/2
   33 ?        00:00:00 migration/2
   34 ?        00:00:00 ksoftirqd/2
   36 ?        00:00:00 kworker/2:0H
   37 ?        00:00:00 watchdog/3
   38 ?        00:00:00 migration/3
   39 ?        00:00:00 ksoftirqd/3
   40 ?        00:00:00 kworker/3:0
   41 ?        00:00:00 kworker/3:0H
   42 ?        00:00:00 khelper
   43 ?        00:00:00 kdevtmpfs
   44 ?        00:00:00 netns
   45 ?        00:00:00 writeback
   46 ?        00:00:00 kintegrityd
   47 ?        00:00:00 bioset
   49 ?        00:00:00 kblockd
   50 ?        00:00:00 ata_sff
   51 ?        00:00:00 khubd
   52 ?        00:00:00 md
   53 ?        00:00:00 devfreq_wq
   56 ?        00:00:00 khungtaskd
   57 ?        00:00:00 kswapd0
   58 ?        00:00:00 ksmd
   59 ?        00:00:00 khugepaged
   60 ?        00:00:00 fsnotify_mark
   61 ?        00:00:00 ecryptfs-kthrea
   62 ?        00:00:00 crypto
   74 ?        00:00:00 kthrotld
   95 ?        00:00:00 deferwq
   96 ?        00:00:00 charger_manager
  139 ?        00:00:00 kpsmoused
  142 ?        00:00:00 scsi_eh_0
  143 ?        00:00:00 scsi_eh_1
  144 ?        00:00:00 scsi_eh_2
  145 ?        00:00:00 scsi_eh_3
  146 ?        00:00:00 scsi_eh_4
  147 ?        00:00:00 scsi_eh_5
  149 ?        00:00:00 kworker/u16:3
  176 ?        00:00:00 kworker/1:3
  245 ?        00:00:00 bioset
  256 ?        00:00:00 kworker/u17:1
  257 ?        00:00:00 jbd2/sda8-8
  258 ?        00:00:00 ext4-rsv-conver
  443 ?        00:00:00 upstart-udev-br
  449 ?        00:00:00 systemd-udevd
  497 ?        00:00:00 irq/49-mei_me
  511 ?        00:00:00 kmemstick
  552 ?        00:00:00 kmpathd
  556 ?        00:00:00 kmpath_handlerd
  593 ?        00:00:00 kworker/0:2
  601 ?        00:00:00 hd-audio0
  602 ?        00:00:00 kvm-irqfd-clean
  603 ?        00:00:00 hd-audio1
  683 ?        00:00:00 cfg80211
  687 ?        00:00:00 upstart-socket-
  899 ?        00:00:00 hci0
  900 ?        00:00:00 hci0
  901 ?        00:00:00 kworker/u17:2
  910 ?        00:00:00 mount.ntfs
  926 ?        00:00:00 mount.ntfs
  933 ?        00:00:00 mount.ntfs
  937 ?        00:00:00 jbd2/sda9-8
  938 ?        00:00:00 ext4-rsv-conver
  952 ?        00:00:00 smbd
  997 ?        00:00:00 upstart-file-br
 1051 ?        00:00:00 rsyslogd
 1053 ?        00:00:00 dbus-daemon
 1099 ?        00:00:00 ModemManager
 1180 ?        00:00:00 bluetoothd
 1185 ?        00:00:00 krfcommd
 1211 ?        00:00:00 systemd-logind
 1222 ?        00:00:00 avahi-daemon
 1254 ?        00:00:00 avahi-daemon
 1328 ?        00:00:00 runsvdir
 1329 tty4     00:00:00 getty
 1333 tty5     00:00:00 getty
 1341 tty2     00:00:00 getty
 1343 ?        00:00:00 runsv
 1345 ?        00:00:00 svlogd
 1346 ?        00:00:00 git-daemon
 1353 tty3     00:00:00 getty
 1362 tty6     00:00:00 getty
 1391 ?        00:00:00 NetworkManager
 1428 ?        00:00:00 polkitd
 1445 ?        00:00:00 sshd
 1475 ?        00:00:00 cups-browsed
 1476 ?        00:00:00 irqbalance
 1485 ?        00:00:00 cron
 1486 ?        00:00:00 atd
 1487 ?        00:00:01 mysqld
 1528 ?        00:00:00 kerneloops
 1560 ?        00:00:00 whoopsie
 1565 ?        00:00:00 acpid
 1633 ?        00:00:00 smbd
 1700 ?        00:00:00 master
 1759 ?        00:00:02 tor
 1779 ?        00:00:00 iprt-VBoxWQueue
 1782 ?        00:00:00 iprt-VBoxTscThr
 1816 ?        00:00:13 teamviewerd
 1819 ?        00:00:00 dnsmasq
 1870 ?        00:00:02 wimaxd
 2001 ?        00:00:00 lightdm
 2011 ?        00:00:00 accounts-daemon
 2027 ?        00:00:00 apache2
 2038 tty7     00:01:50 Xorg
 2066 ?        00:00:00 apache2
 2067 ?        00:00:00 apache2
 2068 ?        00:00:00 apache2
 2069 ?        00:00:00 apache2
 2070 ?        00:00:00 apache2
 2218 ?        00:00:00 lightdm
 2231 ?        00:00:00 kauditd
 2236 ?        00:00:00 init
 2331 tty1     00:00:00 getty
 2341 ?        00:00:00 console-kit-dae
 2741 ?        00:00:00 docker
 2748 ?        00:00:00 winbindd
 2763 ?        00:00:00 dbus-daemon
 2777 ?        00:00:00 upstart-event-b
 2784 ?        00:00:00 window-stack-br
 2788 ?        00:00:00 nmbd
 2791 ?        00:00:00 gnome-keyring-d
 2800 ?        00:00:00 winbindd
 2865 ?        00:00:00 sh
 2876 ?        00:00:00 xfce4-session
 2881 ?        00:00:00 upstart-file-br
 2882 ?        00:00:00 upstart-dbus-br
 2884 ?        00:00:00 upstart-dbus-br
 2922 ?        00:00:00 xfconfd
 2927 ?        00:00:08 xfwm4
 2931 ?        00:00:14 xfce4-panel
 2933 ?        00:00:04 Thunar
 2935 ?        00:00:02 xfdesktop
 2936 ?        00:00:01 xfsettingsd
 2942 ?        00:00:01 artha
 2943 ?        00:00:00 indicator-sound
 2944 ?        00:00:00 cuttlefish
 2945 ?        00:00:00 indicator-appli
 2946 ?        00:01:11 skype
 2947 ?        00:00:00 indicator-bluet
 2948 ?        00:00:00 nm-applet
 2950 ?        00:00:00 indicator-power
 2951 ?        00:00:00 applet.py
 2952 ?        00:00:00 zeitgeist-datah
 2956 ?        00:00:00 xfce4-power-man
 2957 ?        00:00:00 evolution-alarm
 2961 ?        00:00:00 polkit-gnome-au
 2962 ?        00:00:00 blueman-applet
 2966 ?        00:00:00 upowerd
 2970 ?        00:00:02 xfce4-volumed
 2989 ?        00:00:00 gvfsd
 2994 ?        00:00:00 gvfsd-fuse
 3008 ?        00:00:00 pulseaudio
 3010 ?        00:00:00 rtkit-daemon
 3092 ?        00:00:00 kworker/2:2
 3104 ?        00:00:00 zeitgeist-daemo
 3110 ?        00:00:00 zeitgeist-fts
 3111 ?        00:00:05 panel-1-netload
 3112 ?        00:00:00 panel-4-systray
 3113 ?        00:00:00 panel-30-indica
 3114 ?        00:00:00 panel-7-battery
 3115 ?        00:00:00 panel-13-dateti
 3116 ?        00:00:02 xfce4-xkb-plugi
 3117 ?        00:00:00 panel-6-actions
 3118 ?        00:00:28 panel-12-whiske
 3119 ?        00:00:00 panel-40-weathe
 3240 ?        00:00:00 at-spi-bus-laun
 3244 ?        00:00:00 dbus-daemon
 3247 ?        00:00:00 at-spi2-registr
 3268 ?        00:00:00 bright_screen <defunct>
 3272 ?        00:00:00 cat
 3275 ?        00:00:00 init
 3277 ?        00:00:00 indicator-messa
 3284 ?        00:00:00 indicator-datet
 3324 ?        00:00:00 gconfd-2
 3426 ?        00:00:00 evolution-sourc
 3427 ?        00:00:04 dropbox
 3439 ?        00:00:00 gvfs-udisks2-vo
 3446 ?        00:00:00 udisksd
 3468 ?        00:00:00 obex-data-serve
 3473 ?        00:00:00 gvfsd-metadata
 3480 ?        00:00:00 evolution-calen
 3488 ?        00:00:00 cupsd
 3503 ?        00:00:00 gvfs-gphoto2-vo
 3532 ?        00:00:00 gvfs-afc-volume
 3537 ?        00:00:00 gvfs-mtp-volume
 3747 ?        00:12:06 firefox
 4197 ?        00:00:00 kworker/u16:0
 4339 ?        00:00:00 gvfsd-trash
 4347 ?        00:00:07 tumblerd
 4363 ?        00:00:00 dconf-service
 4486 ?        00:00:00 kworker/3:1
 4487 ?        00:00:00 kworker/2:0
 4733 ?        00:00:00 gnome-screensav
 4738 ?        00:00:00 kworker/1:1
 5494 ?        00:00:00 kworker/0:0
 5586 ?        00:00:00 dhclient
 5610 ?        00:00:00 xfce4-notifyd
 5683 ?        00:00:00 qmgr
 5684 ?        00:00:00 pickup
 5864 ?        00:00:00 syndaemon
 5898 ?        00:00:00 ntpd
 5911 ?        00:00:26 gnome-system-mo
 5939 ?        00:00:00 synaptic-pkexec
 5940 ?        00:00:03 synaptic
 5953 ?        00:00:00 dbus-launch
 5954 ?        00:00:00 dbus-daemon
 6036 ?        00:00:00 xfce4-terminal
 6041 ?        00:00:00 gnome-pty-helpe
 6042 pts/0    00:00:00 bash
 6084 ?        00:00:00 kworker/u16:1
 6145 pts/0    00:00:00 ps


```

```
~ >>> ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  34104  3516 ?        Ss   14:48   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    14:48   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    14:48   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   14:48   0:00 [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    14:48   0:02 [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    14:48   0:01 [rcuos/0]
root         9  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuos/1]
root        10  0.0  0.0      0     0 ?        S    14:48   0:01 [rcuos/2]
root        11  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuos/3]
root        12  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuos/4]
root        13  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuos/5]
root        14  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuos/6]
root        15  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuos/7]
root        16  0.0  0.0      0     0 ?        S    14:48   0:00 [rcu_bh]
root        17  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/0]
root        18  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/1]
root        19  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/2]
root        20  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/3]
root        21  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/4]
root        22  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/5]
root        23  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/6]
root        24  0.0  0.0      0     0 ?        S    14:48   0:00 [rcuob/7]
root        25  0.0  0.0      0     0 ?        S    14:48   0:00 [migration/0]
root        26  0.0  0.0      0     0 ?        S    14:48   0:00 [watchdog/0]
root        27  0.0  0.0      0     0 ?        S    14:48   0:00 [watchdog/1]
root        28  0.0  0.0      0     0 ?        S    14:48   0:00 [migration/1]
root        29  0.0  0.0      0     0 ?        S    14:48   0:00 [ksoftirqd/1]
root        31  0.0  0.0      0     0 ?        S<   14:48   0:00 [kworker/1:0H]
root        32  0.0  0.0      0     0 ?        S    14:48   0:00 [watchdog/2]
root        33  0.0  0.0      0     0 ?        S    14:48   0:00 [migration/2]
root        34  0.0  0.0      0     0 ?        S    14:48   0:00 [ksoftirqd/2]
root        36  0.0  0.0      0     0 ?        S<   14:48   0:00 [kworker/2:0H]
root        37  0.0  0.0      0     0 ?        S    14:48   0:00 [watchdog/3]
root        38  0.0  0.0      0     0 ?        S    14:48   0:00 [migration/3]
root        39  0.0  0.0      0     0 ?        S    14:48   0:00 [ksoftirqd/3]
root        40  0.0  0.0      0     0 ?        S    14:48   0:00 [kworker/3:0]
root        41  0.0  0.0      0     0 ?        S<   14:48   0:00 [kworker/3:0H]
root        42  0.0  0.0      0     0 ?        S<   14:48   0:00 [khelper]
root        43  0.0  0.0      0     0 ?        S    14:48   0:00 [kdevtmpfs]
root        44  0.0  0.0      0     0 ?        S<   14:48   0:00 [netns]
root        45  0.0  0.0      0     0 ?        S<   14:48   0:00 [writeback]
root        46  0.0  0.0      0     0 ?        S<   14:48   0:00 [kintegrityd]
root        47  0.0  0.0      0     0 ?        S<   14:48   0:00 [bioset]
root        49  0.0  0.0      0     0 ?        S<   14:48   0:00 [kblockd]
root        50  0.0  0.0      0     0 ?        S<   14:48   0:00 [ata_sff]
root        51  0.0  0.0      0     0 ?        S    14:48   0:00 [khubd]
root        52  0.0  0.0      0     0 ?        S<   14:48   0:00 [md]
root        53  0.0  0.0      0     0 ?        S<   14:48   0:00 [devfreq_wq]
root        56  0.0  0.0      0     0 ?        S    14:48   0:00 [khungtaskd]
root        57  0.0  0.0      0     0 ?        S    14:48   0:00 [kswapd0]
root        58  0.0  0.0      0     0 ?        SN   14:48   0:00 [ksmd]
root        59  0.0  0.0      0     0 ?        SN   14:48   0:00 [khugepaged]
root        60  0.0  0.0      0     0 ?        S    14:48   0:00 [fsnotify_mark]
root        61  0.0  0.0      0     0 ?        S    14:48   0:00 [ecryptfs-kthrea]
root        62  0.0  0.0      0     0 ?        S<   14:48   0:00 [crypto]
root        74  0.0  0.0      0     0 ?        S<   14:48   0:00 [kthrotld]
root        95  0.0  0.0      0     0 ?        S<   14:48   0:00 [deferwq]
root        96  0.0  0.0      0     0 ?        S<   14:48   0:00 [charger_manager]
root       139  0.0  0.0      0     0 ?        S<   14:48   0:00 [kpsmoused]
root       142  0.0  0.0      0     0 ?        S    14:48   0:00 [scsi_eh_0]
root       143  0.0  0.0      0     0 ?        S    14:48   0:00 [scsi_eh_1]
root       144  0.0  0.0      0     0 ?        S    14:48   0:00 [scsi_eh_2]
root       145  0.0  0.0      0     0 ?        S    14:48   0:00 [scsi_eh_3]
root       146  0.0  0.0      0     0 ?        S    14:48   0:00 [scsi_eh_4]
root       147  0.0  0.0      0     0 ?        S    14:48   0:00 [scsi_eh_5]
root       149  0.0  0.0      0     0 ?        S    14:48   0:00 [kworker/u16:3]
root       176  0.0  0.0      0     0 ?        S    14:48   0:00 [kworker/1:3]
root       245  0.0  0.0      0     0 ?        S<   14:48   0:00 [bioset]
root       256  0.0  0.0      0     0 ?        S<   14:48   0:00 [kworker/u17:1]
root       257  0.0  0.0      0     0 ?        S    14:48   0:00 [jbd2/sda8-8]
root       258  0.0  0.0      0     0 ?        S<   14:48   0:00 [ext4-rsv-conver]
root       443  0.0  0.0  19604   912 ?        S    14:48   0:00 upstart-udev-bridge --daemon
root       449  0.0  0.0  52116  2248 ?        Ss   14:48   0:00 /lib/systemd/systemd-udevd --daemon
root       497  0.0  0.0      0     0 ?        S    14:48   0:00 [irq/49-mei_me]
root       511  0.0  0.0      0     0 ?        S<   14:48   0:00 [kmemstick]
root       552  0.0  0.0      0     0 ?        S<   14:48   0:00 [kmpathd]
root       556  0.0  0.0      0     0 ?        S<   14:48   0:00 [kmpath_handlerd]
root       593  0.0  0.0      0     0 ?        S    14:48   0:00 [kworker/0:2]
root       601  0.0  0.0      0     0 ?        S<   14:48   0:00 [hd-audio0]
root       602  0.0  0.0      0     0 ?        S<   14:48   0:00 [kvm-irqfd-clean]
root       603  0.0  0.0      0     0 ?        S<   14:48   0:00 [hd-audio1]
root       683  0.0  0.0      0     0 ?        S<   14:48   0:00 [cfg80211]
root       687  0.0  0.0  15388   652 ?        S    14:48   0:00 upstart-socket-bridge --daemon
root       899  0.0  0.0      0     0 ?        S<   14:48   0:00 [hci0]
root       900  0.0  0.0      0     0 ?        S<   14:48   0:00 [hci0]
root       901  0.0  0.0      0     0 ?        S<   14:48   0:00 [kworker/u17:2]
root       910  0.0  0.0  23728  1024 ?        Ss   14:48   0:00 /sbin/mount.ntfs /dev/sda5 /media/jahid/Softs -o rw
root       926  0.0  0.0  23728  1028 ?        Ss   14:48   0:00 /sbin/mount.ntfs /dev/sda6 /media/jahid/Workplace -o rw
root       933  0.0  0.0  23748  1028 ?        Ss   14:48   0:00 /sbin/mount.ntfs /dev/sda7 /media/jahid/Storage -o rw
root       937  0.0  0.0      0     0 ?        S    14:48   0:00 [jbd2/sda9-8]
root       938  0.0  0.0      0     0 ?        S<   14:48   0:00 [ext4-rsv-conver]
root       952  0.0  0.1 273112  7832 ?        Ss   14:48   0:00 smbd -F
root       997  0.0  0.0  15272   636 ?        S    14:48   0:00 upstart-file-bridge --daemon
syslog    1051  0.0  0.0 255840  1604 ?        Ssl  14:48   0:00 rsyslogd
message+  1053  0.0  0.0  40608  2584 ?        Ss   14:48   0:00 dbus-daemon --system --fork
root      1099  0.0  0.0 334440  4520 ?        Ssl  14:48   0:00 /usr/sbin/ModemManager
root      1180  0.0  0.0  19556  2176 ?        Ss   14:48   0:00 /usr/sbin/bluetoothd
root      1185  0.0  0.0      0     0 ?        S<   14:48   0:00 [krfcommd]
root      1211  0.0  0.0  43448  1900 ?        Ss   14:48   0:00 /lib/systemd/systemd-logind
avahi     1222  0.0  0.0  32344  1620 ?        S    14:48   0:00 avahi-daemon: running [JAHID-PC.local]
avahi     1254  0.0  0.0  32220   464 ?        S    14:48   0:00 avahi-daemon: chroot helper
root      1328  0.0  0.0    188    36 ?        Ss   14:48   0:00 runsvdir -P /etc/service log: .................................................................................................
root      1329  0.0  0.0  23004   964 tty4     Ss+  14:48   0:00 /sbin/getty -8 38400 tty4
root      1333  0.0  0.0  23004   964 tty5     Ss+  14:48   0:00 /sbin/getty -8 38400 tty5
root      1341  0.0  0.0  23004   964 tty2     Ss+  14:48   0:00 /sbin/getty -8 38400 tty2
root      1343  0.0  0.0    168     4 ?        Ss   14:48   0:00 runsv git-daemon
gitlog    1345  0.0  0.0    184     4 ?        S    14:48   0:00 svlogd -tt /var/log/git-daemon
gitdaem+  1346  0.0  0.0  14072   876 ?        S    14:48   0:00 /usr/lib/git-core/git-daemon --verbose --reuseaddr --base-path=/var/lib /var/lib/git
root      1353  0.0  0.0  23004   964 tty3     Ss+  14:48   0:00 /sbin/getty -8 38400 tty3
root      1362  0.0  0.0  23004   964 tty6     Ss+  14:48   0:00 /sbin/getty -8 38400 tty6
root      1391  0.0  0.0 635112  6984 ?        Ssl  14:48   0:00 NetworkManager
root      1428  0.0  0.0 291320  5388 ?        Sl   14:48   0:00 /usr/lib/policykit-1/polkitd --no-debug
root      1445  0.0  0.0  61368  3060 ?        Ss   14:48   0:00 /usr/sbin/sshd -D
root      1475  0.0  0.0  75356  3412 ?        Ss   14:48   0:00 /usr/sbin/cups-browsed
root      1476  0.0  0.0  19188   768 ?        Ss   14:48   0:00 /usr/sbin/irqbalance
root      1485  0.0  0.0  23652  1028 ?        Ss   14:48   0:00 cron
daemon    1486  0.0  0.0  19136   160 ?        Ss   14:48   0:00 atd
mysql     1487  0.0  0.7 550648 56956 ?        Ssl  14:48   0:01 /usr/sbin/mysqld
kernoops  1528  0.0  0.0  37140  1008 ?        Ss   14:48   0:00 /usr/sbin/kerneloops
whoopsie  1560  0.0  0.0 357420  5192 ?        Ssl  14:48   0:00 whoopsie
root      1565  0.0  0.0   4364   712 ?        Ss   14:48   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1633  0.0  0.0 273112  3528 ?        S    14:48   0:00 smbd -F
root      1700  0.0  0.0  25340  1716 ?        Ss   14:48   0:00 /usr/lib/postfix/master
debian-+  1759  0.0  0.4  61852 32792 ?        S    14:48   0:02 /usr/bin/tor --defaults-torrc /usr/share/tor/tor-service-defaults-torrc --hush
root      1779  0.0  0.0      0     0 ?        S<   14:49   0:00 [iprt-VBoxWQueue]
root      1782  0.0  0.0      0     0 ?        S    14:49   0:00 [iprt-VBoxTscThr]
root      1816  0.4  0.1 286516 10052 ?        Ssl  14:49   0:13 /opt/teamviewer/tv_bin/teamviewerd -f
nobody    1819  0.0  0.0  38212  1560 ?        S    14:49   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager
root      1870  0.0  0.0  39900  1096 ?        Ssl  14:49   0:02 wimaxd -c /etc/wimaxd.conf
root      2001  0.0  0.0 277860  3756 ?        Ssl  14:49   0:00 lightdm
root      2011  0.0  0.0 287612  4332 ?        Sl   14:49   0:00 /usr/lib/accountsservice/accounts-daemon
root      2027  0.0  0.2 385160 18884 ?        Ss   14:49   0:00 /usr/sbin/apache2 -k start
root      2038  3.6  1.0 391076 78624 tty7     Ssl+ 14:49   1:48 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
www-data  2066  0.0  0.0 385192  7144 ?        S    14:49   0:00 /usr/sbin/apache2 -k start
www-data  2067  0.0  0.0 385192  7144 ?        S    14:49   0:00 /usr/sbin/apache2 -k start
www-data  2068  0.0  0.0 385192  7144 ?        S    14:49   0:00 /usr/sbin/apache2 -k start
www-data  2069  0.0  0.0 385192  7144 ?        S    14:49   0:00 /usr/sbin/apache2 -k start
www-data  2070  0.0  0.0 385192  7144 ?        S    14:49   0:00 /usr/sbin/apache2 -k start
root      2218  0.0  0.0 203328  4472 ?        Sl   14:49   0:00 lightdm --session-child 12 15
root      2231  0.0  0.0      0     0 ?        S    14:49   0:00 [kauditd]
jahid     2236  0.0  0.0  43176  2556 ?        Ss   14:49   0:00 init --user
root      2331  0.0  0.0  23004   960 tty1     Ss+  14:49   0:00 /sbin/getty -8 38400 tty1
root      2341  0.0  0.0 2100412 6016 ?        Sl   14:49   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      2741  0.0  0.1 301076 10772 ?        Ssl  14:49   0:00 /usr/bin/docker -d
root      2748  0.0  0.0 230512  5664 ?        Ss   14:49   0:00 /usr/sbin/winbindd -F
jahid     2763  0.0  0.0  40200  2228 ?        Ss   14:49   0:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-llEiOJMsSb
jahid     2777  0.0  0.0  25288  1172 ?        Ss   14:49   0:00 upstart-event-bridge
jahid     2784  0.0  0.0  81736  4656 ?        Ss   14:49   0:00 /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
root      2788  0.0  0.0 191444  2828 ?        Ss   14:49   0:00 nmbd -D
jahid     2791  0.0  0.0 373584  3560 ?        Sl   14:49   0:00 gnome-keyring-daemon --start --components ssh
root      2800  0.0  0.0 230512  3516 ?        S    14:49   0:00 /usr/sbin/winbindd -F
jahid     2865  0.0  0.0   4440   692 ?        Ss   14:49   0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
jahid     2876  0.0  0.1 326244  7888 ?        Sl   14:49   0:00 xfce4-session
jahid     2881  0.0  0.0  33772   748 ?        S    14:49   0:00 upstart-file-bridge --daemon --user
jahid     2882  0.0  0.0  25296   668 ?        S    14:49   0:00 upstart-dbus-bridge --daemon --system --user --bus-name system
jahid     2884  0.0  0.0  25296   676 ?        S    14:49   0:00 upstart-dbus-bridge --daemon --session --user --bus-name session
jahid     2922  0.0  0.0  39560  2628 ?        S    14:49   0:00 /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
jahid     2927  0.2  0.1 171628 13684 ?        S    14:49   0:08 xfwm4 --replace
jahid     2931  0.4  0.2 696760 20208 ?        Sl   14:49   0:13 xfce4-panel
jahid     2933  0.1  0.3 834784 29136 ?        Sl   14:49   0:04 Thunar --daemon
jahid     2935  0.0  0.4 857264 32456 ?        Sl   14:49   0:02 xfdesktop
jahid     2936  0.0  0.1 338172  9596 ?        Ssl  14:49   0:01 xfsettingsd
jahid     2942  0.0  0.4 192508 37864 ?        S    14:49   0:01 artha
jahid     2943  0.0  0.0 480672  6656 ?        Sl   14:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
jahid     2944  0.0  0.4 454876 33956 ?        Sl   14:49   0:00 /usr/bin/python /opt/extras.ubuntu.com/cuttlefish/bin/cuttlefish --hidden
jahid     2945  0.0  0.0 286748  5880 ?        Sl   14:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
jahid     2946  2.3  2.3 581360 180208 ?       Sl   14:49   1:11 skype %U
jahid     2947  0.0  0.0 266808  4960 ?        Sl   14:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
jahid     2948  0.0  0.2 929076 19780 ?        Sl   14:49   0:00 nm-applet
jahid     2950  0.0  0.0 281652  3340 ?        Sl   14:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
jahid     2951  0.0  0.2 224240 18652 ?        Sl   14:49   0:00 /usr/bin/python /usr/share/system-config-printer/applet.py
jahid     2952  0.0  0.1 550216 10128 ?        Sl   14:49   0:00 zeitgeist-datahub
jahid     2956  0.0  0.0 237368  7112 ?        Ssl  14:49   0:00 xfce4-power-manager
jahid     2957  0.0  0.3 759528 26376 ?        Sl   14:49   0:00 /usr/lib/evolution/3.10/evolution-alarm-notify
jahid     2961  0.0  0.2 655584 17856 ?        Sl   14:49   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
jahid     2962  0.0  0.4 732320 30640 ?        Sl   14:49   0:00 /usr/bin/python /usr/bin/blueman-applet
root      2966  0.0  0.0 304972  6764 ?        Sl   14:49   0:00 /usr/lib/upower/upowerd
jahid     2970  0.0  0.1 305812 11344 ?        Ssl  14:49   0:02 xfce4-volumed
jahid     2989  0.0  0.0 199632  3124 ?        Sl   14:49   0:00 /usr/lib/gvfs/gvfsd
jahid     2994  0.0  0.0 345660  3120 ?        Sl   14:49   0:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
jahid     3008  0.0  0.0 442696  7096 ?        S<l  14:49   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     3010  0.0  0.0 168912  1304 ?        SNl  14:49   0:00 /usr/lib/rtkit/rtkit-daemon
root      3092  0.0  0.0      0     0 ?        S    14:49   0:00 [kworker/2:2]
jahid     3104  0.0  0.0 348868  6884 ?        Sl   14:49   0:00 /usr/bin/zeitgeist-daemon
jahid     3110  0.0  0.1 252776  9972 ?        Sl   14:49   0:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts
jahid     3111  0.1  0.1 156840 10168 ?        S    14:49   0:05 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libnetload.so 1 8388647 netload
jahid     3112  0.0  0.0 157484  7492 ?        S    14:49   0:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 4 8388648 systray
jahid     3113  0.0  0.2 673528 21588 ?        Sl   14:49   0:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libindicator-plugin.so 30 83886
jahid     3114  0.0  0.1 156820 10172 ?        S    14:49   0:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libbattery.so 7 8388650 battery
jahid     3115  0.0  0.1 157336 10044 ?        S    14:49   0:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libdatetime.so 13 8388651 datet
jahid     3116  0.0  0.2 594136 16308 ?        Sl   14:49   0:02 /usr/lib/x86_64-linux-gnu/xfce4/panel-plugins/xfce4-xkb-plugin  2 8388652 xkb-plugin Keyboard Layouts Keyboard layouts setup an
jahid     3117  0.0  0.1 573440 10040 ?        Sl   14:49   0:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libactions.so 6 8388653 actions
jahid     3118  0.9  0.1 596640 14864 ?        Sl   14:49   0:28 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libwhiskermenu.so 12 8388657 wh
jahid     3119  0.0  0.1 252268 13904 ?        S    14:49   0:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libweather.so 40 8388659 weathe
jahid     3240  0.0  0.0 337536  3252 ?        Sl   14:49   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
jahid     3244  0.0  0.0  39244  1888 ?        S    14:49   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
jahid     3247  0.0  0.0 124912  3296 ?        Sl   14:49   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
jahid     3268  0.0  0.0      0     0 ?        Z    14:49   0:00 [bright_screen] <defunct>
jahid     3272  0.0  0.0  14400   616 ?        S    14:49   0:00 /bin/cat
jahid     3275  0.0  0.0  34356  1968 ?        S    14:49   0:00 init --user --startup-event indicator-services-start
jahid     3277  0.0  0.0 339136  3692 ?        Ssl  14:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
jahid     3284  0.0  0.1 1166196 13436 ?       Ssl  14:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
jahid     3324  0.0  0.0  60476  2904 ?        S    14:49   0:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
jahid     3426  0.0  0.1 574636 13272 ?        Sl   14:49   0:00 /usr/lib/evolution/evolution-source-registry
jahid     3427  0.1  1.7 2889156 135388 ?      Sl   14:49   0:04 /home/jahid/.dropbox-dist/dropbox-lnx.x86_64-3.16.1/dropbox /newerversion
jahid     3439  0.0  0.1 654188  7920 ?        Sl   14:49   0:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
root      3446  0.0  0.0 371624  5540 ?        Sl   14:49   0:00 /usr/lib/udisks2/udisksd --no-debug
jahid     3468  0.0  0.0  60984  2440 ?        S    14:49   0:00 /usr/bin/obex-data-server --no-daemon 
jahid     3473  0.0  0.0 128044  3308 ?        Sl   14:49   0:00 /usr/lib/gvfs/gvfsd-metadata
jahid     3480  0.0  0.7 1370768 55404 ?       Sl   14:49   0:00 /usr/lib/evolution/evolution-calendar-factory
root      3488  0.0  0.0  76856  3700 ?        Ss   14:49   0:00 /usr/sbin/cupsd -f
jahid     3503  0.0  0.0 215432  3408 ?        Sl   14:49   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
jahid     3532  0.0  0.0 288960  3368 ?        Sl   14:49   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
jahid     3537  0.0  0.0 203268  2848 ?        Sl   14:49   0:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
jahid     3747 24.2  9.9 2148308 753792 ?      Sl   14:50  11:56 /usr/lib/firefox/firefox
root      4197  0.0  0.0      0     0 ?        S    14:55   0:00 [kworker/u16:0]
jahid     4339  0.0  0.0 362404  3592 ?        Sl   15:02   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.25 /org/gtk/gvfs/exec_spaw/0
jahid     4347  0.3  0.8 1281464 61624 ?       SNl  15:02   0:07 /usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd
jahid     4363  0.0  0.0 178428  4876 ?        Sl   15:02   0:00 /usr/lib/dconf/dconf-service
root      4486  0.0  0.0      0     0 ?        S    15:08   0:00 [kworker/3:1]
root      4487  0.0  0.0      0     0 ?        S    15:08   0:00 [kworker/2:0]
jahid     4733  0.0  0.2 579008 16468 ?        Sl   15:08   0:00 /usr/bin/gnome-screensaver --no-daemon
root      4738  0.0  0.0      0     0 ?        S    15:08   0:00 [kworker/1:1]
root      5494  0.0  0.0      0     0 ?        S    15:31   0:00 [kworker/0:0]
root      5586  0.0  0.0  10228  3768 ?        S    15:31   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-eth2.pid 
jahid     5610  0.0  0.1 408432 13288 ?        Sl   15:31   0:00 /usr/lib/x86_64-linux-gnu/xfce4/notifyd/xfce4-notifyd
postfix   5683  0.0  0.0  27456  1560 ?        S    15:31   0:00 qmgr -l -t unix -u
postfix   5684  0.0  0.0  27404  1532 ?        S    15:31   0:00 pickup -l -t unix -u -c
jahid     5864  0.0  0.0  20228   932 ?        S    15:31   0:00 syndaemon -i 2.0 -K -R
ntp       5898  0.0  0.0  33508  2100 ?        Ss   15:31   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 118:128
jahid     5911  5.8  0.4 784056 35040 ?        Sl   15:32   0:24 gnome-system-monitor
jahid     5939  0.0  0.0   4440   656 ?        S    15:34   0:00 /bin/sh /usr/bin/synaptic-pkexec
root      5940  1.1  1.8 703500 137520 ?       Sl   15:34   0:03 /usr/sbin/synaptic
root      5953  0.0  0.0  24436   588 ?        S    15:34   0:00 dbus-launch --autolaunch=e50a31d4da744c1ed9030ce7540f988e --binary-syntax --close-stderr
root      5954  0.0  0.0  39112  1024 ?        Ss   15:34   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
jahid     6036  0.4  0.2 732320 16504 ?        Sl   15:36   0:00 /usr/bin/xfce4-terminal
jahid     6041  0.0  0.0  14820   808 ?        S    15:36   0:00 gnome-pty-helper
jahid     6042  0.0  0.0  31804  5796 pts/0    Ss   15:36   0:00 bash
root      6084  0.0  0.0      0     0 ?        S    15:38   0:00 [kworker/u16:1]
jahid     6122  0.0  0.0  25632  1332 pts/0    R+   15:39   0:00 ps aux


```

---

### Post by HermanAB on 2016-03-26
Look in the crontab files as well as /etc/cron.hourly, daily, weekly...

---

### Post by Habitual on 2016-03-28
Are either of these found?
```
ls -al ~/.mozilla/firefox/profiled ~/.dropbox/DropboxCache
```

---

### Post by Jahidul_Hamid on 2016-03-29
> **Habitual said:**
> Are either of these found?
```
ls -al ~/.mozilla/firefox/profiled ~/.dropbox/DropboxCache
```

No.

---

