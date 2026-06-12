---
title: "PS3, More RAM, Ubuntu"
date: 2007-09-27
forum: The Cafe
---

### Post by Black Mage on 2007-09-27
Ok, in this post I have two questions. My first being

1. I going to buy a PS3 and I want to put Linux on it but I also want atleast a gig of RAM, no 512 or is it 256 split? Well anyway, is there a way to add more RAM to the PS3 for Ubuntu?

2. If I install Ubuntu 7.04 on my PS3, will it be easy to Ubuntu 8 when it comes out?  Like I want to keep all my files and apps while upgrading to 8 on my ps3 without having to back it up.

---

### Post by stmiller on 2007-09-27
The amount of ram in the PS3 is fixed (hard soldiered to the motherboard). So it's 512 (?) I think and you cannot change that. However you can make a nice large swap partition to help.

To keep all of your settings and data through upgrades, make a separate root and home partition.

/ (root partition)
/home
swap

So you can upgrade versions, upgrading the root partition and it will not touch your home partition.

---

### Post by Crashmaxx on 2007-09-27
Putting Ubuntu on a PS3 is neat, but I wouldn't buy one to run it. You can get a much better machine for desktop stuff for that kind of money.

But if you are getting one to play games and perhaps for Blu-Ray, then installing Ubuntu on it. Then go for it.

---

### Post by Black Mage on 2007-09-27
> **stmiller said:**
> The amount of ram in the PS3 is fixed (hard soldiered to the motherboard). So it's 512 (?) I think and you cannot change that. However you can make a nice large swap partition to help.

To keep all of your settings and data through upgrades, make a separate root and home partition.

/ (root partition)
/home
swap

So you can upgrade versions, upgrading the root partition and it will not touch your home partition.
Fixed in RAM? Did Sony do that to maintain control or something? Shouldn't hardware be upgradable....

Anyway, what is this swap partition you speak of?

---

### Post by Frak on 2007-09-27
The PS3 will lock if you change the RAM. Yellow Dog Linux would suit you better. In fact they were contracted by Sony to make a Linux OS for it and its 8 or 9 core PPC.

[http://www.terrasoftsolutions.com/products/ydl/](http://www.terrasoftsolutions.com/products/ydl/)

---

### Post by BigDXLT on 2007-09-27
It's a video game console, not a pc.  The idea behind consoles is that the hardware stays the same for the whole of the generation.  Nintendo toyed with adding ram (for the N64) but most games didn't support it anyway (even though it was really easy to add) because the majority of people buying consoles don't ever intend to upgrade them.  They are built in such a way that they can be mass produced as cheaply as possible as a whole.  (Your modular pc components on the other hand, are not.  Well.  Normally it's this way.  Nintendo knows how to do this.)

And a swap partition is a part of your hard drive that sort of acts like really slow ram.  It sort of holds data temporarily.

---

### Post by Black Mage on 2007-09-27
> **BigDXLT said:**
> It's a video game console, not a pc.  The idea behind consoles is that the hardware stays the same for the whole of the generation.  Nintendo toyed with adding ram (for the N64) but most games didn't support it anyway (even though it was really easy to add) because the majority of people buying consoles don't ever intend to upgrade them.  They are built in such a way that they can be mass produced as cheaply as possible as a whole.  (Your modular pc components on the other hand, are not.  Well.  Normally it's this way.  Nintendo knows how to do this.)

Just a game console? It stopped being just a game consoled when they decided to make it 8-core, 512 megs of Ram, 60 gig hard drive, gigabite ethernet connector, hdmi and avi outputs, and USB ports. Those sound more like computer specs that "just game console" specs. Infact those specs sound better than a few computers on the market right now.

---

### Post by starcraft.man on 2007-09-27
Just to add my 2 cents in. Do buy the PS3 for gaming, Blu Ray movies and media centre support. Don't buy it for Linux.

While I've heard of people installing Linux successfully on the PS3, I don't think it's worth it (cheaper machines will in all likelihood be just as good). It doesn't run Linux that well from what I heard too (the Cell works nothing like an Intel or AMD CPU).

Oh and don't exaggerate, the PS3 is still just a console/media centre. The only upgradeable thing to my knowledge is the hard drive (google for steps). PCs have nothing to sweat in competition, they'll continue to be our mainstay.

