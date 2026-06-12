---
title: "Nautilus: consumo excesivo"
date: 2009-05-29
forum: Software
---

### Post by josecuervo86 on 2009-05-29
Hola a todos! Tengo la siguiente consulta: cuanto es mas o menos el promedio de consumo de nautilus? Porque a mi me esta consumiendo promedio entre 500 y 900 Mb de Ram :-?

Me gustaria ademas que me dieran alguna opinión de como solucionarlo o que me indiquen posibles causas por la que puede estar consumiendo tanto

Dejo imagen de la situación

---

### Post by pablo.s on 2009-05-29
Cuanto marca Firefox?
Parecen ser tres cifras
tambien!

---

### Post by josecuervo86 on 2009-05-29
si, 335 Mb de Ram esta marcando ahora!! tambien es raro? Yo cuando decian que consumia ram pensaba "debe ser normal" pero parece que no.

Para mi que el sistema se esta aprovechando de que me sobra y se hace la panzada

---

### Post by pablo.s on 2009-05-29
Probaste cuanto consume
desde un Live CD?
Medí los dos y es probable
que lleguen a 40/60 MB
cada uno (o menos).

---

### Post by Mauro22 on 2009-05-29
> **josecuervo86 said:**
> si, 335 Mb de Ram esta marcando ahora!! tambien es raro? Yo cuando decian que consumia ram pensaba "debe ser normal" pero parece que no.

Para mi que el sistema se esta aprovechando de que me sobra y se hace la panzada

Nautilus no sé cuanto me marcará.


Firefox 3 en Openbox me da un consumo 20MB, la mitad que Opera.

---

### Post by pablo.s on 2009-05-29
[ATTACH]115594[/ATTACH]

A mi me consume esto.
La versión de Firefox es
3.6a1pre. (Minefield)

---

### Post by josecuervo86 on 2009-05-29
me estan asesinando la Ram!! Ahora pruebo desde el live, pero definitivamente es anormal el consumo.

---

### Post by Mauro22 on 2009-05-29
Mas alla del consumo... El rendimiento cayó?? Por ahi son solo los numeros...

---

### Post by josecuervo86 on 2009-05-29
No, el rendimiento sigue igual, pero me llama mucho la atención la cantidad de recursos que esta consumiendo.

---

### Post by pablo.s on 2009-05-29
Puede deberse a:

-Extensiones de Firefox
-Scripts en Nautilus

?

---

### Post by josecuervo86 on 2009-05-29
Nada de scripts, extensiones de firefox tengo muchas, pero casi todas utiles. Cuando tenga un tiempito me fijo con el livecd, pero es bastante extraño

---

### Post by dirty fingers on 2009-05-29
yo lo tengo rondando siempre los 20MB. estas mas que mal.

---

### Post by josecuervo86 on 2009-05-29
Y yo que me pensaba que estaba alto pero que debia ser normal!!! Estoy para atras muchachos. Ya estoy probando el livecd

---

### Post by josecuervo86 on 2009-05-29
Ya probe el livecd, adivinen cuanto me dio...... 11,8 mb de Ram.

Ahora si que no se para donde agarrar. Alguno tiene una idea?

---

### Post by Hei Ku on 2009-05-29
sacale todos los scripts y extensiones y probá ahí cuánto te consume. Si sigue en lo mismo, estas al horno. Si no, andá agregando de a uno hasta encontrar cuál es el culpable.

---

### Post by josecuervo86 on 2009-05-29
> **Hei Ku said:**
> sacale todos los scripts y extensiones y probá ahí cuánto te consume. Si sigue en lo mismo, estas al horno. Si no, andá agregando de a uno hasta encontrar cuál es el culpable.

Bueno, le saque todos los plugins a firefox para ver si alguno interfería con nautilus y el resultado fue que firefox bajo a 40 Mb pero nautilus sigue igual.... y scripts no tengo, solo los programas que ejecuto normalmente al inicio.

