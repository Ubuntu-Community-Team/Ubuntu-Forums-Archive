---
title: "Can someone please explain to me the significance and use of pkgcon?"
date: 2009-02-01
forum: The Cafe
---

### Post by kevdog on 2009-02-01
I found mention of pkgcon on Distrowatch, specifically for Ubuntu.  What exactly does this utility do, and why would I use it over apt/aptitude?

---

### Post by vikramaditya on 2009-02-02
Lifted from [http://linux.softpedia.com/get/Programming/Compilers/pkg-config-2739.shtml](http://linux.softpedia.com/get/Programming/Compilers/pkg-config-2739.shtml) - plagiaristically yours, VK

> pkg-config description   
 
 
pkg-config is a system for managing library compile/link flags that works with automake and autoconf.
pkg-config is a helper tool used when compiling applications and libraries. It helps you insert the correct compiler options on the command line so an application can use gcc -o test test.c `pkg-config --libs --cflags glib-2.0` for instance, rather than hard-coding values on where to find glib (or other libraries). It is language-agnostic, so it can be used for defining the location of documentation tools, for instance.

The program free software and licensed under the [WWW]GPL version 2 or any later version (at your option).

pkg-config works on multiple platforms: Linux and other UNIX-like operating systems, Mac OS X and Windows. It does not require anything but a reasonably well working C compiler and a C library, but can use an installed glib if that is present. (A copy of glib 1.2.8 is shipped together with pkg-config and this is sufficient for pkg-config to compile and work properly.)

The first implementation was written in shell, by James Henstridge. Later, it was rewritten in C by Havoc Pennington. It also grew an autoconf macro written by Tim Janik, later rewritten by Scott James Remnant.

---

### Post by kevdog on 2009-02-02
When would I use this? and I do compile!

---

