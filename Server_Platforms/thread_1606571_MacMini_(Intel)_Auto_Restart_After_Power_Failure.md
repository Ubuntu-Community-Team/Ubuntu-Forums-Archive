---
title: "MacMini (Intel) Auto Restart After Power Failure"
date: 2010-10-26
forum: Server Platforms
---

### Post by stantonbond on 2010-10-26
Running Ubuntu Linux 8.04.3 on an Intel Apple Mac Mini server. I'm finding that the device will not automatically power itself back on following a power failure. The Apple OS provides a preference setting for "automatically power on computer after power failure." Is there such an option with Ubuntu?

Additionally, I'm finding that Ubuntu Linux 8.04.3 boots up far more reliably if a monitor is connected than if it is not. Do I need a dongle of some kind to simulate a monitor connection when the device is in a server rack and connected monitor is not an option?

---

### Post by arrrghhh on 2010-10-26
Well if there's no monitor connected at boot, Ubuntu has no clue how to setup the screen.  You can force values in GRUB.  Are you running X?  You can also force the values in xorg.conf.

As for the automatic reboot, I thought there was a BIOS setting for that... Alas, you have no BIOS :p  I am not aware of a automatic power up after failure, although I would be curious about it because my server does the same thing, and I do not have the option in my BIOS.

---

