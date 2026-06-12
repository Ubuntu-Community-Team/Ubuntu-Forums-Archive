---
title: "Virtual Ubuntu on Flash Drive"
date: 2007-11-05
forum: Virtualisation
---

### Post by Ian505 on 2007-11-05
I have a 80GB portable Hard Drive that I would like to install a Ubuntu virtual machine on. It has to be completely independent- meaning that the virtual machine will successfully boot on any Windows XP or greater machine that I hook it up to. 

I have tried Qemu, but have note been able to get [Synaptic to work correctly]("http://ubuntuforums.org/showthread.php?p=3694545") and therefore have not been able to install the program that I need and is Linux-only. ([Kalzium]("http://edu.kde.org/kalzium/"), which is a KDE periodic table.) 

I tried simply copying the files from my VirtualBox directory to my hard drive but I get a COM error when I move to a different machine and it won't even load. 

I am looking for a solution that will allow me a completely hardware independent Ubuntu Virtual Machine that will run on Windows XP with the ability to install [Kalzium]("http://edu.kde.org/kalzium/") through Synaptic. 

I am almost ready to give up on this... and I don't give up very well. Please help!

Thanks a million.
Ian

EDIT- Just to clarify, it does NOT have to be bootable, but it does need to be able to run on any Windows XP machine.

---

### Post by InGunsWeTrust on 2007-11-06
If I am understanding this problem correctly you want a virtual machine that you can run on both windows and linux is that right?

If that is the case VMware server is your best bet. I can give you a good tutorial on installing it because I did it once on Ubuntu 7.04

---

### Post by bodhi.zazen on 2007-11-06
[http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/](http://www.pendrivelinux.com/2007/09/20/how-to-make-ubuntu-704-casper-persistent/)

[http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/](http://www.pendrivelinux.com/2007/03/26/portable-qemu-persistent-ubuntu-linux/)

---

### Post by Ian505 on 2007-12-27
Sorry for not posting this sooner- I have been pretty obe lately.

I found my solution. Since VB requires the windows registry, I simply installed a program called [MojoPac]("http://www.mojopac.com/portal/content/hellomojo.jsp") onto the portable drive. It is basically a program that makes a mini-XP desktop on your portable drive. (The host machine must be running XP for this to work, which was fine in this circumstance.)

So I simply entered my mini-desktop, installed VB in the mini desktop, pointed it to the .vdi on my portable drive and it worked! Yay!

I hope this helps someone who was in the same position as I was.

-Ian

---

