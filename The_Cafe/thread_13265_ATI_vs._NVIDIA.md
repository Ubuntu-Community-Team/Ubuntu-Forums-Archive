---
title: "ATI vs. NVIDIA"
date: 2005-01-30
forum: The Cafe
---

### Post by clparker on 2005-01-30
Who has better Linux Support? The Numero Uno Deciding factor in my next video card purchase is gonna be based on who has better support / drivers for linux.

---

### Post by jensyt on 2005-01-30
As of right now, I think most people would agree that nVidia has better Linux support. ATi is coming along, though. I would still suggest nVidia, even though I was dumb enough to go with ATi. :D

---

### Post by poofyhairguy on 2005-01-30
[QUOTE=clparker]Who has better Linux Support? The Numero Uno Deciding factor in my next video card purchase is gonna be based on who has better support / drivers for linux.[/QUOTE]

Its good you asked. Nvidia, no question. ATI isn't even close.

---

### Post by rudi on 2005-01-30
could it be more easy then this?
 ```
     $ sudo apt-get install nvidia-glx
     $ sudo apt-get install nvidia-settings
     $ sudo nvidia-glx-config enable
```

---

### Post by eBopBob on 2005-01-30
Well, I have to say it's unfortunately nVidia.

Personally I don't like nVidia and would choose ATI over it anyday; however ATI does not really support Linux that well. I've heard some people getting their ATI cards to work perfectly however you then have to take into account the hassle they went through.

ATI IMO is the overall better graphics card, however nVidia works better on Linux. If only ATI would work on some good Linux drivers!

---

### Post by Perfect Storm on 2005-01-30
Nvidia, no question of that.

---

### Post by akurashy on 2005-01-30
this might be off topic but i think this post might get to a flaming wars from nvidia users and ati =/ *just saying thinking about the other people that might post saying "nvidia sucks" or "ati sucks"*

---

### Post by clparker on 2005-01-30
I was afraid something like that would happen, but i figure we are all adults here. I was expecting a response similar to what you have all said here. I know as of late, ATI has been spanking Nvidia in most benchmarks in the last few years, however, the newer budget Nvidia cards are giving more bang for the buck, and as for ATI software and drivers being shall i say, being disapointing. Well, that's just a fact of life no?

---

### Post by Viro on 2005-01-30
[QUOTE=clparker]I was afraid something like that would happen, but i figure we are all adults here. I was expecting a response similar to what you have all said here. I know as of late, ATI has been spanking Nvidia in most benchmarks in the last few years, however, the newer budget Nvidia cards are giving more bang for the buck, and as for ATI software and drivers being shall i say, being disapointing. Well, that's just a fact of life no?[/QUOTE]
 I think I'll be different and say ATI. Why? nVidia support is great on x86. But their support is non-existant on other platforms. I'm running a Powerbook with an nVidia GeForce fx5200. Nice chip on OS X, but has absolutely the worst drivers on Linux, thanks to the nv driver. No 3D acceleration, no dual head capability, absolutely poor.

ATI on the other hand has released their specs to the OSS community. Sure, it only goes up to the Radeon 9200, but it's a start. The OSS radeon driver is a lot better than the nv driver and even supports 3D acceleration, up till the Radeon 9200. If only ATI released the specs to their high end Radeon cards, then they would be even better.

Now nVidia needs to get their act together and either release the specs for the nVidia cards, or release Linux drivers that are cross platform.

---

### Post by jdodson on 2005-01-30
[QUOTE=Viro]I think I'll be different and say ATI. Why? nVidia support is great on x86. But their support is non-existant on other platforms.[/QUOTE]

thats not true at all.  nvidia supports more.

nvidia supports gnu/linux amd64, ia64, i386.  they also support freebsd i386.

ati?  amd64 and i386 gnu/linux only.  

neither support gnu/linux ppc.

[QUOTE=Viro]I'm running a Powerbook with an nVidia GeForce fx5200. Nice chip on OS X, but has absolutely the worst drivers on Linux, thanks to the nv driver. No 3D acceleration, no dual head capability, absolutely poor.[/QUOTE]

