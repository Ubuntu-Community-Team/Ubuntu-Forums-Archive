---
title: "quad -&gt; six core : ? performance boost ?"
date: 2010-05-03
forum: Virtualisation
---

### Post by Beowulf.1000 on 2010-05-03
Anybody upgraded from a tri or quad core to a six or eight core and notice any change in virtualization performance? I tried virtualization with virtualbox (and vmware) with my quadcore system, performance was borderline for apps I needed (running Windows XP inside of Ubuntu 9). But I just ordered a six core cpu to upgrade my system, it will arrive in a couple of days, so I am curious if this should help with virtualizatio? I am getting the just released AMD six core CPU.  Can I expect a noticeable boost in performance for virtualbox and Windows apps running in it?

---

### Post by robvas on 2010-05-05
You will have to view your performance stats while you are running big workloads. Are you maxing out RAM? Heavy disk activity? Pegging all your CPU's?

It is usually the disk subsystem that starts to fall behind first. If you are using virtualbox I would guess that you are running a desktop PC with a single SATA hard drive.

---

### Post by javyn999 on 2010-06-17
Sorry for the late reply but how is that 6 core working for you?  

I wouldn't have thought it would make a difference, since a VM is just going to be on one core anyway isn't it?

---

