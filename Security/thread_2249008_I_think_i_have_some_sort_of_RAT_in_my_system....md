---
title: "I think i have some sort of RAT in my system..."
date: 2014-10-18
forum: Security
---

### Post by CCgirl6690 on 2014-10-18
Hello I accidently downloaded some kinda java RAT and i feel like my Ubuntu 14.4 is infected and i feel like someone is watching my desktop or have access to to my laptop remotely. So my question is, how can i find out if there's something doing this, how to detect it? How to stop it?  I have team viewer too Thank you so much, I'm worried

---

### Post by sandyd on 2014-10-18
> **CCgirl6690 said:**
> Hello I accidently downloaded some kinda java RAT and i feel like my Ubuntu 14.4 is infected and i feel like someone is watching my desktop or have access to to my laptop remotely. So my question is, how can i find out if there's something doing this, how to detect it? How to stop it?  I have team viewer too Thank you so much, I'm worried

Hi, you can view current processes running on your system using the System Monitor, and see if you have suspicious looking processes running. In addition, you can see established connections to your computer via the command
```

lsof -i
```.

If you dont know if a process/connection is suspicious, post the output of
```

ps aux
lsof -i
```
Please make sure to obscure information such as your own IP address/etc

---

### Post by CCgirl6690 on 2014-10-18
Hello Thnaks of rthe reply,  Here is my output
```
none@Root:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   4600  2608 ?        Ss   16:44   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    16:44   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    16:44   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   16:44   0:00 [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    16:44   0:00 [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    16:44   0:00 [rcu_bh]
root         9  0.0  0.0      0     0 ?        S    16:44   0:00 [migration/0]
root        10  0.0  0.0      0     0 ?        S    16:44   0:00 [watchdog/0]
root        11  0.0  0.0      0     0 ?        S    16:44   0:00 [watchdog/1]
root        12  0.0  0.0      0     0 ?        S    16:44   0:00 [migration/1]
root        13  0.0  0.0      0     0 ?        S    16:44   0:00 [ksoftirqd/1]
root        14  0.0  0.0      0     0 ?        S    16:44   0:00 [kworker/1:0]
root        15  0.0  0.0      0     0 ?        S<   16:44   0:00 [kworker/1:0H]
root        16  0.0  0.0      0     0 ?        S<   16:44   0:00 [khelper]
root        17  0.0  0.0      0     0 ?        S    16:44   0:00 [kdevtmpfs]
root        18  0.0  0.0      0     0 ?        S<   16:44   0:00 [netns]
root        19  0.0  0.0      0     0 ?        S<   16:44   0:00 [writeback]
root        20  0.0  0.0      0     0 ?        S<   16:44   0:00 [kintegrityd]
root        21  0.0  0.0      0     0 ?        S<   16:44   0:00 [bioset]
root        22  0.0  0.0      0     0 ?        S<   16:44   0:00 [kworker/u5:0]
root        23  0.0  0.0      0     0 ?        S<   16:44   0:00 [kblockd]
root        24  0.0  0.0      0     0 ?        S<   16:44   0:00 [ata_sff]
root        25  0.0  0.0      0     0 ?        S    16:44   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   16:44   0:00 [md]
root        27  0.0  0.0      0     0 ?        S<   16:44   0:00 [devfreq_wq]
root        28  0.0  0.0      0     0 ?        S    16:44   0:00 [kworker/0:1]
root        30  0.0  0.0      0     0 ?        S    16:44   0:00 [khungtaskd]
root        31  0.0  0.0      0     0 ?        S    16:44   0:00 [kswapd0]
root        32  0.0  0.0      0     0 ?        SN   16:44   0:00 [ksmd]
root        33  0.0  0.0      0     0 ?        SN   16:44   0:00 [khugepaged]
root        34  0.0  0.0      0     0 ?        S    16:44   0:00 [fsnotify_mark]
root        35  0.0  0.0      0     0 ?        S    16:44   0:00 [ecryptfs-kthre
root        36  0.0  0.0      0     0 ?        S<   16:44   0:00 [crypto]
root        48  0.0  0.0      0     0 ?        S<   16:44   0:00 [kthrotld]
root        49  0.1  0.0      0     0 ?        R    16:44   0:03 [kworker/0:2]
root        70  0.0  0.0      0     0 ?        S<   16:44   0:00 [deferwq]
root        71  0.0  0.0      0     0 ?        S<   16:44   0:00 [charger_manage
root        72  0.0  0.0      0     0 ?        S    16:44   0:02 [kworker/1:2]
root       133  0.0  0.0      0     0 ?        S<   16:44   0:00 [kpsmoused]
root       134  0.0  0.0      0     0 ?        S<   16:44   0:00 [firewire]
root       135  0.0  0.0      0     0 ?        S<   16:44   0:00 [firewire_ohci]
root       136  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_0]
root       137  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_1]
root       138  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_2]
root       139  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_3]
root       140  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_4]
root       141  0.0  0.0      0     0 ?        S    16:44   0:00 [scsi_eh_5]
root       170  0.0  0.0      0     0 ?        S<   16:44   0:00 [kworker/u5:1]
root       171  0.0  0.0      0     0 ?        S    16:44   0:00 [jbd2/sda2-8]
root       172  0.0  0.0      0     0 ?        S<   16:44   0:00 [ext4-rsv-conve
root       331  0.0  0.0   3144   960 ?        S    16:44   0:00 upstart-udev-br
root       337  0.0  0.0  12464  1812 ?        Ss   16:44   0:00 /lib/systemd/sy
root       425  0.0  0.0      0     0 ?        S<   16:44   0:00 [cfg80211]
root       435  0.0  0.0      0     0 ?        S    16:44   0:00 [wl_event_handl
root       455  0.0  0.0      0     0 ?        S    16:44   0:00 [pccardd]
syslog     527  0.0  0.0  31376  1080 ?        Ssl  16:44   0:00 rsyslogd
root       530  0.0  0.0   2888   608 ?        S    16:44   0:00 upstart-file-br
message+   532  0.0  0.1   5164  2184 ?        Ss   16:44   0:00 dbus-daemon --s
avahi      558  0.0  0.0   3480  1496 ?        S    16:44   0:00 avahi-daemon: r
avahi      559  0.0  0.0   3480   436 ?        S    16:44   0:00 avahi-daemon: c
root       564  0.0  0.0      0     0 ?        S<   16:44   0:00 [hd-audio0]
root       601  0.0  0.0   4884  1640 ?        Ss   16:44   0:00 /usr/sbin/bluet
root       628  0.0  0.0   4220  1808 ?        Ss   16:44   0:00 /lib/systemd/sy
root       640  0.0  0.3  27696  6512 ?        Ss   16:44   0:00 smbd -F
root       667  0.0  0.0      0     0 ?        S<   16:44   0:00 [krfcommd]
root       725  0.0  0.1  38392  3840 ?        Ssl  16:44   0:00 /usr/sbin/Modem
root       764  0.0  0.0   3140   864 ?        S    16:44   0:00 upstart-socket-
root       964  0.1  0.5  53584 10564 ?        Ssl  16:44   0:03 NetworkManager
root       973  0.0  0.2  36040  4524 ?        Sl   16:44   0:00 /usr/lib/policy
root       982  0.0  0.1  27696  3476 ?        S    16:44   0:00 smbd -F
root       991  0.0  0.1   6920  2460 ?        Ss   16:44   0:00 /sbin/wpa_suppl
root      1199  0.0  0.0   4652   868 tty4     Ss+  16:44   0:00 /sbin/getty -8 
root      1203  0.0  0.0   4652   872 tty5     Ss+  16:44   0:00 /sbin/getty -8 
root      1210  0.0  0.0   4652   876 tty2     Ss+  16:44   0:00 /sbin/getty -8 
root      1211  0.0  0.0   4652   872 tty3     Ss+  16:44   0:00 /sbin/getty -8 
root      1214  0.0  0.0   4652   868 tty6     Ss+  16:44   0:00 /sbin/getty -8 
root      1287  0.0  0.0   2200   656 ?        Ss   16:44   0:00 acpid -c /etc/a
root      1296  0.0  0.1  22588  3160 ?        Sl   16:44   0:00 /usr/sbin/conso
root      1300  0.0  0.0   3060   896 ?        Ss   16:44   0:00 cron
daemon    1301  0.0  0.0   2648   124 ?        Ss   16:44   0:00 atd
root      1383  0.0  0.1   8884  2916 ?        Ss   16:44   0:00 /usr/sbin/cups-
whoopsie  1411  0.0  0.2  53944  4760 ?        Ssl  16:44   0:00 whoopsie
nobody    1415  0.0  0.0   5556  1444 ?        S    16:44   0:00 /usr/sbin/dnsma
postgres  1458  0.0  0.3  51148  7932 ?        S    16:44   0:00 /usr/lib/postgr
root      1579  0.0  0.2  21424  4636 ?        Ss   16:44   0:00 /usr/sbin/winbi
root      1600  0.0  0.1  17380  2460 ?        Ss   16:44   0:00 nmbd -D
root      1602  0.0  0.1  21424  3164 ?        S    16:44   0:00 /usr/sbin/winbi
postgres  1610  0.0  0.0  51148  1580 ?        Ss   16:44   0:00 postgres: write
postgres  1611  0.0  0.0  51148  1344 ?        Ss   16:44   0:00 postgres: wal w
postgres  1612  0.0  0.1  51572  2392 ?        Ss   16:44   0:00 postgres: autov
postgres  1613  0.0  0.0  21380  1432 ?        Ss   16:44   0:00 postgres: stats
root      1627  0.0  0.2  43388  5572 ?        SLsl 16:44   0:00 lightdm
root      1640  2.8  2.2 183088 44992 tty7     Ssl+ 16:44   1:16 /usr/bin/X -cor
root      1643  0.0  0.1  36416  3828 ?        Sl   16:44   0:00 /usr/lib/accoun
postgres  1690  0.0  0.6 163380 13024 ?        S    16:44   0:00 /usr/lib/postgr
root      1709  0.0  0.0      0     0 ?        S    16:44   0:00 [kauditd]
postgres  1723  0.0  0.0 163380  1500 ?        Ss   16:44   0:00 postgres: check
postgres  1724  0.0  0.1 163380  2292 ?        Ss   16:44   0:00 postgres: write
postgres  1725  0.0  0.0 163380  1284 ?        Ss   16:44   0:00 postgres: wal w
postgres  1726  0.0  0.1 163808  2368 ?        Ss   16:44   0:00 postgres: autov
postgres  1727  0.0  0.0  21504  1392 ?        Ss   16:44   0:00 postgres: stats
dictd     1787  0.0  0.0   2780   908 ?        Ss   16:45   0:00 dictd 1.12.1: 0
kernoops  1809  0.0  0.0   6392   948 ?        Ss   16:45   0:00 /usr/sbin/kerne
root      1858  0.0  0.1  18112  3700 ?        Sl   16:45   0:00 lightdm --sessi
root      1922  0.0  0.2  37836  4080 ?        Sl   16:45   0:00 /usr/lib/upower
rtkit     1955  0.0  0.0  21368  1240 ?        SNl  16:45   0:00 /usr/lib/rtkit/
root      2227  0.0  0.0   4792  1492 ?        Ss   16:45   0:00 /usr/lib/postfi
debian-+  2261  0.1  1.2  29144 25132 ?        S    16:45   0:03 /usr/bin/tor --
root      2272  0.0  0.0      0     0 ?        S<   16:45   0:00 [iprt]
root      2382  0.0  0.0   4652   860 tty1     Ss+  16:45   0:00 /sbin/getty -8 
root      2449  0.0  0.2   9380  4488 ?        Ss   16:45   0:00 /usr/sbin/cupsd
colord    2453  0.0  0.4  37372  9304 ?        Sl   16:45   0:00 /usr/lib/colord
none      2487  0.0  0.2  55532  4200 ?        SLl  16:46   0:00 /usr/bin/gnome-
none      2489  0.0  0.1   6148  2208 ?        Ss   16:46   0:00 init --user
none      2550  0.0  0.0   4216   196 ?        Ss   16:46   0:00 ssh-agent -s
none      2557  0.0  0.0   5000  2012 ?        Ss   16:46   0:01 dbus-daemon --f
none      2566  0.0  0.0   4920  1064 ?        Ss   16:46   0:00 upstart-event-b
none      2569  0.0  0.1  39464  3708 ?        Ss   16:46   0:00 /usr/lib/i386-l
none      2576  0.0  0.0   5204   668 ?        S    16:46   0:00 upstart-file-br
none      2578  0.0  0.0   4924   600 ?        S    16:46   0:00 upstart-dbus-br
none      2580  0.0  0.0   4924   360 ?        S    16:46   0:00 upstart-dbus-br
none      2586  0.0  0.8 148012 17976 ?        Ssl  16:46   0:00 /usr/lib/unity-
none      2591  0.0  1.0  97924 20520 ?        Ssl  16:46   0:01 /usr/lib/i386-l
none      2593  0.0  0.1  43668  3304 ?        Ssl  16:46   0:00 /usr/lib/at-spi
none      2594  0.0  0.4  87076  9548 ?        Ssl  16:46   0:00 gnome-session -
none      2599  0.0  0.0   4372  1812 ?        S    16:46   0:00 /bin/dbus-daemo
none      2601  0.1  0.9 202396 18988 ?        Ssl  16:46   0:03 /usr/lib/unity/
none      2603  0.0  0.1  17368  3096 ?        Sl   16:46   0:00 /usr/lib/at-spi
none      2611  0.0  0.1  27760  2776 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2615  0.0  0.3  43360  6992 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2623  0.0  0.6 196628 12900 ?        Sl   16:46   0:00 /usr/lib/i386-l
none      2664  0.0  0.2 100384  5816 ?        S<l  16:46   0:00 /usr/bin/pulsea
none      2665  0.0  0.0   3748   808 ?        S    16:46   0:01 syndaemon -i 1.
none      2670  0.0  0.1  14552  2532 ?        S    16:46   0:00 /usr/lib/pulsea
none      2672  0.0  0.1   9736  3144 ?        S    16:46   0:00 /usr/lib/i386-l
none      2674  0.0  0.5 216928 10648 ?        Sl   16:46   0:00 /usr/lib/i386-l
none      2678  0.0  0.2  44648  5328 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2683  0.0  0.1  36304  2736 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2685  0.0  0.1  36924  3004 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2695  0.0  0.6 101104 13976 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2696  0.0  0.3 125196  7152 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2699  0.0  0.4  56396  9728 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2703  0.0  0.3  62236  7668 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2716  0.0  0.3  38384  6336 ?        Ssl  16:46   0:00 /usr/lib/i386-l
none      2728  0.0  0.7 185564 15572 ?        Sl   16:46   0:01 /usr/lib/i386-l
none      2737  0.0  0.5  73200 11616 ?        Sl   16:46   0:00 /usr/lib/evolut
none      2767  1.5  2.9 346780 59688 ?        Sl   16:46   0:38 compiz
none      2781  0.0  0.2  24788  4828 ?        Sl   16:46   0:00 /usr/lib/dconf/
none      2796  0.0  0.1  37688  3676 ?        Sl   16:46   0:00 /usr/bin/ibus-d
none      2829  0.0  0.4  42956  8212 ?        Sl   16:46   0:00 /usr/lib/policy
none      2831  0.0  0.5  52140 10152 ?        Sl   16:46   0:00 /usr/lib/unity-
none      2832  0.4  4.0 356768 81852 ?        Sl   16:46   0:11 nautilus -n
none      2838  0.0  0.9 340868 19216 ?        SLl  16:46   0:01 nm-applet
none      2855  0.0  0.1  19080  3416 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2859  0.0  0.9 135708 18240 ?        Sl   16:46   0:00 /usr/lib/gnome-
none      2863  0.0  1.7 111580 34444 ?        Sl   16:46   0:00 /usr/lib/evolut
none      2866  0.0  0.2  38704  4208 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
root      2872  0.0  0.2  52544  4496 ?        Sl   16:46   0:00 /usr/lib/udisks
none      2881  0.0  0.1  27196  2548 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2885  0.0  0.1  28436  2980 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2892  0.0  0.1  39372  2680 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2920  0.0  0.1  46084  3420 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2929  0.0  0.4  44292  9444 ?        Sl   16:46   0:00 /usr/lib/telepa
none      2944  0.0  0.3  36980  6888 ?        Sl   16:46   0:00 /usr/lib/gvfs/g
none      2961  0.0  0.5  83340 10260 ?        Sl   16:47   0:00 telepathy-indic
none      2968  0.0  0.5  77584 11032 ?        Sl   16:47   0:00 zeitgeist-datah
none      2973  0.0  0.2  44620  4384 ?        Sl   16:47   0:00 /usr/bin/zeitge
none      2981  0.0  0.4  58368  8468 ?        Sl   16:47   0:00 /usr/lib/i386-l
none      2992  0.0  0.0   4252   540 ?        S    16:47   0:00 /bin/cat
none      3021  0.0  0.6  61704 13664 ?        Sl   16:47   0:00 update-notifier
none      3042  0.0  0.3  47444  7644 ?        Sl   16:48   0:00 /usr/lib/i386-l
root      3129  0.0  0.1   5520  3116 ?        S    16:54   0:00 /sbin/dhclient 
postfix   3201  0.0  0.0   4812  1324 ?        S    16:54   0:00 pickup -l -t fi
postfix   3202  0.0  0.0   4856  1344 ?        S    16:54   0:00 qmgr -l -t fifo
root      3261  0.0  0.1  20040  2780 ?        Sl   16:54   0:00 /usr/lib/Networ
root      3269  0.1  0.1   5864  3024 ?        S    16:54   0:02 /usr/sbin/openv
none      3346 15.3 23.7 1250788 479192 ?      Sl   16:54   5:14 /usr/lib/firefo
none      3371  0.0  0.2  34792  4548 ?        Sl   16:54   0:00 /usr/lib/libuni
none      3458  0.4  2.3 255372 48220 ?        Sl   16:56   0:09 pidgin
none      3538  0.0  0.0      0     0 ?        Z    16:56   0:00 [pidgin] <defun
none      3543  0.0  0.0      0     0 ?        Z    16:56   0:00 [pidgin] <defun
root      3711  0.0  0.0      0     0 ?        S    17:01   0:00 [kworker/u4:0]
none      3731  0.0  0.3  41804  6088 ?        Sl   17:03   0:00 /usr/lib/gvfs/g
none      3800  0.1  0.7 132880 14588 ?        Sl   17:12   0:01 /usr/lib/firefo
none      3805  0.0  0.6  97380 12316 ?        Sl   17:12   0:00 /opt/google/tal
root      3867  0.0  0.0      0     0 ?        S    17:18   0:00 [kworker/u4:2]
root      4046  0.0  0.0      0     0 ?        S    17:24   0:00 [kworker/u4:1]
none      4141  5.6  0.8 207344 17212 ?        Rl   17:29   0:00 gnome-terminal
none      4183  0.0  0.0   2424   724 ?        S    17:29   0:00 gnome-pty-helpe
none      4184  0.8  0.2   7692  4040 pts/0    Ss   17:29   0:00 bash
none      4232  0.0  0.0   5228  1160 pts/0    R+   17:29   0:00 ps aux
none@Root:~$ lsof -i

```

---

### Post by Elfy on 2014-10-19
We're so sorry that the moderation team isn't able to patrol the forum 24/7.

Try and remember that _everyone_ here is a volunteer.

---

### Post by CCgirl6690 on 2014-10-19
> **Elfy said:**
> We're so sorry that the moderation team isn't able to patrol the forum 24/7.

Try and remember that _everyone_ here is a volunteer.

Hello Elfy.
It's a pleasure that you posted in my thread. 
Sorry for that. i was just waiting 12 hours for Sandy to reply back. i shouldn't  have posted that.
I'm Sorry again...

---

### Post by ian-weisser on 2014-10-19
Still awaiting the lsof -i.

---

### Post by CCgirl6690 on 2014-10-19
> **ian-weisser said:**
> Still awaiting the lsof -i.

Sandy asked me not to post that here. And my problem seems to be solved for now. Thanks for everyone who responded

---

### Post by Penguin360 on 2014-10-20
> **CCgirl6690 said:**
> Sandy asked me not to post that here. And my problem seems to be solved for now. Thanks for everyone who responded

Would you mind sharing how you solved the problem so other people might be able to benefit from your experience?

Thanks,

---

