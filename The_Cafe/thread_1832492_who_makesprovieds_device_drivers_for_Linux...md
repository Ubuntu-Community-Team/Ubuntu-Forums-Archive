---
title: "who makes/provieds device drivers for Linux..?"
date: 2011-08-24
forum: The Cafe
---

### Post by asifnaz on 2011-08-24
when I installed windows on my PC I had to install 3 drivers manually  sound card , Ethernet and VGA card .

but when I installed Ubuntu on same PC it had all three in it .

I am very curious to know who makes/provides these drivers..?

The hardware manufacturer ?
Linux developers (if yes how ..?)
or
Linux uses 1 fits all(generic ) drivers?

Thank you

---

### Post by Old_Grey_Wolf on 2011-08-24
Consider yourself lucky that you didn't have to install any drivers. Ubuntu tries to make it easy to install them when they aren't in the default install; however, with all the hardware out there they don't always succeed.

Some hardware manufactures make drivers for Linux; however, some do not.

Linux developers do make drivers for hardware, usually for hardware where the hardware manufactures don't provide Linux drivers. The developers do it by reverse engineering the driver, writing a wrapper around the vendors drive so that it works with Linux, or trying their best to write a drive that makes the hardware work. They do the best they can, occasionally making something that works better than what the hardware manufacture can produce themselves. Canonical really isn't involved in that very much, based on my understanding.

If an individual user developed a driver for some hardware, I would consider them a Linux developer.

---

### Post by 3Miro on 2011-08-24
Windows comes with barely any drivers at all and MS relies on the hardware manufacturers to make drivers for Windows.

MacOSX comes with drivers only for the Apple hardware, which is good hardware, but overall limited selection.

Linux has two types of drivers, Open Source and Proprietary. Open Source drivers can come either form the community (like most Ethernet and Sound Cards) or from the hardware manufacturer (like Intel and recently AMD/ATI). Those drivers ship with Ubuntu by default and you don't have to do a damned thing, just plug it and it works.

The second type of Linux drivers are the proprietary ones, those cannot come installed by default for legal reasons (some community based distributions like PSLinuxOS or Mint can go around the laws, but Canonical cannot do that do that for Ubuntu). If your system is in need of a proprietary drivers, then you get a popup (or you can go System -> Admin -> Additional Drivers) and install those after you install Ubuntu. Proprietary rivers are for example Nvidia drivers and some ATI drivers as well as Broadcom wireless drivers. Proprietary drivers are usually a pain in the ***, although Nvidia overall does a good job.

IMO all manufacturers should be required to make Open Source drivers regardless if it is for Windows or Linux or OSX. We already payed for the hardware, they should give us appropriate drivers.

---

### Post by akand074 on 2011-08-24
Linux is basically a collection of drivers. GNU/Linux operating systems is basically a platform written over those collection of drivers. Linux is just a kernel. A kernel is the core of an OS, it's basically the software that interacts with the hardware. Linux has open-source drivers written right into the kernel provided by hardware manufacturers and Linux developers. You can also install proprietary drivers from manufacturers similarly like you would in Windows for those that aren't available or for those that have better proprietary drivers than open-source ones.

---

### Post by christopher.wortman on 2011-08-25
> **3Miro said:**
> 
IMO all manufacturers should be required to make Open Source drivers regardless if it is for Windows or Linux or OSX. We already payed for the hardware, they should give us appropriate drivers.

I see this argument all the time.

Look at this from NVIDIA's point of view as a point of sales reference.

They sell their chip to the likes of BFG and EVGA and have contracts with them. Both companies provide life time RMA warranties on their products from low end to high end. You pay shipping they replace the card for free. 

Look at Linux and the mess that it's in (it has cleaned up a bit) but even with power consumption on laptops. The chipset driver is Open Source... they can't get that right.

Now think about the Nvidia driver it is over 230MB in size to handle all of the floating points and some cards run with 100+ cores per processor and each processor is capable of handling bit points and floating integers in the quadrillions of flops. 

Now look at the state of Open Source Software... Nothing holds a candle to the ones used in business. We need applications that do what Photoshop and MS Office and Sony Vegas Pro can do and so on, yet everyone complains about it being a pain in the butt to code something of that stature...

You are telling me that Nvidia should break contract and risk losing billions in revenue? :lolflag: Troll harder.

---

### Post by christopher.wortman on 2011-08-25
> **christopher.wortman said:**
> I see this argument all the time.

Look at this from NVIDIA's point of view as a point of sales reference.

They sell their chip to the likes of BFG and EVGA and have contracts with them. Both companies provide life time RMA warranties on their products from low end to high end. You pay shipping they replace the card for free. 

Look at Linux and the mess that it's in (it has cleaned up a bit) but even with power consumption on laptops. The chipset driver is Open Source... they can't get that right.

Now think about the Nvidia driver it is over 230MB in size to handle all of the floating points and some cards run with 100+ cores per processor and each processor is capable of handling bit points and floating integers in the quadrillions of flops. 

Now look at the state of Open Source Software... Nothing holds a candle to the ones used in business. We need applications that do what Photoshop and MS Office and Sony Vegas Pro can do and so on, yet everyone complains about it being a pain in the butt to code something of that stature...

