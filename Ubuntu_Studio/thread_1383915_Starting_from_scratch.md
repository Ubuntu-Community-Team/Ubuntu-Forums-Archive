---
title: "Starting from scratch"
date: 2010-01-17
forum: Ubuntu Studio
---

### Post by lev-unr on 2010-01-17
Hey all I am thinking about getting a desktop to use with ubuntu studio. I will mainly be doing music recording editing composing djing etc. A little bit of video editing as well and tons of blender use. 

Would it be better to build my own computer from scratch and if so what would you reccomendation for specs I want it to be as smooth as possible when it comes to hardware comparability. 

Or would you go with a pre built system76 unit? I don't know which one to choose. I don't want to spend more than $1,500. 

Also it would be nice to see what you guys use. If you do music production I would love to see why equipmnt and hardware / software you are using.

Thank you!

---

### Post by theozzlives on 2010-01-17
I don't use music production, but I would say lots of RAM and lots of Hard Drive. Strong video card also if you want true MultiMedia.

---

### Post by GraysonPeddie on 2010-01-19
From Newegg.com:

[AMD Athlon II 2.6GHz AM3 CPU](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103706): $99
[GIGABYTE GA-770TA-UD3 AM3 SATA III/USB 3.0 Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128419): $94.99
[OCZ 2x2GB DDR3 Memory](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227346): $79.99
[Western Digital RE3 WD7502ABYS 750GB 32MB Cache Hard Drive](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136316): $129.99
[ATI FireGL V7700 512MB PCI Express 2.0 x16 Workstation Video Card](http://www.newegg.com/Product/Product.aspx?Item=N82E16814195061): $179.99
[ARK 4U-500-CA Black Rackmount Case](http://www.newegg.com/Product/Product.aspx?Item=N82E16811182566): $72.99
[SILVERSTONE Nightjar ST45NF 450W Fanless PSU](http://www.newegg.com/Product/Product.aspx?Item=N82E16817256047): $179.97

From AmericanMusical.com:

[Focusrite Saffire Pro 24 Firewire Audio Interface](http://www.americanmusical.com/Item--i-FOC-SAFPRO24-LIST): $299.97 (you should be able to make 3 payments with this)

It comes up to $1,136.91 before shipping.

It's a good digital audio/video station for a start.

---

### Post by lev-unr on 2010-01-19
That is exactly what I was looking for. Thank you so much for all the wonderful information! 
 
Quick question though. A lot of people on here stated that nVidia works better than ATI. As far as support etc.. does this particular card work well with ubuntu or should I stick to the tired and true nVidia. Personally on my windows machines I always preferred ATI. 
 
Thanks again! 
 
Lev

---

### Post by GraysonPeddie on 2010-01-19
I have no problem with ATI in Ubuntu 9.10.

I am using an onboard Radeon HD 3200 which is part of AMD 780G chipset in my ECS motherboard. That is for my HTPC (Home Theater PC) so I use Windows for that and my AverMedia Hybrid Volar Max H788 TV tuner is not compatible with Linux, unfortunately. :( As for my 2005-built laptop that came with ATI Radeon Mobility X200 (with a built-in graphics chipset), I used to do music production in Ubuntu Studio 8.10 before I gave it away to my mom and put back the preloaded version of Windows XP and installed Google Chrome. That graphics chip worked very well. Unfortunately, the CPU and system fan went crazily loud before my laptop shuts down during music production/playback.

> AMD's FireGL and Radeon product support is unified with their fglrx Linux driver, which is part of the Catalyst for Linux package.

Source: [http://www.phoronix.com/scan.php?page=article&item=amd_firegl_v8600&num=5](http://www.phoronix.com/scan.php?page=article&item=amd_firegl_v8600&num=5)

Update:

You might want to replace both an 80mm and 120mm fans with this:

[COOLER MASTER R4-L2R-20CG-GP 120mm Green LED Case Fan](http://www.newegg.com/Product/Product.aspx?Item=N82E16835103062)
[Nexus PWM Series SP802512H-03PWM 80mm Case Fan](http://www.newegg.com/Product/Product.aspx?Item=N82E16835610001)

Based on the reviews, they should be able to cool your workstation without making a lot of noise (based on the reviews).

You can replace a stock heatsink that came with an AMD CPU with this:

[ZALMAN CNPS10X FLEX CPU Cooler](http://www.newegg.com/Product/Product.aspx?Item=N82E16835118056)

And then add two 120mm fans (that I recommended you) if you like.

---

### Post by Quazimoto on 2011-02-04
Great idea, learn more about Linux, etc.  I built my system from scratch for the same reasons you are asking about. Also, you will be in a good place to build your own kernel!

Now, about the FireGL series from ATI/AMD

These cards are great, if you want a workstation card and are okay with the older standards it comes with... I bought a v7700 and it is damn fast. This card is very good with matching color across different monitors! I  have never had such a match in the almost 20 years of doing graphic  design I am very impressed.

There is a issue with the FireGL v77oo and probably other ATI FireGL workstation cards and I am putting info here hoping to save others the insane process I went through. AMD was not much help at all. No one seems to be using this series of cards when installing Ubuntu either, but now that prices are soooo low... well, I think others will be hitting the same wall I did. So, if you do get the card, then you will need to read these instructions or it will be very much a drag.

First, you can not install ANY Ubuntu 10.04 or 10.10 with this card as it needs the propeietory driver in the install or the monitor will not light up, operate, looks like it freezes, but it is not it is a video issue so there is no screen. It doesn't matter if you use safe mode... The same goes for most Linux installs as I tried quite a few. Even ones that did start from the disc had errors installing in my system. I will list my system below for more info if anyone is interested.

So the only way I was able to deal with the issue is really lucky, I had gotten a MB with built in ATI video. I can not say if another card like from nVidea will work in this process, I can only tell you what I did. To do what I know works, use a consumer card from ATI and not the workstation cards it will install and the video issue is not a problem with that kind of video card. So, either get a cheap card or get a main board that has built in video again, ATI worked for me. 

Once the system is up and running, Ubuntu will tell you that there is a proprietary ATI driver available. Activate that driver. Then shut down, replace the cheap card with the ATI FireGL workstation card, or if you used a MB with built-in video put in the FireGL in the Video Slot. Once you are done with that, start-up and set your preferences in the System Preferences -  ati CCC (use the administrative option). You may not see any change when you set for one desktop across the 2 monitors option, or several others, I found that you will only see your changes on restart... sometimes. Do Not Use the driver that can be downloaded at AMD website,  trying to install AMD's linux driver from the website messes up everything and you will have to start over, unless you are good at dealing with this kind of issue once the video is messed up.

I am fairly certain my set-up is not creating a unusual situation forcing me to follow the steps above... but, how can I know since I do not have any way of checking... So, here is what I made. I only spent $700 or so, and another $300 for a new big flat screen. I had some spare parts from a friends box that was damaged, so I had a couple HDD's and ram from that. 

Main Board; Gigabyte GA-MA785GM
6 GIG 800 - DDR2
ASUS VW266H Monitor
Old Hitachi V810 CRT
AMD Phenom Black ed. 3.4 GHz
ATI FireGL v7700 workstation video

Sorry about the verbose mode... too much coffee!

---

