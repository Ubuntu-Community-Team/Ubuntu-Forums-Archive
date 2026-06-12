---
title: "Problem with Deepin OS"
date: 2015-01-12
forum: Ubuntu/Debian BASED
---

### Post by jesus-freak on 2015-01-12
Hello, I have been having a major problem with Deepin. I first installed it over a month ago and I really love it. However, I was having a lot of trouble with it freezing and not opening applications. Even if an application was already open and just minimized, I could click on it to maximize it and it would just freeze and I would have to wait in between 15 seconds to 45 seconds for everything to un-freeze and for the program to maximize. At the time I was running Deepin on an old hard drive and so I assumed that the hard drive was dying and causing these issues. So I got a new Solid Sates Hard drive, installed Deepin and it starts up super fast and runs super fast but there are still times when the exact same things happens just like before and everything freezes up and I just have to wait for it to un-freeze. I have 4GB of Ram so I don't think it's an issue of not having enough Ram. 4GB is enough to run most OS's with out major issues. So then I launched my system monitor and I noticed that it seemed to be using way to much swap, some times a higher % of swap than of physical memory. That didn't seem right to me so I changed the swappiness all the way to 0 but it doesn't seem to have changed anything significantly. I use this computer for work and so I need it running good. I love Deepin but if I can't get this fixed I'll have to move on to another OS because this never happened to me before. Here are the specs of my laptop 
[http://www.pcmag.com/article2/0,2817,23 ... ?tab=Specs]("http://www.pcmag.com/article2/0,2817,23 ... ?tab=Specs")
Here is the "Top" command results with everything running that I would normally use for my work.
```
top - 11:02:28 up  2:07,  1 user,  load average: 1.00, 1.27, 1.47
Tasks: 213 total,   1 running, 212 sleeping,   0 stopped,   0 zombie
%Cpu(s): 21.2 us,  7.7 sy,  0.0 ni, 68.4 id,  2.6 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   3839812 total,  3721412 used,   118400 free,     9236 buffers
KiB Swap:  3027964 total,   549508 used,  2478456 free.  2170168 cached Mem
 
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1027 root      20   0  977924 345476 331736 S   5.9  9.0  13:24.53 Xorg
22034 justdrea  20   0  749512 121620   7240 S   5.9  3.2   0:18.16 skype
22438 justdrea  20   0   24960   1464   1048 R   5.9  0.0   0:00.03 top
    1 root      20   0   33912   1412      0 S   0.0  0.0   0:01.93 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.30 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   0:13.54 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:04.57 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:04.08 rcuos/1
   10 root      20   0       0      0      0 S   0.0  0.0   0:04.55 rcuos/2
   11 root      20   0       0      0      0 S   0.0  0.0   0:04.24 rcuos/3
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/4
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/5
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/6
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/7
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1
   19 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2
   20 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/4
   22 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/5
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/6
   24 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/7
   25 root      rt   0       0      0      0 S   0.0  0.0   0:00.60 migration/0
   26 root      rt   0       0      0      0 S   0.0  0.0   0:00.07 watchdog/0
   27 root      rt   0       0      0      0 S   0.0  0.0   0:00.07 watchdog/1
   28 root      rt   0       0      0      0 S   0.0  0.0   0:02.29 migration/1
   29 root      20   0       0      0      0 S   0.0  0.0   0:00.25 ksoftirqd/1
   31 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H
   32 root      rt   0       0      0      0 S   0.0  0.0   0:00.06 watchdog/2
   33 root      rt   0       0      0      0 S   0.0  0.0   0:00.34 migration/2
   34 root      20   0       0      0      0 S   0.0  0.0   0:00.28 ksoftirqd/2
   36 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0H
   37 root      rt   0       0      0      0 S   0.0  0.0   0:00.08 watchdog/3
   38 root      rt   0       0      0      0 S   0.0  0.0   0:00.24 migration/3
   39 root      20   0       0      0      0 S   0.0  0.0   0:00.22 ksoftirqd/3
   40 root      20   0       0      0      0 S   0.0  0.0   0:12.38 kworker/3:0
   41 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0H
   42 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   43 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   44 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   45 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   46 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   47 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   49 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   50 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   51 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khubd
   52 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
   53 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
   57 root      20   0       0      0      0 S   0.0  0.0   0:00.01 khungtaskd
   58 root      20   0       0      0      0 S   0.0  0.0   3:09.23 kswapd0
   59 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   60 root      39  19       0      0      0 S   0.0  0.0   0:02.50 khugepaged
   61 root      20   0       0      0      0 S   0.0  0.0   0:00.01 fsnotify_mark
   62 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-kthrea
   63 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   75 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
   98 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   99 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_manager
  157 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
  172 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  177 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  178 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_2
  179 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_3
  180 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_4
  181 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_5
  213 root      20   0       0      0      0 S   0.0  0.0   0:01.92 jbd2/sda1-8
  214 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-conver
  324 root      20   0   19736    196      0 S   0.0  0.0   0:00.23 upstart-udev-br
  330 root      20   0   51704    156      4 S   0.0  0.0   0:00.11 systemd-udevd
  373 root     -51   0       0      0      0 S   0.0  0.0   0:00.00 irq/42-mei_me
  376 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 cfg80211
  382 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmemstick
  383 root     -51   0       0      0      0 S   0.0  0.0   0:38.40 irq/43-iwlwifi
  400 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 iwlwifi
  436 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmpathd
  438 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmpath_handlerd
  466 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kvm-irqfd-clean
  479 message+  20   0   40564   1876    704 S   0.0  0.0   0:09.76 dbus-daemon
  514 root      20   0    4444      8      4 S   0.0  0.0   0:00.00 bluetooth
  528 root      20   0   19088    292    168 S   0.0  0.0   0:00.00 bluetoothd
  544 root      20   0   43452    616    488 S   0.0  0.0   0:00.05 systemd-logind
  547 syslog    20   0  255844    236     60 S   0.0  0.0   0:01.15 rsyslogd
  575 root      20   0       0      0      0 S   0.0  0.0   0:00.08 ips-adjust
  578 root      20   0       0      0      0 S   0.0  0.0   0:01.94 ips-monitor
  579 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio0
  586 root      20   0   74720      0      0 S   0.0  0.0   0:00.01 cupsd
  595 avahi     20   0   32348    264     56 S   0.0  0.0   0:00.15 avahi-daemon
  601 avahi     20   0   32224     68      0 S   0.0  0.0   0:00.00 avahi-daemon
  652 root      20   0  330232      0      0 S   0.0  0.0   0:00.02 ModemManager
  700 root      20   0   15820      8      4 S   0.0  0.0   0:00.00 getty
  701 root      20   0  352440   2788   1728 S   0.0  0.1   0:06.48 NetworkManager
  703 root      20   0   15820      8      4 S   0.0  0.0   0:00.00 getty
  709 root      20   0   15820      8      4 S   0.0  0.0   0:00.00 getty
  710 root      20   0  297152   1884    584 S   0.0  0.0   0:00.39 dde-system-daem
  715 root      20   0   15820      8      4 S   0.0  0.0   0:00.00 getty
  717 root      20   0 2094236    528    528 S   0.0  0.0   0:00.15 console-kit-dae
  784 root      20   0   15820      8      4 S   0.0  0.0   0:00.00 getty
  797 root      20   0  295996   4432    976 S   0.0  0.1   0:00.59 polkitd
  849 root      20   0   23656    268    156 S   0.0  0.0   0:00.02 cron
  850 daemon    20   0   19140     24      0 S   0.0  0.0   0:00.00 atd
  854 root      20   0   19188    376    268 S   0.0  0.0   0:01.42 irqbalance
  972 root      20   0    4444      4      0 S   0.0  0.0   0:00.00 sh
  977 root      20   0   15732    344      4 S   0.0  0.0   0:00.02 initctl
  986 root      20   0    4368     28      0 S   0.0  0.0   0:00.96 acpid
  996 root      20   0  366392     32      4 S   0.0  0.0   0:00.03 lightdm
 1024 root      20   0   16200    124      0 S   0.0  0.0   0:00.02 upstart-file-br
 1031 root      20   0  302232    320    108 S   0.0  0.0   0:00.56 accounts-daemon
 1041 root      20   0   16048    104      0 S   0.0  0.0   0:00.02 upstart-socket-
 1123 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
 1191 root      20   0    4444      4      0 S   0.0  0.0   0:00.00 _plutorun
 1192 root      20   0    4340      4      0 S   0.0  0.0   0:00.00 logger
 1193 root      20   0    4444      4      0 S   0.0  0.0   0:00.00 _plutorun
 1194 root      20   0    4444      0      0 S   0.0  0.0   0:00.00 _plutoload
 1197 root      20   0   94060     84      0 S   0.0  0.0   0:00.04 pluto
 1224 root      30  10   94068     20      0 S   0.0  0.0   0:00.00 pluto
 1225 root      30  10   94068     20      0 S   0.0  0.0   0:00.00 pluto
 1227 root      30  10   94068     20      0 S   0.0  0.0   0:00.00 pluto
 1264 root      20   0    4440      4      0 S   0.0  0.0   0:00.00 xl2tpd
 1361 root      20   0   15820      8      4 S   0.0  0.0   0:00.00 getty
 1395 root      20   0    6356      0      0 S   0.0  0.0   0:00.00 _pluto_adns
 1422 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1423 root      20   0       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1424 root      20   0       0      0      0 S   0.0  0.0   0:00.01 i2400m-usb:1-1.
 1441 root      20   0   30608   1168    984 S   0.0  0.0   0:01.93 wpa_supplicant
 1472 root      20   0  174620      0      0 S   0.0  0.0   0:00.02 lightdm
 1489 justdrea  20   0 1409360   8916   1936 S   0.0  0.2   1:15.30 startdde
 1531 justdrea  20   0   10616     36      0 S   0.0  0.0   0:00.07 ssh-agent
 1534 justdrea  20   0   24440      0      0 S   0.0  0.0   0:00.00 dbus-launch
 1535 justdrea  20   0   44740   5728    632 S   0.0  0.1   3:42.45 dbus-daemon
 1558 justdrea  20   0  349236   7124   3184 S   0.0  0.2   0:27.80 gtk-window-deco
 1559 justdrea  20   0  504652  11712   2628 S   0.0  0.3   6:40.40 compiz
 1572 justdrea  20   0  178296   1248    808 S   0.0  0.0   0:01.14 dconf-service
 1591 justdrea  20   0  320088   4260    752 S   0.0  0.1   0:00.17 gvfs-udisks2-vo
 1594 root      20   0  386168   4108    460 S   0.0  0.1   0:02.62 udisksd
 1601 justdrea  20   0  192444   1192    588 S   0.0  0.0   0:00.07 gvfsd
 1609 justdrea  20   0  208244   1196    644 S   0.0  0.0   0:00.05 gvfs-gphoto2-vo
 1613 justdrea  20   0  291908   3476    424 S   0.0  0.1   0:00.06 gvfs-afc-volume
 1618 justdrea  20   0  183324   2936    504 S   0.0  0.1   0:00.06 gvfs-goa-volume
 1622 justdrea  20   0  196080   1136    508 S   0.0  0.0   0:00.05 gvfs-mtp-volume
 1627 justdrea  20   0  367572   2324      0 S   0.0  0.1   0:00.02 at-spi-bus-laun
 1631 justdrea  20   0   39248    952    528 S   0.0  0.0   0:00.08 dbus-daemon
 1634 justdrea  20   0  124912    960    380 S   0.0  0.0   0:00.19 at-spi2-registr
 1654 root      20   0  253792   2256    924 S   0.0  0.1   0:00.18 upowerd
 1658 root      20   0   10232   2288      0 S   0.0  0.1   0:00.00 dhclient
 1683 justdrea   9 -11  369696   3084   1048 S   0.0  0.1   6:34.93 pulseaudio
 1685 rtkit     21   1  168916    228      0 S   0.0  0.0   0:00.15 rtkit-daemon
 1702 root      20   0  143064  11400      0 S   0.0  0.3   0:15.84 teamviewerd
 1719 nobody    20   0   31028    388    188 S   0.0  0.0   0:00.75 dnsmasq
 1759 justdrea  20   0 2496748  36240  11652 S   0.0  0.9   0:18.74 dde-launcher
 1762 justdrea  20   0 2154840  24944   9376 S   0.0  0.6   0:34.65 dde-desktop
 1783 justdrea  20   0  370116    992      0 S   0.0  0.0   0:00.12 gvfsd-trash
 1796 justdrea  20   0 2169568 166792  10196 S   0.0  4.3   7:20.37 dde-dock
 1827 justdrea  20   0   53524   1832    784 S   0.0  0.0   0:00.22 gconfd-2
 1836 justdrea  20   0  318916   6456   1060 S   0.0  0.2   4:06.75 mousearea
 1907 justdrea  20   0  218180   1600    612 S   0.0  0.0   0:00.20 polkit-gnome-au
 1918 justdrea  20   0  456348   7620    792 S   0.0  0.2   0:01.10 deepin-menu
 2244 justdrea  20   0 1075248 119392  22764 S   0.0  3.1  17:54.10 maxthon
 2257 justdrea  20   0  309668   6836   1480 S   0.0  0.2   0:09.02 maxthon
 2258 justdrea  20   0    6500     80      0 S   0.0  0.0   0:00.00 maxthon_sandbox
 2259 justdrea  20   0  352492   5964      0 S   0.0  0.2   0:00.23 maxthon
 2266 justdrea  20   0  140904   1300      0 S   0.0  0.0   0:00.01 nacl_helper
 2267 justdrea  20   0  360688   6316    280 S   0.0  0.2   0:00.09 maxthon
 2312 justdrea  20   0 1063372 115264   6180 S   0.0  3.0   3:40.57 maxthon
 2346 justdrea  20   0 1107936 122992  17300 S   0.0  3.2   1:59.03 maxthon
 2361 justdrea  20   0  500288  26548   7800 S   0.0  0.7   4:17.69 maxthon
 2366 justdrea  20   0  388896   4160      8 S   0.0  0.1   0:00.00 maxthon
 2370 justdrea  20   0  340728  10232   1528 S   0.0  0.3   0:19.66 maxthon
 2544 root      20   0       0      0      0 S   0.0  0.0   0:11.66 kworker/1:2
 2963 justdrea  20   0 1024916  23312   6980 S   0.0  0.6   0:14.59 nautilus
 2977 justdrea  20   0  266180    576      0 S   0.0  0.0   0:00.01 gvfsd-burn
 3007 justdrea  20   0  120392    748      0 S   0.0  0.0   0:00.03 gvfsd-metadata
11265 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:1
11859 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 xfsalloc
11860 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 xfs_mru_cache
11861 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 xfslogd
11867 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsIO
11868 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
11869 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
11870 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
11871 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
11872 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsSync
11891 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
19249 justdrea  20   0  821840  43424   6544 S   0.0  1.1   1:51.90 dde-dock-applet
19338 justdrea  20   0  165676   9080    732 S   0.0  0.2   0:00.35 dsc-daemon
20164 root      20   0       0      0      0 S   0.0  0.0   0:08.66 kworker/2:0
20386 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/1:1
20415 root      20   0       0      0      0 S   0.0  0.0   0:07.38 kworker/0:1
20478 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/2:1
21464 justdrea  20   0 1059276  93396    148 S   0.0  2.4   0:08.14 maxthon
21781 root       0 -20       0      0      0 S   0.0  0.0   0:00.06 kworker/u17:0
21783 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:2
21838 justdrea  20   0 1014176  54524   9372 S   0.0  1.4   1:29.74 maxthon
21954 root      20   0       0      0      0 S   0.0  0.0   0:00.97 kworker/u16:2
21968 root      20   0       0      0      0 S   0.0  0.0   0:00.86 kworker/u16:0
22022 root       0 -20       0      0      0 S   0.0  0.0   0:00.02 kworker/u17:1
22026 root      20   0       0      0      0 S   0.0  0.0   0:00.19 kworker/u16:3
22081 root      20   0       0      0      0 S   0.0  0.0   0:00.34 kworker/0:0
22114 justdrea  20   0  347724  25256  17520 S   0.0  0.7   0:00.49 skype-call-reco
22117 justdrea  20   0  550444  32052  20600 S   0.0  0.8   0:14.11 audacity
22204 justdrea  20   0 2909840 141892  15508 S   0.0  3.7   1:32.22 dde-session-dae
22214 justdrea  20   0    4444    656    552 S   0.0  0.0   0:00.00 sh
22215 justdrea  20   0   20232    944    772 S   0.0  0.0   0:00.16 syndaemon
22365 justdrea  20   0  787300  82616  22656 S   0.0  2.2   0:05.69 evince
22373 justdrea  20   0  104436   2444   2044 S   0.0  0.1   0:00.01 evinced
22390 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u17:2
22392 justdrea  20   0  977720  60968  23784 S   0.0  1.6   0:02.32 maxthon
22406 justdrea  20   0  627768 102524  18656 S   0.0  2.7   0:01.92 deepin-terminal
22416 justdrea  20   0   14824    820    664 S   0.0  0.0   0:00.01 gnome-pty-helpe
22417 justdrea  20   0   40476   4256   2084 S   0.0  0.1   0:00.30 zsh
22437 root      20   0   78380   9956   4008 S   0.0  0.3   0:00.12 deepin-store-ba
```
Can anyone see any problems here? I really need help with this!! Thanks

---

### Post by jesus-freak on 2015-01-13
I was able to get two Top results while the system was experiencing difficulty. I placed a skype call and this caused the system to freeze up. Here are the results.
```
top - 13:11:50 up 8 min,  1 user,  load average: 1.12, 0.90, 0.46
Tasks: 202 total,   1 running, 201 sleeping,   0 stopped,   0 zombie
%Cpu(s): 25.8 us,  4.9 sy,  0.0 ni, 68.9 id,  0.4 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   3839812 total,  3172748 used,   667064 free,    42012 buffers
KiB Swap:  3027964 total,        0 used,  3027964 free.  1812416 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 2344 justdrea  20   0  729172 151532  51184 S  54.7  3.9   0:44.70 skype
 1686 justdrea   9 -11  435380   6596   4260 S  30.4  0.2   0:12.60 pulseaudio
 2760 justdrea  20   0 2800116  70896  17188 S  30.4  1.8   1:20.83 dde-session-dae
 1531 justdrea  20   0   40324   2372    836 S  12.2  0.1   0:12.84 dbus-daemon
 2858 justdrea  20   0  694264  72776  32900 S  12.2  1.9   0:05.54 dde-control-cen
 1556 justdrea  20   0  504400  27848  12996 S   6.1  0.7   0:15.83 compiz
 1854 justdrea  20   0  827628  68476  31468 S   6.1  1.8   0:06.59 dde-dock-applet
 1926 justdrea  20   0  301052   9044   4616 S   6.1  0.2   0:08.15 mousearea
 2436 justdrea  20   0  588840  36792  25028 S   6.1  1.0   0:05.38 skype-call-reco
 2925 justdrea  20   0   24952   1468   1048 R   6.1  0.0   0:00.02 top
    1 root      20   0   33900   3220   1468 S   0.0  0.1   0:02.98 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/0
    4 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   0:01.32 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.62 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.44 rcuos/1
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.59 rcuos/2
   11 root      20   0       0      0      0 S   0.0  0.0   0:00.47 rcuos/3
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/4
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/5
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/6
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/7
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1
   19 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2
   20 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/4
   22 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/5
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/6
   24 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/7
   25 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/0
   26 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/0
   27 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1
   28 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 migration/1
   29 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/1
   30 root      20   0       0      0      0 S   0.0  0.0   0:00.55 kworker/1:0
   31 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H
   32 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/2
   33 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 migration/2
   34 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/2
   36 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0H
   37 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/3
   38 root      rt   0       0      0      0 S   0.0  0.0   0:00.12 migration/3
   39 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/3
   40 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0
   41 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0H
   42 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   43 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kdevtmpfs
   44 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   45 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   46 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   47 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   48 root       0 -20       0      0      0 S   0.0  0.0   0:00.02 kworker/u17:0
   49 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   50 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   51 root      20   0       0      0      0 S   0.0  0.0   0:00.01 khubd
   52 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
   53 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
   54 root      20   0       0      0      0 S   0.0  0.0   0:00.55 kworker/0:1
   55 root      20   0       0      0      0 S   0.0  0.0   0:00.53 kworker/3:1
   57 root      20   0       0      0      0 S   0.0  0.0   0:00.66 kworker/2:1
   59 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd
   60 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kswapd0
   61 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   62 root      39  19       0      0      0 S   0.0  0.0   0:00.01 khugepaged
   63 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_mark
   64 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-kthrea
   65 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   77 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
   98 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   99 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_manager
  154 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
  159 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  160 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  161 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_2
  169 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_3
  172 root      20   0       0      0      0 S   0.0  0.0   0:00.01 scsi_eh_4
  177 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_5
  180 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u16:2
  181 root      20   0       0      0      0 S   0.0  0.0   0:00.28 kworker/u16:3
  183 root      20   0       0      0      0 S   0.0  0.0   0:00.35 kworker/u16:4
  185 root      20   0       0      0      0 S   0.0  0.0   0:00.20 kworker/u16:6
  194 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/1:2
  213 root      20   0       0      0      0 S   0.0  0.0   0:00.12 jbd2/sda1-8
  214 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-conver
  324 root      20   0   20004   1180    612 S   0.0  0.0   0:00.50 upstart-udev-br
  329 root      20   0   51704   1860   1012 S   0.0  0.0   0:00.25 systemd-udevd
  338 root       0 -20       0      0      0 S   0.0  0.0   0:00.02 kworker/u17:1
  378 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmpathd
  379 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmpath_handlerd
  423 message+  20   0   40092   2308   1008 S   0.0  0.1   0:01.80 dbus-daemon
  437 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 cfg80211
  438 root     -51   0       0      0      0 S   0.0  0.0   0:00.00 irq/42-mei_me
  440 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmemstick
  442 root     -51   0       0      0      0 S   0.0  0.0   0:01.80 irq/43-iwlwifi
  455 root      20   0    4444    784    604 S   0.0  0.0   0:00.00 bluetooth
  458 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ips-adjust
  459 root      20   0       0      0      0 S   0.0  0.0   0:00.09 ips-monitor
  467 root      20   0   19088   1724   1500 S   0.0  0.0   0:00.08 bluetoothd
  484 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 iwlwifi
  487 root      20   0   43532   1908   1508 S   0.0  0.0   0:00.05 systemd-logind
  507 syslog    20   0  255844   3200    816 S   0.0  0.1   0:00.25 rsyslogd
  531 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kvm-irqfd-clean
  536 avahi     20   0   32348   1616   1308 S   0.0  0.0   0:00.05 avahi-daemon
  543 root      20   0   74720   3700   2644 S   0.0  0.1   0:00.02 cupsd
  547 avahi     20   0   32224    472    216 S   0.0  0.0   0:00.00 avahi-daemon
  585 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio0
  641 root      20   0  330232   4408   3268 S   0.0  0.1   0:00.05 ModemManager
  690 root      20   0  352548   7168   5508 S   0.0  0.2   0:01.04 NetworkManager
  710 root      20   0  295992   5932   3740 S   0.0  0.2   0:00.24 polkitd
  716 root      20   0    4444    656    552 S   0.0  0.0   0:00.00 sh
  720 root      20   0   15868   1588    876 S   0.0  0.0   0:00.12 initctl
  722 root      20   0   15820    968    808 S   0.0  0.0   0:00.00 getty
  724 root      20   0   15820    968    808 S   0.0  0.0   0:00.00 getty
  730 root      20   0   15820    972    808 S   0.0  0.0   0:00.00 getty
  731 root      20   0  297408  10168   4024 S   0.0  0.3   0:00.14 dde-system-daem
  736 root      20   0   15820    960    808 S   0.0  0.0   0:00.00 getty
  739 root      20   0 2092100   3604   2588 S   0.0  0.1   0:00.06 console-kit-dae
  745 root      20   0   15820    968    808 S   0.0  0.0   0:00.00 getty
  880 root      20   0   23656   1036    792 S   0.0  0.0   0:00.00 cron
  882 daemon    20   0   19140    160      0 S   0.0  0.0   0:00.00 atd
  899 root      20   0    4368    708    532 S   0.0  0.0   0:00.01 acpid
  918 root      20   0   19188    720    492 S   0.0  0.0   0:00.07 irqbalance
  947 root      20   0  292652   4592   3660 S   0.0  0.1   0:00.06 lightdm
  969 root      20   0  461236 121332 110360 S   0.0  3.2   0:31.56 Xorg
  972 root      20   0  302232   4976   3920 S   0.0  0.1   0:00.20 accounts-daemon
  976 root      20   0   16464   1776    384 S   0.0  0.0   0:00.06 upstart-file-br
  980 root      20   0   15920   1300    388 S   0.0  0.0   0:00.05 upstart-socket-
 1004 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
 1028 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1029 root      20   0       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1030 root      20   0       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1132 root      20   0   30608   2672   2096 S   0.0  0.1   0:00.14 wpa_supplicant
 1225 root      20   0    4444    116      0 S   0.0  0.0   0:00.00 _plutorun
 1226 root      20   0    4340    656    552 S   0.0  0.0   0:00.00 logger
 1227 root      20   0    4444    304    188 S   0.0  0.0   0:00.00 _plutorun
 1228 root      20   0    4444    644    540 S   0.0  0.0   0:00.00 _plutoload
 1229 root      20   0   94060   3832   2876 S   0.0  0.1   0:00.02 pluto
 1249 root      30  10   94068   1116    196 S   0.0  0.0   0:00.00 pluto
 1250 root      30  10   94068   1116    196 S   0.0  0.0   0:00.00 pluto
 1252 root      30  10   94068   1116    196 S   0.0  0.0   0:00.00 pluto
 1312 root      20   0    4440    328    216 S   0.0  0.0   0:00.00 xl2tpd
 1380 root      20   0   15820    964    808 S   0.0  0.0   0:00.00 getty
 1429 root      20   0    6356    384    296 S   0.0  0.0   0:00.00 _pluto_adns
 1464 root      20   0  174620   3820   3000 S   0.0  0.1   0:00.04 lightdm
 1481 justdrea  20   0 1486552  23632  10236 S   0.0  0.6   0:03.87 startdde
 1527 justdrea  20   0   10616    316      0 S   0.0  0.0   0:00.00 ssh-agent
 1530 justdrea  20   0   24440    580    332 S   0.0  0.0   0:00.00 dbus-launch
 1555 justdrea  20   0  348384  15896  10844 S   0.0  0.4   0:06.64 gtk-window-deco
 1569 justdrea  20   0  178296   2696   2172 S   0.0  0.1   0:00.16 dconf-service
 1590 justdrea  20   0  320088   6016   4352 S   0.0  0.2   0:00.09 gvfs-udisks2-vo
 1594 root      20   0  386168   6076   4220 S   0.0  0.2   0:00.37 udisksd
 1607 justdrea  20   0  192444   3004   2464 S   0.0  0.1   0:00.04 gvfsd
 1618 justdrea  20   0  208244   3368   2632 S   0.0  0.1   0:00.04 gvfs-gphoto2-vo
 1622 justdrea  20   0  291908   4208   3228 S   0.0  0.1   0:00.04 gvfs-afc-volume
 1627 justdrea  20   0  183324   4596   2128 S   0.0  0.1   0:00.03 gvfs-goa-volume
 1631 justdrea  20   0  196080   2800   2252 S   0.0  0.1   0:00.04 gvfs-mtp-volume
 1635 justdrea  20   0  367572   6392   3616 S   0.0  0.2   0:00.02 at-spi-bus-laun
 1639 justdrea  20   0   39116   1884   1488 S   0.0  0.0   0:00.03 dbus-daemon
 1642 justdrea  20   0  124912   3312   2756 S   0.0  0.1   0:00.07 at-spi2-registr
 1663 root      20   0  253792   5352   4008 S   0.0  0.1   0:00.13 upowerd
 1688 rtkit     21   1  168916   1304   1084 S   0.0  0.0   0:00.01 rtkit-daemon
 1707 root      20   0   10232   3724   1440 S   0.0  0.1   0:00.00 dhclient
 1710 root      20   0  143060  15340   3976 S   0.0  0.4   0:00.83 teamviewerd
 1727 nobody    20   0   31028   1524   1280 S   0.0  0.0   0:00.12 dnsmasq
 1776 justdrea  20   0 2062648  36840  19876 S   0.0  1.0   0:04.38 dde-desktop
 1794 justdrea  20   0  369988   4436   3600 S   0.0  0.1   0:00.06 gvfsd-trash
 1845 justdrea  20   0  414200  21096  15952 S   0.0  0.5   0:00.44 deepin-menu
 1862 justdrea  20   0  238792  10320   6776 S   0.0  0.3   0:00.30 polkit-gnome-au
 1870 justdrea  20   0 2378372  92588  31548 S   0.0  2.4   0:08.34 dropbox
 1917 justdrea  20   0   53428   3112   2068 S   0.0  0.1   0:00.05 gconfd-2
 1930 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/2:2
 1964 justdrea  20   0    4444    644    544 S   0.0  0.0   0:00.00 sh
 1967 justdrea  20   0 1361172  51096  22640 S   0.0  1.3   0:04.47 variety
 2077 justdrea  20   0 2369760  57156  21548 S   0.0  1.5   0:20.21 dde-dock
 2097 justdrea  20   0 1010600 131336  50900 S   0.0  3.4   0:32.81 maxthon
 2110 justdrea  20   0  309700   9192   3044 S   0.0  0.2   0:02.74 maxthon
 2111 justdrea  20   0    6500    392    312 S   0.0  0.0   0:00.00 maxthon_sandbox
 2112 justdrea  20   0  352492  24052  17384 S   0.0  0.6   0:00.19 maxthon
 2119 justdrea  20   0  140904   4624   3328 S   0.0  0.1   0:00.02 nacl_helper
 2120 justdrea  20   0  360688   7444    764 S   0.0  0.2   0:00.03 maxthon
 2165 justdrea  20   0 1060292 123852  17636 S   0.0  3.2   0:16.31 maxthon
 2195 justdrea  20   0 2511712  57428  33276 S   0.0  1.5   0:03.61 dde-launcher
 2218 justdrea  20   0  340664  24116  15144 S   0.0  0.6   0:00.89 maxthon
 2219 justdrea  20   0 1059140 108212  16908 S   0.0  2.8   0:06.30 maxthon
 2248 justdrea  20   0  995220  63036  24228 S   0.0  1.6   0:05.45 maxthon
 2264 justdrea  20   0 1097632 134996  31156 S   0.0  3.5   0:21.03 maxthon
 2277 justdrea  20   0  432300  40352  24348 S   0.0  1.1   0:02.29 maxthon
 2282 justdrea  20   0  388960   8096    256 S   0.0  0.2   0:00.00 maxthon
 2306 justdrea  20   0  988944  48808  19540 S   0.0  1.3   0:01.14 maxthon
 2318 justdrea  20   0  980984  55980  24520 S   0.0  1.5   0:04.93 maxthon
 2330 justdrea  20   0  979752  56960  24040 S   0.0  1.5   0:03.50 maxthon
 2708 justdrea  20   0  628680 104276  18968 S   0.0  2.7   0:05.46 deepin-terminal
 2720 justdrea  20   0   14824    820    664 S   0.0  0.0   0:00.00 gnome-pty-helpe
 2721 justdrea  20   0   40476   4256   2084 S   0.0  0.1   0:00.29 zsh
 2770 justdrea  20   0    4444    656    552 S   0.0  0.0   0:00.00 sh
 2771 justdrea  20   0   20232    940    772 S   0.0  0.0   0:00.07 syndaemon
 2792 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u17:2
 2808 justdrea  20   0  299148   9192   4824 S   0.0  0.2   0:00.07 graphic
&#10140;  /  top -b -n 1
top - 13:12:01 up 8 min,  1 user,  load average: 1.03, 0.89, 0.46
Tasks: 202 total,   3 running, 199 sleeping,   0 stopped,   0 zombie
%Cpu(s): 26.0 us,  5.1 sy,  0.0 ni, 68.6 id,  0.3 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   3839812 total,  3190676 used,   649136 free,    42028 buffers
KiB Swap:  3027964 total,        0 used,  3027964 free.  1812580 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 2344 justdrea  20   0  729172 151532  51184 S  49.3  3.9   0:49.93 skype
 2760 justdrea  20   0 2800116  70896  17188 S  37.0  1.8   1:24.25 dde-session-dae
 1686 justdrea   9 -11  435380   6596   4260 S  24.7  0.2   0:15.12 pulseaudio
 1531 justdrea  20   0   40324   2372    836 S  12.3  0.1   0:13.93 dbus-daemon
   10 root      20   0       0      0      0 S   6.2  0.0   0:00.62 rcuos/2
 1556 justdrea  20   0  504244  27848  12996 S   6.2  0.7   0:16.22 compiz
 1926 justdrea  20   0  301052   9044   4616 S   6.2  0.2   0:09.09 mousearea
 2077 justdrea  20   0 2370784  57676  22004 S   6.2  1.5   0:21.56 dde-dock
 2097 justdrea  20   0 1010600 131600  51140 S   6.2  3.4   0:32.94 maxthon
 2436 justdrea  20   0  588748  36700  24936 S   6.2  1.0   0:06.25 skype-call-reco
 2708 justdrea  20   0  647212 122820  18980 S   6.2  3.2   0:06.43 deepin-terminal
 2858 justdrea  20   0  694264  72776  32900 S   6.2  1.9   0:06.51 dde-control-cen
 2932 justdrea  20   0   24952   1472   1048 R   6.2  0.0   0:00.02 top
    1 root      20   0   33900   3220   1468 S   0.0  0.1   0:02.98 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/0
    4 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 R   0.0  0.0   0:01.39 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.64 rcuos/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.46 rcuos/1
   11 root      20   0       0      0      0 S   0.0  0.0   0:00.49 rcuos/3
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/4
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/5
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/6
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/7
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1
   19 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2
   20 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/4
   22 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/5
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/6
   24 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/7
   25 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/0
   26 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/0
   27 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1
   28 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 migration/1
   29 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/1
   30 root      20   0       0      0      0 S   0.0  0.0   0:00.58 kworker/1:0
   31 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H
   32 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/2
   33 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 migration/2
   34 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/2
   36 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0H
   37 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/3
   38 root      rt   0       0      0      0 S   0.0  0.0   0:00.12 migration/3
   39 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/3
   40 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0
   41 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0H
   42 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   43 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kdevtmpfs
   44 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   45 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   46 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   47 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   48 root       0 -20       0      0      0 S   0.0  0.0   0:00.02 kworker/u17:0
   49 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   50 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   51 root      20   0       0      0      0 S   0.0  0.0   0:00.01 khubd
   52 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
   53 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
   54 root      20   0       0      0      0 S   0.0  0.0   0:00.58 kworker/0:1
   55 root      20   0       0      0      0 S   0.0  0.0   0:00.56 kworker/3:1
   57 root      20   0       0      0      0 R   0.0  0.0   0:00.69 kworker/2:1
   59 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd
   60 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kswapd0
   61 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   62 root      39  19       0      0      0 S   0.0  0.0   0:00.01 khugepaged
   63 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_mark
   64 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-kthrea
   65 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   77 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
   98 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   99 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_manager
  154 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
  159 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  160 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  161 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_2
  169 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_3
  172 root      20   0       0      0      0 S   0.0  0.0   0:00.01 scsi_eh_4
  177 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_5
  180 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u16:2
  181 root      20   0       0      0      0 S   0.0  0.0   0:00.29 kworker/u16:3
  183 root      20   0       0      0      0 S   0.0  0.0   0:00.36 kworker/u16:4
  185 root      20   0       0      0      0 S   0.0  0.0   0:00.20 kworker/u16:6
  194 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/1:2
  213 root      20   0       0      0      0 S   0.0  0.0   0:00.12 jbd2/sda1-8
  214 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-conver
  324 root      20   0   20004   1180    612 S   0.0  0.0   0:00.50 upstart-udev-br
  329 root      20   0   51704   1860   1012 S   0.0  0.0   0:00.25 systemd-udevd
  338 root       0 -20       0      0      0 S   0.0  0.0   0:00.02 kworker/u17:1
  378 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmpathd
  379 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmpath_handlerd
  423 message+  20   0   40092   2308   1008 S   0.0  0.1   0:01.81 dbus-daemon
  437 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 cfg80211
  438 root     -51   0       0      0      0 S   0.0  0.0   0:00.00 irq/42-mei_me
  440 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kmemstick
  442 root     -51   0       0      0      0 S   0.0  0.0   0:01.88 irq/43-iwlwifi
  455 root      20   0    4444    784    604 S   0.0  0.0   0:00.00 bluetooth
  458 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ips-adjust
  459 root      20   0       0      0      0 S   0.0  0.0   0:00.10 ips-monitor
  467 root      20   0   19088   1724   1500 S   0.0  0.0   0:00.08 bluetoothd
  484 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 iwlwifi
  487 root      20   0   43532   1908   1508 S   0.0  0.0   0:00.05 systemd-logind
  507 syslog    20   0  255844   3200    816 S   0.0  0.1   0:00.25 rsyslogd
  531 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kvm-irqfd-clean
  536 avahi     20   0   32348   1616   1308 S   0.0  0.0   0:00.05 avahi-daemon
  543 root      20   0   74720   3700   2644 S   0.0  0.1   0:00.02 cupsd
  547 avahi     20   0   32224    472    216 S   0.0  0.0   0:00.00 avahi-daemon
  585 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio0
  641 root      20   0  330232   4408   3268 S   0.0  0.1   0:00.05 ModemManager
  690 root      20   0  352548   7168   5508 S   0.0  0.2   0:01.06 NetworkManager
  710 root      20   0  295992   5932   3740 S   0.0  0.2   0:00.24 polkitd
  716 root      20   0    4444    656    552 S   0.0  0.0   0:00.00 sh
  720 root      20   0   15868   1588    876 S   0.0  0.0   0:00.12 initctl
  722 root      20   0   15820    968    808 S   0.0  0.0   0:00.00 getty
  724 root      20   0   15820    968    808 S   0.0  0.0   0:00.00 getty
  730 root      20   0   15820    972    808 S   0.0  0.0   0:00.00 getty
  731 root      20   0  297408  10088   4024 S   0.0  0.3   0:00.14 dde-system-daem
  736 root      20   0   15820    960    808 S   0.0  0.0   0:00.00 getty
  739 root      20   0 2092100   3604   2588 S   0.0  0.1   0:00.06 console-kit-dae
  745 root      20   0   15820    968    808 S   0.0  0.0   0:00.00 getty
  880 root      20   0   23656   1036    792 S   0.0  0.0   0:00.00 cron
  882 daemon    20   0   19140    160      0 S   0.0  0.0   0:00.00 atd
  899 root      20   0    4368    708    532 S   0.0  0.0   0:00.01 acpid
  918 root      20   0   19188    720    492 S   0.0  0.0   0:00.07 irqbalance
  947 root      20   0  292652   4592   3660 S   0.0  0.1   0:00.06 lightdm
  969 root      20   0  462540 121440 110468 S   0.0  3.2   0:32.52 Xorg
  972 root      20   0  302232   4976   3920 S   0.0  0.1   0:00.20 accounts-daemon
  976 root      20   0   16464   1776    384 S   0.0  0.0   0:00.06 upstart-file-br
  980 root      20   0   15920   1300    388 S   0.0  0.0   0:00.05 upstart-socket-
 1004 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
 1028 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1029 root      20   0       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1030 root      20   0       0      0      0 S   0.0  0.0   0:00.00 i2400m-usb:1-1.
 1132 root      20   0   30608   2672   2096 S   0.0  0.1   0:00.14 wpa_supplicant
 1225 root      20   0    4444    116      0 S   0.0  0.0   0:00.00 _plutorun
 1226 root      20   0    4340    656    552 S   0.0  0.0   0:00.00 logger
 1227 root      20   0    4444    304    188 S   0.0  0.0   0:00.00 _plutorun
 1228 root      20   0    4444    644    540 S   0.0  0.0   0:00.00 _plutoload
 1229 root      20   0   94060   3832   2876 S   0.0  0.1   0:00.02 pluto
 1249 root      30  10   94068   1116    196 S   0.0  0.0   0:00.00 pluto
 1250 root      30  10   94068   1116    196 S   0.0  0.0   0:00.00 pluto
 1252 root      30  10   94068   1116    196 S   0.0  0.0   0:00.00 pluto
 1312 root      20   0    4440    328    216 S   0.0  0.0   0:00.00 xl2tpd
 1380 root      20   0   15820    964    808 S   0.0  0.0   0:00.00 getty
 1429 root      20   0    6356    384    296 S   0.0  0.0   0:00.00 _pluto_adns
 1464 root      20   0  174620   3820   3000 S   0.0  0.1   0:00.04 lightdm
 1481 justdrea  20   0 1486552  23632  10236 S   0.0  0.6   0:03.87 startdde
 1527 justdrea  20   0   10616    316      0 S   0.0  0.0   0:00.00 ssh-agent
 1530 justdrea  20   0   24440    580    332 S   0.0  0.0   0:00.00 dbus-launch
 1555 justdrea  20   0  348384  15896  10844 S   0.0  0.4   0:06.65 gtk-window-deco
 1569 justdrea  20   0  178296   2696   2172 S   0.0  0.1   0:00.16 dconf-service
 1590 justdrea  20   0  320088   6016   4352 S   0.0  0.2   0:00.09 gvfs-udisks2-vo
 1594 root      20   0  386168   6076   4220 S   0.0  0.2   0:00.37 udisksd
 1607 justdrea  20   0  192444   3004   2464 S   0.0  0.1   0:00.04 gvfsd
 1618 justdrea  20   0  208244   3368   2632 S   0.0  0.1   0:00.04 gvfs-gphoto2-vo
 1622 justdrea  20   0  291908   4208   3228 S   0.0  0.1   0:00.04 gvfs-afc-volume
 1627 justdrea  20   0  183324   4596   2128 S   0.0  0.1   0:00.03 gvfs-goa-volume
 1631 justdrea  20   0  196080   2800   2252 S   0.0  0.1   0:00.04 gvfs-mtp-volume
 1635 justdrea  20   0  367572   6392   3616 S   0.0  0.2   0:00.02 at-spi-bus-laun
 1639 justdrea  20   0   39116   1884   1488 S   0.0  0.0   0:00.03 dbus-daemon
 1642 justdrea  20   0  124912   3312   2756 S   0.0  0.1   0:00.07 at-spi2-registr
 1663 root      20   0  253792   5352   4008 S   0.0  0.1   0:00.13 upowerd
 1688 rtkit     21   1  168916   1304   1084 S   0.0  0.0   0:00.01 rtkit-daemon
 1707 root      20   0   10232   3724   1440 S   0.0  0.1   0:00.00 dhclient
 1710 root      20   0  143060  15340   3976 S   0.0  0.4   0:00.85 teamviewerd
 1727 nobody    20   0   31028   1524   1280 S   0.0  0.0   0:00.12 dnsmasq
 1776 justdrea  20   0 2062648  36792  19876 S   0.0  1.0   0:04.51 dde-desktop
 1794 justdrea  20   0  369988   4436   3600 S   0.0  0.1   0:00.06 gvfsd-trash
 1845 justdrea  20   0  414200  21096  15952 S   0.0  0.5   0:00.44 deepin-menu
 1854 justdrea  20   0  827628  68476  31468 S   0.0  1.8   0:07.35 dde-dock-applet
 1862 justdrea  20   0  238792  10320   6776 S   0.0  0.3   0:00.30 polkit-gnome-au
 1870 justdrea  20   0 2378372  92588  31548 S   0.0  2.4   0:08.35 dropbox
 1917 justdrea  20   0   53428   3112   2068 S   0.0  0.1   0:00.05 gconfd-2
 1930 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/2:2
 1964 justdrea  20   0    4444    644    544 S   0.0  0.0   0:00.00 sh
 1967 justdrea  20   0 1361172  51260  22652 S   0.0  1.3   0:04.52 variety
 2110 justdrea  20   0  309700   9192   3044 S   0.0  0.2   0:02.74 maxthon
 2111 justdrea  20   0    6500    392    312 S   0.0  0.0   0:00.00 maxthon_sandbox
 2112 justdrea  20   0  352492  24052  17384 S   0.0  0.6   0:00.19 maxthon
 2119 justdrea  20   0  140904   4624   3328 S   0.0  0.1   0:00.02 nacl_helper
 2120 justdrea  20   0  360688   7444    764 S   0.0  0.2   0:00.03 maxthon
 2165 justdrea  20   0 1060292 123852  17636 S   0.0  3.2   0:16.31 maxthon
 2195 justdrea  20   0 2511712  57416  33276 S   0.0  1.5   0:03.62 dde-launcher
 2218 justdrea  20   0  340664  24116  15144 S   0.0  0.6   0:00.89 maxthon
 2219 justdrea  20   0 1059140 108212  16908 S   0.0  2.8   0:06.30 maxthon
 2248 justdrea  20   0  995220  63036  24228 S   0.0  1.6   0:05.45 maxthon
 2264 justdrea  20   0 1096608 133832  31156 S   0.0  3.5   0:21.23 maxthon
 2277 justdrea  20   0  432300  40352  24348 S   0.0  1.1   0:02.29 maxthon
 2282 justdrea  20   0  388960   8096    256 S   0.0  0.2   0:00.00 maxthon
 2306 justdrea  20   0  988944  48808  19540 S   0.0  1.3   0:01.14 maxthon
 2318 justdrea  20   0  980984  55980  24520 S   0.0  1.5   0:04.93 maxthon
 2330 justdrea  20   0  979752  56960  24040 S   0.0  1.5   0:03.50 maxthon
 2720 justdrea  20   0   14824    820    664 S   0.0  0.0   0:00.00 gnome-pty-helpe
 2721 justdrea  20   0   40476   4244   2084 S   0.0  0.1   0:00.30 zsh
 2770 justdrea  20   0    4444    656    552 S   0.0  0.0   0:00.00 sh
 2771 justdrea  20   0   20232    940    772 S   0.0  0.0   0:00.07 syndaemon
 2792 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u17:2
 2808 justdrea  20   0  299148   9192   4824 S   0.0  0.2   0:00.07 graphic

```
If skype is the problem then I'm really in trouble because I use skype for my work.

---

### Post by sffvba[e0rt on 2015-01-13
> **jesus-freak said:**
> If skype is the problem then I'm really in trouble because I use skype for my work.

Not really, except if you are forced to use Deepin.

---

### Post by jesus-freak on 2015-01-13
Can anyone offer actual help here and not just useless comments?

---

### Post by ajgreeny on 2015-01-13
The link you gave to see the specs of the machine is not working so we're all in the dark about that.

Can you show the output of **lspci** to see what graphic card you have and also the wireless chip it's using which might give us a clue.
It is also worth running memtest+86 from the grub menu and leaving it running for a few hours, even overnight, to see if any memory problems are causing these freezes.

I don't know Deepin at all, other than what I have read at [www.distrowatch.com](www.distrowatch.com), so how did you install skype?

I have used skype from both the repos and also direct from skype and both run fine on my Xubuntu 14.04 64bit system, so it is not necessarily skype itself causing your difficulty, but perhaps some hardware incompatibility with your machine; so as I said earlier show us what the hardware really is.

---

### Post by jesus-freak on 2015-01-13
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak] (rev 5f)
15:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
15:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
15:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
15:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```
As for how I installed Skype, The first time I used the Deepin software center and installed it from there. Then after I re-installed Deepin on my system, then I downloaded Skype from the web site and installed it that way. There didn't seem to be any difference. All I know is that when I use skype and make a call, the CPU usage for skype and for pulse audio both go WAY up. I'm not sure if that has anything to do with it. I mean I've run Skype on Ubuntu 14.04 (which Deepin is based off of) and didn't have any of these problems

---

### Post by jesus-freak on 2015-01-13
I noticed that when I use skype that the CPU usage of skype and pulseaudio both go WAY up and it's normally when my system starts to act badly. When I open the system monitor and go to the processes, pulseaudio is set to "Very high" priority. If I turn that down to "low" or "very low" it seems to run skype better. I still have the same issue but it seems less frequent and when it happens it seems less severe.  However, when pulse audio is set to low I do have trouble running other audio programs such as spotify.

---

### Post by jesus-freak on 2015-01-14
Deepin just responded to my request for help. Here is what they said > So probably this means that it has been used the user-space approach to device driving the devices of your laptop / Desktop PC (at least one device drivers installed); this approach has a number of drawbacks. The most important is that if the driver has been swapped to disk, response time is unacceptably long. One big difference between kernel-space addresses and user-space addresses is that memory in user-space can be swapped out. Using the mlock system call might help, but, usually, you&#8217;ll need to lock several memory pages, because a user-space program depends on a lot of library code. mlock, too, is limited to privileged users. Worse yet, when the kernel accesses a userspace pointer, the associated page may not be present in memory, and a page fault is generated. What does anyone think about what Deepin said? Any thoughts or ideas? I've also noticed something else. On the system monitor when I get these freezes, all four CPUs jump up to 95% to 100%. Something is sucking my CPU. And if I leave my computer for a while, like 10 or 15 min and then I come back, when I try to use it I instantly get one of these freezes where the CPU jumps to 100% even if nothing is running. Is there any way to check and see what it is that is doing this? At least then I could figure out how to deal with it.

---

