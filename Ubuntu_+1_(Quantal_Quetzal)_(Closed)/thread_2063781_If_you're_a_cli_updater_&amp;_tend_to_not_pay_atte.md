---
title: "If you're a cli updater &amp; tend to not pay attention then"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-27
Over the next several hours or longer you may want to (pay attention
There are possibilities of upgrades that will cause removals of a not kind nature.
currently - 
libatk1.0-0 - Edit should be ok now
xserver-xorg-core -held

---

### Post by ventrical on 2012-09-27
Thanks mac.

---

### Post by jerrylamos on 2012-09-27
Oops!  Thanks for the warning.  I just removed the "-y" from my cli exec.  Looked over the update/upgrade log and didn't see any removal of xorg.

This is a new 2 install..

---

### Post by wojox on 2012-09-27
```
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  glib-networking glib-networking-services xserver-xorg-core
The following packages will be upgraded:
  activity-log-manager-common activity-log-manager-control-center apparmor at-spi2-core baobab binutils command-not-found
  command-not-found-data cpp-4.7 cups cups-bsd cups-client cups-common cups-ppdc deja-dup devhelp devhelp-common
  dh-translations dpkg dpkg-dev eog file-roller foomatic-db-compressed-ppds g++-4.7 gcalctool gcc-4.7 gcc-4.7-base gedit
  gedit-common gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-goa-1.0 gir1.2-gtksource-3.0 gir1.2-soup-2.4 gnome-bluetooth gnome-contacts
  gnome-desktop3-data gnome-font-viewer gnome-menus gnome-online-accounts gnome-screensaver gnome-screenshot
  gnome-system-log gnome-system-monitor grub-common grub-pc grub-pc-bin grub2-common gtk2-engines gucharmap gvfs
  gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs klibc-utils language-selector-common
  language-selector-gnome libatk-adaptor libatk-adaptor-data libatk-bridge2.0-0 libatk-bridge2.0-dev libatk1.0-0
  libatk1.0-data libatk1.0-dev libatk1.0-doc libatspi2.0-0 libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1
  libdevhelp-3-1 libdpkg-perl libgcc1 libgfortran3 libgirepository-1.0-1 libglib2.0-0 libglib2.0-bin libglib2.0-data
  libglib2.0-dev libglib2.0-doc libgnome-bluetooth11 libgnome-desktop-3-4 libgnome-menu-3-0 libgoa-1.0-0 libgoa-1.0-common
  libgomp1 libgtksourceview-3.0-0 libgtksourceview-3.0-common libgucharmap-2-90-7 libgweather-3-1 libitm1 libklibc
  libpam-freerdp libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpython2.7 libquadmath0
  libsoup-gnome2.4-1 libsoup2.4-1 libstdc++6 libstdc++6-4.7-dev libtelepathy-glib0 libunity-webapps0 libyelp0 mountall
  mousetweaks openprinting-ppds ppp python2.7 python2.7-dev python2.7-minimal python3-pyatspi2 signon-ui simple-scan
  system-config-printer-udev telepathy-gabble ubuntu-mono unity-lens-shopping unity-webapps-common unity-webapps-service
  vino xkb-data xserver-xorg-video-intel xserver-xorg-video-mga yelp yelp-xsl
135 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 95.1 MB of archives.
After this operation, 584 kB disk space will be freed.
Do you want to continue [Y/n]? 
```
No dist upgrade tonight then thanks mc4man.

---

### Post by mc4man on 2012-09-27
For the most part it should be better now - the point really was to ck. before committing

right now only evince & ubuntu-desktop will be removed if xserver-xorg-core is held, an hour ago or so a ton of stuff would have from the atk up

Cli'ers can always run a sim first, just add -s to command

sudo apt-get -s blah blah

---

