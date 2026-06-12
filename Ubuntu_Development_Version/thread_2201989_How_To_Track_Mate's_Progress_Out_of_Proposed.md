---
title: "How To Track Mate's Progress Out of Proposed?"
date: 2014-01-26
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2014-01-26
I see a number of Mate packages are in Universe for Trusty, apparently after completing their rite of passage through Proposed.

What should I track to learn when all of Mate is in Universe and installable?

---

### Post by deadflowr on 2014-01-27
How about the package mate-desktop?

---

### Post by kansasnoob on 2014-01-27
> **deadflowr said:**
> How about the package mate-desktop?

No, not really, I've tried:

```
sudo apt-get install mate-desktop mate-themes mate-icon-theme mate-backgrounds mate-notification-daemon desktop-base
```

Seemed to go OK:

```
lance@lance-desktop:~$ sudo apt-get install mate-desktop mate-themes mate-icon-theme mate-backgrounds mate-notification-daemon desktop-base
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gtk2-engines gtk2-engines-pixbuf libmate-desktop-2-17 libmatewnck-common
  libmatewnck0 libunique-1.0-0 mate-desktop-common
Suggested packages:
  gnome kde-standard xfce4 wmaker
The following NEW packages will be installed:
  desktop-base gtk2-engines gtk2-engines-pixbuf libmate-desktop-2-17
  libmatewnck-common libmatewnck0 libunique-1.0-0 mate-backgrounds
  mate-desktop mate-desktop-common mate-icon-theme mate-notification-daemon
  mate-themes
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.1 MB of archives.
After this operation, 58.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

##############################################

y/main libunique-1.0-0 i386 1.1.6-4ubuntu2 [21.0 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mate-backgrounds all 1.6.0-1 [9,406 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mate-desktop-common all 1.6.2-1 [395 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mate-desktop i386 1.6.2-1 [17.8 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mate-icon-theme all 1.6.3-1 [10.7 MB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mate-notification-daemon i386 1.6.1-1 [69.7 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mate-themes all 1.6.2-1 [2,116 kB]
Fetched 29.1 MB in 29s (985 kB/s)                                              
Selecting previously unselected package desktop-base.
(Reading database ... 165490 files and directories currently installed.)
Preparing to unpack .../desktop-base_7.0.3ubuntu1_all.deb ...
Unpacking desktop-base (7.0.3ubuntu1) ...
Selecting previously unselected package libmate-desktop-2-17:i386.
Preparing to unpack .../libmate-desktop-2-17_1.6.2-1_i386.deb ...
Unpacking libmate-desktop-2-17:i386 (1.6.2-1) ...
Selecting previously unselected package libmatewnck-common.
Preparing to unpack .../libmatewnck-common_1.6.1-3_all.deb ...
Unpacking libmatewnck-common (1.6.1-3) ...
Selecting previously unselected package libmatewnck0:i386.
Preparing to unpack .../libmatewnck0_1.6.1-3_i386.deb ...
Unpacking libmatewnck0:i386 (1.6.1-3) ...
Selecting previously unselected package gtk2-engines:i386.
Preparing to unpack .../gtk2-engines_1%3a2.20.2-3ubuntu1_i386.deb ...
Unpacking gtk2-engines:i386 (1:2.20.2-3ubuntu1) ...
Selecting previously unselected package gtk2-engines-pixbuf:i386.
Preparing to unpack .../gtk2-engines-pixbuf_2.24.22-1ubuntu1_i386.deb ...
Unpacking gtk2-engines-pixbuf:i386 (2.24.22-1ubuntu1) ...
Selecting previously unselected package libunique-1.0-0.
Preparing to unpack .../libunique-1.0-0_1.1.6-4ubuntu2_i386.deb ...
Unpacking libunique-1.0-0 (1.1.6-4ubuntu2) ...
Selecting previously unselected package mate-backgrounds.
Preparing to unpack .../mate-backgrounds_1.6.0-1_all.deb ...
Unpacking mate-backgrounds (1.6.0-1) ...
Selecting previously unselected package mate-desktop-common.
Preparing to unpack .../mate-desktop-common_1.6.2-1_all.deb ...
Unpacking mate-desktop-common (1.6.2-1) ...
Selecting previously unselected package mate-desktop.
Preparing to unpack .../mate-desktop_1.6.2-1_i386.deb ...
Unpacking mate-desktop (1.6.2-1) ...
Selecting previously unselected package mate-icon-theme.
Preparing to unpack .../mate-icon-theme_1.6.3-1_all.deb ...
Unpacking mate-icon-theme (1.6.3-1) ...
Selecting previously unselected package mate-notification-daemon.
Preparing to unpack .../mate-notification-daemon_1.6.1-1_i386.deb ...
Unpacking mate-notification-daemon (1.6.1-1) ...
Selecting previously unselected package mate-themes.
Preparing to unpack .../mate-themes_1.6.2-1_all.deb ...
Unpacking mate-themes (1.6.2-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for libglib2.0-0:i386 (2.39.3-0ubuntu4) ...
Processing triggers for gnome-menus (3.8.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20131125-0ubuntu2) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.6-1) ...
Setting up desktop-base (7.0.3ubuntu1) ...
update-alternatives: using /usr/share/images/desktop-base/joy-wallpaper_1600x1200.svg to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode
update-alternatives: using /usr/share/images/desktop-base/joy-wallpaper_1920x1080.svg to provide /usr/share/images/desktop-base/desktop-background (desktop-background) in auto mode
update-alternatives: using /usr/share/images/desktop-base/joy.xml to provide /usr/share/images/desktop-base/desktop-background.xml (desktop-background.xml) in auto mode
update-alternatives: using /usr/share/images/desktop-base/spacefun-splash.svg to provide /usr/share/images/desktop-base/desktop-splash (desktop-splash) in auto mode
update-alternatives: using /usr/share/images/desktop-base/joy-grub.png to provide /usr/share/images/desktop-base/desktop-grub.png (desktop-grub) in auto mode
update-initramfs: deferring update (trigger activated)
Setting up libmate-desktop-2-17:i386 (1.6.2-1) ...
Setting up libmatewnck-common (1.6.1-3) ...
Setting up libmatewnck0:i386 (1.6.1-3) ...
Setting up gtk2-engines:i386 (1:2.20.2-3ubuntu1) ...
Setting up gtk2-engines-pixbuf:i386 (2.24.22-1ubuntu1) ...
Setting up libunique-1.0-0 (1.1.6-4ubuntu2) ...
Setting up mate-backgrounds (1.6.0-1) ...
Setting up mate-desktop-common (1.6.2-1) ...
Setting up mate-desktop (1.6.2-1) ...
Setting up mate-icon-theme (1.6.3-1) ...
Setting up mate-notification-daemon (1.6.1-1) ...
Setting up mate-themes (1.6.2-1) ...
Processing triggers for initramfs-tools (0.103ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-5-generic
Processing triggers for libc-bin (2.18-0ubuntu6) ...
lance@lance-desktop:~$ 

##################################################

lance@lance-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But no login option appeared in 'lightdm' so I installed gdm:

```
lance@lance-desktop:~$ sudo apt-get install gdm
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-icon-theme-full gnome-shell
  gnome-shell-common gnome-themes-standard gnome-themes-standard-data
  libcaribou-common libcaribou0 libgdm1 libgjs0d libmozjs-17.0-0 libmutter0c
  mutter-common xserver-xephyr