You are telling me that Nvidia should break contract and risk losing billions in revenue? :lolflag: Troll harder.

Not to mention that Intel and Nvidia MCP chipsets are as open source as they are gunna get and AMD released the specs of their cards and yet I still have to use the proprietary driver because the open source one sucks 4 years after the release...

---

### Post by 3rdalbum on 2011-08-25
> **christopher.wortman said:**
> 
Look at Linux and the mess that it's in (it has cleaned up a bit) but even with power consumption on laptops.

That's because there's no such thing as a power management standard. All x86 computers have totally different, possibly broken-and-worked-around-by-Windows-drivers, power management in their BIOSes. Usually, if something to do with power management or power consumption is broken on some laptops on Linux, it's because the kernel developers are trying to work around a different problem caused by a bad engineer hack in a different set of laptops.

> Troll harder.

If they're trolling, they just succeeded.

To answer the OP's question: It's usually kernel developers who contribute the drivers. Sometimes the hardware manufacturers do too, especially if it's hardware that you might find in a server.

For things like certain webcams, mass storage devices, USB input, USB audio etc, the way those device interact with the computer is fully standardised and you don't need any driver for that specific device. That's why you don't need to install a driver for each USB flash drive you use in your computer. It's also the same reason why you don't need a "mouse driver", even though Windows pretends to be installing a driver whenever you plug in a mouse :-)

---

### Post by 3Miro on 2011-08-25
> **christopher.wortman said:**
> I see this argument all the time.

Look at this from NVIDIA's point of view as a point of sales reference.

They sell their chip to the likes of BFG and EVGA and have contracts with them. Both companies provide life time RMA warranties on their products from low end to high end. You pay shipping they replace the card for free. 


What's your point? I give BFG or EVGA money and they provide a product with the support for it. Do you think Nvidia has a contract with those companies to make sure they don't release the source for the drivers? This makes no sense, those companies make money from selling hardware and making sure their products work on all distribution out-of-the box would only increase sales.

Nvidia at least has good proprietary drivers, try boradcom to see what garbage those are.

> 
Look at Linux and the mess that it's in (it has cleaned up a bit) but even with power consumption on laptops. The chipset driver is Open Source... they can't get that right.

If Nvidia provides Open Source drivers, this doesn't mean that they will not get to keep working on those. A company can make Open Source software, this doesn't mean that they have to somehow stop supporting their own products.

> 
Now think about the Nvidia driver it is over 230MB in size to handle all of the floating points and some cards run with 100+ cores per processor and each processor is capable of handling bit points and floating integers in the quadrillions of flops. 

Nvidia already has the driver, so all that they need to do is change the licensing so it can be included by default in all distributions.

> 
Now look at the state of Open Source Software... Nothing holds a candle to the ones used in business. We need applications that do what Photoshop and MS Office and Sony Vegas Pro can do and so on, yet everyone complains about it being a pain in the butt to code something of that stature...

I don't pay money to use Libre Office and hence it is hard for Libre Office to compete with MS Office. I do pay money for an Nvidia card, there is no need or whatsoever for them to be placing restrictions on me.

Newer AMD cards work great with the Open Source driver, the only issue is wine games.

> 
You are telling me that Nvidia should break contract and risk losing billions in revenue? :lolflag: Troll harder.

You have no idea what you are talking about, although I do wonder about your definition of a Troll.

---

### Post by DangerOnTheRanger on 2011-08-25
> **christopher.wortman said:**
> 
Now look at the state of Open Source Software... Nothing holds a candle to the ones used in business. We need applications that do what Photoshop and MS Office and Sony Vegas Pro can do and so on, yet everyone complains about it being a pain in the butt to code something of that stature...


Troll alert. I advise getting back on topic before this thread is locked.

---

### Post by christopher.wortman on 2011-08-25
The point I am trying to make is that there is a lot of copyrighted material in the driver probably from people other than NVidia.

This is on topic.

All I hear are excuses about "windows driver workarounds" what if the NVIDIA driver has like 50 or so workarounds that some cards have something broken in them and it is a software fix? The point is, nobody is doing anything to fix the "broken power issue" with open source software, so why open source the driver, risk licensing fees, court costs, and losing BFG and EVGA and other companies as customers to sell your chip to?

Nvidia makes the driver, companies buy the chip and driver and make a card out of it.

I am sure if the developers of Open Source Software pulled their game together and made stuff worth while that works 99% of the time, and applications worth using, other companies may see the point and open source their stuff too. If you are doing nothing but complaining about "its too hard" or statements like "there are about 1000 different issues solved by Windows drivers" my question is why even try? Either do or don't but please stop complaining about things not being open source if you are not going to try to fix the issues at hand or make awesome killer applications that are more than "good enough".

---

### Post by ninjaaron on 2011-08-25
> **3Miro said:**
> IMO all manufacturers should be required to make Open Source drivers regardless if it is for Windows or Linux or OSX. We already payed for the hardware, they should give us appropriate drivers. While I agree that *they* should give away the drivers, the idea that they should be required to is bordering on fascism.  People should be required to do nothing with regard to their own property. 

