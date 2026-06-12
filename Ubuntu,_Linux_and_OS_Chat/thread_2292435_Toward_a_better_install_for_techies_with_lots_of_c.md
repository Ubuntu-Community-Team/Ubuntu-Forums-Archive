---
title: "Toward a better install for techies with lots of computers"
date: 2015-08-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Chalisque on 2015-08-28
Consider the following procedure given a new machine Newbie.
1. You have a simple bootable USB drive with a linux kernel and hardware detection software and nothing else. It boots, you give the machine a name, it runs hardware detection and saves the profile to the usb drive.
2. You stick this in a working linux machine Master (e.g. ubuntu, debian or centos).
3. You stick a sata hdd or sdd in to a usb enclousure and plug it in to Master (or plug many at once).
4. On the working linux machine (Master), which could sensibly have the entire repository on an hdd, or at least everything you personally would regularly install, the install enquires all the settings that the current install normally asks, at the start, then you hit go and it writes a working system image to the drive (using the data from the hardware detection usb drive for things like memory size, chipset, etc.)
5. You can test it by then disconnecting the usb enclosure from Master, plugging it into Newbie, and booting from usb.
6. Optionally, you can then take the hdd/ssd out of the enclosure and stick it in the actual machine and configure it's bios/efi to boot from it.

Why can't we make it that simple? (p.s. I am happy to do what I can to help develop such a system -- most of the working code to do it is of course already written in the current installer scripts, which are in python, so we really just need to dissect the current installer, write a few bits of code, stick it together.)

---

### Post by mastablasta on 2015-08-28
simple? I consider this complicated. 

get an OEM image (modify it if oyu wish to), clone it to how many devices you want at the same time and that's it. new user boots the image and it asks them for password and user name. that's it.

---

### Post by help_me2 on 2015-08-29
> **mastablasta said:**
> simple? I consider this complicated. 


I agree. How is that simple?

---

### Post by ian-weisser on 2015-08-29
I can see this sort of concept useful for installs that are off-network, and cannot be easily moved to go on-network.
However, for most off-network installs, I don't see how this method improves much over the existing installer. Perhaps that could be explained a bit more?

Seems like one main benefit is a centralized install machine instead of LiveUSB sticks (perhaps with preseed files). Perhaps that benefit could be explained more?

---

