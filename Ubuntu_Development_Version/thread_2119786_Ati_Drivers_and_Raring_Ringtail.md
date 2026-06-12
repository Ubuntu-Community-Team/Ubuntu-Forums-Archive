---
title: "Ati Drivers and Raring Ringtail"
date: 2013-02-24
forum: Ubuntu Development Version
---

### Post by garginis on 2013-02-24
There are many people with old  ATI graphics cards (HD <5000 series), and i'm one of those (HD 4670).I would like to ask what we can expect in ubuntu 13.04?In 12.10 there was some fix with downgrading x server to 1.12 and installing ati legacy drivers.But what to expect in 13.04?Will i be able to use 13.04 wihout graphics problems?

Cheers, Dragan

---

### Post by Yellow Pasque on 2013-02-25
> Will i be able to use 13.04 wihout graphics problems?
With the open-source radeon driver, yes. 3D performance won't be as good as the proprietary driver, so if you're a gamer, that may be an issue.

Don't expect ATI/AMD to update their legacy driver for compatibility with newer X or kernels.
Stick with 12.04 if you want to run proprietary drivers.

---

### Post by garginis on 2013-02-25
As i thought..
I'm not a gamer.I've kernel version 3.5.25.
I tried to install proprietary driver on 12.04, but it breaks my unity.
AMD says that proprietary 13.1 driver is for kernel version up to 3.4.Is this a problem?

Cheers, Dragan

---

### Post by bbdimitriu on 2013-03-19
The Open Source drivers do seem to generally work, but they tend to heat up my laptop big time and the battery drains like crazy (last time I tried them was when 12.10 was released). It's a shame the proprietary drivers hit a dead end...
Maybe things look batter in 13.04?

---

### Post by balloons on 2013-03-20
> **bbdimitriu said:**
> The Open Source drivers do seem to generally work, but they tend to heat up my laptop big time and the battery drains like crazy (last time I tried them was when 12.10 was released). It's a shame the proprietary drivers hit a dead end...
Maybe things look batter in 13.04?

I'm on a desktop, on the open drivers, but I also have a HD6xxx card, so I'm not legacy.. Everything just works on the open drivers, and I've no complaints in 13.04.

---

### Post by xaliqen on 2013-03-21
> **guitara said:**
> I'm on a desktop, on the open drivers, but I also have a HD6xxx card, so I'm not legacy.. Everything just works on the open drivers, and I've no complaints in 13.04.

Until very recently, I'd be right there with you in recommending the open drivers.  At the moment though, the proprietary drivers still have an edge in game performance.  Of course, this is only relevant if you play games.

I am interested in playing games every once in awhile, and, now that Steam is available for Linux, it's somewhat bitter since my laptop uses the 4000 series (e.g. 'legacy').  For people with the legacy GPUs, it might be wise to consider sticking with Precise.  Of course, if AMD releases legacy drivers compatible with newer versions of X-Server, it would change everything.

It's likely there will be a repository with drivers patched for 3.8+ kernels, and you can already get Raring builds of X-Server 1.12 from the makson96 repo (which is where I'd put money on patched drivers showing up at some point).  If you absolutely must run Raring, then using a specialized PPA like this will be an easy solution (once it's available), similar to how it works in Quantal.

---

### Post by ogyct on 2013-03-31
I have bought my laptop 3 years ago, I have 4570 card, and now it's support is gone. I also have geforce 6600 gt on my home pc, NVIDIA still supports it with new drivers. I guess it's obvious what to chose, when buying new pc.

---

