---
title: "starcraft lag"
date: 2009-05-04
forum: Wine
---

### Post by zero777zero on 2009-05-04
Hello, i installed starcraft a few times before. this is the first time on my new system which has better specs than my old system, however this time starcraft is lagging.

---

### Post by castlefox on 2009-05-05
What wine version do you have?

Are you running the free driver for your card or the non-free one?

---

### Post by zero777zero on 2009-05-05
wine dev 1.1.20

i'm using the default driver after 9.04 install. pretty sure it's open source

---

### Post by u235sentinel on 2009-05-05
> **zero777zero said:**
> wine dev 1.1.20

i'm using the default driver after 9.04 install. pretty sure it's open source

Perhaps your video card is the issue?  I have it installed and haven't seen problems with 1.1.20.  I'm running an Nvidia 9800GTX with the proprietary drivers.

---

### Post by zero777zero on 2009-05-05
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

---

### Post by jofa on 2009-05-05
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

$ wine --version
wine-1.0.1
```

I've played Starcraft without problems on Intrepid, but after a fresh Jaunty install yesterday, it's unplayable. Lags like hell, even the mouse in the main menu...

---

### Post by zero777zero on 2009-05-05
yea same, i'm getting mouse lag in the menu

---

### Post by NightMKoder on 2009-05-05
Wine bug 421 ([http://bugs.winehq.org/show_bug.cgi?id=421](http://bugs.winehq.org/show_bug.cgi?id=421)). There's no DIB engine, so if your computer isn't fast enough, you probably can't run it well.

You can try Max's patches there (the latest one), but you have to compile wine yourself.

---

### Post by YokoZar on 2009-05-05
> **zero777zero said:**
> wine dev 1.1.20

i'm using the default driver after 9.04 install. pretty sure it's open source

Wait are you using the Wine 1.1.20 package or just the wine-dev 1.1.20 package?  You don't need wine-dev at all unless you're building winelib apps (you aren't).

what does dpkg -s wine give you?

---

### Post by jofa on 2009-05-06
This guy doesn't explain the problem, but mentions it's a known issue with Intel graphics and the Jaunty release:

[http://ubuntuforums.org/showthread.php?p=7169385&highlight=starcraft#post7169385]("http://ubuntuforums.org/showthread.php?p=7169385&highlight=starcraft#post7169385")

---

### Post by zero777zero on 2009-05-06
> **YokoZar said:**
> Wait are you using the Wine 1.1.20 package or just the wine-dev 1.1.20 package?  You don't need wine-dev at all unless you're building winelib apps (you aren't).

what does dpkg -s wine give you?

Package: wine
Status: install ok installed
Priority: optional
Section: otherosfs
Installed-Size: 63884
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 1.1.20~winehq0~ubuntu~9.04-0ubuntu1
Replaces: libwine-alsa, libwine-arts, libwine-capi, libwine-cms, libwine-esd, libwine-gl, libwine-gphoto2, libwine-jack, libwine-ldap, libwine-nas, libwine-print, libwine-sane, libwine-twain, wine-doc, wine-utils, winesetuptk, xwine
Depends: procps, binfmt-support (>= 1.1.2), libasound2 (>> 1.0.18), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.7), libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35), libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libgphoto2-2 (>= 2.4.0), libgphoto2-port0 (>= 2.4.0), libice6 (>= 1:1.0.0), liblcms1 (>= 1.15-1), libldap-2.4-2 (>= 2.4.7), libsm6, libx11-6, libxau6, libxext6, libxml2 (>= 2.6.27), libxt6
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Recommends: ttf-liberation, winbind, wine-gecko
Suggests: msttcorefonts, xdg-utils
Conflicts: binfmt-support (<< 1.1.2), libwine, libwine-alsa, libwine-arts, libwine-capi, libwine-cms, libwine-esd, libwine-gl, libwine-gphoto2, libwine-jack, libwine-ldap, libwine-nas, libwine-print, libwine-sane, libwine-twain, wine-doc, wine-utils, winesetuptk, xwine
Conffiles:
 /etc/xdg/menus/applications-merged/wine.menu d15dadc3527b2c6dca96023a5351aedc
 /etc/sysctl.d/wine.sysctl.conf 6eb1c09e24335b0058c3fc60013f1837
Description: Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This package includes a program loader for running unmodified Windows executables
 as well as the Wine project's free version of the Windows API for running programs
 ported from Windows.
 .
  Homepage: [http://www.winehq.org/](http://www.winehq.org/)
Original-Maintainer: Scott Ritchie <scottritchie@ubuntu.com>

---

