---
title: "Linux and Laptop Video"
date: 2011-09-17
forum: The Cafe
---

### Post by 3Miro on 2011-09-17
I am looking at buying a new laptop for Linux although not necessarily for Ubuntu. However, I am confused about some of the hardware drivers and their current state. Mainly I am concerned about the video card.

When it comes to the CPU, it seems that AMD is out of the Laptop market for the time being. Almost everything new comes with Intel CPU, so I guess I am getting Intel.

Question 1: I know Intel has generally good wireless support, but are there any Intel wireless cards that I should avoid?

Question 2: I know that optimus doesn't run well and they still haven't fixed that. Can I get Nvidia Optimus and just run on the Nvidia GPU? I know it means less battery life, but I can live with that.

Question 3: Have all Sandy Bridge issues been fixed for the newer kernel versions (say 2.6.39 or even 3.0)?

Question 4: I know that ATI Open Source driver works well for newer cards, however, if I get ATI, would I need the proprietary driver for decent battery life?

Basically I am asking for people's experience on those questions.

---

### Post by kaldor on 2011-09-17
> **3Miro said:**
> I am looking at buying a new laptop for Linux although not necessarily for Ubuntu. However, I am confused about some of the hardware drivers and their current state. Mainly I am concerned about the video card.

When it comes to the CPU, it seems that AMD is out of the Laptop market for the time being. Almost everything new comes with Intel CPU, so I guess I am getting Intel.

Question 1: I know Intel has generally good wireless support, but are there any Intel wireless cards that I should avoid?

Question 2: I know that optimus doesn't run well and they still haven't fixed that. Can I get Nvidia Optimus and just run on the Nvidia GPU? I know it means less battery life, but I can live with that.

Question 3: Have all Sandy Bridge issues been fixed for the newer kernel versions (say 2.6.39 or even 3.0)?

Question 4: I know that ATI Open Source driver works well for newer cards, however, if I get ATI, would I need the proprietary driver for decent battery life?

Basically I am asking for people's experience on those questions.


1: Unsure. I know that for me, I've had no issues. You should load a LiveUSB on a store PC before buying just to be sure. I also know that Realtek cards have quite good support.

2: I would just avoid optimus entirely.

3: No, but I know of lots of people doing fine with them. 

4: Open source AMD or Nouveau are dreadful on laptops due to heat problems. Intel drivers are almost always nice on Linux.


My advice is to research the laptop prior to buying. These days, it is mostly just the wireless to watch out for.

---

### Post by 3Miro on 2011-09-17
> **kaldor said:**
> 1: Unsure. I know that for me, I've had no issues. You should load a LiveUSB on a store PC before buying just to be sure. I also know that Realtek cards have quite good support.

2: I would just avoid optimus entirely.

3: No, but I know of lots of people doing fine with them. 

4: Open source AMD or Nouveau are dreadful on laptops due to heat problems. Intel drivers are almost always nice on Linux.


My advice is to research the laptop prior to buying. These days, it is mostly just the wireless to watch out for.

Thanks for the reply. I am not looking at a specific model, but a custom build one on-line, since I don't want it to have Windows pre-installed. Unfortunately I cannot use the obvious methods like liveUSB or review of the specific models. Thus I am looking at general information.

I had only seen Realtek wired cards. Do the wireless ones come with nice FOSS drivers?

---

### Post by edcrumly on 2011-09-17
I just got a brand new Toshiba L750D, complete with AMD A6 processor, ATI 6520G video, and everything worked out of the box, wireless too. Upgraded to ATI's propriety video driver, and feed the HDMI signal to my 32" LG flatscreen T.V. Sounds great, 1080P is great, microphone is only thing I haven't had much luck with, but I'm buying a webcam for high def skype, so I'm not worried about that anyways. Replaced 500GB slow hard drive with 64GB SSD drive , (5 screws) , and it boots in 13 seconds. Laptop was $500.00 Canadian, which was very affordable for me. Have to say, very happy with purchase!

---

