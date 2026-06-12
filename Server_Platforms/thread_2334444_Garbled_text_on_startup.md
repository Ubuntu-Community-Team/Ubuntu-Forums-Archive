---
title: "Garbled text on startup"
date: 2016-08-19
forum: Server Platforms
---

### Post by fatgeek on 2016-08-19
I'm having an issue with my Ubuntu Server 16.04 installation. I have it running on a Zotac Z-Box CI23 Nano. It installed fine, but on its first boot all I had was a blank screen. I edited ```
/etc/default/grub
``` and changed ```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

This let me see the startup, but the text is all garbled white blocks:

[IMG]http://i.imgur.com/pCUswXr.jpg[/IMG]

I first thought it might be a bad cable, so I switched cables with no change. I changed monitors with no effect. I switched to a TV using HDMI with no effect.

Any ideas would appreciated.

---

### Post by fatgeek on 2016-08-21
No one?

---

### Post by howefield on 2016-08-21
Not sure that it will help but I have moved your thread to the "*Server Platforms*" forum. Some of the experts who frequent this forum may have some suggestions.

---

### Post by Graham_Willis on 2016-08-21
Did this machine work correctly with any other OS?
The ideas presented in [http://askubuntu.com/questions/98294/ubuntu-server-11-10-boot-white-terminal-with-garbled-black-text](http://askubuntu.com/questions/98294/ubuntu-server-11-10-boot-white-terminal-with-garbled-black-text) may prove worth trying.

---

### Post by fatgeek on 2016-08-22
> **Graham_Willis said:**
> Did this machine work correctly with any other OS?
The ideas presented in [http://askubuntu.com/questions/98294/ubuntu-server-11-10-boot-white-terminal-with-garbled-black-text](http://askubuntu.com/questions/98294/ubuntu-server-11-10-boot-white-terminal-with-garbled-black-text) may prove worth trying.

No, I tried Ubunru 14.04, 16.04 and Debian 8. Both Ubuntus had the issue noted above. Debian installed OK, then crashed whenever I tried to boot it. 

I put in an RMA request for the machine and the new one should be here tomorrow. I'll report back if it was just bad hardware.

---

### Post by fatgeek on 2016-08-22
I finally got this figured out. At first I thought it was bad hardware so I RMA'd the machine. The same exact thing was happening on the replacement. So I spent a few hours fiddling with grub settings. This is what ended up working for this machine:

in /etc/default/grub:

Comment out GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" entirely.

Uncomment GRUB_TERMINAL=console

Uncomment GRUB_GFXMODE=640x480 I set it to GRUB_GFXMODE=1280x800 because that's the monitor I'm using's default.

Save it then `sudo update-grub` and reboot and it is showing as expected. Only the combination of those three changes seem to make it work for me, but YMMV.

---

