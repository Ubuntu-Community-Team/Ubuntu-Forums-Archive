---
title: "New graphics cards on older motherboards, worth the trouble?"
date: 2015-03-04
forum: Ubuntu, Linux and OS Chat
---

### Post by pmi2 on 2015-03-04
Not looking for technical support on a specific issue, just curious what other people think.  

I have browsed through a lot of support threads, and the video compatibility list, as well as the "Bringing Old Hardware Back to Life Thread", but its really not clear (to me) when or whether an upgrade like that makes sense, at least in the opinion of other more experienced Linux users...

---

### Post by TheFu on 2015-03-04
Depends on how slow the existing CPU is or what your performance targets are.

For me, I absolutely do not care about GPU performance and will purge unity anyways, so swapping out a AMD E350 for an Intel G3258 was worth it. The Haswell on-board GPU is more than enough for my needs.
[http://cpuboss.com/cpus/Intel-Pentium-G3258-vs-AMD-E-350](http://cpuboss.com/cpus/Intel-Pentium-G3258-vs-AMD-E-350) provides some of the reasons. The MB+CPU swap was $126 for about 6-7x faster CPU performance.

I'm really moving systems around, so an E6600 will be replaced by the E-350 which is replaced by the new G3258. 
[http://cpuboss.com/cpus/Intel-Pentium-G3258-vs-Intel-Core2-Duo-E6600](http://cpuboss.com/cpus/Intel-Pentium-G3258-vs-Intel-Core2-Duo-E6600), which will save 50% on the power bill while running about 2-3x faster. I don't know what GPU is in the E6600 - it was a $40  nvidia card 7 yrs ago.

The E-350 will become a pfsense router and replace a few cheapo home routers.

If I already had a recent CPU (3 yrs) and graphics performance seemed to be an issue (not CPU proven by performance statistics), then a newer $40 card might be useful.

I suspect that my use is not really the same as yours.

---

### Post by grahammechanical on 2015-03-04
Upgrading old hardware

1) are the necessary components still being sold? More powerful CPU? More RAM? More powerful graphic adapter? If we cannot buy the components then there is not much point in going further.

2) cost comparison. Should the cost of the upgrade components be put towards the cost of a newer machine?

3) if the present hardware is upgraded, how long before you will wish you had purchased or self built a newer machine? Will you be satisfied?

4) the best computer to buy is the one that will be on sale in 6 months time.

Regards.

---

### Post by DuckHook on 2015-03-04
Depends what you mean by "older" MOBOs and "new" GPUs. To some people, a three-year-old MOBO is old. To me, it isn't even middle-aged until 10 yrs. Same, but in reverse for the GPU. Because these are such vague and relative measures, it is more useful to look at things from a use case perspective than any rule of thumb like old vs new.

I have an "older" MOBO/CPU that nonetheless still has decent enough horsepower (dual core) to run Ubuntu, with the exception of the video card, which is clearly the choke point. Installing even an entry-level but modern video card would solve this problem, but I must decide if it's worth a $40 investment. Instead, I installed Lubuntu and the system now works like new.

The lightweight flavour was a workable solution for me because I have no objection to running LXDE, but not to someone who insists on Unity. For such a person, a new video card would make sense, since it represents a small fraction of the cost of a new system and yet is all that is necessary to revitalize the system for another few years.

So, like most things, the answer is: "it depends". In this case, it depends on just how old the components are, what native power those components had to start with, what apps are intended to be run, and what the user is happy with.

---

### Post by pmi2 on 2015-03-04
Thanks for the answers....
> **TheFu said:**
> ... I suspect that my use is not really the same as yours.No, but that is exactly the point of the post, to get opinions from other people.  Good links, thanks!

> **grahammechanical said:**
> ... 4) the best computer to buy is the one that will be on sale in 6 months time.LOL.  Yes, no doubt :D.  For the purpose of discussion, I am assuming the processor and memory are adequate, and that there is a nice empty PCIe slot.

> **DuckHook said:**
> Depends what you mean by "older" MOBOs and "new" GPUs. To some people, a three-year-old MOBO is old. Good point.  Since I had more-or-less found my answer by the time I posted this, it was really an open q, sort-of like, when does it make sense to buy something new at retail, when you are installing it in an old system.  

"older", to me today usually means something like LGA775/Core 2 Duo, and "new" means a contemporary graphics card still sold at a major online retailer.  

