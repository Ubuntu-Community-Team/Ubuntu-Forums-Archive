---
title: "Avant Wndow Navigator (AWN) duplicado"
date: 2008-07-21
forum: Software
---

### Post by luks911 on 2008-07-21
Buenas,
Uso el Avant Window Navigator, la versión trunk y no la que viene en los repositorios de Ubuntu. Esta tiene los applets. Resulta que hace un par de días hubo una actualización y después de eso el AWN al inicar la máquina se ejecuta en dos instancias, o sea por duplicado.
 
Probé sacando la entrada de Sesiones que lo ejecutaba al inicio. Y nada. Lo desinstalé por completo, borré la configuración como explica la wiki de AWN y lo volví a instalar. Y nada. También fui a sesiones y guardé una sesión en la que el AWN no se ejecutaba y desmarqué la casilla para que se guarde la sesión en forma automática. Y nada. ](*,)

Sé que no es grave, pero si puedo evitar que se vea uno encima del otro y me ahorro unos MB de RAM, mejor.
Para más datos, me pasa algo que tal vez sea para otro hilo pero que puede estar relacionado: el control de volumnen queda clavado en 81%. Siempre. Lo bajo, lo subo, reinicio y queda en 81. Ejecuté sudo alsaconf store, algo que leí en algún foro o blog, pero sigue clavado.

La solución que encontré es bastante provisoria y cavernícola, ajustada a mi poco conocimiento: creé una entrada para que al incio se ejecute la siguiente línea
```
killall awn & awn
```
Cierra los AWN y ejecuta uno. 

Bueno, escucho sugerencias para una solución civilizada. 
Muchas gracias

PD: Sí, escribí mal el título el hilo. ¿Cómo lo arreglo? Perdón

---

### Post by faktorqm on 2008-07-23
Bueno, posteá la salida de este comando a ver que cosas estás arrancando en el inicio, NO BORRES NADA, sólo ponelo para ver si está ahi el problema.

```
ls /etc/init.d
```

Salu2!

---

### Post by luks911 on 2008-07-23
Bien, me devolvió todo esto
```

acpid               hostname.sh            rcS
acpi-support        hotkey-setup           readahead
alsasound           hwclockfirst.sh        readahead-desktop
alsa-utils          hwclock.sh             README
anacron             keyboard-setup         reboot
apmd                killprocs              rmnologin
apparmor            klogd                  rsync
apport              laptop-mode            screen-cleanup
atd                 loopback               sendsigs
avahi-daemon        makedev                single
binfmt-support      module-init-tools      skeleton
bluetooth           mountall-bootclean.sh  smartmontools
bootclean           mountall.sh            stop-bootlogd
bootlogd            mountdevsubfs.sh       stop-bootlogd-single
bootmisc.sh         mountkernfs.sh         stop-readahead
brltty              mountnfs-bootclean.sh  sysklogd
checkfs.sh          mountoverflowtmp       udev
checkroot.sh        mtab.sh                udev-finish
console-screen.sh   networking             ufw
console-setup       ntp                    umountfs
cron                pcmciautils            umountnfs.sh
cupsys              policykit              umountroot
dbus                powernowd              urandom
dhcdbd              powernowd.early        usplash
dkms_autoinstaller  pppd-dns               vbesave
dns-clean           preload                waitnfs.sh
gdm                 procps                 winbind
glibc.sh            pulseaudio             wpa-ifupdown
hal                 rc                     x11-common
halt                rc.local               xserver-xorg-input-wacom
```

Creo que no hay nada del AWN, ¿alguna idea?
Un saludo

---

### Post by faktorqm on 2008-07-24
Si no es en el rc.local, y si realmente lo sacaste desde vos decís que lo sacaste, la verdad no sé. Posteate eso, salu2!

```
cat /etc/rc.local
```

---

### Post by Hei Ku on 2008-07-24
Pero el awn no es un daemon, eso debería estar en el Autostart del usuario. Para KDE seria en ~/.kde/Autostart. Para gnome debería ser en un lugar similar.

---

### Post by luks911 on 2008-07-24
> **faktorqm said:**
> Si no es en el rc.local, y si realmente lo sacaste desde vos decís que lo sacaste, la verdad no sé. Posteate eso, salu2!

```
cat /etc/rc.local
```

Les agradezco por colaborar. El rc.local sé que no es porque yo mismo le metí mano por aquel tema de los ciclos de los discos. De hecho:

```
lucas@lucas-notebook:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
hdparm -B 255 /dev/sda

exit 0
```

> **Hei Ku said:**
> Pero el awn no es un daemon, eso debería estar en el Autostart del usuario. Para KDE seria en ~/.kde/Autostart. Para gnome debería ser en un lugar similar.

Busqué todas las carpetas con el nombre autostart y encontré lo siguiente:

1)
/usr/share/gnome/autostart

```
lucas@lucas-notebook:/usr/share/gnome/autostart$ ls
gsynaptics-init.desktop
```

Controlador del touchpad

2)
/usr/share/autostart

```
lucas@lucas-notebook:/usr/share/autostart$ ls
trackerd.desktop

```

3)
/usr/etc/xdg/autostart

```
lucas@lucas-notebook:/usr/etc/xdg/autostart$ ls
mail-notification.desktop

```

4)
/etc/xdg/autostart

```
lucas@lucas-notebook:/etc/xdg/autostart$ ls
bluetooth-applet.desktop        pulseaudio-module-xsmp.desktop
evolution-alarm-notify.desktop  redhat-print-applet.desktop
gnome-at-session.desktop        tracker-applet.desktop
gnome-power-manager.desktop     trackerd.desktop
gnome-volume-manager.desktop    update-notifier.desktop
nm-applet.desktop               user-dirs-update-gtk.desktop

```

Sigo escuchando sugerencias.
:rolleyes:

---

### Post by luks911 on 2008-07-24
Al final lo solucioné, les cuento qué hice a ver si me lo explican, je, porque fue pura intuición. 
Fui al menú Sistema > Preferencias > Sesiones, allí a la pestaña Sesión actual. Por lo que veo aparecen las aplicaciones en ejecución y noté que, entre otras, aparecían en la lista awn y avant-window-navigator. Eso podía explicar el hecho de que se duplicaran. Lo curioso es que seguían ahí incluso después de ejecutar killall awn y sin el dock. 
Primero las marqué, le di al botón de Quitar y después a Aplicar. Pero al reiniciar seguía con el problema. Así que repetí la operación pero después de quitarlas fui a la pestaña Opciones de sesión y a "Recordar las aplicaciones ejecutándose actualmente". Al reiniciar y desmarcando antes esa entrada del inicio que decía "killall awn & awn", el AWN no apareció. 
Ahora falta alguien que me lo explique
:lolflag:
Gracias a los que aportaron

---

