---
title: "Procesos en ejecución"
date: 2009-09-25
forum: Software
---

### Post by emiliano_raso on 2009-09-25
Hola muchachos. Este es un screenshot de los procesos activos apenas termino de bootear GNU/Linux.

1) Cuales se pueden sacar? Cuales aplicaciones se pueden reemplazar por otros que consuman menos recursos?
2) Si tengo desactivado el screensaver, porque de todas formas aparece cada vez que booteo?

---

### Post by aromo on 2009-09-25
El grafico no es claro, por favor envia la salida de este comando:
ps -elf

---

### Post by juancarlospaco on 2009-09-25
Como poder podes si no afecta en nada matarlos, 
pero cada uno de esos que mates te saca una funcionalidad,
matalos casi todos y terminas con una sesion de X pelada, no muy usable el desktop asi.

Que queres hacer...?, necesitas correr algo pesado?,
proba como hago yo... 
que tuneo el lanzador de esa aplicacion poniendole que antes de lanzarse mate todo:
*killall blah ; killall blahblah ; /usr/bin/aplicacion-re-pesada*

:)

---

### Post by emiliano_raso on 2009-09-26
Perdón que me colgué. Esta es la salida de ps -elf
Es simplemente porque quiero reducir la cantidad de procesos al minimo. Sacar lo que no es necesario.
Por ejemplo, el screen-saver está desactivado, pero sigue apareciendo.

Gracias por responder muchachos...