emmm, ok well i don't mean to be rude but why would you buy a mac laptop and put gnu/linux on it?  

[QUOTE=Viro]ATI on the other hand has released their specs to the OSS community. Sure, it only goes up to the Radeon 9200, but it's a start. The OSS radeon driver is a lot better than the nv driver and even supports 3D acceleration, up till the Radeon 9200. If only ATI released the specs to their high end Radeon cards, then they would be even better.[/QUOTE]

i have to give this one to you.  i am not sure that "wishing" will get them to open up thier high end cards, it is possible, however i would'nt bank on it.  

[QUOTE=Viro]Now nVidia needs to get their act together and either release the specs for the nVidia cards, or release Linux drivers that are cross platform.[/QUOTE]

i totally agree.

oh yeah and i think you should go nvidia.  hands down the best support in gnu/linux.

---

### Post by daniels on 2005-01-30
jdodson: For the r2xx series (up to 9250), there is 3D acceleration through DRI for whatever platform you can put a Radeon in and run Xorg on; this includes powerpc, ia64, hppa, hurd-i386 if you want ... whatever.  From a driver point of view, the open source radeon drivers wipe the floor with nv, not only because they have acceleration for some chipsets, but because it's actually readable, and when a bug crops up in them, I can say something other than 'hassle nVidia'.

Daniel, going back to hunt a bug deep down in i810, thanks to the actual open source driver

---

### Post by poofyhairguy on 2005-01-30
[QUOTE=jdodson]
emmm, ok well i don't mean to be rude but why would you buy a mac laptop and put gnu/linux on it?  [/QUOTE]


If Hoary is as good as Warty is...I might buy a Mini Mac to put Ubuntu on it. It really is better IMHO.

---

### Post by Ex-Cyber on 2005-01-31
If all you care about is game performance, go with NVidia. If you want a card whose drivers will almost certainly still be actively maintained 5 years or longer from now, go with ATI. I know some people consider the idea of a graphics card that old to be ridiculous, but I haven't upgraded mine for several years and plan to keep it for at least another year, or however long it takes for AMD64 software support to solidify a bit more and budget AMD64+PCI Express platforms to enter the market.

The following is pretty speculation-heavy, so take it with a grain of salt, but it seems to fit the facts I've seen much better than any other hypothesis I've encountered.

Many rationales have been offered for NVidia's refusal to support open-source driver development. But I recently found out that it goes beyond that - they don't just shun open source, they seem to shun third-party driver development in general. What makes me say this is that Xi Graphics (not so) subtly complains in several places on their site that they can't get any cooperation from NVidia and that GeForce cards are unsupported by Accelerated-X. My guess is that from a business standpoint (though not necessarily a marketing standpoint), NVidia simply does not consider the end users to really be their customers - they sell chips and license drivers and firmware to card manufacturers. In a couple cases they appear to have leveraged this business model by selling the same chips as two different products and letting the driver/BIOS implement the differences (GeForce vs. Quadro, NForce4 Ultra vs. NForce4 SLI). This is a pretty sweet deal for them, but it also means that the driver is effectively made to be part of the product, and anyone else making drivers would confuse that business model substantially. Ergo, they don't spend any effort helping that happen. Which is fine as far as it goes, but it doesn't get me driver support that I feel like I can really trust. But if you're going to buy a new card in 6-12 months anyway, maybe it doesn't matter to you.

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=Ex-Cyber]If all you care about is game performance, go with NVidia. If you want a card whose drivers will almost certainly still be actively maintained 5 years or longer from now, go with ATI. I know some people consider the idea of a graphics card that old to be ridiculous, but I haven't upgraded mine for several years and plan to keep it for at least another year, or however long it takes for AMD64 software support to solidify a bit more and budget AMD64+PCI Express platforms to enter the market.

The following is pretty speculation-heavy, so take it with a grain of salt, but it seems to fit the facts I've seen much better than any other hypothesis I've encountered.