Aca va imagen

Pd: como veran, nautilus se tomo la libertad de robarme 100 Mb mas jejeje

---

### Post by anarko on 2009-05-29
Hace una cosa, habri una consola y pone "ps f -A" y fijate que se desprende del nautilus es muy raro que se chupe 600Mb.

A mi como al la mayoria me ronda los 20Mb.
El ff varia depende de las paginas el contenido de las mimas, los pluguins, pero yo lo he llegado a ver comiendo 1Gb de ram.

---

### Post by josecuervo86 on 2009-05-29
> **anarko said:**
> Hace una cosa, habri una consola y pone "ps f -A" y fijate que se desprende del nautilus es muy raro que se chupe 600Mb.

A mi como al la mayoria me ronda los 20Mb.
El ff varia depende de las paginas el contenido de las mimas, los pluguins, pero yo lo he llegado a ver comiendo 1Gb de ram.

Aca va el resultado:

```
josecuervo86@josecuervo86-desktop:~$ ps f -A
  PID TTY      STAT   TIME COMMAND
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00  \_ [migration/0]
    4 ?        S<     0:00  \_ [ksoftirqd/0]
    5 ?        S<     0:00  \_ [watchdog/0]
    6 ?        S<     0:00  \_ [migration/1]
    7 ?        S<     0:00  \_ [ksoftirqd/1]
    8 ?        S<     0:00  \_ [watchdog/1]
    9 ?        S<     0:00  \_ [cpuset]
   10 ?        S<     0:00  \_ [events/0]
   11 ?        S<     0:00  \_ [events/1]
   12 ?        S<     0:00  \_ [work_on_cpu/0]
   13 ?        S<     0:00  \_ [work_on_cpu/1]
   14 ?        S<     0:00  \_ [khelper]
   15 ?        S<     0:00  \_ [kintegrityd/0]
   16 ?        S<     0:00  \_ [kintegrityd/1]
   17 ?        S<     0:00  \_ [kblockd/0]
   18 ?        S<     0:00  \_ [kblockd/1]
   19 ?        S<     0:00  \_ [kacpid]
   20 ?        S<     0:00  \_ [kacpi_notify]
   21 ?        S<     0:00  \_ [cqueue]
   22 ?        S<     0:00  \_ [ata/0]
   23 ?        S<     0:00  \_ [ata/1]
   24 ?        S<     0:00  \_ [ata_aux]
   25 ?        S<     0:00  \_ [ksuspend_usbd]
   26 ?        S<     0:00  \_ [khubd]
   27 ?        S<     0:00  \_ [kseriod]
   28 ?        S<     0:00  \_ [kmmcd]
   29 ?        S<     0:00  \_ [btaddconn]
   30 ?        S<     0:00  \_ [btdelconn]
   31 ?        S      0:00  \_ [pdflush]
   32 ?        S      0:00  \_ [pdflush]
   33 ?        S<     0:00  \_ [kswapd0]
   34 ?        S<     0:00  \_ [aio/0]
   35 ?        S<     0:00  \_ [aio/1]
   36 ?        S<     0:00  \_ [ecryptfs-kthrea]
   39 ?        S<     0:00  \_ [scsi_eh_0]
   40 ?        S<     0:00  \_ [scsi_eh_1]
   41 ?        S<     0:00  \_ [scsi_eh_2]
   42 ?        S<     0:00  \_ [scsi_eh_3]
   43 ?        S<     0:00  \_ [kstriped]
   44 ?        S<     0:00  \_ [kmpathd/0]
   45 ?        S<     0:00  \_ [kmpathd/1]
   46 ?        S<     0:00  \_ [kmpath_handlerd]
   47 ?        S<     0:00  \_ [ksnapd]
   48 ?        S<     0:00  \_ [kondemand/0]
   49 ?        S<     0:00  \_ [kondemand/1]
   50 ?        S<     0:00  \_ [krfcommd]
  678 ?        S<     0:00  \_ [scsi_eh_4]
  690 ?        S<     0:00  \_ [usb-storage]
  727 ?        S<     0:00  \_ [kjournald]
 1532 ?        S<     0:00  \_ [kpsmoused]
    1 ?        Ss     0:00 /sbin/init
  848 ?        S<s    0:00 /sbin/udevd --daemon
 2239 ?        Ss     0:00 /usr/sbin/pppd call dsl-provider
 2510 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 2511 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 2517 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 2518 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 2519 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 2585 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 2628 ?        Ss     0:00 /sbin/syslogd -u syslog
 2651 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 2653 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 2676 ?        Ss     0:00 /bin/dbus-daemon --system
 2736 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 4154 ?        Sl     0:02  \_ /usr/sbin/mysqld --basedir=/usr --datadir=/var/li
 4156 ?        S      0:00  \_ logger -p daemon.err -t mysqld_safe -i -t mysqld
 2970 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 3042 ?        Ss     0:00 /usr/bin/freshclam -d --quiet
 3594 ?        Ss     0:00 /usr/sbin/hald
 3595 ?        S      0:00  \_ hald-runner
 3624 ?        S      0:00      \_ hald-addon-input: Listening on /dev/input/eve
 3677 ?        S      0:00      \_ hald-addon-storage: polling /dev/sdc (every 2
 3678 ?        S      0:00      \_ hald-addon-storage: polling /dev/sdd (every 2
 3679 ?        S      0:00      \_ hald-addon-storage: polling /dev/sde (every 2
 3680 ?        S      0:00      \_ hald-addon-storage: polling /dev/sr0 (every 2
 3681 ?        S      0:00      \_ hald-addon-storage: polling /dev/sdb (every 2
 3682 ?        S      0:00      \_ /usr/lib/hal/hald-addon-cpufreq
 3683 ?        S      0:00      \_ hald-addon-acpi: listening on acpid socket /v
 3701 ?        Ss     0:00 /usr/sbin/bluetoothd
 3743 ?        Ss     0:00 /usr/sbin/gdm
 3746 ?        S      0:00  \_ /usr/sbin/gdm
 3749 tty7     Ss+    3:19      \_ /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/l
 4192 ?        Ssl    0:00      \_ /usr/bin/gnome-session
 4260 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch -
 4289 ?        Ss     0:00          \_ /usr/bin/seahorse-agent --execute /usr/bi
 4313 ?        S      0:00          \_ /bin/sh /usr/bin/compiz
 4366 ?        S      0:56          |   \_ /usr/bin/compiz.real --ignore-desktop
 4456 ?        Ss     0:00          |       \_ /bin/sh -c /usr/bin/compiz-decora
 4457 ?        S      0:00          |           \_ /bin/sh /usr/bin/compiz-decor
 4459 ?        S      0:01          |               \_ /usr/bin/gtk-window-decor
 4367 ?        S      0:05          \_ gnome-panel
 4372 ?        S      6:55          \_ nautilus --no-desktop --browser
 4383 ?        S      0:00          \_ update-notifier --startup-delay=60
 4387 ?        S      0:00          \_ /bin/sh /usr/bin/gnome-do --quiet
 4401 ?        Sl     0:02          |   \_ /usr/bin/cli /usr/lib/gnome-do/Do.exe
 4394 ?        S      0:00          \_ nm-applet --sm-disable
 3777 ?        Ss     0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 3796 ?        Ss     0:00 avahi-daemon: running [josecuervo86-desktop.local]
 3797 ?        Ss     0:00  \_ avahi-daemon: chroot helper
 3816 ?        S      0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.lo
 3818 ?        S      0:00 /usr/sbin/nm-system-settings --config /etc/NetworkMan
 3825 ?        Ss     0:00 /usr/sbin/cupsd
 3853 ?        Ss     0:00 /usr/bin/system-tools-backends
 3926 ?        Ss     0:00 /usr/sbin/atd
 3955 ?        Ss     0:00 /usr/sbin/cron
 4000 ?        Ss     0:00 /usr/sbin/apache2 -k start
 4002 ?        S      0:00  \_ /usr/sbin/apache2 -k start
 4004 ?        S      0:00  \_ /usr/sbin/apache2 -k start
 4006 ?        S      0:00  \_ /usr/sbin/apache2 -k start
 4008 ?        S      0:00  \_ /usr/sbin/apache2 -k start
 4010 ?        S      0:00  \_ /usr/sbin/apache2 -k start
 5763 ?        S      0:00  \_ /usr/sbin/apache2 -k start
 6356 ?        S      0:00  \_ /usr/sbin/apache2 -k start
 4132 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4180 ?        S      0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 4263 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pul
 4264 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 6 --print-addres
 4269 ?        Ssl    2:00 /usr/bin/pulseaudio --start
 4270 ?        S      0:00  \_ /usr/lib/pulseaudio/pulse/gconf-helper
 4272 ?        S      0:01 /usr/lib/libgconf2-4/gconfd-2
 4292 ?        S      0:00 /usr/lib/gvfs/gvfsd
 4298 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/josecuervo86/.g
 4307 ?        Ssl    0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 4375 ?        S      0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
 4377 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 4404 ?        S      0:00 /usr/lib/notify-osd/notify-osd
 4406 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 4412 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvf
 4418 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 4420 ?        S      0:00 /usr/lib/gnome-applets/drivemount_applet2 --oaf-activ
 4423 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs
 4432 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 4436 ?        S      0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-app
 4478 ?        Ss     0:06 gnome-screensaver
 5032 ?        Rl     3:16 /usr/lib/firefox-3.0.10/firefox
 8049 ?        Sl     0:00  \_ /usr/lib/nspluginwrapper/i386/linux/npviewer.bin
 6583 ?        S      0:00 /bin/sh /opt/Songbird/songbird
 6588 ?        Rl     2:23  \_ /opt/Songbird/./songbird-bin
 7001 ?        S      0:00 /bin/sh /usr/bin/avant-window-navigator
 7003 ?        S      0:01  \_ awn
 7267 ?        S      0:00 /bin/sh /usr/bin/gmail-notify
 7268 ?        S      0:01  \_ python ./notifier.py
 8066 ?        Sl     0:00 gnome-terminal
 8067 ?        S      0:00  \_ gnome-pty-helper
 8068 pts/0    Ss     0:00  \_ bash
 8086 pts/0    R+     0:00      \_ ps f -A

```

