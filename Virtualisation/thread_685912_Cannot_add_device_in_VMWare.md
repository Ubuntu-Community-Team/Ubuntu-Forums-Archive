---
title: "Cannot add device in VMWare"
date: 2008-02-02
forum: Virtualisation
---

### Post by sheilnaik on 2008-02-02
This is a little odd, but for some reason my new VMWare Server installation won't let me add any devices other than the preinstalled ones.  I've attached a screenshot, where you can see that the Add button is grayed out and can't be clicked.  Any ideas as to what could be causing this?  I'm trying to add a sound device to get sound to work in XP, so that's why I'm asking about this.

---

### Post by sheilnaik on 2008-02-02
Never mind, I figured out the problem.  Turns out the virtual machine has to be powered off before any device changes can be made to it.  After adding the sound device, I initially had trouble getting it to work, but after I made sure all programs running in Ubuntu that used sound were turned (including YouTube videos), everything works perfectly.

VMWare is really, really, really cool.

---