Reasoning is as follows, this kind of "older motherboard and processor runs operating systems in mainstream use today, like Windows 7, or Linux flavors (with no 3-d).  It plays HD video, and runs most major 2D apps quite well.  It is however much "slower" in some instances like Unity than my LGA1155 desktop with an i5 (which is also an old model now).  

So, is there still an argument for reviving the old hardware with a new graphics card? 

 Personally I would lean towards NO, if there are flavors of Linux that run the same apps in a less demanding desktop environment - I would lean toward YES if the apps themselves demand it.

---

### Post by mörgæs on 2015-03-05
> **pmi2 said:**
> So, is there still an argument for reviving the old hardware with a new graphics card? 

 Personally I would lean towards NO, if there are flavors of Linux that run the same apps in a less demanding desktop environment - I would lean toward YES if the apps themselves demand it.

Yes, that pretty much sums it up. Test first with a selection of light desktop environments and if the applications are still slow then the hardware has to be upgraded. Used gear is so cheap than there is no reason not to consider it.

---

### Post by buzzingrobot on 2015-03-05
If you do decide to look at new video cards, make sure it has power requirements that can be met by the power supply in the older system, and that the power supply has all the cabling and connections the card needs. 

There are, though, some low-power video cards that draw their power directly from the slot there in.  They do not require a feed from the power supply.  These may also not need cooling fans and, so, can be rather quiet. 

For myself, if I had an old machine with very low RAM -- 1-2 gigs, I'd first bump up the RAM to 4, maybe 8, gigs.  Then, if video performance was inadequate, I'd look for a cheaper model of the aforementioned low-power cards. 

Caveats:  If the machine has Intel Haswell video, I'd stay with that.  If I wanted to play contemporary games, I'd buy an entire new system.;)

---

### Post by mastablasta on 2015-03-05
@pmi2 - I just did this. full, maximum and final upgrade.

I have this Frankenstein PC where special board with AGP and PCIe exists and with DDR as well as DDR2 ram. I had old ATI radeon 9600 256MB AGP card and DDR ram (1,25 GB) and this was the cheapest solution at the time. since I only needed new board and E3300 Celeron. 

anyway I am getting crashes, so I decided to do an upgrade. If it all work well after upgrade, then good if not then I can use some of these components on an older PC. and replace the motherboard and CPU onthis one.

anyway the upgrade:
new hard disk
new AMD R5 230 2GB GPU
new 2 GB DDR2 ram (which is the max the board can take - wish it could be 4 Gb though...).

anyway this should make it a more pleasant experience (hopefully) with some light games. If not I can use the ram on a much older single core PC that has only 1 Gb stick inside. while the GPU can be used on any newer PC, motherboard. it's nothing special, but it is descent form what I read. and low profile with lower power consumption. 

anyway this will be final upgrade. when the PC is not working again it will be a full replacement using the parts I can and that are relatively new (disks, GPU, PSU, case fans...)

---

### Post by pmi2 on 2015-03-05
@buzzingrobot: Good point about power requirements.  I am somewhat limited there, but not too bad... (400~450W).  The power supplies I have access to have some loose PCI-E labeled connectors.

I don't think RAM is really an issue, it is relatively cheap for older motherboards.  One Gb of RAM is about the price of a Latte at Starbucks (!)  

@mastablasta - yeah, all of my personal machines are and have been 'Frankensteins", but graphics tends to be the weak point of used/old systems.  (I have talked myself into building one for a couple old friends, so I have to be more careful than usual about what I do, LOL).

I am unsure how much the graphic requirements are affected by the more contemporary desktops with lots of eye candy, like Unity, Gnome, or whatever.  

If buying a new(or used) graphics card for an older system, it should probably support the latest Unity or Gnome desktops.

IMO if NOT upgrading the graphics, an older system should be able to run a current release of one of the "light" desktop environments.  Ideally a current LTS release.

A better question might be what kind of graphics card will actually do any good - meaning, off-load the processor?

---

### Post by buzzingrobot on 2015-03-05
> **pmi2 said:**
> 
I am unsure how much the graphic requirements are affected by the more contemporary desktops with lots of eye candy, like Unity, Gnome, or whatever.  


Best approach is likely to be booting and running different interfaces in live mode and checking things out. 