Estoy viendo muchas aplicaciones con k por ahi, mejor me mando un 
```
 sudo apt-get remove -purge kubuntu-desktop
```
no?

---

### Post by pablo.s on 2009-05-29
A ver, pará el servidor
Apache2... Me huele que
hay una relación entre
los indios y los submarinos.

Los servicios que empiezan
con k no están relacionados
con KDE (estos no)

---

### Post by josecuervo86 on 2009-05-29
ok, entonces le hago un kill a apache y veo que onda, ya vuelvo :P

Edit: bueno, apache no es.... seguimos

---

### Post by pablo.s on 2009-05-29
Que versión de Nautilus es?
64 bits?

---

### Post by josecuervo86 on 2009-05-29
Sep, benditos 64 bits! 

Nota de color: googleando un poco encontre un flaco que se horrorizaba porque nautilus le consumia **50 Mb de RAM!!** si me viera a mi :P

---

### Post by pablo.s on 2009-05-29
> **josecuervo86 said:**
> encontre un flaco que se horrorizaba porque nautilus le consumia **50 Mb de RAM!!** si me viera a mi :P

Y hay gente que no tiene
recursos. Nautilus es un
exceso para mucha gente
que tiene maquinas un poco
antiguas. Nosotros tenemos
que estar agradecidos que
utilizamos un S.O. como Dios
manda y software que es
estable y además de todo eso
se da el lujo de nadar en RAM.

