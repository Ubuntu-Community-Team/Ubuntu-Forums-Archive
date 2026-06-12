---
title: "[SOLVED] need simple, yet powerful, backup script"
date: 2008-02-21
forum: Server Platforms
---

### Post by yarozar on 2008-02-21
Can anyone recommend me script or program which can do the following:

1) backup particular folders (copy and TAR archive),
2) make TAR archive filename based on date of backup,
3) delete obsolete backups (say, ones that are more than 7 days old)

I think I will need to write bash script for this and just add manually to cronjob. Right?

---

### Post by OffAxis on 2008-02-21
you might want to try sbackup; I think it does all of that.

```

sudo apt-get install sbackup
```

---

### Post by yarozar on 2008-02-21
looking at:

The following NEW packages will be installed:
  appres beforelight bitmap cpp cpp-4.1 dbus editres esound-common fontconfig fstobdf gamin gcc-4.1-base gconf2
  gconf2-common gksu gnome-keyring gnome-mime-data iceauth ico libart-2.0-2 libatk1.0-0 libaudiofile0 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libcairo2 libcupsys2 libdatrie0 libdbus-glib-1-2 libdmx1 libdrm2 libesd-alsa0 libfontenc1 libfs6 libgail-common libgail18
  libgamin0 libgconf2-4 libgksu2-0 libgl1-mesa-glx libglade2-0 libglib2.0-0 libgnome-keyring0 libgnome2-0 libgnome2-common
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgtk2.0-0
  libgtk2.0-common libgtop2-7 libgtop2-common libhal-storage1 libhal1 libice6 libidl0 liborbit2 libpango1.0-0
  libpango1.0-common libsm6 libstartup-notification0 libthai-data libthai0 libtiff4 libxaw7 libxcomposite1 libxcursor1
  libxdamage1 libxext6 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxmu6 libxmuu1 libxrandr2 libxrender1
  libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 listres mcpp mesa-utils oclock
  python-cairo python-gconf python-glade2 python-gnome2 python-gnomecanvas python-gobject python-gtk2 python-numeric
  python-pyorbit sbackup sessreg shared-mime-info smproxy viewres x11perf xauth xbase-clients xbiff xcalc xclipboard xclock
  xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-encodings xfonts-utils xfontsel xgamma xgc
  xhost xinit xkbutils xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman xmessage xmodmap xmore xpmutils xprop
  xrandr xrdb xrefresh xrgb xset xsetmode xsetpointer xsetroot xsm xstdcmap xtrap xutils xutils-dev xvidtune xvinfo xwd
  xwininfo xwud


I'd better do simple copies than installing so much additional packags for simple backup. :-)

---

### Post by astrotech226 on 2008-02-21
This can be done pretty easily in a bash script:

```
#!/bin/bash

curdate=`date '+%Y-%m-%d'`

tar cvfhz /path/to/backups/mybackups-$curdate.tar.gz /path/to/dir1 /path/to/dir2

find /path/to/backups -name "mybackups*gz" -ctime +7 -exec rm -f {} \;
```

Tars and gzips two different directories into one file and then removes any tar.gz files in the backup path that were created more than seven days ago.

---

### Post by yarozar on 2008-02-21
Fascinating!! Exactly what I needed. :)

Many thanks!

---

