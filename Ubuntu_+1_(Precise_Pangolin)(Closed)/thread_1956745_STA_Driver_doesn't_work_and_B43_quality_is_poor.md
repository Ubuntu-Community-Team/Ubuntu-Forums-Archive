---
title: "STA Driver doesn't work and B43 quality is poor"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MasterNetra on 2012-04-11
Yea, running 12.04 Beta 2 and I rely on my wireless. I use a Broadcom BCM4312 for wireless (laptop) and STA doesn't work at all, and b43's quality is very poor. Which is especially troubling to me as I was hoping to jump to 12.04 and stick with LTS's for business reasons.

*Also I don't have access to a landline I go to the library for wireless atm.*

---

### Post by dontquoteme on 2012-04-11
I have the Broadcom 4312 - which relies on the STA driver.
A lot of Dell laptop owners will be affected.  Thanks for the heads up.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Some of the Dell devices that rely on the Broadcom STA driver.

[LIST]
[*]BRCM  devices using STA.
[*] 4311 2.4 Ghz        0x14e4    0x4311      Dell 1390
[*] 4311 Dualband        0x14e4    0x4312      Dell 1490
[*] 4311 5 Ghz        0x14e4        0x4313
[*]4312 2.4 Ghz        0x14e4    0x4315      Dell 1395
[*]4313 2.4 Ghz        0x14e4    0x4727         Dell 1501
[*] 4321 Dualband        0x14e4    0x4328      Dell 1505
[*] 4321 Dualband        0x14e4    0x4328      Dell 1500
[*] 4321 2.4 Ghz        0x14e4    0x4329
[*] 4321 5 Ghz        0x14e4    0x432a
[*] 4322     Dualband    0x14e4    0x432b      Dell 1510
[*] 4322 2.4 Ghz      0x14e4     0x432c
[*] 4322 5 Ghz        0x14e4     0x432d
[*] 43224 Dualband    0x14e4    0x4353      Dell 1520
[*]43225 2.4 Ghz     0x14e4    0x4357
[*] 43227 2.4 Ghz     0x14e4    0x4358
[*]43228 Dualband    0x14e4    0x4359      Dell 1530
[/LIST]
There are far more Dell machines than these...as the Dell studio range also uses the 4312 range -  so a lot of people will be affected.

If you find a workaround, can you update us.

---

### Post by MasterNetra on 2012-04-11
Well today's update had a kernal update after its install and retart the wireless seems to be doing better, it drops down to weak at times but its been doing a lot better. I made the first post prior today's updates.

 Haven't retested STA yet. I'll have to do another STA test tommorrow, as I left my USB Wireless adapter at home (( Yea ok, I'm not completely helpless without a landline, but the dang thing gets hot real fast so not a good idea for me to rely on it)).

Also yea, my laptop is a Dell Latitude D530 and I'm using the 32bit version of Ubuntu (which they're using PAE Kernals for 12.04).

---

### Post by cariboo on 2012-04-11
Again, I'm one of those unfortunates, that can't seem to find a hardware problem :P My Compaq netbook has a BCM4312 wireless device, using the STA(wl) driver. I haven't had a wireless problem since the start of the development cycle, as a matter of fact wireless works better in Precise than it ever has with earlier release, it connects before it finishes coming out of sleep, and is connected on boot before the login screen is displayed.

---

### Post by MasterNetra on 2012-04-12
> **cariboo907 said:**
> Again, I'm one of those unfortunates, that can't seem to find a hardware problem :P My Compaq netbook has a BCM4312 wireless device, using the STA(wl) driver. I haven't had a wireless problem since the start of the development cycle, as a matter of fact wireless works better in Precise than it ever has with earlier release, it connects before it finishes coming out of sleep, and is connected on boot before the login screen is displayed.

Yea curse the non-standization of hardware. STA Doesn't work for me at all in 12.04, it doesn't in 11.10 either, I'm on a Dell Latitude D530 btw. Don't think it worked in 11.04 either, but don't remember off hand. Regardless tested STA via Addtional Drivers and wireless was dead in the water. Would be nice if they brought back b43 in addtional drivers and have it install b43 via the firmware-b43-installer package...

What would be even more nice is if broadcom opensourced the blasted firmware so it could be in Ubuntu via default. I swear if it wasn't for this Encore Wireless-G USB Adapter, I would be up a creek without a paddle.

---

### Post by cariboo on 2012-04-12
I use a[ RetailPlus]("http://www.retailplus.com/products/wireless-usb-adapter/retail-plus-wireless-g-usb-adapter") usb wireless device, when I'm to lazy to dig out a network cable. :P To install the STA driver.

---

### Post by seenthelite on 2012-04-12
I am posting using live usb (Unetbootin) and wireless Broadcom BCM4321. I activated the driver (STA) by using Jockey and no internet connection. Downloaded the Daily Build last night. It does not get any better than that. Speed is fine.

---

### Post by teh603 on 2012-04-12
I've had issues with STA not working because of a corrupted modaliases package. If STA doesn't work, my first answer is to purge the modaliases and reinstall from scratch. That would get it working back in Karmic and Lucid.

Figure if it worked once, its worth trying again?

---

