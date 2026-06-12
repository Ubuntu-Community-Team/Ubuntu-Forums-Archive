---
title: "Install vmware tools on Ubuntu 7.10 guest problem"
date: 2008-02-19
forum: Virtualisation
---

### Post by optimizer on 2008-02-19
Install vmware tools on Ubuntu 7.10 guest problem
Workstation 5.5, XP host, Ubuntu 7.10 guest

I installed gcc-3.4
and did an export CC=/usr/bin/gcc-3.4
CPP looks like it's already installed.

The config routine wants to install in /usr/src/linux/include

I have what looks like linux headers file in /usr/src

I tried /usr/src but the config routine is looking for a "linux" file or folder in it.
I tried the linux-hearers-2.6.22-14 (or whatever it was), but it didn't like it either.

Even if I get through all this it's going to bomb out with the "detected x.org" abort.

Has anyone else had problems installing tools on Ubuntu 7.10?

---

### Post by PmDematagoda on 2008-02-19
This thread has been moved to the Virtualisation section.

---

### Post by optimizer on 2008-02-20
I noticed another post that appeared to be trying to solve the same kind of problem except a few years ago, so I tried a few of the steps:
[http://ubuntuforums.org/showthread.php?t=27303&goto=nextoldest]("http://ubuntuforums.org/showthread.php?t=27303&goto=nextoldest")

cd /usr/src
ln -s linux-headers-2.6.22-14 linux
cd /usr/src/linux
make

it procduced errors and warnings, starting out looking like this:

HOSTCC scripts/basic/fixdep

scripts/basic/fixdep.c.107:23: error: sys/types.h no such file or directory
and lots more of them...

I set the 3.4 compiler based on some other threads, so unsure if I should be using an older compiler.

The instructions I read said do a "make install", but there was no install file to make, so i just did a "make" like the errors suggested at that time.

I need some help from someone with Workstation 5.5 that has been doing linux-header builds and knows the problems, and might also know why I'm getting the "detect x.org" message.

Thanks

---

### Post by karel1980 on 2008-08-21
If you are missing sys/types.h and other sys header files,
you probably need to install the libc6-dev package.

---

