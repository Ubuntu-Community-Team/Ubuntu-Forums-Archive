---
title: "How or Where to message ubuntu builders about what users need in the next ub release?"
date: 2015-04-06
forum: The Cafe
---

### Post by newbie14 on 2015-04-06
I want to tell them to please build and release an .iso image file for ubuntu desktop installer which will be optimised to work perfectly with rufus, usb booting tool. And also optimised to be installed in a flash disk instead of a hard disk. Example: I set up a Kingston flash disk to be a bootable usb with ubuntu installer, using rufus. When I boot the computer, I plugged in another flash disk, -say sandisk- and installed the entire ubuntu O.S to the sandisk flash disk. So my primary hard disk never touch any ubuntu O.S. I want to request them to build and release that.

Edit1: Or is it already existed? which ubuntu release which optimised to be set up as bootable usb flash-disk and optimised to be installed on usb flash disk?

My question is: How or where to message them?

---

### Post by ian-weisser on 2015-04-06
> **newbie14 said:**
> How or where to message them?
This forum is as good a place as any for drive-by feature requests (Improvements that you don't wish to develop yourself and subsequently contribute to Ubuntu)



> **newbie14 said:**
> ubuntu desktop installer which will be optimised to work perfectly with  rufus, usb booting tool. And also optimised to be installed in a flash  disk instead of a hard disk.
The current ubiquity installer will happily install .iso images to a flash drive, an SD card, or any other mountable storage. It's hidden behind an Advanced Settings button, since relatively few users seem to want to do that. It requires a minimal understanding of what 'mounting' and 'partitioning' are, and how to do them. Any user who wants to improve or simplify the process is, of course, welcome to contribute usability bug reports, or -better yet- appropriate improvements to the ubiquity source code.


How, exactly, do the current .iso images not work with rufus?

---

### Post by newbie14 on 2015-04-06
> **ian-weisser said:**
> How, exactly, do the current .iso images not work with rufus?

It actually works well so far, so far so good. I have been using ubuntu via flash disk for a few weeks. But a few days earlier last week, I tried to turn the flash disk I installed ubuntu upon to become a regular usb flash disk again, so windows can detect it as a regular storage device. (before turning / changing the flash disk, windows cant read it and demanded that I should format it). Now that I have formatted the flash disk containing the ubuntu bootable desktop, My flash disks capacity shrink, from 32 GB (only 28 GB usable) to only 24 GB Usable.

the shrinking of the capacity is a bit unrelated, but I was ready and aware for that. But the ubuntu 12.10 I installed on the flash disk worked pretty well.

I want to build ubuntu myself, but I am still a very beginner. Maybe if I can learn in this forum, reading step by step answers, some day I will be able to build ubuntu myself.

---

### Post by grahammechanical on 2015-04-06
The installer in Ubuntu is called Ubiuity.

[https://wiki.ubuntu.com/Ubiquity](https://wiki.ubuntu.com/Ubiquity)

But actually, your request is nothing to do with the Ubuntu installer. Is it? But with Rufus not working well with the Ubuntu ISO images. 
> 
[h=4]System Requirements:[/h] 		Windows XP or later, 32 or 64 bit doesn't matter. Once downloaded, the application is ready to use.



> It can be especially useful for cases where:			


[LIST]
[*]you need to create USB installation media from bootable ISOs (Windows, Linux, UEFI, etc.)
[/LIST]


[https://rufus.akeo.ie/](https://rufus.akeo.ie/)

So, if you are finding that Rufus is not living up to the claims made for it by the developers, then report a bug with the Rufus developers.

Regards.

---

