---
title: "change display drivers for xorg.conf when dual booting instead of launching VM guest?"
date: 2008-11-19
forum: Virtualisation
---

### Post by garnwraly on 2008-11-19
I like the guest additions for virtualbox, but the additions change the xorg.conf file's screen driver to vboxvideo, so when i boot it natively the graphics are all messed up and i have to edit the xorg.conf and change it to the nvidia driver and restart, which is really annoying because i'd have to undo that when i boot the system in virtualbox again.

Is there a way to have linux detect whether i'm running it in a VM during boot and from there decide what driver to use in xorg.conf?

---

