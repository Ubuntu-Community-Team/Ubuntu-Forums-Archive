---
title: "Low cost mini pc (arm)"
date: 2016-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by enricobe on 2016-01-07
Hello,
I want to buy a low cost mini pc (max 100&#8364;/$). There is a wide range of mini pc, but I've understood that the large part of them are poor. I have un-pledged  a single board PC on kicksarter (really sad to cancel the pledge) and now I want to ask to you which are the best ones. 

I would like a mini-pc with:
- Arm cpu and at least some linux os to install on it with good performance
- NOT AN AllWinner CPU (I've read that they are really poor cpu)
- Low consumption (lower is better)


I want to use it as a small "home server" and sometimes play some videos but I don't need a 4K support or a 2Ghz processor :) Any idea about the one I should buy?
Thank you!

---

### Post by MartyBuntu on 2016-01-07
Why ARM?

---

### Post by QIII on 2016-01-07
Did you want to stick with an SBC?

---

### Post by pqwoerituytrueiwoq on 2016-01-07
I use a Raspberry Pi as a home server
assuming you want a wired network you should go with a B+ or B2 model, the B+ uses less power, but it is discontinued so it is harder to find at a fair price compared to the more powerful b2

---

### Post by Bucky Ball on 2016-01-07
I use an Odroid and before that a Raspberry Pi. I can recommend either. Never a problem.

---

### Post by QIII on 2016-01-07
I've had three R Pis, most recently the Model 2 B.  Great devices. At $35US (you'll have to buy a few more items to make them useful -- maybe $75 at most), they are hard to beat.

The Odroid XU4 I have now is pretty impressive, but just the board and power supply were $75US.  I'm using it as a web development platform.  Beware!  You can get sucked in to adding bells and whistles!

---

### Post by enricobe on 2016-01-08
Thank you all!

I don't really need an ARM but I want a low energy consumption and low temperature device and it seems that ARM devices are the best. I can also consider other CPU if they have those characteristics.

I prefer a mini-pc with a little case as tronsmart r68 or belink i68 which I've considered for a while, but I really can't understand if these mini-pic type can run Linux or only android. I really don't want Android because I don't need a "smart-tv" mini-pc.

on Amazon ITA the Raspberry Pi 2 with desktop kit costs 66&#8364;, is it a good price?
The kit includes

[LIST]
[*][COLOR=#111111]Latest Raspberry Pi 2 Model B (Quad Core, 1GB RAM)[/COLOR]
[*][COLOR=#111111]8GB Sandisk Ultra Class 10 MicroSD (pre-imaged with NOOBS[/COLOR]
[*][COLOR=#111111]Raspberry Pi Official Multinational 5V 2A Power Supply[/COLOR]
[*][COLOR=#111111]Raspberry Pi Official Case[/COLOR]
[/LIST]

---

### Post by Bucky Ball on 2016-01-08
Don't know if that's a good price (in Australia) but just to add that you can wipe Noobs and install a different spin if you want.

Also, just to make you aware that with the RPi, and the Odroid, it is not as simple as downloading the ISO from the Ubuntu site and installing. You will need an image for the specific device which works for ARM. [Here are some for the RPi]("https://www.raspberrypi.org/downloads/"). You will find some more and some for Odroid also if you go looking. I use RaspBMC myself (now known as OSMC I believe). Using the Odroid as a media server only so a perfect fit.

---

### Post by mastablasta on 2016-01-08
I bought mine from UK from modmypi along with case and all. I have the old version. which would be enough for what you want to do. but newer version is faster so it should fit well. I am running OpenElec (media server). 

you will need card reader for SD cards if you do not have one yet. a USB one costs less than 2 EUR in china.
I also bought a small keyboard later on for 12 EUR form china. it has a trackpad and is a keyboard mouse thingy. works well to enter some text occasionally. I also use it on th eother server.

anyway pi is strong enough even as a small web server (as long as there isn't some large amount of users loging on at same time). can serve as family server or maybe for some backups (not the fastest but it does it's job).

---

### Post by enricobe on 2016-01-08
> **Bucky Ball said:**
> 
Also, just to make you aware that with the RPi, and the Odroid, it is not as simple as downloading the ISO from the Ubuntu site and installing. You will need an image for the specific device which works for ARM. [Here are some for the RPi]("https://www.raspberrypi.org/downloads/"). You will find some more and some for Odroid also if you go looking. I use RaspBMC myself (now known as OSMC I believe). Using the Odroid as a media server only so a perfect fit.
Yes, I know that is not so simple as a normal PC but I'm sure that I'll find a lot of help and documentation about that. I've compiled a kernel with the online documentation so I think I can do that :D
 
> **mastablasta said:**
> I bought mine from UK from modmypi along with case and all. I have the old version. which would be enough for what you want to do. but newer version is faster so it should fit well. I am running OpenElec (media server). 

you will need card reader for SD cards if you do not have one yet. a USB one costs less than 2 EUR in china.
I also bought a small keyboard later on for 12 EUR form china. it has a trackpad and is a keyboard mouse thingy. works well to enter some text occasionally. I also use it on th eother server.

anyway pi is strong enough even as a small web server (as long as there isn't some large amount of users loging on at same time). can serve as family server or maybe for some backups (not the fastest but it does it's job).
Thank you. So do you advice me to buy a Rpi2 too?

it seems there are no other option for what I want :D

---

### Post by Bucky Ball on 2016-01-08
> **enricobe said:**
> I want to use it as a small "home server" and sometimes play some videos but I don't need a 4K support or a 2Ghz processor :)

> **enricobe said:**
> So do you advice me to buy a Rpi2 too?

The Pi or a version of the Odroid seem to fit the specs you are looking for and can do what you are wanting to do. Both have worked well for me. Small home server and used to watch tons of catch-up TV, not 4K, and TV recordings. The Odroid, running Lubuntu, has a 1Gb hard drive dangling off it with a large video collection. Hums along.

Good luck. :)

---

### Post by coldraven on 2016-01-08
I bought a raspberry pi 2 bundle, which included a USB keyboard, power supply etc. for £50 on ebay. I love my Pi :)

---

### Post by enricobe on 2016-01-08
I'm a Raspberry Pi 2 owner. Thank you all for your help!
:D:D:D

Now I need to study! :popcorn:

---

### Post by speedwell68 on 2016-01-09
I have 5 RPIs.  One model 2B, 3 model Bs and the new Zero.  All are brilliant devices.

---

### Post by enricobe on 2016-01-09
> **speedwell68 said:**
> I have 5 RPIs.  One model 2B, 3 model Bs and the new Zero.  All are brilliant devices.
What do you use them for? :)

---

### Post by pqwoerituytrueiwoq on 2016-01-09
given you location aside from ebay/amazon here are 2 distributors
[http://thepihut.com/collections/raspberry-pi](http://thepihut.com/collections/raspberry-pi)
[https://shop.pimoroni.com/products/raspberry-pi-2-model-b](https://shop.pimoroni.com/products/raspberry-pi-2-model-b) | [https://shop.pimoroni.com/products/raspberry-pi-zero](https://shop.pimoroni.com/products/raspberry-pi-zero)
if you get a gigabit USB 3 adapter you can get around 200Mbit over the network
personally i would not get a 8gb card, just get 16 or 32 gb, i have never had a issue with G.Skill cards, i just got some 16gb cards for just under 4 USD each and a 32gb card for under 10 USD

if you just want a headless server you can get a pi zero and a lan adapter for under the cost of a pi2, but yo will have to wait for them to get instock, hoping to see some monday

this adapter is known to work [http://www.amazon.com/gp/product/B00FFJ0RKE](http://www.amazon.com/gp/product/B00FFJ0RKE)
you may want to pick up a mini hdmi to hdmi cable for watching videos on a pi zero
though unless you plan to control it via network you will want a usb hub for adding a mouse/keyboard, the hub can power the pi via the data usb port, so make sure you only use one adapter

both those stores have a thing called omnivesa that you can use to put a pi on the back of your tv, not sure if your tv is wall mounted

---

### Post by Bucky Ball on 2016-01-09
I would not power the RPi from anything but a separate power supply and the hub from its own power supply.

---

### Post by pqwoerituytrueiwoq on 2016-01-09
if you use 2 make sure the micro usb does not backfeed the pi, remember the original B board
this can require usb cable moding
the pi zero only needs 160ma without extra hardware, so running it off the hub is feasable as long as you use a quality power adapter on the hub

---

### Post by enricobe on 2016-01-09
I bought the PI2, the Official power supply and the official case.

This is what I've bought [http://www.amazon.it/Raspberry-Pi-Official-Desktop-Starter/dp/B015OJ5B8C/ref=sr_1_4?s=pc&ie=UTF8&qid=1452354819&sr=1-4&keywords=raspberry+pi+2](http://www.amazon.it/Raspberry-Pi-Official-Desktop-Starter/dp/B015OJ5B8C/ref=sr_1_4?s=pc&ie=UTF8&qid=1452354819&sr=1-4&keywords=raspberry+pi+2)

I think that the kit should have all what I need, doesn't it? Maybe I could spend a little less, but 66&#8364; seems a good price and it fits my budget

---

### Post by Bucky Ball on 2016-01-09
Pretty much it. You'll need a microHDMI (from memory) to HDMI cable to connect to a HDMI monitor and any other bits and bobs that become useful. I used mine with a powered seven port USB hub, USB wireless keyboard and mouse plugged into the television. The Odroid, which is very similar, has no hub and a powered USB dual-HDD dock with a 1Tb HDD in it.

The change in approach was that with the RPi, all our media files were strewn around various computers in the house and we'd access them via network on the Pi. With the Odroid, we are making an attempt to keep all media on the attached hard drive 'locally'. 

Customise post-purchase as required. A lot depends on what you want to do with it, but saying that, you may discover other things you can do with it you didn't think of before. :)

---

### Post by enricobe on 2016-01-09
> **Bucky Ball said:**
> Pretty much it. You'll need a microHDMI (from memory) to HDMI cable to connect to a HDMI monitor
Customise post-purchase as required. A lot depends on what you want to do with it, but saying that, you may discover other things you can do with it you didn't think of before. :)

I've read that the Raspberry Pi has a Full-size HDMI so, if this info is right, I think that I won't need a microHDMI->HDMI cable.

I bought it exactly because I want to understand what I can do with it. It quite difficult to guess want I can do with the RasPi without having it in my hands :) It should be delivered Tuesday or Wednesday of the next week. Only few days. 

Another question: I've found another distro that is packaged for the RaspPi and it's not listed in the official site. It's an independent italian distro, but also available in English and Spanish. [https://openmamba.org/en/](https://openmamba.org/en/) Has anyone ever tried it? I'm pretty interested but not sure that should be my first choice if no one has tried it.

---

### Post by Bucky Ball on 2016-01-09
Raspberry Pi project #1. Buy a 4 or 8Gb SD card and install openmamba on it in preparation to try it on the Pi. 

I tried a few out like this when I first got the Pi. In the end, the second card was used to keep a clone of the functioning OS card in case that install broke (which it occasionally did back in the early days of Pi!).

---

### Post by enricobe on 2016-01-09
> **Bucky Ball said:**
> Raspberry Pi project #1. Buy a 4 or 8Gb SD card and install openmamba on it in preparation to try it on the Pi. 

I tried a few out like this when I first got the Pi. In the end, the second card was used to keep a clone of the functioning OS card in case that install broke (which it occasionally did back in the early days of Pi!).
I have some 2Gb cards, the image size to download is 750MB, when I put it on the card it will use only that space (750mb)? If yes, can I try with that 2Gb cards? If no, how much space will it use (in your experience)? I'm downloading the image now

Some years ago people advise against install a OS on the USB flash disks because they were not designed for so much frequent read/write sessions. Is the same with the SD card? install the system on the Sd card could damage it?

---

### Post by Bucky Ball on 2016-01-09
Ah ha. There's a trick with the RPi. You can actually install the OS on a USB and it speeds things up considerably, BUT ... you still need to boot the device from the SD card. (I know I'm changing the subject a bit from what you asked but you reminded me of it. :))

[Here's a tutorial for Raspbian on USB]("http://raspipress.com/2013/05/install-and-run-raspbian-from-a-usb-flash-drive/"), but I would imagine it would apply to others with a tweak or two in the instructions. 

Yes, neither a USB or SD is going to last forever, certainly not the life expectancy of a HDD or SSD, which is one of the reasons I had a clone handy.

As for the 2Gb cards, give them a try and see if it fits. It will be good practice in creating SDs for the RPi. As there seems to be very little information on the openmamba site, you're just going to have to be a pioneer on that one. But you could try asking on the forums there. :) 

One thing I will say, by all means try it, but by the looks of their wiki page and forums, you may be pretty much on your own when it comes to getting support.

---

### Post by enricobe on 2016-01-09
> **Bucky Ball said:**
> Ah ha. There's a trick with the RPi. You can actually install the OS on a USB and it speeds things up considerably, BUT ... you still need to boot the device from the SD card. (I know I'm changing the subject a bit from what you asked but you reminded me of it. :))

[Here's a tutorial for Raspbian on USB]("http://raspipress.com/2013/05/install-and-run-raspbian-from-a-usb-flash-drive/"), but I would imagine it would apply to others with a tweak or two in the instructions. 

Yes, neither a USB or SD is going to last forever, certainly not the life expectancy of a HDD or SSD, which is one of the reasons I had a clone handy.

As for the 2Gb cards, give them a try and see if it fits. It will be good practice in creating SDs for the RPi. As there seems to be very little information on the openmamba site, you're just going to have to be a pioneer on that one. But you could try asking on the forums there. :) 

One thing I will say, by all means try it, but by the looks of their wiki page and forums, you may be pretty much on your own when it comes to getting support.

Thank you for the trick, I'll try it when I will be able to manage the RPi well :) There is a way to load the whole system on the Ram? I mean light systems like Puppy Linux and others. This should "fix the problem".

You said "you may be pretty much on your own when it comes to getting support.". This is exactly why I'll load OpenMamba on the 2GB Sd card and not in the 8Gb one :p The user data will be saved on the Sd Card, right? So I can switch system very easily by using the other Sd card, I suppose. Really thank you for your help and the time spent answering my questions

---

### Post by Bucky Ball on 2016-01-09
All good. I love these little devices! :)

> **enricobe said:**
> There is a way to load the whole system on the Ram? I mean light systems like Puppy Linux and others. This should "fix the problem".

Installing to RAM is one of the main features of Puppy, but never seen it done on a Pi and not sure if it's possible. These are development devices and all about experimenting, though, so ... What is the 'problem' you speak of?

> **enricobe said:**
> The user data will be saved on the Sd Card, right? So I can switch system very easily by using the other Sd card, I suppose.

Exactly right. Each SD is its own self-contained system, unless you dream up, discover, experiment with something exotic. Likewise, if you use the SD card boot/OS installed on USB method, each install would still be independent and include a set of SD card and USB specific to that OS only. Nothing is stored on the Pi itself. Nowhere to store it.

---

### Post by enricobe on 2016-01-09
> **Bucky Ball said:**
> All good. I love these little devices! :)



