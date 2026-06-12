---
title: "What makes Linux Tick?!"
date: 2005-06-04
forum: The Cafe
---

### Post by maspro on 2005-06-04
What exactly makes Linux do the things it does? Is Linux nothing more then a kernel upon which different packages are set up? 

If enough packages are lifted to a higher version, while the kernel stays at the same version, would it be possible to make a complete new distribution with new features?

What makes that some Linux distributions are more automated then others? Is it the kernel or the packages?

What is the difference between Warty, Hoary and Breezy, is it just adjustments in packages that provides newer features?

What makes the whole stick together?

 ;-)

---

### Post by jdong on 2005-06-04
[QUOTE=maspro]What exactly makes Linux do the things it does? Is Linux nothing more then a kernel upon which different packages are set up? 
[/quote]
Correct. Linux technically is the name of the kernel ONLY. In other words, only /boot/* and /lib/modules/* is Linux. Everything else are the packages that take advantage of the kernel. For that reason, it's more correct to call a Linux distribution like Ubuntu GNU/Linux.

> 
If enough packages are lifted to a higher version, while the kernel stays at the same version, would it be possible to make a complete new distribution with new features?


Sure. Look at the Ubuntu Backports Project, which provides package updates for stable Ubuntu releases.

Also, derivative distributions, like Guadalinux and Kubuntu, build packages on top of the Ubuntu base.

> 
What makes that some Linux distributions are more automated then others? Is it the kernel or the packages?

Mostly the packages. SuSE, Mandrake, and Fedora (RedHat) have all invested significant time and development effort in new GUI administration tools, and self-maintainance.

> What is the difference between Warty, Hoary and Breezy, is it just adjustments in packages that provides newer features?
New kernels, new features, newer packages. :)

> 
What makes the whole stick together?

 ;-)
The hard work of distribution developers :)

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=maspro]
What makes the whole stick together?

 ;-)[/QUOTE]

Users. Users that give back make Linux tick. A patch here, some backporting there (looking at jdong). Linux works as well as it does because many users love it for what it is (a free OS) and they try to improve it.

---

### Post by crane on 2005-06-04
Gremlins :)

---

### Post by az on 2005-06-04
If you want to know why it is that so many disparate peices can work together, well, that is the nature of source code and the tools that have developed to make such software.

If you want to know why open source software works, (better than other development models) read the cathedral and the bazaar, by Eric Raymond.   You can google for it and it should take you a half an hour to read it and get it.

---

### Post by Brunellus on 2005-06-05
[QUOTE=crane]Gremlins :)[/QUOTE]
 You are not yet ready for MOGWAI! (or at least, as ready as Linux is for the desktop :P   )

---

### Post by Lovechild on 2005-06-05
sssh.. don't you know that all electronics are filled with little people.. that's why Japanese people make the best stuff, they are so small - gets them closer to the electronics

---

### Post by maspro on 2005-06-05
Hmm, so for example if I plug-in an usb flashdrive and it is automatically recognized and automatically mounted, then that's the packages at work? 

So in short, Linux without the packages is worthless?!

---

### Post by Lovechild on 2005-06-05
[QUOTE=maspro]Hmm, so for example if I plug-in an usb flashdrive and it is automatically recognized and automatically mounted, then that's the packages at work? 

So in short, Linux without the packages is worthless?![/QUOTE]

For the example given:

Gnome-volume-manager -> HAL -> kernel

Just like the Windows kernel itself is useless to the enduser, yes..

Kernel space is generally preceived as useless since it doesn't do anything the user sees, whereas userspace does (things like X, GNOME, OpenOffice.org, etc.). The kernel has many applications, e.g. it contains the stuff that makes your system able to talk to the hardware (namely drivers).

---

### Post by jdong on 2005-06-05
[QUOTE=maspro]Hmm, so for example if I plug-in an usb flashdrive and it is automatically recognized and automatically mounted, then that's the packages at work? 

So in short, Linux without the packages is worthless?![/QUOTE]

No. This is how the flashdrive thing works:

1. Kernel supports an interface called "hotplug", which allows user-space programs to be notified to hardware events (i.e. new USB device). In this case, the kernel sends out a message (via /sys) that there's a USB attach event.

2. The userland hotplug listener hears about the USB attachment, and finds an appropriate device driver for the hardware. In this case, it's the module "usb_storage". The userland hotplug proceeds to load the USB Mass Storage driver into the kernel.

3. Dbus and HAL are now aware about a new removable storage device, and go and alert GNOME's gnome-volume-manager about the new device. Fstab entries are auto-created, and the icon pops up. In addition, g-v-m can be configured to automount the device.

---

### Post by maspro on 2005-06-05
Cool thx for explaining. It's always nice to know how things work at a deeper level. 

So the reason why one Linux distro is different from another is the way packages are set up by the manufacturer. In essence all Linux distro's are the same, but it's the tweaks, customisations and specific packages that are used in combination with custom kernel patches and customisations that make a difference?

Does this sound about right?  ;-)

---

### Post by tread on 2005-06-05
Yep, that sounds right. 

Each distribution usually has a specific aim in mind and works towards it, debian wants stability, ubuntu wants everything to just work, gentoo wants you to do almost everything :) and so on ..

---

### Post by allforcarrie on 2005-06-05
chewing gum.

---

### Post by jdong on 2005-06-06
[QUOTE=maspro]Cool thx for explaining. It's always nice to know how things work at a deeper level. 

So the reason why one Linux distro is different from another is the way packages are set up by the manufacturer. In essence all Linux distro's are the same, but it's the tweaks, customisations and specific packages that are used in combination with custom kernel patches and customisations that make a difference?

Does this sound about right?  ;-)[/QUOTE]
Precisely. That's why seasoned Linux users get ticked when a user asks which is the "best" distribution, or claim one distribution has some 'new feature' that's not in another distribution. In reality, you can splice as many distributions together as your free time allows!


BTW, don't make the distribution developers' job sound so easy... In reality, there's a lot of work that goes into the tweaks and customizations ;)

---

### Post by allforcarrie on 2005-06-06
so tecnicly all you have to do is change packages and you have a new distro IE Ubuntu+KDE=Kubuntu.

---

