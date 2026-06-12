---
title: "32 bit libs on a 64 bit server"
date: 2014-06-29
forum: Server Platforms
---

### Post by Lou_Kitz on 2014-06-29
Hello,

Is there an easy way to install all the 32 bit libs on my 64 bit 14.04 server?  I'm trying to install a 32 bit program (America's Army 2.5) but I keep getting lib missing errors.

---

### Post by TheFu on 2014-06-30
It appears that the old 32libs package is gone in 14.04.  Google found this: [http://askubuntu.com/questions/454253/64bit-ubuntu-14-04-running-32bit-binaries](http://askubuntu.com/questions/454253/64bit-ubuntu-14-04-running-32bit-binaries) which provides an alternative method.
```
sudo apt-add-architecture i386
``` seems to be the trick, then update - of course, installing .deb files directly will break the dependency stuff - if not today, eventually and the system will end up in "APT hell."

---

