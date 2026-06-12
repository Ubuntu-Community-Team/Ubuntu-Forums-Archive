---
title: "KVM XP install problems"
date: 2009-01-19
forum: Virtualisation
---

### Post by goldleader on 2009-01-19
Im tring to install Windows XP on to my KVM on Ubuntu 8.10 64bit.  Im using Virtual Machine Manager, the install starts and everything seems to be working fine the Blue screen installer copies all the files and then reboots and brings up the GUI part of the installer but it then pops up and says it can't see the CD in the drive.  Im installing it from the CD-ROM drive that i tell it to when the the new machine wizard runs.  It seems to be loosing the CD-ROM drive when it does the reboot half way through the install.  Anyone got any ideas?

---

### Post by schoonbee on 2009-01-21
1) How about creating an iso and installing from that?

2) With Virtual Machine Manager 0.5.4 you should be able to CONNECT the drive:
- View > Details > Hardware
- Add Storage Device > Simple file > (your IS0), Type: IDE CDROM
- Change the Boot device to the CD. Boot Options > Boot Device.

---

### Post by goldleader on 2009-01-22
Thanks for the reply.  I will give it a try and let you know.

---

