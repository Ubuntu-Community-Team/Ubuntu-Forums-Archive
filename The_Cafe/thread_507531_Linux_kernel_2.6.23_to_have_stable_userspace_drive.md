---
title: "Linux kernel 2.6.23 to have stable userspace driver API"
date: 2007-07-23
forum: The Cafe
---

### Post by v8YKxgHe on 2007-07-23
> Linus Torvalds included patches into the mainline tree which implement a stable userspace driver API into the Linux kernel.

    This interface allows the ability to write the majority of a driver in userspace with only a very small shell of a driver in the kernel itself. It uses a char device and sysfs to interact with a userspace process to process interrupts and control memory accesses.

Since future drivers using this API will run mainly in userspace there is no need to open up the source code for these parts. Also, drivers can be re-used even after kernel changes because the API will remain stable.

[Source/Read more]("http://liquidat.wordpress.com/2007/07/21/linux-kernel-2623-to-have-stable-userspace-driver-api/")

What are your thoughts on this?

---

### Post by prizrak on 2007-07-23
This is actually really nice. For one userspace drivers are easier to restart in case of something happening since the kernel doesn't need to be rebooted. For two it makes installation much easier since it doesn't have to build itself into the kernel anymore.

---

### Post by igknighted on 2007-07-23
I am happy and worried at the same time.  The obvious benefits of better driver support exist, but by appeasing third party vendors like this, we may have signed away our beautiful monolithic kernel.  If everyone says "gee, I don't need to release drivers to be included in the kernel anymore" and just releases userspace drivers, what good is the monolithic kernel that is linux's strength?  Now we need to go download third party drivers for everything.  It could also very easily lead to less and less OSS drivers, as a userspace driver that interacts with an API does not need to be open sourced at all.  So convenient it is, but it also worries me.

---

### Post by v8YKxgHe on 2007-07-23
> **igknighted said:**
> I am happy and worried at the same time.  The obvious benefits of better driver support exist, but by appeasing third party vendors like this, we may have signed away our beautiful monolithic kernel.  If everyone says "gee, I don't need to release drivers to be included in the kernel anymore" and just releases userspace drivers, what good is the monolithic kernel that is linux's strength?  Now we need to go download third party drivers for everything.  It could also very easily lead to less and less OSS drivers, as a userspace driver that interacts with an API does not need to be open sourced at all.  So convenient it is, but it also worries me.

Those are my exact thoughts on it as well. I was actually quite shocked when I saw the article, it's something I would never have expected Linus to accept.

---

### Post by prizrak on 2007-07-23
AlexC, igknighted,
You guys are panicking for no reason. user space drivers won't be replacing kernel drivers. For one there are certain drivers that are better off in userspace, such as printers, scanners, and audio. Others are better in the kernel. At the same time availability of closed source drivers never stopped open source developers, look at nouveau project, we have fully working 3D drivers from nVidia yet they are still working their assses off on that project.

---

### Post by Polygon on 2007-07-23
and this of course will encourage companies to make drivers for linux as they dont necessarily have to be open source

---

### Post by phrostbyte on 2007-07-23
Yeah this is stupid I think, I actually think the idea of having all the drivers in the kernel is an elegant solution... I hate the mess that is the Windows drivers hunt everytime I need to reinstall WinXP and I do it many times (it's one of my job duties :mad:) It's always fun to try to get ethernet drivers

---

### Post by Redache on 2007-07-23
It's a good idea when it comes down to it. We need more hardware support in Linux but manufacturers refuse to release detailed spec's for their devices, and they can't write closed source drivers for the Kernel so it will hopefully push them to release some form of support.

As the IT world continues to evolve, so does Linux, it may annoy some people but evolution has to happen.

---

### Post by prizrak on 2007-07-23
> **phrostbyte said:**
> Yeah this is stupid I think, I actually think the idea of having all the drivers in the kernel is an elegant solution... I hate the mess that is the Windows drivers hunt everytime I need to reinstall WinXP and I do it many times (it's one of my job duties :mad:) It's always fun to try to get ethernet drivers

Drivers don't have to be part of the kernel to be provided with the default install. nVidia drivers for instance are not part of the kernel yet they can be(and are in some cases) included with the distro. This will also mean that non-free drivers can be shipped by default as that would not violate the GPL in any way shape or form.

---

### Post by igknighted on 2007-07-23
> **prizrak said:**
> Drivers don't have to be part of the kernel to be provided with the default install. nVidia drivers for instance are not part of the kernel yet they can be(and are in some cases) included with the distro. This will also mean that non-free drivers can be shipped by default as that would not violate the GPL in any way shape or form.

Well, lets not get beyond ourselves.  From the article, graphics drivers and file system drivers are still beyond the scope of this (and I would wager audio drivers as well), but maybe logitech would give us a decent driver.

Another thought... should more and more companies release drivers like this, there is no way they could all be included on a single CD distro like Ubuntu.  Perhaps in the future the liveCD could have basic drivers, a liveDVD could have full driver support, and the installer (esp for the liveCD) would scan your computer and install drivers for devices it finds (downloading them on an available internet connection if need be).  This would cut down on bloat and also since the third party drivers would be optional the FOSS purists could be kept at bay.

All of this said, I still prefer a monolithic kernel where I can compile in exactly what I need.  I prefer a kernel-space driver for any device that is going to remain constant on my system.  Userspace drivers are nice for times that I may borrow a friends __________ and use it (say digital camera), or perhaps things like keyboards/mice that tend to wear out, but the main system components should stay in the kernel.  Theres no reason they should leave, otherwise you run into situations like windows where you install and there are no drivers for bits of your motherboard, and if one of those bits happens to be the ethernet port, well, you're screwed trying to get those drivers.  Lets not give manufacturers of these parts the quick way out, make them develop true FOSS drivers and add them to the kernel.

---

