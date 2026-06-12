---
title: "Flashdrive not showing up on fdisk"
date: 2014-06-19
forum: Server Platforms
---

### Post by matt14 on 2014-06-19
I'm running Ubuntu 12.04 Server. I am trying to mount a usb drive to add more space on my server. For some reason, the physical drive does not show up when I run "sudo fdisk -l"

I know the problem is not the usb port because other usb drives show up on fdisk and can be mounted. I also know the problem is not the usb drive because I have connected it to my windows laptop.

Any ideas on why I cannot mount the usb drive? It is a Kingston DT 101 G2 (USB 2.0, 16 GB). Is there some incompatibility that I am not aware of?

Any suggestions would be appreciated.

---

### Post by SeijiSensei on 2014-06-20
Make sure you have plugged it into a USB 2.0 slot.  I've sometimes had USB problems with 2.0 devices in 3.0 slots.

---

### Post by matt14 on 2014-06-20
The computer I'm using only has USB 2.0 slots. It's a Dell Optiplex GX260 mini tower. It's a pretty old computer so maybe that's part of the problem.

---