I have a laptop with Intel 3000 video and a Radeon card, and a desktop with Intel Haswell video and a Nvidia 750ti card. Unity and Gnome run nicely on both Intels. KDE runs nicely on on the Haswell, as well as the older Intel 3000 after I tone down some of its flashy shiny bits (aka kill most visual effects). (Current releases of Gnome, KDE and Unity are well polished.) Subjectively, the Nvidia and the Radeon seem to deliver marginally better performance in things like full-screen video clips. Since I don't play games, and everything I do is equivalent to light office work and web browsing, I tend to use Intel.

---

### Post by pmi2 on 2015-03-05
I don't have access to any systems with Intel 4th gen/Haswell architecture, at least not to play with.  I do have a desktop with Intel 3rd Gen/Ivy Bridge motherboard and cpu (i5), w. intel HD 2500 graphics.  

This has some issues running Unity with all the goodies, but its ok.  In any case, that's beyond what I would consider "old" hardware, to me old that means something like "Sandy Bridge", earlier, or Core 2 Duo.

My guess is that a Core 2 Duo with integrated graphics may well run HD video from a compressed file under Windows or a lighter version of Linux, but may NOT do the same with the current Unity or Gnome desktop, at least not without some kind of Graphics upgrade.

---

### Post by mastablasta on 2015-03-06
> **pmi2 said:**
> 
A better question might be what kind of graphics card will actually do any good - meaning, off-load the processor?

depends what kind of load you plan to put it through. these days new APU use little power and have descent performance even in some light gaming.

GPU at home is used mostly for gaming these days. for everything else the built-ins are quite fine. intel improved their chips quite a bit.

if you don't have a built in chip then AMD R5 or similar NVidia will do some very light games and fluent video. next step in price will get you some medium gaming. another step up and you get to the "really good stuff" for games.

since I was just searching to do either an upgrade or new and I came to the fact that upgrade is cheaper even though it will have less ram and keeps the weaker CPU. anyway while searching I see you can get really nice combos with AMD A6 + board. but I would maybe go with AMD A8 APU and new board and 4GB ram. it should have low power consumption, 1 GB ram will be take by the GPU part of the APU. it would be good enough for gaming. A6 should play some light games. which means that Unity should also run well. anyway prices are not the cheapest here (in fact we have high prices of this computer stuff) but the completely box would cost about 350 EUR. maybe I could reduce it down to 300 EUR (since I chose some stuff a bit too powerful - e.g. the PSU). but upgrade would cost me 165 EUR. so kind of I save some money and will spend it on other things instead. while the PC should work well enough for what we use it (fingers crossed).

I have old Ahtlon 3200+ single core, with 4 GB ram and radeon HD 3650 512MB. it still runs windows XP and plays many games even from recent time (well as long as they support directx9). anyway I tried KDE on it as well as Unity and both run very fluently. so 500GB of the disk is free & set aside for when I have the time to move it to Kubuntu. point is the PC is good enough for what I need it now (I missed the train to upgrade it with better CPU like Phenom or X2 which was my initial plan). I won't be upgrading it anymore. next one will be a new one and I started saving money for it. but there are so many things that have much higher priority.

---

### Post by pmi2 on 2015-03-06
> **mastablasta said:**
> I have old Ahtlon 3200+ single core, with 4 GB ram and radeon HD 3650  512MB. it still runs windows XP and plays many games even from recent  time (well as long as they support directx9). anyway I tried KDE on it  as well as Unity and both run very fluently...I will take this as a vote in favor of the add-on graphics for older hardware.  I looked up that processor, and it is a rough equivalent of a later model Pentium 4.  In my (limited to one system) experience, a single-core P4 does not handle contemporary desktops well, if paired with a basic graphics card like what may have been sold with it at the time (chuckle).

---

### Post by mastablasta on 2015-03-08
i need to add a bit of a warning here - there is an issue with old motherbaords and PCIe 3.0 cards, especially AMD ones. and that is that old motherboards have Pcie1.1 while these new AMD cards do not support that. learned it the hard way - it didn't work, so i need to now return it. the thing is that AMD "rewired" their cards to use less power but in doing so they are only compatible with PCie 2.0 and not the lower ones. some nvidia ones are sitll compatible with Pcie 1.1 though. they do draw more power.
all hope for older motherboards is not lost though. as in some motherboards BIOS upgrade can solve the issue. but not in my case. so i am dissapointed, upset etc. and in search for an nvidia GT 650 (or lower) or AMD Radeon HD 4xxx series or lower. so far nothing interesting. if anyone knows the place or has a used one.

