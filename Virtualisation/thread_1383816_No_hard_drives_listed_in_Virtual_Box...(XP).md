---
title: "No hard drives listed in Virtual Box...(XP)?"
date: 2010-01-17
forum: Virtualisation
---

### Post by anm112 on 2010-01-17
I finally got Virtual Box running XP on my Ubuntu installation, but I'm having a major problem with getting to my other hard drives.  In the past, all of my other drives are listed under a network shared location...but with this new install they are no where to be found.  I'm sure I'm missing something simple here...can anyone help?

Thanks.

---

### Post by anm112 on 2010-01-17
A related problem that I am also having is that I can not get usb devices to work.  For some reason my USB keyboard and mouse work fine, but my external hard drive, thumb drive, and other devices don't even show up.

---

### Post by AlexandreP on 2010-01-18
You may have to install Guest Additions to allow folder sharing between your VM and your host OS.

And USB support only works with the proprietary edition of VirtualBox, the one distributed directly from [VB's website]("http://www.virtualbox.org") and repository. The open-source edition (the one found in Ubuntu repository) does not support USB peripherals.

---

