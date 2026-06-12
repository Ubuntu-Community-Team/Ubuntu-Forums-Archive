---
title: "feeling like a newb... windows installer 3.0"
date: 2010-01-06
forum: Wine
---

### Post by cacycleworks on 2010-01-06
Hey everyone,

I've been banging my head on this for a while and am thinking that I'm just not getting something simple... 

I want to install something and it demands windows installer 3.0. And another program wants .NET 2.0. I install .NET 2.0 when I click on it in winetricks and then IT wants in installer 3.0. It's kind of a weird circular argument. :P I've got win installer 3 and .NET downloaded ... kinda just lost for the moment unable to do anything with either of these.

~shrugs~ 

Windows is vexing no matter where they are. :)

---

### Post by Peekie on 2010-01-06
What is it that you want to install?

---

### Post by mocoloco on 2010-01-06
I found out that wine can use mono to handle much of the .net stuff.  So install [mono-runtime]("apt:mono-runtime") and see if that takes care of your .net 2.0 dependency. Amazing but true. Those wine coders are geniuses!
Worked for my app, though your mileage may vary.

---

### Post by mocoloco on 2010-01-06
Went and checked my notes on the machine I did the wine app, the package I installed was mono-mcs, which depends on mono-runtime.  Probably works with just runtime, since it says mcs is a compiler, but thought I'd mention it in case it actually affects anything.

---

### Post by cacycleworks on 2010-01-06
> **Peekie said:**
> What is it that you want to install?

Hi Peekie, [Rhino 3D modelling software]("http://ubuntuforums.org/showthread.php?p=8617668"). Bur I was also trying to run nLite to slipstream a new install CD (just went from SSD back to conventional HDD on my laptop, so I reinstalled everything). nLite wanted .NET 2.0, which apparently also requires Windows Installer 3.0.

> **mocoloco said:**
> I found out that wine can use mono to handle much of the .net stuff.  So install [mono-runtime]("apt:mono-runtime") and see if that takes care of your .net 2.0 dependency. Amazing but true. Those wine coders are geniuses!
Worked for my app, though your mileage may vary.

Hi mocoloco, THANKS! I'll keep this in mind. Now that I have a fresh install of both windows and ubuntu 9.10, I'm going to put in a better effort to get Rhino working in ubuntu either via wine or in a virtual machine. The new HDD I got was 320G (cost more to get a smaller one?!) so there's plenty of space for me to use doing odd OS things... 

:)

Thanks!
Chris

---

### Post by KrisDouglas on 2010-08-02
Hello, I am also experiencing this problem, I remember it working long ago, but now I am unable to install .net 2.0 as it is bugging me for a while because I need xencentre.

I haven't tried mono yet as I would prefer stability over openness.

---

