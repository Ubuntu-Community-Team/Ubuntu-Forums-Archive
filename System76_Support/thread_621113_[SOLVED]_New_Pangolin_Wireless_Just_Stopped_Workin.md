---
title: "[SOLVED] New Pangolin Wireless Just Stopped Working"
date: 2007-11-23
forum: System76 Support
---

### Post by georgedonnelly on 2007-11-23
I just bought a new pangolin, the wireless was working great. Then I used it on a wired network in a hotel for a few days. I am back home now and I can not get it to work.

This is a Pangolin running 7.10 and I am sure I have not applied any updates. I installed xubuntu-desktop and some other apps and this was working fine before both on gnome and xfce but now won't work on either. 

uname -a gives Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

The system76 Drive panel says:

System Name: Serval Performance
System Model: serp3

i tried restarting a few times, tried restarting nm-applet. The hardware information panel sees the wireless card but ifconfig only shows eth2 and lo, so the wireless ifs are not being seen at all.

I searched around in all the right places but didn't find anything.

Thanks.

---

### Post by georgedonnelly on 2007-11-23
LOL!

There is a manual wifi on-off switch at the front left of the machine.

I found this thanks to:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg548670.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg548670.html)

I switched this to on and the wifi immediately came back.

:lolflag:

---

