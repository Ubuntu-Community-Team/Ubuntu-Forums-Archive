---
title: "Please backport gtk2 version of mplayerplug-in (mozilla-mplayer)"
date: 2005-07-10
forum: Ubuntu Backports
---

### Post by jcohen on 2005-07-10
It's always bugged me that Debian packaged mozilla-mplayer without gtk2 support. If compiled with gtk2 support, mplayerplug-in is actually very nice. It has buttons to play, pause, stop, and make the video full screen. there's also a menu which can be used to make the video full screen or to save the stream when it's done downloading. In essence, by compiling with gtk2 you're making mozilla-mplayer more user friendly, easier to use, more attractive, and giving fullscreen & download functionality. All you have to do is compile with the ./configure --enable-gtk2 flag. I've done this myself and built a deb package with checkinstall. I'm using the latest version of mozilla-mplayer which is 2.85. 

Since some users prefer the non-gtk version, there could always be a seperate gtk version packaged.

---

### Post by jcohen on 2005-07-10
This change is ridiculously easy to make. You merely have to edit ./mplayerplug-in-2.70/debian/rules and change "DEB_CONFIGURE_EXTRA_FLAGS := --enable-x" to "DEB_CONFIGURE_EXTRA_FLAGS := --enable-gtk2". I rebuilt the package with "fakeroot dpkg-buildpackage" and the resulting deb installed and worked perfectly. I've attached the edited rules file.

---

### Post by jcohen on 2005-07-10
I had to alter the debian/changelog, debian/files, and debian/mozilla-mplayer/DEBIAN/control to up the version to 2.70-1ubuntu2. I built a new deb package and I have the new source available as well.

---

### Post by Piksou on 2005-08-07
and for mplayer itself ? :)
i have tried to compile a patched version but the result was not great :-/
could someone build a mplayer-gtk2 ?

---

