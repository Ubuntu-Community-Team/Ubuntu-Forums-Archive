---
title: "Real time virtualization help for new desktop?"
date: 2012-06-19
forum: Virtualisation
---

### Post by cgb223 on 2012-06-19
Hey all,
I am planning on building my own computer here this summer, and I would like to pack it full of as much processing power and memory as a desktop these days can hold. I have this idea for my desktop however, and I would like to know if what I want to do is possible. So here it is:

I would like to have some sort of small fast OS as the main OS on the computer, and then have various virtual machines for each "partition" I otherwise would have setup. So like I'd have one virtual machine with windows and one for Ubuntu and others for maybe Backtrack, or OpenBSD or something. 

What I am wondering, is if I make my setup work this way, with all the processing power and memory inside my computer, will I be able to run the OS's about as fast as they would installed on the computer itself?

So say, if I open up my windows virtual machine, will it be fast enough to play something super resource intensive like Crysis or Skyrim on the highest video settings? Would I be able to compile a large C++ project in about the time it would take on a non-virtualized system?

If this is possible, what would be the best software to use, and the best way to set it all up?


I know thats all a mouthful...

Thanks!

---

### Post by houstonbofh on 2012-06-20
First, no, the virtual systems will not be as fast as running native.  However, with proper hardware, they will run very well, and perhaps better than some peoples native.

Next is hardware...  Some virtual systems will see your hardware and some will not.  Specifically, that high end video hardware.  If you want to play games with max performance, you need a dedicated Windows environment.  And by dedicated, I mean not used for much else at all.

As to other stuff, (like compiles) you can place a lot of resources in a VM if you wish, and it will fly.  But your desktop will not.  However, those settings can be changed on a give run. (Specifically memory and processors.)

So, for me, I use Ubuntu as my normal desktop.  I have also installed KVM with a few Windows installs (different versions) some additional Linux installs (some for version, some for minimal config) and a FreeBSD install.  I spin them up as needed.  I also sping them up when the fiancée needs a Windows desktop and she can just RDP into it.

---