No, yo te preguntaba que
versión de Nautilus (2 punto
26 cuanto más?)

---

### Post by josecuervo86 on 2009-05-29
Ahh, ok, la versión de nautilus es 2.26.2

---

### Post by pablo.s on 2009-05-29
Yo en 32 bits tengo la
2.26.2. Fijate si no está
la misma en 64 bits.

---

### Post by josecuervo86 on 2009-05-29
ya actualize la info pablo, me fije despues en nautilus y era 2.26.2 la versión. O sea que por ese lado tampoco es.

---

### Post by Mauro22 on 2009-05-29
Intentaste salir de nautilus y volverlo a inciar ??



```
nautilus -q && nautilus
```


y, si tenes ganas corre un chequeo y carga sin el escritorio:

```
nautilus -q && nautilus -c && nautilus --no-desktop
```

Y postea si hay algo raro, en especial con el c ... o el debug que va tirando nautilus por consola.

---

### Post by pablo.s on 2009-05-29
Acabo de buscar en
Launchpad y no hay
presentado ningún bug
report similar a tu problema,
asi que descarto la idea
de un bug.

---

### Post by josecuervo86 on 2009-05-29
Conocen la expresión "para hacer dulce"? esa fue la cantidad de errores que tiro.

Aca va el **nautilus -q && nautilus**