> **christopher.wortman said:**
> Now look at the state of Open Source Software... Nothing holds a candle to the ones used in business. We need applications that do what Photoshop and **MS Office** and Sony Vegas Pro can do and so on...

What's this about MS Office?:confused:

---

### Post by 3Miro on 2011-08-25
> **christopher.wortman said:**
> The point I am trying to make is that there is a lot of copyrighted material in the driver probably from people other than NVidia.

This is on topic.

All I hear are excuses about "windows driver workarounds" what if the NVIDIA driver has like 50 or so workarounds that some cards have something broken in them and it is a software fix? The point is, nobody is doing anything to fix the "broken power issue" with open source software, so why open source the driver, risk licensing fees, court costs, and losing BFG and EVGA and other companies as customers to sell your chip to?

Nvidia makes the driver, companies buy the chip and driver and make a card out of it.

I am sure if the developers of Open Source Software pulled their game together and made stuff worth while that works 99% of the time, and applications worth using, other companies may see the point and open source their stuff too. If you are doing nothing but complaining about "its too hard" or statements like "there are about 1000 different issues solved by Windows drivers" my question is why even try? Either do or don't but please stop complaining about things not being open source if you are not going to try to fix the issues at hand or make awesome killer applications that are more than "good enough".

You are still making no sense. I don't want Nvidia to open their drivers, I want EVERYONE to open their drivers, then there will be nothing to sue.

Manufacturers should make the drivers and manufacturers should be the ones fixing the drivers. The community should help like in the case of the Nvidia drivers and KDE. There was a bug in the Nvidia driver and KDE didn't run, it took them months to fix and nobody from the community could do anything about it.

Proprietary drivers made without the community suck. Open Drivers made by the community alone sick as well. Companies and the community should work together, which is possible only if the proprietary drivers became open.

If manufacturers make open drivers, then the drivers can only get better.

---

### Post by 3Miro on 2011-08-25
> **ninjaaron said:**
> While I agree that *they* should give away the drivers, the idea that they should be required to is bordering on fascism.  People should be required to do nothing with regard to their own property. 


fascism? Are you serious. I pay money for the video card and I **own** the video card. Yet I am not allowed to use it the way I want. Every industry out there has consumer protection laws, you wouldn't call meat inspectors fascist, would you. 

The software industry is the only exception with nobody ever being responsible for writing bad software, even when it ends up costing consumers millions of dollars. I don't see how the software industry can be any further from "fascism" and I don't see how simple consumer protection is oppressive in any form.

---

### Post by decoherence on 2011-08-25
wow, christopher.wortman and 3miro -- give it a rest guys or go start another thread.

@asifnaz the drivers generally come from the community. They are made as generic as possible so as to work with as wide a variety of similar devices as possible. having the drivers is only one part of the equation: one of the things that made Ubuntu popular was that it had device autodetection which could automatically identify devices as the computer booted and load the appropriate driver. this is fairly common now, but ubuntu had one of the earlier implementations.

some drivers come from manufacturers but this isn't as common as many people would wish.

to quickly address the root of the spat between those two posters, the main reason companies don't open source their proprietary drivers are 

