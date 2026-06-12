---
title: "Stuck on reboot in VirtualBox"
date: 2015-07-11
forum: Virtualisation
---

### Post by dave_h2 on 2015-07-11
I installed ubuntu-14.04.2-desktop-i386.iso on the latest VirtualBox on Windows 7 and it gets stuck after reboot and just says:

_* Deactivating swap... [OK]
* Stopping early crypto disks... [OK] (I didn't do crypto disks, just normal default installation)

If I hit any key, it activates shutdown and gets stuck again with a warning (see screenshot)

[IMG]http://imgur.com/Y5OFp7b[/IMG][http://imgur.com/Y5OFp7b](http://imgur.com/Y5OFp7b)

---

### Post by Bucky Ball on 2015-07-11
*Thread moved to **Virtualisation**.*

---

### Post by ajgreeny on 2015-07-11
That is the normal way that VBox deals with what in a hard-metal installation would be the ejection of the live system DVD or USB, so I presume you may have used one or other of those ways to install.  Just hit Enter and it should eject and shutdown allowing you to start it again, though you may have to remove the DVD or USB from the storage devices shown in the VM's settings before you reboot the VM, leaving just the vdi.

It is much easier to install in VBox by booting direct from the ubuntu.iso image file direct.  Just make a new VM in the normal way and then when you start it at the first screen hit the small icon to the right of the box asking for the filesystem to boot (I can't remember the actual words it uses) to point it to the .iso file.

---

