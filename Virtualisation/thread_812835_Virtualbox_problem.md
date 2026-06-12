---
title: "Virtualbox problem"
date: 2008-05-30
forum: Virtualisation
---

### Post by reyhan on 2008-05-30
Hello i just finished install Virtualbox but when i want to start the Virtual machine
theres a problem here's the Screenshots :confused::confused:

---

### Post by NetworkGuy on 2008-05-30
You need to also install the kernel module for VirtualBox that matches your kernel.

Type from the command prompt   sudo apt-get install virtualbox-ose-modules-generic

This will install the correct kernel module.   Then try to start your virtual machine again.

---

### Post by pixel :-) on 2008-05-30
And add your self in the group "vboxusers"

Then if you know the command load the kernel module,wheninstalled it's not loaded automaticly.If you don't now the command, reboot.

---

### Post by pizpot on 2008-06-01
if you are dual booting, select the -16 generic kernel instead of -17 version. if you don't get that option, sudo gedit your /boot/grub/menu.lst so that it boots from the right kernel. ie) change the line that says "default" from 0 to 4 or whatever is right. (remember the first choice is 0). Either that or just increase the "timeout" from 0 to 300 so you have time. As always, do a "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup" first.

Low tech fix, but since it will fix itself anyways one day, it's cool.

---