---

### Post by Billy_McBong on 2007-09-27
[COLOR="Blue"]the PS3 is great and if you like to game buy it, but don't buy it just to use Linux on it

P.S. get Resistance:Fall of Man its the best FPS i have ever played[/COLOR]

---

### Post by kopinux on 2007-09-28
my pc is dying, so instead of an upgrade, ill just get a PS3.

PS3 for gaming and movies!

Ubuntu for gimp graphics, internet, messenger, office, etc.

meets my needs! and more power efficient, durable than my pc, and can fold@home more!.

---

### Post by the_darkside_986 on 2007-09-28
Actually, the PS3 runs Linux in sorta a virtualized manner, and there is no access to the graphics card. In fact, Linux has access to about 192 MB of RAM, afaik, in the PS3. So don't expect to get too much done with resource hogs such as Gnome and image editing software like GIMP. The main reason for running Linux on the PS3 is to do programming for the Cell processor.

I would like a PS3 myself but only when it is possible to run real unsigned code on it.

---

### Post by Black Mage on 2007-09-28
The problem with PS3 and Ubuntu is Ubuntu doesn't utilize all 8 of the cores, supposedly. Which is believe because games that run on the PS3 can't run on computer which aren't powerful enough. This is a reponse for using  "time pi 1000000 >/dev/null" command on a PS3 in the thread at [http://news.softpedia.com/news/Ubuntu-7-04-on-PS3-52699.shtml](http://news.softpedia.com/news/Ubuntu-7-04-on-PS3-52699.shtml)

"There are two reasons for this: firstly, the PS3 has 8 cores on it. one core is a PPC (power pc) and the other 7 are SPEs (synergistic processing element), although only 6 are enabled. The pi program only runs on the PPC core, which is general purpose and not very fast. secondly, the playstation uses a hypervisor (i.e. an emulator) to make sure that you aren't doing anything that you shouldn't (like trying to rip a bluray disc or something)."

Besides the hard drive space, which can be overcome by using an external hard drive which can be done on a PS3, the only other major draw back is that you can't upgrade, so it seems. So if you Ubuntu had the ability to use all 8 cores, with a little tweaking, whats stopping it from working better on PS3 than a regular computer. Not to mention a mouse and keyboard can be attached to a PS3.

And then I get a computer, blu-ray player and a game console all in one. I wouldn't complain about Ubuntu not having games anymore because even if PS3 are limited, it still plays PS2 games.

---

### Post by stmiller on 2007-09-28
> **Frak said:**
> The PS3 will lock if you change the RAM. Yellow Dog Linux would suit you better. In fact they were contracted by Sony to make a Linux OS for it and its 8 or 9 core PPC.

