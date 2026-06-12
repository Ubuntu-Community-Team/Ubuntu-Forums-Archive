---
title: "Getting x11 dev stuff install"
date: 2005-04-22
forum: Repositories &amp; Backports
---

### Post by lpsantil on 2005-04-22
I'm a n00b to Ubuntu and I'm trying to figure out how to get the all the dev stuff for X11.  I tried apt-get install xlibs-dev / xlibs-static-dev / libx11-dev / etc., and I'm getting nowhere fast.   I have some simple X11 code that's failing because it can't find X11/X11.h (which should have been installed with xlibs-dev but only libX11.so is installed).

Thanks,
lpsantil

PS - BTW, is there a package for Eclipse?

---

### Post by p!=f on 2005-04-22
```

sudo apt-get install x-dev x-window-system-dev

```
should do the trick. :)

---

### Post by lpsantil on 2005-04-22
[QUOTE=p!=f]```

sudo apt-get install x-dev x-window-system-dev

```
should do the trick. :)[/QUOTE]

Ahh...I finally understand what was happening.  I didn't have the right repositories uncommented in my /etc/apt/sources.list file.  Man, took me several hours to find that solution in [Dev Howto](http://www.ubuntulinux.org/wiki/DevelopingPreparation#preparing-your-ubuntu-system-for-software-development).  After I uncommented updates, all the packages I was looking for showed up.

lpsantil

---

### Post by John Francis Lee on 2007-08-03
I've followed the steps outlined but 
 jfl@ws1:~$ sudo apt-get install x-dev x-window-system-dev
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 Package x-dev is not available, but is referred to by another package.
 This may mean that the package is missing, has been obsoleted, or
is only available from another source
 E: Package x-dev has no installation candidate

what do I do from here? I'm new to debian/ubuntu and I've got to admit that a linux system with NO development facilities, coupled with the apt-get system, wherein you guess what the name of the package you need might be, is making me hate it a lot!

---

