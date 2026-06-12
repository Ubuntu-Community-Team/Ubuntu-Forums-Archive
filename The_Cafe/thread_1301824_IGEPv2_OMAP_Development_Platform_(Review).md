---
title: "IGEPv2 OMAP Development Platform (Review)"
date: 2009-10-26
forum: The Cafe
---

### Post by simonrichards150 on 2009-10-26
***I posted this over at [[COLOR="DarkOrange"]ebuyer forums[/COLOR]]("http://forums.ebuyer.com/showthread.php?t=52288"), and someone suggested I should post it here, so enjoy!***

So yesterday the FedEx guy brought me something special :D

[IMG]http://farm3.static.flickr.com/2588/4008578742_2cedc75a9c.jpg[/IMG]

I give you... the IGEPv2 OMAP dev platform!

Hardware:

[[IMG]http://farm3.static.flickr.com/2666/4007931247_2752f0b5f3.jpg[/IMG]]("http://www.flickr.com/photos/simonrichards150/4007931247/sizes/o/")
(Click for larger version)

I've only been playing with it for a day but it seems pretty awesome so far. I got linux to boot and i've got the WiFi working, so I can SSH/SCP. 

The fact it's ARM means I have to recompile everything which is a bit of a pain, but i'm working on getting Ubuntu on it. 

ISEE (the company making these) provides an ubuntu VM image with compilation tools etc which is handy:

[IMG]http://www.upload3r.com/serve/131009/1255444445.jpg[/IMG]

I can't try out the HDMI as I don't have a DVI monitor, but when I do get one I will update this thread with my findings.

Here's the serial output when the board is powered on:

```
Texas Instruments X-Loader 1.4.2 (Oct 13 2009 - 13:40:57)
Detected Numonyx OneNAND 4G Flash
Reading boot sector
Loading u-boot.bin from onenand


U-Boot 2009.08-0-dirty (Sep 22 2009 - 13:31:59)

OMAP3530-GP ES3.1, CPU-OPP2 L3-165MHz
IGEP v2.x rev. B + LPDDR/ONENAND
DRAM:  512 MB
Muxed OneNAND(DDP) 512MB 1.8V 16-bit (0x58)
OneNAND version = 0x0031
Chip support all block unlock
Chip has 2 plane
Scanning device for bad blocks
OneNAND: 512 MB
In:    serial
Out:   serial
Err:   serial
Die ID #7b8c00040000000004035c1411010004
Net:   smc911x-0
Warning: smc911x-0 MAC addresses don't match:
Address in SROM is         ff:ff:ff:ff:ff:ff
Address in environment is  ac:de:48:00:02:54

Hit any key to stop autoboot:  0
```Everything works pretty well, it's definitely speedy, and when I get a DVI monitor it should really come into it's own, if I can get the DSP to work, then it will play back HD video. 

And of course, with that USB port, it will use any USB device you have drivers for!

So anyway, more pictures :

[IMG]http://farm3.static.flickr.com/2597/4008582470_af4140244b.jpg[/IMG]
[IMG]http://farm3.static.flickr.com/2669/4008514136_e95c1b7750.jpg[/IMG]
[IMG]http://farm3.static.flickr.com/2593/4008572208_587d3b5ebe.jpg[/IMG]

And they are all (and more) on my flickr: [http://www.flickr.com/photos/simonrichards150/sets/72157622577300296/](http://www.flickr.com/photos/simonrichards150/sets/72157622577300296/)

Update: Ubuntu is now running on it, with apache/PHP/mysql/webmin etc

Any questions feel free to ask :)

---

### Post by Elfy on 2009-10-27
moved to cafe

---

### Post by 3rdalbum on 2009-10-27
Wow that's pretty cool. I was looking at the Beagleboard a while back, trying to justify a purchase ("I could use it for web surfing when my main computer is doing video encoding, and switch between them with a KVM"). I never did. But I'm glad you're getting use and enjoyment out of your purchase!

---

### Post by simonrichards150 on 2009-10-29
Thanks for moving!

@3rdalbum

It's a wonderful device. Its just like the beagleboard except it has more I/O already there on the board itself. Lots of fun for 149 Euros :p

---

### Post by Nevon on 2009-10-29
Holy crap! I didn't realize how small it was until that picture with the credit card next to it. :O

---

### Post by adceran on 2011-07-27
Hi! I have this IGEPv2, but my Ubuntu release dont boot fully...I followed the steps of the igep.wiki.es for the 10.10 version, where dou you find info to install ubuntu? can do you see the Wifi interface? a lot of thanks!

---

### Post by belewm2010 on 2012-03-16
I am looking for Used IGEPv2 boards. Anyone have one they'd like to sell? Also do you know if there are any US distributors for this board?

---