Installing to RAM is one of the main features of Puppy, but never seen it done on a Pi and not sure if it's possible. These are development devices and all about experimenting, though, so ... What is the 'problem' you speak of?

It isn't a real problem, I was speaking about the risk of damage the SD card with a OS installed on it. It's not a problem, I was only thinking if a "load on ram" OS would be possibile. 


> **Bucky Ball said:**
> 
Exactly right. Each SD is its own self-contained system, unless you dream up, discover, experiment with something exotic. Likewise, if you use the SD card boot/OS installed on USB method, each install would still be independent and include a set of SD card and USB specific to that OS only. Nothing is stored on the Pi itself. Nowhere to store it.
Very good news. In this way we can use different SD with different OS for different purpose.
Do you think that I can install the system also on a microSD card using the adapter or this can bring to other problems? I also have some 2GB microSD cards.

---

### Post by Bucky Ball on 2016-01-09
The micro-SD card adapter is the only method I've ever used. I don't know of many, or any, laptop/desktop computers with a micro-SD card slot 'natively'. :)

Adapter is exactly the same as using the micro-SD in a micro-SD card slot. Wouldn't be overly worried about SDs wearing out. It certainly is not going to happen within a week or month (or would be highly unusual).

---

### Post by enricobe on 2016-01-10
> **Bucky Ball said:**
> The micro-SD card adapter is the only method I've ever used. I don't know of many, or any, laptop/desktop computers with a micro-SD card slot 'natively'. :)

