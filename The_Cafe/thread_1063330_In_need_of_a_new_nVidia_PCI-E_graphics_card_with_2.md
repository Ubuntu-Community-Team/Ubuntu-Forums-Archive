---
title: "In need of a new nVidia PCI-E graphics card with 2xHDMI"
date: 2009-02-07
forum: The Cafe
---

### Post by RaZoR1394 on 2009-02-07
I feel like I don't want to buy another laptop like I have planned. Instead I want to buy a new graphics card for my fulltower. It's an old board in it, DFI Lanparty NF4 Ultra-D which has the old PCI-E 1.0. I only need something which can output both video and audio through HDMI. One HDMI connector will be used for my Onkyo TX-SR606 receiver. The other one for my TFT screen but may in the future be used with another HDMI receiver. I'm not going to play any games with it AFAIK. I need something that doesn't use more than one slot/backplate. Even though the case is huge there are a lot of PCI-E and PCI cards in it. Active cooling would be a positive. It has to be nVidia cause ATI has failed me again with the Mobility 3200HD. It needs to be able to help with decoding x264 cause my Opteron 185 isn't that great and I want to do other things like browsing on my TFT while watching x264 on my 32" LCD. I'm not going to do 1080P, only 720P but in the future I may go higher but in case that happens I will probably have a new computer by then.

Please help me find a decent Geforce card. It has to work with Jaunty.

So will I have to connect a cable between the motherboard and the graphics card and the motherboard for audio? Do you think it will work.

---

### Post by mips on 2009-02-08
> **RaZoR1394 said:**
> It needs to be able to help with decoding x264 ...


Look for cards that have VDPAU support with the 180.xx drivers. Will probably have to browse the nVidia website.

---

### Post by RaZoR1394 on 2009-02-08
Thanks. I'm pretty sure I saw a card with 2xHDMI outputs and one DVI-I. I think it was based on the Geforce 9500GT or 9600GT GPU. I can't find it though.

---

### Post by mips on 2009-02-09
I'm pretty sure you get DVI->HDMI adapters.

How many outputs do you need, 3?

---

### Post by madverb on 2009-02-09
Isn't DVI higher quality than HDMI?

---

### Post by RaZoR1394 on 2009-02-09
> **mips said:**
> I'm pretty sure you get DVI->HDMI adapters.

How many outputs do you need, 3?

No, the card I saw had two pure HDMI outputs, without crappy adaptors. There was also either a DVI-I or DVI-D output, most likely DVI-I incase you would like to use analogue.

I have seen a lot of ATI cards with the DVI-I->HDMI "solution".

I only need two HDMI. I don't care about DVI or VGA.

DVI and HDMI carries the same signal except DVI doesn't carry AUDIO. That's how I understood it. Displayport however is bit different.

---

### Post by RaZoR1394 on 2009-02-09
I found one with 1xDVI, 1xHDMI and 1xDisplayPort.

Sparkle Geforce 9500GT DisplayPort Passive 1GB

