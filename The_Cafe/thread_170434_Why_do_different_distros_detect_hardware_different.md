---
title: "Why do different distros detect hardware differently?"
date: 2006-05-04
forum: The Cafe
---

### Post by aysiu on 2006-05-04
I understand that Linux distros cannot automatically detect *all* hardware.

I understand that some hardware manufacturers will not create Linux drivers or release their driver code so that Linux developers can create their own drivers.

Fair enough.

What confuses me is when distro X can detect my USB mouse, and distro Y cannot. Or distro X recognizes my optimal screen resolution, and distro Y cannot. You get my drift, I hope.

For example, Ubuntu Hoary could not recognize my native screen resolution (it's been fixed since Breezy) but the version of Mepis that was around at that time could. Ubuntu Breezy could recognize my sound card, but PCLinuxOS could not.

Presumably, if one Linux distribution has drivers or information on a piece of hardware, shouldn't it release that information to other Linux developers? Am I not understanding the situation? Can someone explain why this happens?

---

### Post by nickle on 2006-05-04
Good question! I had wondered the same thing too. I (probably wrongly) assumed that the different distros had slightly different kernels with one being slightly more up to date than the other....???

---

### Post by GeneralZod on 2006-05-04
[QUOTE=aysiu]
Presumably, if one Linux distribution has drivers or information on a piece of hardware, shouldn't it release that information to other Linux developers? Am I not understanding the situation? Can someone explain why this happens?[/QUOTE]

[http://en.wikipedia.org/wiki/Not_invented_here](http://en.wikipedia.org/wiki/Not_invented_here)

Lots of good distro-specific things (utils, hardware detection scripts, etc) are never adopted by other distros (despite being Free software), and personally I blame NIH Syndrome for a lot of this.

---

### Post by prizrak on 2006-05-04
nickle, 
You are basically right. Linux is a monolithic kernel, which means that it puts the drivers into the kernel. For the most part distros tend to use their own kernel setup. Now why all distros don't include all the possible drivers in their kernel is a different question :)

---

### Post by jc87 on 2006-05-04
My theory is :

A) Automatic scripts , probably each distro runs its own pack of scripts to detect and handle hardware (changing configs and etc..).

B) Kernel type , some distros run the 2.6 , others the 2.4 , 2.2 , etc...

C) Kernel/Drivers philosophies , some distros use only the default drivers at the kernel , others include unstable drivers , others proprietary drivers , etc...

D) Community feedback , Damn Small Linux developers are as likely to receive a bug report about the xorg.conf not working with their brand new geforce 6800 as Ubuntu ones of booting errors at a Pentium MMX, ...

E) Also lack of communication between different Distros developers ....

---

### Post by 23meg on 2006-05-04
Drivers are compiled into the kernel or exist as kernel modules, so hardware support is almost entirely a kernel issue. Whether or not a certain piece of hardware is supported in a particular distro depends on the version of the kernel it is utilizing. Also HAL (Hardware Abstraction Layer) has some role in how your OS "talks" to your hardware, since it presents interfaces to the kernel for your hardware.

*Detection* of hardware specifics, however, can be a bit of a distro-specific issue; your example of screen resolution is one area where this can be a matter of how a particular distro is configured. Some distros may well be superior to others in detecting the particular properties of your hardware at install time with their autodetection scripts and other tricks. This is usually a userspace matter rather than a kernel one, since it depends on the distro's set of userspace tools used to communicate with the kernel and utilize the hardware. 

Here's a rough scenario: if distro releases A and B both use the same kernel (that does have support for your hardware compiled in it), but distro A has version 0.5 of, say, wacom-tools, which is the package that contains the userspace utilities to configure Wacom devices, and distro B has 0.6, distro B may be able to configure your new Wacom device whereas distro A may not, if support for your particular device has just arrived in version 0.6.

---

### Post by 23meg on 2006-05-04
[QUOTE=aysiu]
Presumably, if one Linux distribution has drivers or information on a piece of hardware, shouldn't it release that information to other Linux developers? [/QUOTE]

