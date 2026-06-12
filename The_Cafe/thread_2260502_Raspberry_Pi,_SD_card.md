---
title: "Raspberry Pi, SD card"
date: 2015-01-12
forum: The Cafe
---

### Post by linuxyogi on 2015-01-12
Hi,
I have ordered a Raspberry PI today with a HDMI to DVI cable, a case for the Pi, micro usb cable.
I already have a USB power supply. Do I need to buy a SD card separately or does each board comes preinstalled with a SD card ?
I have ordered the Pi from[ here]("http://www.snapdeal.com/product/raspberry-pi-model-b-plus/2089912179"). Please have a look. [This]("http://www.amazon.in/Digitek-USB-Travel-Charger-DMC-010/dp/B00GB0PBV6") is my usb power supply

---

### Post by QIII on 2015-01-12
Unless you bought a "kit", the SD card is not included.  You'll have to purchase that separately.  I bougbt a 32 GB card rather than the bare minimum.

---

### Post by linuxyogi on 2015-01-12
Just placed [an order]("http://www.flipkart.com/sandisk-sdhc-8-gb-class-10-ultra/p/itmddxa8kqmg6cbw?pid=ACCDDXAFYKSQMCGB"). Thanks. Once I get all the items I will try an figure out how to install the image on the SD card. It may sound weird but I will be using this Pi as my main PC and the x86 for gaming only.

---

### Post by QIII on 2015-01-12
The Pi is no speed demon and the resources are limited, so bear that in mind.

I used the Rasbian image from the R Pi website and followed the simple and clear instructions.

---

### Post by linuxyogi on 2015-01-12
I just need a browser and hd video playback. I heard that the pi can play 1080p videos

---

### Post by pqwoerituytrueiwoq on 2015-01-12
depending on the codec you may have issues with that, hope you are not planning on using adobe flash which it could not handle if it were even compatible with the architecture
you may need to OC it some, you can OC to 800MHz without increasing the voltage
* i have a Pi (raspbian), i have yet to use the GUI DE on it, it does everything i have asked of it

---

### Post by linuxyogi on 2015-01-12
I rarely use flash player. I use livestreamer to stream the video to mplayer. My guess is a PI can decode h.264 coz some people are using XBMC on it.

---

### Post by tgalati4 on 2015-01-12
It can even do 3D high definition in 1080.  It's impressive for the price and small power consumption.  Let us know how it works out.

---

### Post by Bucky Ball on 2015-01-13
> **linuxyogi said:**
> My guess is a PI can decode h.264 coz some people are using XBMC on it.

RaspBMC image best for using xbmc. Worked great for my purposes. Don't think of this as a regular computer you can install whatever Linux OS on. Depends what images are available for it. I used addons to watch Australian catch-up tv channels, but never ran a browser on it. Not sure how you'd go with that. 

Great as a media server, though. Have moved onto the Odroid U3 now, which has images for Ubuntu and flavours of it. 

The Pi can play different formats (h.264 and 1080p) but when I was using one, you needed to purchase the codecs from Element 14 then install. No biggie. Less than AU$5 for both from memory.

Good luck. It's a fun little machine, but don't expect a full blown speed machine, that's for sure. ;)

---

### Post by mastablasta on 2015-01-13
you might not use flash but websites do. if I remember correctly it's perfomance is similar to 300 MHz Pentium II, with a good GPU.

---

