---
title: "Is this a viable concept?"
date: 2020-07-18
forum: The Cafe
---

### Post by MoebusNet on 2020-07-18
I want an inexpensive piece of hardware like a Raspberry Pi to use as a stand-alone anonymous web browser only. I want to boot it from removable storage or ROM media then run the OS and browser in RAM only with no permanent storage. Removable storage mounted only when required then removed. For anonimity I want to be able to change MAC address at every boot-up. This would be used at public or nonatritable wifi hotspots only. Is this a viable concept? Any hardware or OS suggestions? Puppy ARM seems to be a start, but not to alpha stage yet.

---

### Post by Frogs Hair on 2020-07-18
For something portable you may want check out a pi-top 3 though not inexpensive .  There are kits that include mini keyboards and monitors for R pi and other mico computers.I don't know about changing the mac address as they are often assigned/flashed at the OEM.  

[https://www.raspberrypi.org/products/raspberry-pi-keyboard-and-hub/](https://www.raspberrypi.org/products/raspberry-pi-keyboard-and-hub/)
[https://www.androidcentral.com/best-raspberry-pi-screen](https://www.androidcentral.com/best-raspberry-pi-screen)
[https://www.amazon.com/Raspberry-Touchscreen-Monitor-1024x600-Speakers/dp/B07S51QDTG?tag=androidcentralb-20&ascsubtag=UUacUdUnU79661YYwYg](https://www.amazon.com/Raspberry-Touchscreen-Monitor-1024x600-Speakers/dp/B07S51QDTG?tag=androidcentralb-20&ascsubtag=UUacUdUnU79661YYwYg)

---

### Post by MoebusNet on 2020-07-19
Thank you for the links; very interesting. A touchscreen interface would be more portable, but my impression is that this is still a work-in-progress in Linux. You are definitely correct that cost could quickly become an issue - it seems the display and the battery are the major cost concerns, although packaging a portable system in a case to eliminate external wiring is another issue. As far as changing MAC addresses, it seems relatively trivial in software to write a macro that would randomly selected among plausible MAC addresses. In Windows and others ;) it is trivial to manually change your MAC address shown to your network. It just seems everyone designs their hardware and software for maximum surveillability. Cell phones as a textbook example.

---

### Post by Tadaen_Sylvermane on 2020-07-19
Dont reinvent the wheel? Get a modest laptop and use a live image? Shouldn't be to hard to modify image to automatically do the mac address business on boot. Also install your preferred browser.

Built for portability.

---

### Post by MoebusNet on 2020-07-20
Ya know, I considered the notebook/laptop concept. The trouble I find is that the expense as well as the weight & size are deterrents. For example, I've got an older notebook with a decent battery that is paid for; trouble is it is too old for the video card to be well-supported (no proprietary drivers) and its 32-bit operating system requirement is no longer supported by most distros. It weighs about 7 pounds, too. I was hoping for something smaller and *much* cheaper. I suppose something like a Chromebook running Linux might work if the price was right. I'd still want a live image that was very light-weight to avoid excessive boot times as well as to run in RAM only.

---

### Post by mastablasta on 2020-07-21
> **MoebusNet said:**
> I suppose something like a Chromebook running Linux might work if the price was right. I'd still want a live image that was very light-weight to avoid excessive boot times as well as to run in RAM only.

you can get descent HPs with ryzen 3 for 350 EUR. wth nvme inside, they boot in few seconds (less than 20sec). add a specialised live os and you really are ready in few seconds (8-10). also ryzen 3 is strong enough to do some other work on it.

if you are in US i think there was an underrated very good 200USD Walmart laptops that worked well with linux. i remember seeing a review somewhere.

why limit yourself with chromebook?

---

### Post by MoebusNet on 2020-07-21
Having owned a netbook (remember when those were a thing?) I try not to low-ball the specifications for my systems that I intend to do work on. That was why I was hoping for an extremely cheap way to web-browse anonymously. With the world-wide political climate, I'm sure I'm not the only one who would like to access information without joining someone's list of politically incorrect thinkers. You might think there would be a market for such a device.

---

### Post by mastablasta on 2020-07-22
> **MoebusNet said:**
> Having owned a netbook (remember when those were a thing?) I try not to low-ball the specifications for my systems that I intend to do work on. That was why I was hoping for an extremely cheap way to web-browse anonymously. With the world-wide political climate, I'm sure I'm not the only one who would like to access information without joining someone's list of politically incorrect thinkers. You might think there would be a market for such a device.

a device can be any PC, you just need a USB key. since it can be any PC you could get a used laptop with i3 or i5 inside. depending on your needs. they would be very cheap. and as i see they still sell 12" and 13" ones but they don't call them netbooks. 

there is also a bunch of cheap laptops with Intel celereon (old Atoms). some are without OS. they actually perform well for websurfing and if you are short on cash you could probably get a used one for 80 EUR or less.

---

### Post by MoebusNet on 2020-07-24
Thanks for the ideas,; I had no idea that  Celerons were a version of Atom processors. It's too bad that there aren't any distro's to take advantage of old tablets (that I'm aware of). Big screen, big battery, minimal weight. If only the proprietary bits could be identified and open-sourced, tablets booted to run from removable media would fit the bill nicely. Apple's hardware, for example, is standardized across it's year models. But Android's OS was Linux-conceived even if hardware was less standardized. For example, this ancient tablet is running on Android 4; current is 10 but this is basically abandonware. Battery & screen are still great, just abandoned as 'too old'.

---

