---
title: "dd .img file to usb"
date: 2011-06-24
forum: The Cafe
---

### Post by vishnumrao on 2011-06-24
Just bought a Hitachi coolspin 2Tb drive. I need to run Hitachi's Drive Fitness Tool before I put any data on it.

[http://www.hitachigst.com/support/downloads/#DFT](http://www.hitachigst.com/support/downloads/#DFT)

Although their website has instructions to dd to a floppy disk drive, I dded the image to a USB. 

Problem: I tried to boot the USB off of many computers, desktops, laptops, netbooks etc. It does not boot from any of them, but one HP mini netbook.

I can't figure out why. Any ideas anyone?

---

### Post by Legendary_Bibo on 2011-06-24
Cafe isn't support.

---

### Post by NightwishFan on 2011-06-24
> **Legendary_Bibo said:**
> Cafe isn't support.
Just use report and the mods will move it.

> Problem: I tried to boot the USB off of many computers, desktops, laptops, netbooks etc. It does not boot from any of them, but one HP mini netbook.
If it can boot you did it right. Does it always boot on the one machine or just once?

---

### Post by vishnumrao on 2011-06-24
I wasn't sure where to post it. Its not a Ubuntu question to be put in the Ubuntu support categories. Let the mods decide where to move it to.

Well, on the HP mini netbook, it consistently boots, but its no use. I tried to run the DFT by hooking it to a external hdd case. But the tool detects hdds only if they are connected to the SATA port. 

But on other computers I can't boot of the USB.

---

### Post by cariboo on 2011-06-24
This really doesn't fit in any of the support categories, so this is a good a place as any. What I do is create a bootable iso using Nero (Linux or Windows) as Hitachi's utilities don't, and include the utilities in the iso.

I've serviced Hitachi products for longer than I care to remember, and their end-user support has always been terrible, if it wasn't for the people that work for them, I would have stopped servicing their stuff a long time ago.

---

### Post by mips on 2011-06-24
I doubt the floppy disk image has the required support files to boot from usb.

---

### Post by vishnumrao on 2011-06-24
@cariboo907 How do you create a bootable iso from the img file? BTW, they already have a .iso file available for download, which can be burnt to a cd. I don't want to go this route. I like the live-usb concept, its "greener".

What Hitachi products have serviced? I have had 6 Hitachi hard drives, and they run like great.

@mips: I can successfully boot off the USB on one netbook. No problem. But not on any other machine.

---

### Post by cariboo on 2011-06-24
The iso's on Hitachi's web site don't boot whether burned to a CD or put on a usb thumb drive, at least the ones I tried several weeks ago didn't. What I was trying to build, was a multiboot CD with all the various Hard drive testing utilities from the various manufacturers, all of them booted except for the Hitachi disk fitness utility. What I had to do was create a bootable CD using one of the boot images from [here]("http://www.bootdisk.com/bootdisk.htm"), then starting the disk fitness utility from the command prompt.

I see the page has been updated, and now there is an .img file that you should be able to use with unetbootin, which is in the repositories to create a bootable usb thumb drive. The images are [here]("http://www.hitachigst.com/support/downloads/")

---

