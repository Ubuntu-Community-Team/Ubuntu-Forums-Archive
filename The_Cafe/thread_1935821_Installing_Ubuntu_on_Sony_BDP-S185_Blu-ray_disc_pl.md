---
title: "Installing Ubuntu on Sony BDP-S185 Blu-ray disc player?"
date: 2012-03-05
forum: The Cafe
---

### Post by honeybear on 2012-03-05
Hello,

Since it is a nice hardware, I would like to know if it is possible to run / or install Mythtv or any multimedia linux center ? The best would be ubuntu

Thanks

---

### Post by Nixarter on 2012-03-05
well, you should be able to connect it with dlna to your nixbox, but running anythign on the device itself would be highly problematic.  They sign everything and you're have to either make a physical hack to bypass that or get the encryption keys used to sign the code.  There is a chance that the ps3/psp keys that were hacked are the same, and you can sign your own code, but I doubt it.  The tv and gaming are completely separated at sony.  They don't really work with each-other aside from sharing documentation when they need tech for a project.

---

### Post by honeybear on 2012-03-06
> **Nixarter said:**
> well, you should be able to connect it with dlna to your nixbox, but running anythign on the device itself would be highly problematic.  They sign everything and you're have to either make a physical hack to bypass that or get the encryption keys used to sign the code.  There is a chance that the ps3/psp keys that were hacked are the same, and you can sign your own code, but I doubt it.  The tv and gaming are completely separated at sony.  They don't really work with each-other aside from sharing documentation when they need tech for a project.

thanks how would you perform installing and which distro of Linux?

---

### Post by whatthefunk on 2012-03-06
What would be the advantage of doing this?

---

### Post by 3rdalbum on 2012-03-06
> **honeybear said:**
> thanks how would you perform installing and which distro of Linux?

If you don't already know, then you are not knowledgeable enough to do it. You could not do it without learning the most intimate details of how the hardware works, and then writing very low-level software in Assembly.

Besides, I suspect a Bluray player would not have enough RAM for any modern Linux desktop.

---

### Post by honeybear on 2012-03-07
> **3rdalbum said:**
> If you don't already know, then you are not knowledgeable enough to do it. You could not do it without learning the most intimate details of how the hardware works, and then writing very low-level software in Assembly.

Besides, I suspect a Bluray player would not have enough RAM for any modern Linux desktop.

Ram is indeed an issue with all those devices. Maybe NetBsd? 

Look for instance PS1 can be intalled linux on it, a tiny linux version.

How do you boot the USB pendrive (Link: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)), because the machine at boot does not prompt select bootable media ?

---

### Post by LowSky on 2012-03-07
Three questions I see a lot, "will it blend," "can I install install Linux on it," and "Yeah, but can it run Crysis."

I understand we in the age where people can install a different ROM on their phone, run routers with open-source firmwares, and build robots that use console game machine hardware as eyes, but to what end do we need to turn a run-of-the-mill optical media player into a full blown PC?

---

### Post by honeybear on 2012-03-07
> **LowSky said:**
> Three questions I see a lot, "will it blend," "can I install install Linux on it," and "Yeah, but can it run Crysis."

I understand we in the age where people can install a different ROM on their phone, run routers with open-source firmwares, and build robots that use console game machine hardware as eyes, but to what end do we need to turn a run-of-the-mill optical media player into a full blown PC?

full blown PC, is offering few disavandtages. 

Let's install Linux everywhere. Even into your modern media fridge!!

Linux forever. Hey guys Support LiNUX on all platforms!

---

### Post by VMC on 2012-03-07
I just now took my BDP-S185 apart to see what's inside. Apart from the drive, there is a small amount of ram to buffer the blue ray drive and Sony's proprietary chip.
 I see now way to install any OS.

---

### Post by 3rdalbum on 2012-03-08
The player is not designed to be able to run anything except the operating system provided on the chip. It's not as easy as "Insert USB stick with Ubuntu and change BIOS settings to boot from it" - the unit is hardwired to boot from its Flash ROM.

You would have to find a way to reflash the flash ROM with a custom-written bootloader (not GRUB or anything else that currently exists) that can access the USB port and convince the CPU to start running code from the USB port.

Oh, and you'd have to reverse-engineer the video output chip and write a framebuffer driver so that Linux can actually display text or images onto your TV screen.

You'd have to be a pretty talented programmer to do this. It's certainly not impossible to hack a Bluray player to run custom code, but few if any people on the forum possess the skill to do this.

---

### Post by ARooster on 2012-03-08
> **LowSky said:**
> Three questions I see a lot, "will it blend," "can I install install Linux on it," and "Yeah, but can it run Crysis."

I understand we in the age where people can install a different ROM on their phone, run routers with open-source firmwares, and build robots that use console game machine hardware as eyes, but to what end do we need to turn a run-of-the-mill optical media player into a full blown PC?


I imagine the answer could be the one the late George Herbert Leigh Mallory gave to the question of why he  wanted to climb Mount Everest... because it's there :)

