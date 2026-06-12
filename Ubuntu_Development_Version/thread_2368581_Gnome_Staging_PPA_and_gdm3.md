---
title: "Gnome Staging PPA and gdm3"
date: 2017-08-12
forum: Ubuntu Development Version
---

### Post by harry332 on 2017-08-12
Is anyone here using Gnome Staging PPA and the newest GDM3_3.25.90?
Does that work with you?

I have enabled that PPA (artful), but I cannot upgrade gdm3 nor gnome-desktop3:

1. Gdm3_3.25.90 stops at tty1 with a desktop background (not the usual grey bg) but with no login window.
The official version 3.24.2 is fine.

2. Gnome-desktop3_3.25.90 is broken with thumbnailer (thumbnailer crashes), so nautilus does not show any thumbnails. (LP: [#1709164]("https://launchpad.net/bugs/1709164"))
Again the official version 3.24.2 is fine.

---

### Post by P-I H on 2017-08-12
I have used it in two installations both worked for a while, but crashed later after upgrades. In one system I couldn't login. It started with a "Gnome User". The other system didn't start the desktop environment. Both systems required re-installation.
There were also problems with gnome-control-center. 
[https://bugzilla.gnome.org/show_bug.cgi?id=784562](https://bugzilla.gnome.org/show_bug.cgi?id=784562)
[https://bugs.launchpad.net/ubuntu-gnome/+bug/1709965](https://bugs.launchpad.net/ubuntu-gnome/+bug/1709965)

---

### Post by harry332 on 2017-08-12
OK, pretty much the same kind of an experience that I had.
After unsuccessful starting, I did login manually from tty7, and downgraded gdm3 to the official 3.24.2 version.
No need to any re-installations.

---

### Post by rrnbtter on 2017-08-12
Greetings, 
Interesting.  I'm getting 3.24.3 by default through the downstream. Proposed enabled.

rrnbtter@rrnbtter-110-15ISK:~$ inxi1
inxi -Sxx
System:    Host: rrnbtter-110-15ISK Kernel: 4.12.0-11-generic x86_64
           bits: 64 gcc: 7.1.0
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1) dm: gdm3
           Distro: Ubuntu Artful Aardvark (development branch)
$DESKTOP_SESSION
gnome-wayland
$XDG_SESSION_TYPE
wayland
GNOME Shell 3.24.3
Version: 3.24.3-0ubuntu1
loginctl type
Type=wayland

---

### Post by jbicha on 2017-08-13
gdm3 should be fixed now. Sorry about that.

The gnome-desktop3 thumbnailer is a known issue: please read the debian/changelog if you want more information about that.

---

### Post by harry332 on 2017-08-13
Thanks Jeremy.
Yes confirming the gdm3_3.25.90-0ubuntu0~artful2 works well.

And yes I know the thumbnailer crash issue.

---

### Post by harry332 on 2017-08-13
Rrnbtter,
I think the 3.24.3 in your pasted text means the gnome-shell version, not that of the gdm3.

---

### Post by rrnbtter on 2017-08-14
Greetings,
@harry332: Yes, 
rrnbtter@rrnbtter-110-15ISK:~$ apt-show-versions gdm3
gdm3:amd64/artful 3.24.2-1ubuntu9 uptodate
gdm3:i386 not installed

Thanks, I will get this sooner or later..... or not!

---

### Post by amano on 2017-08-17
Everything looks up to date now, even nautilus. Only some libraries like gdk-pixbuf or gegl are missing...

---

