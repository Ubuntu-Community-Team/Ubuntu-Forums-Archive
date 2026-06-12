---
title: "Raring alternate iso?"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by bird1500 on 2013-03-21
Hi,
The install dialog from the daily live (amd64) ISO doesn't seem to pass past the 1st slide, after I hit "next" it stays the same forever.
Is there a solution for it? Alternate ISOs don't seem to exist any longer.

---

### Post by dino99 on 2013-03-21
google around "ubuntu boot option"

---

### Post by tancrackers on 2013-03-21
There are alternative downloads for Lubuntu, but I don't see any for Ubuntu. Sorry :(

---

### Post by bird1500 on 2013-03-21
> **dino99 said:**
> google around "ubuntu boot option"

Thanks, but I don't know what you mean, I don't have problems booting the live CD. While in live Desktop session I launch the GUI installer and it takes forever without any error messages.

---

### Post by dino99 on 2013-03-21
> **bird1500 said:**
> Thanks, but I don't know what you mean, I don't have problems booting the live CD. While in live Desktop session I launch the GUI installer and it takes forever without any error messages.

first try with acpi=off (but it can be something else too, depending on your hardware)

---

### Post by grahammechanical on 2013-03-21
Alternate images for Ubuntu are no longer produced. This is done to reduce the work load on the Ubuntu development community. Have you tried choosing Install Ubuntu instead of running from the Live Session? At the first purple screen press Enter. Then press enter again to select English as the default installer language. Then select Install Ubuntu from the TRY - INSTALL screen.

You may also need to try some of the F6 options available from the same TRY - INSTALL screen.

Regards.

---

### Post by Cheesemill on 2013-03-21
If the machine you are installing on has an internet connection you can use the mini CD.

This is exactly the same as the old alternate installer except that all of the required packages are downloaded rather than being on the CD.

You can find the mini iso here...

[http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-amd64/current/images/netboot/mini.iso) - 64-bit
[http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-i386/current/images/netboot/mini.iso) - 32-bit

---

### Post by bird1500 on 2013-03-21
Thanks anyone, issue solved.

At boot tried out:
- Install, no custom options, same issue.
- Install, custom option (1st one) "acpi=off", same issue
- Install, custom options 2nd, 3rd, 4th, 5th - worked! Don't know which one helped though.

---

### Post by ventrical on 2013-03-21
probably "nomodeset"

---

### Post by Rukiri on 2013-03-21
So let me guess, it freezes at "Preparing to install ubuntu" correct?  I've had this issue since 12.10 which the bug still persists into 13.04... 

Here's what worked for me, boot from the live dvd and click try ubuntu.
Open the terminal which is ctrl+alt+t and than see if you have any weird partitions or borked partitions by either using gdisk(need to install from .deb first) or just do df /dev/sdx where x is your hard drive. 

if everything looks okay don't click on the installer just type ubiquity --debug, for some reason this actually worked for me but if I click on the installer it won't (actually tested 3 times, ubiquity --debug solves the issue but the average user will see it as tiresome, have them install gentoo a few times and see if it's tiresome.)

---

### Post by bird1500 on 2013-03-21
Thanks, yes, there's the "Welcome.." screen, then the 2nd one says something like "Preparing to install" or so, and on this one I click "continue" which lasts forever.
And yes, I had the feeling it has something to do with not being able to handle the partitions properly, I got like 10 partitions.
I had this (or very similar) issue with previous versions of Ubuntu but they were fixed in time before release, so it seems like a recurring bug.

---

### Post by kevpan815 on 2013-03-21
As previously stated by Cariboo907 (One of the Moderators in this Sub-Forum) the BOTH the Alternate Installer AND the DVD Installer have been DISCONTINUED as of Ubuntu 12.10, AND the Features of those Two Downloads have been MERGED into the Desktop Installer. Otherwise you will need to Download 12.04.2 to find BOTH the Alternate AND DVD Installer.

---

