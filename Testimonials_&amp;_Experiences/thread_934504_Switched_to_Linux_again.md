---
title: "Switched to Linux again"
date: 2008-09-30
forum: Testimonials &amp; Experiences
---

### Post by Enix3k on 2008-09-30
Hi, im new here and i just switched over again to Linux (my first post as well).

So i've been a normal windows user for many years but has sometimes switched back and forth between Linux and Windows.
First distro i tried was RedHat back in 1999, i didn't know what Linux was back then frankly i didn't get it. So i moved back to.... i think it was Windows98?
Anyway time moved on, tried many distros like Fedora, Gentoo (never got the hang of it), Debian, Mandriva and also a few BSD flavors like FreeBSD and OpenBSD (but never got into these). I've always used these distros on a spare machine and kept WindowsXP on my main workstation. I was also a addicted PC gamer so i couldn't remove it that easy. However PC games began to be crap and i moved to consoles like XB360, Wii and PS3 and im a happy owner of all 3 of them, i use them as my gaming machines. Then last year i switched over to Ubuntu for the first time (think it was 7.04) on my main workstation, compiz-fusion (or beryl as it was called back then) was a bit tricky to get to work, i remember had to work with it for days (mainly because im a newbie, but hey we all begin somewhere right?) but finally got it to work and i was hooked. But then i got this idea of getting a MacBook as i wanted to try OSX, so i sold all my PC's and bought a MacBook (i still have it today but im about to sell it) and used OSX Tiger for a year. A few weeks ago i got tired of only having a Mac so i built a new PC, i put in XP on it and was temporarly happy with it.
But then the classic problems began, i got tons of viruses. 
You know, after being in a OSX environment for a year i wasn't used to have viruses so i got tons of them. I got enough today when i accidently got that MSN virus that affected both my Home PC and my School laptop, so i decided; "**** WINDOWS, im tired of you!"
So i reformatted my Home PC with only Ubuntu 8.04 x64 as the main OS but kept Dual boot on the laptop, else the school administration would go nuts. The more i use Ubuntu, the more i realise i don't need closed-source OS like Windows or OSX anymore (you can't say OSX is open-source, some parts are but not all). Everything i need exists in Ubuntu and im now hopefully a 100% Ubuntu-only user. Im gonna get rid of WindowsXP on the laptop when im finnished with school because i don't need it anymore.

Im not dualbooting on the laptop because i want too (the XP partition is virus infected) its just because i need to keep that partition.

My solution to this problem is to install virtualbox but i can't get it to run, everytime im about to start this virtual machine i get this strange error.

"Virtualbox kernel driver not installed blablabla"
How am i supposed to solve this? I've tried to install a package i thougt i needed: sudo-apt-get install virtualbox-ose-modules-generic.
But it doesn't want to install so im stuck or im doing something wrong, im completely lost. Now don't get me wrong, i might be a newbie now but as i want to stick with Linux forever, i want to learn it as much as possible and i think Ubuntu is the right place to start to get used to it.

Btw, i've been reading quite a few posts here before as a guest and this community looks very friendly, by far the most newbie-friendly i've come across i think.

Well thats about it i think, or else the thread gets too big and takes too much time to read :D
(As you might notice, english isn't my primary language :) )

---

### Post by rzrgenesys187 on 2008-09-30
I was getting the same error with virtualbox.  To fix it I had to download the modules for my kernel (don't worry they are in the repositories) ```
sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic
```
Note: the 2.6.24-19 is for my specific kernel, change this to match the kernel you are running.  You can find that information out with ```
uname -r
```

If I remember correctly after I installed this package it edited my /boot/grub/menu.lst file and my default entry was changed.  When I tried to boot into this my wireless card and a few other things didn't work so if this problem happens to you just reboot and select the kernel you boot into now and that should solve any problems and allow you to run virtualbox.  If you don't use the virtualbox entry you can comment it out by putting a # in front of the lines you don't need in your /boot/grub/menu.lst

---

### Post by WWSmith36 on 2008-09-30
I think you must install the kernel specific modules.  In synaptic you can do a search for virtualbox and install the one that matches you kernel

For example virtualbox-ose-modules-2.6.24-20-generic.

---

### Post by steveneddy on 2008-09-30
You may ask that this be put in a support thread so that you can get some more help with your issues.

---

### Post by wolfen69 on 2008-09-30
welcome back. enjoy your stay.

---

