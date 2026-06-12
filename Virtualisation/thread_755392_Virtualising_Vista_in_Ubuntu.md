---
title: "Virtualising Vista in Ubuntu"
date: 2008-04-14
forum: Virtualisation
---

### Post by Ensamvarg on 2008-04-14
I am completely new to virtualisation. I was just wondering whether or not it would be possible to virtualise Vista under Ubuntu 7.10, and be able to play games as though it was a normal Windows machine. I appreciate that Vista is a monster when it comes to RAM but with a birthday coming up I'm hoping my issues will be sorted.

I just want to be able to use Linux and only have Windows for its gaming abilities.

---

### Post by ridetheteapot on 2008-04-15
why not just go with windows xp? there isnt too much in the line of 3d accelerated virtualization, vmware has a svga driver, but.... i'd assume that it doesn't deal with most of the graphics routines that your card has, making any vista exclusive games unplayable or ugly. but thats a guess, cause i definatly dont have or know anyone who has the hardware to even bother trying.

As for actually installing vista in vmware i've heard as far as vmware workstation (not free) is concerned vista will install on ver 6, not earlier versions.

---

### Post by fjgaude on 2008-04-15
VMware server, which is free, handles Vista, said to be experimental in v1.0.5. Some have used it here, but no 3D graphics, that's for sure.

Games are something that virtual doesn't do.

---

### Post by Victormd on 2008-04-15
> **Ensamvarg said:**
> I am completely new to virtualisation. I was just wondering whether or not it would be possible to virtualise Vista under Ubuntu 7.10, and be able to play games as though it was a normal Windows machine. I appreciate that Vista is a monster when it comes to RAM but with a birthday coming up I'm hoping my issues will be sorted.

I just want to be able to use Linux and only have Windows for its gaming abilities.

Why not just dual-boot Vista and Linux?
If you boot into my windows XP, all you'll see are games... nothing else... hehehe

---

### Post by yeehi on 2008-04-17
No 3D graphics with VMserver running Vista on Ubuntu?

But, for example, Photoshop would work ok, but a 3d game like Assasins Creed wouldn't?

---

### Post by fjgaude on 2008-04-17
> **yeehi said:**
> No 3D graphics with VMserver running Vista on Ubuntu?

But, for example, Photoshop would work ok, but a 3d game like Assasins Creed wouldn't?

I'm a graphic designer, notice my signature, and can say all the design programs run well and good in vmware server. They show just as they do from a Windows boot.

Games that use, need hardware support, acceleration simply don't work.

---

### Post by yeehi on 2008-04-17
OK - 3d games need hardware support... so, does that mean,if there is a modern graphics card from nvidia, for example, the games should work?

---

### Post by fjgaude on 2008-04-17
No, what it means is that the virtualization of the modern video card is not yet possible. I do believe vmware is trying to get a software emulation that is better than the present **svga** one.

We simply have to be patient for such to come about, if it ever does.

Gaming is not big in the business world and virtual systems are being developed primarily for businesses.

---

### Post by VMan on 2008-04-18
I had Vista running in a VMware virtual machine on a 1.6GHz Dual core with 2G of RAM.  It ran so so slow, that I didn't even bother to try to run it anymore.  If you're thinking of gaming with it, even if the game doesn't require 3D acceleration, it's not going to work well.

As a side note, with this laptop, I can run three instances of XP in seperate virtual machines with stuff running in the Ubuntu host, and they all run faster than Vista runs natively (not to mention how slow Vista was in a virtual machine even when it was the only thing running on the host).

---

### Post by phrostbyte on 2008-04-18
It should be made clear that presently there is no way to execute hardware accelerated 3d applications in any virtual machine with any degree of reliabitly. For your VM actually virtualizes all hardware on the machine, and any software which requires direct hardware access may have problems (which is unfortunatly most video games). THis may change in the future but not in the near future.

---

### Post by yeehi on 2008-04-18
Here is something related to hardware acceleration and virtualization i read in another forum:

> Dual-booting and perhaps Wine, are considered old-school. Use Vmware to host your virtual machines. I've tried 32-bit Vmware on both Ubuntu and Fedora, and in both cases I was able to install (and run!) Windows. However, as I sat there staring at the sky-blue screen of WinXP, I pondered what to do next... I couldn't think of anything to do, so I closed the session and went back to using Linux.  

Alternatively, install Vmware under Windows and host a Linux distro (or two).



The problem with using virtualisation is that there are currently no techniques to translate DirectX calls into native. This really rules out the only compulsion I have for booting Windows for newer games or using Wine for older ones.

Another thing that many don't know about is Hardware Virtualisation. Basically if your CPU/motherboard supports it, it is much, much faster than software calls. For Intel processors, here are the following with support:
CODE
It is available on certain Pentium 4 6x1 and 6x2 models, Pentium D 9x0, Xeon 3xxx/5xxx/7xxx, Core Duo (excluding the T2300E and T2x50 models) and Core 2 Duo processors (excluding the T52x0, T5300, T54x0, T5500 with stepping "B2", E2xx0, E4x00 and E8190 models).


And on AMD's side:
CODE
stepping "F" and "G", Athlon 64 X2 with stepping "F" and "G", Turion 64 X2, Opteron, Phenom, and all newer processors.


Those running Linux can put in a terminal to discover if their cpu supports hardware virtualisation:
For Intel
CODE
sudo cat /proc/cpuinfo | grep vmx

or for AMD
CODE
sudo cat /proc/cpuinfo | grep svm

I guess that Hardware Virtualization of the CPU isn't going to help much with the 3D graphics though.

---

### Post by tnl2k7 on 2008-04-18
Hello,

There's an application called Wine that can run some Windows games without needing to own a copy of Windows and without a virtual machine.

You can download it by opening up Applications > Accessories > Terminal and typing:
```
sudo aptitude install wine
```

It's pretty good with some games, but can be crap with others. For help using it, go to [the Wine HQ website](http://www.winehq.org/). They have a pretty useful application database too with information about what games work with Wine and what settings are required in order to make it work.

I'm surprised it hasn't been mentioned yet.

Your best bet, in my opinion, is to just install Windows. It works better with games and you'll get better frame rates.

Hope this helps.

---

