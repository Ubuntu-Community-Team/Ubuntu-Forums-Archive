---
title: "VMWare Server on Darter"
date: 2007-04-06
forum: System76 Support
---

### Post by akniss on 2007-04-06
I'm going to be getting a laptop in the next few months.  I would like something small for traveling, and I will need to use it to give presentations.  None of my co-workers use linux, so I will have to have a working version of Powerpoint on the laptop.  I would prefer not to have to dual boot... Its such a pain.

So my question is this: if I get the darter with the 2GHz Core 2 Duo and 1.5 GB of RAM, will a virtual WinXP run pretty well? (I'm currently using VMWare Server, but would not be opposed to VirtualBox if it has similar performance.)    The jump in price for the 2.16 or 2.33 GHz CPU is substantial, and I'm curious if I really need that much power.  I don't have too much trouble on my Dell Pentium M 2GHz with 1GB of RAM, but I don't know how the integrated graphics on the 2 computers would compare.  I would assume that the Intel graphics on the darter should be as good or better than the ATI Radeon R250 I've currently got in my Dell... Is that a poor assumption?

---

### Post by aay on 2007-04-06
I don't have a Darter, but I suspect VMware would run pretty well with 1gb of ram and very well with 2.  The next edition of Ubuntu, Feisty, will have VMware's vmi in the kernel, which should allow very good performance using the current beta release of VMware.  However, if all you need is powerpoint, I'd consider using OpenOffice which will play powerpoint files, or using Powerpoint itself under WINE or Crossover office.  The second option is a lot more resource effecient than using VMware.

---

### Post by maniacmusician on 2007-04-07
> **akniss said:**
> I'm going to be getting a laptop in the next few months.  I would like something small for traveling, and I will need to use it to give presentations.  None of my co-workers use linux, so I will have to have a working version of Powerpoint on the laptop.  I would prefer not to have to dual boot... Its such a pain.

So my question is this: if I get the darter with the 2GHz Core 2 Duo and 1.5 GB of RAM, will a virtual WinXP run pretty well? (I'm currently using VMWare Server, but would not be opposed to VirtualBox if it has similar performance.)    The jump in price for the 2.16 or 2.33 GHz CPU is substantial, and I'm curious if I really need that much power.  I don't have too much trouble on my Dell Pentium M 2GHz with 1GB of RAM, but I don't know how the integrated graphics on the 2 computers would compare.  I would assume that the Intel graphics on the darter should be as good or better than the ATI Radeon R250 I've currently got in my Dell... Is that a poor assumption?
You'll definitely get good virtualization. I would also personally choose VirtualBox over VMWare, it's given me better performance.

For virtualization purposes, I recommend that you look carefully at the processors. I would go with the one that has 4MB of L2 cache...it's a pretty important featur. That's the T7200, at 2.0GHz.  Upwards of that, it's your decision how much money you want to spend. i would agree with you that it's not worth the increases in price as the clock speed gets higher, so I would either get the T7400 if you can swing it, or even the T7200 will suffice. I have the desktop version of the T7200 and am quite satisfied.

You are correct about your assumption about the graphics chipset. The intel graphics are quite resilient. If you want, you can run Beryl, multiple instances of VirtualBox, whatever. It can handle it. 

The 1.5 GB in the darter should be enough for you to get by on as well. I wish 2GB was available, but 1.5 GB is quite good.

---

### Post by akniss on 2007-04-08
> **maniacmusician said:**
> You'll definitely get good virtualization. I would also personally choose VirtualBox over VMWare, it's given me better performance.

That's great to hear.  It would be nice to support an open source project.

> **maniacmusician said:**
> 
For virtualization purposes, I recommend that you look carefully at the processors. I would go with the one that has 4MB of L2 cache...it's a pretty important featur. That's the T7200, at 2.0GHz.  Upwards of that, it's your decision how much money you want to spend. i would agree with you that it's not worth the increases in price as the clock speed gets higher, so I would either get the T7400 if you can swing it, or even the T7200 will suffice. I have the desktop version of the T7200 and am quite satisfied.

The L2 cache is the reason I wanted to get up to the 2GHz CPU.  I would be curious if anyone really thinks the 2.16GHz would make an improvement substantial enough to justify the increased price.  It sounds like you share my skepticism.

> **maniacmusician said:**
> 
You are correct about your assumption about the graphics chipset. The intel graphics are quite resilient. If you want, you can run Beryl, multiple instances of VirtualBox, whatever. It can handle it. 

Also good to hear.  I'm looking forward to ditching ATI graphics.  I probably won't run beryl 95% of the time on my laptop, but its nice to know it will run well when I want to show people how Linux has had all the pretty "vista features" for some time. 

Does beryl cause CPU usage to increase on the Darter?  It really seems to eat cpu cycles on my current laptop.  xorg and beryl processes typically combine to use about 10% of my processor when I'm not doing anything.

> **maniacmusician said:**
> The 1.5 GB in the darter should be enough for you to get by on as well. I wish 2GB was available, but 1.5 GB is quite good.

I've been getting along reasonably well with 1GB of RAM, so 1.5 will allow me to set up my VM machine with more than the current 384 MB of virtual ram.  It will seem like quite an upgrade to me!

---

