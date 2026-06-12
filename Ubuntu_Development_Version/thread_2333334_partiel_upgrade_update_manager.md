---
title: "partiel upgrade update manager"
date: 2016-08-09
forum: Ubuntu Development Version
---

### Post by valereguerin on 2016-08-09
Hello community,

Yesterday i upgrade 16.04 to 16.10, and do partiel upgrade after with console ; and after reboot with update manager...

Now when i put my computer on, i arrived on another session directly on Vboxuser session  ! 

i can't login my admin session !

i try ctrl + alt + f1,2,3,4,5,6 it's the same thing too many code ligne, impossible to read it's too speed ! 

How find my user session ?

Thanks for regards,

---

### Post by kansasnoob on 2016-08-09
You should never accept a partial upgrade:

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by valereguerin on 2016-08-09
it's ok !
i put automatic connection in Users, i log out and now i'm on my admin session !

You should never accept a partial upgrade...Yes i know but i test it ! it' very risky with too many apps i have ! but it's OK, thanks.

i use GDM3....

---

### Post by jbicha on 2016-08-17
Don't have [-proposed updates enabled]("http://askubuntu.com/q/785414/1579") during the development cycle. As long as you take that advice, it is uncommon to be offered partial updates.

---

### Post by valereguerin on 2016-08-17
hello, after reboot now i m on login window one seconde i see Virtual box kernel is not running... and black screen half seconde and problem software detected in good résolution and half seconde later in less resolution and hals second later too many code lines and repeat those sequence ...ctrl f"x" too many code lines for the moments...

in recovery mod no network connection (pb with libstdc++.so.6...)
etc/resolv.conf no file...