1. licensing  issues (the company who makes the driver may have licensed IP or other technology from another company -- these parts have to be removed before the driver can be open sourced, or the other company has to relicense their part which in most cases has a snowball's chance in hell of happening)

2. trade secrets. if nvidia open sourced their proprietary driver, they would be concerned that AMD could look at it and use parts to improve their own products. obscuring their driver code may allow nvidia to keep a competitive advantage.

---

### Post by ninjaaron on 2011-08-25
> **3Miro said:**
> fascism? Are you serious. I pay money for the video card and I **own** the video card. Yet I am not allowed to use it the way I want. Every industry out there has consumer protection laws, you wouldn't call meat inspectors fascist, would you. 

The software industry is the only exception with nobody ever being responsible for writing bad software, even when it ends up costing consumers millions of dollars. I don't see how the software industry can be any further from "fascism" and I don't see how simple consumer protection is oppressive in any form.

You are perfectly free to buy whatever graphics card you like if you have a problem with company policies.

And bad meat is a public health risk.  Malicious software also poses another kind of pubic risk, though *generally* less serious.  Closed-sources drivers never hurt a soul.

But you're right that labelling it fascist was probably a little extreme, and I apologise.  I still think their drivers are their business, and Nvidia drivers are the last thing I want the government to protect me from.  I do not see how they constitute "bad software" in the least.

---

### Post by 3Miro on 2011-08-25
> **ninjaaron said:**
> You are perfectly free to buy whatever graphics card you like if you have a problem with company policies.

And bad meat is a public health risk.  Malicious software also poses another kind of pubic risk, though *generally* less serious.  Closed-sources drivers never hurt a soul.

But you're right that labelling it fascist was probably a little extreme, and I apologise.  I still think their drivers are their business, and Nvidia drivers are the last thing I want the government to protect me from.  I do not see how they constitute "bad software" in the least.

Nvidia drivers are a bad example, because unlike most proprietary Linux drivers, they at least work well. I do use Nvidia myself, but I also don't want to find myself in another KDE 4.1 situation, where the buggy driver was crushing the DE.

Much better examples would be some Broadcom drivers and the ATI ones before AMD made a push towards FOSS. The driver barely works, the company doesn't want to fix it and nobody else is allowed to fix it.

In terms of public risks and things that the government should protect its people from, drivers are fairly low on the list, however, having bigger problems is not a reason to close my eyes to the smaller ones.

At any rate, I think the OP got his answer by post 3 and now we a just beating a dead thread.

---

### Post by Thewhistlingwind on 2011-08-25
> **ninjaaron said:**
> While I agree that *they* should give away the drivers, the idea that they should be required to is bordering on fascism.  People should be required to do nothing with regard to their own property. 



Agreed.

(Though the fascism thing was a bit much.)

---

### Post by ninjaaron on 2011-08-25
The funny thing about this is that my computer is a piece of junk and has all stock Intel ICH9 cards which are all open source drivers, and I'm the one defending Nvidia's business practices (or rather, I don't think they are good, but I accept their right to distribute their products as they see fit).

On the other hand, I do have a netbook with Broadcom Crystal HD card that doesn't work and an eGalax touchscreen that doesn't support multitouch like it does on windows.  I wish they worked. Come to think of it... the eGalax driver is in the kernel... It must be open, but nobody is fixing it (and I wouldn't have a clue).  Not sure about the Broadcom... oh... did a search... it also appears to be open source... but ah... It doesn't look like it's in the kernel... oh... there are instructions here... hmmm...

sorry about that last bit

> **3Miro said:**
> At any rate, I think the OP got his answer by post 3 and now we a just beating a dead thread.

Doesn't mean we can't have fun doing it!

---

### Post by 3Miro on 2011-08-25
> **ninjaaron said:**
> The funny thing about this is that my computer is a piece of junk and has all stock Intel ICH9 cards which are all open source drivers, and I'm the one defending Nvidia's business practices (or rather, I don't think they are good, but I accept their right to distribute their products as they see fit).

On the other hand, I do have a netbook with Broadcom Crystal HD card that doesn't work and an eGalax touchscreen that doesn't support multitouch like it does on windows.  I wish they worked. Come to think of it... the eGalax driver is in the kernel... It must be open, but nobody is fixing it (and I wouldn't have a clue).  Not sure about the Broadcom... oh... did a search... it also appears to be open source... but ah... It doesn't look like it's in the kernel... oh... there are instructions here... hmmm...

sorry about that last bit



Doesn't mean we can't have fun doing it!

So long as we are having fun...

There is a difference between FOSS drivers made by the community and FOSS drivers made by the manufacturer. Most FOSS drivers are actually made by the community with little or no help from the manufacturers. Intel is the big exception in that regard for both wireless and video (although they did have some issue with Sandy Bridge). My sister's laptop can get full compiz effects and wireless (as well as sound as so on) straight from a live CD, no proprietary driver needed. It is a huge advantage.

Manufacturers know their hardware best and they can do the best job of making the driver initially as well as debugging it. However, as manufacturers stop making old hardware, they no longer have the incentive to keep supporting older drivers. The community on the other hand are best for supporting older hardware, so long as a significant number of people use the older hardware, some of them would have the skills to port the driver to the next version of the kernel or Xorg or whatever (porting the driver is much easier than writing form scratch).

Way too many manufacturers go with the windows mentality that drivers have to be proprietary and they can't keep up with the rapid changing Linux environment.

As for the argument that proprietary drivers somehow guard manufacturer's technology, that's why we have hardware patents. You make a piece of hardware and you patent it, then you don't have to worry how to hide it, you are protected from others "stealing" your technology. People should patent their hardware and then do things out in the open.

---

### Post by disabledaccount on 2011-08-25
> **christopher.wortman said:**
> All I hear are excuses about "windows driver workarounds" what if the NVIDIA driver has like 50 or so workarounds that some cards have something broken in them and it is a software fix? The point is, nobody is doing anything to fix the "broken power issue" with open source software, so why open source the driver, risk licensing fees, court costs, and losing BFG and EVGA and other companies as customers to sell your chip to?

Nvidia makes the driver, companies buy the chip and driver and make a card out of it.

I am sure if the developers of Open Source Software pulled their game together and made stuff worth while that works 99% of the time, and applications worth using, other companies may see the point and open source their stuff too. If you are doing nothing but complaining about "its too hard" or statements like "there are about 1000 different issues solved by Windows drivers" my question is why even try?I'll try to fix Your ignorancy:
1. Linux power managment is fine - lack of consistent PM standard and hundreds of bugs both in HW and FW caused the decision to disable (by default) some features to keep system stable - but it's possible to turn it on.
2. NV is not selling the drivers, again - You are uninformed. BFG, MSI and Asus have the source because they are adding some useless extensions. Useless, like nicer interface to already-available-in-control-panel-options. One exception, that shows interesting thing is unwinder's overclocking extension originally included in RivaTuner and beeing reverse-engineered from proprietary nv driver. Interesting is that RivaTuner is just crushing proprietary nv drivers in terms of HW control.
Proprietary drivers are not as perfect as You think - NV history is full of crappy drivers and HW. I can only laugh when I recall nforce2 - never working "hardware" firewall, never stable etharnet NIC driver (both for windows and linux) ridiculously crappy/unstable nvraid, tens of fixes without success. The funny thing is that nv NIC worked stable only with linux forcedeth driver (open source).

> **christopher.wortman said:**
> Not to mention that Intel and Nvidia  MCP chipsets are as open source as they are gunna get and AMD released  the specs of their cards and yet I still have to use the proprietary  driver because the open source one sucks 4 years after the  release...You know nothing about open source AMD-ATI drivers - that's for sure.
1. OpenSrc drv works properly with xserver, unlike proprietary driver (still many issues)
2. Supports older HW - so it's possible to run latest Linux on it. Try win7.
3. Performance is rising very fast with each build.


> **christopher.wortman said:**
> Now think about the Nvidia driver it is over 230MB in size to handle all  of the floating points and some cards run with 100+ cores per processor  and each processor is capable of handling bit points and floating  integers in the quadrillions of flops. 
  :lolflag: Troll harder. Troll harder - NV driver is bloated with multilanguage support, hundreds of game/application profiles and opanCL/CUDA API, not because it handles-the-FLOPS-and-cores. As NV fanboy You should have discovered that 3rd party modified NV driver packages are *much* slimmer and have better performance.

---

### Post by decoherence on 2011-08-25
Way to turn around the conversation! I hope OP is still reading because this dialogue really illustrates many of the concerns/thoughts/beliefs of the community.

I'm with you, 3miro, re: patenting hardware and not software, but that would be a big culture shift for a lot of companies who feel like the less they reveal, the less their competitors have on them. It's the 'safe, conservative' point of view and that's what the shareholders like.

Sure, they'd have a larger market for their hardware, but for a long time the market has been hell-bent on using whatever Microsoft feeds them anyway. That has to change before manufacturers take OS agnosticism more seriously. Of course, one of the things preventing that change is a lack of drivers and software in general. Chicken, meet egg. I would say we're heading in the right direction, though. Hardware support for non-Windows systems in general has steadily improved, even if it is slapping a "compatible with Mac OS" sticker on a box. And of course, hardware support on linux can't be called anything other than a huge triumph. Linux supports more hardware out of the box than anything else, by a long shot, despite having little to no support from the manufacturers. That's the power of motivated people!

The more manufacturers are forced to acknowledge that not everybody uses Windows, the better it is for everybody regardless of what operating system they use. This might not even be a matter of releasing drivers but even just making sure their hardware works to spec rather than working around errata with their windows drivers. If things like ACPI worked consistently across computers, you'd see a whole bunch of 'help me' threads on here disappear.

Besides, if nvidia opened their drivers, AMD might be able to use their benchmark optimization tricks! :lolflag:

---

### Post by christopher.wortman on 2011-08-25
> **decoherence said:**
> Way to turn around the conversation! I hope OP is still reading because this dialogue really illustrates many of the concerns/thoughts/beliefs of the community.

I'm with you, 3miro, re: patenting hardware and not software, but that would be a big culture shift for a lot of companies who feel like the less they reveal, the less their competitors have on them. It's the 'safe, conservative' point of view and that's what the shareholders like.

Sure, they'd have a larger market for their hardware, but for a long time the market has been hell-bent on using whatever Microsoft feeds them anyway. That has to change before manufacturers take OS agnosticism more seriously. Of course, one of the things preventing that change is a lack of drivers and software in general. Chicken, meet egg. I would say we're heading in the right direction, though. Hardware support for non-Windows systems in general has steadily improved, even if it is slapping a "compatible with Mac OS" sticker on a box. And of course, hardware support on linux can't be called anything other than a huge triumph. Linux supports more hardware out of the box than anything else, by a long shot, despite having little to no support from the manufacturers. That's the power of motivated people!

The more manufacturers are forced to acknowledge that not everybody uses Windows, the better it is for everybody regardless of what operating system they use. This might not even be a matter of releasing drivers but even just making sure their hardware works to spec rather than working around errata with their windows drivers. If things like ACPI worked consistently across computers, you'd see a whole bunch of 'help me' threads on here disappear.

Besides, if nvidia opened their drivers, AMD might be able to use their benchmark optimization tricks! :lolflag:

Thats the real point I was trying to make. While I don't agree with closed source by any means I can still understand and see why they are closed. I am not an NV "fanboy" by any means I just understand their position. If AMD were at all intelligible they would have figured it out by now because it isn't like it has been kept under lock and key so much lol. Honestly I like ATI cards and AMD is coming out with some serious stuff here real shortly.

The fact I keep trying to get across is simply where are the applications? You would think people would have figured it out that you will never see Sony Vega and you will never see Adobe Photoshop on Linux until a serious competitor exists on this platform. People need to pull together, agree on some standards, and develop some applications instead of worrying about how they should be packaged. 

This thread being beat to death is how I feel about Linux entirely. Why do I need 10 different ways to package something? Why do I need 4 different audio sub systems? Why is Gimp my only real option? Why is Audacity my only real option? I mean we finally get a decent cad application: Briscad. Yes I paid for it. The issue facing Linux is that which faces everyone in the market. If you are going to be a market leader you need to have a follow up game that hits just as hard as those around you to get them to notice you.

Power management may not be perfect, however, 99% of it is open source, and you can look at the white sheet to just about any laptop BIOS power handling. Obviously there is an exception, however, the MCP bridge is made public knowledge and we as a community cannot even get that right, and yet you expect every hw developer to grace you with the source code to their drivers? Show the initiative and perfect something. Linux is great, open source is a fantastic idea, but unless there is no practice and everyone falls into luke warm waters and accepts the "good enough" attitude, we will never have OS agnosticism in any corner of the market. Linux will lag at 1% and for some of you that may be a good thing. I am not at all by any means saying that this is a bad thing, but there are those with this vision that Linux or any OSS OS be a market acceptable thing, better have a killer game to follow because you won't get anywhere without it.

One thing I understand is marketing, it is what I do for a living. I may not know how to code, however, I know that with the wimpy application set, you cannot expect people to notice you too much. They will see your product, use it, say "hey this isn't like what exists, lets use it a little more" they then find that the product is inferior, and it turns them off to it. People aren't stupid sheep, they understand and know what they know. The good enough attitude versus the "go big or go home" attitude. If you want to see Linux flourish, do something amazing with it. Then and only then will you get noticed. You need to do something notable to get noticed.

---

### Post by ninjaaron on 2011-08-25
^^^^
The man has a point.  At the same time, realising enormous projects like he describes is unrealistic without philanthropy.  Nobody has a right to complain about these things unless they chip in money or time to support the project.

I'm not faulting you, cause you might do this, and it's really none of my business.  I'm just saying everyone is a critic, and it's BS if you don't contribute.  The truth is, it's only free as in freedom, cause at the end of the day, there is no such thing as a free lunch.

---

### Post by ninjaaron on 2011-08-25
> **3Miro said:**
> As for the argument that proprietary drivers somehow guard manufacturer's technology, that's why we have hardware patents. You make a piece of hardware and you patent it, then you don't have to worry how to hide it, you are protected from others "stealing" your technology. People should patent their hardware and then do things out in the open.

This is interesting.  I actually take the (somewhat fringe) view that intellectual property laws are unnecessary.  In my opinion, the government shouldn't control information that has nothing to do with it's own affairs (you'll begin to notice a theme here).  On the other hand, if Nvidia wants to compile binaries without releasing the code, that is their business.  I might (and do) think they are unwise and unhelpful, but I think it's their decision, and they are the ones who ultimately live with the consequences.

They *should* release their code, but they shouldn't *have to*.

---

### Post by 3Miro on 2011-08-25
> **ninjaaron said:**
> This is interesting.  I actually take the (somewhat fringe) view that intellectual property laws are unnecessary.  In my opinion, the government shouldn't control information that has nothing to do with it's own affairs (you'll begin to notice a theme here).  On the other hand, if Nvidia wants to compile binaries without releasing the code, that is their business.  I might (and do) think they are unwise and unhelpful, but I think it's their decision, and they are the ones who ultimately live with the consequences.

They *should* release their code, but they shouldn't *have to*.

decoherence made the point that corporations use proprietary drivers to guard their secrets, so this was more of a response to his point.

I am also in the opinion that the government shouldn't meddle too much, however, I want them to stand ready to interfere should it become necessary. The biggest driving force in the free market economy is competition and whenever we have a monopoly or anything preventing fair competition, the government should step in and restore balance with minimal intervention (and then step back out). Maybe idealistic, but IMO this is the proper way for things to work.

Drivers are made primarily for Windows and MS does have a monopoly. The FOSS community has to resort to reverse-engineering and all sorts of desperate techniques to get a Linux driver. With Open Drivers, people from any OS will have a chance to port the drivers and this will create bigger competition. Ultimately Windows may stay dominant, but it should be because of better technology and not because of established monopoly. This will improve both Windows and Linux, so it would be a win-win for everyone.

---

### Post by ninjaaron on 2011-08-25
> **3Miro said:**
> I am also in the opinion that the government shouldn't meddle too much, however, I want them to stand ready to interfere should it become necessary. The biggest driving force in the free market economy is competition and whenever we have a monopoly or anything preventing fair competition, the government should step in and restore balance with minimal intervention (and then step back out). Maybe idealistic, but IMO this is the proper way for things to work.I turn this issue over in my mind all the time, and you might be right.  I just have trouble figuring out where to draw the line.  I see your point, however.

> This will improve both Windows and Linux, so it would be a win-win for everyone.

or preferably Win/Lin.

Sorry! I can't help it!

---

### Post by 3Miro on 2011-08-25
> **ninjaaron said:**
> I turn this issue over in my mind all the time, and you might be right.  I just have trouble figuring out where to draw the line.  I see your point, however.

That balance is the tricky part and a potentially very politically loaded discussion.

> 
or preferably Win/Lin.

Sorry! I can't help it!

:lolflag:

---

### Post by christopher.wortman on 2011-08-25
> or preferably Win/Lin.

Sorry! I can't help it!     +1 XD

I agree with everyone's view here that everything *SHOULD* be open source. Or at the very least if possible have a base that is open source then have an area thats locked off. The base then can be tailored to meet requirements. Case in point: Air and Flash should be OSS and the applications that make them should be heavily guarded. There are a lot of Flash developing tools that are not by Adobe, so them keeping it closed source makes no sense whatsoever.

I just see their point. Drivers, and applications should be Open Source, however they aren't. That's how things are. I live and breathe marketing. Statistics are meaningless really. Statistics show the aftermath. You need to get a step ahead of the game, once the statistics are released you already lost the battle, you already feel the burn of the sharp blade that penetrated your gut and you are just now looking down realizing the warm blood is your own and not theirs. It is a very cut throat market. You should be grateful that Microsoft has been gracious not to cannibalize Linux. They could have 100 times over. 

How is this on point? Drivers fall right into this. He who has the gold makes the rules. He who makes the hardware makes the drivers and can say and do whatever makes them happy. How do we win their hearts? Show that we can be as nimble and fantastic as physically possible. Broken desktop effects, and shotty applications, and shotty power management, and shotty audio management won't do the trick. 

Do I like this? Not in the least, but I understand it a lot better than most open source enthusiasts seem to think. I run across them and they call me blind, and want Linux to rule the world. I try to tell them "its all about content baby!" then they get all annoyed and call me a -insert geek meme here-. They complain that drivers aren't open source or good, then go on and on about KDE vs Gnome vs Deb vs RPM vs ALSA vs LADSPA. They refuse to standardize and agree on anything. One of my favorite Bible quotes comes to mind here: a house divided against itself cannot stand. Having multiple technologies is not the issue, it is the fact nobody can agree on any one thing. Or they will try to be all politically correct about it and throw everything into one pot and call it good enough because the ones who argue over this stuff will complain. 

One thing Ubuntu did right, they decided early on they would standardize on Gnome, they weren't going to worry about the kernel, and they were going to standardize on one vision, the user. Unity, while not my bag of chips, is their decision. I respect them and love them and will use it because they decided. Nobody argued internally, followed one vision and almost overtook the desktop market. It was really close, a hair closer and the world would be standardized on Ubuntu. What went wrong? Ubuntu listened to the ones who complained and backed down. They got scared and didn't strike the final blow. The silent walk away and Microsoft wiped the sweat from it's brow. That is why Microsoft stopped fighting, they saw they weren't as big as they thought they were. Realized Linux and Open Source when pissed off is way more dangerous than if left alone. 

Where do drivers fall into this? They are everything, they literally make your computer work. Without them and it would fail to run. Nvidia (this is just an example, they are big so I use them) has a huge part in this. If they open sourced the drivers it would be catastrophic to Windows. They, as I am sure most are well aware of, have contracts with Microsoft not to open source their drivers. The companies they sell their chips to also have contracts with Microsoft and Nvidia. To keep everyone happy, and the Linux crowd included so everyone can play nicely together before the inevitable war, they threw a bone and released them closed. I remember the outcry when it happened. Life would be easier if they were opened, but they weren't released opened. If they were to suddenly release a new open source driver then this would be fine. They can't break contract and open source the ones that already exist. Breaking contract would be insanely stupid. The OSS community wont have the money to pay the billions of $ lost in revenue. Wont have the millions of $ to pay the fines and fees for breaking contract. SO  they remain closed.

---

### Post by ninjaaron on 2011-08-25
Sounds dramatic.
[IMG]http://1.bp.blogspot.com/__nH14BWWXT8/TMV4_o0WuLI/AAAAAAAACDA/XNSglJ77FUc/s1600/Emo-Kids.jpg[/IMG]

---

### Post by disabledaccount on 2011-08-26
> **christopher.wortman said:**
> Why do I need 10 different ways to package something? Why do I need 4 different audio sub systems? Why is Gimp my only real option? Why is Audacity my only real option? I mean we finally get a decent cad application: Briscad. Yes I paid for it. The issue facing Linux is that which faces everyone in the market. If you are going to be a market leader you need to have a follow up game that hits just as hard as those around you to get them to notice you.
Audacity is your only real option? Where are You from? Redmont? never heard of Amarok, Rythmbox, DeadBeef, and hundreds of others? Inkscape? Have You ever tried Linux-based system?

> **christopher.wortman said:**
> Power management may not be perfect, however, 99% of it is open source, and you can look at the white sheet to just about any laptop BIOS power handling. Obviously there is an exception, however, the MCP bridge is made public knowledge and we as a community cannot even get that right, and yet you expect every hw developer to grace you with the source code to their drivers? Show the initiative and perfect something. Linux is great, open source is a fantastic idea, but unless there is no practice and everyone falls into luke warm waters and accepts the "good enough" attitude, we will never have OS agnosticism in any corner of the market. Linux will lag at 1% and for some of you that may be a good thing. I am not at all by any means saying that this is a bad thing, but there are those with this vision that Linux or any OSS OS be a market acceptable thing, better have a killer game to follow because you won't get anywhere without it.You are staying confused between OpenSource (which is choice of programmer/user), open HW specification (which is choice of manufacturer) and open standard (which is in fact the only way to crate standards). I really don't want NV (or any other manufacturer) driver source - I need HW specs, that are matcheing the real HW - unlike in case of laptops PM.
Linux has about 70% on servers and 99% on supercomputers - so I think it's more than "good enough" and we don't have to show "perfect something". 

> **christopher.wortman said:**
> One thing I understand is marketing, it is what I do for a living. I may not know how to code, however, I know that with the wimpy application set, you cannot expect people to notice you too much. They will see your product, use it, say "hey this isn't like what exists, lets use it a little more" they then find that the product is inferior, and it turns them off to it. People aren't stupid sheep, they understand and know what they know. The good enough attitude versus the "go big or go home" attitude. If you want to see Linux flourish, do something amazing with it. Then and only then will you get noticed. You need to do something notable to get noticed.I want to see linux distros open source, community-driven and free. Actually, application set available for desktop is rather "good enough" than "perfect" - but I can tollerate some bugs in free software. It's at least better than buggy products sold without warranty with licences that disables Your most basic consumer rights.
You don't like it? - You don't have to.

> **christopher.wortman said:**
> Where do drivers fall into this? They are everything, they literally  make your computer work.Right. Most of hardware works OOTB with even LiveUSB - more than on windows.

---

### Post by ninjaaron on 2011-08-26
> **tomazzi said:**
> Audacity is your only real option? Where are You from? Redmont? never heard of Amarok, Rythmbox, DeadBeef, and hundreds of others? Inkscape? Have You ever tried Linux-based system?

Audacity, not Audacious.  JoKosher is the main alternative to Audacity, and it wasn't very stable the last time I tried it, but there have been major releases since then.

And WTF Inkscape?  It's wonderful, but what does it have to do with audio?

---

### Post by disabledaccount on 2011-08-26
> **ninjaaron said:**
> Audacity, not Audacious.  JoKosher is the main alternative to Audacity, and it wasn't very stable the last time I tried it, but there have been major releases since then.

And WTF Inkscape?  It's wonderful, but what does it have to do with audio?
oops, yes You right about audacity -> ardour is one of the best "competitors"
Inskape was related to GIMP, I was writing too fast :)

---

### Post by ninjaaron on 2011-08-26
I forgot about ardour, never having used it.  It looks great.  I don't have a good mic for recording my stuff, and it's usually a lot easier to record all the tracks with a mixer first and then go to the DAW for editing, at least with consumer-level hardware and applications.  I don't have a mixer either.

> **tomazzi said:**
> Inskape was related to GIMP, I was writing too fast :)

Inkscape is only related to GIMP in that they both involve images, and they make a great team for graphic design.  There is almost no overlap whatsoever in their functionality.  I guess you *could* try to create original graphics from scratch purely in GIMP, but I doubt a professional or even a serious hobbiest would ever attempt such a thing.

My Paint sorta competes with GIMP, as they are both raster editors, but GIMP is more geared towards editing pre-existing images, and my paint is for creating original works of art using semi-realistic imitation of physical media optimized for a stylus.

---

### Post by el_koraco on 2011-08-26
> **ninjaaron said:**
> I turn this issue over in my mind all the time, and you might be right.  I just have trouble figuring out where to draw the line.  I see your point, hower

Nothing to turn over in your mind about. The government should keep its greasy incompetent finger away from pretty much anything. There's a million better ways to protect any kind of "right", and a gazillion better ways to stifle the creation of monopolies than a bunch of B grade students working one out of every eight work {edit} hours {/edit}.

---

### Post by 3Miro on 2011-08-26
> **el_koraco said:**
> Nothing to turn over in your mind about. The government should keep its greasy incompetent finger away from pretty much anything. There's a million better ways to protect any kind of "right", and a gazillion better ways to stifle the creation of monopolies than a bunch of B grade students working one out of every eight work {edit} hours {/edit}.

Ignoring the political blabber, how would you break a monopoly without the intervention of the government or the court system.

---

### Post by ninjaaron on 2011-08-26
> **el_koraco said:**
> Nothing to turn over in your mind about. The government should keep its greasy incompetent finger away from pretty much anything. There's a million better ways to protect any kind of "right", and a gazillion better ways to stifle the creation of monopolies than a bunch of B grade students working one out of every eight work {edit} hours {/edit}.

I tend towards such a view as well.  Then these situations come up where it seems like it would be nice if someone with a big stick could just take care of it.

The problem is that government is crufty by design, and while not everything they do is exactly horrible, it is almost never the best way (or even a sensible way).

---

### Post by el_koraco on 2011-08-26
> **3Miro said:**
> Ignoring the political blabber, how would you break a monopoly without the intervention of the government or the court system.

eat me

---

### Post by cariboo on 2011-08-26
> **el_koraco said:**
> eat me

With that, this thread is closed.

---

