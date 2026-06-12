---
title: "what processes are normal on 13.04"
date: 2013-08-12
forum: Security
---

### Post by MikeCyber on 2013-08-12
Hi
are that many processes normal on a default 13.04? I ask because since recently, often during surfing, a Union Bank page pops up randomly. Also in my home dir is now a file: libpeerconnection.log that I've never seen prior to 13.04.
Thanks


```
michael@michael-Ubuntu:~$ ps axu
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  1.5  0.0  27072  2864 ?        Ss   07:27   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    07:27   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/0:0]
root         5  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/0:0H]
root         6  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:0]
root         7  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/u:0H]
root         8  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/0]
root         9  0.0  0.0      0     0 ?        S    07:27   0:00 [rcu_bh]
root        10  0.0  0.0      0     0 ?        S    07:27   0:00 [rcu_sched]
root        11  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/0]
root        12  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/1]
root        14  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/1]
root        15  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/1:0]
root        16  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/1:0H]
root        17  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/2]
root        18  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/2]
root        19  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/2]
root        20  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/2:0]
root        21  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/2:0H]
root        22  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/3]
root        23  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/3]
root        24  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/3]
root        25  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/3:0]
root        26  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/3:0H]
root        27  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/4]
root        28  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/4]
root        29  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/4]
root        30  0.0  0.0      0     0 ?        R    07:27   0:00 [kworker/4:0]
root        31  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/4:0H]
root        32  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/5]
root        33  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/5]
root        34  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/5]
root        35  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/5:0]
root        36  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/5:0H]
root        37  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/6]
root        38  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/6]
root        39  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/6]
root        40  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/6:0]
root        41  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/6:0H]
root        42  0.0  0.0      0     0 ?        S    07:27   0:00 [watchdog/7]
root        43  0.0  0.0      0     0 ?        S    07:27   0:00 [ksoftirqd/7]
root        44  0.0  0.0      0     0 ?        S    07:27   0:00 [migration/7]
root        45  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/7:0]
root        46  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/7:0H]
root        47  0.0  0.0      0     0 ?        S<   07:27   0:00 [cpuset]
root        48  0.0  0.0      0     0 ?        S<   07:27   0:00 [khelper]
root        49  0.0  0.0      0     0 ?        S    07:27   0:00 [kdevtmpfs]
root        50  0.0  0.0      0     0 ?        S<   07:27   0:00 [netns]
root        51  0.0  0.0      0     0 ?        S    07:27   0:00 [bdi-default]
root        52  0.0  0.0      0     0 ?        S<   07:27   0:00 [kintegrityd]
root        53  0.0  0.0      0     0 ?        S<   07:27   0:00 [kblockd]
root        54  0.0  0.0      0     0 ?        S<   07:27   0:00 [ata_sff]
root        55  0.0  0.0      0     0 ?        S    07:27   0:00 [khubd]
root        56  0.0  0.0      0     0 ?        S<   07:27   0:00 [md]
root        57  0.0  0.0      0     0 ?        S<   07:27   0:00 [devfreq_wq]
root        58  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/3:1]
root        60  0.0  0.0      0     0 ?        S    07:27   0:00 [khungtaskd]
root        61  0.0  0.0      0     0 ?        S    07:27   0:00 [kswapd0]
root        62  0.0  0.0      0     0 ?        SN   07:27   0:00 [ksmd]
root        63  0.0  0.0      0     0 ?        SN   07:27   0:00 [khugepaged]
root        64  0.0  0.0      0     0 ?        S    07:27   0:00 [fsnotify_mark]
root        65  0.0  0.0      0     0 ?        S    07:27   0:00 [ecryptfs-kthrea]
root        66  0.0  0.0      0     0 ?        S<   07:27   0:00 [crypto]
root        77  0.0  0.0      0     0 ?        S<   07:27   0:00 [kthrotld]
root        78  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:1]
root        80  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/1:1]
root        81  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/0:1]
root        82  0.0  0.0      0     0 ?        S<   07:27   0:00 [binder]
root       101  0.0  0.0      0     0 ?        S<   07:27   0:00 [deferwq]
root       102  0.0  0.0      0     0 ?        S<   07:27   0:00 [charger_manager]
root       103  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/3:2]
root       104  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/4:1]
root       261  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_0]
root       262  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_1]
root       265  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_2]
root       272  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_3]
root       273  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_4]
root       274  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_5]
root       277  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:2]
root       278  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:3]
root       279  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:4]
root       280  0.2  0.0      0     0 ?        S    07:27   0:00 [kworker/u:5]
root       281  0.1  0.0      0     0 ?        S    07:27   0:00 [kworker/u:6]
root       282  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:7]
root       283  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_6]
root       284  0.0  0.0      0     0 ?        S    07:27   0:00 [scsi_eh_7]
root       285  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:8]
root       286  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/u:9]
root       287  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/6:1]
root       288  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/2:1]
root       289  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/5:1]
root       318  0.0  0.0      0     0 ?        S    07:27   0:00 [jbd2/sda5-8]
root       319  0.0  0.0      0     0 ?        S<   07:27   0:00 [ext4-dio-unwrit]
root       338  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/7:1]
root       364  0.0  0.0  15268   392 ?        S    07:27   0:00 upstart-file-bridge --daemon
root       422  0.1  0.0  17448   904 ?        S    07:27   0:00 upstart-udev-bridge --daemon
root       424  0.1  0.0  22264  2052 ?        Ss   07:27   0:00 /sbin/udevd --daemon
root       480  0.0  0.0      0     0 ?        S    07:27   0:00 [irq/45-mei]
root       509  0.0  0.0      0     0 ?        S<   07:27   0:00 [kpsmoused]
root       581  0.0  0.0      0     0 ?        S<   07:27   0:00 [cfg80211]
root       617  0.0  0.0  21940  1368 ?        S    07:27   0:00 /sbin/udevd --daemon
root       623  0.0  0.0  22260  1612 ?        S    07:27   0:00 /sbin/udevd --daemon
root       633  0.0  0.0      0     0 ?        S<   07:27   0:00 [hd-audio0]
root       636  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/7:2]
root       699  0.0  0.0      0     0 ?        S<   07:27   0:00 [hd-audio1]
root       744  0.0  0.0      0     0 ?        S<   07:27   0:00 [led_workqueue]
root       755  0.0  0.0  15388   632 ?        S    07:27   0:00 upstart-socket-bridge --daemon
root       757  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/1:1H]
root       759  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/5:1H]
root       760  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/0:1H]
root       761  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/4:1H]
root       788  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/0:2]
root       791  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/0:3]
root       793  0.0  0.0      0     0 ?        S    07:27   0:00 [kworker/0:4]
root       837  0.0  0.0      0     0 ?        S<   07:27   0:00 [kvm-irqfd-clean]
root       843  0.0  0.0      0     0 ?        S<   07:27   0:00 [hci0]
root       851  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/u:1H]
root       935  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/6:1H]
root       936  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/7:1H]
root       949  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/2:1H]
root      1024  0.0  0.0  52252  2852 ?        Ss   07:27   0:00 /usr/sbin/sshd -D
102       1030  0.2  0.0  24876  2192 ?        Ss   07:27   0:00 dbus-daemon --system --fork
root      1051  0.0  0.0  83408  3276 ?        Ss   07:27   0:00 /usr/sbin/modem-manager
root      1053  0.0  0.0  19240  1964 ?        Ss   07:27   0:00 /usr/sbin/bluetoothd
syslog    1060  0.0  0.0 247460  1644 ?        Sl   07:27   0:00 rsyslogd -c5
root      1061  0.0  0.0      0     0 ?        S<   07:27   0:00 [krfcommd]
root      1117  0.2  0.0 264660  6696 ?        Ssl  07:27   0:00 NetworkManager
avahi     1125  0.0  0.0  32340  1740 ?        S    07:27   0:00 avahi-daemon: running [michael-Ubuntu.local]
avahi     1127  0.0  0.0  32220   468 ?        S    07:27   0:00 avahi-daemon: chroot helper
root      1134  0.1  0.0 209020  5660 ?        Sl   07:27   0:00 /usr/lib/policykit-1/polkitd --no-debug
root      1167  0.0  0.0  76508  8008 ?        Ss   07:27   0:00 /usr/sbin/cupsd -F
root      1179  0.0  0.0  20276  1000 tty4     Ss+  07:27   0:00 /sbin/getty -8 38400 tty4
root      1186  0.0  0.0  20276   992 tty5     Ss+  07:27   0:00 /sbin/getty -8 38400 tty5
root      1205  0.0  0.0  20276   996 tty2     Ss+  07:27   0:00 /sbin/getty -8 38400 tty2
root      1207  0.0  0.0  20276  1000 tty3     Ss+  07:27   0:00 /sbin/getty -8 38400 tty3
root      1210  0.0  0.0  20276  1000 tty6     Ss+  07:27   0:00 /sbin/getty -8 38400 tty6
root      1211  0.0  0.0  21492   684 ?        Ss   07:27   0:00 /usr/sbin/miredo
miredo    1212  0.0  0.0 128164  1024 ?        Sl   07:27   0:00 /usr/sbin/miredo
colord    1225  0.1  0.0 223868  6084 ?        Sl   07:27   0:00 /usr/lib/colord/colord
root      1229  0.0  0.0  70428  2812 ?        Ss   07:27   0:00 /usr/sbin/cups-browsed
root      1248  0.0  0.0   4360   612 ?        Ss   07:27   0:00 anacron -s
root      1249  0.0  0.0   4508   816 ?        Ss   07:27   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1251  0.0  0.0  21324  1028 ?        Ss   07:27   0:00 cron
daemon    1253  0.0  0.0  19124   164 ?        Ss   07:27   0:00 atd
root      1257  0.0  0.0 275480  3304 ?        Ssl  07:27   0:00 lightdm
root      1277  0.0  0.0  19148   768 ?        Ss   07:27   0:00 /usr/sbin/irqbalance
whoopsie  1308  0.0  0.0 291060  5224 ?        Ssl  07:27   0:00 whoopsie
root      1368  4.4  0.3 186836 54032 tty7     Ss+  07:27   0:01 /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -bac
root      1468  0.0  0.0   8568   416 ?        S    07:27   0:00 /usr/lib/miredo/miredo-privproc 4
root      1499  0.1  0.0  32036  2460 ?        Ss   07:27   0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/w
root      1501  0.0  0.0   4440   628 ?        S    07:27   0:00 /bin/sh /etc/init.d/ondemand background
root      1505  0.0  0.0   4352   368 ?        S    07:27   0:00 sleep 60
root      1507  0.0  0.0  20276  1000 tty1     Ss+  07:27   0:00 /sbin/getty -8 38400 tty1
root      1519  0.0  0.0 169964  3640 ?        Sl   07:27   0:00 lightdm --session-child 12 15
root      1520  0.0  0.0      0     0 ?        S    07:27   0:00 [kauditd]
root      1523  0.0  0.0 277188  4300 ?        Sl   07:27   0:00 /usr/lib/accountsservice/accounts-daemon
root      1547  0.0  0.0      0     0 ?        S<   07:27   0:00 [kworker/3:1H]
root      1549  0.0  0.0 4188908 3928 ?        Sl   07:27   0:00 /usr/sbin/console-kit-daemon --no-daemon
michael   1624  0.1  0.0 429900 10868 ?        Ssl  07:27   0:00 gnome-session --session=ubuntu
michael   1669  0.0  0.0  12612   320 ?        Ss   07:27   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-
michael   1672  0.0  0.0  24596   864 ?        S    07:27   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-session --session=u
michael   1673  0.4  0.0  26184  2504 ?        Ss   07:27   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
michael   1683  0.0  0.0 356604  4312 ?        Sl   07:27   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
michael   1687  0.0  0.0  23984  1716 ?        S    07:27   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-addre
michael   1690  0.0  0.0 124720  3364 ?        Sl   07:27   0:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
michael   1701  0.2  0.1 686056 17960 ?        Sl   07:27   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
michael   1705  0.0  0.0 461508  4480 ?        Sl   07:27   0:00 /usr/bin/gnome-keyring-daemon --start --components=secrets
michael   1712  0.0  0.0 439504  6308 ?        S<l  07:27   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1714  0.0  0.0 168916  1368 ?        SNl  07:27   0:00 /usr/lib/rtkit/rtkit-daemon
root      1721  0.0  0.0 222296  4448 ?        Sl   07:27   0:00 /usr/lib/upower/upowerd
michael   1764  0.0  0.0 196712  3216 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfsd
michael   1776  0.0  0.0 349344  3800 ?        Sl   07:27   0:00 /usr/lib/gvfs//gvfsd-fuse -f /run/user/michael/gvfs
michael   1891  2.9  0.6 1298268 108428 ?      Sl   07:27   0:01 compiz
michael   1896  0.0  0.0 178128  2720 ?        Sl   07:27   0:00 /usr/lib/dconf/dconf-service
michael   1899  0.0  0.0 490352  9828 ?        Sl   07:27   0:00 /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
michael   1901  1.2  0.2 1426312 34940 ?       Sl   07:27   0:00 nautilus -n
michael   1902  0.0  0.0 344948  9660 ?        Sl   07:27   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
michael   1903  0.5  0.1 694188 18668 ?        Sl   07:27   0:00 nm-applet
michael   1913  0.0  0.0 224908  6352 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
root      1918  0.2  0.0 373448  6448 ?        Sl   07:27   0:00 /usr/lib/udisks2/udisksd --no-debug
michael   1934  0.0  0.0  58184  3592 ?        S    07:27   0:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
michael   1937  0.0  0.0 203804  3332 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
michael   1941  0.0  0.0 191640  2760 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
michael   1945  0.0  0.0 285780  3312 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
michael   1951  0.0  0.0 363364  4320 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.11 /org/gtk/gvfs/exec_spaw/0
michael   1958  0.2  0.0 508224 11260 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
michael   1963  0.0  0.0   4440   628 ?        Ss   07:27   0:00 /bin/sh -c /usr/bin/gtk-window-decorator
michael   1964  0.1  0.0 350068 13004 ?        Sl   07:27   0:00 /usr/bin/gtk-window-decorator
michael   1967  0.8  0.1 538648 18540 ?        Sl   07:27   0:00 /usr/lib/unity/unity-panel-service
michael   1970  0.4  0.0 366400  5720 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/hud/hud-service
michael   1983  0.0  0.0 459304  5556 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/indicator-sync/indicator-sync-service
michael   1985  0.1  0.0 637936 11016 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/indicator-datetime-service
michael   1987  0.0  0.0 542312  7340 ?        Sl   07:27   0:00 /usr/lib/indicator-messages/indicator-messages-service
michael   1989  0.0  0.0 526780 11008 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/indicator-printers-service
michael   1991  0.0  0.0 555176  7108 ?        Sl   07:27   0:00 /usr/lib/indicator-session/indicator-session-service
michael   1994  0.1  0.0 458440  6020 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/indicator-application-service
michael   1995  0.0  0.0 651952  9032 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/indicator-sound-service
michael   2006  0.0  0.0 489168  6712 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
michael   2039  0.0  0.0 384052  8352 ?        Sl   07:27   0:00 /usr/lib/evolution/evolution-source-registry
michael   2056  0.0  0.0 132944  3856 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfsd-metadata
michael   2067  0.3  0.1 445516 16988 ?        Sl   07:27   0:00 /usr/lib/x86_64-linux-gnu/notify-osd
michael   2071  0.0  0.0 351824 10652 ?        Sl   07:27   0:00 /usr/bin/gnome-screensaver --no-daemon
michael   2075  0.0  0.0 270448  3124 ?        Sl   07:27   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.11 /org/gtk/gvfs/exec_spaw/1
root      2079  0.0  0.0      0     0 ?        S    07:27   0:00 [flush-8:0]
root      2081  0.0  0.0  10240  3764 ?        S    07:27   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs
nobody    2085  0.0  0.0  33348  1536 ?        S    07:27   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid
michael   2128  0.0  0.0 438496 11376 ?        Sl   07:27   0:00 telepathy-indicator
michael   2135  0.0  0.0 260744  8068 ?        Sl   07:27   0:00 /usr/lib/telepathy/mission-control-5
michael   2143  1.6  0.1 417716 17120 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-applications/unity-applications-daemon
michael   2145  0.1  0.0 469660  6412 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-files/unity-files-daemon
michael   2151  0.0  0.0 629460  6520 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-friends
michael   2153  0.1  0.0 745152  8292 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-music/unity-music-daemon
michael   2155  0.8  0.1 634556 24832 ?        Sl   07:28   0:00 /usr/bin/python3 /usr/lib/unity-lens-photos/unity-lens-photos
michael   2158  0.3  0.0 862444 10344 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-shopping/unity-shopping-daemon
michael   2160  0.0  0.0 741484  5832 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-video/unity-video-lens-daemon
michael   2208  0.0  0.0 263300  3960 ?        Sl   07:28   0:00 /usr/bin/zeitgeist-daemon
michael   2214  0.0  0.0 225180  5408 ?        Sl   07:28   0:00 /usr/lib/zeitgeist/zeitgeist-fts
michael   2216  0.2  0.0 391188  7716 ?        Sl   07:28   0:00 zeitgeist-datahub
michael   2219  0.0  0.0  11672   624 ?        S    07:28   0:00 /bin/cat
michael   2224  0.0  0.0   4440   624 ?        S    07:28   0:00 sh -c /usr/lib/x86_64-linux-gnu/libproxy/0.4.7/pxgsettings org.gnome.system.proxy org
michael   2225  0.0  0.0 199556  3416 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/libproxy/0.4.7/pxgsettings org.gnome.system.proxy org.gnome
michael   2232  0.0  0.0   4440   628 ?        S    07:28   0:00 sh -c /usr/lib/x86_64-linux-gnu/libproxy/0.4.7/pxgsettings org.gnome.system.proxy org
michael   2233  0.0  0.0 199556  3416 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/libproxy/0.4.7/pxgsettings org.gnome.system.proxy org.gnome
root      2255  0.0  0.0      0     0 ?        S    07:28   0:00 [kworker/4:2]
michael   2260  0.0  0.0 276072  3656 ?        Sl   07:28   0:00 /usr/lib/libunity-webapps/unity-webapps-service
michael   2291  0.3  0.1 600708 18588 ?        Sl   07:28   0:00 /usr/bin/python3 /usr/lib/unity-lens-files/unity-scope-gdrive
michael   2293  0.3  0.0 452920 10400 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-video/unity-scope-video-remote
michael   2295  0.0  0.0 484448  7952 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/unity-lens-music/unity-musicstore-daemon
michael   2310  0.0  0.0   4440   628 ?        S    07:28   0:00 sh -c /usr/lib/x86_64-linux-gnu/libproxy/0.4.7/pxgsettings org.gnome.system.proxy org
michael   2311  0.0  0.0 199556  3420 ?        Sl   07:28   0:00 /usr/lib/x86_64-linux-gnu/libproxy/0.4.7/pxgsettings org.gnome.system.proxy org.gnome
root      2319  0.0  0.0 129480  2884 ?        Sl   07:28   0:00 /usr/lib/NetworkManager/nm-dispatcher.action
michael   2401  1.8  0.1 612936 19564 ?        Rl   07:28   0:00 gnome-terminal
michael   2407  0.0  0.0  14832   836 ?        S    07:28   0:00 gnome-pty-helper
michael   2408  0.2  0.0  26404  3140 pts/1    Ss   07:28   0:00 bash
michael   2463  2.6  0.2 524372 47580 ?        Sl   07:28   0:00 /usr/bin/signon-ui
michael   2466  0.0  0.0  22900  1360 pts/1    R+   07:28   0:00 ps axu
michael@michael-Ubuntu:~$
```

---

### Post by Aenima99x on 2013-08-12
Did you install and setup Miredo? If not, then I'd be worried about that.

root 1211 0.0 0.0 21492 684 ? Ss 07:27 0:00 /usr/sbin/miredo
miredo 1212 0.0 0.0 128164 1024 ? Sl 07:27 0:00 /usr/sbin/miredo
root 1468 0.0 0.0 8568 416 ? S 07:27 0:00 /usr/lib/miredo/miredo-privproc 4

Miredo - [http://manpages.ubuntu.com/manpages/raring/man8/miredo.8.html](http://manpages.ubuntu.com/manpages/raring/man8/miredo.8.html)

---

### Post by MikeCyber on 2013-08-13
Thanks yes I've installed Miredo. So all should be fine, I've questioned foremost the proxy and the libpeerconnection.log. Modemmanager ist necessary for WiFi I guess?

---