```
josecuervo86@josecuervo86-desktop:~$ nautilus -q && nautilus
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:84: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:85: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:207: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:238: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:251: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:277: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:307: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:331: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:84: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:85: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:207: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:238: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:251: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:277: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:307: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:331: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

(nautilus:10028): Unique-DBus-WARNING **: Error while sending message: Message did not receive a reply (timeout by message bus)

(nautilus:10028): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Aca va el **nautilus -q && nautilus -c && nautilus --no-desktop **

```
josecuervo86@josecuervo86-desktop:~$ nautilus -q && nautilus -c && nautilus --no-desktop
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:84: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:85: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:207: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:238: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:251: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:277: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:307: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:331: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:84: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:85: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:207: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:238: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:251: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:277: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:307: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:331: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:84: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:85: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:207: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:238: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:251: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:277: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:307: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/josecuervo86/.themes/Murrina Quiet/gtk-2.0/gtkrc:331: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

** (nautilus:10040): WARNING **: Unable to add monitor: No soportado
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///home/josecuervo86

(nautilus:10040): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:10040): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

```

Esos errores de Murrine que tira a mansalva imagino que son por el theme que tengo puesto no?

---

### Post by pablo.s on 2009-05-29
Más que Murrine me
llama la atención el
error de Dbus que sale.
Algo de una carpeta
compartida que no 
encuentra... por ahi
está la cosa eh...

---

### Post by Mauro22 on 2009-05-29
Lo del tema no le daria bola, pero podes probar cambiandolo y reiniciando nautilus, para ver que onda.


Yo le daria bola a esto:

```
** (nautilus:10040): WARNING **: Unable to add monitor: No soportado
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///home/josecuervo86

(nautilus:10040): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:10040): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
```


Tenes un error de red_compartida, puede ser que se la pasa "conectando" colgando el proceso y morfando RAM como algo colateral.

y.

Tenes esos dos warning, pero no se a que se refieren... pero por algo lo destaca.

---

### Post by josecuervo86 on 2009-05-29
Bueno, ahora el asunto seria saber **cual proceso se esta trantando de conectar y como cancelarlo**. Gracias por la ayuda muchachos, han hechado mucha claridad al problema.

Una buena: nautilus esta estabilizado en 200 MB, jajaja

---

### Post by Mauro22 on 2009-05-29
Fijate si tenes corriendo:

Nautilus Connect Server


Que segun el ""man"" sirve para:

```
"Nautilus Connect Server is the connection manager for the  GNOME  desktop.

