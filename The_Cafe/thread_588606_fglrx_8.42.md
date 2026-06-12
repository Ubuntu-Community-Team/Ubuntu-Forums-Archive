---
title: "fglrx 8.42"
date: 2007-10-23
forum: The Cafe
---

### Post by igknighted on 2007-10-23
[http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1)

Here it is folks.  I don't have an ATI card to test it out, any reviews from users?

---

### Post by Vansinnesvisan on 2007-10-23
I've been seeing some people from phoronix.com's forums say that it is slower than the open source driver. :( And a number are having video corruption.

---

### Post by dinxter on 2007-10-25
nice to have compiz up and running with fglrx. at the moment there seems to be a problem with displaying windowed video (in xine/totem/kaffeine/etc) but works fine in full-screen mode.
also problems with windowed opengl(?) in google earth, again, fine in full screen. everything else seems fast and fine, 8.42 also gets rid of the odd corruptions i was getting with 8.41

---

### Post by Mr. Picklesworth on 2007-10-25
Important thing to know: You can create a Debian package for Ubuntu, to prevent messing anything up. This is done by:
sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/gutsy
or sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/feisty
(Or whatever version you are running).
No need to run that as root.

This way, you can happily remove it. I was bracing myself for some ugly Windows-esque driver installation, but this remains quite tidy.

Unfortunately, I have some gross 8.41.7 remnants stowed away in some corners of the system. Luckily, they aren't in the way... (Famous last words).

---

### Post by hagabaka on 2007-10-31
> **Mr. Picklesworth said:**
> Important thing to know: You can create a Debian package for Ubuntu, to prevent messing anything up. This is done by:
sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/gutsy
or sh ati-driver-installer-8.42.3-x86.x86_64.run  --buildpkg Ubuntu/feisty
(Or whatever version you are running).
No need to run that as root.



I did this on Ubuntu Gutsy and installed the generated xorg-driver-fglrx_8.42.3-1_i386.deb, but when I run fgl_glxgears, first I got 
> fgl_glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

I made a symlink /usr/lib/libGL.so.1 => /usr/lib/libGL.so.1.2 (which is installed by this package); fgl_glxgears opens a window, but immediately quits, outputing
> Using GLX_SGIX_pbuffer
zsh: segmentation fault  fgl_glxgear

Update:

I used the installer directly, and now the driver works. Maybe a bug in the package builder?

---

