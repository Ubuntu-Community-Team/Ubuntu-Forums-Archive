---
title: "multiple linux distros on a Live USB"
date: 2010-08-08
forum: The Cafe
---

### Post by ged25 on 2010-08-08
I was wondering if it was possible to have multiple linux distros in a USB flash drive. So I can select a distro and run it as a live usb to try it or install it to my hard drive. Is this possible ?

---

### Post by oldfred on 2010-08-08
I did it manually and have several Ubuntu & rescue ISOs booted by grub2. The main issue I had was finding the correct grub2 entries.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script but only limited ISOs, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

But this script looks like it does the entire thing fo many ISOs:

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

