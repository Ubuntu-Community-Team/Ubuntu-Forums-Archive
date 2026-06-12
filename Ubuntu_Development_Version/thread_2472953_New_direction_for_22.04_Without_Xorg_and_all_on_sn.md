---
title: "New direction for 22.04? Without Xorg and all on snaps?"
date: 2022-03-18
forum: Ubuntu Development Version
---

### Post by zika on 2022-03-18
```



&#1057;&#1083;&#1077;&#1076;&#1077;&#1115;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080; &#1073;&#1080;&#1115;&#1077; &#1059;&#1050;&#1051;&#1054;&#1034;&#1045;&#1053;&#1048;:
  apport apport-gtk aptdaemon apturl apturl-common command-not-found gnome-control-center language-selector-common language-selector-gnome libappindicator3-1 nautilus-share python3-apport python3-apt 
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-commandnotfound python3-distupgrade python3-software-properties python3-update-manager software-properties-common software-properties-gtk 
  ttf-mscorefonts-installer ubuntu-advantage-desktop-daemon ubuntu-advantage-tools ubuntu-desktop ubuntu-desktop-minimal ubuntu-drivers-common ubuntu-minimal ubuntu-release-upgrader-core 
  ubuntu-release-upgrader-gtk unattended-upgrades update-manager update-manager-core update-notifier update-notifier-common xorg xserver-xorg
&#1057;&#1083;&#1077;&#1076;&#1077;&#1115;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080; &#1073;&#1080;&#1115;&#1077; &#1085;&#1072;&#1076;&#1086;&#1075;&#1088;&#1072;&#1106;&#1077;&#1085;&#1080;:
  duplicity libayatana-appindicator3-1 libldb2 libpython3-stdlib libsmbclient libtalloc2 libwbclient0 python3 python3-cairo python3-cffi-backend python3-cups python3-dbus python3-distutils python3-gdbm 
  python3-gi python3-gi-cairo python3-ldb python3-lib2to3 python3-minimal python3-netifaces python3-protobuf python3-psutil python3-pyxattr python3-systemd python3-talloc python3-urwid python3-yaml samba-libs
&#1085;&#1072;&#1076;&#1086;&#1075;&#1088;&#1072;&#1106;&#1077;&#1085;&#1080;&#1093; &#8212; 28, &#1085;&#1086;&#1074;&#1086;&#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1080;&#1093; &#8212; 0, &#1079;&#1072; &#1091;&#1082;&#1083;&#1072;&#1114;&#1072;&#1114;&#1077; &#8212; 37, &#1080; &#1085;&#1077;&#1085;&#1072;&#1076;&#1086;&#1075;&#1088;&#1072;&#1106;&#1077;&#1085;&#1080;&#1093; &#8212; 0.
&#1052;&#1086;&#1088;&#1072;&#1084; &#1076;&#1072; &#1076;&#1086;&#1074;&#1091;&#1095;&#1077;&#1084; 8790 kB &#1072;&#1088;&#1093;&#1080;&#1074;&#1072;.
&#1053;&#1072;&#1082;&#1086;&#1085; &#1086;&#1074;&#1077; &#1088;&#1072;&#1076;&#1114;&#1077;, &#1085;&#1072; &#1076;&#1080;&#1089;&#1082;&#1091; &#1073;&#1080;&#1115;&#1077; &#1086;&#1089;&#1083;&#1086;&#1073;&#1086;&#1106;&#1077;&#1085;&#1086; 22,2 MB &#1087;&#1088;&#1086;&#1089;&#1090;&#1086;&#1088;&#1072;.


```I know, I do use prerelease ppa's and this list is growing every day. I've removed whole LibreOffice, RhythmBox, to get that list a bit smaller, and still... ;) I do not complain, all works pretty nice but, just wondering about Xorg and apt. Snap is not install on this machine so I do not know what is offered in Snap domain...

---

### Post by colin-i on 2022-03-18
Snap is a universal linux packaging method preferable instead of deb/rpm packaging.
X11 is more popular than wayland.

---

### Post by zika on 2022-03-18
> **colin-i said:**
> Snap is an universal linux packaging method preferable instead of deb/rpm packaging.
X11 is more popular than wayland.OK, god to know Your opinion. Thank You. Are there any kind of sources, of data, that You draw those conclusions from? Any knowledge about the question I've asked about 22.04?

---

### Post by Claus7 on 2022-03-18
Hello,

