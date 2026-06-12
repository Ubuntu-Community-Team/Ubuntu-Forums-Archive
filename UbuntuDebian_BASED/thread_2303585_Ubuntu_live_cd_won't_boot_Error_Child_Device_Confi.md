---
title: "Ubuntu live cd won't boot: Error Child Device Config Size 27 is too small"
date: 2015-11-20
forum: Ubuntu/Debian BASED
---

### Post by schelry on 2015-11-20
Hi there. I have been trying to configure an old computer for my home wireless lan and although i found the drivers for my wireless adapter in Mandriva 2010 I did not succeed in getting the machine up on the net. 

So, I have made a live cd of Ubuntu Mini Remix 15.10 i386 and at first I get the purple screen and then the screen with "Ubuntu" and the 4 colorchanging dots below it, then I get this:

[    10/239346] [drm_parse_bios *ERROR* Child Device Config Size 27 is Too Small.

and then after about 10 seconds or so it drops to a command line.
I am a linux beginner and have no idea what to do with a command line. I did try a few things I found (sudo apt-get type commands) but of course without a network connection everything I found as a suggestion failed.

Would really appreciate any help.

The wireless adapter device is an EW-78llun and is new. I have been troubleshooting with the vendor and they had recommended I use a new linux distro and make sure that I have the rtl8191cu or the rtl8188cu driver and I tried to work this with a puppy linux tahr pup cd and found that while both of those drivers were present on the disk to "load module" what happened when I loaded the module was that it spent a few seconds then came back and told me no new device was found and recommended i de-install those modules.

Frantic! Please help.
Michele

---

### Post by mörgæs on 2015-11-20
Hi, welcome to the fora.

Please begin with a complete hardware description.

---

### Post by Bucky Ball on 2015-11-21
*Thread moved to **Ubuntu/Debian BASED**.*

Welcome. Ubuntu Mini Remix is not among the supported distros/flavours in the main support areas here. Just wondering why you are going for such an install when you are unfamiliar with Ubuntu. That is not for the novice. Try a bog standard Lubuntu or Xubuntu install if it is a low-spec machine. Much easier if you don't know what you are doing.

If you want to go on a steep learning curve, don't use the (rather obscure) Ubuntu Mini Remix. Use the Ubuntu minimal install which is fully supported here. Some links.

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Be prepared to put aside some time to learn if you decide to go up that track.

PS: Puppy is not supported in the main areas here either.

PPS: Mandriva is based on Red Hat so unsure why or if a wireless driver from Mandriva is going to work in the Debian based Ubuntu.

---

### Post by schelry on 2015-11-23
ok sorry I left out the hardware specs.

I'm trying to resuscitate an old Dell Optiplex gx260 which has a cd-rom drive that works but only one usb 2.0 port and the rest are 1.1. I'm using an edimax ew-7811un wireless adapter that gets shown in lsusb but does not produce a corresponding network interface when I run ifconfig.

To answer questions from other posts, I was using distros that I was able to find that could run on an older computer... limiting what I was trying to those distros that fit a live installation on a cdrom. I have tried maybe 5 since posting the original post. The decision making was driven by the cdrom and "older computer" although my preference was to run some flavor of ubuntu.

Today I went ahead and burned a cd of Lubuntu 15.10 which I figured would have solved the rtl7192cu/rtl8188cu problem which the linux kernel 3.0+ was reported to have solved. I did not do this before because I didn't think the latest version would fit on a cdrom. Surprise, it does.

I have just now managed to get the wireless up and running on that pc although I did not succeed at configuring for it in Network Manager. I couldn't resolve what the host should be. The good news is that the network menu (at the bottom right and therefore nearly invisible to me) is able to scan and report available networks even if I haven't set up the network manager correctly.

So, for me at any rate, this thread can be closed as I am now up and running with internet access on the Optiplex.

I did not ever manage to get the Ubuntu Mini installed and I still do not know what was up with the child device config error. I did waste a lot of cd's in this process.

---

### Post by mörgæs on 2015-11-23
Good, please mark the thread 'solved'.

Installing with wired internet access is preferred. Might have saved you some CD's.

If Lubuntu grows bigger than a CD some day there is also the alternate ISO to consider.

---

### Post by Bucky Ball on 2015-11-23
> **mörgæs said:**
> Good, please mark the thread 'solved'.

Please see the first link in my signature and good luck. :)

---

### Post by schelry on 2015-11-25
> **mörgæs said:**
> Good, please mark the thread 'solved'.

Installing with wired internet access is preferred. Might have saved you some CD's.

If Lubuntu grows bigger than a CD some day there is also the alternate ISO to consider.

I was unable to get either wired or wireless internet access working on the pc in question. Until I finally got up and running with Lubuntu 15.10 when it finally recognized the wireless adapter. It still shows that there is a wired nic installed but does not identify or utilize that nic at all for no reason I was unable to uncover. Eh, I figure if I got it running with the wireless adapter, I can quit while I'm ahead.

---

### Post by mörgæs on 2015-11-25
Glad to hear. Enjoy :-)

---