Adapter is exactly the same as using the micro-SD in a micro-SD card slot. Wouldn't be overly worried about SDs wearing out. It certainly is not going to happen within a week or month (or would be highly unusual).

Thank you. One last (really!) question: the SD  class (class 4, class 6, class 10...) is significant for the performance of the whole system? Supposing I have to buy another SD card and I want a good system performance, should I buy a class 10 (or more) sd card or I can save some money buying a class 4/6? I guess that a class 10 is always better and the answers depends on what the Pi is used for, but how much is important the class of the SD card?

---

### Post by Bucky Ball on 2016-01-10
Class 10. Nothing more to say on that one. It's what's recommended and expect the unexpected if you use a card that can't handle the job.

---

### Post by enricobe on 2016-01-10
> **Bucky Ball said:**
> Class 10. Nothing more to say on that one. It's what's recommended and expect the unexpected if you use a card that can't handle the job.

Ok, thanks!

---

### Post by Bucky Ball on 2016-01-10
[See this]("http://elinux.org/RPi_SD_cards"). Make sure you have a dig because there is a lot of info on the RPi already out there (a popular little devil). :)

[This]("http://elinux.org/RPi_SD_cards#Working_.2F_Non-working_SD_cards") shows that other class card do work, but I've never used one. Sandisk, Class10, 8Gb is my tool of choice, but you probably only need 4Gb.

