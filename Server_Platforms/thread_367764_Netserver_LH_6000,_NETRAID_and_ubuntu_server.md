---
title: "Netserver LH 6000, NETRAID and ubuntu server"
date: 2007-02-22
forum: Server Platforms
---

### Post by kaltsi on 2007-02-22
I can't install ubuntu server to this hp server :(
Ubuntu can't hand drives.

What can I do??

---

### Post by RX7Godfather on 2007-02-27
Seems like a lot of us are having issues with NetRaid SCSI cards in HP Servers installing Ubuntu.

No one appears to have an answer yet and I personally haven't seen anyone from the Ubuntu Team out here answering any.

Hopefully someone will soon.

---

### Post by RX7Godfather on 2007-02-27
OK, I may have found an answer, at least it is working for my NetRAID 1Si SCSI controller.

You need to enter the bios of your scsi card, usually Ctrl+M while booting, locate somewhere in your scsi config utility the emulation section, you may have to dig for it, I know I did....

Change your SCSI emulation from I20 to MASS STORAGE, erase your array (you will lose everything on your drives) and rebuild and initialize it. This way Ubuntu will not see multiple installations and will erase the entire disks.

After doing that, try to install it again, so far it is working with my NetRAID 1Si controller.

Hope this helps...

---

