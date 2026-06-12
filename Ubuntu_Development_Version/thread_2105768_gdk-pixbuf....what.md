---
title: "gdk-pixbuf....what?"
date: 2013-01-17
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2013-01-17
Yeaaaayyy....for today upgrades:lolflag:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  baobab gconf-service gconf-service-backend gconf2 gconf2-common
  gir1.2-freedesktop gir1.2-gconf-2.0 gir1.2-gdata-0.0 gir1.2-gdkpixbuf-2.0
  gir1.2-glib-2.0 gir1.2-peas-1.0 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1
  libdrm2 libgconf-2-4 libgdata-common libgdata13 libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgirepository-1.0-1 libglib2.0-0 libglib2.0-bin
  libglib2.0-data libpeas-1.0-0 libpeas-common libpoppler-glib8 libpoppler28
  poppler-utils python3-update-manager update-manager update-manager-core
  xserver-xorg-video-intel
33 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,780 kB of archives.
After this operation, 280 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
```

```
gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```

unity greeter:

[IMG]http://i.imgur.com/13Th6.jpg[/IMG]

Unity won't load, drop to tty1, sudo service lightdm stop, startx....Yeaaaayyyy ):P

gnome-screenshot or scrot not working, using camera phone:

[IMG]http://i.imgur.com/EWaeV.jpg[/IMG]

---

### Post by serdotlinecho on 2013-01-17
OK, problem solved :D

```
sudo apt-get install libgdk-pixbuf2.0-dev
gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```

[http://paste.ubuntu.com/1540498/](http://paste.ubuntu.com/1540498/)

---

