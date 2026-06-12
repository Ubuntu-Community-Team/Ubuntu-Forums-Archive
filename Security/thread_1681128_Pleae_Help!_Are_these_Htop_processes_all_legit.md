---
title: "Pleae Help! Are these Htop processes all legit?"
date: 2011-02-03
forum: Security
---

### Post by Hagler on 2011-02-03
Hi,  I ran Htop and was really shocked to see all these processes running.  I'd be really grateful if any of you good souls can have a look at this list and give me an idea if these processes seem legit and safe. 

MyID=my username


```
  1  [||                                              0.7%]     Tasks: 171 total, 1 running
  2  [||                                              0.6%]     Load average: 0.29 0.18 0.07 
  Mem[|||||||||||||||||                         216/2012MB]     Uptime: 00:05:58
  Swp[                                            0/5890MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command           
    1 root      20   0  2536  1524  1136 S  0.0  0.1  0:00.79 /sbin/init
  457 root      20   0  2288   836   580 S  0.0  0.0  0:00.02 upstart-udev-bridge --daemon
  460 root      16  -4  2648  1052   300 S  0.0  0.1  0:00.02 udevd --daemon
  652 root      18  -2  2644  1028   276 S  0.0  0.0  0:00.00 udevd --daemon
  653 root      18  -2  2644  1032   276 S  0.0  0.1  0:00.00 udevd --daemon
 1058 messageb  20   0  3096  1508   760 S  0.0  0.1  0:00.12 dbus-daemon --system --fork
 1059 root      20   0  1856   544   448 S  0.0  0.0  0:00.04 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
 1072 haldaemo  20   0  6120  4064  3444 S  0.0  0.2  0:00.08 hald --daemon=yes
 1073 root      20   0 18532  3748  3140 S  0.0  0.2  0:00.02 NetworkManager
 1076 avahi     20   0  2828  1500  1236 S  0.0  0.1  0:00.00 avahi-daemon: registering [MyID-desktop.local]
 1077 syslog    20   0 34464  1748   976 S  0.0  0.1  0:00.00 rsyslogd -c4
 1078 avahi     20   0  2828   524   308 S  0.0  0.0  0:00.00 avahi-daemon: chroot helper
 1086 root      20   0  3916  2120  1704 S  0.0  0.1  0:00.02 /usr/sbin/modem-manager
 1103 root      20   0  8620  3328  2728 S  0.0  0.2  0:00.00 gdm-binary
 1113 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.02 /usr/sbin/console-kit-daemon
 1114 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1116 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1117 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1118 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1119 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1120 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1122 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1123 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1124 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1125 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1126 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1127 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1128 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1129 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1130 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1131 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1132 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1133 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1134 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1135 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1136 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1137 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1138 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1139 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1140 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1141 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1142 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1143 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1144 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1145 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1146 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1147 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1148 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1149 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1150 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1151 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1152 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1153 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1154 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1155 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1156 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1157 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1158 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1159 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1160 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1161 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1162 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1163 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1164 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1165 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1166 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1167 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1168 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1169 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1170 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1171 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1172 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1173 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1174 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1175 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1176 root      20   0  3348  1188   980 S  0.0  0.1  0:00.00 hald-runner
 1229 syslog    20   0 34464  1748   976 S  0.0  0.1  0:00.00 rsyslogd -c4
 1230 syslog    20   0 34464  1748   976 S  0.0  0.1  0:00.00 rsyslogd -c4
 1233 root      20   0  4788  1660  1396 S  0.0  0.1  0:00.00 /sbin/wpa_supplicant -u -s
 1234 root      20   0  2148   952   828 S  0.0  0.0  0:00.00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.ac
 1235 root      20   0 18532  3748  3140 S  0.0  0.2  0:00.00 NetworkManager
 1311 root      20   0  1708   544   464 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty4
 1325 root      20   0  1708   544   464 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty5
 1367 root      20   0  1708   548   464 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty2
 1370 root      20   0  1708   544   464 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty3
 1374 root      20   0  3424  1132   972 S  0.0  0.1  0:00.00 hald-addon-input: Listening on /dev/input/event1 /dev/input/eve
 1375 root      20   0  1708   540   464 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty6
 1379 root      20   0  1980   872   500 S  0.0  0.0  0:00.00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
 1395 root      20   0  3424  1140   972 S  0.0  0.1  0:00.09 hald-addon-storage: polling /dev/sr0 (every 2 sec)
 1397 root      20   0  2092   872   692 S  0.0  0.0  0:00.00 cron
 1398 daemon    20   0  1964   420   292 S  0.0  0.0  0:00.00 atd
 1399 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1413 root      20   0  8544  3288  2668 S  0.0  0.2  0:00.00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayMa
 1424 root      20   0  3432  1128   964 S  0.0  0.1  0:00.00 /usr/lib/hal/hald-addon-cpufreq
 1425 haldaemo  20   0  3268  1116   940 S  0.0  0.1  0:00.00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socke
 1458 clamav    20   0 13188  1448   896 S  0.0  0.1  0:00.00 /usr/bin/freshclam -d --quiet
 1500 root      20   0  551M 30728 10304 S  1.0  1.5  0:08.38 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-qqbv
 1520 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 1862 Debian-e  20   0  6548   904   540 S  0.0  0.0  0:00.00 /usr/sbin/exim4 -bd -q30m
 1913 root      20   0 11660  1560  1000 S  0.0  0.1  0:00.00 /usr/sbin/winbindd
 1985 root      20   0  6776  2568  1880 S  0.0  0.1  0:00.00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
 1986 root      20   0 11660  1296   736 S  0.0  0.1  0:00.00 /usr/sbin/winbindd
 2104 root      20   0  8648  2952  2388 S  0.0  0.1  0:00.00 /usr/lib/gdm/gdm-session-worker
 2116 root      20   0 20440  2996  2140 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2126 MyID      20   0 25672  6724  5264 S  0.0  0.3  0:00.08 gnome-session
 2171 root      20   0  1708   544   464 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty1
 2203 MyID      20   0  4716   612   284 S  0.0  0.0  0:00.00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /us
 2206 MyID      20   0  3388   728   468 S  0.0  0.0  0:00.00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session
 2207 MyID      20   0  3112  1340   604 S  0.0  0.1  0:00.12 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --sessi
 2211 MyID      20   0 94180  4556  3404 S  0.0  0.2  0:00.08 /usr/bin/pulseaudio --start
 2213 MyID      20   0 94180  4556  3404 S  0.0  0.2  0:00.00 /usr/bin/pulseaudio --start
 2214 MyID      20   0 94180  4556  3404 S  0.0  0.2  0:00.00 /usr/bin/pulseaudio --start
 2215 MyID      20   0 10640  2912  2324 S  0.0  0.1  0:00.00 /usr/lib/pulseaudio/pulse/gconf-helper
 2217 MyID      20   0  7748  4724  2180 S  0.0  0.2  0:00.26 /usr/lib/libgconf2-4/gconfd-2
 2222 root      20   0  5136  2480  2012 S  0.0  0.1  0:00.00 /usr/lib/devicekit-power/devkit-power-daemon
 2250 MyID      20   0 25672  6724  5264 S  0.0  0.3  0:00.00 gnome-session
 2252 MyID      20   0 40900  3100  2496 S  0.0  0.2  0:00.00 gnome-keyring-daemon --start
 2254 MyID      20   0 96644  9064  7076 S  0.0  0.4  0:00.24 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 2255 MyID      20   0 40900  3100  2496 S  0.0  0.2  0:00.00 gnome-keyring-daemon --start
 2256 MyID      20   0 40900  3100  2496 S  0.0  0.2  0:00.00 gnome-keyring-daemon --start
 2259 MyID      20   0 96644  9064  7076 S  0.0  0.4  0:00.00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 2260 MyID      20   0 22496  7324  5352 S  0.0  0.4  0:00.06 seahorse-daemon
 2263 MyID      20   0  5764  2184  1840 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfsd
 2267 MyID      20   0 17448  6344  5152 S  0.0  0.3  0:00.02 /usr/lib/notify-osd/notify-osd
 2270 MyID       20   0 29800  2456  1964 S  0.0  0.1  0:00.00 /usr/lib/gvfs//gvfs-fuse-daemon /home/MyID/.gvfs
 2271 MyID       20   0 29800  2456  1964 S  0.0  0.1  0:00.00 /usr/lib/gvfs//gvfs-fuse-daemon /home/MyID/.gvfs
 2272 MyID       20   0 29800  2456  1964 S  0.0  0.1  0:00.00 /usr/lib/gvfs//gvfs-fuse-daemon /home/MyID/.gvfs
 2273 MyID       20   0 29800  2456  1964 S  0.0  0.1  0:00.00 /usr/lib/gvfs//gvfs-fuse-daemon /home/MyID/.gvfs
 2274 MyID       20   0 62700 42324 12736 S  0.0  2.1  0:02.98 /usr/bin/compiz.real --sm-client-id 1056c2dd1d9dd90434126668964
 2278 MyID       20   0 57044 21008 14712 S  0.0  1.0  0:03.57 gnome-panel --sm-config-prefix /gnome-panel-1HdZxp/ --sm-client
 2290 MyID       20   0  1756   480   412 S  0.0  0.0  0:00.00 /bin/sh -c /usr/bin/compiz-decorator
 2291 MyID       20   0 20104  9576  7752 S  0.0  0.5  0:00.50 /usr/bin/gtk-window-decorator
 2293 MyID       20   0  106M 28096 16572 S  0.0  1.4  0:00.76 nautilus --sm-client-id 1056c2dd1d9dd90434126668964532261800000
 2295 MyID       20   0 41680  3508  2660 S  0.0  0.2  0:00.04 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activa
 2297 MyID       20   0 41680  3508  2660 S  0.0  0.2  0:00.00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activa
 2303 MyID       20   0 34244 10064  7540 S  0.0  0.5  0:00.06 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GN
 2304 MyID       20   0 60136 11428  9036 S  0.0  0.6  0:00.04 /usr/lib/evolution/2.28/evolution-alarm-notify --sm-config-pref
 2307 MyID       20   0 16552  5648  4596 S  0.0  0.3  0:00.00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
 2308 MyID       20   0 99828 11424  8588 S  0.0  0.6  0:00.08 gnome-volume-control-applet
 2310 MyID       20   0  6396  2848  2376 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
 2311 MyID       20   0 17168  6988  5700 S  0.0  0.3  0:00.04 gnome-power-manager
 2313 MyID       20   0 43424 12088  8912 S  0.0  0.6  0:00.12 nm-applet --sm-disable
 2318 MyID       20   0  6216  2776  2356 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spa
 2320 root      20   0  4952  2544  2116 S  0.0  0.1  0:00.02 /usr/lib/devicekit-disks/devkit-disks-daemon
 2321 root      20   0  4832   756   504 S  0.0  0.0  0:00.04 devkit-disks-daemon: polling /dev/sr0
 2324 MyID       20   0 29436 14460  8204 S  0.0  0.7  0:00.09 python /usr/share/system-config-printer/applet.py
 2328 MyID       20   0 17172  6456  5212 S  0.0  0.3  0:00.02 /usr/lib/gnome-disk-utility/gdu-notification-daemon
 2329 MyID       20   0 30312 10580  7964 S  0.0  0.5  0:00.12 update-notifier --startup-delay=60
 2332 MyID       20   0  6536  2212  1804 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 2334 MyID       20   0 60136 11428  9036 S  0.0  0.6  0:00.00 /usr/lib/evolution/2.28/evolution-alarm-notify --sm-config-pref
 2338 root      20   0  5852  3504  2740 S  0.0  0.2  0:00.02 /usr/lib/policykit-1/polkitd
 2340 MyID       20   0 52048 11196  8860 S  0.0  0.5  0:00.04 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activa
 2341 MyID       20   0 17444  2632  1396 S  0.0  0.1  0:00.00 gnome-screensaver
 2342 MyID       20   0 52048 11196  8860 S  0.0  0.5  0:00.00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activa
 2344 MyID       20   0 78828  8780  6716 S  0.0  0.4  0:00.02 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-ii
 2345 MyID       20   0 78828  8780  6716 S  0.0  0.4  0:00.00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-ii
 2349 MyID       20   0 35172 11064  8364 S  0.0  0.5  0:00.09 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=O
 2351 MyID       20   0 36352 12524  9656 S  0.0  0.6  0:00.09 /usr/lib/indicator-applet/indicator-applet-session --oaf-activa
 2360 MyID       20   0 78828  8780  6716 S  0.0  0.4  0:00.00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-ii
 2374 MyID       20   0  8240  3500  2784 S  0.0  0.2  0:00.04 /usr/lib/indicator-messages/indicator-messages-service
 2376 MyID       20   0 11936  3168  2600 S  0.0  0.2  0:00.00 /usr/lib/indicator-session/indicator-status-service
 2379 MyID       20   0  6908  2676  2268 S  0.0  0.1  0:00.00 /usr/lib/indicator-session/indicator-session-service
 2380 MyID       20   0  6340  2112  1792 S  0.0  0.1  0:00.00 /usr/lib/indicator-session/indicator-users-service
 2394 MyID       20   0  6324  2488  1532 S  0.0  0.1  0:00.02 /usr/lib/gvfs/gvfsd-metadata
 2398 MyID       20   0  5768  2260  1940 S  0.0  0.1  0:00.00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw
 2446 MyID       21   1 50664 19636 11980 S  0.0  1.0  0:04.09 gedit
 2454 MyID       20   0 43308 13528  9924 S  1.0  0.7  0:02.50 /usr/bin/gnome-terminal -x htop
 2455 MyID       20   0  1908   700   572 S  0.0  0.0  0:00.00 gnome-pty-helper
 2456 MyID       20   0  2508  1276   952 R  0.0  0.1  0:02.46 htop
 2457 MyID       20   0 43308 13528  9924 S  0.0  0.7  0:00.00 /usr/bin/gnome-terminal -x htop
```Thanks!

