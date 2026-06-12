---
title: "Installing from USB"
date: 2010-09-14
forum: Ubuntu Studio
---

### Post by RastaCalavera on 2010-09-14
I have tried to install Ubuntu Studio from a USB drive and have been having issues. I used Unetbootin to but it on the flash, but when I goto install it says it needs to grab files for the disk drive (there isn't one because I am installing form a USB) I choose to look on the media for "drivers" and the entire process is ruined. It doesn't crash it just won't finish installation and I am brought back to a menu and just forced to turn off my computer. Anyone have similar issues or know a work around besides buring a dvd?

---

### Post by C.S.Cameron on 2010-09-14
If you are unhappy with Unetbootin try the Startup Disk Creator on the Live CD.
Another option for Windows users is the Universal installer from PendriveLinux.com

---

### Post by snowpine on 2010-09-14
Is there a reason you cannot burn a DVD?

---

### Post by RastaCalavera on 2010-09-16
I will try pen drive. The only reason i am not burning a dvd is the lack there of and the unwillingness to buy some :P thanks for the replies i will let you know how it works out. Well i got some followers, is there a good (easy) way to delete old kernel images? My grub is getting crowded hahaha

---

### Post by utnubuuser on 2010-09-16
When you use Unetbootin, are there different versions of the .iso to choose from?  Might it be that? 

Unetbootin probably doesn't copy the live-Cd verbatim as does Ubuntu's USB-creator.
If the USB-flash boots, you might be able to use it to make a USB-flash through System>>Administration>>USB-creator (second flash-drive and USB slot?)

---

### Post by RastaCalavera on 2010-09-20
hmmm well still no luck. I think it has to do with the installation its self. It says it can't continue unless it can detect the cd-rom drive that has the data on it. I have both a cd and dvd rom drive but i am booting off the usb so I think it is just getting confused. Have any of you actually installed from a flash drive? I also burned a dvd to boot off of but my bios can't be set to choose a dvd drive. I can choose between cd rom drive, flash drive, network boot and hard disk but no dvd drive. I really want to try Ubuntu studio, this is frustrating. :(

---

### Post by Pablo_F on 2010-09-20
Hi, 

Don't desperate. There are two things you can do:

1) Install generic ubuntu and install the ubuntustudio metapackages later.

(I have not tried this):
2) Try this trick (or similar):
[http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/](http://coliena.com/blog/2010/05/how-to-install-ubuntu-10-04-on-a-netbook-with-full-disk-encryption/)

Seen here:
[http://ubuntuforums.org/showthread.php?t=1572216](http://ubuntuforums.org/showthread.php?t=1572216) (comment #5)

Cheers! Pablo

---

### Post by RastaCalavera on 2010-09-20
Great links! They were very informative I will hopefully find a solution soon!

---

### Post by mango42 on 2010-10-03
Having just attempted the same operation because my 32bit machine cannot burn DVDs (Unetbootin Ubuntustudio 10.04 32bit install from a USB stick), ISTM the problem *cannot* be solved until the installer code recognises that the install files are to be looked for *on the USB stick it booted from, rather than a non-existent DVD*!

From a cursory glance at the above links, I suspect they maybe not immediately helpful for *alternate* UStudio installs?

I imagine it is just a case of patience until some kind, vocational programmer finds the time and inclination to modify the installer code.

Patience and penguins go together ;-)

:popcorn:

---

