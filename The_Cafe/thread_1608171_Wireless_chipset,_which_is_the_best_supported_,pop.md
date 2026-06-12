---
title: "Wireless chipset, which is the best supported ,popular"
date: 2010-10-28
forum: The Cafe
---

### Post by MooPi on 2010-10-28
I've been buying wireless adapters with purpose of testing the compatibility and speed recently. I have a small assortment of wireless usb dongles and pci adapters both g/n functionality. I purchased mostly known compatible chips but have recently been going with unknowns to widen my scope. I'm going to be doing computer repair after the first of the year and also hope to sell custom Linux boxes.So the larger the resource pool I have of workable devices the better. Mostly Ralink chips and a couple of Realtek. Lets see in Ralink I've got 2561, 2870, 3060 and Realtek a couple of different brands with RTL8187. What's your favorite and what working for you ?

---

### Post by cariboo on 2010-10-28
I've never purchased a wireless device that I haven't been able to get working. Sometimes they will only work with ndiswrapper and a 32-bit version, and others work as soon as they are plugged in, in both 64 and 32-bit versions.

I have the following devices:

[list]
[*] Broadcom BCM4312 - uses the Broadcom  wl driver - great performance
[*] D-Link WUA-1340 - uses RT73 driver - works better using PCLOS that Ubuntu
[*] D-Link WUA-2340 - only works using ndiswrapper and the 32-bit Windows driver
[*] Unkown Broadcom B4303 PCI - works out of the box with the B43Legacy- installer
[*] Trendnet ZD1211 - uses zd1211 driver - works out of the box
[*] Prism in  an HP laptop - uses the orinocco driver - works out of the box
[/list]

I also had a MSI 54g broadcom based that finally died after 6 years of usage, it only worked with ndiswrapper and the XP drivers.

---

### Post by Spr0k3t on 2010-10-28
I've had only a few simple problems with the Atheros chipsets, mainly the draft-n sets prior to the source code release.  However, that's to be expected really.  Most of the wireless cards (atheros) have been plug and go out of the box.  I think all but one wireless card I have uses an atheros chipset.  The one that isn't atheros is broadcom... that thing has been a nightmare every time I try to get it working on a fresh load without any other network interface.

---

### Post by SeePU on 2011-01-13
Any update to this?:

Maybe we should make a list?

Also, divide the usb adapters into 'wireless G' and 'wireless N.'

G:
??

N:
??

I thought Atheros would be good for either but I think there are some newer chipsets/drivers that aren't quite supported yet?  

The newest driverset is ar9710usb???   But, it requires firmware?

I guess there's no chipset/drivers that work totally 'OOTB?'  

Would these chipsets be the best bets?  Zydas, Ralink and Atheros?

Also, I think we are discussing usb dapters in this particular instance.

The more convenient pages to compare, I think, are:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

[http://wireless.kernel.org/](http://wireless.kernel.org/) (<--- this one can be very slow to load or not load at all!)

The web pages are only good as guides and not all inclusive nor totally up-to-date at all times.

---

### Post by chriswyatt on 2011-01-13
My integrated Intel wireless has always worked fine, ever since I first tried Ubuntu:

Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Though I can't use it anymore because the wireless kill switch has died on my laptop. :(

---

### Post by JDShu on 2011-01-13
The problem is that walking into a store to buy a wireless card doesn't help because the box doesn't say what the chipset is. The best way to find out is to go on amazon or newegg and check out the reviews.

---

