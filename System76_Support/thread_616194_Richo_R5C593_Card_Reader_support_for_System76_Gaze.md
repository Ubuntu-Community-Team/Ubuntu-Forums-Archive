---
title: "Richo R5C593 Card Reader support for System76 Gazelle 2300"
date: 2007-11-17
forum: System76 Support
---

### Post by rmemm on 2007-11-17
Regarding the Richo R5C593 Card Reader support in the Gazelle 2300.  Mine has never worked.  Is this suppose to work?  If so how?

I'm just not sure what direction to take here -- I've seen posts that say a later kernel supports this device?  I've also seen some drivers on sourceforge that might?  I've also seen something called the System76 Driver which my system does not seem to have?

So what's the best way to get support for this in the Gazelle 2300.  By the way I'm interested in SD card support, and I current still have Dapper.

Rob

---

### Post by thomasaaron on 2007-11-19
How does it work:

Typically, if you insert an SD card into it, it should auto-mount and cause an icon to appear on your Desktop.

To see if it is doing *anything*, go to a terminal and enter this command: tail -f /var/log/syslog

Then insert a card and see if anything is added to the log (and post it here). If nothing is added to the log, it is probably not working at all.


I *think* that model card reader is working under Gutsy.

---

### Post by rmemm on 2007-11-19
Thanks.  I tried that.  It actually is seen by the system, but no mounting operation happens.  Actually get:

> pccard: PCMCIA card inserted into slot0
pcmcia: resgistering new device pcmcia 0.0

Nothing else happends.  Then when you eject the crad you get:

> pccard: card ejected from slot 0.

So it at least knows about the device.  

The other interesting thing -- the USB plug beside the card reader does not work either.  That is the one beside the reader and under the PCMCIA slot.  Is this somehow related?

The other 2 USB slots on the other side of the computer have always worked find.  Don't know if the one near the reader ever worked.  I tested this with a usb flash drive -- kind of like there is no power to it.

Anyway -- there seems to be something strange about the whole cluster -- PCMCIA, SD Reader, and USB Plug slot.

If it's an OS version thing -- I think I'd wait until Ubuntu 8 -- once they get the LTS release sorted out.  I like the 3 year cycle myself.  On the other hand, if I can easily fix this now -- I would.

Thoughts?

Rob

---

### Post by thomasaaron on 2007-11-19
1. How is the sd card formatted? Palm device? There are several filesystem types that card readers don't recognize under Ubuntu.

2. As for the USB port, get a known good USB device and plug it in. Use the same command I gave you above to see if it is registering any messages.

---

### Post by rmemm on 2007-11-19
Flash card, I assume formated with FAT.  It has images on it from a CANNON PowerShot A570IS camera.  The other strange thing -- on the logs -- the card is recognized to a point -- but no sd* device is assigned to it.  When you mount a USB flash drive on one of the 2 USB rigth side ports you get a lot more messages including allocation of an sd* device.  Seems kind of like the base insert events are known, but no block device gets setup.

Regarding USB port.  I did try it with a Flash Drive that is known to work.  Works great on the 2 right side ports, does nothing on the left port -- green light on drive does not light, no log messages at all on the system log.  Not that important to me really -- other than one would think this should work.  Also wondering if this was somehow correlated to the flash drive issue.  Other thing that is strange, on the port on the left side near the card reader I have to put the flash drive in upside-down.  Seems like the port plug is flipped.  Other question -- is there such a thing as an unpowered USB port -- presuambly a flash drive needs power?

The reason I'm insterested in the card reader port is that we just purchased the camera and it would be handy to just be able to stick in the flash cards without having the plug-in the camera all the time.

Rob

---

