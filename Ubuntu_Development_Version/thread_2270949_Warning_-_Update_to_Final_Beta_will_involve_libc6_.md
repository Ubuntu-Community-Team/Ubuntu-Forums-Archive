---
title: "Warning - Update to Final Beta will involve libc6 upgrade from 2.19 to 2.21"
date: 2015-03-26
forum: Ubuntu Development Version
---

### Post by syntaxerror74 on 2015-03-26
As libc6 is the system's **achilles heel**, I thought it would be a good idea to WARN people before doing an upgrade to Final Beta of 15.04. When the core C library is upgraded, this will often mean that the whole base system has to be upgraded as well because of significant internal changes (e. g. entry points) affecting the inner workings of libc6.
So if you only have one machine, think twice perhaps. :)
While my installation survived the upgrade with flying colors, this does not necessarily mean it will on other people's 'Buntu boxes.

---

### Post by dino99 on 2015-03-26
everything is ok, no drama, no pain ):P

---

### Post by syntaxerror74 on 2015-03-26
:)
Hmm, is my memory so fuzzy, or wasn't it so that from Utopic to Trusty, the xy in the 2.xy libc6 version always stayed the same, merely the patch level changed? Well, I seem to remember it was both 2.19, and 2.17 was even PRE-14.04...

---

### Post by VMC on 2015-03-29
Wasn't sure what to look out for. In the past I do recall some error message regarding out of date or wrong version, but after looking at package I see why:
```
$ dpkg -s libc6
Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 10568
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: glibc
Version: 2.21-0ubuntu4
Replaces: libc6-amd64
Depends: libgcc1
Suggests: glibc-doc, debconf | debconf-2.0, locales
Breaks: hurd (<< 1:0.5.git20140203-1), libtirpc1 (<< 0.2.3), lsb-core (<= 3.2-27), nscd (<< 2.21)
Conflicts: prelink (<= 0.0.20090311-1), tzdata (<< 2007k-1), tzdata-etch
Conffiles:
 /etc/ld.so.conf.d/x86_64-linux-gnu.conf 593ad12389ab2b6f952e7ede67b8fbbf
Description: GNU C Library: Shared libraries
 Contains the standard libraries that are **used by nearly all programs** on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
```

---

### Post by syntaxerror74 on 2015-04-13
No surprising news bud. :) Breaking libc6 *does* imply breaking the whole system. (But wait, oh yes vi still works. (yippieh!\\:D/))

---

