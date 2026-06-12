---
title: "Spectacular Crash - think it was the nouveax driver."
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by philinux on 2013-03-20
Was using dash to search and machine froze. Left it a while and then screen took on a pop art random look. 

Machine then rebooted. Not sure how to bug this but in kern.log was this.

Multiple entries of this Mar 20 14:58:13 philcb-desktop kernel: [ 3113.174777] nouveau E[  PGRAPH][0000:01:00.0]  ILLEGAL_MTHD
And then the following. Any advice how to bug this.
```
Mar 20 14:58:13 philcb-desktop kernel: [ 3113.174777] nouveau E[  PGRAPH][0000:01:00.0]  ILLEGAL_MTHD
Mar 20 14:58:13 philcb-desktop kernel: [ 3113.174786] nouveau E[  PGRAPH][0000:01:00.0] ch 2 [0x001fb13000] subc 7 class 0x8297 mthd 0x1230 data 0x00300180
Mar 20 15:21:19 philcb-desktop kernel: [ 4496.910820] nouveau E[   PFIFO][0000:01:00.0] DMA_PUSHER - Ch 2 Get 0x002002d814 Put 0x002002e00c IbGet 0x00000179 IbPut 0x0000017a State 0x40000004 (err: INVALID_MTHD) Push 0x00406040
Mar 20 15:21:37 philcb-desktop kernel: [ 4514.912011] [sched_delayed] sched: RT throttling activated
Mar 20 15:22:17 philcb-desktop kernel: [ 4554.972016] nouveau E[    1184] failed to idle channel 0xcccc0000
Mar 20 15:22:20 philcb-desktop kernel: [ 4558.168021] nouveau E[    2081] failed to idle channel 0xcccc0000
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
Mar 20 15:23:22 philcb-desktop kernel: imklog 5.8.11, log source = /proc/kmsg started.
```

---

### Post by mc4man on 2013-03-20
Just curious - 
if you only restarted/logged out _once_ since then in ~/.xsession-errors.old do you have something like
> nouveau: kernel rejected pushbuf: Cannot allocate memory
(if done more than once then .xsession-errors.old isn't any value anymore

---

### Post by philinux on 2013-03-20
> **mc4man said:**
> Just curious - 
if you only restarted/logged out _once_ since then in ~/.xsession-errors.old do you have something like

(if done more than once then .xsession-errors.old isn't any value anymore

Not got that error but a few of these on various apps. Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

Or could it be a Unity crash?

---

### Post by mc4man on 2013-03-20
> **philinux said:**
> Not got that error but a few of these on various apps. Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
Those are normal, from logging out/restart/shutdown
I guess your issue is diff from what I've seen with certain nvidia chipsets, using the Dash with the default option of active blur can on occasion lead to message I posted & unpredictable results graphically. 

As far your specific, (or thereabouts), I believe I've seen that in several bug reports  - here's a more recent one
[https://bugs.launchpad.net/ubuntu/+source/linux-lts-quantal/+bug/1097178](https://bugs.launchpad.net/ubuntu/+source/linux-lts-quantal/+bug/1097178)
or
[https://bugs.freedesktop.org/show_bug.cgi?id=54786](https://bugs.freedesktop.org/show_bug.cgi?id=54786)

(not to say the ^ is exactly your's..

---

### Post by philinux on 2013-03-20
Righto cheers for info. I changed driver now to 310 (propietary tested) see how that goes.

---

