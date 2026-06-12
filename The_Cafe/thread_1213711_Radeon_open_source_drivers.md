---
title: "Radeon open source drivers"
date: 2009-07-15
forum: The Cafe
---

### Post by Pasdar on 2009-07-15
Who here uses it and what are your experiences with it? Would it be recommendable to buy an ATI card and use these open source drivers? What are the things the drivers lack (what wont I be able to do?) Does it have TV out support for example, is it perfect with video playback (on PC and online, divx, DVD, etc), will I see the extra effects on my desktop? etc

---

### Post by Colo2 on 2009-07-15
I have had a very successful experiance with Radeon drivers, with the drivers included in ubuntu, I can use desktop effects on my ancient card.

NVIDIA drivers are just as good and well supported in ubuntu 9.04 :)

---

### Post by vinutux on 2009-07-15
better go Nvidia they people support linux more...

---

### Post by mcduck on 2009-07-15
Ati/radeon driver works great for me, better than the proprietary driver ever did (as in no video problems and the system actually wakes up again if suspended). Compiz woks fine (apart from the Blur plugin), and I haven't had any problems with 3D performance (although I don't play PC games that much so nothing I've tried is likely to task the GPU too much).

If these driver get any better than this then both Ati and Nvidia should be realy, really ashamed for making such bad Linux drivers.. :D

---

### Post by Pasdar on 2009-07-15
The thing is, I want to buy a laptop...  ATI cards are just more powerful than NVIDIA cards and on Windows a NVIDIA card will simply not be able to beat an ATI card. Other than that the cards are very cheap, especially the combination AMD CPU with ATI GPU, because they're both owned by the same company. So it basically 'hurts' to settle for something weaker for a higher price, when you know you can for example get an ATI 3650 / 4650 for the same price. Other than that you also limit yourself...

---

### Post by b3n87 on 2009-07-15
> **Pasdar said:**
> The thing is, I want to buy a laptop...  ATI cards are just more powerful than NVIDIA cards and on Windows a NVIDIA card will simply not be able to beat an ATI card. Other than that the cards are very cheap, especially the combination AMD CPU with ATI GPU, because they're both owned by the same company. So it basically 'hurts' to settle for something weaker for a higher price, when you know you can for example get an ATI 3650 / 4650 for the same price. Other than that you also limit yourself...

I disagre - ATI have failed hard recently, and their lack of support for Linux is poor. If you look at benchmarks, your find that Nvidia almost win every time.

Although the drivers for Nvidia are proprietary, they are very good, and stable. The release drivers on a regular basis and have already started support for OpenGL 3.1

---

### Post by Colo2 on 2009-07-15
b3n87 is right, Although ATI cards are very good, NVIDIA do take the lead. If someone made me choose, I would go for nvidia every time

---

### Post by b3n87 on 2009-07-15
I left ATI for Nvidia when I decided to buy myself a new laptop.

I bought a Dell XPS M1330 with a Nvidia 8400M card - fantastic bit of kit and the Nvidia drivers work fawlessly for me.

Edit:

BTW you do realise that Canonical have to get a private copy of a binary beta driver from ATI to ensure that its "compatible" with the latest release of Ubuntu - the quality of those drivers are pretty poor from what Ive heard.

---

### Post by Pasdar on 2009-07-15
> **b3n87 said:**
> I disagre - ATI have failed hard recently, and their lack of support for Linux is poor. If you look at benchmarks, your find that Nvidia almost win every time.

Although the drivers for Nvidia are proprietary, they are very good, and stable. The release drivers on a regular basis and have already started support for OpenGL 3.1

I agree that on Linux the proprietary drivers of NVIDIA are better than those of ATI, and I also agree that the proprietary drivers of ATI lack support from the company. They seem to be investing little money in their Linux drivers, and the fact that they have released all the information to the open source scene to make their own drivers proves this point... it comes across as, "here is all the info, please make the drivers, cus we don't feel like it".

