---
title: "Ubuntu Hardy Heron - &quot;Clipboard&quot; hijacked"
date: 2008-08-11
forum: Security
---

### Post by TC10284 on 2008-08-11
All,

Since late last week I have been noticing that anything I copy/paste to the "clipboard" in Ubuntu doesn't stick. I keep getting a link pasted like this **DON'T OPEN IT!** "http://xp-vista-update.net/?id=31863829103" **DON'T OPEN IT!** (not including the DON'T OPEN IT part - that was my warning)

Which is one of the typical adware/spyware sites out there that likes to screw up your OS.

Today I found out when I right-clicked to create a new folder, I saw a strange thing when I looked at "Paste". I noticed it would flash from black, meaning that were was something in the clipboard to be pasted, to gray, like the clipboard had been erased. There is obviously a script or cron job overwriting my clipboard. But my question is, how/where do I find it and how do I kill it as it's becoming quite annoying...
I can use the middle click on my laptop. But I prefer ctrl-v to paste.

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 6220 tavisc    20   0  256m  35m  13m S    9  1.8   4:16.27 compiz.real                                                                                                         
 5807 root      20   0  972m  80m  11m S    8  4.0   7:03.95 Xorg                                                                                                                
 7269 tavisc    20   0  145m  50m  11m S    4  2.5   4:39.26 npviewer.bin                                                                                                        
 6773 tavisc    20   0  984m 523m  25m S    2 26.2  22:27.74 firefox                                                                                                             
 7236 tavisc    20   0  533m  48m  34m S    2  2.4   1:13.27 totem-plugin-vi                                                                                                     
 6127 tavisc    20   0  148m 7168 4300 S    1  0.4   1:54.97 pulseaudio                                                                                                          
 6794 tavisc    20   0  264m  27m  12m S    1  1.4   0:06.10 gnome-terminal                                                                                                      
 7098 tavisc    20   0  648m  47m  22m S    1  2.4   0:46.33 pidgin                                                                                                              
 6139 tavisc    20   0  135m 6536 4668 S    1  0.3   0:09.98 gnome-screensav                                                                                                     
 6145 tavisc    20   0  311m  27m  14m S    1  1.4   0:22.44 gnome-panel                                                                                                         
 6240 tavisc    20   0  373m  10m 8056 S    1  0.5   0:17.30 gnome-cups-icon                                                                                                     
22302 tavisc    20   0 18992 1276  932 R    1  0.1   0:00.12 top                                                                                                                 
    1 root      20   0  4020  888  600 S    0  0.0   0:02.24 init                                                                                                                
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.06 migration/0                                                                                                         
    4 root      15  -5     0    0    0 S    0  0.0   0:00.32 ksoftirqd/0                                                                                                         
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1                                                                                                         
    7 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1                                                                                                         
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                          
    9 root      15  -5     0    0    0 S    0  0.0   0:00.08 events/0                                                                                                            
   10 root      15  -5     0    0    0 S    0  0.0   0:00.12 events/1                                                                                                            
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                             
   44 root      15  -5     0    0    0 S    0  0.0   0:00.16 kblockd/0                                                                                                           
   45 root      15  -5     0    0    0 S    0  0.0   0:00.16 kblockd/1                                                                                                           
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                              
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                        
  145 root      15  -5     0    0    0 S    0  0.0   0:00.20 kseriod                                                                                                             
  192 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                             
  193 root      20   0     0    0    0 S    0  0.0   0:00.20 pdflush                                                                                                             
  194 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                             
  237 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                               
  238 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                               
 1336 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksnapd                                                                                                              
 1560 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                       
 1565 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                               
 1705 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                            
 1740 root      15  -5     0    0    0 S    0  0.0   0:00.40 ata/0                                                                                                               
 1742 root      15  -5     0    0    0 S    0  0.0   0:00.50 ata/1            USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   4020   888 ?        Ss   10:10   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   10:10   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   10:10   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   10:10   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   10:10   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   10:10   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   10:10   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   10:10   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   10:10   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   10:10   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   10:10   0:00 [khelper]
