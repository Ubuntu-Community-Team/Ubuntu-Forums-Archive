---
title: "Updated to proprietary graphics driver, now Virtualbox kicks me to login"
date: 2013-04-25
forum: Virtualisation
---

### Post by Nick Scratch on 2013-04-25
Hello,

I'm having trouble with my Virtualbox. I updated my Nvidia drivers, and some programs -- most notably Virtualbox -- have been kicking me. That is to say, I start the program and it boots me to the login screen at the first glance. With Virtualbox, I can't even get into the preferences, much less start a virtual machine. Thus, I have no logs to provide. If there is a way for me to help you help me, please share.

I tried uninstalling, reinstalling, etc. I'm not exactly a pro, so my options are limited. I have scoured the Internets in search for answers, and as a result I'm ready to throw myself out a window in frustration.

Any assistance is appreciated.

---

### Post by Nick Scratch on 2013-04-26
The problem persists. If I am not giving enough info, please help me to do so.

---

### Post by Nick Scratch on 2013-04-26
Goodbye, Ubuntu. I thought I was entering a brave new world, but it turned out to be a post-apocalyptic hellhole. I never experienced an operating system that randomly rebooted you to the !@#$!@ logout screen when you try to right-click. Trying to find a solution is like looking for a needle in haystack. I spent at least 18 hours trying to tackle one problem without success, and not through a lack or effort.

Back to ****** Windows.

---

### Post by Nick Scratch on 2013-04-27
Update: The Ubuntu DVD writer ruined my last DVD. It can't even burn DVDs right. So I spend half my day trying to get a RUINED DVD to boot (thinking it was another problem), in in the process formatted my computer. I'm in the middle of taking apart my computer piece-by-piece in an attempt to load Windows back on my computer, for some AWESOME reason it won't load, even with a formatted hard drive.

Ubuntu is the worst thing that's ever happened to me, and I've been in mental hospitals.

---

### Post by ARooster on 2013-04-27
Yup, VirtualBox can be a nightmare. Unfortunately, sometimes an inevitable one since there's no better alternative for the task as far as I know. If it makes you feel any better, it's probably to do with VirtualBox-nVidia drivers compatibility issues, not with Ubuntu itself. Which version of Ubuntu btw? When 12.10 came out I happily upgraded but reverted to 12.04 within a month or so, mainly for this very reason. I did find 12.04 was stable enough. You should also install the latest release of VirtualBox (which is usually not the one offered in the Software Centre).

---

### Post by heiko_s on 2013-04-29
It looks like you got various problems, not only Virtualbox.

Instead of booting from DVD, download the Ubuntu version you want, check the mdm5 sum, and make a bootable USB stick using for example unetbootin (also available under Windows). Then boot from USB (hit the right key while booting to get into the boot menu or BIOS, then select the USB stick).

It would perhaps help if you stated your hardware, the Ubuntu version you are running, and some more about your installation.

The problems you experience could be anything from hardware (RAM ?), a bug, some corrupted files, incompatibility, or configuration issues. Or simply a buggy Nvidia driver (that wouldn't be the first time). If you haven't messed up your installation, I would start with reverting the Nvidia driver back to the one that worked.

---

