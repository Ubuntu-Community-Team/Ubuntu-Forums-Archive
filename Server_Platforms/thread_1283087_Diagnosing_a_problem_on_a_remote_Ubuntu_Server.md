---
title: "Diagnosing a problem on a remote Ubuntu Server"
date: 2009-10-05
forum: Server Platforms
---

### Post by lloowen on 2009-10-05
Hi all,
 
This is my very first forum post here :popcorn:
 
 
I have set up a server remotely using ssh putty. On this server is the usual stuff. Apache2.2, php5, mysql, sftp, samba. This server is sitting in side a LAN and I connect to it using the dynamic IP addressing service provided by dyndns.com. Every thing worked like a dream until one day when I tried to log in using my ssh putty and I could not get in!
The last thing I had been doing just prior to loosing contact, was setting up vnc4server. 
 
 
I did the usual ping'ing and traceroute but could not get through. 
I asked the owner of the Server to have a look his end. He says he cannot use the web server, sftp or ssh on his LAN. However he can access the server using a vnc client set up on his mac and he can access his samba share. 
 
He has four ps on his LAN and I think he is using two routers.
 
I asked him to email me a copy of the history commands to re-trace my steps. Every thing looks normal. The only things I am suspicious of is that I ran the commands:
 
 
# apt-get update
 
and
 
# apt-get install vnc4server xinetd
 
Would doing an update throw a spanner in the works? I have later read that Ubuntu uses the application inetd instead of xinetd. Would this mess things up?
 
I have also asked the owner to pipe the outputs of the commands 'ps aux' and 'netstat -an | grep LISTEN' and email them to me. 
 
 
I am not up on interpreting this data. But as far as I can tell all the servers are running and the ports are open. If so this is indeed a router firewall conflict/problem. 
That is what I deduce. But it is likely that I am wrong. I'd be grateful if anyone could please scan the outputs from 'ps aux' and 'netstat -an | grep LISTEN' below and confirm that I read the information correclty.
 
 
Thanks in advance
 
 
 