---

### Post by mlentink on 2011-02-03
[http://ubuntuforums.org/showthread.php?t=556272](http://ubuntuforums.org/showthread.php?t=556272)
[http://ubuntuforums.org/showthread.php?t=1284873](http://ubuntuforums.org/showthread.php?t=1284873)
[http://www.google.com/search?client=ubuntu&channel=fs&q=console-kit-daemon&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=console-kit-daemon&ie=utf-8&oe=utf-8)

---

### Post by Hagler on 2011-02-03
> **mlentink said:**
> [http://ubuntuforums.org/showthread.php?t=556272](http://ubuntuforums.org/showthread.php?t=556272)
[http://ubuntuforums.org/showthread.php?t=1284873](http://ubuntuforums.org/showthread.php?t=1284873)
[http://www.google.com/search?client=ubuntu&channel=fs&q=console-kit-daemon&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=console-kit-daemon&ie=utf-8&oe=utf-8)

Thanks for your really unhelpful links and reply :(      I feel that basically your telling me that a beginner has no right to part of the Ubuntu Community, and therefore has no right to use the OS if they can't fully comprehend it's workings.    I'm struggling to get to terms with using Ubuntu, and it really does not help when people become obstructive and impatient.       H

---

### Post by uRock on 2011-02-03
Those links explain more about the console-kit-daemon process that shows up multiple times in our htop outputs. The process is normal. The links also explain how to stop the process from running, which make them helpful.

You can find a lot of answers by googling the name of the process and including the keyword "ubuntu" in the search.

It is hard for someone to say what is and what isn't normal without knowing everything you have installed and have running.

Edit: Moved to security discussions sub-forum.

---

### Post by Hagler on 2011-02-03
I'm very sorry uRock but I must disagree.  The links which deal with console-kit-daemon processes seem to very ambiguous to say the least, and don't seem to find a definitive answer to the problem.

I would really be grateful you or anyone else could give any advice regarding the other processes.

Thanks

---

### Post by spynappels on 2011-02-03
Are you running server edition or desktop edition?

Edit: I see you are running desktop, so the daemon COULD be used if you ever have more than one session active at any one time.

One of the links included a comment that the numerous instances you see running are probably threads of the same process, and in any case only 1 process is actually running, the rest are just waiting. You're only using 10-15% of your RAM so you're fine.

This is a very friendly community, sometimes people simply answer the same questions so many times that a simple link is easier to give. The information was there, it can PROBABLY be safely removed from a headless server, but not from a desktop.

Essentially, as far as I can tell, all the processes are legit.

---

### Post by Hagler on 2011-02-03
Thanks Spynappels,   it's good to hear that you think that the processes are legit.       I sincerely apologize to mlentick & uRock for appearing to be offhand, I'm just a bit frustrated by my own lack of knowledge, and the apparent lack of easily findable help for new users like me.      Once again I'm sorry, and I really appreciate your help.       Thanks.

---

### Post by uRock on 2011-02-03
No problem. I usually google a process that I do not recognize. Watching htop takes a little while to get used to, but once you learn the common processes it will get easier.

Most people will see different processes due to having different configurations and different applications installed and running.

Do feel free to ask questions as they come up.

Cheers,
uRock

---

