---
title: "Nvidia GTX 460"
date: 2010-07-12
forum: The Cafe
---

### Post by LowSky on 2010-07-12
Nvidia just released the GTX 460 graphics card... 

Finally a $200 option of Nvidia's newest design.

Anyone else looking at picking one (or maybe two) up, I placed my order this morning. 

Unfortunately it doesn't look like the card is supported for Linux yet... but Nvidia is usually quick to fix that. I guess I'll be using Windows 7 a bit more until it is. I usually don't buy new hardware that is days old (and lacks Linux support) but I really needed an upgrade to get ready for Starcraft 2, LOL.

---

### Post by 3rdalbum on 2010-07-12
I already have a space heater, and that $200 graphics card doesn't look so cheap when you'd have to upgrade your power supply too. I'd also wonder how it performs against a similar ATI card, even on Linux (note: Phoronix guys, PLEASE benchmark ATI versus Nvidia at price points on Linux!).

---

### Post by chiliman on 2010-07-12
i came across this
[http://forum.donanimhaber.com/m_41096432/tm.htm](http://forum.donanimhaber.com/m_41096432/tm.htm)
 
seems nice, for me already running a gtx260 core 216 its about a 20% boots in performance if those specs are correct.  Its probably not worth it for me to get. but if your running something older and already have a ~500W powersupply, that would be a freaking sweet upgrade for the price.

---

### Post by LowSky on 2010-07-12
> **3rdalbum said:**
> (note: Phoronix guys, PLEASE benchmark ATI versus Nvidia at price points on Linux!).

A bunch of other sites have already reviewed, and engadget was nice to link them all
[http://www.engadget.com/2010/07/12/nvidia-geforce-gtx-460-becomes-everyones-favorite-midrange-grap/2#c29225906](http://www.engadget.com/2010/07/12/nvidia-geforce-gtx-460-becomes-everyones-favorite-midrange-grap/2#c29225906)

From the looks of it this card is going to replace the GTX 465.

---

### Post by chiliman on 2010-07-12
> **LowSky said:**
> [http://www.engadget.com/2010/07/12/nvidia-geforce-gtx-460-becomes-everyones-favorite-midrange-grap/2#c29225906](http://www.engadget.com/2010/07/12/nvidia-geforce-gtx-460-becomes-everyones-favorite-midrange-grap/2#c29225906)


Ahh very nice, what i came across is probably outdated anyways.  The more i read about it the more i want the 1GB version.  I also think its fantastic that its 2 inches smaller than a gtx260, i read a lot of complaints with people with not big enough cases couldn't fit it at all or would have to move HD's around.

---

### Post by LowSky on 2010-07-16
I got mine yeasterday. It worked fine with the 195 driver that Ubuntu has in the repos. only issue is VDPAU doens't work within MythTV, I geuss I can try the newer driver on Nvidia's website

The GTX 260 runs really cool at 37'C. And the fans were not audible at all. I will say it is a bit of a long card, and it needs two 6 pin power lines. The card nearly ran into my motherboard's 24pin cable (AMD 790FX  motherboard).

---

### Post by llawwehttam on 2010-07-16
From all the benchmarks I've seen this is a great card. For once nvidia have produced a card that doesn't gobble power and seems to work well for the money.

One disappointing feature of this new card is that it doesn't seem able to make toast like other nvidia cards.

---

### Post by LowSky on 2010-07-16
> **llawwehttam said:**
> One disappointing feature of this new card is that it doesn't seem able to make toast like other nvidia cards.

It doesn't go well with jam either...

---

### Post by monovitae on 2010-07-17
> I got mine yeasterday. It worked fine with the 195 driver that Ubuntu has in the repos. only issue is VDPAU doens't work within MythTV, I geuss I can try the newer driver on Nvidia's website

I also have the 460 and am having issues with a fresh install of Lucid. Jockey doesn't suggest any drivers and I'm only seeing 185's in my repo. Do you have some PPA's added to your sources list? 

Also have you tinkered with the drivers from Nvidia's site yet? I've tried 256.35 to no avail haven given 195.35.31 a shot yet.

---

### Post by cariboo on 2010-07-17
Give the drivers in the [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") a try, make sure you read the page first.

---

### Post by monovitae on 2010-07-17
@cariboo907:

Thanks for the suggestion, I've read through the main page that you linked and I am unclear as to which packages to try and install specifically after adding the PPA. I see the following command listed for lucid.

Lucid:
sudo apt-get update && sudo apt-get install libdrm-dev/lucid libdrm2/lucid libdrm-nouveau1/lucid libdrm-radeon1/lucid libdrm-intel1/lucid

However from the looks of it, it seems to be a nouveau update? I be clear I do need the 3d functionality provided by the proprietary driver, such that I can play games via wine(steam,SC2,etc.)

If I'm misunderstanding please let me know, please do not think that I am being unappreciative, I just want to understand what is being suggested.

---

### Post by davidogg on 2010-07-24
any luck?

---

### Post by camrn86 on 2010-08-04
There is this driver: [http://www.nvidia.com/object/linux-display-amd64-256.44-driver.html]("http://www.nvidia.com/object/linux-display-amd64-256.44-driver.html") now but it looks somewhat complicated to install and configure properly [http://us.download.nvidia.com/XFree86/Linux-x86_64/256.44/README/index.html]("http://us.download.nvidia.com/XFree86/Linux-x86_64/256.44/README/index.html")

anyone have an easier method than is apparent from NVIDIAs guide?

---

### Post by cariboo on 2010-08-04
Look for nvidia-current from xorg-edgers, the latest is 256.44. The nvidia-current driver in Maverick is 256.35

---

### Post by LowSky on 2010-08-04
I'm using the 256.44 driver and it works great.

---

### Post by camrn86 on 2010-08-04
Thanks i got 256.44 running. 

One odd issue. I have two monitors setup. My second monitor has a much lower brightness than my first despite the monitor settings being equivalent. Is there a place where this setting is being controlled in xorg.conf or somewhere else?

---

### Post by mcooke1 on 2010-08-05
Installed X Updates ppa. Installed the new updates including Nvidia driver 256.44 and the low graphics issue has gone.

---

### Post by camrn86 on 2010-08-05
thanks mcooke. i just did the same. looks great now.

---

### Post by epi 1:10,000 on 2010-08-14
[GIGABYTE GV-N460OC-1GI GeForce GTX 460 (Fermi) 1GB 256-bit GDDR5 PCI Express 2.0 x16 HDCP Ready SLI Support Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814125333")  with X Updates ppa  works well. Driver 256.44  Linux-x86_64

PowerMizer has 4 power states

Performance Level       NV Clock     Memory Clock
0                                    50 MHz        135 MHz
0                                    405 MHz      324 MHz
0                                    405 MHz      1800 MHz
0                                    715 MHz      1800 MHz

with the PowerMizer States it uses less power than my old ATI ASUS EAH4850 Top card


VDPAU w/ MythTV works and the card increases a maximum of 20 watts from baseline power usage on SD video, 50 watts for 720P, and 60 watts for 1080I.

All mesurments taken from a KillaWatt meter on SD mpeg 2 PS and HD mpeg 2 TS.

---

### Post by AICollector on 2010-11-21
Hey all...

I've been meaning to assemble my own computer, and was told this was the card I'd be after...sadly, I wasn't given some info; can it work with the Nouveau?

---

### Post by Matthewthegreat on 2010-11-21
I got a 1GB 460 gtx on sale at newegg for 177.99 after rebate. It's a very good card and works fine in ubuntu.

---

### Post by Dustin2128 on 2010-11-21
The 430 is already under a hundred- but I assume you're looking for a mid-range graphics card.

---

### Post by AICollector on 2010-11-22
I'm just looking for something that'll play nice with wobbly windows and Unity, whilst letting me watch videos :P

---

### Post by Dustin2128 on 2010-11-22
> **AICollector said:**
> I'm just looking for something that'll play nice with wobbly windows and Unity, whilst letting me watch videos :P
well then you're overdoing it just a tiny bit. My geforce 4 Ti4800 worked with all compiz effects. I'd say you should probably just go with one of the low-mid 200 series cards. Or 9000. Or 8, 7, 6 or FX.

---

### Post by AICollector on 2010-11-23
Well, as I said eariler, I am just looking for something that plays nice with Nouveau as well. I'd much prefer to boot up and install Ubuntu.

Right now, if I need to reinstall Ubuntu on my current machine, I have to install 10.04, run the 'xforcevesa' command at boot options...(Nouveau does not like my card, VESA does!) and as I'd rather not buy anything which might NOT work...


Also, did I mention I'm looking for a card with HDMI output?

---

### Post by Swagman on 2010-11-23
Ironic that this topic has been bumped as I'm going to buy a GTX 470  after Chrimbo.. Maybe even push to a 480 ?

I'm assuming they work ok in Ubuntu (i686) ?

Not interested in gaming, I have a Ps3 for that mullarky.. It's for CUDA.. I crunch Rosetta.

---

### Post by LowSky on 2010-11-23
> **AICollector said:**
> Hey all...

I've been meaning to assemble my own computer, and was told this was the card I'd be after...sadly, I wasn't given some info; can it work with the Nouveau?

yes it will but why buy such a high end model if you are going to use the open source driver?

---

### Post by AICollector on 2010-11-23
I'd like to future-proof it.

Also, I tend to work on my 42" TV. (My hobby revolves around GIMP and Inkscape :P) so a fairly good card is needed

---

