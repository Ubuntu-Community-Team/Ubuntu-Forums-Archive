---
title: "Virtualbox - /etc/init.d/vboxdrv setup fails"
date: 2013-10-30
forum: Virtualisation
---

### Post by UBigmac on 2013-10-30
The basics:
Running Ubuntu Server 12.10 on Asus AMD64 w/16 Gbyte memory & Virtualbox 4.3.  This was an upgrade from 12.04 & 4.2

Note:  Virtualbox and all my guest OS's worked under 12.04

Virtualbox comes and lists all my guest OS's.  If try to start any of them there's a popup indicating the 'kernel driver is not installed' and run /etc/init.d/vboxdrv setup

So I run that command, but that fails with 'Your kernel headers for kernel 3.8.0-32-generic cannot be found'

So I ran uname -r which returned 3.8.0-32-generic

If I run apt-get install linux-headers-3.8.0-32-generic there is an error 'Package linux-headers-3.8.0-32-generic is not available, but is referred to by another package'

I've tried deinstalling/reinstalling Virtualbox but get same error when I attempt to start any of the guest OS's.

How do I resolve this?

I'm more of a Wintel guy that plays with linux...meaning I have no in depth knowledge of linux

Bigmac

---

