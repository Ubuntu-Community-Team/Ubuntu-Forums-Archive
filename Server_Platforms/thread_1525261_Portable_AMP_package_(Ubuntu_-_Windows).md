---
title: "Portable AMP package (Ubuntu - Windows)"
date: 2010-07-06
forum: Server Platforms
---

### Post by EgoGratis on 2010-07-06
Is there such a thing. 

-Apache-MySQL-PHP 
-Portable (USB pendrive)
-Works inside Ubuntu and Windows

---

### Post by infamous-online on 2010-07-09
I haven't heard of this, because those packages need to be installed onto your actual machine.

---

### Post by EgoGratis on 2010-07-09
Actually i think this would be very hard to achieve. Because of two different kind of operating systems. But WAMP package like Uniform Server works without installing anything (but services when in use) on windows machine. So you basically have a folder and everything in it. Completely portable and very easy to use. It would be very hard probably if not impossible to make the software run like that on two different OS. You would probably need two sets of programs but at the same time they would have to share MySQL database and content of web server (root folder) and settings and everything else important to end user to get his web page properly displayed. **Mission impossible?**[B]
 

[/B]

---

### Post by bodhi.zazen on 2010-07-09
You could try this :

[http://portableapps.com/apps/development/xampp](http://portableapps.com/apps/development/xampp)

most portable apps I have used run in wine with no problem.

Your other option would be to use portable virtualbox or qemu with a small OS (slitaz) with a web server installed.

---

### Post by EgoGratis on 2010-07-16
Yes. The closest and most universal thing i know off would be with VirtualBox + virtual machine images (or other virtualization software). Every OS must have VB installed that is true! But otherwise it stays untouched. Good point!

Funny thing would be if there would be portable virtualization software available? That would have Windows and Ubuntu version. And then you could do just that. On both OS. Without changing one thing. It would be possible to run  virtual machine images from USB stick for example.

Is there any portable virtualization software available for Ubuntu? Your solution is great. Virtualization software on target OS + virtual machine images. This just work.

But for discussion purposes. Is there any portable virtualization software for Ubuntu (and the same time for windows and maybe other OS)?

---

### Post by bodhi.zazen on 2010-07-16
qemu is portable and cross platform.

Tons of turorials on this :

[http://www.pendrivelinux.com/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/portable-qemu-persistent-ubuntu-linux/)

I have done that, qemu on a flash drive, the only problem is qemu is slow. So you should either perform a minimal installation (no desktop) or use a light weight OS (Slitaz).

The qemu image will boot on both linux and windows and the link I gave you to portable Linux has scripts to boot the image in both Linux and windows.

VirtualBox is also portable.

[. : Portable-VirtualBox : .]("http://www.vbox.me/")

---

### Post by EgoGratis on 2010-08-07
OK i will mark this post as solved. The (closest) correct answer to the question is Virtual Machine. And some workarounds!

Thanks for the answers.

---

