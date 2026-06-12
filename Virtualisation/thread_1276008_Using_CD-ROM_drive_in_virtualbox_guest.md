---
title: "Using CD-ROM drive in virtualbox guest"
date: 2009-09-26
forum: Virtualisation
---

### Post by nmccrina on 2009-09-26
Hi!

I have Windows Vista running in virtualbox. I'm trying to install MSOffice from a CD, but Windows does not recognize the drive. I found this thread: 

[http://ubuntuforums.org/showthread.php?t=386584]("http://ubuntuforums.org/showthread.php?t=386584")

This seems pretty simple, but in my case it does not work. I did the solution in that thread, replacing sr0 in the virtualbox xml file with my CD-ROM device (scd0, according to fstab). Unfortunately, whenever I change the xml file, virtualbox disables the CD-ROM drive; however, if I then enable the drive in virtualbox it replaces my edit with the default sr0 device. Either way, Windows cannot read the CD-ROM drive.

Any ideas? Is there a way to make my CD-ROM drive sr0 instead of scd0 so that the virtualbox default works?

---