Many rationales have been offered for NVidia's refusal to support open-source driver development. But I recently found out that it goes beyond that - they don't just shun open source, they seem to shun third-party driver development in general. What makes me say this is that Xi Graphics (not so) subtly complains in several places on their site that they can't get any cooperation from NVidia and that GeForce cards are unsupported by Accelerated-X. My guess is that from a business standpoint (though not necessarily a marketing standpoint), NVidia simply does not consider the end users to really be their customers - they sell chips and license drivers and firmware to card manufacturers. In a couple cases they appear to have leveraged this business model by selling the same chips as two different products and letting the driver/BIOS implement the differences (GeForce vs. Quadro, NForce4 Ultra vs. NForce4 SLI). This is a pretty sweet deal for them, but it also means that the driver is effectively made to be part of the product, and anyone else making drivers would confuse that business model substantially. Ergo, they don't spend any effort helping that happen. Which is fine as far as it goes, but it doesn't get me driver support that I feel like I can really trust. But if you're going to buy a new card in 6-12 months anyway, maybe it doesn't matter to you.[/QUOTE]


So....are you getting that new card to use now....or later when ATI releases the specs...

---

### Post by Viro on 2005-01-31
[QUOTE=jdodson]thats not true at all.  nvidia supports more.

nvidia supports gnu/linux amd64, ia64, i386.  they also support freebsd i386.

ati?  amd64 and i386 gnu/linux only.  

neither support gnu/linux ppc.
[/quote]

or SPARC, or Alpha, or anything else really.


> 
emmm, ok well i don't mean to be rude but why would you buy a mac laptop and put gnu/linux on it?  

You've obviously never used a Powerbook ;). It's the coolest laptop ever, and at 12" it's the most portable laptop I've ever owned. Cheapest laptop in the 12" catagory as well. The build quality is fantastic as well. This is the first laptop I've owned where I'm not afraid the screen hinge will die on me. The whole thing pretty much feels solid. But I'm digressing here, and I could go on and on about why run Linux on the Powerbook. 

Though I can give 3 reasons not to run Linux. Sleep/3D/Wireless. Everything else is just peachy :D.

---