### Post by drawkcab on 2011-09-18
It's hard to avoid Optimus if you want a decent Nvidia card.  I'm not sure that you want to avoid Optimus because, in the long run, support for Optimus will eventually arrive.  On the other hand the new ATI cards and drivers seem to be easy to work with according to what I've been hearing.  Intel 3000 cards are great but not for high-powered gaming and multimedia stuffs.

You might want to check to see if the bios of the systems you are looking at offer an option to switch from Optimus to full-time Nvidia discrete graphics.  i've heard that Lenovo offers a physical switch that allows you to toggle from Optimus to discrete.

---

### Post by leviathan8 on 2011-09-18
From my experience, I would strongly advise you to avoid anything with Intel GMA HD graphics card. I tried many distros on it, yet all of them had the same issue, freezing. Randomly or when changing a setting, all of the distros managed to froze up. Three major distros were Ubuntu 10.04, Fedora 15 and Debian 6. I finally gave up and put Windows back, although my heart still goes to Linux. The laptop is Dell Inspiron N5010 with the Intel i3 core processor, which has the built in graphics card. However, I still have Ubuntu on my desktop and it has been working perfectly fine from the very first day! :KS

---

### Post by 3Miro on 2011-09-18
@edcrumly: this is good news about AMD, thanks for the idea. Does anyone know of a site that sells A6 laptops with Linux or no OS (I am in USA).

@drawkcab: I don't really want to buy a laptop hoping to be able to use it in a year or so. However, if I understand you correctly, I can use Optimus in Nvidia just like any other Nvidia. I will see if I can do that with the laptop, but the idea seems very good.

@leviathan8: Sandy Bridge isn't supposed to work with Ubuntu 10.04 or Debian 6 (kernel 2.6.32), however, it should work with Fedora 15 (2.6.38 ). Thanks for the warning.

---

### Post by LowSky on 2011-09-18
You are not going to find a AMD A4, A6 or A8 laptop without windows. Heck finding any laptop without windows is kinda a chore. Not to mention you don't really save any money getting one without, ie: System76

Optimus doesn't work like a regular Nvidia card. It does on the fly switching between Intel's built in graphics and the nvidia card. Some of the newer models have a  BIOS switch and some don't.

I think we would see much more issues on the forums if the newer Intel chips didn't work.

---

### Post by 3Miro on 2011-09-18
> **LowSky said:**
> You are not going to find a AMD A4, A6 or A8 laptop without windows. Heck finding any laptop without windows is kinda a chore. Not to mention you don't really save any money getting one without, ie: System76

There is some Voodoo Economics going on behind the scenes (basically the crapware that comes with the default Windows machines pays for the license), however, System76 and AVA Direct do give great deals. If you take the base laptop, it is about the same price as a good windows machine, however, if you customize them, you can get monsters for much cheaper. Basically, getting a custom upgrades System 76 or AVA Direct is much cheaper than a windows machine with the same specs.

> 
Optimus doesn't work like a regular Nvidia card. It does on the fly switching between Intel's built in graphics and the nvidia card. Some of the newer models have a  BIOS switch and some don't.

I understand the optimums idea (get the best of both world combine power and battery life) and while it is a good idea, it needs drivers. Apparently many laptops don't have options to disable one GPU or another and I read reviews and forum posts where people ended up using Intel CPU without disabling the Nvidia one ... i.e. the worst of both worlds, weak graphics with lots of power loss.

> 
I think we would see much more issues on the forums if the newer Intel chips didn't work.

Good point. I made some searches on the forum and there have been no recent posts about Sandy Bridge. I guess they should be well enough for work (no gaming).

Given that the ATI are rare and Nvidia is not an option, I guess the Intel is the best bet for the time being. I went with an upgraded Pangolin from System76 (i7, 8GB RAM, 500GB HDD). I will post back when I get it and test the graphics.

Thanks everybody for the replies.

---

### Post by drawkcab on 2011-09-19
As long as you're not doing hardcore gaming, that should be a fine laptop.  The intel card will handle most games native to linux with ease.

---

### Post by wolfen69 on 2011-09-20
I simply make sure I get an Intel cpu and graphics, and never have any problems. My laptop sports a dual core i5, and it's blazing fast with ubuntu on it.

