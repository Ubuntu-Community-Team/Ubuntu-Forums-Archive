---
title: "Hardware support Idea"
date: 2009-10-09
forum: The Cafe
---

### Post by keiichidono on 2009-10-09
[QUOTE=http://www.tuxradar.com/content/opensolaris-vs-linux]Linux has a big advantage over OpenSolaris in that it supports a lot more hardware, but OpenSolaris makes up for this by having a fixed device driver interface. Where the Linux kernel developers give priority to adding features even when they break compatibility with hardware drivers (which creates more work for the distro makers) OpenSolaris keeps the driver interface static, so if your printer worked with OpenSolaris 2008.05 it'll work with 2009.6 - users can even run 10-year-old drivers written for the original Solaris platform.

OpenSolaris also gives you a clear overview of what is supported, rather than the suck-it-and-see approach favoured by Linux. The best way to find out whether specific hardware components are supported is by searching the Solaris Hardware Compatibility List online.

Another option to test hardware support on a computer is simply to fire up the live CD. The Device Driver Utility icon should show up on the desktop, which detects all available hardware and lists which driver supports it, even if it is third-party. For example, when I fired up the Device Driver Utility on my Dell laptop, the program said that it didn't have a driver for my WLan chipset (from Broadcom), but referred me to a website where I could download a third-party driver.

There is also a related utility, the Device Detection Tool: this is a Java program giving the same information, which you can run on Windows, Linux and Mac OS X. So with this tool, you get a perfect overview of the hardware support before you even install OpenSolaris.[/QUOTE]

[IMG]http://www.tuxradar.com/files/LXF122.solaris.devicedriveru.jpg[/IMG]



[SIZE="4"]What do you guys think? Should we bring this over to Linux or am I beating a dead horse?[/SIZE] :confused:

---

### Post by earthpigg on 2009-10-09
i love the live cd mode to to test hardware compatibility.

a combination of the functionalities of lshw and jockey.

---

### Post by keiichidono on 2009-10-10
No one else has any thoughts on this?

---

### Post by Dark Aspect on 2009-10-10
> **CalvinB said:**
> No one else has any thoughts on this?

Surprising, no. In fact I rarely have thoughts at all.

On a more serious note, doesn't Ubuntu have the same thing with its Hardware Drivers (under Administration).

---

### Post by keiichidono on 2009-10-10
> **Dark Aspect said:**
> Surprising, no. In fact I rarely have thoughts at all.

On a more serious note, doesn't Ubuntu have the same thing with its Hardware Drivers (under Administration).

Similar, but no dice. Only for proprietary graphics card and wifi drivers.

---

### Post by moster on 2009-10-10
CalvinB, of course you are right. But there is no simple solution beside just listing hardware what work and what do not work.

---

### Post by earthpigg on 2009-10-10
> **Dark Aspect said:**
> Surprising, no. In fact I rarely have thoughts at all.

On a more serious note, doesn't Ubuntu have the same thing with its Hardware Drivers (under Administration).

not quite.

based on my basic understanding:

every piece of hardware in your computer needs either a kernel module or direct kernel support to function.

usually what happens is at boot the best option is automatically picked. when that doesn't work, user needs to muck about at the command line to manually blacklist a module, which means the 2nd best option is picked.

but there may be 4 or 5 options in total.

maybe one is better at power conservation, another at performance, and 3 that are mostly rubbish except for some niche priority that only one person in a million cares about, and maybe 1 fries your motherboard under heavy load?


again, i think. not positive about any of that.

---

### Post by madjr on 2009-10-10
> [SIZE="4"]What do you guys think? Should we bring this over to Linux or am I beating a dead horse?[/SIZE] :confused:

yes please

i just wonder how would be the best way to implement it

---

### Post by Eisenwinter on 2009-10-10
I think the Linux kernel is far too evolved for this to be implemented currently.

The way the kernel handles devices and drivers will have to be changed, and I don't see the developers doing this right now, or even ever.

---

### Post by 3rdalbum on 2009-10-10
What exactly do you want to port to Linux? OpenSolaris kernel compatibility? A fixed ABI for drivers on Linux? The tool that says whether your hardware will work with OpenSolaris?

The Device Detection Tool runs on Linux anyway.

---

### Post by keiichidono on 2009-10-10
> **3rdalbum said:**
> What exactly do you want to port to Linux? OpenSolaris kernel compatibility? A fixed ABI for drivers on Linux? The tool that says whether your hardware will work with OpenSolaris?

The Device Detection Tool runs on Linux anyway.

I'd like the Device Driver Utility to be ported over to Linux. A stable ABI has been long discussed and I don't think we'll see one soon.

---

### Post by keiichidono on 2009-10-10
[bump]

---