Having said that, I'm a person who believes that Apple is trying to reinvent the wheel by making it oval-shaped with their iPad. Or putting it more directly, it's not really progress unless it actually offers advantages over existing technology :)

---

### Post by honeybear on 2012-03-11
> **VMC said:**
> I just now took my BDP-S185 apart to see what's inside. Apart from the drive, there is a small amount of ram to buffer the blue ray drive and Sony's proprietary chip.
 I see now way to install any OS.

Have you seen how silent it the BDP-S185? It makes absolutely no noises. It could be also cool for a server side machine (email, chat, apache, ...)

---

### Post by honeybear on 2012-03-12
> **3rdalbum said:**
> The player is not designed to be able to run anything except the operating system provided on the chip. It's not as easy as "Insert USB stick with Ubuntu and change BIOS settings to boot from it" - the unit is hardwired to boot from its Flash ROM.

You would have to find a way to reflash the flash ROM with a custom-written bootloader (not GRUB or anything else that currently exists) that can access the USB port and convince the CPU to start running code from the USB port.

Oh, and you'd have to reverse-engineer the video output chip and write a framebuffer driver so that Linux can actually display text or images onto your TV screen.

You'd have to be a pretty talented programmer to do this. It's certainly not impossible to hack a Bluray player to run custom code, but few if any people on the forum possess the skill to do this.

would you know if it exists bluray players that could be installed Linux on it or eventually NetBsd (certainly more suited) ? could be cool

---

### Post by Dry Lips on 2012-03-12
I want to install Ubuntu on my electric toothbrush! I'm thinking that my teeth probably would get a lot cleaner if I did. There's a lot of good dental hygiene in Open Source!

/just kidding \\:D/

---

### Post by honeybear on 2012-03-12
Here is the manual of hte BDP-S185.
[http://pdf.crse.com/manuals/4290282112.pdf](http://pdf.crse.com/manuals/4290282112.pdf)

THere is no single information about NFS or SAMBA.

Can the sony player play videos on an UBUNTU Samba file server?

---

### Post by whatthefunk on 2012-03-12
I dont understand why you want to put Linux on this thing.  It is a Blue Ray Disc player.  It is designed to play Blue Ray Discs, that is all.  Im assuming that it plays discs fine, so why bother trying to make it something its not designed to be?  Its like trying to make a shoe into a sweater just for the sake of it....

---

### Post by honeybear on 2012-03-12
> **whatthefunk said:**
> I dont understand why you want to put Linux on this thing.  It is a Blue Ray Disc player.  It is designed to play Blue Ray Discs, that is all.  Im assuming that it plays discs fine, so why bother trying to make it something its not designed to be?  Its like trying to make a shoe into a sweater just for the sake of it....

Linux could be simply better, no? Why not installing Mythtv if it would have been possible. I saw that it has too little ram. 

You could have a silent file server for only 50 euros. So that's a fair price

---

### Post by honeybear on 2012-03-25
I am trying to play avi's from my Canon camera with this Sony BDP-S185 Blu-ray disc player. Man, it has really nothing like codecs this sony box. 

I wish I could use linux on it if it would have been possible. Or to flash the rom from an official sony rom from sony.com with more codecs.

This sony box can play videos from one camera I have but the other one, no way. Pitty not to watch vacation videos on tv ...:(

---

### Post by KiwiNZ on 2012-03-25
you would gain precisely nothing. Also the device is probably already running a modified Linux based Firmware.

---

### Post by sffvba[e0rt on 2012-03-25
Maybe... just maybe if you follow the same method as described here you can get it to work - [Link]("http://www.strangehorizons.com/2004/20040405/badger.shtml") YMMV...


404

---

### Post by honeybear on 2012-03-26
It is indeed true. Man, if they have put Linux on it, at least they could have installed w32codecs :)

---

### Post by KiwiNZ on 2012-03-26
> **honeybear said:**
> It is indeed true. Man, if they have put Linux on it, at least they could have installed w32codecs :)

it's an Appliance designed for one task, play Blu-Ray disc's. Why would they waste time adding features not required for the task. This would raise the development and support cost and increase the retail price.

---

### Post by knight2000 on 2012-03-28
I'm not gonna shoot down your ideas. Sadly people here are repetitively very quick to pour water on peoples hobbies on this board. 

The first thing you should do is get a hold of the firmware for this device. Read the license agreement and find out what the rules are regarding reverse engineering are. Sometimes they can be quite strict.

Get as much information as you can about the firmware, using a hex editor if necessary. A key thing to do is try and find other people who are interested or have been working with that platform. They might have already made some progress customising that appliance so their information could be valuable. They might also know to what extent things have been locked down by Sony 

You'd also need to do a little digging to find out if the Ubuntu kernel can handle the hardware that the appliance contains. Does Ubuntu support that CPU architecture? Will there be extra drivers required for some hardware components? Do you have the ability to write those drivers or know people who can write the drivers?

If you have a look at those things then it will be easier to asses the possibilities of such a project. Good luck, and don't be discouraged by Negative Nigels.

---