*zika* I do not understand what these packages are all about. I tried the other time an ubuntu development release using virtualbox and snap was used by default. In order to install software center, it could be done via command line. Also libreoffice and many other applications were snap ones. I do not know if I answer your question. You can check also here posts 16 and 18:
[https://ubuntuforums.org/showthread.php?t=2472529&page=2](https://ubuntuforums.org/showthread.php?t=2472529&page=2)

Regards!

---

### Post by grahammechanical on 2022-03-18
Ubuntu 20.04 defaults to the X-server with Ubuntu on Wayland as a login option. Ubuntu 22.04 will default to a Wayland compositor with Ubuntu on X-server as a login option. So, I guess that X.server will be part of the Ubuntu repositories at least for the life span of Ubuntu 22.04.

Apparently, there are some programs coded to work with X-server that have not been re-written to work with Wayland. So, we have a library called X-wayland for those programs or a login to Ubuntu on the X-server.

There are security vulnerabilities in the X-server that cannot be closed. So, in general, and in Ubuntu in particular there is a shift away from using the x-server to using an alternative windowing system such as a Wayland compositor. I guess that it will be some years before the Ubuntu developers can strip out all the X-server packages without getting a complaint for somebody.

Regards

---

### Post by colin-i on 2022-03-18
> **zika said:**
> OK, god to know Your opinion. Thank You. Are there any kind of sources, of data, that You draw those conclusions from? Any knowledge about the question I've asked about 22.04?

About x11/wayland: [https://raw.githubusercontent.com/linuxhw/Trends/master/README.md](https://raw.githubusercontent.com/linuxhw/Trends/master/README.md)  

Talking about snap, there aren't many apps at ```
snap list
``` for a minimal installation but, for example, firefox will be snap only in a few days, it is in "proposed". And I said it is universal to pack as snap for many linux distribution instead of deb/rpm for every linux distribution from a developer point of view.

---

### Post by grahammechanical on 2022-03-18
I have chosen to talk about snap separately.

I do know from experience that if we upgrade to 22.04 the deb version of Firefox gets replaced by the snap version. So, I guess that a fresh install of 22.04 and all following releases will come with the snap version of Firefox as default. I do not think that anyone will notice the difference.

I know that there is a snap version of Libreoffice but I do not know if it will be installed by default from 22.04 onwards. I guess it depends on whether the Libreoffice developers take over responsibility for maintaining the snap version or not. The Firefox snap is now an official offering by the Firefox developers.

There is a movement to what is called an immutable Linux. Redhat is developing such an OS. They call it Silverblue and they use Flatpacks.

[https://www.redhat.com/sysadmin/immutability-silverblue](https://www.redhat.com/sysadmin/immutability-silverblue)

Canonical has an immutable Linux. It is called Ubuntu Core. It uses snaps. It does not have a desktop environment. Some years ago Canonical experimented with a immutable Linux with a desktop environment. It was called Ubuntu Desktop Next. It was a snap based OS that could only run snap apps. It was built on 14.10 code and was not upgraded to 15.04 code and beyond. It used the Unity 8 desktop that was being developed for the Ubuntu phone OS.

There has been talk about certain utilities being installed in snap versions by default. I cannot find any in 20.04. Just the snaps that I have installed myself and the snap libraries that are needed by those apps. Rub this code in 22.04 to reveal all or nothing.

```
snap list
```

Regards

---

### Post by zebra2 on 2022-03-19
The only thing that stays the same is everything changes. I have been using Wayland and Gnome since they were introduced with the discontinuing of the Unity 
Desktop.  I took on Unity the first day that it was introduced with Natty way back there and was satisfied with that when many were complaining about the demise of Gnome 2.  Wayland was a little clunky at first until xwayland advanced to where it is now.  I use out of the box Ubuntu/Gnome4/Wayland on all of my systems and have no complaints. It all works well. I personally think it is all going where it needs to go to survive anyway.  Canonical is a forward thinking company. Anyone can read the support requests here and elsewhere to see there is a need for solutions. Hanging onto the past when support for new ideas and needs are required is not an option. X and Apt are on the way out. I was ok with it all but when it is over, its over.

---

### Post by jbicha on 2022-03-21
If you want your command in English for easier sharing, you can prefix your command with something like

```
LANGUAGE=en 
```

---

### Post by zika on 2022-04-04
> **jbicha said:**
> If you want your command in English for easier sharing, you can prefix your command with something like ```
LANGUAGE=en 
```
Sorry, my mistake, not my intention, I know how to present in more readable way but I was just carried by a question I wanted to ask. 
```
The following packages will be REMOVED:  apport apport-gtk aptdaemon apturl apturl-common command-not-found gnome-control-center language-selector-common language-selector-gnome libappindicator3-1 nautilus-share python3-apport python3-apt
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-commandnotfound python3-distupgrade python3-software-properties python3-update-manager software-properties-common software-properties-gtk
  ttf-mscorefonts-installer ubuntu-advantage-desktop-daemon ubuntu-advantage-tools ubuntu-desktop ubuntu-desktop-minimal ubuntu-drivers-common ubuntu-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk unattended-upgrades update-manager update-manager-core update-notifier update-notifier-common xorg xserver-xorg
The following packages will be upgraded:
  duplicity libayatana-appindicator3-1 libldb2 libpython3-stdlib libsmbclient libtalloc2 libwbclient0 python3 python3-brlapi python3-cairo python3-cffi-backend python3-cups python3-dbus python3-distutils
  python3-gdbm python3-gi python3-gi-cairo python3-ldb python3-lib2to3 python3-minimal python3-netifaces python3-protobuf python3-psutil python3-pyxattr python3-systemd python3-talloc python3-urwid python3-yaml
  samba-libs
29 upgraded, 0 newly installed, 37 to remove and 0 not upgraded.
Need to get 8884 kB of archives.
After this operation, 22,2 MB disk space will be freed.
```
Other machine:
```

:~$ sudo apt dist-upgrade 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apg apport-symptoms aptdaemon-data distro-info gir1.2-goa-1.0 gir1.2-snapd-1 gnome-control-center-faces gnome-online-accounts gnome-software-common libcolord-gtk1 libglu1-mesa libgsound0 libmad0
  libmalcontent-0-0 libmikmod3 libntfs-3g883 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libsdl1.2debian libtorrent-rasterbar10 libwhoopsie-preferences0 libxatracker2 libxvmc1
  mobile-broadband-provider-info network-manager-gnome power-profiles-daemon python-apt-common python3-certifi python3-dateutil python3-debconf python3-defer python3-distro-info python3-httplib2
  python3-jeepney python3-keyring python3-launchpadlib python3-lazr.restfulclient python3-lazr.uri python3-macaroonbakery python3-problem-report python3-protobuf python3-pymacaroons python3-pyparsing
  python3-requests python3-rfc3339 python3-secretstorage python3-systemd python3-tz python3-wadllib python3-xkit realmd whoopsie-preferences x11-apps x11-session-utils xcvt xfonts-scalable xinit xinput
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  apport apport-gtk aptdaemon apturl apturl-common command-not-found fuse gnome-control-center gnome-software language-selector-common language-selector-gnome libappindicator3-1 libsndio7.1 nautilus-share
  python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets python3-commandnotfound python3-distupgrade python3-software-properties python3-update-manager software-properties-common
  software-properties-gtk ubuntu-advantage-desktop-daemon ubuntu-advantage-tools ubuntu-desktop ubuntu-desktop-minimal ubuntu-drivers-common ubuntu-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk unattended-upgrades update-manager update-manager-core update-notifier update-notifier-common xorg xserver-xorg
The following NEW packages will be installed:
  fuse3 libntfs-3g89 libopusfile0 libsdl2-image-2.0-0 libsdl2-mixer-2.0-0 libsdl2-ttf-2.0-0 libsndio7.0 libtorrent-rasterbar2.0
The following packages will be upgraded:
  duplicity exfat-fuse ffmpeg gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hplip hplip-data libavcodec58 libavdevice58 libavfilter7 libavformat58 libavutil56 libayatana-appindicator3-1
  libboost-python1.74.0 libfuse2 libhpmud0 libldb2 libopenal-data libopenal1 libpostproc55 libpython3-stdlib libsane-hpaio libsmbclient libswresample3 libswscale5 libtalloc2 libtevent0 libwbclient0 ntfs-3g
  printer-driver-hpcups python3 python3-brlapi python3-cairo python3-cap-ng python3-cffi-backend python3-cups python3-dbus python3-distutils python3-gdbm python3-geoip python3-gi python3-gi-cairo python3-ldb
  python3-lib2to3 python3-libtorrent python3-markupsafe python3-minimal python3-netifaces python3-numpy python3-pil python3-protobuf python3-psutil python3-pygame python3-pyrsistent python3-pyxattr
  python3-rencode python3-renderpm python3-reportlab python3-reportlab-accel python3-setproctitle python3-systemd python3-talloc python3-urwid python3-yaml python3-zope.interface samba-libs xdg-desktop-portal
  xdg-desktop-portal-gtk
72 upgraded, 8 newly installed, 39 to remove and 0 not upgraded.
Need to get 37,7 MB of archives.
After this operation, 28,0 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```
This is not a call for help, just a snapshot of current state and glimpse of that are here things to come...

Update&#8321;: Downloaded, yesterday, at work, 22.04 daily_build_ISO and worked with it for some time. It seems that I have some dependence(s) war so I will be following that and try to locate who is fighting with whom... XOrg is installed in ISO, by default so...

Update&#8322;: In the meantime I had one (the same) quirk with oncoming SW for testing in 22.04devel cycle so I did, after lot of trying to detect what was, the same, error and, eventually, did fresh install of 21.04devel so this question is answered and I have new friendship with X11 and snap. So, thread is marked as (kind of, let's say..) &#8222;solved&#8220; .

---

