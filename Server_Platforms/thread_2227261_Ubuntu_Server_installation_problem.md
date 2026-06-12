---
title: "Ubuntu Server installation problem"
date: 2014-05-31
forum: Server Platforms
---

### Post by germ65 on 2014-05-31
Hello,
I am trying to install Ubuntu Server 14.04 LTS on an Atom 330 machine. Downloaded the installer (ubuntu-14.04-server-i386.iso) and created USB stick from .iso. (This was done on OS X, following instructions here: [blog.tinned-software.net/create-bootable-usb-stick-from-iso-in-mac-os-x/]("blog.tinned-software.net/create-bootable-usb-stick-from-iso-in-mac-os-x/")). Installing on empty 32 GB SSD PATA drive. I got as far as when the installer copies files to disk. However, in the middle of this copying process, I get the following message:

Please insert the disc labeled: 'Ubuntu-Server 14.04 LTS _Trusty Tahr_ - Release i386 (20140416.2)' in the drive '/media/cdrom/' and press enter.

I have a choice of <Continue> or <Go Back>

Of course, I have no CD-ROM drive and this message does not make any sense. Both choices bring me back to the same point. I am stuck. What is going on?

One more thing, during "loading more component files from CD-ROM", I got error several times, but I could hit Continue and it would proceed until finished.

---

### Post by germ65 on 2014-06-01
Solved: it was a bad USB stick. Just tried another one and now it installs fine. No more errors when "loading additional components".

---