one thing to add here the computer does boot faster with more ram and new disk. the experience is A LOT better. my wife is very pleased now as browsing through her pictures and files is faster, web browsing is faster... at leats it all feels faster. but unfortunatelly some games still crash, so the kid is not that pelased and is wathing with those big sad brown eyes telling me how we couldn't upgrade. and i haven't figgured out the cause of crashes yet. it could be the old GPU. but then again  it could be something else. enemy territory still crashed about 40-50 seconds into the game - everything freezes and after some time picture dissapers. looks very much like overheating. though youtube videos and such work fine. reseting immediatelly after crash and getting into BIOS showed 48 C on the PCU. high, but shouldn't be too high. and these run on high temp anyway.

oh btw i have 1 x 1 Gb DDR (cooled) Patriot ram available and 1x 256 MB DDR ram (don't know the brand) available. and an old IDE disk 60 GB. i am thinkign of donating this stuff if i can't sell it. dd can do the 1 and 0 over data on disk right?

and one final thing - the PSU - it was oldish and ghad only one new plug for the sata disk, but luckilly i  found a converter from 4x molex connector to these new disk power plugs in my motherboard's box. so all is good now. 2 sata drives are in but i can't add any more.

---

### Post by Mike_Walsh on 2015-03-09
> **mastablasta said:**
> i need to add a bit of a warning here - there is an issue with old motherbaords and PCIe 3.0 cards, especially AMD ones. and that is that old motherboards have Pcie1.1 while these new AMD cards do not support that. learned it the hard way - it didn't work, so i need to now return it. the thing is that AMD "rewired" their cards to use less power but in doing so they are only compatible with PCie 2.0 and not the lower ones. some nvidia ones are sitll compatible with Pcie 1.1 though. they do draw more power.

My situation is very similar. I've got the same Athlon 64 3200+ (in my mind, one of the very best of the old, single-core CPUs). The motherboard on MY machine (an elderly HP/Compaq Presario desktop) is an MSI one, known by fellow Presario owners as the 'Amethyst-M'. It has a single PCIe slot, wired up to the even older 1.0a standard; I found this out when, like mastablasta, I attempted to fit an Asus GT 210 'fanless', silent card to it. It needed at LEAST the PCIe 2.0 standard; it point-blank refused to work (although I think the slot has other issues, anyway.....like faulty connections). That's what HP's 'PCDoctor' diagnostic tool told me when I was still running Win XP, early last year.

[http://www.elhvb.com/mboards/oem/hp/manual/amethystM_manual.pdf](http://www.elhvb.com/mboards/oem/hp/manual/amethystM_manual.pdf)

Quote from the above manual:-
> [COLOR=transparent][FONT=sans-serif]Slots [/FONT][/COLOR][COLOR=transparent][FONT=serif]Ü [/FONT][/COLOR]
[COLOR=transparent][FONT=sans-serif]One [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]PCI [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]Express [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]x16 [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]slot [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif](supports [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]PCI [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]Express [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]Bus [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]specification [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]v1.0a [/FONT][/COLOR][COLOR=transparent][FONT=sans-serif]compliant)[/FONT][/COLOR] 

Since the built-in, ATI 'Xpress 200' video card runs Unity very well, without any problems to speak of (despite being over 10 yrs old, AND needing to use 256 MB of my 3 GB system RAM), the PCIe slot now plays host to a USB 3.0 adapter card (which only occupies the top 1/3 of the slot, and avoids the supposedly 'faulty' pins at the 'back end')....  

It, too, works perfectly.....and allows me to use my external, USB 3.0 Seagate SATA HDD at near its full data transfer rate. So, all-in-all, I haven't bothered messing about any further with add-on video cards; I'm happy with my set-up just as it is.....it still works very nicely.


Regards,

Mike. :)

---

### Post by mastablasta on 2015-03-10
In my hunt for the GPU that works with older PCIe I came across NVidia GT 630 - they have various versions, fanless and with fan. various ram. anyway they should work with 1.1. as one company (Zotac) even states that specifically. how strong is the card? not strong, but a there are plenty interesting videos. apparently coupled with a descent CPU it can run certain modern AAA games maxed out.

another interestin gone I am pursuing is a slightly stronger GT 730. it's als supposed ot be mae or PCie 2.0


otherise I saw in US they still sell Raden HD 4xxx seres which is actually a good GPU.

---

