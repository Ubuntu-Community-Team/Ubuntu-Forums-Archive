---
title: "Mounting dev/cdrom (dev/scc0) on a netbook"
date: 2011-08-26
forum: Virtualisation
---

### Post by gnometorule on 2011-08-26
Ubuntu 10.04; VirtualBox 3.1.6 from repositories

To enable shared folders in guest accounts in VirtualBox, I need to mount in either one of the following forms (so the ISO virtually mounted within Virtualbox to cdrom, as I understand it, can be linked, its files found in /cdrom, and then an install script sh run on the host):

mount /dev/cdrom /cdrom, or
mount /dev/scc0 /media/cdrom

or similar. I remember not seeing either device defined in the devices.txt list. To make matters worse, I don't seem to be able to find my devices.txt list anymore. From memory, it was in /usr/src, then the kernel module; but in that folder i only have 4 kernel-header-genericxxx files, plus VirtualBox. I search for it using find (I am not a find expert):

find /usr/src -name devices.txt
find / -name devices.txt

and don't find it either.

So my questions:

(1) Where is my devices.txt file?

(2) After I find my list, do I use makedev, and is that, on a netbook, likely to succeed? If I don't overextend my welcome, what is the proper syntax? As I believe that the device was not currently in the devices.txt list (when I could still find it), is makedv (or mknod) even possible? If not, what to do? 

P.S.: These are links to the VirtualBox forum answers discussing this, where you see what type of mount is required, which I cannot currently execute. I've taken all other preparatory steps:
[http://forums.virtualbox.org/viewtopic.php?t=15679](http://forums.virtualbox.org/viewtopic.php?t=15679)
[http://forums.virtualbox.org/viewtopic.php?f=1&t=34328&p=153575&hilit=mount+cdrom+on+netbook#p153575](http://forums.virtualbox.org/viewtopic.php?f=1&t=34328&p=153575&hilit=mount+cdrom+on+netbook#p153575)

P.P.S.: I wasn't really sure which forum to post this...

---

