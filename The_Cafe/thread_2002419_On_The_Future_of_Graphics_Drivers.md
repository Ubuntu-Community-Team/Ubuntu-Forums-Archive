---
title: "On The Future of Graphics Drivers"
date: 2012-06-12
forum: The Cafe
---

### Post by BigSilly on 2012-06-12
[Interesting blog post here by the developer of Compiz.]("http://smspillaz.wordpress.com/2012/06/08/on-the-future-of-graphics-drivers/")

My feeling has always been that I want my Linux desktop to be the best experience there is without any compromise. This has typically meant in the past that I've always installed the proprietary Nvidia driver as it's simply been the best tool for the job, especially as I have some Linux games I want to see running well. But I have always had these thoughts at the back of my mind, and have wanted to use the free driver if the performance is right. I think come the next release of Ubuntu, I will be selecting the free driver, if nothing else to see how far its come on, but with a desire to see it properly compete in performance with the Nvidia driver.

What are your thoughts about this subject? Are you using the Nouveau driver, and has it been an impressive experience?

---

### Post by jockyburns on 2012-06-12
My computer had a NVidia graphics card, until the card stopped working. I'm using the onboard graphics for now with the nouveau driver. When I had the graphics card installed though, I down loaded the proprietary driver, but I'm not sure that it ever used it (running 11.04 Natty and it always showed that the proprietary driver was installed but not in use) Had a look on the forums for info on how to solve it, but couldn't be bothered going to lengthy workarounds for something that should work anyway (Is this always a major problem with releases?) 
I don't know what the future holds though as NVidia are now introducing far more advanced graphics cards. They may well work, out of the box, with Windoze, but it's small comfort if us Linux users can't take full advantage of these graphics cards. Perhaps better support from NVidia and Ubuntu developers would go a long way to helping us in the future.

---

### Post by kaldor on 2012-06-12
Feature-complete open source graphics drivers are a must. Blobs only hurt progress over time even though they currently have better 3d performance and feature completion. 

If you want a good open source driver experience, you're best off with a 4000 or 5000 series ATI card in the low to mid range. The 3d performance isn't that great compared to the proprietary blobs, but the 2d works much better than Fglrx and NVIDIA in a lot of cases. If you're not into much 3d gaming, it's probably fine. AMD has put a decent amount of effort into hardware enablement/support, so there's more stuff being completed all the time. From my experience, it works better than Fglrx and NVIDIA with GNOME Shell and Compiz/Unity. AMD's open source driver stuff started up around 2008; it's been 4 years, and it has improved in leaps and bounds. Remember that Intel was once in the same sort of situation- now they're usually considered as having the most trouble-free out-of-the-box drivers.

Nouveau is the one that lags behind the most; it has no support from NVIDIA. It also has some issues with the newer generations. 

I'd be using Nouveau if not for the fact it overheats my laptop. I'd be using the open source Radeon driver if it were good enough for games like Quake 4 or WINE stuff.

Overall, I suspect that the blobs will be required for a while yet for gaming. Aside from that, I think open source will do fine.

---

### Post by BigSilly on 2012-06-12
> **kaldor said:**
> 
Nouveau is the one that lags behind the most; it has no support from NVIDIA...

Well that shoots me down. For some reason I was led to believe that Nouveau was actually quite ahead of the ATI equivalent in spite of the lack of support from Nvidia.

---

### Post by sdowney717 on 2012-06-12
From past experience, I tend to think the Nvidia driver better than the ATI driver.

I also tend to think both ATI and Nvidia know exactly what they have inside their chips and therefore will know how best to code for what they have made, if they want to do that. I dont think they always wanted to overwhelmingly support Linux, more of a luke warm support in allocating resources.

Designing a different opensourced video driver is not perceived by them to be in their interest, although it could be. Better drivers could mean more market share. But since they are in a highly competitive marketplace, controlling the information leakage is a big issue to overcome. Sharing it all out is like loose lips to sink big ships.

---

### Post by Paqman on 2012-06-12
I think we'd all quite happily use nouveau if it was up to par. Quite apart from raw 3D performance the lack of things like CUDA and VDPAU are huge holes IMO.

---

### Post by kaldor on 2012-06-12
> **BigSilly said:**
> Well that shoots me down. For some reason I was led to believe that Nouveau was actually quite ahead of the ATI equivalent in spite of the lack of support from Nvidia.

You *do* have an older and better supported card, if the 9800 is what you're referring to. I'd be rather worried about temperature and fan speed, though.

AMD, like Intel, is official. Nouveau is reverse-engineered by people outside of NVIDIA (I think Red Hat contributes here?). This is why the support for Nouveau is weaker and lagging behind. 


> **sdowney717 said:**
> From past experience, I tend to think the Nvidia driver better than the ATI driver.

If you're referring to the blobs, this is true. It's the opposite for open source (Radeon, Nouveau).

> **sdowney717 said:**
> Designing a different opensourced video driver is not perceived by them to be in their interest, although it could be. Better drivers could mean more market share. But since they are in a highly competitive marketplace, controlling the information leakage is a big issue to overcome. Sharing it all out is like loose lips to sink big ships.

But this *is* pretty much what's happening. AMD does (extensive) legal review on their software to make sure they are not releasing anything they aren't legally able to. Sometimes, the community beats them to it (HDMI audio with 6000 series). But, AMD does put lots of effort into their open source drivers. If you haven't tried it within the last 2 years (or even 6 months) you should give it another look. The open source Radeon improvements from Ubuntu 11.04 to 12.04 is pretty huge. You should be able to get out-of-the-box 3d with the majority of AMD cards on 12.04 or even 11.10.

Basically, there's no longer any need to eliminate AMD cards from your options unless you're a gamer. This is thanks to AMD's official open source development.

---

### Post by BrokenKingpin on 2012-06-13
I would also happily use the nouveau driver for my NVidia cars, but unfortunately I get crap performance with it. I hear it is getting better, but it is just easier to enable the proprietary one for now.

Once it gets to the point where I get good compositing performance and no issues with dual screen I will use it, and would prefer to use it over the proprietary one.

Good article.

---

### Post by buzzingrobot on 2012-06-14
I **can't** use Nouveau with any 3.2/3.3 kernel.  That combination plus my card, an Nvidia 550ti, won't boot.  Not even install CD's.  For any distribution.  I need to boot with some specific kernel options to keep nouveau from loading until I can install Nvidia's driver.

I'm not a gamer and really have little need for 3D or most of the capacity of contemporary cards.  I put a premium on stability and font and image rendering quality. I have no problem using nouveau or any other free software product.  But, I see no reason to use something, free or closed, that delivers a second-rate experience. I'm not inclined to see my software choices as ethical issues.

---

### Post by BigSilly on 2012-06-18
[This is pretty good news (I hope) for those of us with Nvidia cards.]("http://www.h-online.com/open/news/item/Free-NVIDIA-graphics-driver-reaches-version-1-0-1620188.html") In other news, [Linus Torvalds takes a good and proper swipe at Nvidia]("http://www.phoronix.com/scan.php?page=news_item&px=MTEyMTc"). Erk!

---

