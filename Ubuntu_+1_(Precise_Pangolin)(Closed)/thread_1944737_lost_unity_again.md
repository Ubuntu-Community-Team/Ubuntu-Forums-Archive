---
title: "lost unity again"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ernestj on 2012-03-21
anyone loose unity after updates or dist-upgrade?

this is the second time for me.


ernie

---

### Post by wojox on 2012-03-21
maybe you should not dist-upgrade? it pulls in partial upgrades, which there is a sticky about. :)

If I run from the terminal this is what I get:
```
wojox@wojox-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  empathy empathy-common gir1.2-rb-3.0 gnome-online-accounts gnome-tweak-tool
  gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
  libgoa-1.0-0 libidl0 libpackagekit-glib2-14 libpurple0 librhythmbox-core5
  libsyncdaemon-1.0-1 libtotem-plparser17 libunity-2d-private0 linux-generic
  linux-headers-generic linux-image-generic nautilus-sendto-empathy
  python-ubuntuone-control-panel rhythmbox rhythmbox-data
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone
  ubuntu-desktop ubuntuone-control-panel ubuntuone-control-panel-common
  ubuntuone-control-panel-gtk ubuntuone-control-panel-qt unity-2d-panel
  unity-2d-shell unity-2d-spread
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.

```

It's holding back packages. If I run the Gui I get I'm offered a partial upgrade:

[IMG]http://ubuntuforums.org/picture.php?albumid=2470&pictureid=8369[/IMG]

Which if I run dist-upgrade it pulls in partial upgrade:
```
wojox@wojox-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libgstfarsight0.10-0 libtelepathy-farsight0 python-farsight python-papyon
  telepathy-butterfly
The following NEW packages will be installed:
  alacarte cups-pk-helper gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjs-1.0 gir1.2-gkbd-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs
  gnome-applets gnome-applets-data gnome-contacts gnome-icon-theme-full
  gnome-panel gnome-panel-data gnome-session-fallback gnome-shell
  gnome-shell-common gnome-themes-standard indicator-applet-complete
  indicator-messages indicator-status-provider-mc5 libarchive12
  libcaribou-common libcaribou0 libclutter-1.0-0 libclutter-1.0-common
  libcogl-common libcogl-pango0 libcogl9 libfarstream-0.1-0 libgjs0c
  libgmime-2.6-0 libgoa-1.0-common libidl-common libmutter0 libnettle4
  libpanel-applet-4-0 libqt4-sql-sqlite libtelepathy-farstream2
  linux-headers-3.2.0-19 linux-headers-3.2.0-19-generic
  linux-image-3.2.0-19-generic mutter-common python-gmenu rhythmbox-mozilla
  rhythmbox-plugin-zeitgeist unity-2d-common
The following packages have been kept back:
  libsyncdaemon-1.0-1 python-ubuntuone-control-panel ubuntuone-control-panel
  ubuntuone-control-panel-common ubuntuone-control-panel-gtk
  ubuntuone-control-panel-qt
The following packages will be upgraded:
  empathy empathy-common gir1.2-rb-3.0 gnome-online-accounts gnome-tweak-tool
  gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
  libgoa-1.0-0 libidl0 libpackagekit-glib2-14 libpurple0 librhythmbox-core5
  libtotem-plparser17 libunity-2d-private0 linux-generic linux-headers-generic
  linux-image-generic nautilus-sendto-empathy rhythmbox rhythmbox-data
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone
  ubuntu-desktop unity-2d-panel unity-2d-shell unity-2d-spread
32 upgraded, 61 newly installed, 5 to remove and 6 not upgraded.
Need to get 84.6 MB of archives.
After this operation, 287 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by ernestj on 2012-03-21
you are right, now i might need those packages.

running gnome 3 now, need to get back to unity. i need the force.:p

ernie

---