```
update-alternatives 2016-08-02 18:33:30: run with --install /usr/bin/editor editor /bin/nano 40 --slave /usr/share/man/man1/editor.1.gz editor.1.gz /usr/share/man/man1/nano.1.gz
update-alternatives 2016-08-02 18:33:30: run with --install /usr/bin/pico pico /bin/nano 10 --slave /usr/share/man/man1/pico.1.gz pico.1.gz /usr/share/man/man1/nano.1.gz
update-alternatives 2016-08-02 18:33:31: run with --quiet --remove rlogin /usr/bin/ssh
update-alternatives 2016-08-02 18:33:31: run with --quiet --remove rcp /usr/bin/ssh
update-alternatives 2016-08-02 18:33:55: run with --install /usr/bin/aptitude aptitude /usr/bin/aptitude-curses 30 --slave /usr/share/man/man8/aptitude.8.gz aptitude.8.gz /usr/share/man/man8/aptitude-curses.8.gz --slave /usr/share/man/cs/man8/aptitude.8.gz aptitude.cs.8.gz /usr/share/man/cs/man8/aptitude-curses.8.gz --slave /usr/share/man/de/man8/aptitude.8.gz aptitude.de.8.gz /usr/share/man/de/man8/aptitude-curses.8.gz --slave /usr/share/man/es/man8/aptitude.8.gz aptitude.es.8.gz /usr/share/man/es/man8/aptitude-curses.8.gz --slave /usr/share/man/fi/man8/aptitude.8.gz aptitude.fi.8.gz /usr/share/man/fi/man8/aptitude-curses.8.gz --slave /usr/share/man/fr/man8/aptitude.8.gz aptitude.fr.8.gz /usr/share/man/fr/man8/aptitude-curses.8.gz --slave /usr/share/man/gl/man8/aptitude.8.gz aptitude.gl.8.gz /usr/share/man/gl/man8/aptitude-curses.8.gz --slave /usr/share/man/it/man8/aptitude.8.gz aptitude.it.8.gz /usr/share/man/it/man8/aptitude-curses.8.gz --slave /usr/share/man/ja/man8/aptitude.8.gz aptitude.ja.8.gz /usr/share/man/ja/man8/aptitude-curses.8.gz --slave /usr/share/man/pl/man8/aptitude.8.gz aptitude.pl.8.gz /usr/share/man/pl/man8/aptitude-curses.8.gz
update-alternatives 2016-08-02 18:34:07: run with --install /usr/bin/gnome-www-browser gnome-www-browser /usr/bin/firefox 40
update-alternatives 2016-08-02 18:34:07: run with --install /usr/bin/x-www-browser x-www-browser /usr/bin/firefox 40
update-alternatives 2016-08-02 18:34:15: run with --install /usr/bin/x-session-manager x-session-manager /usr/bin/gnome-session 50 --slave /usr/share/man/man1/x-session-manager.1.gz x-session-manager.1.gz /usr/share/man/man1/gnome-session.1.gz
update-alternatives 2016-08-02 18:35:10: run with --install /usr/bin/oslo-messaging-zmq-broker oslo-messaging-zmq-broker /usr/bin/python2-oslo-messaging-zmq-broker 300
update-alternatives 2016-08-02 18:35:10: run with --install /usr/bin/oslo-messaging-zmq-proxy oslo-messaging-zmq-proxy /usr/bin/python2-oslo-messaging-zmq-proxy 300
update-alternatives 2016-08-02 18:35:34: run with --quiet --install /usr/bin/ssh-askpass ssh-askpass /usr/lib/openssh/gnome-ssh-askpass 30 --slave /usr/share/man/man1/ssh-askpass.1.gz ssh-askpass.1.gz /usr/share/man/man1/gnome-ssh-askpass.1.gz
update-alternatives 2016-08-08 17:50:02: run with --install /usr/lib/libblas.so.3 libblas.so.3 /usr/lib/libblas/libblas.so.3 10
update-alternatives 2016-08-08 17:50:13: run with --quiet --remove rlogin /usr/bin/ssh
update-alternatives 2016-08-08 17:50:13: run with --quiet --remove rcp /usr/bin/ssh
update-alternatives 2016-08-08 17:50:14: run with --install /usr/bin/guile guile /usr/lib/x86_64-linux-gnu/guile-2.0/bin/guile 2011 --slave /usr/share/man/man1/guile.1.gz guile.1.gz /usr/share/man/man1/guile-2.0.1.gz
update-alternatives 2016-08-08 17:50:30: run with --install /usr/lib/liblapack.so.3 liblapack.so.3 /usr/lib/lapack/liblapack.so.3 10
update-alternatives 2016-08-08 17:50:42: run with --install /usr/bin/oslo-config-generator oslo-config-generator /usr/bin/python2-oslo-config-generator 300
update-alternatives 2016-08-08 17:50:44: run with --quiet --install /usr/bin/ssh-askpass ssh-askpass /usr/lib/openssh/gnome-ssh-askpass 30 --slave /usr/share/man/man1/ssh-askpass.1.gz ssh-askpass.1.gz /usr/share/man/man1/gnome-ssh-askpass.1.gz
update-alternatives 2016-08-08 17:50:56: run with --install /usr/bin/alembic alembic /usr/bin/python2-alembic 300
update-alternatives 2016-08-08 18:37:05: run with --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/breeze_cursors.theme 102
update-alternatives 2016-08-08 18:37:05: link group x-cursor-theme updated to point to /etc/X11/cursors/breeze_cursors.theme
update-alternatives 2016-08-08 18:37:06: run with --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/Breeze_Snow.theme 41
update-alternatives 2016-08-08 18:37:06: run with --install /usr/bin/ryu ryu /usr/bin/python2-ryu 300
update-alternatives 2016-08-08 18:37:06: link group ryu updated to point to /usr/bin/python2-ryu
update-alternatives 2016-08-08 18:37:06: run with --install /usr/bin/ryu-manager ryu-manager /usr/bin/python2-ryu-manager 300
update-alternatives 2016-08-08 18:37:06: link group ryu-manager updated to point to /usr/bin/python2-ryu-manager
update-alternatives 2016-08-08 18:37:16: run with --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/Adwaita/cursor.theme 90
update-alternatives 2016-08-08 18:37:16: run with --quiet --install /lib/cpp cpp /usr/bin/cpp 10
update-alternatives 2016-08-08 18:37:20: run with --install /usr/bin/mkvinfo mkvinfo /usr/bin/mkvinfo-text 30
update-alternatives 2016-08-08 18:37:26: run with --install /usr/bin/aptitude aptitude /usr/bin/aptitude-curses 30 --slave /usr/share/man/man8/aptitude.8.gz aptitude.8.gz /usr/share/man/man8/aptitude-curses.8.gz --slave /usr/share/man/cs/man8/aptitude.8.gz aptitude.cs.8.gz /usr/share/man/cs/man8/aptitude-curses.8.gz --slave /usr/share/man/de/man8/aptitude.8.gz aptitude.de.8.gz /usr/share/man/de/man8/aptitude-curses.8.gz --slave /usr/share/man/es/man8/aptitude.8.gz aptitude.es.8.gz /usr/share/man/es/man8/aptitude-curses.8.gz --slave /usr/share/man/fi/man8/aptitude.8.gz aptitude.fi.8.gz /usr/share/man/fi/man8/aptitude-curses.8.gz --slave /usr/share/man/fr/man8/aptitude.8.gz aptitude.fr.8.gz /usr/share/man/fr/man8/aptitude-curses.8.gz --slave /usr/share/man/gl/man8/aptitude.8.gz aptitude.gl.8.gz /usr/share/man/gl/man8/aptitude-curses.8.gz --slave /usr/share/man/it/man8/aptitude.8.gz aptitude.it.8.gz /usr/share/man/it/man8/aptitude-curses.8.gz --slave /usr/share/man/ja/man8/aptitude.8.gz aptitude.ja.8.gz /usr/share/man/ja/man8/aptitude-curses.8.gz --slave /usr/share/man/pl/man8/aptitude.8.gz aptitude.pl.8.gz /usr/share/man/pl/man8/aptitude-curses.8.gz
update-alternatives 2016-08-08 18:37:27: run with --install /usr/share/icons/gnome/scalable/places/start-here.svg start-here.svg /usr/share/icons/gnome/scalable/places/debian-swirl.svg 30 --slave /usr/share/icons/gnome/16x16/places/start-here.png start-here-16.png /usr/share/icons/gnome/16x16/places/debian-swirl.png --slave /usr/share/icons/gnome/22x22/places/start-here.png start-here-22.png /usr/share/icons/gnome/22x22/places/debian-swirl.png --slave /usr/share/icons/gnome/24x24/places/start-here.png start-here-24.png /usr/share/icons/gnome/24x24/places/debian-swirl.png --slave /usr/share/icons/gnome/256x256/places/start-here.png start-here-256.png /usr/share/icons/gnome/256x256/places/debian-swirl.png --slave /usr/share/icons/gnome/32x32/places/start-here.png start-here-32.png /usr/share/icons/gnome/32x32/places/debian-swirl.png --slave /usr/share/icons/gnome/48x48/places/start-here.png start-here-48.png /usr/share/icons/gnome/48x48/places/debian-swirl.png
update-alternatives 2016-08-08 18:37:27: link group start-here.svg updated to point to /usr/share/icons/gnome/scalable/places/debian-swirl.svg
update-alternatives 2016-08-08 18:37:27: run with --install /usr/share/icons/gnome/scalable/places/start-here.svg start-here.svg /usr/share/icons/gnome/scalable/places/gnome-foot.svg 20 --slave /usr/share/icons/gnome/16x16/places/start-here.png start-here-16.png /usr/share/icons/gnome/16x16/places/gnome-foot.png --slave /usr/share/icons/gnome/22x22/places/start-here.png start-here-22.png /usr/share/icons/gnome/22x22/places/gnome-foot.png --slave /usr/share/icons/gnome/24x24/places/start-here.png start-here-24.png /usr/share/icons/gnome/24x24/places/gnome-foot.png --slave /usr/share/icons/gnome/256x256/places/start-here.png start-here-256.png /usr/share/icons/gnome/256x256/places/gnome-foot.png --slave /usr/share/icons/gnome/32x32/places/start-here.png start-here-32.png /usr/share/icons/gnome/32x32/places/gnome-foot.png --slave /usr/share/icons/gnome/48x48/places/start-here.png start-here-48.png /usr/share/icons/gnome/48x48/places/gnome-foot.png
update-alternatives 2016-08-08 18:37:40: run with --install /usr/bin/x-session-manager x-session-manager /usr/bin/gnome-session 50 --slave /usr/share/man/man1/x-session-manager.1.gz x-session-manager.1.gz /usr/share/man/man1/gnome-session.1.gz
update-alternatives 2016-08-08 18:37:55: run with --install /usr/bin/gnuplot gnuplot /usr/bin/gnuplot-qt 100 --slave /usr/share/man/man1/gnuplot.1.gz gnuplot.1.gz /usr/share/man/man1/gnuplot-qt.1.gz --slave /usr/share/gnuplot/gnuplot.gih gnuplot.gih /usr/share/gnuplot/gnuplot-qt.gih
update-alternatives 2016-08-08 18:37:57: run with --quiet --install /usr/bin/cc cc /usr/bin/gcc 20 --slave /usr/share/man/man1/cc.1.gz cc.1.gz /usr/share/man/man1/gcc.1.gz
update-alternatives 2016-08-08 18:37:57: run with --quiet --install /usr/bin/c89 c89 /usr/bin/c89-gcc 20 --slave /usr/share/man/man1/c89.1.gz c89.1.gz /usr/share/man/man1/c89-gcc.1.gz
update-alternatives 2016-08-08 18:37:57: run with --quiet --install /usr/bin/c99 c99 /usr/bin/c99-gcc 20 --slave /usr/share/man/man1/c99.1.gz c99.1.gz /usr/share/man/man1/c99-gcc.1.gz
update-alternatives 2016-08-08 18:37:59: run with --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/gnome-terminal.wrapper 40 --slave /usr/share/man/man1/x-terminal-emulator.1.gz x-terminal-emulator.1.gz /usr/share/man/man1/gnome-terminal.1.gz
update-alternatives 2016-08-08 18:38:06: run with --install /usr/bin/c++ c++ /usr/bin/g++ 20 --slave /usr/share/man/man1/c++.1.gz c++.1.gz /usr/share/man/man1/g++.1.gz
update-alternatives 2016-08-08 18:38:16: run with --install /usr/bin/x-window-manager x-window-manager /usr/bin/mutter 60 --slave /usr/share/man/man1/x-window-manager.1.gz x-window-manager.1.gz /usr/share/man/man1/mutter.1.gz
update-alternatives 2016-08-08 18:38:36: run with --install /usr/bin/x-session-manager x-session-manager /usr/bin/startkde 40
update-alternatives 2016-08-09 14:53:52: run with --install /usr/bin/x-window-manager x-window-manager /usr/bin/xfwm4 60 --slave /usr/share/man/man1/x-window-manager.1.gz x-window-manager.1.gz /usr/share/man/man1/xfwm4.1.gz
```