root        44  0.0  0.0      0     0 ?        S<   10:10   0:00 [kblockd/0]
root        45  0.0  0.0      0     0 ?        S<   10:10   0:00 [kblockd/1]
root        48  0.0  0.0      0     0 ?        S<   10:10   0:00 [kacpid]
root        49  0.0  0.0      0     0 ?        S<   10:10   0:00 [kacpi_notify]
root       145  0.0  0.0      0     0 ?        S<   10:10   0:00 [kseriod]
root       192  0.0  0.0      0     0 ?        S    10:10   0:00 [pdflush]
root       193  0.0  0.0      0     0 ?        S    10:10   0:00 [pdflush]
root       194  0.0  0.0      0     0 ?        S<   10:10   0:00 [kswapd0]
root       237  0.0  0.0      0     0 ?        S<   10:10   0:00 [aio/0]
root       238  0.0  0.0      0     0 ?        S<   10:10   0:00 [aio/1]
root      1336  0.0  0.0      0     0 ?        S<   10:10   0:00 [ksnapd]
root      1560  0.0  0.0      0     0 ?        S<   10:10   0:00 [ksuspend_usbd]
root      1565  0.0  0.0      0     0 ?        S<   10:10   0:00 [khubd]
root      1705  0.0  0.0      0     0 ?        S<   10:10   0:00 [khpsbpkt]
root      1740  0.0  0.0      0     0 ?        S<   10:10   0:00 [ata/0]
root      1742  0.0  0.0      0     0 ?        S<   10:10   0:00 [ata/1]
root      1743  0.0  0.0      0     0 ?        S<   10:10   0:00 [ata_aux]
root      1917  0.0  0.0      0     0 ?        S<   10:10   0:00 [knodemgrd_0]
root      2445  0.0  0.0      0     0 ?        S<   10:10   0:00 [scsi_eh_0]
root      2446  0.0  0.0      0     0 ?        S<   10:10   0:00 [scsi_eh_1]
root      2447  0.0  0.0      0     0 ?        S<   10:10   0:00 [scsi_eh_2]
root      2458  0.0  0.0      0     0 ?        S<   10:10   0:01 [scsi_eh_3]
root      2459  0.0  0.0      0     0 ?        S<   10:10   0:00 [scsi_eh_4]
root      2613  0.0  0.0      0     0 ?        S<   10:10   0:00 [kcryptd_io]
root      2614  0.1  0.0      0     0 ?        S<   10:10   0:15 [kcryptd]
root      2729  0.0  0.0      0     0 ?        S<   10:10   0:00 [kjournald]
root      2942  0.0  0.0  17196  1304 ?        S<s  10:10   0:00 /sbin/udevd --daemon
root      3369  0.0  0.0      0     0 ?        S<   10:10   0:00 [iwl4965/0]
root      3372  0.0  0.0      0     0 ?        S<   10:10   0:00 [iwl4965/1]
root      3444  0.0  0.0      0     0 ?        S<   10:10   0:00 [kpsmoused]
root      4275  0.0  0.0      0     0 ?        S<   10:10   0:00 [pccardd]
root      4287  0.0  0.0      0     0 ?        S<   10:10   0:00 [iwl4965]
root      4661  0.0  0.0      0     0 ?        S<   10:10   0:00 [kjournald]
root      4947  0.0  0.0   3864   596 tty4     Ss+  10:10   0:00 /sbin/getty 38400 tty4
root      4948  0.0  0.0   3864   596 tty5     Ss+  10:10   0:00 /sbin/getty 38400 tty5
root      4950  0.0  0.0   3864   592 tty2     Ss+  10:10   0:00 /sbin/getty 38400 tty2
root      4952  0.0  0.0   3864   592 tty3     Ss+  10:10   0:00 /sbin/getty 38400 tty3
root      4954  0.0  0.0   3864   592 tty6     Ss+  10:10   0:00 /sbin/getty 38400 tty6
root      5139  0.0  0.0  13208  1876 ?        Ss   10:10   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5173  0.0  0.0      0     0 ?        S<   10:10   0:00 [kondemand/0]
root      5174  0.0  0.0      0     0 ?        S<   10:10   0:00 [kondemand/1]
syslog    5251  0.0  0.0  12296   724 ?        Ss   10:10   0:00 /sbin/syslogd -u syslog
root      5305  0.0  0.0   8132   592 ?        S    10:10   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5307  0.0  0.1   7200  3912 ?        Ss   10:10   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       5329  0.0  0.0  21568  1440 ?        Ss   10:10   0:05 /usr/bin/dbus-daemon --system
root      5345  0.0  0.1 134588  2528 ?        Ssl  10:10   0:01 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      5359  0.0  0.0  28384  1416 ?        Ss   10:10   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      5372  0.0  0.0  35192  1220 ?        Ss   10:10   0:00 /usr/bin/system-tools-backends
avahi     5392  0.0  0.0  29700  1572 ?        Ss   10:10   0:00 avahi-daemon: running [upgradearefailed.local]
avahi     5393  0.0  0.0  29580   504 ?        Ss   10:10   0:00 avahi-daemon: chroot helper
root      5425  0.1  0.1  72440  2532 ?        Ss   10:10   0:11 /usr/sbin/cupsd
root      5458  0.0  0.0   3712   204 ?        S    10:10   0:00 /usr/sbin/thinkpad-keys --no-brightness
root      5538  0.0  0.0   6272   992 ?        Ss   10:10   0:00 /usr/sbin/dhcdbd --system
111       5563  0.0  0.2  40280  4792 ?        Ss   10:10   0:03 /usr/sbin/hald
root      5566  0.0  0.1 106628  2588 ?        Ssl  10:10   0:00 /usr/sbin/console-kit-daemon
root      5567  0.0  0.0  22048  1300 ?        S    10:10   0:00 hald-runner
root      5641  0.0  0.0  24156  1288 ?        S    10:10   0:00 hald-addon-input: Listening on /dev/input/event6 /dev/input/event5 /dev/input/event1 /dev/input/event11 /dev/inp
ut/event2 /dev/input/event3 /dev/input/event4 /dev/input/event9 /dev/input/event12
root      5654  0.0  0.0  24168  1324 ?        S    10:10   0:00 /usr/lib/hal/hald-addon-cpufreq
111       5655  0.0  0.0  16672  1040 ?        S    10:10   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5675  0.0  0.0  24156  1276 ?        S    10:10   0:01 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5696  0.0  0.0  17760  1316 ?        Ss   10:10   0:00 /usr/sbin/hcid -x -s
root      5721  0.0  0.0      0     0 ?        S<   10:10   0:00 [btaddconn]
root      5722  0.0  0.0      0     0 ?        S<   10:10   0:00 [btdelconn]
root      5733  0.0  0.0  17656  1416 ?        S    10:10   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5751  0.0  0.0  17580  1208 ?        S    10:10   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5763  0.0  0.0      0     0 ?        S<   10:10   0:00 [krfcommd]
root      5801  0.0  0.0 116172  1904 ?        Ss   10:10   0:00 /usr/sbin/gdm
root      5804  0.0  0.1 128920  3352 ?        S    10:10   0:00 /usr/sbin/gdm
root      5807  4.7  4.0 959720 82092 tty7     SLs+ 10:10   7:09 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
daemon    5850  0.0  0.0  16428   432 ?        Ss   10:11   0:00 /usr/sbin/atd
root      5864  0.0  0.0  18616   980 ?        Ss   10:11   0:00 /usr/sbin/cron
root      5980  0.0  0.0   3864   596 tty1     Ss+  10:11   0:00 /sbin/getty 38400 tty1
tavisc    6032  0.0  0.2  43772  5880 ?        S    10:11   0:00 /usr/lib/libgconf2-4/gconfd-2 4
tavisc    6034  0.0  0.1  70240  2396 ?        S    10:11   0:00 /usr/bin/gnome-keyring-daemon -d --login
tavisc    6035  0.0  0.4 193580  8988 ?        Ssl  10:11   0:00 x-session-manager
tavisc    6118  0.0  0.3 214932  7960 ?        Ss   10:11   0:00 /usr/bin/seahorse-agent --execute x-session-manager
tavisc    6122  0.0  0.0  21452  1212 ?        Ss   10:11   0:07 dbus-daemon --fork --print-address 20 --print-pid 22 --session
tavisc    6123  0.0  0.7 261304 14968 ?        Sl   10:11   0:02 gnome-settings-daemon
tavisc    6127  1.2  0.3 152440  7168 ?        Sl   10:11   1:55 /usr/bin/pulseaudio --log-target=syslog
tavisc    6130  0.0  0.1  57836  2704 ?        S    10:11   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
tavisc    6139  0.1  0.3 138892  6536 ?        Ss   10:11   0:10 gnome-screensaver
tavisc    6144  0.0  0.0   3944   616 ?        S    10:11   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
tavisc    6145  0.2  1.3 318760 28508 ?        Sl   10:11   0:22 gnome-panel --sm-client-id default1
tavisc    6147  0.1  4.1 465396 84728 ?        S    10:11   0:13 nautilus --no-default-window --sm-client-id default2
tavisc    6154  0.0  0.1  84284  3760 ?        Ssl  10:11   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
tavisc    6180  0.0  0.1  44772  2292 ?        S    10:11   0:00 /usr/lib/gvfs/gvfsd
tavisc    6190  0.0  0.1  62320  2200 ?        Ssl  10:11   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/tavisc/.gvfs
tavisc    6220  2.9  1.7 258844 35908 ?        SL   10:11   4:19 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 core ccp
tavisc    6221  0.0  0.3 123140  6648 ?        S    10:11   0:00 bluetooth-applet --singleton
tavisc    6224  0.0  0.8 208564 16608 ?        S    10:11   0:00 update-notifier
tavisc    6230  0.0  0.6 306084 12404 ?        Sl   10:11   0:00 /usr/lib/evolution/2.22/evolution-alarm-notify
tavisc    6231  0.0  0.3 121728  6392 ?        S    10:11   0:00 tracker-applet
tavisc    6234  0.0  0.5 142388 11020 ?        SNl  10:11   0:00 trackerd
tavisc    6237  0.1  0.8 193908 16440 ?        S    10:11   0:14 python /usr/share/system-config-printer/applet.py
tavisc    6238  0.0  0.9 205068 18876 ?        S    10:11   0:04 nm-applet --sm-disable
tavisc    6239  0.0  0.2 187404  5352 ?        Ss   10:11   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
tavisc    6240  0.1  0.5 382704 10496 ?        S    10:11   0:17 gnome-cups-icon --sm-client-id default3
tavisc    6241  0.0  0.6 218768 12532 ?        Ss   10:11   0:01 gnome-power-manager
tavisc    6330  0.0  0.1  44772  2376 ?        S    10:11   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
tavisc    6333  0.0  0.3 237524  8056 ?        Sl   10:11   0:00 /usr/lib/evolution/evolution-data-server-2.22 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.
2 --oaf-ior-fd=23
tavisc    6344  0.0  0.6 195096 12680 ?        S    10:11   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=26
tavisc    6350  0.0  0.1  63552  2936 ?        S    10:11   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/2
tavisc    6357  0.0  0.5 301344 11996 ?        Sl   10:12   0:00 /usr/lib/evolution/2.22/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_
CalFactory:1.2 --oaf-ior-fd=24
tavisc    6389  0.0  0.0   3944   552 ?        Ss   10:12   0:00 /bin/sh -c /usr/bin/compiz-decorator
tavisc    6390  0.0  0.0   3944   588 ?        S    10:12   0:00 /bin/sh /usr/bin/compiz-decorator
tavisc    6392  0.0  0.6 144348 13480 ?        S    10:12   0:04 /usr/bin/gtk-window-decorator
tavisc    6399  0.0  0.8 241876 18144 ?        Sl   10:12   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=25
tavisc    6402  0.0  0.7 210764 15976 ?        S    10:12   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Fa
ctory --oaf-ior-fd=35
root      6768  0.0  0.1  17348  2900 ?        S    10:13   0:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global
tavisc    6773 15.3 24.9 980664 511232 ?       Sl   10:13  22:37 /usr/lib/firefox-3.0.1/firefox
tavisc    6794  0.0  1.3 271280 28352 ?        Sl   10:13   0:06 gnome-terminal
tavisc    6805  0.0  0.0  23572   972 ?        S    10:13   0:00 gnome-pty-helper
dhcp      6888  0.0  0.0  15112  1480 ?        S    10:13   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.wlan0.pid -q -e dhc_dbus=31 -d 
wlan0
ntp       7037  0.0  0.0  25420  1408 ?        Ss   10:14   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 112:124 -g
tavisc    7098  0.5  2.3 664008 48980 ?        Sl   10:14   0:46 pidgin
tavisc    7236  0.8  2.4 545804 49576 ?        Sl   10:15   1:13 /usr/lib/totem/gstreamer/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux x86_64; e
n-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1 --mimetype video/x-ms-wmv
tavisc    7269  3.2  2.4 104872 50692 ?        Sl   10:15   4:40 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-nonfree/libflashplayer.so --conne
ction /org/wrapper/NSPlugins/libflashplayer.so/6773-2
tavisc    8966  0.0  0.1  20824  3744 pts/1    Ss   10:31   0:00 bash
tavisc    8986  0.0  0.1  44380  2808 pts/1    S+   10:31   0:00 ssh to.ast
tavisc   21247  0.0  0.1  20824  3772 pts/0    Ss   12:28   0:00 bash
tavisc   22429  0.0  0.0  15064  1088 pts/0    R+   12:40   0:00 ps aux
tavisc   22430  0.0  0.0   9444   952 pts/0    S+   12:40   0:00 more
                                                                                                   



