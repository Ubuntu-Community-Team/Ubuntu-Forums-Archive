---
title: "Why generic kernel is non-free?"
date: 2007-06-17
forum: The Cafe
---

### Post by BrokeBody on 2007-06-17
[http://ubuntuforums.org/showthread.php?t=335094](http://ubuntuforums.org/showthread.php?t=335094) :-?

---

### Post by Erunno on 2007-06-17
Because Mark Shuttleworth is dedicated to Free Software *cough* Launchpad *cough*.

---

### Post by aidanr on 2007-06-17
What does Launchpad have to do with the kernel? I'm guessing it's like a false positive or a bug, I was under the impression that the non-free drivers were in linux-restricted-modules

---

### Post by Gustav on 2007-06-17
Because linux-generic is just a meta package that pulls the restricted kernel packages (among other things)

---

### Post by az on 2007-06-17
> **Erunno said:**
> Because Mark Shuttleworth is dedicated to Free Software *cough* Launchpad *cough*.

Launchpad is neither free nor non-free.  For it to fall under one of those categories, it would have to be software that they distribute (give to someone).  There is only one place that it is being run/developed.  The point is irrelevant.

As for the kernel, the linux-image packages are completely DFSG free.  The restricted-modules packages are not.  The linux-generic package depends on the restricted modules, so it is non-free, but that has nothing to do with the kernel itself.

You can remove the linux-restricted-modules packages and that will remove the linux-generic metapackage, but that will not remove the linux-image packages and your computer will still run just fine.  You will even continue to get security-updates.

---

### Post by Anthem on 2007-06-17
> **az said:**
> Launchpad is neither free nor non-free.  For it to fall under one of those categories, it would have to be software that they distribute (give to someone).  There is only one place that it is being run/developed.  The point is irrelevant.
Thank you.  That's one of the most annoying arguments ever.

---

### Post by H.E. Pennypacker on 2007-06-17
> **az said:**
> Launchpad is neither free nor non-free.  For it to fall under one of those categories, it would have to be software that they distribute (give to someone).  There is only one place that it is being run/developed. 

That is not true.  Launchpad is open source if the source is available to the public, but it is not.  Therefore, it is closed source.  The open source definition of "free" would make Launchpad non-free.

---

### Post by az on 2007-06-17
> **Anthem said:**
> Thank you.  That's one of the most annoying arguments ever.

Your welcome?

> **H.E. Pennypacker said:**
> That is not true.  Launchpad is open source if the source is available to the public, but it is not.  Therefore, it is closed source.  The open source definition of "free" would make Launchpad non-free.

There is not a single free-libre open-source license that covers applications that only run over a network.  If a web application is running on another computer, it has nothing to do with free software.

The GPL and any GPL-compatible license is a contract between the distributer of the software and the recipient.  In the case of Launchpad, the software is not distributed.  

If launchpad was available for download, this would be a different story.

It's a service, it's not software.  Just like Google.

Do you want to make up a license that requires the server of a web application to provide the source code to its clients?  Do you think that will work out?  How far do you think it should go?  Would you oblige the serve to make public it's logs?  How about the contents of the database?

Can you explain to me why that would make sense?

---

### Post by prizrak on 2007-06-17
> **H.E. Pennypacker said:**
> That is not true.  Launchpad is open source if the source is available to the public, but it is not.  Therefore, it is closed source.  The open source definition of "free" would make Launchpad non-free.

If you read the GPL it will CLEARLY state that if you DISTRIBUTE any software covered by the GPL you MUST provide the source code to that software. It does NOT say ANYTHING about software that is not distributed. You can take Ubuntu rewrite it as much as you want and as long as you never distribute it it would not violate the license. 
Distribution terms is what makes software free or non free not what happens during development. Linux kernel was worked on by Torvalds at some point without anyone's involvement, would you say it wasn't free?

---

### Post by deanlinkous on 2007-06-17
But if launchpad is a software package that is installed on a system.....then isn't it software? It IS a software package, it also requires lib packages, and a python package and it looks like it isn't easy to remove and a lot relies on it....

Sounds like software to me....

> root@deans:~# apt-get remove launchpad-integration
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  deskbar-applet eog epiphany-browser evince file-roller gaim gcalctool
  gconf-editor gedit gnome-app-install gnome-applets gnome-games gnome-media
  gnome-nettool gnome-panel gnome-system-monitor gnome-terminal gnome-utils
  gthumb gucharmap hal-device-manager language-selector launchpad-integration
  libgucharmap4 liblaunchpad-integration0 liblpint-bonobo0 nautilus
  python-gnome2-desktop python-launchpad-integration python2.4-gnome2-desktop
  rhythmbox serpentine sound-juicer synaptic totem totem-gstreamer
  update-manager update-notifier yelp
0 upgraded, 0 newly installed, 39 to remove and 55 not upgraded.
Need to get 0B of archives.
After unpacking 106MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

That being said, it is included in gnewsense so I do not think it is the non-free culprit. The kernel modules are the problem.

---

### Post by Anthem on 2007-06-17
> **deanlinkous said:**
> But if launchpad is a software package that is installed on a system.....then isn't it software? It IS a software package, it also requires lib packages, and a python package and it looks like it isn't easy to remove and a lot relies on it....

Sounds like software to me....
The launchpad-integration package is Ubuntu's bugtracker.  That's different from the launchpad server, which isn't distributed.

---

### Post by deanlinkous on 2007-06-17
uh okay.....I understand the difference. I just wanted to point out that part of launchpad WAS installed software and was free. Then I think I pointed out that the non-free comes from the kernel modules - not anything to do with launchpad.

---

### Post by Anthem on 2007-06-17
> **deanlinkous said:**
> uh okay.....I understand the difference. I just wanted to point out that part of launchpad WAS installed software and was free. Then I think I pointed out that the non-free comes from the kernel modules - not anything to do with launchpad.
Oh, right.  Sorry, I misread.

---

### Post by prizrak on 2007-06-18
> **deanlinkous said:**
> But if launchpad is a software package that is installed on a system.....then isn't it software? It IS a software package, it also requires lib packages, and a python package and it looks like it isn't easy to remove and a lot relies on it....

Sounds like software to me....



That being said, it is included in gnewsense so I do not think it is the non-free culprit. The kernel modules are the problem.

Yeah seems like the clients parts are free. I think the server parts were meant to be non-free. Far as I can remember Mark said he was going to release it open source when he felt it was mature enough. For now he wanted to have full control over where it's going to make sure he can implement all the ideas he wants to.

---

### Post by kevinlyfellow on 2007-06-20
I think linux-generic is non-free because the entire kernel is tainted once you load non-free drivers.  I remember getting warnings about tainting the kernel when trying to get my linmodem working.

---

### Post by prizrak on 2007-06-20
> **kevinlyfellow said:**
> I think linux-generic is non-free because the entire kernel is tainted once you load non-free drivers.  I remember getting warnings about tainting the kernel when trying to get my linmodem working.

It's been answered above but I'll recap. Linux-generic is a meta package that depends on the latest kernel and kernel modules available. As one of those is the restricted module when reading package data it comes up as non-free.

---

### Post by BrokeBody on 2007-06-21
After clean installation of Ubuntu, when I go to the Update Manager, I already have to update linux-restricted-modules... AND I JUST INSTALLED "FREE" DISTRO, no drivers or anything! :confused:

wtf?! :o

Seems like Ubuntu is free only on paper. :-k

---

### Post by Tuna-Fish on 2007-06-21
> **prizrak said:**
> Linux kernel was worked on by Torvalds at some point without anyone's involvement, would you say it wasn't free?

This is completely beside the point, but back then, it wasn't free. The Linux kernel was originally under a non-free license that allowed you to see and modify the source, but placed heavy restrictions on redistribution. Then Torvalds fell in love with GPL v2 and the rest is history.

---

### Post by prizrak on 2007-06-21
> **BrokeBody said:**
> After clean installation of Ubuntu, when I go to the Update Manager, I already have to update linux-restricted-modules... AND I JUST INSTALLED "FREE" DISTRO, no drivers or anything! :confused:

wtf?! :o

Seems like Ubuntu is free only on paper. :-k

Ubuntu comes with a set of non-free drivers. Mostly firmware for Wi-Fi cards, so it's not totally FREE when it comes to your HDD. However if your hardware will not require those drivers/firmware they will not be loaded. Also Mark himself said that Ubuntu is as free as possible while still functional, it will have certain non-free drivers if they are required for hardware operation. That is also on paper, in fact it says so on the website :) 

Gutsy is also supposed to have a completely Libre version that does not include any of those things out of the box. They will be working with gNewSense in order to get it done. 

It's pretty much impossible to have a 100% FREE desktop system as a good number of what you would normally do on a desktop will require some non-free software. There is Flash, certain codecs, wireless firmware and so on.
> This is completely beside the point, but back then, it wasn't free. The Linux kernel was originally under a non-free license that allowed you to see and modify the source, but placed heavy restrictions on redistribution. Then Torvalds fell in love with GPL v2 and the rest is history.
Yes it was under that license for like a week and most people don't even know it. However you see my point, any product before it's released is technically closed source. Also the GPL only makes provisions as to distribution of software itself not the work performed with it. In this sense Launchpad is like a web server, you only see the output but you are not using the actual software locally.

---

### Post by deanlinkous on 2007-06-24
> **prizrak said:**
>  

It's pretty much impossible to have a 100% FREE desktop system as a good number of what you would normally do on a desktop will require some non-free software. There is Flash, certain codecs, wireless firmware and so on.
.
nah not impossible... :D

I havent heard much more about the *ultra-free* gutsy gibbon version, anyone heard more about it?

---

### Post by prizrak on 2007-06-24
> **deanlinkous said:**
> nah not impossible... :D

I havent heard much more about the *ultra-free* gutsy gibbon version, anyone heard more about it?

I said pretty much ;)