You  can  use  the file manager to access a remote server, be it an FTP
site, a Windows share, a WebDav server or an SSH server."
```

si esta, trata de matarlo (dale con todo jeje) a ver si es ese proceso...


Guarda todo lo importante por las dudas jeje



PD: cambiaste de gtk theme?

---

### Post by pablo.s on 2009-05-29
Para mi sin mostaza
y si puede ser un
agua tónica, gracias.

---

### Post by josecuervo86 on 2009-05-29
No, no esta :-? Ahora lo que me llama la atencion es que se haya establizado en 211 Mb y no siga subiendo como de costumbre :P

---

### Post by pablo.s on 2009-05-29
Es probable que te hayas
armado alguna vez una
carpeta compartida por
SAMBA y después se haya
"descompartido"? Yo me
fijaría cualquier trazo de
smb.conf y limpiarlo,
además de desinstalar
el servicio.

---

### Post by Mauro22 on 2009-05-29
Lo unico que se me ocurre es iniciar nautilus como root y ver si el consumo es el mismo (sin tocar nada porque sos superusuario)


```
nautilus -q && sudo nautilus
```



Me fije, y a mi tambien me das los warning esos, asi que descartado!

---

### Post by josecuervo86 on 2009-05-29
> **pablo.s said:**
> Es probable que te hayas
armado alguna vez una
carpeta compartida por
SAMBA y después se haya
"descompartido"? Yo me
fijaría cualquier trazo de
smb.conf y limpiarlo,
además de desinstalar
el servicio.

Nunca use SAMBA pablo, esto es algo muy raro. probablemente sea algo que hecho yo, pero no tengo la menor idea de que puede ser

---

### Post by josecuervo86 on 2009-05-29
> **Mauro22 said:**
> Lo unico que se me ocurre es iniciar nautilus como root y ver si el consumo es el mismo (sin tocar nada porque sos superusuario)


```
nautilus -q && sudo nautilus
```



Me fije, y a mi tambien me das los warning esos, asi que descartado!

ya lo hice y tampoco, es mas, ni figura entre los procesos el nautilus con superusuario

---

### Post by josecuervo86 on 2009-05-29
Bueno, acabo de reiniar y he notado 2 cosas:

1- Que ya va en camino a los 500 - 600 MB nuevamente
2- Que me consume mucho procesador apenas empieza durante al menos 3 minutos y coincide con la escalada en consumo.

No se que estara haciendo, pero mientras escribia esto salto de 250 a 550 MB en uso :-?

---

### Post by Mauro22 on 2009-05-29
Encontre:


Uno que tenia 128mb de nautilus, 198mb de firefox y 158mb de thunderbird 

y lo arreglo:

```
"I discovered the memory hog... 'twas '**nautilus-clamscan**'. Removing that got memory usage down to 38MB"
```


Otro:

procesos que involucren a nautilus

```
ps aux | grep nautilus
```

---

### Post by josecuervo86 on 2009-05-29
**ps aux | grep nautilus**
```
josecuervo86@josecuervo86-desktop:~$ ps aux | grep nautilus
1000      4378 14.6 18.7 1139636 620436 ?      S    19:34   6:56 nautilus --no-desktop --browser
1000      7192  0.0  0.0   7544   920 pts/0    S+   20:22   0:00 grep nautilus
```

El primero no se bien que hay que hacer...

---

### Post by Mauro22 on 2009-05-29
El primero tenes que eliminar el proceso

nautilus-clamscan


Pero me suena al antivirus ese Clam :S ... no creo que lo tengas..




Y ahora si, la ultima bolilla que me queda es probar con otro usuario (o crear otra cuenta) o hacer backup de /home/usuario/.nautilus y borrarla. 

Es lo ultimo que se me viene a la mente.

---

### Post by josecuervo86 on 2009-05-29
si, el antivirus lo tengo, el proceso ese no, lo elimino al antivirus a ver que pasa, total ni lo uso, ya vuelvo :P

Pd: Todo igual...ahora pruebo creando otro usuario

---

### Post by josecuervo86 on 2009-05-29
Bueno, cree el otro usuario y nautilus marca 7,2 MB. CHAN! Y si instalo nautilus again?

---

### Post by Mauro22 on 2009-05-29
Por lo menos, una buena... el problema es tu sesion jejej...


Yo probaria backup de .nautilus y borrarla (o crearla vacia)

Y tambien hay sobre nautilus en .gnome y .gnome2, pero ahi perdes las configuraciones y eso :SS



Por ahi alguien tiene una mejor idea... aunque la de reinstalar nautilus ta buena.


PD: Y firefox es esa sesion?? Porque si tambien baja... no es solo el nautilus, es algo mas groso-

---

### Post by josecuervo86 on 2009-05-29
Doy plazo hasta media noche (?) y si no me dan una mejor idea primero hago lo que me dijiste vos Mauro y si tampoco anda lo vuelvo a reinstalar y listo. Muchas Gracias por la ayuda.

---

### Post by pablo.s on 2009-05-29
Mas fácil es hacerte un
nuevo usuario, configurar
todo como querés y ver si
el problema sigue.
Si no sigue, ahi si mudás
toda la configuración al
usuario nuevo.

---

### Post by josecuervo86 on 2009-05-29
Si, ya lo hice pablo, y ahi nautilus marca 7,2 asique el problema esta en mi sesión, pasa que es mucho laburo volver a reconfigurar tooooooooooooodo. Voy a ver que hago. Lo tengo que pensar (?)

---

### Post by oktubrer on 2009-05-29
Reinstalar el Nautilus no creo que sirva de mucho porque la configuración en tu home no se elimina.  


> Yo probaria backup de .nautilus y borrarla (o crearla vacia)
Coincido con Mauro22

---

### Post by josecuervo86 on 2009-05-30
Bueno, una menos. Borre el contenido de .nautilus y sigue igual. Cada vez me desconcierta mas este problema. Lo bueno es que en general el rendimiento sigue igual, lo que si noto es que tarda mucho en empezar.

---

### Post by Hei Ku on 2009-05-30
Cual es el proceso que tarda al comenzar? El mismo nautilius?

---

### Post by josecuervo86 on 2009-05-30
> **Hei Ku said:**
> Cual es el proceso que tarda al comenzar? El mismo nautilius?

Sabes que pasa Hei Ku, es que no tarda en comenzar, sino que comienza y vuelve mas lento a todo en general. Llega a estar aprox 2 o mas minutos consumiendo el 50% del procesador al mismo tiempo que come Ram, pasando en esos minutos de unos "normales" 76MB a 350MB. Y si, es nautilus :P

---

### Post by Hei Ku on 2009-05-30
no tiene una opcion --clean o algo asi, para arrancar con una configuracion limpia? Recuerden que gnome tiene el gconf-edit que guarda la configuracion en un solo archivo y no solo en la carpeta .nautilius.

---

### Post by josecuervo86 on 2009-05-30
Yo la cortaría aca. En unos dias voy a comprarme un disco duro, hago un backup de todo y luego fresh install de Jaunty. 
Estimo, porque en realidad no tengo noción de cuando empezo a consumir tanto, que es un problema que viene de arrastre de la epoca en que recien me inicie en Linux y tocaba todo sin saber muy bien que hacia. Ahora con algo mas de 8 meses de contacto constante con GNU/linux (no uso mas Windows, ni para jugar ni nada, solo lo tengo virtualizado por si las deudas) me parece que no voy a volver a repetir el error o por lo menos voy a estar mas pendiente cuando observe esta clase de errores (que para mi eran normales, talvez por haber experimentado Vista en carne ropia).

Gracias a todos! Hicimos lo mas que pudimos. Igual sigo con las orejas abiertas ante cualquier idea ;)

---

