---
title: "Installing packages DESTROYS my VM"
date: 2018-05-30
forum: Virtualisation
---

### Post by alek-dev on 2018-05-30
Depending on the package, installing some packages through apt can completely destroy my VM. This means I can't open anything including terminal. Some of these packages include:

gtk-doc-tools
xorg-dev
libgdk-pixbuf2.0-dev
libpango1.0-dev

Now the strange thing is - apt update and apt upgrade can do the same thing depending on what packages I have previously installed.


I'm assuming it's a combination of packages that are in conflict which causes this issue, however its the SAME, EXACT issue of not being able to open anything. I've started taking routine snapshots, but I'd prefer figuring out the problem.

---

### Post by alek-dev on 2018-05-30
Edit: It seems to be one of these packages thats absolutely destroying the machine (manual installs). Unfortunately all of these were downloaded from their official sites, so something isn't compatible with the new 18.04 version:



libffi ([ftp://sourceware.org/pub/libffi](ftp://sourceware.org/pub/libffi))
libpcre ([https://www.pcre.org](https://www.pcre.org))
zlib ([https://zlib.net](https://zlib.net))
glib (./configure --with-pcre) <- V2.56
gobject-introspection <--- linuxfromscratch
atk 
libpng [https://ftp-osl.osuosl.org/pub/libpng/src](https://ftp-osl.osuosl.org/pub/libpng/src)
pixman (cairographics.org/releases)
cairo (cairographics.org/releases)
libuuid  (e2fsprogs.sourceforge.net), libuuid is part of e2fsprogs package
FreeType ([https://www.freetype.org](https://www.freetype.org))
harfbuzz
fontconfig ([https://www.freedesktop.org/software/fontconfig/release](https://www.freedesktop.org/software/fontconfig/release))
libtiff
gdk-pixbuf  (linux from scratch) 
fribidi (linux from scratch)

---

### Post by monkeybrain20122 on 2018-05-30
?? Are you running Ubuntu as the host or the guest in the VM?? Why are you downloading packages from source? Did you compile them? 

Please give some context to your question if you need help.

---