### Post by jdodson on 2005-01-31
[QUOTE=Viro]`
You've obviously never used a Powerbook ;). It's the coolest laptop ever, and at 12" it's the most portable laptop I've ever owned. Cheapest laptop in the 12" catagory as well. The build quality is fantastic as well. This is the first laptop I've owned where I'm not afraid the screen hinge will die on me. The whole thing pretty much feels solid. But I'm digressing here, and I could go on and on about why run Linux on the Powerbook. 
.[/QUOTE]

your right, i have not run a powerbook before:)  i have a trashy gateway laptop, but it is just that.  i never really had good luck with laptops, i usually just stick with homebrew desktop systems.  i might try a powerbook though.

---

### Post by jdodson on 2005-01-31
[QUOTE=daniels]jdodson: For the r2xx series (up to 9250), there is 3D acceleration through DRI for whatever platform you can put a Radeon in and run Xorg on; this includes powerpc, ia64, hppa, hurd-i386 if you want ... whatever.  From a driver point of view, the open source radeon drivers wipe the floor with nv, not only because they have acceleration for some chipsets, but because it's actually readable, and when a bug crops up in them, I can say something other than 'hassle nVidia'.

Daniel, going back to hunt a bug deep down in i810, thanks to the actual open source driver[/QUOTE]

yeah these are very good selling point of ATI cards.  i have heard of people playing enemy territory using the open source driver only on an old ATI card getting 30+ FPS(which is cool).  if ATI opens the new high end cards in the way they opened the older ones and keeps up the gnu/linux proprietary driver support i might give them another shot.  it just seemed to me at the time i made my purchase(no XORG drivers at the time) that nvidia was the better choice.

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=jdodson]yeah these are very good selling point of ATI cards.  i have heard of people playing enemy territory using the open source driver only on an old ATI card getting 30+ FPS(which is cool).  if ATI opens the new high end cards in the way they opened the older ones and keeps up the gnu/linux proprietary driver support i might give them another shot.  it just seemed to me at the time i made my purchase(no XORG drivers at the time) that nvidia was the better choice.[/QUOTE]


Still is the better choice. ATI drivers sucks (even the new ones) for any card that is not old enough to have open drivers (aka a card new enough to play modern games).

---

### Post by zenwhen on 2005-01-31
[QUOTE=poofyhairguy]Still is the better choice. ATI drivers sucks (even the new ones) for any card that is not old enough to have open drivers (aka a card new enough to play modern games).[/QUOTE]


Agreed. ATI's drivers are an insult to Linux users and anyone who uses Linux on a regular basis should vote with their money and not support their sick  disregard for the open source software commmunity.

Nvidia on the other hand provides drivers that are as good as a binary driver is going to get.

---

### Post by Viro on 2005-01-31
[QUOTE=zenwhen]Agreed. ATI's drivers are an insult to Linux users and anyone who uses Linux on a regular basis should vote with their money and not support their sick  disregard for the open source software commmunity.

Nvidia on the other hand provides drivers that are as good as a binary driver is going to get.[/QUOTE]
 Ah ... a conundrum :). Who to support? Non x86 users will be supporting ATI while x86 users will be rooting for nVidia.

---

### Post by zenwhen on 2005-01-31
[QUOTE=Viro]Ah ... a conundrum :). Who to support? Non x86 users will be supporting ATI while x86 users will be rooting for nVidia.[/QUOTE]

What on Earth are you talking about? What does Nvidia not support?

---

### Post by Ex-Cyber on 2005-01-31
> So....are you getting that new card to use now....or later when ATI releases the specs...
As I said, I am waiting for AMD64+PCI Express hardware to go down in price a good bit, so I expect to be waiting at least a year. Since I don't want to spend a lot of money, I will likely buy whatever the market equivalent is of the Radeon 9200's position today (i.e. a cost-reduced version of the last-generation architecture), which should be supported by free drivers by that time.

> What on Earth are you talking about? What does Nvidia not support?
For starters, PowerPC, as well as any OS other than Linux, Windows, and FreeBSD. The point is not that ATI's drivers do support these systems, but that they open up the possibility of them being supported without having to convince ATI that it is necessary to commit resources to a particular platform. And as daniels said, even on x86 or AMD64, if you find a bug in NVidia's driver you have no option but to complain and wait for NVidia to fix it. With free drivers any interested party can work on a bugfix, put up a bounty for someone else to work on the bugfix, etc.

---

### Post by jdodson on 2005-01-31
[QUOTE=zenwhen]What on Earth are you talking about? What does Nvidia not support?[/QUOTE]

gnu/linux pcc, sparc, alpha, mips, etc.

i think gnu/linux dec is also not supported :-D

---

### Post by Viro on 2005-02-01
[QUOTE=jdodson]gnu/linux pcc, sparc, alpha, mips, etc.

i think gnu/linux dec is also not supported :-D[/QUOTE]
 Yeap :). And it's not just limited to GNU/Linux. The ATI(up to Radeon 9200) drivers will work anywhere XFree or xorg will run. That includes Solaris, all the *BSDs, pretty much every UNIX out there.

---

### Post by ember on 2005-02-01
Coming back to the origin of this discussion, I think it has to taken into account what you expect from your graphics card. I'm currently stuck with a Radeon 9600, which I really like expect for it refused to be run with ATI 3D-driver, so I'll always have to reboot when I want to play Warhammer. Yet it's the fastest affordable card (paid about 100 Euro) with passive cooling.
If you only want some 3D acceleration for some older games, try one of those ATI 9250 cards (as many here said before), they're quit good.
However if you like running modern games, I think an Nvidia 6600 GT Board might be an option. The offer a lot of 3D power for a moderate price (~ 200 Euro) and my experiences with Nvidia driver and Linux are far better than with ATI.

My 2 cent,
Ember

---

