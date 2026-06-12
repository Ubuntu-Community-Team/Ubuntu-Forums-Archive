---
title: "nVidea Drivers"
date: 2009-07-06
forum: The Cafe
---

### Post by sydbat on 2009-07-06
I am looking to get an upgraded card for my fathers computer. It is an *[eVGA e-GeForce 8400GS 512MB PCI w/ DVI HDTV-Out]("http://www.memoryexpress.com/Products/PID-MX23976(ME).aspx")*. 

As I have never installed/used an nVidea card, I am wondering what your experiences are with the current set of drivers, specifically for Hardy 32bit.

I only ask for people to post if they have nVidea cards. Please do not post if you are simply going to flame or say "ZOMG!!1!! ATI ROCKS!!!!1!" or some such.:p

Thank you.

---

### Post by Skripka on 2009-07-06
Nvidia drivers are painless to install and usually just work...and I actually like their Linux driver better than their Win driver, as the control panel is far more explicit and open.


I'd be a little reluctant over a card that old-as legacy card support can be a funny thing.  The 185 driver is known to work fine with the 2.6.30 kernel linuxes-but has known issues when combined with older kernels (probably Hardy, although I cannot say for certain).

---

### Post by hessiess on 2009-07-06
Install from the ristricted drivers tool and everything usuily just works.

---

### Post by sydbat on 2009-07-06
Thanks.

I just realized that his motherboard has an agp slot so I might just go with this one instead - [eVGA e-GeForce 6200 256MB AGP w/ DVI, TV-Out]("http://www.memoryexpress.com/Products/PID-MX23935(ME).aspx")

---

### Post by Gizenshya on 2009-07-06
that is WAY expensive for that card!  you can get AGP 6800's all day for that.

what are the specs of the computer?  if the power supply is too small, you might have trouble.

---

### Post by cta16 on 2009-07-06
I just install [Envy-NG]("http://albertomilone.com/nvidia_scripts1.html")(also in the repositories). It's pretty idiot-proof after that since you only have to choose to install ATI or Nvidia driver.

---

### Post by sdlynx on 2009-07-06
> **sydbat said:**
> Thanks.

I just realized that his motherboard has an agp slot so I might just go with this one instead - [eVGA e-GeForce 6200 256MB AGP w/ DVI, TV-Out]("http://www.memoryexpress.com/Products/PID-MX23935(ME).aspx")

I have this for my desktop.  Actually I got the 5200 and it was defective so I RMA'd it and they sent that back to me lol but yeah it works like a charm on my Ubuntu 9.04 for my desktop.

---

### Post by sydbat on 2009-07-07
Thanks for your replies.

---

### Post by stwschool on 2009-07-07
Basically NVIDIA's the most hassle-free of the 3 major vendors.

ATIs drivers are problematic with Wine and Compiz, such that gaming's a nightmare and compiz while playing a video is a bad idea. (experienced this on all ATI machines I've tried).

Intel drivers are problematic on Jaunty, but ok for Hardy, but intel graphics hardware is poor in my experience.

NVIDIA drivers are as capable as their windows counterparts and let me play Windows games in Wine while playing movies and running compiz with no ill-effects. I heartily recommend them.

---

### Post by sloggerkhan on 2009-07-07
Nvidia's driver is good feature wise, but it does have one major annoyance:
It doesn't use DKMS or support building .deb files with one command. So every time there's a kernel update for ubuntu, I have to reinstall the nvidia driver (because I use the latest, or sometimes even prerelease, drivers, rather than repo driver.)

---

### Post by MechaMechanism on 2009-07-07
Does your father play allot of games.  I ask because most of the time a 3D card is nothing more than a space heater.  Have you any thoughts about power consumption and heat issues.

---

### Post by sydbat on 2009-07-07
> **MechaMechanism said:**
> Does your father play allot of games.  I ask because most of the time a 3D card is nothing more than a space heater.  Have you any thoughts about power consumption and heat issues.No, he does not play games, but wants to have certain 3D things enabled (like Google Earth). 

His current set up is on-board Intel that doesn't seem to have 3D capability (will not activate Visual Effects). Maybe increasing the RAM (which I am doing) will allow me to up the video in the BIOS and then get Visual Effects running.

His motherboard is [MS-7061]("http://www.msicomputer.com/product/p_spec.asp?model=KM4M-V").

---

