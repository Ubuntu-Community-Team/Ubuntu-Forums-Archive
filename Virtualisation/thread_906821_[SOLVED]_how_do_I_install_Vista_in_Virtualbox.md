---
title: "[SOLVED] how do I install Vista in Virtualbox"
date: 2008-08-31
forum: Virtualisation
---

### Post by charonred on 2008-08-31
I've spent hours trying all sorts of things to get Vista to install as a guest OS in Virtualbox, but when Virtualbox tries to mount the .iso, I get the message that there is no bootable media ?

Looking at the Vista disc; it has a setup.exe, but Virtualbox fails to boot the .iso - so how do I get access to the disc to run the setup file and install Vista as a guest OS in Virtualbox

---

### Post by mellowd on 2008-08-31
Try booting off the original CD itself

---

### Post by charonred on 2008-08-31
Tried that as well, get same message - no bootable media ?

---

### Post by benerivo on 2008-08-31
Do any other iso's work in virtualbox or is it just the vista one that fails?

---

### Post by charonred on 2008-08-31
I have XP Pro installed and running fine with Dreamweaver MX2004 and some other apps.

Just thought I'd try some of my other OS's in Virtualbox; it'd be great if I could have them running at same time on one desktop.

Going to try Win95/98 and 3.11 as well, just to see how they go on new hardware ;)

---

### Post by charonred on 2008-09-01
installed via work around - tried cloning the XP .vdi, but that had all sorts of errors when trying to run, so nuked that idea.

Ended up doing it the long way around; created a new 'machine' and installed XP all over again to it, then did an upgrade to Vista (hell of a lot faster than installing either of them natively on a drive). 

Going out for a while now, when I get back I'll do the Vista SP1 install (wonder how much faster that is than the approx 2 hours natively)

---

### Post by mellowd on 2008-09-01
Hmm, strange indeed. At least it's now working though

---

### Post by charonred on 2008-09-01
Vista SP1 only took 30 minutes in VirtualBox; compared to nearly 2 hours natively on a friends PC and notebook.

---

### Post by tuxulin on 2008-09-01
did you get win 98 or 95 installed yet ?
i would love to know.

LOL

Tuxulin

---

### Post by charonred on 2008-09-01
not as yet, but will try in a couple of hours when I get back home.

---

### Post by mellowd on 2008-09-01
tbh, I'd love to install windows 3.11 for a laugh. I can hardly remember the interface

---

### Post by charonred on 2008-09-01
yeah, I'll get around to that.

It maybe a bit fiddly as I have all the floppy discs and also have then on a CD (disk1, disk2 etc), but will have to make the CD bootable so I can save the .iso for Virtualbox to install from.

Would appreciate any tips on how to do that; I have N-lite on my old XP install, but not sure how to 'script' it to boot the setup.exe file.

---

### Post by charonred on 2008-09-02
Bit of a hiccup here; N-lite doesn't support Win 3.11 or Win 95/98, so that idea's nuked. 

Also, both my Win95 & 98 CDs require a boot floppy (most CDs weren't bootable) - they are genuine CDs with licence; picked them up for few dollars years ago out of the local paper :) (also got NT4 and Win2000)

Unfortunately my floppy drive doesn't mount/work in Ubuntu 8.04 (reported it as a bug when I installed), so will have to get that fixed/working before I can go any further with Win95/98 in Virtualbox.

Alternatively, anyone know how to make a boot floppy image so Virtualbox can mount that instead of the actual floppy drive? Then I can run the setup.exe file on the CD and install OS from there.

:confused:

---

### Post by mellowd on 2008-09-02
> **charonred said:**
> 
Alternatively, anyone know how to make a boot floppy image so Virtualbox can mount that instead of the actual floppy drive? Then I can run the setup.exe file on the CD and install OS from there.
:confused:

[http://www.bootdisk.com/](http://www.bootdisk.com/)

all you need is a floppy image that you can mount. That image just needs to essentially boot and load a cd driver of some sort. You're then good to go.

---

### Post by charonred on 2008-09-02
thanks for that will get onto it later in day - have some work to do for the moment

---

