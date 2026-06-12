---
title: "Computer hangs when trying to sleep after external monitor is connected or disconnect"
date: 2011-04-07
forum: System76 Support
---

### Post by mjumbewu on 2011-04-07
I posted this as a bug ([https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/753216](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/753216)), but wanted to check whether I was the only one with the problem, and that it's not system specific.

On my Lemur (with Maverick installed), suspend will stop working after I configure the machine to use an external monitor.  It does not matter whether I use multiple displays or mirror the same display onto both screens.  It also doesn't matter whether I disconnect the monitor or I disable the second display first.  I use gnome-display-properties to set up my screens.  In order to use the computer again I must force a reboot.

Steps to reproduce:
1) Boot computer
2) Connect external monitor (into VGA port)
3) Set up dual heads
4) Disconnect external monitor
5) Close the lid

Expected results:
- Computer goes into standby, as normal.

Actual results:
- Computer remains on and no longer responds to mouse or keyboard.  Fan also spins up.

Has anyone seen this before?  Any ideas?  Thanks.  Btw, by and large, great machine!

---

### Post by isantop on 2011-04-07
I can't say we're seeing any issues like that with our shop Lemur, but I'll do some testing. Is it a LemU2?

Also, try doing the same steps from a LiveCD. That will rule out any software problems.

---