The following NEW packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-icon-theme-full gnome-shell
  gnome-shell-common gnome-themes-standard gnome-themes-standard-data
  libcaribou-common libcaribou0 libgdm1 libgjs0d libmozjs-17.0-0 libmutter0c
  mutter-common xserver-xephyr
0 upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.4 MB of archives.
After this operation, 47.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Still no login option for Mate :(

And there is no dedicated mailing list for "ubuntu-mate":

[http://ml.mate-desktop.org/listinfo/](http://ml.mate-desktop.org/listinfo/)

---

### Post by vasa1 on 2014-01-27
> **deadflowr said:**
> How about the package mate-desktop?

[https://launchpad.net/ubuntu/+source/mate-desktop/1.6.2-1](https://launchpad.net/ubuntu/+source/mate-desktop/1.6.2-1) ?

---

### Post by Mateusz Stachowski on 2014-01-27
Those packages are copied from Debian Unstable.

> 
[LIST]
[*]Copied from debian sid in Primary Archive for Debian GNU/Linux by [Ubuntu Archive Auto-Sync]("https://launchpad.net/~katie")(sponsored by [Ubuntu Archive Robot]("https://launchpad.net/~ubuntu-archive-robot"))
[/LIST]


They are created by Debian MATE Packaging Team and you should track the progress by looking at their packages overview.

[http://qa.debian.org/developer.php?login=pkg-mate-team@lists.alioth.debian.org](http://qa.debian.org/developer.php?login=pkg-mate-team@lists.alioth.debian.org)

---

### Post by buzzingrobot on 2014-01-27
> **Mateusz Stachowski said:**
> Those packages are copied from Debian Unstable.



They are created by Debian MATE Packaging Team and you should track the progress by looking at their packages overview.

[http://qa.debian.org/developer.php?login=pkg-mate-team@lists.alioth.debian.org](http://qa.debian.org/developer.php?login=pkg-mate-team@lists.alioth.debian.org)

Thanks.

I'm assuming (hoping?) there will be an announcement when it's completed, and a meta-package analagous to kde-full, kubuntu-desktop, etc., created.

---

### Post by kansasnoob on 2014-01-27
> **Mateusz Stachowski said:**
> Those packages are copied from Debian Unstable.



They are created by Debian MATE Packaging Team and you should track the progress by looking at their packages overview.

[http://qa.debian.org/developer.php?login=pkg-mate-team@lists.alioth.debian.org](http://qa.debian.org/developer.php?login=pkg-mate-team@lists.alioth.debian.org)

So maybe also follow this mailing list:

[http://ml.mate-desktop.org/listinfo/debian-mate](http://ml.mate-desktop.org/listinfo/debian-mate)

Or if you have the time even subscribe :D

I would but I've already had to step back from most of my Lubuntu activities because I just have too much on my plate :(

---