Thanks for your time.

---

### Post by Mister.Vash on 2008-08-11
Did you read over the Ubuntu Security post?
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)
Especially the section on rootkits and log reading and maybe the bit on the antivirus as a start

If those programs don't turn up anything, I would say check and see if it still occurs after a reboot?  Start up the machine then get a list of running process.  Then just open up a text editor like gedit, and try the copy and paste.  See if it occurs right away - if it doesn't wait a little bit and try again.  Either way, get an output of the processes running at that time and save them.

If the text program didn't show the behavior, try starting up firefox and see if it does it - again get an output of the running process, oh and make sure you can identify the log as you save them so you tell which one was first, which one was with the editor, etc

Just some ideas as where to start, that could help find what is going on

---

### Post by lavinog on 2008-08-11
I have been getting alot of calls from windows users about "viruses" lately, this site is pretty much what they described.

maybe try searching for the text that is being pasted:
```
grep -r '31863829103' ~
```
if it doesn't find it change ~ to /
be prepared to wait awhile.

note the number is part of the url link that you said it was pasting.

---

### Post by hyper_ch on 2008-08-12
> **TC10284 said:**
> Since late last week I have been noticing that anything I copy/paste to the "clipboard" in Ubuntu doesn't stick.

(1) when posting output or config files use [noparse]```

```[/noparse] brackets around it

