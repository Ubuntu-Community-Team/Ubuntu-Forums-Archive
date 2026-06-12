---
title: "How can hardware stop working"
date: 2009-11-28
forum: The Cafe
---

### Post by Glenn nl on 2009-11-28
How can hardware stop working.
Many people have that when they try a new version of ubuntu wireless fails, graphics dont work as they used to, usb devices stop working.

Is this in the linux kernel or something else?
I would think that more and more hardware would be supported in newer versions and not that hardware stops working

---

### Post by jwbrase on 2009-11-28
It's in the drivers.

Not all hardware manufacturers make their own drivers for Linux, because Linux doesn't have much market share, so writing drivers for Linux doesn't attract many customers for them. For hardware from those manufacturers, the community has to write its own drivers, which is very difficult if the manufacturer doesn't release specifications for the hardware. Every once in a while the drivers need to be updated, for instance to support a new kernel version, and sometimes when that happens the people writing the drivers make mistakes because they're writing blind instead of from the manufacturers specification.

For instance, on my other machine back home, this happened with my ATI video card when upgrading from Intrepid to Jaunty. ATI had stopped writing Linux drivers for certain of their video cards, and as a result Jaunty gave me trouble. It works fine on this machine though.

---

### Post by Exodist on 2009-11-28
> **jwbrase said:**
> It's in the drivers.

Not all hardware manufacturers make their own drivers for Linux, because Linux doesn't have much market share, so writing drivers for Linux doesn't attract many customers for them. For hardware from those manufacturers, the community has to write its own drivers, which is very difficult if the manufacturer doesn't release specifications for the hardware. Every once in a while the drivers need to be updated, for instance to support a new kernel version, and sometimes when that happens the people writing the drivers make mistakes because they're writing blind instead of from the manufacturers specification.

For instance, on my other machine back home, this happened with my ATI video card when upgrading from Intrepid to Jaunty. ATI had stopped writing Linux drivers for certain of their video cards, and as a result Jaunty gave me trouble. It works fine on this machine though.
^^This^^

---

### Post by Ylon on 2009-11-28
The answer for this is, plain... do not buy anylonger hardware made exclusively for windows.

Also, if someone ask you an advice on which hardware buy... advise against linux unfriendly hardware. Point that, even if you were going to put just windows on that hardware.. he wouldn't able to choice for another OS in future: Windows isn't alway backward compatible.

An hardware unsupported for Linux is an hardware, probably, ready for death in time of one or two windows versions.


HW linux friendly will be _always_ reusable for future assembled pc, reselling or even a gift: Ubuntu 10.04, 11.06 or 99.04.









Correctly develop (for Linux) Hardware wouldn't never stop working.

---

### Post by 3rdalbum on 2009-11-28
Regressions are caused by human error, or simply that the programmer assumes that the modifications they've made to the driver will work on all supported hardware when in fact they won't.

Hardware breakage doesn't only happen in the kernel. Gnome developers seem to switch between the idea of treating my Walkman as a Universal Mass Storage and treating it as an Media Transfer Protocol device. When they change their definitions so it becomes treated as MTP, that's when it stops working properly.

The next release, they fix it. The release after that, they've forgotten about it and they break it again. It's human error, but it's not any less annoying. KDE doesn't make that mistake with my device.

---

### Post by sdowney717 on 2009-11-28
windows is a boon for hardware makers, forcing users to change out perfectly good hardware when the os no longer supports it and the manufacturers wont write drivers to work with new windows os's.

The reason is clear, they want you to buy a new device.

---

### Post by clanky on 2009-11-28
> **Glenn nl said:**
> How can hardware stop working.
Many people have that when they try a new version of ubuntu wireless fails, graphics dont work as they used to, usb devices stop working.

Is this in the linux kernel or something else?
I would think that more and more hardware would be supported in newer versions and not that hardware stops working

So Linux upgrades cause hardware issues because.....

> **sdowney717 said:**
> windows is a boon for hardware makers, forcing users to change out perfectly good hardware when the os no longer supports it and the manufacturers wont write drivers to work with new windows os's.

The reason is clear, they want you to buy a new device.

Huh?

OK, as for the OP, do you mean why does my hardware stop working after I upgrade or why do they not make upgrades that break my hardware?

---

### Post by tgalati4 on 2009-11-28
Newer kernels cause breakage because support for old stuff is removed.  For instance, ISA bus support was removed (I don't remember which kernel).  So if you have an ancient ISA ethernet card, it will cease to function, making your life difficult.

You can manually load the module in the newer kernel, or recompile the kernel for older hardware, turning on the appropriate switches in the kernel configurator.

In other cases, simple regressions occur as the kernel attempts to address a rapidly-growing universe of hardware.  Adding new code can result in bugs that cause old hardware to freak out.

---

### Post by Chronon on 2009-11-28
> **3rdalbum said:**
> 
Hardware breakage doesn't only happen in the kernel. Gnome developers seem to switch between the idea of treating my Walkman as a Universal Mass Storage and treating it as an Media Transfer Protocol device. When they change their definitions so it becomes treated as MTP, that's when it stops working properly.

The next release, they fix it. The release after that, they've forgotten about it and they break it again. It's human error, but it's not any less annoying. KDE doesn't make that mistake with my device.

Good point.  This behavior drives me crazy too.  Even when I'm running KDE Gnome will, at times, interfere if it's installed.  I have to kill various Gnome processes to get my UMS devices to get recognized as such.  So, yes, regressions in hardware support can arise at various layers.

---

### Post by toupeiro on 2009-11-28
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

Reference this before buying hardware.

---

### Post by Ylon on 2009-11-28
> **clanky said:**
> OK, as for the OP, do you mean why does my hardware stop working after I upgrade or why do they not make upgrades that break my hardware?


You had to consider this first: who make the rules for the Hardware.. and that one is Microsoft.


New (PC) hardware is made under the rule and guideline made by Microsoft and, very commonly, these lines were dropped/unsupported/ignored by Microsoft itself when they realize that something that was forced in (previous) Windows was plain stupid.. so they make a newer version with new bizarre rules totally ignoring what was **agreed** just few years ago.

Windows Seven isn't ready to make your hardware run... is *the* hardware that had to be made "ready" [:KS](http://www.avaruusmies.com/jokes-root/img/161.jpg).

Now, step back with Ubuntu.. what's the problem? There's a babel of hardware around there:
*Hardware '95* can't talk with *Hardware Xp*.. and *Hardware '98* can't talk with *Hardware Vista*.

This basically mean.. if you make little change based upon Hardware 'Me (driver-module improvement/fix)... hell! you have absolute no idea what you've done on HW 95/98/2000/XP/Vista/Seven/Eight!

That's the problem: new (software) improvement made for a specific hardware cause effect back and forth!

Only with Linux/Ubuntu community is possible to solve this: a single person can't test anything.. but, looks like, launchpad comunity can!


I did notice this: with Linux hardware can pause... but not stop.


> **toupeiro said:**
> [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

Reference this before buying hardware.

Finally found it! I really needed this. Thanks [img]http://img.freeforumzone.it/upload/507093_inchino.gif[/img].

---

### Post by Ylon on 2009-11-28
[to delete]

---

