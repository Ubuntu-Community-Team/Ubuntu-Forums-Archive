---
title: "Getting Windows 2000 to fill up the screen"
date: 2014-07-06
forum: Virtualisation
---

### Post by Tom_ZeCat on 2014-07-06
I've gotten Windows 2000 to run under Kubuntu 14.04 via VirtualBox.  However, the best resolution I've been able to get is 800x600, and, hence, it will not fill up the monitor on my Lenovo Z570.  My laptop is way newer than Win 2K.  There therefore probably isn't a Win 2K driver for its monitor.  What's my best course of action?  Should I hunt down Windows XP drivers and see if I can get them to work?  In case you're wondering why I would run such an old OS, I need to run an old software development tool, MS Visual BASIC 6.  I wrote some software a long time ago and need to check out my code and run it line by line so that I can rewrite it for Linux in C++.  

Here's a screenshot of my Win 2K under VirtualBox:

[img]http://s20.postimg.org/y57c5utbh/Win2_Ksnapshot.png[/img]

---

### Post by ibjsb4 on 2014-07-06
Did you install the **VirtualBox Extension Pack**?

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by Tom_ZeCat on 2014-07-06
> **ibjsb4 said:**
> Did you install the **VirtualBox Extension Pack**?

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Yes, I've installed that.  I had installed it before and I've got Windows 7 running under Kubuntu/VirtualBox.  I followed your link and upgraded to the latest.  I'm still stuck at 800x600.  I'm also limited to 16 colors.  

I'm watching Youtube videos in which people install Win 2K under VB in case someone has some ideas about screen res.  I'm not sure if a Windows XP driver might exist for my Z570.  If it does, making that work in Win 2K might be the deal.  

Another thought would be to buy a really old laptop at a thrift store and install Win 2K on that.  I saw one for $20 about a month ago.  Maybe I should have snatched it up.

An update: I tried the Windows XP display driver.  It came with an executable install program, but that did not work.  Maybe some kind of generic Win 2K driver would work?  

Frustrating.  Buying an old cheap laptop is looking better and better.

---

### Post by Tom_ZeCat on 2014-07-06
An update: I tried the Windows XP display driver.  It came with an executable install program, but that did not work.

---

### Post by ubeauty on 2014-07-07
Not sure if this is helpful, but AFAIK W2K, has fixed res ratios so you will never fill in the screen without distortion on a wide screen.

---

### Post by TheFu on 2014-07-08
Another option is to dump virtualbox and use KVM.  It emulates a GPU, so there aren't any client-side drivers to install. Choose either cirrus or VGA and don't expect great performance, since you'll be connecting over VNC.

I hope you get that banking system or ATM code to work. ;)

---

### Post by KillerKelvUK on 2014-07-08
Try using Wine+PlayOnLinux instead of full OS virt, WineHQ says VB6 is functional (mostly) so if all you need is code and debug you might get lucky?!

Best of luck

---