---

### Post by enricobe on 2016-01-10
> **Bucky Ball said:**
> [See this]("http://elinux.org/RPi_SD_cards"). Make sure you have a dig because there is a lot of info on the RPi already out there (a popular little devil). :)

[This]("http://elinux.org/RPi_SD_cards#Working_.2F_Non-working_SD_cards") shows that other class card do work, but I've never used one. Sandisk, Class10, 8Gb is my tool of choice, but you probably only need 4Gb.
Yes, you are right. I should search instead of asking here for everything. I'm trying to emulate Raspian with qemu following the online how-tos so my journey starts now ;)

---

### Post by speedwell68 on 2016-01-10
> **enricobe said:**
> What do you use them for? :)

Media Centres.  Apart from the Pi Zero which is currently an Emulation Station, although that is going to become a robot of some kind as I have found a better way of playing retro games.

I have a RPI Model B in the 3 bedrooms of my house and in my lounge room I have a Model B2, all running Kodi 15.2 on Openelec 6.0.  The one in my lounge has an Ambilight Clone which is very cool.  I have also made a media server so they all have a synchronised media library.  Very simply I have got an old Acer Revo R3600 on which I have installed Ubuntu Server.  I then hooked up 4 large external HDDs, 2 for movies and 2 for TV shows, music is stored on the Revo's internal HDD.  I then upped the RAM to 4GB, using RAM I salvaged from scrap laptops.  I the setup NFS shares to the drives and music folder and used MySQL to tie it all together.  It all works very well.

