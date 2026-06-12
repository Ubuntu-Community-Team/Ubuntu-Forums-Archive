---
title: "ATI Video Cards... a few questions"
date: 2011-06-15
forum: The Cafe
---

### Post by BrokenKingpin on 2011-06-15
I am looking to get a new video card for my media server and have a few questions about ATI cards. I have exclusively been using Nvidia video cards for the last decade, mainly because they played nicer with Linux, but lately I have been hearing that ATI cards work just fine on Linux. So I would like to have a few things answered before deciding between ATI and NVidia...

1) Are the ATI open source drivers on par with the proprietary drivers? Keep in mind this is for media server (video playback), not gaming. Not having to install the proprietary driver would be a bonus.

2) Are the open source ATI drivers included with Ubuntu out of the box (so I wouldn't have to do anything to get the card working after install)?

3) Would ATI cards be preferable over Nvidia cards for video decoding/playback on Linux? Do ATI cards offer any features over Nvidia for handling video decoding, etc.?

4) Assuming an ATI card would be a good route to go for a media server, what would be a good mid-range card to get (there are just so many models I don't even know where to start)?

Thanks for any info you guys could give me on the subject.

---

### Post by 3Miro on 2011-06-15
1. No, but it is close. Unless you are doing gaming, the FOSS driver should be good enough.

2. Yes.

3. Currently Nvidia + Nvidia prop drivers are better than ATI + any ATI driver. ATI FOSS drivers are improving very fast so this can change in the future.

4. I have good experience with 4xxx models, 4250 (integrated) in particular. All 4xxx should be good and it is more a matter of cash than anything else. 5xxx should also be good. The latest 6xxx may be not worth the money for just video purposes.

---

### Post by wolfen69 on 2011-06-15
Every nvidia card I've used in linux has worked well.

---

### Post by coffeecat on 2011-06-15
I have a Radeon HD4350 in one of my desktop machines. I can get good compiz with the open source driver which may not be relevant to a media server. More important is that it will play HD video with the open source driver on my 24" 1920x1200 resolution monitor (obviously in 1920x1080 with black bands) without lagging. When I say it will play HD video, I've only been ale to try trailers as I don't have any longer HD videos, but I don't see why not.

Two advantages of this card is that it is now at the inexpensive end of the price range and mine is passively cooled = silent. Which must be good for a media server.

---

### Post by el_koraco on 2011-06-15
I've never had problems watching videos on my HD4200 with the open source drivers. With the proprietary ones, it's a hit and miss situation. Ubuntu 11.04 is even shipping with the Galium driver enabled by default, which improves performance, otherwise one can add the x-swat or x-edgers ppa.

The proprietary drivers are much better at controlling fans, so take that into account when deciding, plus add to that the fact that noone is sure which ATI card works with which kind of driver setup.

---

### Post by gufide on 2011-06-15
I only got problem with my ati card, while all my nvidia worked out of the box

---

### Post by handy on 2011-06-16
> **BrokenKingpin said:**
> I am looking to get a new video card for my media server and have a few questions about ATI cards. I have exclusively been using Nvidia video cards for the last decade, mainly because they played nicer with Linux, but lately I have been hearing that ATI cards work just fine on Linux. So I would like to have a few things answered before deciding between ATI and NVidia...

1) Are the ATI open source drivers on par with the proprietary drivers? Keep in mind this is for media server (video playback), not gaming. Not having to install the proprietary driver would be a bonus. 

They are not as good for 3D, but are at least as good or better in every other way. Which is really nice. :) Most especially nice as they are so easy to maintain when compared to any other driver.

> **BrokenKingpin said:**
> 
2) Are the open source ATI drivers included with Ubuntu out of the box (so I wouldn't have to do anything to get the card working after install)? 

Yes, Ubuntu in 11.04 is using the Gallium stack which is great, as it is the leader of the open-source driver stack pack.

> **BrokenKingpin said:**
> 
3) Would ATI cards be preferable over Nvidia cards for video decoding/playback on Linux? Do ATI cards offer any features over Nvidia for handling video decoding, etc.? 

I think that there may be certain high resolutions that people use to play on TVs that may not be supported yet, though work is ongoing, so what isn't yet, will soon be, in that regard. 

I play my videos on 1920x1200 from a NAS box over the LAN with no problems whatsoever. Which is also very nice.

