---
title: "Too much -dev packages for my humble taste... ;)"
date: 2014-09-22
forum: Ubuntu Development Version
---

### Post by zika on 2014-09-22
Unity-Proposed enabled...
```
:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic unity-control-center unity-settings-daemon usb-modeswitch-data
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
``````
:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  debhelper dh-apparmor libatk-bridge2.0-dev libatk1.0-dev libatspi2.0-dev
  libcairo-script-interpreter2 libcairo2-dev libdbus-1-dev libdbus-glib-1-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgdk-pixbuf2.0-dev
  libglib2.0-dev libgtk-3-dev libharfbuzz-dev libharfbuzz-gobject0 libice-dev
  libmail-sendmail-perl libmirclient-dev libmircommon-dev libpango1.0-dev
  libpcre3-dev libpcrecpp0 libpixman-1-dev libpng12-dev libprotobuf-dev
  libprotobuf-lite8 libpthread-stubs0-dev libsm-dev libsys-hostname-long-perl
  libunity-settings-daemon1 libwayland-dev libx11-dev libx11-doc libxau-dev
  libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxft-dev libxi-dev libxinerama-dev libxkbcommon-dev libxrandr-dev
  libxrender-dev libxtst-dev po-debconf x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev
  zlib1g-dev
The following packages have been kept back:
  usb-modeswitch-data
The following packages will be upgraded:
  unity-control-center unity-settings-daemon
2 upgraded, 67 newly installed, 0 to remove and 1 not upgraded.
Need to get 13,0 MB of archives.
After this operation, 67,4 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

---

### Post by mc4man on 2014-09-22
Maybe because libunity-settings-daemon1 [depends on libgtk3-dev, libglib2.0-dev]("https://bugs.launchpad.net/bugs/1372686")

---

### Post by zika on 2014-09-24
Marking &#8222;solved&#8220;:```
:~$ man hardening-check 
zika@zika:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libunity-settings-daemon1
The following packages have been kept back:
  usb-modeswitch-data
The following packages will be upgraded:
  unity-control-center unity-settings-daemon
2 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 1270 kB of archives.
After this operation, 261 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu/ utopic-proposed/main libunity-settings-daemon1 amd64 14.04.0+14.10.20140922-0ubuntu2 [67,7 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ utopic-proposed/main unity-settings-daemon amd64 14.04.0+14.10.20140922-0ubuntu2 [466 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ utopic/main unity-control-center amd64 14.10.0+14.10.20140922-0ubuntu1 [736 kB]
Fetched 1270 kB in 2s (618 kB/s)              
Selecting previously unselected package libunity-settings-daemon1.
(Reading database ... 201582 files and directories currently installed.)
Preparing to unpack .../libunity-settings-daemon1_14.04.0+14.10.20140922-0ubuntu2_amd64.deb ...
Unpacking libunity-settings-daemon1 (14.04.0+14.10.20140922-0ubuntu2) ...
Preparing to unpack .../unity-settings-daemon_14.04.0+14.10.20140922-0ubuntu2_amd64.deb ...
Unpacking unity-settings-daemon (14.04.0+14.10.20140922-0ubuntu2) over (14.04.0+14.10.20140605-0ubuntu2) ...
Preparing to unpack .../unity-control-center_14.10.0+14.10.20140922-0ubuntu1_amd64.deb ...
Unpacking unity-control-center (14.10.0+14.10.20140922-0ubuntu1) over (14.10.0+14.10.20140702.1-0ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.41.5-1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu3) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for man-db (2.7.0-1) ...
Setting up libunity-settings-daemon1 (14.04.0+14.10.20140922-0ubuntu2) ...
Setting up unity-settings-daemon (14.04.0+14.10.20140922-0ubuntu2) ...
Setting up unity-control-center (14.10.0+14.10.20140922-0ubuntu1) ...
Processing triggers for libc-bin (2.19-10ubuntu1) ...
```
Many thanks to everybody involved in correcting this.

---