[http://www.prisjakt.nu/produkt.php?p=389900](http://www.prisjakt.nu/produkt.php?p=389900)

Maybe better to have one DisplayPort to be ready for the future?

edit:

It's on Phoronix.

[http://www.phoronix.com/scan.php?page=article&item=sparkle_9500gt&num=1](http://www.phoronix.com/scan.php?page=article&item=sparkle_9500gt&num=1)

---

### Post by Joeb454 on 2009-02-09
I have a passive cooled 9500GT (1GB) It has DVI, VGA & HDMI

I would've quite liked display port, but it works fine under Ubuntu :)

---

### Post by RaZoR1394 on 2009-02-09
> **Joeb454 said:**
> I have a passive cooled 9500GT (1GB) It has DVI, VGA & HDMI

I would've quite liked display port, but it works fine under Ubuntu :)

Do you know how much it helps when decoding h264/x264 in Ubuntu with VDPDAU? Will there be problems with using PCI-E 2.0 with an 1.0 slot? Is it like SATA; backwards compatible? Maybe I will loose some performance? I don't really think there should be a problem with 720P?

It looks like I'm buying this card as soon as I can. I found a store with an acceptable price. The card is really cheap in comparison to those I have bought for gaming.

---

### Post by mips on 2009-02-09
> **RaZoR1394 said:**
> Do you know how much it helps when decoding h264/x264 in Ubuntu with VDPDAU? 

Will there be problems with using PCI-E 2.0 with an 1.0 slot? Is it like SATA; backwards compatible?

It helps a lot. [http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_vdpau&num=1)


[http://en.wikipedia.org/wiki/PCI-E](http://en.wikipedia.org/wiki/PCI-E)
> PCIe 2.0 is backward and forward compatible with PCIe v1.x. PCI Express 2.0 has good backwards compatibility, new PCIe 2.0 graphics cards are compatible with PCIe 1.1 motherboards, meaning that they will run on them using the available bandwidth of PCI Express 1.1. Overall, graphic cards or motherboards designed for v2.0 will be able to work with the other being v1.1 or v1.0.

---

### Post by RaZoR1394 on 2009-02-09
Looks good. Thanks. The Sparkle card is also not Passive like written in the "Prisjakt" link. I have reported this to Prisjakt. It's active both by looking at the picture and the Sparkle link. I don't find any problem with it being active however.

[http://www.sparkle.com.tw/product_detail.asp?id=83&sub_id=271#](http://www.sparkle.com.tw/product_detail.asp?id=83&sub_id=271#)

---

### Post by RaZoR1394 on 2009-02-20
Ok both the price comparison page and the store had the wrong picture. The one currently on Sparkle is correct (large black passive) but I believe Sparkle had the older picture with the active cooler last time I looked. I may be mistaken.

The cooler took 2 slots easily. I couldn't use the top x16 slot so I used the bottom. I don't know how big difference that will make. I connected my computer monitor to the DVI-I port and my receiver to the HDMI port. When I booted up I got picture on my main computer TFT LCD. I installed the nVidia drivers 180.29 and rebooted. Once I was booted up and logged in the icons were bouncing on the main screen and the cursor was going crazy swiching between working mode and standard pointing mode. The top and bottom bar were not present. It was as if the bars were trying to load then failed. I switched on the HDMI output. I checked the receiver and there was picture on the LCD but the mouse acted the same there. ALT-F2 made the launch prompt appear then it quickly died. I managed to launch nautilus and launch nvidia-settings from there and once I was there the desktop was stable. So I switched the type of extended desktop mode. Once I rebooted everything was normal after logging in. I have connected the cable from the SPDIF pins on the motherboard to the SPDIF IN on the Sparkle card. I connected the "empty" one to SPDIF OUT and the "+" one to +5V. I don't know if this is correct but the manual provided both on the Sparkle site and in the box was really bad. It was more like a generic manual for all their cards. I checked the receiver and there was no sound. I'm going to dig further into it. Probably I'll have it solved during the weekend.

This worries me (from nvidia-settings):

Bus Type: PCI Express 2X

edit:

Seems like the Sparkle site had the correct picture. I mixed these two up:

SX95GT1024D2-3D - ACTIVE
SX95GT1024D2-3DP - PASSIVE

---

### Post by RaZoR1394 on 2009-02-25
I have now gotten HDMI with Dolby Digital working from Mplayer and Totem. I'm currently using MPlayer and 720P mkv works fine. I know 1080P is an issue on this computer with XV so I need to get VDPAU up and working. I have installed VPDAU libs, 180.35 and the vdpau enabled mplayer and the player crashes but I will read through nvnews as they have some info on it.

I used this guide:

[http://zacgarrett.com/software/installing-mplayer-vdpau/index.html](http://zacgarrett.com/software/installing-mplayer-vdpau/index.html)

This was how I connected S/PDIF from the mobo:

Black - GND
Red - S/PDIF OUT

---