HOWEVER <- a big however, ATI beats NVIDIA hands down on Windows, benchmarks can be found at: [http://www.notebookcheck.net/AMD-ATI-Mobility-Radeon-HD-4870-X2-Crossfire.14406.0.html](http://www.notebookcheck.net/AMD-ATI-Mobility-Radeon-HD-4870-X2-Crossfire.14406.0.html)

Not only do they have the fastest card period, but in each class they're also cheaper.

The choice one has to make here seems to be very simple, on the one hand you have ATI:
Positive:
1. Great videocard on Windows,
2. Cheaper than NVIDIA
3. More powerful than NVIDIA in each class, until the top.
4. They released an open source version, plus all the info needed for the open source community to make their own drivers.
5. Its much cheaper than NVIDIA, especially in combination with AMD CPU.

Negative:
1. ATI has a lack of interest in making good drivers for linux, so in the short run we will not have high quality professionally made drivers for ATI cards on Linux.

Now NVIDIA:
Positive
1. Works great on Linux with their proprietary drivers.
2. They have a team actively working on the linux drivers.

Negative:
1. They're more expensive than ATI
2. They dont care about open source and will not release anything for the open source community, other than their proprietary drivers <-- al though this doesn't necessarily dissuade me from getting a nvidia card.

---

### Post by gradinaruvasile on 2009-07-15
Nvidia. Better drivers, more stability. 
In contrast with the Ati drivers (both opensource and proprietary), where a Compiz crash tends to take down the whole X server, you can reload the window manager from compiz icon and go on without problems. I had an uptime of 2 months on my workplace desktop, compiz crashed quite a few times, but didnt take the rest of X with it.

The opensource Ati drivers do work with compiz but they are way behind proprietary drivers in features. 
Try to start 3D games on them, only a handful will work. I had lots of crashes and hard locks (i was forced to unplug the computer to stop it) with the radeon drivers on a X1600 on Jaunty. I heard the newer proprietary Ati drivers are more stable but cannot confirm this.

---

### Post by stwschool on 2009-07-15
Trust me, NVIDIA every time. Gaming on linux is a nightmare with ATI. On an NVIDIA card it's a smooth experience. Everything just works.

---

### Post by ssri on 2009-07-15
Yeah, I heard of hard X lockups from radeon drivers.  In additional, due to the lack of GLSL and shader support, do not expect great 3D from radeon drivers, especially when compared to ATI/AMD's proprietary Catalyst drivers.  Then again, the proprietary drivers have issues of their own, as seen from the myriad of complaint threads that sprout up with every monthly release.  Still, depending on your card, the radeon drivers offer great 2D performance.  Also, 3D works for the older the cards, but not as well, as I explained earlier.  Take for example GoogleEarth.  Sure, it will run, but some of the features are not available (so I heard).

I do not know if it is true or not, I read a post somewhere that claims an improved KDE 4.x experience under ATI cards than with Nvidia.  Can someone verify this?  I think it had more to do with the state of nvidia's drivers at that time.

---

### Post by b3n87 on 2009-07-15
> **Pasdar said:**
> I agree that on Linux the proprietary drivers of NVIDIA are better than those of ATI, and I also agree that the proprietary drivers of ATI lack support from the company. They seem to be investing little money in their Linux drivers, and the fact that they have released all the information to the open source scene to make their own drivers proves this point... it comes across as, "here is all the info, please make the drivers, cus we don't feel like it".

HOWEVER <- a big however, ATI beats NVIDIA hands down on Windows, benchmarks can be found at: [http://www.notebookcheck.net/AMD-ATI-Mobility-Radeon-HD-4870-X2-Crossfire.14406.0.html](http://www.notebookcheck.net/AMD-ATI-Mobility-Radeon-HD-4870-X2-Crossfire.14406.0.html)

Not only do they have the fastest card period, but in each class they're also cheaper.

The choice one has to make here seems to be very simple, on the one hand you have ATI:
Positive:
1. Great videocard on Windows,
2. Cheaper than NVIDIA
3. More powerful than NVIDIA in each class, until the top.
4. They released an open source version, plus all the info needed for the open source community to make their own drivers.
5. Its much cheaper than NVIDIA, especially in combination with AMD CPU.

Negative:
1. ATI has a lack of interest in making good drivers for linux, so in the short run we will not have high quality professionally made drivers for ATI cards on Linux.

Now NVIDIA:
Positive
1. Works great on Linux with their proprietary drivers.
2. They have a team actively working on the linux drivers.

Negative:
1. They're more expensive than ATI
2. They dont care about open source and will not release anything for the open source community, other than their proprietary drivers <-- al though this doesn't necessarily dissuade me from getting a nvidia card.

These are very fair points.

I do think though, in maybe 12 to 18 months time when the open-source driver for ATI has matured well and supports a vast amount of cards (3D acceleration, etc), it will be hard to choose a Nvidia card over ATI because of the pure fact that the driver will be open source.

Until then its Nvidia all the way for me :-D

---

### Post by frup on 2009-07-15
Well my flatmate's (room mate's) computer has a radeon 9600pro or something similar. FGLRX no longer supports this as it is legacy, so one must use the open source ATI driver. This should be a good thing, and for the most part is except:

The ATI driver has support for OpenGL 1.3 (from glxinfo)
The FGLRX has support for OpenGL 2+

This means Linux games such as savage2, games in wine that should be platinum etc. etc. don't work. Big problem for him. He likes Ubuntu now, but is going to be dual booting XP soon. He wouldn't need XP if the open source driver wasn't so far behind in OpenGL.

Conversely, my laptops inbuilt intel 945 chipset has support for OpenGL 1.4. His card is far more powerful, even if it is old.

---

### Post by 3rdalbum on 2009-07-15
> **b3n87 said:**
> I do think though, in maybe 12 to 18 months time when the open-source driver for ATI has matured well and supports a vast amount of cards (3D acceleration, etc), it will be hard to choose a Nvidia card over ATI because of the pure fact that the driver will be open source.

Except that the cards available in 12 to 18 months time will be much newer than what the drivers support; plus, the Radeonhd driver is missing some functionality compared to the proprietary driver.

AMD needs to implement VDPAU support for its cards, AND release documentation to help open-source developers to implement video acceleration in Radeonhd. Nvidia has working VDPAU on Mpeg, H.264 and VC1 for most 8000-series cards and everything newer; for AMD to catch up they really need to take advantage of the VDPAU work that's in Mplayer and libavcodec rather than continue developing its own video acceleration API at snail's pace.

---

### Post by descendent87 on 2009-07-15
What card are you thinking of getting? The opensource radeon drivers have working 3D/KMS for everything upto r5xx cards at the moment. 3D for r6xx/r7xx is coming along nicely and should be in a usable state soon hopefully (check out phoronix for news about it)

---

### Post by ThisEndlessFall on 2009-07-15
The Radeon opensource drivers are next to useless for any kind of serious 3D ala ET:QW.

---

### Post by racerraul on 2009-07-15
I have an HP Windows Laptop for work with ATI on board... Compared to my old Dell with NVIDIA the output to my 24" monitor hands down SUCKS on the newer HP laptop with ATI.

It's not the monitor since it is just as bad on th 17" it is on right now doing dual Mon duty.

All that said, if you still want an ATI because of "Windows" knock yourself out... just don't say you weren't warned and then put Linux on it.

Windows performance is IRRELEVANT if you are going to use Linux.  You can get it to work... but you might as well dual boot it so you can go back to Windows for what DOESN"T work.

---

### Post by papangul on 2009-07-15
> **racerraul said:**
> output to my 24" monitor hands down SUCKS on the newer HP laptop with ATI.
..output of what? 2D, video, game....or of everything?

---