Xsession.errors :

```
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting XAUTHORITY=/home/freeman/.Xauthority
openConnection: connect: Aucun fichier ou dossier de ce type
cannot connect to brltty at :0
dbus-update-activation-environment: setting GTK_MODULES=gail:atk-bridge
Error: couldn't find RGB GLX visual or fbconfig
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
dbus-update-activation-environment: setting CLUTTER_IM_MODULE=xim
dbus-update-activation-environment: setting XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/freeman
dbus-update-activation-environment: setting SHELL=/bin/bash
dbus-update-activation-environment: setting QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
dbus-update-activation-environment: setting GTK_MODULES=gail:atk-bridge
dbus-update-activation-environment: setting USER=freeman
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
dbus-update-activation-environment: setting XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
dbus-update-activation-environment: setting DEFAULTS_PATH=/usr/share/gconf/gnome.default.path
dbus-update-activation-environment: setting LIBVIRT_DEFAULT_URI=qemu:///system
dbus-update-activation-environment: setting XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/usr/share/upstart/xdg:/etc/xdg
dbus-update-activation-environment: setting DESKTOP_SESSION=gnome
dbus-update-activation-environment: setting PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
dbus-update-activation-environment: setting QT_QPA_PLATFORMTHEME=appmenu-qt5
dbus-update-activation-environment: setting PWD=/home/freeman
dbus-update-activation-environment: setting XDG_SESSION_TYPE=x11
dbus-update-activation-environment: setting XMODIFIERS=@im=none
dbus-update-activation-environment: setting LANG=fr_FR.UTF-8
dbus-update-activation-environment: setting MANDATORY_PATH=/usr/share/gconf/gnome.mandatory.path
dbus-update-activation-environment: setting GDM_LANG=fr_FR
dbus-update-activation-environment: setting IM_CONFIG_PHASE=1
dbus-update-activation-environment: setting GDMSESSION=gnome
dbus-update-activation-environment: setting GTK2_MODULES=overlay-scrollbar
dbus-update-activation-environment: setting SHLVL=1
dbus-update-activation-environment: setting HOME=/home/freeman
dbus-update-activation-environment: setting LANGUAGE=fr_FR
dbus-update-activation-environment: setting XDG_SESSION_DESKTOP=gnome
dbus-update-activation-environment: setting LOGNAME=freeman
dbus-update-activation-environment: setting QT4_IM_MODULE=xim
dbus-update-activation-environment: setting XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting XDG_RUNTIME_DIR=/run/user/1000
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting GTK_IM_MODULE=xim
dbus-update-activation-environment: setting XDG_CURRENT_DESKTOP=GNOME
dbus-update-activation-environment: setting XAUTHORITY=/home/freeman/.Xauthority
dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-environment
upstart: Le processus gnome-session (GNOME) main (1871) s'est achevé avec l'état 1
upstart: Le processus logrotate main (1768) a été tué par le signal TERM
upstart: Le processus update-notifier-crash (/var/crash/_opt_teamviewer_tv_bin_teamviewerd.0.crash) main (1808) a été tué par le signal TERM
upstart: Le processus update-notifier-crash (/var/crash/_usr_lib_xorg_Xorg.0.crash) main (1809) a été tué par le signal TERM
upstart: Le processus update-notifier-crash (/var/crash/_usr_share_apt-xapian-index_update-apt-xapian-index-dbus.0.crash) main (1810) a été tué par le signal TERM
upstart: Le processus dbus main (1776) a été tué par le signal TERM
```:confused:

radeon R9 no propriatory driver
unity 16.04 desktop crash,  i had installed gdm3 and gnome desktop...

Thanks for regards,):P

two others 16.04 and one 15.10, PFFFuuu safe....

---