**********************************************************************
 
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
root 1 0.0 0.0 3084 296 ? Ss Oct03 0:01 /sbin/init
root 2 0.0 0.0 0 0 ? S< Oct03 0:00 [kthreadd]
root 3 0.0 0.0 0 0 ? S< Oct03 0:00 [migration/0]
root 4 0.0 0.0 0 0 ? S< Oct03 0:00 [ksoftirqd/0]
root 5 0.0 0.0 0 0 ? S< Oct03 0:00 [watchdog/0]
root 6 0.0 0.0 0 0 ? S< Oct03 0:00 [events/0]
root 7 0.0 0.0 0 0 ? S< Oct03 0:00 [khelper]
root 8 0.0 0.0 0 0 ? S< Oct03 0:00 [kstop/0]
root 9 0.0 0.0 0 0 ? S< Oct03 0:00 [kintegrityd/0]
root 10 0.0 0.0 0 0 ? R< Oct03 0:00 [kblockd/0]
root 11 0.0 0.0 0 0 ? S< Oct03 0:00 [kacpid]
root 12 0.0 0.0 0 0 ? S< Oct03 0:00 [kacpi_notify]
root 13 0.0 0.0 0 0 ? S< Oct03 0:00 [cqueue]
root 14 0.0 0.0 0 0 ? S< Oct03 0:02 [ata/0]
root 15 0.0 0.0 0 0 ? S< Oct03 0:00 [ata_aux]
root 16 0.0 0.0 0 0 ? S< Oct03 0:00 [ksuspend_usbd]
root 17 0.0 0.0 0 0 ? S< Oct03 0:00 [khubd]
root 18 0.0 0.0 0 0 ? S< Oct03 0:00 [kseriod]
root 19 0.0 0.0 0 0 ? S< Oct03 0:00 [kmmcd]
root 20 0.0 0.0 0 0 ? S< Oct03 0:00 [btaddconn]
root 21 0.0 0.0 0 0 ? S< Oct03 0:00 [btdelconn]
root 23 0.0 0.0 0 0 ? S Oct03 0:00 [pdflush]
root 24 0.0 0.0 0 0 ? S< Oct03 0:00 [kswapd0]
root 25 0.0 0.0 0 0 ? S< Oct03 0:00 [aio/0]
root 26 0.0 0.0 0 0 ? S< Oct03 0:00 [ecryptfs-kthrea]
root 29 0.0 0.0 0 0 ? S< Oct03 0:00 [scsi_eh_0]
root 30 0.0 0.0 0 0 ? S< Oct03 0:04 [scsi_eh_1]
root 31 0.0 0.0 0 0 ? S< Oct03 0:00 [kstriped]
root 32 0.0 0.0 0 0 ? S< Oct03 0:00 [kmpathd/0]
root 33 0.0 0.0 0 0 ? S< Oct03 0:00 [kmpath_handlerd]
root 34 0.0 0.0 0 0 ? S< Oct03 0:00 [ksnapd]
root 35 0.0 0.0 0 0 ? S< Oct03 0:00 [kondemand/0]
root 36 0.0 0.0 0 0 ? S< Oct03 0:00 [krfcommd]
root 654 0.0 0.0 0 0 ? S< Oct03 0:01 [kjournald]
root 788 0.0 0.0 2224 248 ? S<s Oct03 0:00 /sbin/udevd --daemon
root 1093 0.0 0.0 0 0 ? S< Oct03 0:00 [kpsmoused]
root 1964 0.0 0.0 1808 196 tty4 Ss+ Oct03 0:00 /sbin/getty 38400 tty4
root 1965 0.0 0.0 1808 196 tty5 Ss+ Oct03 0:00 /sbin/getty 38400 tty5
root 1971 0.0 0.0 1808 196 tty2 Ss+ Oct03 0:00 /sbin/getty 38400 tty2
root 1973 0.0 0.0 1808 196 tty3 Ss+ Oct03 0:00 /sbin/getty 38400 tty3
root 1974 0.0 0.0 1808 196 tty6 Ss+ Oct03 0:00 /sbin/getty 38400 tty6
root 2042 0.0 0.0 2204 212 ? Ss Oct03 0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog 2083 0.0 0.0 2040 412 ? Ss Oct03 0:00 /sbin/syslogd -u syslog
root 2104 0.0 0.0 1968 180 ? S Oct03 0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog 2106 0.0 0.0 3628 288 ? Ss Oct03 0:00 /sbin/klogd -P /var/run/klogd/kmsg
108 2127 0.0 0.2 3256 1312 ? Ss Oct03 0:04 /bin/dbus-daemon --system
root 2202 0.0 0.0 1872 164 ? S Oct03 0:00 /bin/sh /usr/bin/mysqld_safe
mysql 2244 0.0 0.3 128804 1536 ? Sl Oct03 1:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root 2246 0.0 0.0 1792 208 ? S Oct03 0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root 2316 0.0 0.3 6060 1712 ? S Oct03 0:02 ddclient - sleeping for 140 seconds
root 2350 0.0 0.2 7232 1136 ? Ss Oct03 0:01 /usr/sbin/nmbd -D
root 2392 0.0 0.2 12988 1360 ? Ss Oct03 0:00 /usr/sbin/smbd -D
111 2440 0.0 0.3 6656 1672 ? Ss Oct03 0:04 /usr/sbin/hald
root 2451 0.0 0.3 16856 1960 ? Ssl Oct03 0:02 /usr/sbin/console-kit-daemon
root 2455 0.0 0.0 12988 324 ? S Oct03 0:00 /usr/sbin/smbd -D
root 2558 0.0 0.1 3328 624 ? S Oct03 0:00 hald-runner
root 2621 0.0 0.0 5176 412 ? S Oct03 0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3
root 2666 0.0 0.1 5180 580 ? S Oct03 0:05 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root 2667 0.0 0.1 5180 572 ? S Oct03 0:00 hald-addon-storage: no polling on /dev/fd0 because it is explicitly disabled
111 2671 0.0 0.0 5032 264 ? S Oct03 0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root 2685 0.0 0.0 3556 452 ? Ss Oct03 0:00 /usr/sbin/bluetoothd
root 2718 0.0 0.0 15028 432 ? Ss Oct03 0:00 /usr/sbin/gdm
root 2723 0.0 0.1 15552 620 ? S Oct03 0:00 /usr/sbin/gdm
root 2727 0.5 2.7 43260 13860 tty7 Rs+ Oct03 7:34 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root 2742 0.0 0.4 16304 2040 ? Ssl Oct03 0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root 2747 0.0 0.0 4280 320 ? S Oct03 0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root 2751 0.0 0.2 6932 1160 ? S Oct03 0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
avahi 2766 0.0 0.1 2944 880 ? Ss Oct03 0:00 avahi-daemon: running [richard-desktop.local]
avahi 2767 0.0 0.0 2944 120 ? Ss Oct03 0:00 avahi-daemon: chroot helper
root 2791 0.0 0.2 6108 1280 ? Ss Oct03 0:00 /usr/sbin/cupsd
[COLOR=red]proftpd 2812 0.0 0.0 5624 356 ? Ss Oct03 0:00 proftpd: (accepting connections)[/COLOR]
root 2840 0.0 0.0 4324 448 ? Ss Oct03 0:00 /usr/bin/system-tools-backends
daemon 2919 0.0 0.0 2096 176 ? Ss Oct03 0:00 /usr/sbin/atd
root 2947 0.0 0.0 3480 352 ? Ss Oct03 0:00 /usr/sbin/cron
root 2992 0.0 1.3 46552 6752 ? Ss Oct03 0:03 /usr/sbin/apache2 -k start
root 3069 0.0 0.0 1808 196 tty1 Ss+ Oct03 0:00 /sbin/getty 38400 tty1
richard 3150 0.0 0.4 26416 2392 ? Ssl Oct03 0:00 x-session-manager
richard 3207 0.0 0.0 4784 128 ? Ss Oct03 0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
richard 3210 0.0 0.0 3144 260 ? S Oct03 0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
richard 3211 0.0 0.2 3068 1024 ? Ss Oct03 0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
richard 3221 0.0 0.2 94680 1160 ? Ssl Oct03 0:00 /usr/bin/pulseaudio --start
richard 3222 0.0 0.1 7844 568 ? S Oct03 0:00 /usr/lib/pulseaudio/pulse/gconf-helper
richard 3224 0.0 0.4 7596 2224 ? S Oct03 0:02 /usr/lib/libgconf2-4/gconfd-2
richard 3236 0.0 0.2 19112 1412 ? Ss Oct03 0:00 /usr/bin/seahorse-agent --execute x-session-manager
richard 3241 0.0 0.5 29144 2756 ? Ssl Oct03 0:02 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
richard 3243 0.0 0.1 17448 884 ? S Oct03 0:00 gnome-keyring-daemon --start
richard 3245 0.0 0.1 5616 956 ? S Oct03 0:00 /usr/lib/gvfs/gvfsd
richard 3253 0.0 0.2 38940 1060 ? Ssl Oct03 0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/richard/.gvfs
richard 3259 0.0 1.5 21000 8032 ? S Oct03 0:16 /usr/bin/metacity --replace
richard 3280 0.1 2.1 36756 11052 ? S Oct03 2:30 gnome-panel
richard 3281 0.0 1.6 64028 8340 ? R Oct03 0:07 nautilus
richard 3283 0.0 0.1 40748 648 ? Ssl Oct03 0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
richard 3286 0.1 3.7 65316 19228 ? S Oct03 2:50 /usr/lib/vino/vino-server
richard 3287 0.0 0.3 16116 1964 ? S Oct03 0:00 bluetooth-applet
richard 3290 0.0 0.4 27808 2376 ? S Oct03 0:00 python /usr/share/system-config-printer/applet.py
richard 3294 0.0 0.6 27928 3220 ? S Oct03 0:01 update-notifier --startup-delay=60
richard 3295 0.0 0.8 23720 4440 ? S Oct03 0:01 nm-applet --sm-disable
richard 3296 0.0 0.6 42644 3144 ? Sl Oct03 0:00 /usr/lib/evolution/2.26/evolution-alarm-notify
richard 3306 0.0 0.4 24748 2400 ? Ss Oct03 0:01 gnome-power-manager
richard 3308 0.0 1.1 23116 5872 ? S Oct03 0:01 /usr/lib/notify-osd/notify-osd
richard 3312 0.0 0.2 7836 1512 ? S Oct03 0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
richard 3314 0.0 1.3 25492 6960 ? S Oct03 0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
richard 3317 0.0 0.2 5940 1236 ? S Oct03 0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
richard 3319 0.0 0.1 8212 972 ? S Oct03 0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
richard 3325 0.0 0.7 27300 3900 ? S Oct03 0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=19
richard 3328 0.0 0.6 44388 3072 ? Sl Oct03 0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=26
richard 3331 0.0 0.6 22548 3436 ? S Oct03 0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=32
richard 3336 0.0 0.1 5616 660 ? S Oct03 0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
richard 3349 0.0 0.7 16652 3944 ? Ss Oct03 0:08 gnome-screensaver
richard 3351 1.0 14.8 180824 75656 ? Rl Oct03 15:37 /usr/lib/firefox-3.0.14/firefox
root 3371 0.0 0.5 13620 2564 ? S Oct03 0:00 /usr/bin/python /usr/lib/system-service/system-service-d
richard 3376 0.0 2.0 98040 10412 ? SN Oct03 0:15 /usr/bin/python2.6 /usr/bin/update-manager --no-focus-on-map
root 3407 0.0 0.0 4132 328 ? S Oct03 0:00 su
root 3415 0.0 0.1 4328 648 ? S Oct03 0:00 bash
[COLOR=red]root 3506 0.0 0.0 5436 216 ? Ss Oct03 0:00 /usr/sbin/sshd[/COLOR]
root 4451 0.0 0.6 11968 3240 ? S Oct03 0:01 Xvnc :1 -desktop richard-desktop:1 (root) -auth /home/richard/.Xauthority -geometry 1024x768 -depth 16 -rfbwait 30000 -rfbauth /root/.vnc/passwd -rfbport 5901 -pn -extension XFIXES
root 4453 0.0 0.3 26248 1956 ? Sl Oct03 0:00 x-session-manager
root 4492 0.0 0.0 3144 228 ? S Oct03 0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
root 4493 0.0 0.0 2936 480 ? Ss Oct03 0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root 4497 0.0 0.2 94552 1064 ? S<sl Oct03 0:00 /usr/bin/pulseaudio --start
root 4498 0.0 0.1 7844 592 ? S Oct03 0:00 /usr/lib/pulseaudio/pulse/gconf-helper
root 4500 0.0 0.3 7596 1696 ? S Oct03 0:01 /usr/lib/libgconf2-4/gconfd-2
root 4511 0.0 0.2 18784 1212 ? Ss Oct03 0:00 /usr/bin/seahorse-agent --execute x-session-manager
root 4514 0.0 0.1 5616 908 ? S Oct03 0:00 /usr/lib/gvfs/gvfsd
root 4519 0.0 0.2 29584 1208 ? Ssl Oct03 0:00 /usr/lib/gvfs//gvfs-fuse-daemon /root/.gvfs
root 4530 0.0 0.2 25648 1128 ? S Oct03 0:00 gnome-keyring-daemon --start
root 4534 0.0 0.5 16772 2692 ? S Oct03 0:00 /usr/bin/metacity --replace
root 4557 0.0 1.5 33960 7672 ? S Oct03 0:06 gnome-panel
root 4558 0.0 1.1 51992 5760 ? S Oct03 0:01 nautilus
root 4560 0.0 0.2 40748 1436 ? Ssl Oct03 0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
root 4563 0.0 0.5 16788 2600 ? S Oct03 0:00 bluetooth-applet
root 4564 0.0 1.4 27680 7404 ? S Oct03 0:00 python /usr/share/system-config-printer/applet.py
root 4570 0.0 0.8 42496 4328 ? Sl Oct03 0:00 /usr/lib/evolution/2.26/evolution-alarm-notify
root 4576 0.0 0.6 24480 3520 ? Ss Oct03 0:00 gnome-power-manager
root 4585 0.0 0.5 17244 2732 ? S Oct03 0:00 /usr/lib/notify-osd/notify-osd
root 4587 0.0 0.2 5940 1476 ? S Oct03 0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
root 4588 0.0 0.0 0 0 ? S Oct03 0:00 [pdflush]
root 4592 0.0 0.3 7836 1788 ? S Oct03 0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
root 4594 0.0 0.2 8212 1348 ? S Oct03 0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
root 4599 0.0 0.7 22704 3560 ? S Oct03 0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
root 4603 0.0 1.0 26144 5184 ? S Oct03 0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=19
root 4606 0.0 0.9 42764 5072 ? Sl Oct03 0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
root 4609 0.0 0.6 22296 3308 ? S Oct03 0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=29
root 4612 0.0 0.1 5616 952 ? S Oct03 0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
root 22224 0.0 0.1 2276 664 ? S 17:35 0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
richard 22289 0.0 0.4 13180 2064 ? S 17:35 0:00 /usr/sbin/smbd -D
richard 23804 0.1 2.7 33852 14108 ? Sl 18:10 0:03 gnome-terminal
richard 23805 0.0 0.1 2036 668 ? S 18:10 0:00 gnome-pty-helper
richard 23806 0.0 0.5 5820 2800 pts/1 Ss 18:10 0:00 bash
root 23823 0.0 0.2 4132 1424 pts/1 S 18:10 0:00 su
root 23831 0.0 0.3 4332 1740 pts/1 S 18:10 0:00 bash
root 26743 0.0 0.2 2768 1032 pts/1 R+ 19:06 0:00 ps aux
[COLOR=red]www-data 32746 0.0 1.0 46552 5212 ? S 07:50 0:00 /usr/sbin/apache2 -k start[/COLOR]
[COLOR=red]www-data 32747 0.0 1.0 46552 5212 ? S 07:50 0:00 /usr/sbin/apache2 -k start[/COLOR]
[COLOR=red]www-data 32748 0.0 1.0 46552 5212 ? S 07:50 0:00 /usr/sbin/apache2 -k start[/COLOR]
[COLOR=red]www-data 32749 0.0 1.0 46552 5212 ? S 07:50 0:00 /usr/sbin/apache2 -k start[/COLOR]
[COLOR=red]www-data 32750 0.0 1.0 46552 5212 ? S 07:50 0:00 /usr/sbin/apache2 -k start[/COLOR]
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN 
tcp 0 0 0.0.0.0:5901 0.0.0.0:* LISTEN 
tcp 0 0 0.0.0.0:6001 0.0.0.0:* LISTEN 
[COLOR=red]tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN[/COLOR] 
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 
tcp6 0 0 :::139 :::* LISTEN 
[COLOR=red]tcp6 0 0 :::5900 :::* LISTEN[/COLOR] 
[COLOR=red]tcp6 0 0 :::80 :::* LISTEN[/COLOR] 
tcp6 0 0 :::6001 :::* LISTEN 
[COLOR=red]tcp6 0 0 :::21 :::* LISTEN [/COLOR]
[COLOR=red]tcp6 0 0 :::22 :::* LISTEN[/COLOR] 
tcp6 0 0 ::1:631 :::* LISTEN 
tcp6 0 0 :::445 :::* LISTEN 
unix 2 [ ACC ] STREAM LISTENING 7665 /tmp/.X11-unix/X0
unix 2 [ ACC ] STREAM LISTENING 8697 /tmp/ssh-rEiewl3150/agent.3150
unix 2 [ ACC ] STREAM LISTENING 5645 /var/run/dbus/system_bus_socket
unix 2 [ ACC ] STREAM LISTENING 8788 /tmp/orbit-richard/linc-c98-0-1ea57f9033c3
unix 2 [ ACC ] STREAM LISTENING 8900 /tmp/orbit-richard/linc-c96-0-3b2d60362dafe
unix 2 [ ACC ] STREAM LISTENING 8915 /tmp/.esd-1000/socket
unix 2 [ ACC ] STREAM LISTENING 8918 /home/richard/.pulse/a306ecce6d054911967154484abe24cc:runtime/native
unix 2 [ ACC ] STREAM LISTENING 8958 /tmp/seahorse-H9wOOk/S.gpg-agent
unix 2 [ ACC ] STREAM LISTENING 8989 /tmp/.ICE-unix/3150
unix 2 [ ACC ] STREAM LISTENING 9007 /tmp/orbit-richard/linc-c4e-0-77dc51fe3c4c7
unix 2 [ ACC ] STREAM LISTENING 9116 /tmp/orbit-richard/linc-ca9-0-748de784e7793
unix 2 [ ACC ] STREAM LISTENING 9129 /tmp/keyring-ME1mCn/socket
unix 2 [ ACC ] STREAM LISTENING 9138 /tmp/orbit-richard/linc-caa-0-3b7b5b3450c95
unix 2 [ ACC ] STREAM LISTENING 9142 /tmp/keyring-ME1mCn/socket.ssh
unix 2 [ ACC ] STREAM LISTENING 9144 /tmp/keyring-ME1mCn/socket.pkcs11
unix 2 [ ACC ] STREAM LISTENING 9243 /tmp/orbit-richard/linc-ca4-0-6b51b1fde2ab4
unix 2 [ ACC ] STREAM LISTENING 9390 /tmp/orbit-richard/linc-cbb-0-7197564f7ad50
unix 2 [ ACC ] STREAM LISTENING 9437 /tmp/orbit-richard/linc-cd0-0-60d0381719fff
unix 2 [ ACC ] STREAM LISTENING 9835 /tmp/orbit-richard/linc-cd7-0-2d6c49a0ed6d
unix 2 [ ACC ] STREAM LISTENING 9932 /tmp/orbit-richard/linc-cd1-0-1dadf1825571f
unix 2 [ ACC ] STREAM LISTENING 9984 /tmp/orbit-richard/linc-cd6-0-f9373c795815
unix 2 [ ACC ] STREAM LISTENING 196133 /var/run/cups/cups.sock
unix 2 [ ACC ] STREAM LISTENING 10035 /tmp/orbit-richard/linc-cdd-0-f9373c7bda8d
unix 2 [ ACC ] STREAM LISTENING 10041 /tmp/orbit-richard/linc-cde-0-f9373c7c130d
unix 2 [ ACC ] STREAM LISTENING 10057 /tmp/orbit-richard/linc-cdf-0-31928dc0db278
unix 2 [ ACC ] STREAM LISTENING 10086 /tmp/orbit-richard/linc-cec-0-54d76f6c51b06
unix 2 [ ACC ] STREAM LISTENING 10093 /tmp/orbit-richard/linc-cd3-0-452b9ae79215f
unix 2 [ ACC ] STREAM LISTENING 10212 /tmp/orbit-richard/linc-cf2-0-4af264f53be86
unix 2 [ ACC ] STREAM LISTENING 10414 /tmp/orbit-richard/linc-d03-0-603e5247d829c
unix 2 [ ACC ] STREAM LISTENING 10428 /tmp/orbit-richard/linc-d00-0-45616c4ce0d68
unix 2 [ ACC ] STREAM LISTENING 10453 /tmp/orbit-richard/linc-cfd-0-7a210bfb32752
unix 2 [ ACC ] STREAM LISTENING 10753 /tmp/orbit-richard/linc-d14-0-6f87e0f0d4b02
unix 2 [ ACC ] STREAM LISTENING 10812 /tmp/orbit-richard/linc-d17-0-3db4d6abcc44e
unix 2 [ ACC ] STREAM LISTENING 10840 /tmp/orbit-richard/linc-ce0-0-19aba205b533f
unix 2 [ ACC ] STREAM LISTENING 11327 /tmp/orbit-richard/linc-d30-0-2127056b4e628
unix 2 [ ACC ] STREAM LISTENING 340069 /tmp/orbit-richard/linc-5cfc-0-33ee103872cae
unix 2 [ ACC ] STREAM LISTENING 18125 /tmp/.X11-unix/X1
unix 2 [ ACC ] STREAM LISTENING 18482 /tmp/.ICE-unix/4453
unix 2 [ ACC ] STREAM LISTENING 18224 /tmp/orbit-richard/linc-1194-0-7176af97ba8be
unix 2 [ ACC ] STREAM LISTENING 18404 /tmp/orbit-richard/linc-1192-0-21a49fe6eca3f
unix 2 [ ACC ] STREAM LISTENING 7739 /var/run/avahi-daemon/socket
unix 2 [ ACC ] STREAM LISTENING 18414 /tmp/.esd-0/socket
unix 2 [ ACC ] STREAM LISTENING 18417 /root/.pulse/a306ecce6d054911967154484abe24cc:runtime/native
unix 2 [ ACC ] STREAM LISTENING 18514 /tmp/orbit-richard/linc-1165-0-5bf5a5bcea370
unix 2 [ ACC ] STREAM LISTENING 19353 /tmp/orbit-richard/linc-11d3-0-5c6bc9207a33e
unix 2 [ ACC ] STREAM LISTENING 18697 /tmp/keyring-Iuu4Rc/socket
unix 2 [ ACC ] STREAM LISTENING 18706 /tmp/orbit-richard/linc-11af-0-122cfdeeda91e
unix 2 [ ACC ] STREAM LISTENING 18710 /tmp/keyring-Iuu4Rc/socket.ssh
unix 2 [ ACC ] STREAM LISTENING 18712 /tmp/keyring-Iuu4Rc/socket.pkcs11
unix 2 [ ACC ] STREAM LISTENING 18902 /tmp/orbit-richard/linc-11b6-0-421bc58ecd25d
unix 2 [ ACC ] STREAM LISTENING 18949 /tmp/orbit-richard/linc-11cd-0-6680c32f95b1e
unix 2 [ ACC ] STREAM LISTENING 19406 /tmp/orbit-richard/linc-11d7-0-29319ba93503
unix 2 [ ACC ] STREAM LISTENING 19599 /tmp/orbit-richard/linc-11d0-0-4ddd775cc6b6c
unix 2 [ ACC ] STREAM LISTENING 19436 /tmp/orbit-richard/linc-11ce-0-20dfe69daedeb
unix 2 [ ACC ] STREAM LISTENING 7500 /var/run/sdp
unix 2 [ ACC ] STREAM LISTENING 19550 /tmp/orbit-richard/linc-11e9-0-2c7e25d6174ef
unix 2 [ ACC ] STREAM LISTENING 19699 /tmp/orbit-richard/linc-11f7-0-1ee13bc516703
unix 2 [ ACC ] STREAM LISTENING 19870 /tmp/orbit-richard/linc-1201-0-44dbd69bbeea0
unix 2 [ ACC ] STREAM LISTENING 5456 /var/run/acpid.socket
unix 2 [ ACC ] STREAM LISTENING 19875 /tmp/orbit-richard/linc-11fe-0-2a5904cfc38e6
unix 2 [ ACC ] STREAM LISTENING 19899 /tmp/orbit-richard/linc-11fb-0-2f2bcabbe4b9d
unix 2 [ ACC ] STREAM LISTENING 7510 @/org/bluez/audio
unix 2 [ ACC ] STREAM LISTENING 20243 /tmp/orbit-richard/linc-11da-0-62853b7fc2220
unix 2 [ ACC ] STREAM LISTENING 7664 @/tmp/.X11-unix/X0
unix 2 [ ACC ] STREAM LISTENING 6660 @/var/run/hald/dbus-jTMAlJfFTH
unix 2 [ ACC ] STREAM LISTENING 8712 @/tmp/dbus-qeOrTvE3U1
unix 2 [ ACC ] STREAM LISTENING 7573 /var/run/gdm_socket
unix 2 [ ACC ] STREAM LISTENING 5804 /var/run/mysqld/mysqld.sock
unix 2 [ ACC ] STREAM LISTENING 6421 @/var/run/hald/dbus-yL0kSCR29O
unix 2 [ ACC ] STREAM LISTENING 18174 @/tmp/dbus-08TUYrNNKj

---

### Post by lloowen on 2009-10-05
Please!!! Doesn't anyone have any ideas how I can fix this problem?!!!
 
Thanks

---

### Post by Lars Noodén on 2009-10-06
Can the owner ping the machine from his mac?

---

### Post by lloowen on 2009-10-06
Hello, thanks for replying.

I've now got it figured out.

We tried the pining of all the hardware on his LAN. We found the problem. The DHCP server on his router had changed his LAN IP for the Ubuntu server. Now we've changed it back, but this time it's locked. So hopefully no more problems of that kind.

Thanks.

---

