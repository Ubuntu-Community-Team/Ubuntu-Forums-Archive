---
title: "Ubuntu and Snow Leopard"
date: 2009-03-19
forum: The Cafe
---

### Post by MikeTheC on 2009-03-19
Ok, ok... Before anyone starts reading this thread with the thought that this is another Mac OS X vs. Ubuntu thread in disguise, let me be clear: *it isn't*.

I am starting this thread because, what with Apple's pending release of Mac OS X 10.6 (a.k.a. "Snow Leopard"), they will be incorporating a number of new features (or conceptual changes) and I was curious what sort of parallels either exist now or are in the pipeline for projects upstream of Ubuntu, which then means we users of Ubuntu will have them.


[indent][font="Arial"]**Microsoft Exchange Support**[/font]

Bearing in mind, of course, that Microsoft isn't exactly in the habit of developing for Linux, I know there are interoperabilities in the Linux world. Can anyone comment on this?


[font="Arial"]**64 bit**[/font]

Ostensibly, Snow Leopard is supposed to be (fully, I would imagine) 64 bit. Now, 64 "bitness" is hardly a stranger to Linux, but how fully at this point is a typical "64 bit" Ubuntu system?


[font="Arial"]**Multicore**[/font]

Apple is introducing something called "Grand Central", which is supposed to drive performance by making sure Mac OS X itself is fully multi-threaded, and also to facilitate software developers' efforts to fully support multi-threading in their respective apps. How is multi-threading handled in Linux? What, if anything, is Ubuntu doing to support developers in the F/OSS community?


[font="Arial"]**OpenCL**[/font]

This will allow the OS and applications to access the on-board, dedicated graphics card in equipped systems for purposes of shipping off processing which the graphics card is capable of handling more efficiently than the general-purpose CPU. This is a capability in Linux? Is this something being worked on or otherwise addressed?


[font="Arial"]**ZFS Support**[/font]

At the moment, Snow Leopard Desktop is slated to receive ZFS read support, and Snow Leopard Server will get ZFS Read/Write support. Where is ZFS support at in the Linux community?[/indent]


Thoughts, folks?

---

### Post by Ocxic on 2009-03-19
I dunno about the other stuff, but the Mac OS has been 64-bit for sometime now, it's not really anything new.

---

### Post by Mr. Picklesworth on 2009-03-19
A tad off topic, but has Apple actually told us *anything* concrete about Snow Leopard other than "it's a spit & polish release"?
I keep seeing these "OMG Snow Leopard will be awesome!!!" posts and they're entirely based on rumours. It's [making my hair turn grey]("http://xkcd.com/386/").

---

### Post by schauerlich on 2009-03-19
> **Mr. Picklesworth said:**
> A tad off topic, but has Apple actually told us *anything* concrete about Snow Leopard other than "it's a spit & polish release"?
I keep seeing these "OMG Snow Leopard will be awesome!!!" posts and they're entirely based on rumours.

Well. All of the things listed in the OP.

Largely their focus is on making it faster and lighter. 

