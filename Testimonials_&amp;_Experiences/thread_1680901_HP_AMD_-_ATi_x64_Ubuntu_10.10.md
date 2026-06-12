---
title: "HP/ AMD - ATi/ x64/ Ubuntu 10.10"
date: 2011-02-03
forum: Testimonials &amp; Experiences
---

### Post by Jakin on 2011-02-03
I feel stupid not knowing how to create this topic in the proper 64bit forum... perhaps if this is useful admins can move it there.

I am using a HP g56-127n laptop with -
AMD v140 series processor (clocked at 2.30ghz) 
4GB of DDR-3 ram (i assume ubuntu could run on half that or less)
AMD M880G with ATI Mobility Radeon HD 4250 - graphics
RealTek HD audio chipset
Broadcom 4313 802.11 b/g/n - wireless adaptor (which the driver is already on the install CD and asks you to install once you boot up)
RealTek PCIe FE "family controller" - network LAN (wired net)

(as per basic rundown of the machine)

Using the Ubuntu 10.10 Desktop edition 64bit Live CD i installed the system in something like 25mins; everything on the system worked entirely out of box without a hitch, i am glad to say. Advanced graphics were also enabled with the opensource driver, still the option to get the proprietary is compelling.

One should note installing or even trying the Live CD has a small bug (for this system anyway) and clicking the "try live CD" or "Install ubuntu" when the disc first starts does nothing. Instead to boot into the desktop to try and then install click the close X on that window and say QUIT when it asks. Ubuntu won't actually quit, give it a moment to boot up gnome, and you are good to go- try it out (i must say snappy even when just using from the CD) and then install if you so wish.

So for that simple little installation bug, HP g56 series seems to be a perfect match for Ubuntu 10.10.
I hope this info can be useful for deciding the hardware to use for Ubuntu :)

Alot of us need flash for youtube or whatever- this tutorial works flawless [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

---

### Post by cariboo on 2011-02-03
The 64-bit sub-forum has been closed, as any solution for 32-bit will work for 64-bit. This really isn't a support question, so Moved to Testimonials & Experiences

---

### Post by Jakin on 2011-02-03
Great thanks :) the point was just to get across the hardware that could be used, with ubuntu, and seems to quite well.

---

### Post by stchman on 2011-02-07
I install the flash plugin in the following folder:

/usr/lib/firefox-addons/plugins

This will allow for the use of the plugin if you have multiple accounts on the computer.

So you are saying the Broadcom wireless worked OOB?  I installed Ubuntu 10.04 on an HP laptop with a Broadcom card.  I had to enable the b43 restricted driver and then the wireless card worked.

---

### Post by Jakin on 2012-02-16
I recently did a fresh install of ubuntu 11.04 amd64 now outdated.   On the same hardware i mentioned nearly a year ago, all works Out-of-Box, including the preinstalled FLASH player, working in all browsers without any tweaking.   Not a single issue, actually.     @ stchman   Sorry i hadn't replied... indeed there are proprietary drivers for the Broadcom Card, and i would install later- but it did not NEED the drivers.

---

### Post by coffeecat on 2012-02-16
@Jakin, thank you for your testimonial, but:

> In keeping with a vote by the forum membership which followed a discussion about the management of this section of the forum, threads will now be closed one week after the time of the original post. This is to allow limited discussion.

Since this thread is now a year old, I'll close it.

By the way, I see that you have the Broadcom BCM4313 wireless card. That works for me too out of the box in 11.10, using the open source driver. 

Good luck!

---

