---
title: "NVFlash Help"
date: 2019-01-22
forum: The Cafe
---

### Post by Incarnadine on 2019-01-22
I recently bought a used GTX 970 online, but there seems to be something wrong.

The card has this printed by the PCI Express interface: 180-1G401-1102-A02

Also, before my BIOS POST on boot, I get a notification that the video card is not for production use. What the hell?

Was this a test card? I tried to download the GTX 970 driver from Nvidia, but the driver software doesn't recognize the card.

After grabbing the video card info using NVFlash, this is what I get:

C:\nvflash>nvflash64 --list
NVIDIA Firmware Update Utility patched by Vipeax
Copyright (C) 1993-2018, NVIDIA Corporation. All rights reserved.


NVIDIA display adapters present in system:
<0> Graphics Device      (10DE,13C3,10DE,116D) H:--:NRM  S:00,B:01,D:00,F:00

Would it be possible to re-install the GTX 970 BIOS back on the card with NVFlash? I really have nothing to lose at this point.

---

### Post by TheFu on 2019-01-22
There are a bunch of fake nvidia cards on the internet.  Usually they are $30 cards which have been flashed to report the wrong model number.  You can thank the cryptocurrency mining bubble for this artifact.
[https://linustechtips.com/main/topic/908282-fake-cheap-gtx-970-from-china-and-other-scams/](https://linustechtips.com/main/topic/908282-fake-cheap-gtx-970-from-china-and-other-scams/)

So, your best option is to get your money back, if that isn't too late.
Or figure out which cheap card it actually is and try to flash the correct BIOS. Lots of GTX 550 ti have been used in these scams and some GT 545 from corporate leases.

I hope I'm wrong.

---

### Post by MartyBuntu on 2019-01-24
> **TheFu said:**
> There are a bunch of fake nvidia cards on the internet.
Yep. These cards are all over eBay and other sites.

Quick tip...if it has a VGA port on the back of the card, it's likely a fake.

---

### Post by Frogs Hair on 2019-01-24
Some of these Nvidia cards are actually older cards made to look like newer cards and the electronics have been altered so the operating system misidentifies them.

---

