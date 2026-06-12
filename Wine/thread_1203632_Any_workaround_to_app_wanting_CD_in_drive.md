---
title: "Any workaround to app wanting CD in drive?"
date: 2009-07-03
forum: Wine
---

### Post by Beowulf.1000 on 2009-07-03
Running Wine and also Virtual Box under Ubuntu 9.04. Application is "Final Draft 6" screenwriting software for MS-Windows. I snatched up a copy of FD6 because I saw on the Wine database that FD6 has a Gold rating, the only catch being it requires the original CD to be in the CD-ROM drive in order to run the software. Same thing if I try to run FD6 inside Virtual Box running a WindowsXP machine. I can install FD6 in Wine and also in Virtual Box (WindowsXP), I just can not run it unless I have the original CD in the drive (this is legal, I have the original CD, it is just inconvenient to have to have it in the CD).

Is there any sort of workaround someone can think of to bypass this, it would be very inconvenient to have to always have the original CD in the drive. (I do not want to use Celtx, been there, tried that; actually my main screenwriting software I have been using is Movie Magic Screenwriter 6, but it has rather sophisticated anti-piracy things it does to the Windows registry and such and there is no way it will run in Wine, or Virtual Box.

---

### Post by beastrace91 on 2009-07-03
Perhaps trying making an ISO of the image and try passing that through to Virtual Box as the disc image? That *might* work. And I know what you mean, carrying around CDs is very annoying.

~Jeff

---

### Post by Beowulf.1000 on 2009-07-03
Yup, that worked! I used k3b to make an ISO of the Final Draft 6 CD, the copied that iso file to ~/.VirtualBox then ran Virtual Box and told it to mount the iso image instead of the CDROM drive. Started up the virtual machine (WindowsXP) and ran the installed Final Draft 6 (which for the record I did install using a legal license) and it runs just fine. Screenwriting software was one thing really keeping me from booting into Linux; that, and video editing software like Sony Vegas, but I am pretty much decided to just focus on screenwriting and let filmmaking go.  

Off Topic: I am so disappointed in MS Windows wanting to suck my wallet try yet again with Windows 7, after I just paid a bundle of cash for Windows Vista ULTIMATE about 3 months ago (yeah, I have had to run MS WIndows, for Sony Vegas, Soundforge, After Effects; but by letting go of filmmaking I will rarely need to run Windows hopefully in the near future). I emailed Microsoft and told them such, and that I would just migrate to Linux. They did reply a couple of times.

> **beastrace91 said:**
> Perhaps trying making an ISO of the image and try passing that through to Virtual Box as the disc image? That *might* work. And I know what you mean, carrying around CDs is very annoying.
~Jeff

---

### Post by Beowulf.1000 on 2009-07-03
What is cool too is that I just downloaded the demo trial version of Final Draft 8 to WindowsXP running as a virtual machine in VirtualBox of Ubuntu 9.04, and it installed no problem, runs no problem, saved a script, printed to PDF, etc. Allows entering a license key that can be purchased, so I guessing this could allow seamless easy activation of the already installed demo version, should I want to pay and get Final Draft 8.

And related to this-- (great news for screenwriters), I was also easily able to install Character Writer (there is a linux version!) for character development in stories, and also Contour software by Mariner software which is story development software; Contour is windows software but it installed easily in VirtualBox; I will try it using wine next. I am just so glad I have all my screenwriting software tools running in Linux.

---

### Post by Th3_uN1Qu3 on 2009-07-03
Heh, all programs run in a virtual machine untill you actually get to do any serious work with them. Unless you have a really fast machine it's never going to be anywhere near native speed. At least if we had graphics card virtualization - now that would really be something.

However, with Wine's progress, things are looking good for Linux users indeed.

---

