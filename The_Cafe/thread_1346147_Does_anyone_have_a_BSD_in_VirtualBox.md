---
title: "Does anyone have a BSD in VirtualBox?"
date: 2009-12-04
forum: The Cafe
---

### Post by Pogeymanz on 2009-12-04
I did some googling and it seems that FreeBSD and/or OpenBSD have some bugs in VirtualBox and PCBSD just blows up.

But I found some mixed answers: some say FreeBSD works, some say this version or that wont work at all, etc. But they are somewhat old sites.

I just want to see if anyone has an up-to-date installation of a BSD RIGHT NOW.

I tried FreeBSD and had a problem starting X and I'm not sure if I messed up or if it's a VirtualBox problem. Since I never ever mess anything up, I'm hoping it's a VB bug.

---

### Post by chris200x9 on 2009-12-04
I have not, though if you have a spare partition I would highly recommend checking out freebsd if you use arch(assuming by your sig)  you should find it pretty easy.

---

### Post by dmengo on 2009-12-04
I tested out VirtualBox awhile back with a few different operating systems.  I couldn't get it to work correctly with FreeBSD.

---

### Post by Diluted on 2009-12-04
My past experiences has indicated that VirtualBox doesn't really play well with BSDs. Have you tried other options like QEMU?

---

### Post by Kdar on 2009-12-04
How PC-BSD and Free-BSD are different?

---

### Post by yebo29 on 2010-03-03
KDar:

PC-BSD is just Free-BSD with KDE and some desktop optimizations.

I too am having issues - in fact, I can't even boot PC-BSD 8 on VBox 3.1.4. It just hangs at "Starting BTX Loader". My CPU Util starts to climb and nothing else happens. I've tried turning off VTX, PAE, tried disabling software, and even changing storage drivers in Vbox.

Anybody have any ideas?? I also can't boot OpenSuse 11.2 - GNOME 64 bit.. :(

---

### Post by Techsnap on 2010-03-03
FreeBSD in VirtualBox works here, PC-BSD should work.

---

### Post by The Real Dave on 2010-03-03
Does running FreeNAS in a VM count? :)

---

### Post by Post Monkeh on 2010-03-03
i installed pcbsd just today in vbox.  worked fine, though i didn't give it any major use, but it installed and i could log in to a desktop anyway.

---

### Post by Twitch6000 on 2010-03-03
With PC BSD I had to use the boot with vesa option to get it to work. After that it installed to problem.

---

### Post by Sporkman on 2010-03-03
I've gotten OpenBSD working in Virtualbox.

---

### Post by yebo29 on 2010-03-04
Did you have to use any special settings? If so, what are they? Did you have to do anything else special?

---

### Post by Post Monkeh on 2010-03-04
> **yebo29 said:**
> Did you have to use any special settings? If so, what are they? Did you have to do anything else special?

i just set it with 1 gb memory, 20 gb hard drive, and mounted the iso.

dunno if it makes a difference, but i'm not using the open source edition.

i installed freebsd first a few days back but it was requiring quite a bit of setting up (by default no xserver or desktop environment was installed) and i didn't really have the patience to do lots of setting up for what was essentially just a way for me to see what bsd was like, so i just waited for my download of pcbsd to finish and installed it with no problems.

---

### Post by yebo29 on 2010-03-04
HM. That's the same thing I did. Well, almost. I created a 10GB drive... err, I don't think that would make a difference.. would it?? 

I'm also not using the Open Source version.

I guess I'll try to see if my image is corrupt or something: check md5 or burn it to a disk and boot to it and see what happens..

---

### Post by yebo29 on 2010-03-04
> **yebo29 said:**
> 
I guess I'll try to see if my image is corrupt or something: check md5 or burn it to a disk and boot to it and see what happens..

D'Oh! It seems my MD5Sum is different. HM. I have no burnable DVD's at home. I'll have to go get some. Oh, well. Keep ya'll posted.

---

### Post by Post Monkeh on 2010-03-04
strange. i don't have anything special set. i have the most up to date version of vbox (3.14) and i just have all the basic settings (no video acceleration or anything).

just checked and i actually only have 512mb ram allocated.


edit : well the dodgy iso would be the problem.

---

### Post by yebo29 on 2010-03-04
Hopefully that's the case. I'll let you know.

---

### Post by earthpigg on 2010-03-04
are some of you using the proprietary version of virtualbox from their website, and others using the open source version from the ubuntu repos?

the OSS version (in the repos) is intended to have limited functionality.

---

### Post by Nerd King on 2010-03-04
Using the VBox from their website, I've never had any major difficulties getting BSD to work.

---

### Post by Post Monkeh on 2010-03-05
> **earthpigg said:**
> are some of you using the proprietary version of virtualbox from their website, and others using the open source version from the ubuntu repos?

the OSS version (in the repos) is intended to have limited functionality.

i use the full version as the os version doesn't allow the use of usb devices.

---

### Post by yebo29 on 2010-03-05
> **Twitch6000 said:**
> With PC BSD I had to use the boot with vesa option to get it to work. After that it installed to problem.

Eh, how'd you do that?? :)

Also, the OSS version of Vbox doesn't include the RDP server..

---

### Post by Twitch6000 on 2010-03-05
> **yebo29 said:**
> Eh, how'd you do that?? :)

Also, the OSS version of Vbox doesn't include the RDP server..

Well I use the closed source version so... there is your answer :).

---

### Post by yebo29 on 2010-03-09
I was able to get PC-BSD 8 running on VBox. Th problem was a corrupt ISO, which was downloaded using Ktorrent. I downloaded the ISO directly from the website, and checked the md5sum, and it matched.

I was able to get to the KDE desktop. It did show several errors upon booting (such as that X couldn't find the display), but in the end it booted KDE.

I didn't have to do anything special in the setting besides changing video memory to 32MB... but I'm not even sure that was necessary.

Hope this helps others having the same issues!

---

