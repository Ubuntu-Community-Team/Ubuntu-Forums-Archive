---
title: "windows in a virtual machine ?"
date: 2008-10-09
forum: Virtualisation
---

### Post by WitchCraft on 2008-10-09
Hi, question:

I've installed XP, Vista and Ubuntu on the same hard-disk, and it all runs fine.
I personally use Ubuntu, but for university, I need xp and vista (they just don't care).

Now I wanted to know if it is possible to run windows under a virtual machine from Linux, when I've installed Windows natively,** without having to fill the Linux partition with another installation of Windows**, because then I wouldn't have to shut Linux down while i do something on Windows...

---

### Post by FrostyFlames on 2008-10-09
Hmm, sort of.

I'd look into the following posts for more information:
[http://forums.virtualbox.org/viewtopic.php?t=1966](http://forums.virtualbox.org/viewtopic.php?t=1966)
[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

In all honosty, if you want to run windows in a VM on Ubuntu, you should do it from scratch because of all the stuff windows pulls with hardware checks and whatnot (some might call this a form of DRM).

---

### Post by stinger30au on 2008-10-09
xp will run fine in virtual box by sun systems

no matter what version of virtual box you run you wil *NOT HAVE ACCESS* to direct 3d, only direct draw, and no paralel port access either


if you run the closed source version of virtual box you can access usb, serial etc with no dramas

iyou can share data between the virtual windows and ubuntu easy.

setup shared directoys and map them between both


xp runs fin in virtual box and has no idea its running inside linux

so if you want you can load up virtual xp with drivers for your non supported usb linux device and do what ever you need in there and swap seemlesly between xp and ubuntu and have both running at eactly the same time

magic bit of gear is virtual box

---

### Post by chaosdesigner on 2008-10-09
I too run xp in a virtual machine and its great. I'm using vmware and it's just a awesome programm, one big advantage is that you have a virtual hard drive, that means it starts of at beeing maybe 5 gb big and when your xp grows larger the hard drive will too. This helps you keeping the vm at the lowest space.

Don't know if thats the case for virtual box too.

---

### Post by Rayaz on 2008-10-09
Virual box offers you two options for the virtual hard drive: Dynamically expanding (gets larger as you add more stuff) and Fixed size.

---

### Post by WitchCraft on 2008-10-10
> **chaosdesigner said:**
> I too run xp in a virtual machine and its great. I'm using vmware and it's just a awesome programm, one big advantage is that you have a virtual hard drive, that means it starts of at beeing maybe 5 gb big and when your xp grows larger the hard drive will too. This helps you keeping the vm at the lowest space.

Don't know if thats the case for virtual box too.

yes, but then i have to install it again, and can't use it natively, without the vm, if i need to...

---

### Post by HavocXphere on 2008-10-10
> **WitchCraft said:**
> yes, but then i have to install it again, and can't use it natively, without the vm, if i need to...
If I understand your post correctly, you want to run Windows in a VM most of the time, but also natively boot off it when needed?

I suspect that your wishlist contains mutually exclusive wishes: Windows cannot natively boot off a VM image and Virtualization can't utilize an actual HDD partition.

And constantly converting between VM image and a HDD partition is going to be 100x as much work as dual booting.

So I reckon your options are:
1) Dual-boot
2) Accept that the virtualized Windows and the Native one aren't going to be in sync (i.e. 2 copies of Windows)
3) Accept the restrictions/overheads imposed by virtualization

If it would be possible to have the best of both worlds then everyone would be doing it ages ago:(.

---

### Post by Bushwack on 2008-10-10
It is possible to run the same install of Windows both natively and virtually.

Check out the second link in the first reply to this thread.  I've done it myself and it worked great.  It was extremely difficult to setup, but at the time I didn't have a complete detailed set of instructions like those from the virtualbox forum so it may be a little more straight forward now.

---