> **BrokenKingpin said:**
> 
4) Assuming an ATI card would be a good route to go for a media server, what would be a good mid-range card to get (there are just so many models I don't even know where to start)? 

I'm using an HD 2600 Pro /256MB RAM, GPU & everything works great re. videos. If you moved into the 4*** range you really should be able to get a very powerful card as far as your purposes are concerned, for a great price, & it will be really well supported by the open-source driver stack.

> **BrokenKingpin said:**
> 
Thanks for any info you guys could give me on the subject.

I've been using the -git kernel & driver stack for most of the last 21 months. You do get better performance there & over that period there have only been a couple of hiccoughs. If you do decide to go with the AMD/ATi GPU I have a simple how-to for upgrading the kernel & the driver stack in the first post of this thread under the title of Ubuntu Stuff:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

If you are using a notebook, you will get better power management from the Catalyst driver. That stuff is still being developed for the open-source stack at this stage. It works for some GPUs better than others at this stage - open-source wise.

---

### Post by Dustin2128 on 2011-06-16
I'd either go with AMD (ATi) or Intel (integrated) for a media server. Honestly, with open drivers, it's pretty much the same on the lower end, but AMD owns the high end open stuff. Not sure about *full *HD, but my old celeron laptop with an integrated intel video thingy could handle 720p.

---

### Post by ssam on 2011-06-16
my radeon HD 3650 plays 1080 fine on 1920x1200 display. with compiz. that is with out any tweaking, or installing extra drivers.

phoronic has lots of benchmarks, but mostly for 3D
the opensource drivers are still not as fast as the closed ones
[http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011&num=1)
but they are still improving, and can be tweaked for a bit of a boost
[http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1)

---

### Post by alphacrucis2 on 2011-06-16
One problem I had with the FOSS driver is that it didn't properly handle dual monitors. I had to use the Catalyst driver for that.

---

### Post by BrokenKingpin on 2011-06-16
I just find this card while looking online:
[http://www.canadacomputers.com/product_info.php?cPath=43_557_559&item_id=038482](http://www.canadacomputers.com/product_info.php?cPath=43_557_559&item_id=038482)

It is a nVidia GeForce GT 520 (which has no fan). Does this seem like a good card for a media center? Would this card be enough for high quality HD video (the media center PC is plugged into my LCD TV). I know this is a bit off topic, being that it isn't an ATI question lol).

---

### Post by beew on 2011-06-16
> **ssam said:**
> my radeon HD 3650 plays 1080 fine on 1920x1200 display. with compiz. that is with out any tweaking, or installing extra drivers.

phoronic has lots of benchmarks, but mostly for 3D
the opensource drivers are still not as fast as the closed ones
[http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_mesa_mai2011&num=1)
but they are still improving, and can be tweaked for a bit of a boost
[http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600g_june10&num=1)

Is it because you have enough cpu power (so the graphic card is pretty irrelevant) or is it because AMD/ATI does hardware decoding in Linux?

How does VAPPI compare to VDPAU?

These are not rhetorical questions, I really want to know.

---

### Post by screaminj3sus on 2011-06-16
> **BrokenKingpin said:**
> I am looking to get a new video card for my media server and have a few questions about ATI cards. I have exclusively been using Nvidia video cards for the last decade, mainly because they played nicer with Linux, but lately I have been hearing that ATI cards work just fine on Linux. So I would like to have a few things answered before deciding between ATI and NVidia...

1) Are the ATI open source drivers on par with the proprietary drivers? Keep in mind this is for media server (video playback), not gaming. Not having to install the proprietary driver would be a bonus.

2) Are the open source ATI drivers included with Ubuntu out of the box (so I wouldn't have to do anything to get the card working after install)?

3) Would ATI cards be preferable over Nvidia cards for video decoding/playback on Linux? Do ATI cards offer any features over Nvidia for handling video decoding, etc.?

4) Assuming an ATI card would be a good route to go for a media server, what would be a good mid-range card to get (there are just so many models I don't even know where to start)?

Thanks for any info you guys could give me on the subject.

1. No.
2. Yes.
3. No. XVBA/Vaapi does not work as well as vdpau or intel/vaapi right now. Videos play fine with the open ati drivers but you will get no hardware accleration, with catalyst you *may* get working hardware acceleration but I've found it a bit hit or miss depending on the card. With recent ati cards (UVD2) xvba/vaapi *should* work after installing libva and xvba-video.
4. 5770/6670 are pretty nice mid-range ati cards

Ati's open drivers are alright/improving rapidly, and amd has been pretty open source friendly lately, but in my experience nvidia/intel are a better linux experience driver-wise right now.

Catalyst has gotten a lot better lately (finally no more video tearing!) but I am not really sure how well video acceleration works. My ati machine has a uvd1 card which is unsupported by xvba/vaapi right now. Its supposed to work with newer cards but I am not sure how well. If video acceleration is a priority for you nvidia may be the route to go as vdpau is the most mature video acceleration api in linux.

---

### Post by BrokenKingpin on 2011-06-24
I ended up getting the nVidia GeForce GT 520 with no fan. It is working great under Xubuntu 11.04 with the proprietary Nvidia drivers.

---

### Post by mips on 2011-06-24
> **BrokenKingpin said:**
> I ended up getting the nVidia GeForce GT 520 with no fan. It is working great under Xubuntu 11.04 with the proprietary Nvidia drivers.

Ok, now setup to use VDPAU ;)

---

### Post by BrokenKingpin on 2011-06-24
> **mips said:**
> Ok, now setup to use VDPAU ;)
What is there to setup... I am pretty sure my last NVidia chip VDPAU worked out of the box with XBMC, so why wouldn't it with this one? Either way things are playing smoother now!

---

### Post by SunnyRabbiera on 2011-06-24
Anymore ATI is becoming sort of a non issue for many but its still got a long way to go.
But within the next year I can see the open source ATI drivers becoming on par or even better then the proprietary drivers.
Currently my ATI works fine under the free drivers, I did not need catalyst

---

### Post by JonM33 on 2011-06-24
My Radeon HD 5850 ran Linux without a problem. Of course it's a higher end gaming card that chews up and spits out nearly every game on the market at 1080p so I didn't expect problems.

---

### Post by wolfen69 on 2011-06-24
> **BrokenKingpin said:**
> I ended up getting the nVidia GeForce GT 520 with no fan. It is working great under Xubuntu 11.04 with the proprietary Nvidia drivers.

I would have bet money it would work well. Most mainstream nvidia cards work great without fail.

---

