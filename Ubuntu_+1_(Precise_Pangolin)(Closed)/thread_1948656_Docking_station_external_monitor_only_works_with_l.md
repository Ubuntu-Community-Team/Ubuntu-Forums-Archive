---
title: "Docking station external monitor only works with lid open"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by open.source on 2012-03-28
Im using ubuntu 12.04 with the Linux-x86_64, 295.20 nvidia driver and have disabled the internal laptop monitor through the nvidia settings utility, only enabling my NEC PA241w through display-port as a separate x screen. The monitor will display no-signal if booted with the laptop lid closed on the docking station, it works correctly if booted with the lid open. When the lid is open signal appears on the external monitor with the internal one disabled. With the lid closed there is no signal on both. This worked correctly with the 280.13 drivers, the new ones no longer work.

Can someone please help me with this?:p

---

### Post by open.source on 2012-03-30
Bump...   anyone.

---

### Post by open.source on 2012-04-09
Bump... anyone out there!

---

### Post by RLovelett on 2012-04-11
I have been trying the same things on my M6600 at work. I have run into this issue in addition to a number of others. Unfortunately, I'm starting to think this is not a supported configuration.

---

### Post by cariboo on 2012-04-11
Does your system automagically go to sleep, when you close the lid?

---

### Post by open.source on 2012-04-14
Yes, it automatically goes to sleep when I close the lid. No settings have been changed since ubuntu 11.10.

It won't boot to the external monitor with the lid closed even though the xorg.conf is set up to do this and has been working in ubuntu 11.10. If I boot with the lid open on the docking station it will disable the internal monitor and start my NEC as it is supposed to do. It just can't boot in this configuration with the lid closed and this is what I am trying to fix. I don't want dust in my laptop keyboard and it looks bad.

---

### Post by teraploppy on 2012-04-26
Same issue here.

Dell Latitude E6510.  
If I boot the laptop while in the dock with lid closed, Post shows on external.  Once post ends, the external monitor shutsdown and I must open the laptop in order to use the OS.

TL;DR Can only use laptop monitor and no external monitor with docking station.

---