---

### Post by az on 2007-06-24
> **BrokeBody said:**
> After clean installation of Ubuntu, when I go to the Update Manager, I already have to update linux-restricted-modules... AND I JUST INSTALLED "FREE" DISTRO, no drivers or anything! :confused:

wtf?! :o

Seems like Ubuntu is free only on paper. :-k

All the applications on the cd are free-libre.  The Disk also has non-free drivers, but you can easily remove them by running

sudo apt-get remove linux-restricted-modules*

Or just use synaptic.  That will remove linux-image-generic, but you will still keep linux-image-generic, which will still fetch upgrades and so forth.  

It is trivial to remove the non-free software on a default install.  

It is not so trivial to install them if they are not, which is why they are there.

> **Tuna-Fish said:**
> This is completely beside the point, but back then, it wasn't free. The Linux kernel was originally under a non-free license that allowed you to see and modify the source, but placed heavy restrictions on redistribution. Then Torvalds fell in love with GPL v2 and the rest is history.

Back then?  Linux was released in 1991 and was always under the GPL.  It was always a GNU OS (built with and using the GNU toolchain.)  You must be thinking of Minix or some other Unix clone.

---

### Post by prizrak on 2007-06-24
> **az said:**
> A
Back then?  Linux was released in 1991 and was always under the GPL.  It was always a GNU OS (built with and using the GNU toolchain.)  You must be thinking of Minix or some other Unix clone.

No he is correct. The first time L.T. posted Linux it wasn't under the GPL. It was under a different license but not for very long.

---