Since drivers are compiled into the kernel or exist as kernel modules, they come to being as part of kernel development, not the development of particular distros. However, many kernel developers are also developers for certain distros, and distros do submit lots of upstream patches to software authors in their testing stages, to the kernel as well. 

Whether or not kernel patches make it to the mainline kernel are up to the kernel governance (read: Linus), but since distro patches to the kernel are separately packaged (see the kernel-patch-debian and other similar packages in the repos for an example), they can be adapted by other distros. And with tools like Bazaar and Launchpad, Canonical is focusing on making inter-distro collaboration easier, so that when something gets patched in one distro, all other distros, as well as the upstream author can benefit from it if they want.

---

### Post by MetalMusicAddict on 2006-05-04
[QUOTE=aysiu]Why do different distros detect hardware differently?[/QUOTE]
This is something I noticed when I installed FC5 vs. Dapper. Dapper was much better off the bat.

FC5 missed my nic, video and soundcard. It was weird. :confused: I plan on giving it another go though. :D

---

### Post by RavenOfOdin on 2006-05-04
I think the HAL has something to do with it as well.

---

### Post by darweth on 2007-02-11
Ubuntu has excellent hardware detection for most anything I have used.  That said... why do distros vary here?  I thought drivers and support was loaded directly in the kernel?  If another distro uses the same kernel, why wouldn't it support the same stuff?  I have no experience on the matter since I've only used Ubuntu, but I have read many stories about hardware detection on other distros.  Can anyone explain?

---

### Post by 23meg on 2007-02-11
This question was asked a while ago; [here]("http://www.ubuntuforums.org/showthread.php?t=170434") is the relevant thread.

---

### Post by Henry Rayker on 2007-02-11
some hardware requires firmware on the system in order to function, due to different philosophies, some distros install that firmware, others don't; other causes could be due to a differently compiled kernel. I'm not an expert in this area, but those could be two issues.

---

### Post by aysiu on 2007-02-11
> **23meg said:**
> This question was asked a while ago; [here]("http://www.ubuntuforums.org/showthread.php?t=170434") is the relevant thread.
I've merged the two threads.

---

### Post by RAV TUX on 2007-02-11
I have found KNOPPIX to have the best hardware detection and have often wondered why Ubuntu doesn't adopt such superior hardware detection,....other Distros have historically adopted KNOPPIX hardware detection....

including but not limited to:

Dreamlinux
Musix
Morphix
Nepalinux
Mepis
Kanotix(now defunct)

etc., etc.

---

### Post by Adamant1988 on 2007-02-11
> **aysiu said:**
> I understand that Linux distros cannot automatically detect *all* hardware.

I understand that some hardware manufacturers will not create Linux drivers or release their driver code so that Linux developers can create their own drivers.

Fair enough.

What confuses me is when distro X can detect my USB mouse, and distro Y cannot. Or distro X recognizes my optimal screen resolution, and distro Y cannot. You get my drift, I hope.

For example, Ubuntu Hoary could not recognize my native screen resolution (it's been fixed since Breezy) but the version of Mepis that was around at that time could. Ubuntu Breezy could recognize my sound card, but PCLinuxOS could not.

Presumably, if one Linux distribution has drivers or information on a piece of hardware, shouldn't it release that information to other Linux developers? Am I not understanding the situation? Can someone explain why this happens?


Distro X may be willing to include non-free drivers, Distro Y may not.   Also, different distributions make changes to their kernels and so forth, so would that not effect that?

---

### Post by FyreBrand on 2007-02-11
> **MetalMusicAddict said:**
> This is something I noticed when I installed FC5 vs. Dapper. Dapper was much better off the bat.

FC5 missed my nic, video and soundcard. It was weird. :confused: I plan on giving it another go though. :DI've used Fedora before as well (specifically 4 and 5).  It seems Fedora developers take a slightly harder line approach to providing proprietary modules.  There has been quite some criticism of Ubuntu on some Fedora forums for including the blobs we do to support the hardware we do.  I guess this makes Fedora a "more free" distribution, but personally I think it makes it frustrating and hard to use.

---

