---
title: "Ubuntu Server + Monitorless HP server"
date: 2006-08-25
forum: Server Platforms
---

### Post by StianH on 2006-08-25
I've got this three year old server that has a VGA chip on the MB, but for some reason it's blown. The server takes only 64bit PCI cards, and no AGP, so I am having trouble finding any graphics card that I can use without ordering it online.

Does anyone have a suggestion for installing Ubuntu Server when I do not have a monitor, so the only way would be to control the installation over SSH or some other way from a remote computer.

I was thinking this might be achieved by running the regular Ubuntu 6.06 installer and somehow get vnc running so I could connect to the vnc session and start the installer from my laptop, however I am unshure about how I would go about doing that.

Any suggestions or tips, other then getting a hold of a PCI64 VGA card?

---

### Post by Uluen on 2006-08-25
Real servers doesn't need monitors :)
Did you try booting it without keyboard with a serial console to it?

---

### Post by StianH on 2006-08-25
Well, I don't have a serial console :/ Or rather, have no serial cable or way of getting one.

---

### Post by Uluen on 2006-08-25
Something like [this]("http://www.komplett.no/k/ki.asp?sku=100171")?

Why can't you use standard PCI card? I can in my 64/66 slots (I think :)

---

### Post by StianH on 2006-08-25
I can't use a regular pci card due to that there's an extra "slit" in the slot, or whatever :P Explainatory lines below:

Regular PCI slot:

___________________ _______


PCI slot on my server:

___ _______________ _______ _______



I startet thinking about using a hacksaw on a card to make it fit, but I think I'll resist the urge.

---

### Post by backu on 2006-08-30
Without any sort of Video on the server, your up a creek. I find it interesting that the MB has only PCI64 on it though.

---

### Post by StianH on 2006-08-31
Yeah, but I guess they didn't expect you to make the onboard vga card go byebye. I just found some specs @ HP for this line of servers:

[http://h18003.www1.hp.com/products/quickspecs/11614_div/11614_div.html](http://h18003.www1.hp.com/products/quickspecs/11614_div/11614_div.html)

I was thinking, could there possibly be a way to make a CD that just automatically installs?

---

### Post by Uluen on 2006-08-31
Ah, they're 33MHz slots.
It should be possible to make a boot CD/memorystick/whatever that brings up a serial port I guess, PXE boot perhaps?

Maybe put the disk in another computer, install minimal server, configure SSH server, put the disk back and finish installing via SSH?

---

### Post by backu on 2006-09-01
Just thinking that myself Uluen.

Through all my installs of *nix, there's always been a minimum of user interaction required during install.

---

### Post by spartas on 2006-09-02
If you've got another system with the same arch you can install the os on the drive and then pop it into the server and see if it will boot.

---

