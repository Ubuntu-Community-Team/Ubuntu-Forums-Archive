---
title: "update bios on MSI mb from a bootable flash dos drive?"
date: 2012-12-13
forum: The Cafe
---

### Post by sdowney717 on 2012-12-13
[http://msi.com/service/biosupdate/](http://msi.com/service/biosupdate/)

I may need to do this so how do you create a usb dos bootable drive?
I do have access to win7 and ubuntu pc's.

---

### Post by CharlesA on 2012-12-13
It would be easier to do option #3 and just throw the BIOS file on a thumb drive, boot into the BIOS and update that way.

All of the new mobos I have looked at have that feature.

Oh and don't forget:

>  WARNING!!!!!

DON'T FLASH WHEN YOUR SYSTEM IS RUNNING FINE!!!!

DON'T FLASH IF YOU DON'T KNOW WHAT YOU ARE DOING!!!!

---

### Post by sdowney717 on 2012-12-13
[http://forum-en.msi.com/faq/article/how-to-flash-the-bios-successfully](http://forum-en.msi.com/faq/article/how-to-flash-the-bios-successfully)

very discouraging to see that they dont recommend using their own utilities!

> How to flash the BIOS successfully
Author	 Stu on 19 March, 2011 | Print | Bookmark
We do not recommend using the MSI LiveUpdate tool to update your BIOS! It may be okay for updating your drivers, but please do not use it to flash the BIOS in Windows! It is also not recommended to flash BIOS direct from a floppy disk, as a bad floppy can cause a bad flash which will kill your board!

Windows-based flashing - If you REALLY insist on flashing the BIOS under Windows, if you encounter any error during flashing, whatever you do, DON'T restart your PC! Try again until the flash is successful, otherwise your board will not start!

Boards with built-in M-Flash function - While this is a nice idea, at the moment we are seeing many cases of users using M-Flash to update their BIOS and having problems, so at present we don't recommend people use M-Flash either!


The safest way to flash your BIOS is to use our own MSI HQ Forum USB BIOS Flash Tool, developed by our own Svet.

---

### Post by CharlesA on 2012-12-13
Wow. That makes me glad I stick to Gigabyte and ASUS mobos...

---

### Post by grahammechanical on 2012-12-13
This makes me glad that I have been too nervous to attempt a BIOS flash in the five years I have had my motherboard:

> DON'T FLASH WHEN YOUR SYSTEM IS RUNNING FINE!!!!

It is still running fine.

Regards.

---

### Post by sdowney717 on 2012-12-13
The recommended link to svet way requires a login!
here is another way
[http://msi.com/service/biosupdate/](http://msi.com/service/biosupdate/)

Part of my wondering is I am getting a new MSI 760GM E51

[http://www.amazon.com/MSI-Computer-Motherboards-760GM-E51-FX/dp/B006MCSGZQ](http://www.amazon.com/MSI-Computer-Motherboards-760GM-E51-FX/dp/B006MCSGZQ)

And when reading a comment there, a user said MSI with the FX AMD CPU may need the bios updated.

[http://www.amazon.com/review/R3NWWWYNNO5UWV/ref=cm_cr_dp_cmt?ie=UTF8&ASIN=B006MCSGZQ&nodeID=541966&store=pc#wasThisHelpful](http://www.amazon.com/review/R3NWWWYNNO5UWV/ref=cm_cr_dp_cmt?ie=UTF8&ASIN=B006MCSGZQ&nodeID=541966&store=pc#wasThisHelpful)


> Initial post: Aug 23, 2012 2:29:07 PM PDT
linksith says:
The FX processors have had a few problems in the past but there is good news concerning that. I am a proud owner of the AMD FX 8150 and have recognized that it is mainly BIOS issues and is why MSI has been posting BIOS updates on their website to fix such issues. For those who are reading the comment and have experienced some of these problems I have posted a link to these driver updates for all CPU's supported by this motherboard below...
[http://msi.com/product/mb/760GM-E51--FX-.html#/?div=CPUSupport](http://msi.com/product/mb/760GM-E51--FX-.html#/?div=CPUSupport)

---

### Post by lykwydchykyn on 2012-12-13
I usually download an image of FreeDOS (there's a boot floppy image called "Balder" that you can get), then use K3b to create a bootable CD with the downloaded image as the boot image.  The bios utilities and data can just go on the CD like usual.

Then boot balder, run "loadcd.bat", switch to the D:\ drive and run the utilities.

I haven't had much luck getting freedos to boot from USB, unfortunately, but it may just be the (typically old and clunky) systems I work with.

---

### Post by sdowney717 on 2012-12-13
Link to the svet bios tool
[http://forum-en.msi.com/index.php?topic=108079.0](http://forum-en.msi.com/index.php?topic=108079.0)

What you do is run the tool on a windows PC to create a bootable USB flash drive.
Use the downloaded bios from MSI.

Then take the USB flash drive to the MSI PC and boot from it. And it upgrades the bios

This tool will create the USB drive on any win 64 bit PC, but if the OS is 32 bit, then the pc's board to create the bootable drive has to be MSI.

---

### Post by lykwydchykyn on 2012-12-13
If you have an actual BIOS payload (rather than a payload bundled in a flash utility exe), the "flashrom" utility in the repositories might very well work.  It's probably not recommended or supported by the manufacturer, though.

---

### Post by mips on 2012-12-13
Google 128MB DOS image. It's actually a lot smaller than that.

---