(2) that's how linux behaves... if you copy something to the clipboard and then close the application you copied from then it will also vanish from the clipboard. That's normal linux behaviour.

However there are tools that maintaing things in the clipboard for longer periods than just as long as the original program is running.

---

### Post by jedimonkey27 on 2008-08-13
Wow, I found this thread through a google search. While I have used Ubuntu in the past I do not currently have it installed. Right now I am in Windows Vista and the same exact thing happened to me. My clipboard is stuck to http: //xp-vista-update net/?id=31863829103 How the hell could this happen to me on Vista and to someone using Ubuntu as well? The only common factor I can think of is that I am using Firefox 3.

---

### Post by lavinog on 2008-08-13
> **jedimonkey27 said:**
> Wow, I found this thread through a google search. While I have used Ubuntu in the past I do not currently have it installed. Right now I am in Windows Vista and the same exact thing happened to me. My clipboard is stuck to [http://xp-vista-update.net/?id=31863829103](http://xp-vista-update.net/?id=31863829103) How the hell could this happen to me on Vista and to someone using Ubuntu as well? The only common factor I can think of is that I am using Firefox 3.

wow, you are confirming my suspicions then. Maybe there is a security flaw in firefox. I tried going to that site, and after a bunch of bogus popups saying my windows explorer (i am using ubuntu) is infected...it redirects me to another sight where i get a warning about the site is blocked for malicious reasons.

---

### Post by lavinog on 2008-08-13
Wow a google search for that site shows all sorts of forum posts with bogus stories trying to get people to go to that site.

---

### Post by jedimonkey27 on 2008-08-13
Interesting, a reboot seems to have gotten rid of the problem for me. I will see if it comes back tomorrow. AVG didn't find anything so now I am scanning with a few spyware tools. I hope that the only thing that they got access to was the clipboard. I have not been able to find anyone else through Google searching who fixed this problem. I checked my Mac which also runs FF3 and it is not having that problem.

---

### Post by lavinog on 2008-08-13
I know a guy that followed a link from a email from microsoft instructing him to update IE...It sounds like this is the exact site because he said when he followed it, it told him that his computer was infected and asked if he wanted to install the program...he said he tried to close it but he some how missed the deny button and accepted it...now he gets a bsod everytime he tries to do anything, and AVG disappeared.

My brother is saying something similar too. I think his issue came from his roomate's computer, but I can't get any info from him because he can't get to his computer for a while.

---

### Post by lavinog on 2008-08-13
[http://www.dslreports.com/forum/r20925461-Malvertisement-on-MSNBCcom-using-clipboard-copypaste]("http://www.dslreports.com/forum/r20925461-Malvertisement-on-MSNBCcom-using-clipboard-copypaste")
The problem seems to be linked to advertisements running on msn and msnbc

---

### Post by todb on 2008-08-14
As of mid-2007, it was possible to write to the clipboard via Flash. This is as-designed behavior (at least, it was then). See this tutorial:

[http://ajaxian.com/archives/auto-copy-to-clipboard](http://ajaxian.com/archives/auto-copy-to-clipboard)

I assume this, or something quite like it, still works. I haven't tested since I'm not a Flash guy. (a test would be appreciated if you are!)

Clipboard access is old news for IE, but until this morning, I thought the only way to write to the clipboard via Firefox was through some a priori rigamarole involving Java and setting signed.applets.codebase_principal_support in about:config (see this example: [http://kb.sumtotalsystems.com/kbdisplay.asp?id=Q111781680000014](http://kb.sumtotalsystems.com/kbdisplay.asp?id=Q111781680000014) ).

If Flash can do this silently, we should wait a year for Adobe to fix it. Or use FlashBlock routinely.

---

### Post by 1silver11 on 2008-08-16
I just found this page by searching google with [http://xp-vista-update.net/?id=31863829103](http://xp-vista-update.net/?id=31863829103) which is what is stuck on my ckipboard. I'm using Windows XP and Opera. No matter what I copy or cut that link is stuck on my paste.

---

### Post by lavinog on 2008-08-16
> **1silver11 said:**
> I just found this page by searching google with [http://xp-vista-update.net/?id=31863829103](http://xp-vista-update.net/?id=31863829103) which is what is stuck on my ckipboard. I'm using Windows XP and Opera. No matter what I copy or cut that link is stuck on my paste.

close opera and see if it stops

---

### Post by cpetercarter on 2008-08-16
> As of mid-2007, it was possible to write to the clipboard via Flash. This is as-designed behavior (at least, it was then). See this tutorial:

[http://ajaxian.com/archives/auto-copy-to-clipboard](http://ajaxian.com/archives/auto-copy-to-clipboard)

I assume this, or something quite like it, still works. I haven't tested since I'm not a Flash guy. (a test would be appreciated if you are!)

It is certainly possible to use a tiny Flash object to write to the clipboard in IE and Firefox 3 (and probably other browsers too). I have used the technique - it is very useful! - in a programme which I have written.

---

### Post by TC10284 on 2008-09-15
It would appear that this problem came up again. I booted my Ubuntu Hardy Heron laptop today and noticed the paste problem was back, but with a different URL.
don't click me - [http://windowsxp-privacy.net/?id=31904566544](http://windowsxp-privacy.net/?id=31904566544) - don't click me

I assure you that this reply and post isn't bogus trying to get you to go to the site. I just want to get this fixed. =\

It's seriously annoying.

---

### Post by todb on 2008-09-15
> **TC10284 said:**
> It would appear that this problem came up again.
...
It's seriously annoying.

I'm sure it will persist until Adobe figures out some method to control Flash's clipboard access (maybe only write to it once per X events or something).

This seems like case closed -- doesn't seem to be a lot that Ubuntu can do about it.

Update: Of course, for Firefox, you can use Flashblock and/or Noscript. Google them.

---

### Post by TC10284 on 2008-09-15
Well I guess my question is, is this some type of script/addon installed on my system or just mal-code on a site that is using Flash's clipboard access?

Also, as soon as I installed Flashblock, that killed the constant pasting of the URL to the clipboard. Awesome. Thanks!

---

### Post by todb on 2008-09-19
> **TC10284 said:**
> 
Also, as soon as I installed Flashblock, that killed the constant pasting of the URL to the clipboard. Awesome. Thanks!

Looks like Adobe will be fixing it in the next verison

[http://blogs.zdnet.com/security/?p=1948](http://blogs.zdnet.com/security/?p=1948)

Which means it'll be fixed in Ubuntu in a few years, undoubtedly.

-tod

---

