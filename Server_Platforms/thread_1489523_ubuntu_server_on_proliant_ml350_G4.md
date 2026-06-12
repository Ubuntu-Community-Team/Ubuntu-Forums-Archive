---
title: "ubuntu server on proliant ml350 G4"
date: 2010-05-21
forum: Server Platforms
---

### Post by eduardoavdr on 2010-05-21
Hi Everyone,

I have been given the task to change OS of a HP Proliant ML350 G4 server, and I decided to use Ubuntu server edition for that matter.

The thing is that the server has already installed Windows server 2000 on the only Hard drive it has (SCSI).

My question is, could I install an IDE HD on the IDE connection it has and install ubuntu without overwritting the boot configuration, so if I wanted to go back to the windows 2000 server installation with no problems?

It also has a tape drive which is used for backups. Do you guys know how ubuntu deals with such devices?

---

### Post by cariboo on 2010-05-22
The answer to your questions is yes, except for one thing, the server edition has a hard time recognizing SCSI cd-rom drives, if you can connect a ide cd-rom drive, or boot from usb, your installation will work with zero problems.

---

