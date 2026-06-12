---
title: "Can't run WINETools"
date: 2009-02-20
forum: Wine
---

### Post by pseudotheist on 2009-02-20
I'm trying to get a complete installation of WINE, and using the HOWTO thread for reference: [http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

I've installed winetools, but when I try to run it, I get an error that it can't find a library object: "/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

I've tried "getlibs -p  libgtk-1.2.so.0" but that doesn't find anything.  s there a specific site I need to add to my /etc/apt/sources.list file to get this library, or am I going about this completely wrong?  I think it's a library for a 32 bit OS, and I'm running 64 bit...

Any help would be great.

---

### Post by cogadh on 2009-02-21
Winetools is an incredibly outdated and unsupported application, plus you are using instructions that are three years old and really don't apply anymore. Getting a "complete" installation of Wine is as simple as using Add/Remove Programs or Synaptic Package manager and choosing the Wine package from the available packages. 

If you want to get the latest unstable (development) version of Wine, just follow the instructions here:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

