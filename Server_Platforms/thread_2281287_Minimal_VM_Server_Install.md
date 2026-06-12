---
title: "Minimal VM Server Install"
date: 2015-06-05
forum: Server Platforms
---

### Post by Dale_Start on 2015-06-05
Hi folks,

I'm trying to do a minimum server install of Ubuntu Server 14.04.2 LTS in a VM on Hyper-V Server 2012 R2. I've seen some guides instructing to press F4 at the language selection screen, but F4 doesn't seem to be an available choice when I boot my VM from the ISO I downloaded from [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server). Was this option removed from Ubuntu at some point?

---

### Post by Tadaen_Sylvermane on 2015-06-06
Just run the install all the way through. It will do what it needs. When it asks you which software to install, don't select anything and finish it up. As minimal as it gets.

---

### Post by TheFu on 2015-06-06
> **Dale_Start said:**
> Hi folks,

I'm trying to do a minimum server install of Ubuntu Server 14.04.2 LTS in a VM on Hyper-V Server 2012 R2. I've seen some guides instructing to press F4 at the language selection screen, but F4 doesn't seem to be an available choice when I boot my VM from the ISO I downloaded from [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server). Was this option removed from Ubuntu at some point?

There is a mini-install these days. google found it for me on an ubuntu hosted site.  It is not the normal "server" ISO.  I installed it a few weeks ago and got to struggle to get it to load many normal drivers manually - like for networking - because I asked it to only load the drivers specific to my system. That didn't work out too well.  Had to go back and re-reinstall again, asking for all the kernel drivers the next time attempt to get any networking at all.  OTOH, it was pretty small on disk - relative to std server installs. It leaves out all sorts of things most people want on their server. Sadly, it still included nano. But resolvconf was gone, which did make me happy.  Initially, I think it was 800MB on disk, so much smaller than the 2+G of a normal "server" install.

I vaguely recall having to know which kernel version I needed. The choices were not intuitively obvious, so be certain you can look up answers during the installation.

---

### Post by houstonbofh on 2015-06-06
You might want to look at Ubuntu MinimalCD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and Ubuntu Core. [https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core)

It depends on what you need that the traditional server install is not doing.

---

