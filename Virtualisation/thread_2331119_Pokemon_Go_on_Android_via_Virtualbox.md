---
title: "Pokemon Go on Android via Virtualbox"
date: 2016-07-18
forum: Virtualisation
---

### Post by devlin3 on 2016-07-18
Hello,

I was wondering if I could run Pokemon Go on my Lenovo T530. I have already set up Android Marshmallow successfully on Virtualbox. However, Pokemon Go does not support Intel processors, and my Lenovo has an Intel Core i5. Will this prevent me from running Pokemon Go? Is there some way to have Virtualbox "mock" a different processor?

---

### Post by MAFoElffen on 2016-07-18
> **devlin3 said:**
> Hello,
I was wondering if I could run Pokemon Go on my Lenovo T530. I have already set up Android Marshmallow successfully on Virtualbox. However, Pokemon Go does not support Intel processors, and my Lenovo has an Intel Core i5. Will this prevent me from running Pokemon Go? Is there some way to have Virtualbox "mock" a different processor?
In this recent article [HERE]("http://www.androidpolice.com/2016/07/13/pokemon-go-goes-germany-officially-now-works-android-n/")
> 
UPDATE: 2016/07/13 4:27AM PDT
As confirmed by our readers, version 0.29.2 of Pokémon GO also works with Intel x86-based processors too, like several of ASUS' ZenFone devices.

Not sure which Android x86 would work with is but it now at least sounds possible. Would be curious what you find. Please come back and tell us.

I've used Android x86 in virtual, but had to play with the input devices in the virtual machine to add a mouse mapped touch pad as the touch screen input.

---

### Post by MAFoElffen on 2016-07-19
O-o... I just thought of something. 

Since Pokemon Go uses GPS data. Lenovo T530 does ntot have a GPS. What are you going to use for GPS? Pass-through a USB GPS Receiver?

---

### Post by devlin3 on 2016-08-14
Sorry for the egregiously late reply. Lenovo states on their website that this laptop supports gps with Windows OS, but says nothing about Linux. I suspect that this is the reason that after attempting to download the Pokemon Go game from the Play store, I am unable to run the game without an error screen preventing me from doing so. 

I'll update this thread if I decide to get a usb gps device and go from there

---

### Post by MAFoElffen on 2016-08-15
The challenge in doing something like that would then be to use a hypervisor where you can do USB pass-through... to be able to use a USB GPS on the host, accessed by your VM Guest. I have one that was a rechargeable unit, that I originally got for WinMobile Phone, so has been around long enough to be recognized by Windows, Linux and Android.

---

### Post by Bucky Ball on 2016-08-15
I have run into exactly the same issue, but running another app which is dependent on location. I installed Remix OS (Android for i386) as a virtual machine and, as it won't work with Guest Additions so can't access anything on the host, including a GPS even if I had one, it refuses to place me anywhere but the US (I'm in Australia) and I spent about four or five days unsuccessfully trying to trick it, in the process learning way more about Android than I cared to. ;)

I found a file where I could change location but it made no difference. Couldn't find a fix.

---

