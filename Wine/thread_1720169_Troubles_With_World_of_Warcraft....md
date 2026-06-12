---
title: "Troubles With World of Warcraft..."
date: 2011-04-02
forum: Wine
---

### Post by djsjbh on 2011-04-02
Hey folks,

I'm having a problem playing World of Warcraft under Wine 1.2.2.

I was playing WoW with my old system build just fine last week.  My old system setup was using an Nvidia card. Last week my old motherboard finally crapped out so I upgraded to:

Asus P8H67
Intel Sandybride i-3 2100  64-bit
Radeon HD 5750  1 gig of v-ram
RAM:  4 gig of DDR3
800 watt psu
Ubuntu 10.10 for AMD 64 (which is working great with the Intel processor)

The Ubuntu recommended video driver is installed and working.

The problem is rough game play and missing graphics. I can only see the shoulders and weapon on myself and everyone else.  There is extreme "popping" - trees and such will pop into place as I get closer to where they are supposed to be.

No rush on this folks.  I installed Windows 7 on another drive. All I have to do is plug in the sata cable to get my WoW fix.  I just got used to being the only guy on the block that plays WoW with Linux and I'd like to get it working again.

Thank you for your help...

---

### Post by cwwilson721 on 2011-04-03
Use wine 1.3

And run with 'opengl' switch.

Search this forum. It'll tell you what you missed.

Whenever I do a 'new' install of WoW, I always follow the guide. I've forgotten minor things myself.

(Plus...Good luck with the AMD/Ati cards...Driver quality has been suffering lately. It's a shame, because they do make good hardware, but their drivers...Installing correctly is a MAJOR pain...And if you have and older card, forget it. They don't support like Nvidia does. AMD/Ati is a crap shoot right now)

Let us know how things go

---

### Post by IHeequ5i on 2011-04-04
+1 for using -opengl

---

### Post by khelben1979 on 2011-04-04
A cheap nVidia card should solve your issues. Would be the simplest solution, otherwise you could always wait for Ubuntu 11.04 to see if that works better for you.

---

### Post by cwwilson721 on 2011-04-04
Ubuntu isn't the issue. Nor is wine. Both of them run WoW perfectly fine, and in some cases (like mine), Ubuntu 10.10 and wine runs WoW with higher FPS than Windows.

It's Ati/AMD drivers (or lack of them). Ati/AMD has fallen off the wagon on getting working/good/usable drivers for Linux, and drops support all the time for 'older' Ati cards/chips. Nvidia, on the other hand, keeps support going in it's proprietary drivers for Linux, and Ubuntu packages them up pretty quickly, too. Ati/AMD catches up, eventually, but until then...

Plus, if you add in that WoW graphics have gotten more...intense... since the 4.0 (Cata) patch, and it's wreaking havoc in the wine/WoW area (Don't even try to run WoW if you have a Intel chip for graphics. It can't do it well in Linux anymore). And then add in Ati/AMD driver issues for Linux, and...

Well, you see where this is going.

However, many people have WoW/wine running fine with Ati/AMD cards/chips, so maybe Google for a solution.

---

### Post by khelben1979 on 2011-04-05
Are you using the latest version of [AMD Catalyst]("http://en.wikipedia.org/wiki/AMD_Catalyst")? There's a high risk that what is provided by Ubuntu 10.10 is not the latest version.

---

### Post by cwwilson721 on 2011-04-05
An addition to my previous post:

khelben1979 posted in another post that the issue might be the open source AMD/Ati drivers that are with Ubuntu 10.10, and are due to be upgraded in 11.04. 

This is why Ati/AMD kinda stinks, IMO. That they drop support for a ton of still usable cards, and the open source community HAS to pick up the slack. AMD's decision, which I understand, kinda, is the older cards aren't viable for where they are going now. So, why spend the money to support them?

Unfortunately, it puts endusers in a bind. We need the best possible drivers for our cards, but the people who REALLY know the cards aren't making drivers for them anymore. So the open source community has to do it. And since they aren't the manufacturers, it will take awhile to get their drivers up to speed. What they have managed to do so far is absolutely amazing, but in the realm of 3D drivers, it is a struggle, to say the least.

Thus, AMD users can, and ARE, being left behind in many instances. That is a shame, because AMD/Ati have some older cards that are VERY capable, but aren't being used to their full potential. Nvidia, on the other hand, shows respect for their user base, and continues to upgrade drivers for older cards/chipsets, plus the driver install is painless.

AMD can learn alot from Nvidia.

Now, if Intel ever gets Sandy Bridge to actually work...

---