[http://www.terrasoftsolutions.com/products/ydl/](http://www.terrasoftsolutions.com/products/ydl/)

Yellowdog is a crappy distro, IMO.

Ubuntu, Debian, Gentoo, SUSE, Fedora all have PowerPC and are much better.

[http://psubuntu.com/](http://psubuntu.com/)

---

### Post by bruce89 on 2007-09-28
> **Black Mage said:**
> 2. If I install Ubuntu 7.04 on my PS3, will it be easy to Ubuntu 8 when it comes out?  Like I want to keep all my files and apps while upgrading to 8 on my ps3 without having to back it up.

8? I assume you mean 8.04, version numbers aren't normal numbers you know.

---

### Post by Frak on 2007-09-28
> **stmiller said:**
> Yellowdog is a crappy distro, IMO.

Ubuntu, Debian, Gentoo, SUSE, Fedora all have PowerPC and are much better.

[http://psubuntu.com/](http://psubuntu.com/)
But they cannot use all 8 cores like Terrasoft YDL can. Sony gave them exclusive rights to all the parts of the console. Plus, YDL has the ability to fully virtualize more RAM plus the Graphics card up to 256MB using 4 cores of the PPC Processor.

YDL runs blazing fast on the PS3.

---

### Post by Black Mage on 2007-09-28
How many cores can Ubuntu utilize at this point? And shouldn't 2 or 3 be enough. If Ubuntu could use all 8, it would probably be godly fast, like under 10 second boot.

---

### Post by Frak on 2007-09-28
I believe unless its using some Sony driver and custom compiled for all 8 cores, it can only support only 2...

---

### Post by Black Mage on 2007-09-28
Hmmmmm, time to get hacking and kracking.

---

### Post by Frak on 2007-09-28
The driver/firmware will be reverse engineered in no time, especially when it comes to processors.

---

### Post by Black Mage on 2007-09-28
Have portable RAM through a USB is pointless because its significantly slower. But what about portable RAM through the ethernet port? How much slower is that than regular RAM?

---

### Post by Frak on 2007-09-28
> **Black Mage said:**
> Have portable RAM through a USB is pointless because its significantly slower. But what about portable RAM through the ethernet port? How much slower is that than regular RAM?
I wouldn't think that much if you can find one...

---

### Post by Black Mage on 2007-09-28
[http://www.somacon.com/p123.php](http://www.somacon.com/p123.php)

Imagine, something like this for a RAM Upgrade on the PS3 or any hardware.

---

### Post by Crashmaxx on 2007-09-28
Seriously, there is no point. Just buy a computer if you want one. No reason to make a PS3 into one. It really makes no sense.

Look at what you can get from Dell for that kind of money, with Ubuntu pre-installed:
[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

Any of those would blow a PS3 out of the water for desktop tasks.

---

### Post by starcraft.man on 2007-09-28
> **Black Mage said:**
> [http://www.somacon.com/p123.php](http://www.somacon.com/p123.php)

Imagine, something like this for a RAM Upgrade on the PS3 or any hardware.

ROFL! You've got to be kidding. You really wanna go to all that trouble? Honestly, if you want a powerhouse desktop system for Linux that works well, you can build it on the cheap today for much less effort (and I'm pretty sure following will run Linux without much trouble).

**_Parts:_**
Q6600 (dirt cheap for 4 powerful cores, highly overclockable if you try) - **299**
Any mobo supporting quad (the new p35's are nice, I'd go for the Abit IP35 PRO today, an x38 if you wait.) - **200 (Abit)**
2 GBs of DDR2-800 (can double if you like) - **80**/160
an el cheapo ATI/nVidia card (unless you aim on gaming) I found a cheap 8600 GTS 256MB Dual DVI for **150** (you can find a comparable ATI if you prefer)
Power supply anything over 600 (I'd aim for 800W or more) - **80**-100
One minor note, you need a serious heatsink for the quad so I'd invest in a Tuniq 120 - **50**

**_Omissions: _**
Drives (hard and optical): Can be gotten for cheap (DVD burner 20 bucks, 250GB HD for 80) or reused from any system you own.
Case: Any case with good fan flow will do.
Mouse and Keyboard: I'm sure you already own better than the cheap crap OEMs dish out, reuse.

Total - **859** (represents total of bold prices in Canadian, mostly from reference to NCIX and other stores)

For the price point, that's a pretty good system. Better than a lot of OEMs would give ya for it (only problem really is the graphics card IMO, but unless your a gamer it is irrelevant).

This system much more suited to regular computing like running Linux for following reasons:
1) Fully upgradeable. 
2) More RAM and no hassles.
3) Firewire, dual gigabit ethernet ports, SATA2 support and more input choices (cheap universal memory card readers if you want that are 20 bucks or less on NCIX and work via USB)
4) Runs Windows, Linux, Unix and anything else that boots under the sun with no hassle (minus OSX).

To summarize, pick the right hardware for the right task. The PS3 is a great for gaming/media centre/Blu Ray, if you want that by all means. The PC I listed is great for computing in general like running Linux. That's my thoughts on the matter.

Edit: Crash, while the Dell's are nice, my machine is better bang for the buck.  Only extra thing required for my desktop is a bit of time for assembly and installation.

---

### Post by Black Mage on 2007-09-28
> **Crashmaxx said:**
> Seriously, there is no point. Just buy a computer if you want one. No reason to make a PS3 into one. It really makes no sense.

Look at what you can get from Dell for that kind of money, with Ubuntu pre-installed:
[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

Any of those would blow a PS3 out of the water for desktop tasks.


The two ways in which the Dell laptops beat the PS3 is in hard disk space and ram. But the PS3 can function a lot better on less RAM because of the 8 cores and I would rather keep the bulk of my files on an external raid hard drive anyway. And I use to work in a dell warranty service center, dells are cheap bc there made cheap and break easily, in other words crap hardware.

And for extra RAM for the PS3, I don't actually need it, Im just imagning a way it could be upgradable. In addition, Dells don't have Blu-Ray players or some of my favorite games which are on the PS systems.

---

### Post by Frak on 2007-09-28
> **Black Mage said:**
> The two ways in which the Dell laptops beat the PS3 is in hard disk space and ram. But the PS3 can function a lot better on less RAM because of the 8 cores and I would rather keep the bulk of my files on an external raid hard drive anyway. And I use to work in a dell warranty service center, dells are cheap bc there made cheap and break easily, in other words crap hardware.

And for extra RAM for the PS3, I don't actually need it, Im just imagning a way it could be upgradable. In addition, Dells don't have Blu-Ray players or some of my favorite games which are on the PS systems.
Good mix of Gaming+Linux   ...   PS3

---

### Post by tehkain on 2007-09-29
> **Black Mage said:**
> Just a game console? It stopped being just a game consoled when they decided to make it 8-core, 512 megs of Ram, 60 gig hard drive, gigabite ethernet connector, hdmi and avi outputs, and USB ports. Those sound more like computer specs that "just game console" specs. Infact those specs sound better than a few computers on the market right now.

Welcome to the locked hardware world of the future. Companies like sony and microsoft plan to replace most computers with all in one media devices. Why? Well because MS, more so then sony,  specifically wants lock down and revenue on any application they allow you to run on it. It is also specifically easier for a vendor to maintain and retain quality by controlling what you do physically with their product. Vendor lock at its finest. Just because it is 'powerful' doesnt mean it is a PC, it is a computer just like a GBA is a computer. It is a locked hardware platform along with a locked software platform. You can make the ps3 a PC but it is still hardware locked. Kinda like an apple but with all the slots soldered shut.

---

### Post by kopinux on 2007-09-29
the truth is im tired of assembled PC hardware, it loose quite often and malfunction after a year, you have to reseat the memory, vid card etc, and the power supply is an energy hog and faulty too, bad casing architecture and overheats like an xbox360, different people different systems, different drivers different problems.. 

i want a standard system, solid, rugged, power efficient, small, good heat control like a laptop. but laptop is too expensive. besides the USB can almost do anything rather than opening the casing and placing internal devices inside like a tv tuner or dvd writer.

i think ubuntu can incorporate what yellow dog linux did like wireless and multi core support because of GPL, it just that nobody yet is working on it on ubuntu, the ubuntu for ps3 are actually for apple powerpc computers, since people who have money just get a good PC and people who bought PS3 plays games. yellow dog in the other hand has paid developers working on it.

yes! it beats the "linux do not have enough games" argument.
and yes it is the first Cell Desktop Computer. The possible contender for x86 computing, even x86 computing is having a hard time jumping to 64bit. Cell is already 64 bit. and x86 is dominated by windows, cell is dominated by linux.

---

### Post by kopinux on 2007-09-29
> **tehkain said:**
> Welcome to the locked hardware world of the future. Companies like sony and microsoft plan to replace most computers with all in one media devices. Why? Well because MS, more so then sony,  specifically wants lock down and revenue on any application they allow you to run on it. It is also specifically easier for a vendor to maintain and retain quality by controlling what you do physically with their product. Vendor lock at its finest. Just because it is 'powerful' doesnt mean it is a PC, it is a computer just like a GBA is a computer. It is a locked hardware platform along with a locked software platform. You can make the ps3 a PC but it is still hardware locked. Kinda like an apple but with all the slots soldered shut.

locked hardware of the future... lets see, mobile phone, telephone, tv sets, mouse, routers, powersupply, dvd drive, printers, camera, webcams, electric fans, microware?... an average person do not open and upgrade those, do you?
as long as we have choice there would be no problem, nobody forces anyone to buy an ipod there are a lot of cheaper alternatives out there. in the PC world, it is dominated by windows and forces you to buy windows or learn linux, but in this locked hardware of the future, there is a big and huge chance linux will take over it, its called embedded. yes! even motorolla is now using linux in its newest mobile phones. check out linuxdevices.com on how many devices that runs on linux, even robotics, im pretty excited about it.

---

### Post by Black Mage on 2007-09-29
[http://www.blachford.info/computer/Cell/Cell0_v2.html](http://www.blachford.info/computer/Cell/Cell0_v2.html)

A good read on the Playstation 3 Cell and shows how it is more powerful than a regular computer cell. And then there is 7 in one PS3. What 8 core computer can you buy under 1,500?

---

### Post by mcduck on 2007-09-29
> **Black Mage said:**
> [http://www.blachford.info/computer/Cell/Cell0_v2.html](http://www.blachford.info/computer/Cell/Cell0_v2.html)

A good read on the Playstation 3 Cell and shows how it is more powerful than a regular computer cell. And then there is 7 in one PS3. What 8 core computer can you buy under 1,500?

You have to remember that Cell is not like having a 8-core Core 2 CPU. There is only one core suitable for generic use, the rest are basically vector units and not much benefit for normal computing tasks. Instead they bring a lot power to floating point calculations used in multimedia, 3D and scientific tasks. But even having those cores around is not enough, you still need to write your programs to use them before they do anything at all. Actually most of the programs we are using now are not even able to use the 2 symmetric cores of Intel and AMD multi-core CPUs..

For most of the tasks using PS3 as computer is like having a bit old and slow single-core PPC computer with fairy little of RAM. :D

---

### Post by mysticrider92 on 2007-09-29
> **Black Mage said:**
> The two ways in which the Dell laptops beat the PS3 is in hard disk space and ram. But the PS3 can function a lot better on less RAM because of the 8 cores and I would rather keep the bulk of my files on an external raid hard drive anyway. And I use to work in a dell warranty service center, dells are cheap bc there made cheap and break easily, in other words crap hardware.

And for extra RAM for the PS3, I don't actually need it, Im just imagning a way it could be upgradable. In addition, Dells don't have Blu-Ray players or some of my favorite games which are on the PS systems.

The PS3 'Cell' processor is a very special architecture, and needs a lot of work in terms of software development. Obviously, the potential is there for some extreme performance, but it is not optimized yet, and runs like a low-end PPC G5 (or high-end G4). 

A whole new Linux kernel needs to be written, then a GCC to compile all programs for it. When that is done, the Cell theoretically has the power to blow by quad core Xeon servers in terms of raw performance. Until then, it is not that good for a desktop. 

As for RAM, the PS3 has 256mb of some of the fastest RAM available (XDR, at 3.2ghz), and 256mb of GDDR3 VRAM at 700mhz. This is not user-upgradeable in the sense that you go to Best Buy and pick up a few more sticks. As mentioned before, it is soldered directly to the motherboard (probably helping greatly with the bandwidth), so it is unlikely that even some very good soldering could add more.

---

### Post by Black Mage on 2007-09-29
So if all the cores were put to use, it would be more powerful than a regular computer? YDL alreadys has 4 cores operating, whats holding Ubuntu back besides paid developers?

And a low end G5 is about 1.8ghz, which isn't anything shabby.

**The PS3 now with an full functional operating system. Your mom will no longer be able to tell if you are studying or playing a game**
**And for those porno lovers out there, stream high definition video from the internet straight to your big screen TV with surround sound. Let the neighbors know what a big pervert you are. Coming soon, the PS3 with Ubuntu FireFox.**

---

### Post by kopinux on 2007-09-29
the best is YET to come!

the progress is fast though considering the Cell/PS3 is not yet a year old.

---

### Post by Black Mage on 2007-09-29
Question for anyone who currently has a PS3 running Linux. I am about to buy a wireless keyboard and mouse for it. To be a exact its a  Microsoft 69A-00001 OEM Silver/Black 104 Normal Keys 24 Function Keys USB RF Wireless Ergonomics Wireless Laser Desktop 6000 Mouse.

Is the wireless mouse compatabile with Ubuntu on the PS3?

---

### Post by Frak on 2007-09-29
> **Black Mage said:**
> Question for anyone who currently has a PS3 running Linux. I am about to buy a wireless keyboard and mouse for it. To be a exact its a  Microsoft 69A-00001 OEM Silver/Black 104 Normal Keys 24 Function Keys USB RF Wireless Ergonomics Wireless Laser Desktop 6000 Mouse.

Is the wireless mouse compatabile with Ubuntu on the PS3?
I've only gotten Wired Mice and Wired Keyboards working with PSUbuntu.

---

### Post by stmiller on 2007-09-30
> A whole new Linux kernel needs to be written, then a GCC to compile all programs for it. When that is done, the Cell theoretically has the power to blow by quad core Xeon servers in terms of raw performance. Until then, it is not that good for a desktop.

FYI: All parts of the Cell processor are in use by Linux, [as of earlier this year]("http://lkml.org/lkml/2007/1/31/93"). The kernel is ready right now, and you can configure it for the PS3 with a 
'make ps3_defconfig.'

The problem is, as you stated, that software has to be written specifically for the SPEs.

---

### Post by mysticrider92 on 2007-09-30
> **stmiller said:**
> FYI: All parts of the Cell processor are in use by Linux, [as of earlier this year]("http://lkml.org/lkml/2007/1/31/93"). The kernel is ready right now, and you can configure it for the PS3 with a 
'make ps3_defconfig.'

The problem is, as you stated, that software has to be written specifically for the SPEs.

Hmm, interesting.. They are making fast progress considering Sony will not release much hardware information.

Black Mage: Yes, more cores *almost* always equals more processing power. And a PPC G5 is nothing to laugh at, but the Cell is almost similar to a supercomputer in a single chip. It needs a lot of optimization to show its full potential. Also, I would think the makers of YDL has a deal with Sony including the needed information to actually write a proper kernel for the PS3, but they probably had to pay a large amount for that information.

I would suggest checking out Gentoo on the PS3 if you want the best out there. You would be compiling all software yourself, so the power would be increased that much more.

---

### Post by Frak on 2007-09-30
Because the hardware wouldn't vary, PSUbuntu would be just as fast as Gentoo.

---

### Post by treggs on 2008-05-07
> **kopinux said:**
> my pc is dying, so instead of an upgrade, ill just get a PS3.

PS3 for gaming and movies!

Ubuntu for gimp graphics, internet, messenger, office, etc.

meets my needs! and more power efficient, durable than my pc, and can fold@home more!.

Do you know you can get folding@home to work on an ATI 1800 graphics card and better and not only does it work great but it blitzes the PS3 using all cores not bad 4 a card that is not even close to being as good as the one in the xbox,  good luck with gimp you only have 200mb of ram so you wont be designing websites or high quality images without problems

---

### Post by treggs on 2008-05-07
> **Frak said:**
> Because the hardware wouldn't vary, PSUbuntu would be just as fast as Gentoo.

I don't know how the hell you work that out 2 different OS's on the same system there's no way they will run the same you shouldn't comment on stuff you don't understand

---

### Post by treggs on 2008-05-07
> **Black Mage said:**
> So if all the cores were put to use, it would be more powerful than a regular computer? YDL alreadys has 4 cores operating, whats holding Ubuntu back besides paid developers?

And a low end G5 is about 1.8ghz, which isn't anything shabby.

**The PS3 now with an full functional operating system. Your mom will no longer be able to tell if you are studying or playing a game**
**And for those porno lovers out there, stream high definition video from the internet straight to your big screen TV with surround sound. Let the neighbors know what a big pervert you are. Coming soon, the PS3 with Ubuntu FireFox.**

No in a pc the graphics card does most of the work that the SPE's do and a PC graphics card is more powerful than the whole PS3, the cell is not a new theory it was originally thought of in the 80's basically the cell is bandwidth over latency and standard pc's are latency over bandwidth which basically means that the ps3 will be good at crunching numbers but not good at switching between tasks and the pc the opisit, they realised in the 80's that it was no good for PC computing and scraped it, in reality Sony were mislead by IBM and thought they were getting a chip that will also do the graphics this would have used the SPE's properly but now it has its own graphics core alot of the benifit is waisted as will most of this extra space the blu ray offers which will be used by all the extra code needed to get the power out of the cell

---

### Post by Npl on 2008-05-07
> **treggs said:**
> No in a pc the graphics card does most of the work that the SPE's do and a PC graphics card is more powerful than the whole PS3, the cell is not a new theory it was originally thought of in the 80's basically the cell is bandwidth over latency and standard pc's are latency over bandwidth which basically means that the ps3 will be good at crunching numbers but not good at switching between tasks and the pc the opisit, they realised in the 80's that it was no good for PC computing and scraped it, in reality Sony were mislead by IBM and thought they were getting a chip that will also do the graphics this would have used the SPE's properly but now it has its own graphics core alot of the benifit is waisted as will most of this extra space the blu ray offers which will be used by all the extra code needed to get the power out of the cellYou couldnt be farther from the truth.
*) Cell is all about code/data locality. If coded explicitely coded for the Architecture it has better, and much more important, **deterministic** latency and insane amounts of bandwidth. The difference is that you dont have a cache (on the SPEs) and thus handle prefecting code explicitly - if you dont, then your latency will take a hard hit.
*) using SPEs as Rasterizer was **never** planned
*) For games, code is a small small fraction. You`ll see maybe 20MB of code (and thats a very conservatively rounded upwards) and Gigabytes of textures/geometry/sound
*) IBM and Sony already realized back in 2000 that CPUs will hit a hard frequency wall, [while other CPU Manufactures were still delusional for years]("http://www.infosatellite.com/news/2003/01/a290103nehalem.html"), and properly thought out a scalable multicore-architecture. See where we are now with 8-core cpus coming up and all major CPU-Manufactures have something Cell-like massive-core brewing.

---

### Post by Frak on 2008-05-07
> **treggs said:**
> I don't know how the hell you work that out 2 different OS's on the same system there's no way they will run the same you shouldn't comment on stuff you don't understand
:lolflag:

I love it when new users try to prove experienced pros wrong. They always make me roll on the floor gasping for breath with laughter.

Ubuntu has to be compiled, just like gentoo, for a specific architecture. If you compile gentoo for the Cell, its just like compiling Ubuntu for a Cell: All of the packages will run at the same speed (same compiler, same architecture, same system).

Now before you try to prove any of our other users that like carrying on a conversation, I suggest you leave before you are mistakenly given the troll spray.

---

### Post by done84 on 2008-12-02
So do you guys think anytime soon there will be a linux version that can use all 8 cell's ?
If so emulation for any 3D game console would be possible rigth?
plus we could play any linux Game on the ps3

---

### Post by kilosan on 2008-12-02
Possibly,

Fixstars bought YDL, so Cell hardware and software development is now in one house.

In fact the latest release of YDL, it can use the Video ram as Swap making the linux YDL faster.

):P <this is ugly

---

### Post by uncholowapo on 2008-12-02
Ok lets get something straight, the Cell B/E is does not have 8 cores, it has one PPE (PowerPC Element) and 8 SPE (Synergistic Processing Elements). The PPE is a PowerPC core with Altivec Extensions. This makes the it shown in linux as having 2 cores which is not true. An SPE is not a Processor it is just a lightning fast vector unit that does extremely well with numbers; just check out Folding@Home. 2 of those SPE's are reserved for the system itself; 1 for the XMB and the other for the Hypervisor.

Sony gave access to their hardware letting users install linux on the "OtherOS" hypervised sandbox with restricted access to the RSX nVidia video card. The reason being that they didn't want pirating on their own system and if someone wanted to, they could write their own emulator to play PS3 ISO's. This is the main reason that Linux on the PS3 is so slow. Because it has no hardware acceleration, it has to rely on a software framebuffer. One thing to note that running linux on the PS3 is like running it in a virtualized environment. If it weren't for that virtualized environment then there would be no way to put linux on the PS3 because the kernel would have to be compiled with support for much of the custom hardware that the PS3 utilizes. 

But they did allow access to the full power of the Cell B/E which is the PPE and 6 of the 8 SPE's. The rules for the 2 reservations of SPE's are still applied to the OtherOS. By default any distro that is installed only utilizes only the PPE because none of the packages were compiled to use the SPE's. Utilization of the SPE's would require major change of the original code of the program or a complete rewrite for optimization for the SPE's because they are not full processors. This has been proven difficult for many developers who want to port any program to use the Cell B/E efficiently because of the limitations of the SPE's. Remember back when the famous RSX hacks were found? Why do you think that guy didn't just research on how to write programs to use the SPE's? Because it is such a new architecture with many limitations they are not used to.

It is proven that a Cell will kill an Intel Xeon or anything else. But that is for things like in the scientific field where they are effective in clusters. Obviously the code that was used in those PS3's was optimized for that particular hardware and worked pretty well. If any distro wants to optimize effectively for the PS3 then they would need a good recompilation of the kernel and Cell optimized packages which are in short right now.

Just my 3 cents.:guitar:

---