```
debian:/home/emiliano# ps -elf
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
4 S root         1     0  0  80   0 -   525 -      17:24 ?        00:00:01 init [2]  
5 S root         2     0  0  75  -5 -     0 -      17:24 ?        00:00:00 [kthreadd]
1 S root         3     2  0 -40   - -     0 -      17:24 ?        00:00:00 [migration/0]
1 S root         4     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [ksoftirqd/0]
5 S root         5     2  0 -40   - -     0 -      17:24 ?        00:00:00 [watchdog/0]
1 S root         6     2  0 -40   - -     0 -      17:24 ?        00:00:00 [migration/1]
1 S root         7     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [ksoftirqd/1]
5 S root         8     2  0 -40   - -     0 -      17:24 ?        00:00:00 [watchdog/1]
1 S root         9     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [events/0]
1 S root        10     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [events/1]
1 S root        11     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [khelper]
1 S root        44     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kblockd/0]
1 S root        45     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kblockd/1]
1 S root        47     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kacpid]
1 S root        48     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kacpi_notify]
1 S root       133     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kseriod]
1 S root       174     2  0  80   0 -     0 -      17:24 ?        00:00:00 [pdflush]
1 S root       175     2  0  80   0 -     0 -      17:24 ?        00:00:00 [pdflush]
1 S root       176     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kswapd0]
1 S root       177     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [aio/0]
1 S root       178     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [aio/1]
1 S root       687     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [ksuspend_usbd]
1 S root       688     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [khubd]
1 S root       747     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [ata/0]
1 S root       749     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [ata/1]
1 S root       751     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kmmcd]
1 S root       752     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [ata_aux]
1 S root       863     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [scsi_eh_0]
1 S root       864     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [scsi_eh_1]
1 S root       865     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [scsi_eh_2]
1 S root       866     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [scsi_eh_3]
1 D root       995     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kjournald]
5 S root      1071     1  0  76  -4 -   707 -      17:24 ?        00:00:00 udevd --daemon
1 S root      1691     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [kpsmoused]
1 S root      1707     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [iwl3945/0]
1 S root      1708     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [iwl3945/1]
1 S root      1713     2  0  75  -5 -     0 -      17:24 ?        00:00:00 [iwl3945]
1 S root      2047     1  0  80   0 -   969 -      17:24 ?        00:00:00 /sbin/mount.ntfs-3g /dev/sda2 /media/Windows -o rw,locale=es_ES.UTF8
5 S daemon    2183     1  0  80   0 -   473 -      17:24 ?        00:00:00 /sbin/portmap
5 S statd     2195     1  0  80   0 -   489 -      17:24 ?        00:00:00 /sbin/rpc.statd
5 S root      2405     1  0  80   0 -  7107 -      17:25 ?        00:00:00 /usr/sbin/rsyslogd -c3
1 S root      2416     1  0  80   0 -   441 -      17:25 ?        00:00:00 /usr/sbin/acpid
5 S 103       2427     1  0  80   0 -   687 -      17:25 ?        00:00:00 /usr/bin/dbus-daemon --system
5 S bind      2443     1  0  80   0 - 13864 -      17:25 ?        00:00:00 /usr/sbin/named -u bind
5 S root      2494     1  0  80   0 - 11880 -      17:25 ?        00:00:00 /usr/sbin/lwresd
5 S root      2551     1  0  80   0 -  1586 -      17:25 ?        00:00:00 /usr/sbin/cupsd
5 S 101       2818     1  0  80   0 -  1569 -      17:25 ?        00:00:00 /usr/sbin/exim4 -bd -q30m
5 S root      2840     2  0  75  -5 -     0 -      17:25 ?        00:00:00 [rpciod/0]
1 S root      2842     2  0  75  -5 -     0 -      17:25 ?        00:00:00 [rpciod/1]
1 S root      2866     2  0  75  -5 -     0 -      17:25 ?        00:00:00 [lockd]
1 S root      2867     2  0  75  -5 -     0 -      17:25 ?        00:00:00 [nfsd4]
1 S root      2868     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2869     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2870     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2871     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2872     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2873     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2874     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2875     2  0  80   0 -     0 -      17:25 ?        00:00:00 [nfsd]
1 S root      2879     1  0  80   0 -   516 -      17:25 ?        00:00:00 /usr/sbin/rpc.mountd
5 S root      2890     1  0  80   0 -   488 -      17:25 ?        00:00:00 /usr/sbin/inetd
5 S root      2901     1  0  80   0 -  1762 -      17:25 ?        00:00:00 /usr/sbin/nmbd -D
5 S root      2903     1  0  80   0 -  3130 -      17:25 ?        00:00:00 /usr/sbin/smbd -D
1 S root      2914     1  0  80   0 -  2280 -      17:25 ?        00:00:00 /usr/sbin/winbindd
1 S root      2922  2914  0  80   0 -  2280 -      17:25 ?        00:00:00 /usr/sbin/winbindd
1 S root      2923     1  0  80   0 -   513 -      17:25 ?        00:00:00 /usr/sbin/dhcdbd --system
1 S root      2931  2914  0  80   0 -  2301 -      17:25 ?        00:00:00 /usr/sbin/winbindd
1 S root      2935  2914  0  80   0 -  2280 -      17:25 ?        00:00:00 /usr/sbin/winbindd
1 S root      2936  2903  0  80   0 -  3130 -      17:25 ?        00:00:00 /usr/sbin/smbd -D
5 S 106       2937     1  0  80   0 -  1472 -      17:25 ?        00:00:00 /usr/sbin/hald
0 S root      2938  2937  0  80   0 -   831 -      17:25 ?        00:00:00 hald-runner
0 S root      2956  2938  0  80   0 -   847 -      17:25 ?        00:00:00 hald-addon-input: Listening on /dev/input/event2 /dev/input/event0 /dev/input/even
4 S 106       2961  2938  0  80   0 -   568 -      17:25 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
0 S root      2966  2938  0  80   0 -   847 -      17:25 ?        00:00:00 hald-addon-storage: polling /dev/hda (every 2 sec)
5 S root      2978     1  0  80   0 -  7342 -      17:25 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
1 S root      2986     1  0  80   0 -   877 -      17:25 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManag
1 S root      3023     1  0  80   0 -  3567 -      17:25 ?        00:00:00 /usr/sbin/gdm
5 S root      3030  3023  0  80   0 -  3694 -      17:25 ?        00:00:00 /usr/sbin/gdm
4 S root      3033  3030  1  80   0 -  6231 -      17:25 tty7     00:00:08 /usr/X11R6/bin/X :0 -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
1 S root      3036     1  0  80   0 -   963 -      17:25 ?        00:00:00 /usr/bin/system-tools-backends
1 S daemon    3056     1  0  80   0 -   512 -      17:25 ?        00:00:00 /usr/sbin/atd
1 S root      3076     1  0  80   0 -   864 -      17:25 ?        00:00:00 /usr/sbin/cron
1 S root      3095     1  0  80   0 -  5291 -      17:25 ?        00:00:00 /usr/sbin/apache2 -k start
0 S root      3112     1  0  80   0 -   441 -      17:25 tty1     00:00:00 /sbin/getty 38400 tty1
0 S root      3113     1  0  80   0 -   441 -      17:25 tty2     00:00:00 /sbin/getty 38400 tty2
0 S root      3114     1  0  80   0 -   441 -      17:25 tty3     00:00:00 /sbin/getty 38400 tty3
0 S root      3115     1  0  80   0 -   441 -      17:25 tty4     00:00:00 /sbin/getty 38400 tty4
0 S root      3116     1  0  80   0 -   441 -      17:25 tty5     00:00:00 /sbin/getty 38400 tty5
0 S root      3117     1  0  80   0 -   441 -      17:25 tty6     00:00:00 /sbin/getty 38400 tty6
5 S www-data  3128  3095  0  80   0 -  5291 -      17:25 ?        00:00:00 /usr/sbin/apache2 -k start
5 S www-data  3129  3095  0  80   0 -  5291 -      17:25 ?        00:00:00 /usr/sbin/apache2 -k start
5 S www-data  3130  3095  0  80   0 -  5291 -      17:25 ?        00:00:00 /usr/sbin/apache2 -k start
5 S www-data  3131  3095  0  80   0 -  5291 -      17:25 ?        00:00:00 /usr/sbin/apache2 -k start
5 S www-data  3132  3095  0  80   0 -  5291 -      17:25 ?        00:00:00 /usr/sbin/apache2 -k start
1 S root      3200     1  0  78  -2 -   545 -      17:26 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases e
0 S emiliano  3401     1  0  80   0 -  1770 -      17:31 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 11
1 S emiliano  3403     1  0  80   0 -  3704 -      17:31 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d --login
4 S emiliano  3404  3030  0  80   0 -  7078 -      17:31 ?        00:00:00 x-session-manager
1 S emiliano  3452     1  0  80   0 -   775 -      17:31 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/seahorse-agent --execute x-sessi
1 S emiliano  3453     1  0  80   0 -   655 -      17:31 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
1 S emiliano  3459  3404  0  80   0 -  6025 -      17:31 ?        00:00:00 /usr/bin/seahorse-agent --execute x-session-manager
0 S emiliano  3462  3404  0  80   0 - 13532 -      17:31 ?        00:00:00 gnome-settings-daemon
1 S emiliano  3477     1  0  80   0 -  3903 -      17:31 ?        00:00:00 gnome-screensaver
0 S emiliano  3478  3404  0  80   0 -  5265 -      17:31 ?        00:00:00 /usr/bin/metacity --sm-client-id=default0
0 S emiliano  3479  3404  0  80   0 - 10679 -      17:31 ?        00:00:02 gnome-panel --sm-client-id default1
0 S emiliano  3482  3404  0  80   0 - 18785 -      17:31 ?        00:00:00 nautilus --no-default-window --sm-client-id default2
0 S emiliano  3488     1  0  80   0 -  8315 -      17:31 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=
0 S emiliano  3494     1  0  80   0 -  2557 -      17:31 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
0 S emiliano  3503  3404  0  80   0 -  6656 -      17:31 ?        00:00:00 nm-applet --sm-disable
1 S emiliano  3504     1  0  80   0 -  5017 -      17:31 ?        00:00:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
1 S emiliano  3511     1  0  80   0 -  7316 -      17:31 ?        00:00:00 gnome-power-manager
0 S emiliano  3556     1  0  80   0 -  9828 -      17:31 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_F
0 S emiliano  3563     1  0  80   0 -   720 -      17:31 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapping-daemon
4 S root      3577     1  0  80   0 -  1059 -      17:31 ?        00:00:00 /sbin/wpa_supplicant -g /var/run/wpa_supplicant-global
4 S root      3584  2923  0  80   0 -   545 -      17:31 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.wlan0.leases -pf /var/run/dhclient.w
0 S emiliano  3659     1  0  80   0 -  6727 -      17:31 ?        00:00:00 /usr/lib/notification-daemon/notification-daemon
0 S root      3734     1  0  80   0 -  6000 -      17:32 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=
0 S emiliano  3857     1  0  80   0 -  3652 -      17:35 ?        00:00:00 gksu -D Terminal -- env -u ORBIT_SOCKETDIR /usr/bin/x-terminal-emulator
4 S root      3862  3857  0  80   0 -   953 -      17:35 pts/0    00:00:00 /bin/su root -c /usr/lib/libgksu/gksu-run-helper "env '-u' 'ORBIT_SOCKETDIR' '/usr
0 S root      3864  3862  0  80   0 -   659 -      17:35 pts/0    00:00:00 /usr/lib/libgksu/gksu-run-helper env '-u' 'ORBIT_SOCKETDIR' '/usr/bin/x-terminal-e
0 R root      3871  3864  2  80   0 -  9324 -      17:35 pts/0    00:00:00 gnome-terminal
0 S root      3873     1  3  80   0 -  1740 -      17:35 pts/0    00:00:00 /usr/lib/libgconf2-4/gconfd-2 13
4 S root      3879  3871  0  80   0 -   720 -      17:35 pts/0    00:00:00 gnome-pty-helper
0 S root      3880  3871  0  80   0 -  1052 -      17:35 pts/1    00:00:00 bash
4 R root      3882  3880  0  80   0 -   929 -      17:35 pts/1    00:00:00 ps -elf

```

---

