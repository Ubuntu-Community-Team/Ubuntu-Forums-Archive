---
title: "Make installed on server?"
date: 2007-06-06
forum: Server Platforms
---

### Post by chimerical_brio on 2007-06-06
I just did an install of Ubuntu-server onto a computer using a disk I've done other installs with. With this install, make was not installed, and i'm told that to install it to type "sudo apt-get install make." I need make so that I can install NDISwrapper so that I can get online with my USB adaptor, but when I install make through the .deb file available off the Ubuntu site, it has an error. Should make be installed? I don't think I've had problems whenever I installed off this disk in the past...

Henry

---

### Post by chimerical_brio on 2007-06-06
...bump...

---

### Post by bukwirm on 2007-06-06
Try installing the "build-essential" package - it installs most of the stuff that is needed to compile programs.

---

### Post by chimerical_brio on 2007-06-07
So I'm assuming that build-essential is on the install disk. How do I mount the disk and then use apt to get at build-essential? Thanks.

---

### Post by chimerical_brio on 2007-06-07
Alright, I managed to get build-install installed off of the cd, then I brought ndiswrapper-1.46.tar.gz over via my USB drive, ran "tar xvzf ndiswrapper-1.46.tar.gz", cd-ed into the directory, ran "make distclean", no problem. But, then I run "make" and get the error
```
Can't find kernel build files in /lib/modules/2.6.20-15-server/build;
give the path to kernel build directory with
KBUILD=<path> argument to make
```
Any ideas? What's going wrong? Thanks.

---

### Post by conjur3r on 2007-06-08
Have you also got the kernel sources installed?

# sudo apt-get install linux-headers-`uname -r`

---