[http://www.apple.com/server/macosx/snowleopard/](http://www.apple.com/server/macosx/snowleopard/)
[http://www.apple.com/macosx/snowleopard/](http://www.apple.com/macosx/snowleopard/)
[http://en.wikipedia.org/wiki/Mac_OS_X_v10.6](http://en.wikipedia.org/wiki/Mac_OS_X_v10.6)

Those would be good places to start.

---

### Post by MikeTheC on 2009-03-19
> **Mr. Picklesworth said:**
> A tad off topic, but has Apple actually told us *anything* concrete about Snow Leopard other than "it's a spit & polish release"?

Um... [yeah, they have...](http://www.apple.com/macosx/snowleopard/)

However, my fundamental question still remains: Are the technologies Apple's putting into 10.6 *also* showing up in Linux?

---

### Post by Mr. Picklesworth on 2009-03-19
Heh, thanks for the links.

I know ZFS was being worked on in Linux. Naturally, it's there in Solaris if anyone wants it in a reasonably friendly place. The trouble is, it can't go in the kernel thanks to licensing, so it's going in as a user-space file system (FUSE). A bit ugly, but it should work.

Multicore... I just witnessed a single rogue Java process fill up all CPU resources on both CPUs to 100%. (Another miracle: The system somehow maintained a good enough balance that I didn't notice. Kudos to 2.6.28!). So it can't be bad :P

64-bit Ubuntu = 64-bit. Moreso than any proprietary OS. Apple is a close second because they control a large chunk of the software and the drivers. Dpkg refuses to install packages which weren't built specifically for 64-bit machines unless forced to, and apt automatically grabs those versions from repositories. If you have a 64-bit install and haven't done any forcing, you can be sure that every open source software package installed is quite definitely built specifically for 64-bit architectures.

---

### Post by Rokurosv on 2009-03-19
Hmm dunno if I got this wrong but isn't btrfs trying to be something like ZFS? 

Offtopic: How do Mac upgrades work, I mean is Snow Leopard a new version or just an update?

---

### Post by ghindo on 2009-03-19
> **Rokurosv said:**
> Offtopic: How do Mac upgrades work, I mean is Snow Leopard a new version or just an update?It's an entirely new version, meaning those with Leopard (10.5) will have to shell out however much it will cost to upgrade.

---

### Post by billgoldberg on 2009-03-19
[font="Arial"]**Microsoft Exchange Support**[/font]

[http://www.bynari.net/](http://www.bynari.net/)

Claims to be "fully compatble with MS-Outlook and supports all of its functionality, natively."

It is closed-source and will set you back a few bucks.

[font="Arial"]**64 bit**[/font]

Ubuntu 64-bit is 64-bit. 


[font="Arial"]**Multicore**[/font]

Linux supports multiple cores, no problem.

Not all applications support multi-threading, but as times progresses more and more do so.


[font="Arial"]**OpenCL**[/font]

> The purpose of OpenCL is analogous to that of OpenGL
> OpenCL was initially conceived by Apple Inc., which holds trademark rights


[font="Arial"]**ZFS Support**[/font]

It's possible with FUSE.

---

### Post by JackieChan on 2009-03-19
The new features seem alright, I guess.

---

### Post by scottuss on 2009-03-19
> **JackieChan said:**
> I hate to break it to you all, but Apple sucks. Even worse than Microsoft.

Whether true or not, that argument is not the purpose of this thread.

---

### Post by PhoenixMaster00 on 2009-03-19
> **ghindo said:**
> It's an entirely new version, meaning those with Leopard (10.5) will have to shell out however much it will cost to upgrade.

Not necessarily a few months ago i read an article saying because there is nothing 'new' to grab the attention of the average user and because it is essentially a performance release they are considering giving it out for (or a small fee) which would be very very good.

Me personally im looking forward to the supposed rewritten Finder in Cocoa because at the moment it is terribly basic, especially ever since i used a demo of Pathfinder.

---

### Post by Skripka on 2009-03-19
> **billgoldberg said:**
> 

Linux supports multiple cores, no problem.

Not all applications support multi-threading, but as times progresses more and more do so.




OTTOMH, I cannot think of one multi-threaded app on linux....oerhaps a I need more caoffee-but I am striking a blank.

---

### Post by insane_alien on 2009-03-19
> **Skripka said:**
> OTTOMH, I cannot think of one multi-threaded app on linux....oerhaps a I need more caoffee-but I am striking a blank.

soundconverter is one. its using both of my cores to transcode my enormous flac collection to vorbis for my portable.

---

### Post by tom66 on 2009-03-19
Ubuntu (and Linux, in general), AFAIK handles multi-core fine. However unless programs are multi-threaded they can only take part on one core at a time. However individual programs will be spread across the cores.

64-bit should not be a problem, but some programs are only compiled 32-bit so I don't know what happens then.

Although not a unified system like OpenCL, nVidia and AMD both have libraries which can take advantage of the card to do processing that the GPU is designed for. However it only works on those vendors' cards and it also requires an application compiled specifically for it.

---

### Post by artir on 2009-03-19
[font="Arial"]**OpenCL**[/font]

OpenCL is NOT OpenGL. CL is an OPEN specification that will be included in most OS somewhere in the near future. It makes employing the GPU+CPU power easier for the developer



[font="Arial"]**ZFS Support**[/font]

Who wants ZFS when we will have our uber cool BTRFS[/QUOTE]

---

### Post by MadCat30002 on 2009-08-28
Ok I had to register for this one. I just bought Snow Leopard.

DO NOT BUY THIS PRODUCT (yet)

Bitsonwheels, plain does not work
ReFit which I use to dual boot either Mac or Ubuntu plain does not work.
ANYONE with 10.4, before upgrading back up EVERYTHING as it will not install without wiping the drive
Anyone with 10.5, dont know about this for you guys.

---

### Post by misfitpierce on 2009-08-29
Ubuntu is pretty much full 64 bit on 64 bit version... I have not really hit a app so far that I needed that was not avail in 64 bit today that I needed to run a 32 bit version of... So for 64 bit support we are prob just as far if not further...

---

### Post by Regenweald on 2009-08-29
Just read a review on cnet, summation: a wee bit slower, nice new features, power pc users are screwed, guess they have to fork out another couple grand with a smile.
As always, looks beautiful.

---

### Post by warreno on 2009-08-29
> **Regenweald said:**
> Just read a review on cnet, summation: a wee bit slower, nice new features, power pc users are screwed, guess they have to fork out another couple grand with a smile.
As always, looks beautiful.

Pretty much, yup. On the plus side the X.6 release costs something on the order of US$30.

On the minus side, there is no support for PPC in it. This is a tacit declaration by Apple that they no longer support the PPC architecture, which is too bad, since my work Mac is a G5 PPC dual core that we bought *just before* they switched to Intel.

Of course that one is still running X.4.11, because the Adobe CS2 apps don't work in X.5 on PPC. InDesign in particular hates the combination.

What this means in practical terms is that my home box, a Mac Mini with an Intel core duo, is likely to soon be *two* full OS versions ahead of my work system. Sigh.

---

### Post by Regenweald on 2009-08-29
> **warreno said:**
> Pretty much, yup. On the plus side the X.6 release costs something on the order of US$30.

On the minus side, there is no support for PPC in it. This is a tacit declaration by Apple that they no longer support the PPC architecture, which is too bad, since my work Mac is a G5 PPC dual core that we bought *just before* they switched to Intel.

Of course that one is still running X.4.11, because the Adobe CS2 apps don't work in X.5 on PPC. InDesign in particular hates the combination.

What this means in practical terms is that my home box, a Mac Mini with an Intel core duo, is likely to soon be *two* full OS versions ahead of my work system. Sigh.

I don't really keep up with apple, but does this mean there is no where to go for ppc users ? Everyone with mac bought before the intel transition is in what kind of position ?

---

### Post by Sephoroth on 2009-08-29
[QUOTE=MikeTheC][font="Arial"]**64 bit**[/font]

Ostensibly, Snow Leopard is supposed to be (fully, I would imagine) 64 bit. Now, 64 "bitness" is hardly a stranger to Linux, but how fully at this point is a typical "64 bit" Ubuntu system?[/QUOTE]

Just thought I'd mention this isn't true by default.

[http://hothardware.com/News/Apples-64Bit-Snow-Leopard-OS-Installs-32Bit-Kernel-By-Default/](http://hothardware.com/News/Apples-64Bit-Snow-Leopard-OS-Installs-32Bit-Kernel-By-Default/)

In addition, ZFS support was dropped.

[http://blogs.zdnet.com/storage/?p=584](http://blogs.zdnet.com/storage/?p=584)

---

### Post by warreno on 2009-08-29
> **Regenweald said:**
> I don't really keep up with apple, but does this mean there is no where to go for ppc users ? Everyone with mac bought before the intel transition is in what kind of position ?

Hosed. X.5 is the last OSX to support PPC, by the look of things.

Though I guess you could get an install of Lin for PPC, and turn the Mac into a fileserver or something, but it seems like a heck of a waste.

It's particularly galling for me because the work G5 was bought more or less literally a few months before the switch to Intel architecture, and it's loaded with RAM and still has a long, serviceable operational life ahead of it.

For Apple to simply silently discontinue support for PPC like this is more than a little irritating, I must say.

---

### Post by Regenweald on 2009-08-29
> **Sephoroth said:**
> Just thought I'd mention this isn't true by default.

[http://hothardware.com/News/Apples-64Bit-Snow-Leopard-OS-Installs-32Bit-Kernel-By-Default/](http://hothardware.com/News/Apples-64Bit-Snow-Leopard-OS-Installs-32Bit-Kernel-By-Default/)

In addition, ZFS support was dropped.

[http://blogs.zdnet.com/storage/?p=584](http://blogs.zdnet.com/storage/?p=584)

I am indeed wowed by this release, 64bit userspace on a 32bit kernel, slightly slower, dropping of the most advanced fs currently available, culling of ppc users...29$

I hope the new features and usability are AMAZING.

@Warreno, if BSD 8.0 ppc support is good, you could still have an awesome server/desktop. If i were a ppc user i would be displeased, to say the least.

---

### Post by Frak on 2009-08-29
> **MikeTheC said:**
> 
[indent][font="Arial"]**Microsoft Exchange Support**[/font]

Bearing in mind, of course, that Microsoft isn't exactly in the habit of developing for Linux, I know there are interoperabilities in the Linux world. Can anyone comment on this?


Evolution handles Exchange just fine.

> **MikeTheC said:**
> 
[font="Arial"]**64 bit**[/font]

Ostensibly, Snow Leopard is supposed to be (fully, I would imagine) 64 bit. Now, 64 "bitness" is hardly a stranger to Linux, but how fully at this point is a typical "64 bit" Ubuntu system?


The 32-bit Kernel is loaded by default. The 64-bit kernel is loaded later in a Hypervisor. It isn't "True" 64-bit, and it won't be as long as the original Intel Core processors are supported. (32-bit only)

> **MikeTheC said:**
> 
[font="Arial"]**Multicore**[/font]

Apple is introducing something called "Grand Central", which is supposed to drive performance by making sure Mac OS X itself is fully multi-threaded, and also to facilitate software developers' efforts to fully support multi-threading in their respective apps. How is multi-threading handled in Linux? What, if anything, is Ubuntu doing to support developers in the F/OSS community?


It's up to the developers to implement threading the way they want to. There is no set Thread-Pool to work with, though making one would be neat.

> **MikeTheC said:**
> 
[font="Arial"]**OpenCL**[/font]

This will allow the OS and applications to access the on-board, dedicated graphics card in equipped systems for purposes of shipping off processing which the graphics card is capable of handling more efficiently than the general-purpose CPU. This is a capability in Linux? Is this something being worked on or otherwise addressed?


OpenCL is an Open Standard, and extensions are currently being created by Nvidia and ATi for the Linux and Windows platform. ATi already has one (of last I checked) and an Nvidia Linux build was leaked. Though, OpenCL code can be written for just about any type of hardware containing a processor. OpenCL stands for **Open** **C**omputing **L**anguage.

> **MikeTheC said:**
> 
[font="Arial"]**ZFS Support**[/font]

At the moment, Snow Leopard Desktop is slated to receive ZFS read support, and Snow Leopard Server will get ZFS Read/Write support. Where is ZFS support at in the Linux community?[/indent]


It's not stable, yet, but there will be a read/write usermode driver out soon. EDIT: Link - [http://www.wizy.org/wiki/ZFS_on_FUSE](http://www.wizy.org/wiki/ZFS_on_FUSE)

---

### Post by warreno on 2009-08-29
Oh, and anent Apple's boast that installing Snow Leopard will free up somewhere between 5 and 7 GB of hard disk space: That's probably true. I suspect the reason is that Snow Leopard deletes all PPC architecture support from your OS install. After all, you won't be using it any more.

And there's no guarantee, BTW, that current major production suites — such as Adobe's CS3 — will work in X.6. So the upgrade might be a tremendous mistake and you may have to roll back to the previous OS version, [like I did when I tried to mix X.5 and CS2]("http://indigestible.nightwares.com/2007/12/04/osx-leopard-and-adobe-cs2-bad-juju/").

Problem there is that even the "upgrade" version of an Adobe CS package costs a heck of a lot, like $1800 or so, with $2200 being the cost for a brand-new non-upgrade version. Apple and Adobe seem to be trading notes on strategy here.

@**Regenweald**: Yes, the thought (converting the PPC Mac to a fileserver) has crossed my mind. I suspect there's a hardware upgrade in my future, but it really does seem a heck of a waste to take a dual-core 2 GHz machine with a 250 GB HD and 4.5 GB of RAM, with two fer petesake video cards even, and turn it into a file server or … or a *print spooler* or something.

Sheesh. I blow through several dozen new digital photos per week on average (raw files only; I convert to JPEG in PS), and I haven't even filled the hard drive yet. It's only been 36 months!

It's bad enough that Apple is regularly forcing iPod users to get hardware upgrades. This was a $3000 machine, new, and that was in 2006. A kilobuck per yer before obsolescence is a lousy amortization curve. You wouldn't buy a car with that kind of depreciation, particularly not the computer equivalent of a Porsche.

The other problem, to my mind, is how *fast* they've dropped PPC support. They waited more than half a decade to obsolete OS9 support, but pulled the plug on Granny's PPC in half that time. That's backward, and shabby.

Intellectually I understand the reasons; as a casual programmer I get why dropping PPC architecture is an engineering necessity. But it's awful customer support, and to my knowledge they don't even have a trade-in program that lets you swap out your more-or-less still functional G5 tower for a discount on a new one.

You don't buy hardware from Apple. You lease it.

---

### Post by mrgnash on 2009-08-29
1. Exchange support? Whoopdee-doo.

2. If you install a 64-bit Linux system, it's _fully_ 64-bit, providing you don't forcibly install a bunch of 32-bit stuff... :-S

3. Multi-core support is built into the Linux kernel, and some programs utilize it as well (just as _some_ programs on Snow Leopard will).

4. Interesting, but it remains to be seen how much of a performance boost this will actually deliver.

5. Linux already has enough filesystems available to it.

---

### Post by Paqman on 2009-08-29
> **MikeTheC said:**
> 
[font="Arial"]**64 bit**[/font]

Ostensibly, Snow Leopard is supposed to be (fully, I would imagine) 64 bit. Now, 64 "bitness" is hardly a stranger to Linux, but how fully at this point is a typical "64 bit" Ubuntu system?


[font="Arial"]**Multicore**[/font]

Apple is introducing something called "Grand Central", which is supposed to drive performance by making sure Mac OS X itself is fully multi-threaded, and also to facilitate software developers' efforts to fully support multi-threading in their respective apps. How is multi-threading handled in Linux? What, if anything, is Ubuntu doing to support developers in the F/OSS community?


These are good questions.

As a 64-bit Ubuntu user i'd say that the system is very mature. It's rare to find an app that's not available in 64-bit, and even then it'll only be from a third party like Amazon or Adobe.

However, just because there's a 64-bit .deb available, it doesn't mean the app is properly optimised for 64-bit. Many amd64 CPU-heavy apps don't run any quicker than their 32-bit versions, which is a dead giveaway for a 32-bit app in 64-bit clothes.

As for multicore, again, a lot of apps are still written single threaded. That includes a lot of CPU-heavy things video re-encoding apps (ugh!) that really, really should be multithreaded. The OS itself has been madly SMPing away for years, but many of the apps aren't playing the game.

So the bottom line is that while we do technically have 64-bit and SMP support, YMMV. Your multi-core 64-bit processor may well be running apps at the same speed as a single-core 32-bit chip of the same clock speed. IMO, that sucks.

---

### Post by hanzomon4 on 2009-08-29
holding down 6 and 4 loads the 64bit kernel

---

### Post by NormanFLinux on 2009-08-29
Apple will continue to support current X.5 PPC users for a long time. We will still get updates. Snow Leopard is simply a set of improvements for Intel Macs. I wouldn't worry about Leopard being obsolete for awhile yet.

---

### Post by NCLI on 2009-08-29
> **NormanFLinux said:**
> Apple will continue to support current X.5 PPC users for a long time. We will still get updates. Snow Leopard is simply a set of improvements for Intel Macs. I wouldn't worry about Leopard being obsolete for awhile yet.
What I don't understand is why they can't just release seperate PPC, 32-bit & 64-bit versions, or just have the installer detect what system it's being asked to install to.

---

### Post by Cenotaph on 2009-08-29
as far as 64bit goes, i think linux clearly has the upper hand there, even if we sacrificed compatibility at times, a entirely 64bit linux system is much easier to obtain than a windows one and definitely easier than a mac

---

### Post by NormanFLinux on 2009-08-29
It was too much bother for them to retain support for hardware that in their view will be obsolete now that they switched to Intel, that's why!

---

### Post by MikeTheC on 2009-08-30
Vis a vis PowerPC support and Apple's direction...

Snow Leopard is the first version of Mac OS X that does not support the PPC architecture. They're not using PPC any more because of deteriorating support for and development of the CPU platform by Motorola. At this time there is no reason to believe they will ever go back to anything that bears a resemblance to PPC.

Therefore, why would anyone here reasonably expect Apple to continue support for PPC, which at this point is ridiculously out-classed by current generation C2S, C2D and C4D Intel (and AMD equivalent) chips?

---

### Post by Frak on 2009-08-30
> **MikeTheC said:**
> Vis a vis PowerPC support and Apple's direction...

Snow Leopard is the first version of Mac OS X that does not support the PPC architecture. They're not using PPC any more because of deteriorating support for and development of the CPU platform by Motorola. At this time there is no reason to believe they will ever go back to anything that bears a resemblance to PPC.

Therefore, why would anyone here reasonably expect Apple to continue support for PPC, which at this point is ridiculously out-classed by current generation C2S, C2D and C4D Intel (and AMD equivalent) chips?
If it matters, my G5 still outperforms almost every C2D on the market. I don't want to hear "it is outclassed". Freescale still puts out some very powerful PowerPC processors.

---

### Post by hanzomon4 on 2009-08-30
> **Frak said:**
> If it matters, my G5 still outperforms almost every C2D on the market. I don't want to hear "it is outclassed". Freescale still puts out some very powerful PowerPC processors.

PPC is risc based right? These are suppose to better the X86 even at lower specs right?

---

### Post by warreno on 2009-08-30
> **Frak said:**
> If it matters, my G5 still outperforms almost every C2D on the market. I don't want to hear "it is outclassed". Freescale still puts out some very powerful PowerPC processors.

Thank you. Mine too. The idea that it's obsolete is somewhat irritating.

As for the idea that Apple will continue to support X.5 for a long time — that's an interesting assertion, but I can't think of any evidence to support it.

---