---

### Post by beew on 2011-09-20
> **3Miro said:**
> 

Given that the ATI are rare and Nvidia is not an option, I guess the Intel is the best bet for the time being. I went with an upgraded Pangolin from System76 (i7, 8GB RAM, 500GB HDD). I will post back when I get it and test the graphics.

Thanks everybody for the replies.

I think you do can get a system76 laptop with a good Nvidia card. I don't know what your budget is, it may be a bit pricey perhaps.

---

### Post by 3Miro on 2011-09-20
drawkcab: I do gaming, but I have the Desktop for that. I need a laptop for travel (longer battery) and work (powerful CPU).

beew: System76 does have Nvidia machines, however, those use the high end Nvidia cards and are hence used more as a desktop replacement rather than laptop. Gazelle has only about an hour of batter life for example. Weak Nvidia without optimus would have been much better, but I guess it isn't an option.

---

### Post by 3Miro on 2011-09-26
If anyone cares, I just received my System76 laptop. To my shock, I opened the screen and I saw a big Nvidia Optimus sticker. The laptop is advertised as coming with Intel HD (Sandy Bridge), the laptop works on Intel HD, the BIOS has almost no options and no mention of Nvidia. From what I can tell, there is no part of Nvidia on my laptop, but the Optimus sticker is there.

I will try to see what the deal is and write a more detailed review of the machine on the System76 forum tomorrow.

---

### Post by beew on 2011-09-26
> **3Miro said:**
> If anyone cares, I just received my System76 laptop. To my shock, I opened the screen and I saw a big Nvidia Optimus sticker. The laptop is advertised as coming with Intel HD (Sandy Bridge), the laptop works on Intel HD, the BIOS has almost no options and no mention of Nvidia. From what I can tell, there is no part of Nvidia on my laptop, but the Optimus sticker is there.

I will try to see what the deal is and write a more detailed review of the machine on the System76 forum tomorrow.

Curious. I have forgotten about this thread for a while, but I have since found some Samsung R series laptops with Nvidia that don't appear to have Optimus (it seems that in other models that do have Optimus they advertise it very prominently)

---

### Post by ELD on 2011-10-11
In the end i went for this laptop:
[https://www.saveonlaptops.co.uk/Lenovo_IdeaPad_Z570_1091047.html](https://www.saveonlaptops.co.uk/Lenovo_IdeaPad_Z570_1091047.html)

Seems like a nice all rounder, thanks all

---

### Post by 3Miro on 2011-10-13
> **ELD said:**
> In the end i went for this laptop:
[https://www.saveonlaptops.co.uk/Lenovo_IdeaPad_Z570_1091047.html](https://www.saveonlaptops.co.uk/Lenovo_IdeaPad_Z570_1091047.html)

Seems like a nice all rounder, thanks all

When you get the laptop, could you please tell us if it indeed comes with no Optimus.

---

### Post by ELD on 2011-10-13
> **3Miro said:**
> When you get the laptop, could you please tell us if it indeed comes with no Optimus.

Unfortunately it does come with optimus.

Also as its sandbridge only ubuntu 11.10+ will boot on it.

---

### Post by 3Miro on 2011-10-13
> **ELD said:**
> Unfortunately it does come with optimus.

I though so, but I was hoping to be wrong. Everything mobile below 460 or 560 is Optimus.

> 
Also as its sandbridge only ubuntu 11.10+ will boot on it.

11.04 should be fine on Sandy Bridge. I have System76 Sandy Bridge laptop and it came with 11.04 pre-installed. Then I started paying around with partitions and different distros, Ubuntu 11.04 and Kubuntu 11.04 as well as Fedora 15 and even Sabayon and Gentoo LiveCDs worked fine. Only Xubuntu 10.10 did not work.

---

### Post by ELD on 2011-10-16
Odd 11.04 doesn't boot on it at all, 11.10 does but picks up the wrong make (it thinks its an acer) and wrong wireless chipset so currently Ubuntu isn't well supported on the one i linked, do not buy it.

---