### Post by The Cog on 2015-01-13
I think the Pi B+ uses a micro-SD, not a full sized SD card that the previous models used. 
[http://www.raspberrypi.org/introducing-raspberry-pi-model-b-plus/](http://www.raspberrypi.org/introducing-raspberry-pi-model-b-plus/)

---

### Post by linuxyogi on 2015-01-27
Finally received the Pi, installed Raspbian using the Noob image. Played some 1080p videos using omxplayer. Compiled the GUI for omxplayer know as tboplayer. Problem is it goes fullscreen even when playing mp3 files. I tried gnome-mplayer but it didn't work.

Web surfing is slightly sluggish using Epiphany.

---

### Post by Bucky Ball on 2015-01-28
For media stuff I reckon RaspBMC image is the go. Plays audio/video from any machine in the house once you set up the connections, and that's easy. Has an audio play for music and Xbmc is full screen anyhow. ;)

It doesn't have a web browser, just boots straight to XBMC, but that never bothered me. Didn't want it to be anything but a media server anyhow, and it did that brilliantly. Surfing the web on the RPi would be sluggish.

To my mind, running a regular OS on the Pi is a bit of a hack. Not sure that was really ever the intention of the manufacturers of the dinky device.

---

### Post by linuxyogi on 2015-01-31
I too realized the fact that surfing the web with a Pi is problematic, Installed RaspBMC. Playback is flawless but I am having an issue with running NFS server on the Pi. I have installed NFS server on the Pie. I can mount the share from my Desktop but when I try to copy large files the copy process crashes midway. At this point I can no longer see the contents on the shared folder from the desktop. Then I reboot the Pi but same thing again. I have shared /media on the pie I guess the reason behind the crash is a slow USB flash drive but I am not sure.

---

### Post by Bucky Ball on 2015-01-31
> **linuxyogi said:**
> I too realized the fact that surfing the web with a Pi is problematic, Installed RaspBMC. Playback is flawless but I am having an issue with running NFS server on the Pi. I have installed NFS server on the Pie. I can mount the share from my Desktop but when I try to copy large files the copy process crashes midway. At this point I can no longer see the contents on the shared folder from the desktop. Then I reboot the Pi but same thing again. I have shared /media on the pie I guess the reason behind the crash is a slow USB flash drive but I am not sure.

This is starting to get a bit off-topic from this thread, but install RaspBMC on a flash drive (USB) and try again. Much faster. You don't want to intall the OS to the Pi. You will find that if the image is installed onto USB performance improves dramatically. There is an option to do that during the making of the USB. :)

---

### Post by help_me2 on 2015-02-03
I hate to break it to those who recently bought a pi. It was just announced that there is a new raspberry pi 2. It has a quad core cpu and 1gb ram. It is identical in size and form factor to the B+, (same price too) but much faster. [http://www.raspberrypi.org/raspberry-pi-2-on-sale/](http://www.raspberrypi.org/raspberry-pi-2-on-sale/)

I'm getting one for my Kodi setup.

---

### Post by QIII on 2015-02-03
Why is saying you can get a great deal for $35 "breaking it to" anyone?

It's good news!

Edit:  this is also ARM7, which means Canonical may now support it.

Just ordered mine.

---

### Post by The Cog on 2015-02-03
I would be mighty upset if I had just ordered the B+ (I very nearly did order one the evening before the announcement). As it is, I have a shiny new Pi 2 B in front of me, and I'm about to go and connect it to the TV.

---

### Post by Bucky Ball on 2015-02-03
> **The Cog said:**
> As it is, I have a shiny new Pi 2 B in front of me, and I'm about to go and connect it to the TV.

Good luck with that and enjoy. My older model is retired now, but they are rocking little dinky gizmos. No complaints from me. ;)

If you want to use it as a media server only, I highly recommend the RaspBMC image.

---

### Post by QIII on 2015-02-03
Looking forward to this.  I have my B+ running on a USB thumb drive, which improves the data access by about 40x over the Class 10 SD card (but it still has to boot from SD).

---

### Post by Bucky Ball on 2015-02-03
> **QIII said:**
> I have my B+ running on a USB thumb drive, which improves the data access by about 40x over the Class 10 SD card (but it still has to boot from SD).

Definitely the only way to fly. Greatly improves performance. ;)

---

### Post by linuxyogi on 2015-02-04
My plan was to use my desktop for gaming only and do everything else on the Pi but that's a difficult thing to do given the low ram. What a loss ! I will buy a Pi2 in the middle of this year.

---

