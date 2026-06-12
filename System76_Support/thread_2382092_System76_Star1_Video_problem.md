---
title: "System76 Star1 Video problem"
date: 2018-01-08
forum: System76 Support
---

### Post by linuxhippy on 2018-01-08
I have an old System76 Starling Star1 netbook from 9 years ago that I just did a fresh install of XUbuntu 17.10 but it boots up with the attached video problem:

[ATTACH=CONFIG]278097[/ATTACH]

Any ideas how I can fix the video?  It's an intel setup and starts out booting ok but then ends up looking like that and the black area cannot be closed.  I can do a safe boot to a clean screen and checked save session when I exit but with no intervention it still shows up with a big chunk of screen just black.

Marty

---

### Post by linuxhippy on 2018-01-09
I did find out that if I can get the computer to lock, that when it unlocks it reverts back to a fullscreen.  It seems to be an X11 problem and I see that this is installed using synaptic and it caused problems in the past:

xserver-xorg-video-nouveau

I also now have an ssh server installed and I can plug a VGA monitor into it.

---

### Post by linuxhippy on 2018-01-17
Well, I got it working but I'm not sure how.  It wasn't anything to do with nouveau I'm pretty sure.  What I did was install Mint Linux 18-the XFCE version for 32 bit.  Found that here:

[https://www.linuxmint.com/rel_sarah_xfce_whatsnew.php](https://www.linuxmint.com/rel_sarah_xfce_whatsnew.php)

I'm pretty sure it just uses the Ubuntu repositories so the Linux distro shouldn't matter in this case.  I did one thing different on the Ubuntu and Mint installations-I picked use 3rd party drivers on Ubuntu and on Mint I did not.  Maybe that's why Mint worked on a netbook made for Linux?  I'll install Ubuntu again beside Mint and see.

Also, I did minor surgery on this netbook a couple years ago so that now it sports a new WiFi card for N and drivers for that are built in to the Linux kernel.

---

### Post by linuxhippy on 2018-01-17
I found the blog I followed in 2011 to upgrade my netbook to a wireless N card and I had no problems.

[http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html](http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html)

The netbook has 3 USB slots and I put a new Logitech C920 that encodes in the camera rather than the computer and it connects to the top of the netbook.  This is what I have:

[https://www.amazon.com/gp/product/B006JH8T3S/ref=oh_aui_search_detailpage?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B006JH8T3S/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)

It works fine in Ubuntu so I'm hoping it'll work in Mint.  The netbook has a built in webcam but it is around 10 years old so the webcam hardware is old but the netbook would be good for Skype video conferences.  These were predecessors to Chrome books.

---

### Post by linuxhippy on 2018-01-17
Well, I just tried installing XUbuntu again from a USB flash without picking anything from 3rd party and it installed the same messed up video way.  I have no clue why Ubuntu won't install on this System 76 netbook but Linux Mint 18 does.  So I removed Ubuntu and reintalled Mint so that Mint has the entire 160 GB drive.

Looks like the answer is to go with Mint and Skype works with them on my desktop pc so hopefully it will on this netbook too.

---

