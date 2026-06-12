---
title: "several ltsp images"
date: 2009-10-20
forum: Server Platforms
---

### Post by guaka on 2009-10-20
I would like to be able to test with images while letting other thin clients boot from a relatively stable image.  (And since it's actually not that stable I want to try upgrading to 9.10 as soon as possible, but of course not without testing.)

Is it possible to have several images in /opt/ltsp/i386/, and if so, how?
I've looked into lts.conf and I was surprised to find out there's no option for this.

Kasper

---

### Post by guaka on 2009-10-28
I found this, on having multiple chroots through /etc/ltsp/dhcpd.conf: [https://lists.ubuntu.com/archives/edubuntu-users/2007-November/002593.html](https://lists.ubuntu.com/archives/edubuntu-users/2007-November/002593.html)

I'm still hoping there's an easier way though.

---

