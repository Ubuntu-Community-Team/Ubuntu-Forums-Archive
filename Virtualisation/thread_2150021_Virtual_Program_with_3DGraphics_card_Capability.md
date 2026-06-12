---
title: "Virtual Program with 3D/Graphics card Capability"
date: 2013-05-30
forum: Virtualisation
---

### Post by nankura on 2013-05-30
hey guys

Basically. the only virtualisation program i know of is Virtualbox. and with Virtualbox, 3D and using the graphic's card in the pc isnt 100%, and its never really been a great choice for gaming over wine or something like that

Now im just curious if there's any other virtualisation program's out there , that could grab windows. and properly use resources, even the graphic's card. 

The main reason im asking this is because at the moment i dual boot with window's, and i know steam is coming to linux, but there's alot of "free" company's out there that make little games that i love, and dont support mac or linux

This game holding me back, unfortantly uses gameguard. in which is wine's worst enemy. since it requires core window's components to work. 

The game is called Uncharted waters online, its not hugely graphically intensive. its nice, but doesnt require a super pc to run. so i was hoping that there's a virtualisation program which can get windows going, and have enough graphical power to play this game

I have sort of heard of one called QEMU but im not sure how it work's

if i could play this one game on linux, i would switch completely

---

### Post by Cheesemill on 2013-05-31
There are virtualization solutions that allow a guest OS full access to a graphics card on your machine, this is known as VGA passthrough. It's not easy though, take a look at this thread for some pointers...

[http://ubuntuforums.org/showthread.php?t=2111175](http://ubuntuforums.org/showthread.php?t=2111175)

---

### Post by heiko_s on 2013-05-31
In addition to the above thread, you may want to check my Linux Mint how-to: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013"). It should work with Ubuntu too (note that the LVM part is much easier in Ubuntu or the latest Linux Mint 15 release).

Please note the hardware requirements!!! If your CPU / motherboard don't support VT-d (Intel) or AMD-Vi (or IOMMU for AMD CPUs/motherboards), forget it or go get the right hardware. In addition to Xen as a solution for VGA passthrough you can also try kvm, see here: [https://bbs.archlinux.org/viewtopic.php?id=162768&p=1]("https://bbs.archlinux.org/viewtopic.php?id=162768&p=1") - it's for ArchLinux though.

---

### Post by nankura on 2013-06-12
thanks for all this advice guys, ill give it a try. if only there was a program to do all that automatically :P

---