> **Bucky Ball said:**
> I would not power the RPi from anything but a separate power supply and the hub from its own power supply.

With models A, A+, B, B+ and B2 I would agree with you as the micro USB power socket on those is protected by a poly-fuse.  However on the Pi Zero the micro USB power socket is not protected so it is easier to power it with a hub to save on cabling.

> **enricobe said:**
> I've read that the Raspberry Pi has a Full-size HDMI so, if this info is right, I think that I won't need a microHDMI->HDMI cable.

All RPI models apart from the Zero has a full sized HDMI socket.  The Pi Zero has a mini HDMI, not to be confused with a micro HDMI.

---

### Post by enricobe on 2016-01-10
> **speedwell68 said:**
> Media Centres.  Apart from the Pi Zero which is currently an Emulation Station, although that is going to become a robot of some kind as I have found a better way of playing retro games.

I have a RPI Model B in the 3 bedrooms of my house and in my lounge room I have a Model B2, all running Kodi 15.2 on Openelec 6.0.  The one in my lounge has an Ambilight Clone which is very cool.  I have also made a media server so they all have a synchronised media library.  Very simply I have got an old Acer Revo R3600 on which I have installed Ubuntu Server.  I then hooked up 4 large external HDDs, 2 for movies and 2 for TV shows, music is stored on the Revo's internal HDD.  I then upped the RAM to 4GB, using RAM I salvaged from scrap laptops.  I the setup NFS shares to the drives and music folder and used MySQL to tie it all together.  It all works very well.
I've understand half of what you've done with your rasPis :lolflag:
It looks amazing and I would like to do something like that but I start from Zero (my knowledge, not the Raspberry :D). It's a new world for me and I'm more interested every day in what can be done with these little SBCs

---

### Post by speedwell68 on 2016-01-12
> **enricobe said:**
> I've understand half of what you've done with your rasPis :lolflag:
It looks amazing and I would like to do something like that but I start from Zero (my knowledge, not the Raspberry :D). It's a new world for me and I'm more interested every day in what can be done with these little SBCs

TBH it is easy.  I have only followed 'how to' pages online.

---

