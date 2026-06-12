---
title: "elementaryOS installer crash."
date: 2014-08-25
forum: Ubuntu/Debian BASED
---

### Post by shiftyninja on 2014-08-25
I've been trying to install elementaryOS LUNA 64bit on my machine. I am currently running Ubuntu 14.04 64 bit without any issues.   When attempting to install from a usb drive I get 'NO DEFAULT UI OR CONFIGURATION DIRECTIVE FOUND'... I tried fiddling with the file names from isolinux to syslinux with no avail.

I've burned both the direct download iso's and torrents to dvd and got a little farther but it fails with this error.

[IMG]http://i58.tinypic.com/fz69lz.jpg[/IMG]

I was directed to try installing the 32bit version and that failed as well. It hangs at the initial install screen.

Machine stats:

ASUS P5N32 board,
Intel® Core™2 Quad CPU Q6600 @ 2.40GHz × 4,
4gb ram,
nVidia GFORCE video card.


Like I said, everything works perfectly fine in Ubuntu 14.04 *64* BIT... Not really sure how to resolve the issue.

---

### Post by overdrank on 2014-08-25
Moved to Other Operating Systems and Projects

---

### Post by christopher9 on 2014-08-25
Luna is based on such old repositories and kernel that you really would be better waiting for Freya to stabilize since its based on much more up-to-date software...you CAN load the Freya beta iso to USB and try it out but it's still buggy enough I would only use it inside VirtualBox or similiar....it blew up my UEFI laptop when trying to install it from USB and so corrupted the bootloader on Ubuntu so I that had to kill partitions and re-install to blank HDD...YMMV

---

### Post by Stinger on 2014-08-25
Things that make you go hmmmmm.... ;)

It should be possible to install Luna 64bit on that pc without trouble.
Did you have Ubuntu 12.04 installed before 14.04 ?

---

### Post by shiftyninja on 2014-08-25
Stinger, no. I was using Windows 7 Ultimate, wiped my entire machine and started from scratch with Ubuntu 14.04 64bit. Install went through first time with no issues.

---

### Post by coffeecat on 2014-08-25
I've removed a couple of unhelpful posts and the OP's responses in order to tidy this thread up.

@shiftyninja, sorry about that. You are very welcome to ask for support for operating systems that are not Ubuntu or the official flavours. This is why we have this "Other Operating Systems and Projects" section. The main sections are for Ubuntu and the official flavours only, which are listed in the section headers. You may find, however, that the Elementary OS channels of support may be better, if only because few people here would be using Elementary. In any event, good luck in finding a solution.

---

### Post by Stinger on 2014-08-26
Looking at the picture in the OP, I would say that it's most likely a problem with the install image, a faulty iso file or a problem with the DVD media. Could be the burning process, could be a faulty disc or a read error from the DVD drive reading the disc.  
The USB thing is a different story. How did you create the live USB-pen ?
Did you follow [the guide from elementary]("http://elementaryos.org/docs/user-guide/creating-an-install-disk") ? ( scroll down to where it says 'Creating a Bootable USB' )
I use the dd command myself to create a live USB-pen, works every time but you need to be careful and choose the right drive.
I prefer USB and would go for that.

---

