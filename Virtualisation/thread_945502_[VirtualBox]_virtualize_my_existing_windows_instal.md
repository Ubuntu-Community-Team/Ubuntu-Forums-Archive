---
title: "[VirtualBox] virtualize my existing windows install ?"
date: 2008-10-12
forum: Virtualisation
---

### Post by cybermecano on 2008-10-12
Hi,

Simply I would like to know if it is possible to virtualize my existing windows install using VirtualBox on UBUNTU ? just like it can be done with VMware if I trust the following :

[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)

I'm actually in dual boot and I get two different partitions: one for windows and the other for ubuntu 8.04.1... and it would be great if I can retrieve "MY" windows through VirtualBox !!!

Thanks.

---

### Post by jamesrl on 2008-10-12
I'm not sure how well virtual box supports this feature yet.  [It's complicated as your hardware configuration from a dual boot into windows vs. running virtual box within linux is necessarily different.]
But you can always use vmware and the above guide.

Or if you are brave you may try following this howto/guide:
[How to migrate existing Windows installations to VirtualBox]("http://www.virtualbox.org/wiki/Migrate_Windows")

---

### Post by waydownsouth on 2008-10-13
I'm looking into doing the same,

and came across this:

[http://ubuntuforums.org/showthread.php?t=769883]("http://ubuntuforums.org/showthread.php?t=769883")

might be what you're after?

---

### Post by run1206 on 2008-10-13
yes, it is possible to run your existing Windows partition in Linux. here's some pics of my setup.

i'm running my XP Home partition on Intrepid Ibex (with USB support)
to create the vmdk file, i used the same link that waydownsouth has.

for the USB support, go to this link...
[http://ubuntuforums.org/showthread.php?t=943103](http://ubuntuforums.org/showthread.php?t=943103)
check post #9 for the link and HOWTO to enable usb support.

for my setup, i didn't have to put in the whole "magic to work for usb" part, but i did have to make the usergroup and edit the permission of usb devices, hopefully it works for you all as well.

---

