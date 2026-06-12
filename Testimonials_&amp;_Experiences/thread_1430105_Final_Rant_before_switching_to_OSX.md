---
title: "Final Rant before switching to OSX"
date: 2010-03-14
forum: Testimonials &amp; Experiences
---

### Post by ticktricktrack on 2010-03-14
I just bought an iMac and after a couple of years I want to get all the things that I hate about Ubuntu out.

Have fun

Tick


Problems partially unsorted:

Performance:
1. CPU Usage in idle: 25%
2. CPU Usage with Firefox open, idle except last.fm: 50%
3. Same as 2. after upgrade to lucid: 75%

Multimedia:
4. Videos formats not really working
5. Constant Player crashes with Rhythmbox and MoviePlayer
6. Handles avi, wmv, m4v, quicktime, h264 badly even with codec properly installed
7. In-Browser Multimedia is horrible at best
8. Flashplayer is a bitch to install and use in 64 bit
9. Flashplayer in 32 bit still not performant and buggy
25. Torrent downloads proven slower than uTorrent/Windows
27. Headphone Jack not recognized
28. Microphone problems with every new version
32. Connecting mobile phones

System:
10. Distupgrade is crap compared to clean install
11. Installing proprietary Software such as Skype, AdobeAir 64bit is made purposefully complicated
12. Broken software sources result in many minutes of waiting with every apt-get update
13. No Proper Drivers for [graphics card, sound, webcam, energy savings stuff..., take your pick]
14. Bad integration of Compiz / Desktop effects
15. Bad integration of the no.1 tool :The Browser
26. Multi monitor setup really tricky
33. Copying large amounts to USB sticks is extremely slow
34. Copying to USB sticks/drives and having files / filesystems broken

Usability:
16. Mouse Speed not adjustable after years
17. Extra mouse buttons not configurable
18. Extra mouse buttons with random behaviour in each ubuntu version

Other Stuff:
19. New Kernel every two weeks - yes this is bad, unnecessary reboot + useless boot options in grub
20. Wubi mostly broken (language problem, latest version...)

21. Too many config files without gui
22. Gui tools often look like windows 3.1
23. No Ubuntu uninstaller
24. No uninstall for self compiled packages

29. Printing would be nice after so many years
30. Sharing folders / printers in a windows network
31. Accessing folders / printers in a windows network (didn't work at all with 9.04)

32. Ubuntu Brainstorm ignored!

---

### Post by NightwishFan on 2010-03-14
Well, I suppose you should have placed this in testimonials and experiences, but do not worry, a mod will move this shortly.

Macs seem pretty cool, have fun. I hope it works out. ;)

---

### Post by Minipalmer on 2010-03-14
Well have fun on the new shiny bandwagon!

A lot of those things I have already sorted out on my Ubuntu.

From what it looks like, all things considered, Linux isn't for you because there is not a GUI for *everything.* Which isn't necessarily a bad thing. Too bad though.

---

### Post by samh785 on 2010-03-14
Live long and prosper. :D

---

### Post by ticktricktrack on 2010-03-14
> **Minipalmer said:**
> From what it looks like, all things considered, Linux isn't for you because there is not a GUI for *everything.* Which isn't necessarily a bad thing. Too bad though.

Well I program with Rails, so its mostly console and textfile stuff, but that doesn't mean I want to configure my network shares in a textfile, I'd rather have a dialog.

Remember 2 years ago when you had to edit xorg.conf for every little change?

---

### Post by J_Stanton on 2010-03-14
i had none of those problems. enjoy your new system, i know i won't. you know, for half the price, you can buy a computer with ubuntu preinstalled (which will work perfectly) and a compatible printer for half the price of a mac. oh well, it's your money, waste it as you see fit. you will be opening your wallet A LOT.

---

### Post by mamamia88 on 2010-03-15
to each his own

---

### Post by Madspyman on 2010-03-15
Hmm.. if you're gonna pay to switch away from Linux, you could have paid less for a PC, and with the money you saved, loaded it up with the same Adobe Creative Suite software that makes OS X so popular. 

You could probably get a better graphics card and a Blu-ray player added to it as well, maybe even liquid cooling, IDK. 

Does Apple still think OS X is worth like $300, they must, because the hardware in their computers sure isn't worth the price they ask, the money has to go somewhere.

Can you even add extra hardware to an iMac, or is it one of those integrated things? 

I'm ranting now, anyway enjoy the new Apple sticker on your car.

---

### Post by samh785 on 2010-03-15
> **Madspyman said:**
> Does Apple still think OS X is worth like $300, they must, because the hardware in their computers sure isn't worth the price they ask, the money has to go somewhere.
Naw, it goes straight into the corporate pockets :P.

---

### Post by dreamsburnred on 2010-03-15
> 
                                                  Hmm.. if you're  gonna pay to switch away from Linux, you could have paid less for a PC,  and with the money you saved, loaded it up with the same Adobe Creative  Suite software that makes OS X so popular. 

You could probably get a better graphics card and a Blu-ray player added  to it as well, maybe even liquid cooling, IDK. 

Does Apple still think OS X is worth like $300, they must, because the  hardware in their computers sure isn't worth the price they ask, the  money has to go somewhere.

Can you even add extra hardware to an iMac, or is it one of those  integrated things? 

I'm ranting now, anyway enjoy the new Apple sticker on your car.
ATM OSX Snow Leopard is $30/$60 For Family Pack.

Yes you can replace hardware (mem, GPU, CPU, etc).

Creative suite is $1799 [http://www.adobe.com/products/creativesuite/](http://www.adobe.com/products/creativesuite/) which is (much) more then the entry iMac.

---

### Post by etnlIcarus on 2010-03-15
I can attest to experiencing some of these issues. 

My Lexmark printer doesn't have a working CUPS driver. 

My Logitech Cordless Desktop Wave isn't properly detected: LX8 mouse (HAL sees it as an, "Unknown Button"), making it impossible to change the mouse's speed. Many hours have been spent screwing around with FDI files, to no avail. That said, the mouse buttons are still configurable in CCSM.

Firefox *was* slow as all hell and chewed up CPU time, until someone told me to install rcconf and disable, "on demand". Firefox's XUL interface also integrates poorly, although OO.org is far worse - and less fixable.

Totem/Flash browser plugins are horrible, and major upgrades are a pain. Multi-monitor is also a mess.

Large file operations to/from NTFS partitions used to result in corrupted files. Haven't had an issue since the ntfs-3g driver was declared stable about 2 years ago, however.

That said, I suspect some issues are your own making:

If updates and upgrades are slow due to a broken sources.list, that's really no one's fault but your own.

Your video/codec issues, besides seeming overlap, are probably due to your apparent use of Totem. Just like with Windows, you'll never find one video player to rule them all, which is why there's a wealth of XINE, Gstreamer (Totem) and Mplayer-based video applications, along with VLC.

Unless you encountered a bug with your networking stack, there's no valid reason why torrents would be slower. Only explanation I can think of, is you didn't check to see what port your *nix torrent client used and just assumed your port forwarding settings from uTorrent would suffice.

Installing 3rd party software shouldn't be difficult. As for, "no uninstall for self-compiled packages", you're either meant to keep the source files and use them to uninstall, or build debian packages (dh_make --createorig && dpkg-buildpackage).

Other than that, you shouldn't be using Wubi (and neither should Canonical, for that matter), older kernels are easy to uninstall, you aren't forced to reboot after a kernel upgrade and it's a little silly to be complaining about security fixes. And stuff like 14 and 22 are thoroughly undefined: I can't even tell what the problems are, especially since Win 3.1 was about the most usable thing MS ever released.

---

### Post by mamamia88 on 2010-03-15
> **dreamsburnred said:**
> ATM OSX Snow Leopard is $30/$60 For Family Pack.

Yes you can replace hardware (mem, GPU, CPU, etc).

Creative suite is $1799 [http://www.adobe.com/products/creativesuite/](http://www.adobe.com/products/creativesuite/) which is (much) more then the entry iMac.

really?  how in the world would you replace the gpu on an imac?  you would have to remove the entire screen etc to do so and then you would have very few to chose from that actually have osx drivers

---

### Post by dreamsburnred on 2010-03-15
> 
really?  how in the world would you replace the gpu on an imac?  you  would have to remove the entire screen etc to do so and then you would  have very few to chose from that actually have osx drivers 	

Replace as per first purchase rather then later on (barely anything on the mac that needs heavy GPU anyway but thats another rant).

---

### Post by Madspyman on 2010-03-15
> **dreamsburnred said:**
> ATM OSX Snow Leopard is $30/$60 For Family Pack.

Yes you can replace hardware (mem, GPU, CPU, etc).

Creative suite is $1799 [http://www.adobe.com/products/creativesuite/](http://www.adobe.com/products/creativesuite/) which is (much) more then the entry iMac.

Ok, but still it's $1,199 for an iMac with a dual core processor, a 500gb hard disk, with only 4gb of ram, and a 512mb gpu.

The same PC would cost like $400.

---

### Post by d3v1150m471c on 2010-03-15
99% of your issues solved by better ISP and not buying a crap computer.

---

### Post by dreamsburnred on 2010-03-15
> **Madspyman said:**
> Ok, but still it's $1,199 for an iMac with a dual core processor, a 500gb hard disk, with only 4gb of ram, and a 512mb gpu.

The same PC would cost like $400.
True, but people don't buy it for the hardware but rather the software (and its simplicity). Ubuntu is a free version of Mac that is ever so slowly catching up.

---

### Post by uRock on 2010-03-15
> **Madspyman said:**
> Ok, but still it's $1,199 for an iMac with a dual core processor, a 500gb hard disk, with only 4gb of ram, and a 512mb gpu.

The same PC would cost like $400.

My Asus has almost the same specs for under $400. Good luck to the OP and I hope he doesn't get one of the bad apples.

---

### Post by mamamia88 on 2010-03-15
> **dreamsburnred said:**
> Replace as per first purchase rather then later on (barely anything on the mac that needs heavy GPU anyway but thats another rant).

alright but say later down the road some new piece of software requires a better gpu.  with a pc or linux you could replace the gpu while the only model that you could do that with a mac is mac pro with base model is around $3000.  so with an imac you would just be forced to buy an entire new computer where on pc or linux you spend $100-200 and you are set

---

### Post by dreamsburnred on 2010-03-15
Pretty much only iLife needs a new GPU every 3 years...or so. Yes down the road it would be cheaper, but by then you would have no warranty :p.

---

### Post by ikt on 2010-03-15
> **ticktricktrack said:**
> Problems partially unsorted:

Performance:
1. CPU Usage in idle: 25%
2. CPU Usage with Firefox open, idle except last.fm: 50%
3. Same as 2. after upgrade to lucid: 75%

If something is taking up to 75% cpu usage on idle there is something majorly broken, I have evince open, 6 chrome tabs, konversation with 10 tabs, transmission running and.. my cpu is idling at 0-1% cpu usage on a C2D E4400, so not exactly top of the line or new.

---

### Post by mamamia88 on 2010-03-15
> **dreamsburnred said:**
> Pretty much only iLife needs a new GPU every 3 years...or so. Yes down the road it would be cheaper, but by then you would have no warranty :p.  um who buys a new computer just because the old one is out of warranty?

---

### Post by dreamsburnred on 2010-03-15
> **mamamia88 said:**
> um who buys a new computer just because the old one is out of warranty?
Never said that, more of a statement.

---

### Post by dreamsburnred on 2010-03-15
> **ikt said:**
> If something is taking up to 75% cpu usage on idle there is something majorly broken, I have evince open, 6 chrome tabs, konversation with 10 tabs, transmission running and.. my cpu is idling at 0-1% cpu usage on a C2D E4400, so not exactly top of the line or new.
The only thing that comes to my mind is flash/ads since flash for ubuntu/linux is not top notch thanks to adobe.

---

### Post by cdstuart on 2010-03-15
Hi,

I usually don't participate in discussions like these anywhere because I find them unproductive. I'm making an exception in this case because I think I have a somewhat unique perspective, and it might be informative for someone or another. Some background:

I'm using Ubuntu on a daily basis for the first time in more than four years. The last time I used it semi-regularly was more than three years ago. For about five years I've used OS X as my 'primary' OS, on laptops provided by my employer. Despite the OS on the work-provided laptops, I'm employed as a Linux admin (using an in-house, custom distro based on LFS) in an environment that supports 100,000+ users. Our servers provide various core services for those users, such as network filesystems, authentication, mail, etc. etc. So although I haven't been using Ubuntu, I've been using Linux constantly. 

Our group uses OS X as our primary interface for almost all of our work for numerous reasons. I think some important ones are:

1) Powerful shell, Unix commands available natively
2) Extremely stable and relatively easy to troubleshoot
3) Availability of easy-to-use collaborative tools
4) Fairly easy integration with many elements of Windows environment, as we sometimes need to collaborate with other groups

I've recently built a desktop machine and am triple-booting WinXP, Win7, and Ubuntu, with Ubuntu as my primary OS, and Windows around mostly to catch up on all the games I haven't played in the last 5 years; and also to check out Windows 7 and see what's happened in MS-land in that time frame.

Coming from this perspective, I understand ticktricktrack's frustration. It's obvious that Ubuntu has come a long way since I last used it. But here's the problem: in the past ten days, I've spent about as much time as I used to -- four years ago -- troubleshooting minor issues, tweaking settings, reading documentation, checking these forums for answers, etc. Problems I used to have with Ubuntu are gone, but they've been replaced by new problems. Getting the OS to act the way I want it to act is a pain in the butt. *And I do this for a living.*

I don't want to come home from work after spending all day troubleshooting Linux issues and try to figure out why, when I'm using Firefox in Gnome with more than 7 or 8 tabs open it slows to a crawl, even though it's fast as hell under XFCE with 30 tabs open. (No, it isn't a RAM issue; I've got 4 GB and most of it isn't used.) I just want to use my damn computer, bloated interface and all. I don't want to have to make it work. I don't want to have to think about it.

Note that I said above that I don't want to come home and troubleshoot more *Linux* problems. I didn't say *OS X* problems. That's because I don't have any. Or, at least, they're so damn few and far between that I can't think of any. And please believe me -- I'd notice. ***I know about ten times more about Linux than I do about OS X.*** For the love of Dog, I help maintain a Linux distribution! 

Unlike ticktricktrack, I'm going to continue using Ubuntu as my primary OS. I personally like Linux quite a bit better than OS X (though in my opinion, the interfaces aren't even comparable -- any of them). But I sure do understand where he's coming from.

---

### Post by ikt on 2010-03-15
> **dreamsburnred said:**
> The only thing that comes to my mind is flash/ads since flash for ubuntu/linux is not top notch thanks to adobe.

Yeah but watching youtube isn't exactly idle :P

So I don't think the cpu usage comments have merit.

> **dreamsburnred said:**
> Note that I said above that I don't want to come home and troubleshoot more *Linux* problems. I didn't say *OS X* problems. That's because I don't have any. Or, at least, they're so damn few and far between that I can't think of any. And please believe me -- I'd notice. ***I know about ten times more about Linux than I do about OS X.*** For the love of Dog, I help maintain a Linux distribution!

Good post, I also look forward to the day ubuntu acts like this.

---

### Post by dreamsburnred on 2010-03-15
> **ikt said:**
> Yeah but watching youtube isn't exactly idle :P

So I don't think the cpu usage comments have merit.
Well many many (OK pretty much all) sites/blogs have flash ads. 2-3 ads per page per ad and it even will slow my XP laptop to a grind (after 22 tabs). 

Yes I could use ABP but its more of a adobe issue.

---

### Post by BuffaloX on 2010-03-15
With that amount of problems I think few would use Ubuntu.

Something is horribly wrong on your system.
You start off by stating some extremely high values for CPU usage.
My system is an old 2 Ghz Athlon 64x2 My usage is 1-5% right now with Firefox and quite a few background apps like Apache server, Conky, Compiz + Emerald, xbindkeys wheather app and whatnot.

You should use a system monitor to detect why your CPU usage is so high.

Otherwise have fun with whatever you go on to...

---

### Post by derekeverett on 2010-03-15
I love macs too. Been using them for years. And Ubuntu can be frustrating sometimes for sure.. 

For the record though, the only kernel panic I've ever experienced was on a mac.

No point really, I'm just saying. They aren't perfect either.

---

### Post by J_Stanton on 2010-03-15
> **dreamsburnred said:**
> True, but people don't buy it for the hardware but rather the software (and its simplicity). Ubuntu is a free version of Mac that is ever so slowly catching up.

if you ask me, ubuntu is already there. you just need compatible hardware. when you buy a mac, of course the hardware is going to be a perfect. same with any os. you can buy linux preconfigured ya know. also get an hp printer, and you will be happy.

---

### Post by MarcusW on 2010-03-15
11. Double-clicking a .deb-file is complicated?
 13. Kinda implies you're using totally unsupported hardware, not really a good idea. (the kind of thing you check before you install, you wouldn't install OS X on a PC and then go crazy because drivers are missing, right?) 
16. Yes it is, I've done that.
 17. Yes it is, I've done that.

---

### Post by ticktricktrack on 2010-03-15
Glad that your experience is better, here's mine in more detail.

11. Installing proprietary Software such as Skype, AdobeAir 64bit is made purposefully complicated
*11. Double-clicking a .deb-file is complicated?*
**If one exists, sure, although often it can't be uninstalled that easily. But especially for 64bit, debs don't come by quite as frequent. I'm remembering the good ol' times in Windows here, where everything was installed with a few clicks.**

13. No Proper Drivers for [graphics card, sound, webcam, energy savings stuff..., take your pick]
*13. Kinda implies you're using totally unsupported hardware, not really a good idea. (the kind of thing you check before you install, you wouldn't install OS X on a PC and then go crazy because drivers are missing, right?) *
[B]Well, sure, but sometimes other people like customers, clients, friends and family make those decisions. How does it look when I'm at a clients for a couple of weeks and everythime I want to print something I have to ask somebody. And I'm not just talking Thermoprinters on COM ports.
There was a time when ATI and Intel graphic cards were a no-go. Well, that's just half the market!
[/B]

16. Mouse Speed not adjustable after years
*16. Yes it is, I've done that.*
[B]Not really, look in the forums, speed is either too slow, too fast or barely tolerable.
Linux still treats mouses as PS/2 devices. Means low sensitivity, low poll rates that have to be accelerated. But todays mouses are way better and have to be throttled because the native sensitivity is too high.(If it would actually poll the mouse that often, that is)[/B]

17. Extra mouse buttons not configurable
*17. Yes it is, I've done that.*
**Yeah I know there's BTNX and stuff, some years ago it was xorg.conf. But it's never easy and every damn version it's different to configure, and in some versions it just doesn't work.**


Tick

---

### Post by mastablasta on 2010-03-15
why do you need a 64bit? 32 bit seems to be more stable and also more supported by programmes (one of the reasons why i also run 32Bit WindowsXP - to be able to run more programmes.
 
Also i tried linux (only live CD) on a couple of computers all using USB mouse. Each of the mouses were from different brand and didn't have any problems with sensitivity.
 
When visiting cusomters and using theire printer (this is what i believe you are saying) i doubt you could also just run them on windows. but would also have to install drivers. if it's an older pinter it might work ok. but in this case it would also work with linux. linux has a flaw here because their drivers support is poor due to manufacturers.

---

### Post by Dragonbite on 2010-03-15
A co-worker of mine, who has gone from BSD to OS X was having problems trying to get his Mac to open so he can edit a particular Windows Media video format a friend sent him. He lost a lot of time looking for an OPEN SOURCE solution.

You should have seen the dirty look I got when I innocently asked "I though Apple just works". :lolflag:

So just going from one platform to another does not guarantee nirvana, it just re-arranges the furniture.

Other than that, I'm not going to go line-for-line on your issues. You had problems and I can only assume you asked questions to get to the conclusion to jump ship.  Have fun!

---

### Post by etnlIcarus on 2010-03-15
> **Dragonbite said:**
> You had problems and I can only assume you asked questions

His postcount certainly doesn't reflect it, if he did. At least not on these forums (which may be a good thing).

---

### Post by uRock on 2010-03-15
The OP has been a member since 2008 and there is always possible that he/she got help on the IRC, though I doubt it. I can start a thread and never get help, but the IRC sometimes gives instantaneous results.

---

### Post by madjr on 2010-03-15
@ticktricktrack

i never had any of the problems mentioned on this thread (and i have 4 different laptops in my house; very new and bit older)

you should probably try 32bit ubuntu and see how it compares. well 10.04 is just around the corner.


anyway why dont u install MAC OS on that computer. am sure you will suffer a lot more.

no one ever says hey let me buy an new **ubuntu compatible laptop and/or hardware**

bet u didnt even spend $50 bucks on compatible hardware, while is ok to spend thousands on compatible mac hardware

is always the same story*** "RANT RANT me spend LOTS of money on mac ougga ougga" *scratches butt* /RANT***

maybe if ubuntu wasnt free and u actually had to buy it then people would take it more seriously

if you had spent $thousand on ubuntu first hand i would not see a rant ever

---

### Post by Dragonbite on 2010-03-15
I think it would be more interesting if one were to compare an Ubuntu system pre-installed (Dell, System76, etc.) with all of the drivers, etc. working. Compare it with an Apple OS X and Windows 7 system on a variety of things.

The key is to get somebody who knows HOW to work the machine and not have to go to the command line.

Or how about a comparative panel of a Mac experienced guy, a Windows experienced guy and an Ubuntu experienced guy and see how each does a series of defined tasks to perform some specific result; update system, add new software, perform backup, connect to network, play video, create PDF, change wallpaper, attach external monitor, share a printer, restore from backup, share files, etc.  

Then again, you may need to have a couple of Linux guys, considering there are more choices and methods available.

---

### Post by namluc on 2010-03-15
> why do you need a 64bit? 32 bit seems to be more stable and also more supported by programmes (one of the reasons why i also run 32Bit WindowsXP - to be able to run more programmes.

A quick google search told me that there was little reason not to install 64bit if my computer was good enough. Installation and a longer search taught me otherwise.

> His postcount certainly doesn't reflect it, if he did.

We are encouraged to search for the answers rather than ask, the more lurkers the better isn't it&#65281;

> At least not on these forums (which may be a good thing).

Group decision, do we love ubuntu, do we want widespread adoption? not going to happen with that attitude.

---

### Post by ElSlunko on 2010-03-15
Sometimes I wonder if I'm missing something or just lucky as I never have these types of problems. Maybe I just don't demand much out of my computer.

Anyways, have fun and enjoy your OS!

---

### Post by ticktricktrack on 2010-03-15
Hi Guys, thanks for all your feedback.

Let me explain myself a little better. I have to say I do like Ubuntu, but for an efficients work and home environment it's just not enough anymore.

Tick

Forums:
I stopped posting in forums a while ago, except for when I think I'm really close to the solution.

1. Search in the most used forums and google usually returns a couple of options that I then go through one by one.
2. Lot's of Problems are just to complex to have THE solution, it's a process of trial and error.
3. I lost faith in forums in my Gentoo years. Community was good, but the problems were just too complex.
4. Usual answers include:

*My car is broken!*
Use the bycicle!

or "Be glad the community put so much effort in this" - *Well I am, but I still like it to work.*

5. Older experiences with forums, when you had to edit the xorg.conf for changing mouse speeds and multi monitor settings, left me with many broken Ubuntus, so now I won't go in too deep anymore, this is a work environment for me, I can't have it fall apart by some forum suggestion.


[IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]

Edit: I just noticed the amount of Ubuntu rants has gotten really high lately. Coincidence?

---

### Post by J_Stanton on 2010-03-15
> **ticktricktrack said:**
> this is a work environment for me, I can't have it fall apart by some forum suggestion.

me too, that's why i use ubuntu/linux. i can't afford flaky systems like windows/macos.

as someone mentioned, you could have bought a ubuntu compatible/preinstalled computer and had a great experience. it's your money, throw it away as you see fit.

---

### Post by ElSlunko on 2010-03-15
Again, less things would get broken with compatible hardware. Though there are incidents where this wasn't true, it's generally accurate.

---

### Post by MarcusW on 2010-03-15
> **ticktricktrack said:**
> Glad that your experience is better, here's mine in more detail.

11. Installing proprietary Software such as Skype, AdobeAir 64bit is made purposefully complicated
*11. Double-clicking a .deb-file is complicated?*
**If one exists, sure, although often it can't be uninstalled that easily. But especially for 64bit, debs don't come by quite as frequent. I'm remembering the good ol' times in Windows here, where everything was installed with a few clicks.**

13. No Proper Drivers for [graphics card, sound, webcam, energy savings stuff..., take your pick]

*13. Kinda implies you're using totally unsupported hardware, not really a good idea. (the kind of thing you check before you install, you wouldn't install OS X on a PC and then go crazy because drivers are missing, right?) *
[B]Well, sure, but sometimes other people like customers, clients, friends and family make those decisions. How does it look when I'm at a clients for a couple of weeks and everythime I want to print something I have to ask somebody. And I'm not just talking Thermoprinters on COM ports.
There was a time when ATI and Intel graphic cards were a no-go. Well, that's just half the market!
[/B]

16. Mouse Speed not adjustable after years
*16. Yes it is, I've done that.*
[B]Not really, look in the forums, speed is either too slow, too fast or barely tolerable.
Linux still treats mouses as PS/2 devices. Means low sensitivity, low poll rates that have to be accelerated. But todays mouses are way better and have to be throttled because the native sensitivity is too high.(If it would actually poll the mouse that often, that is)[/B]

17. Extra mouse buttons not configurable
*17. Yes it is, I've done that.*
**Yeah I know there's BTNX and stuff, some years ago it was xorg.conf. But it's never easy and every damn version it's different to configure, and in some versions it just doesn't work.**


Tick

 The first point was mainly because Skype comes in *.deb format, at least it did the last time I installed it. 

 I've adjusted my mouse speed perfectly, and the extra buttons were configured with the same tool as the key shortcuts. Really simple, and same way in Ubuntu Jaunty, Karmic, Debian sid and Debian squeeze. I still believe many of your points are because of incompatible hardware. Don't get me wrong though, unsupported hardware is something to complain about, but saying these things don't work when they clearly work for alot of people is just wrong.

---

### Post by julianb on 2010-03-15
> You should have seen the dirty look I got when I innocently asked "I though Apple just works".

Apple just works a lot of the time. It does the "most common tasks" very well, just like Ubuntu does. Start getting into obscure stuff, and you'd better be using the platform that is most popular for whatever obscure-stuff you are doing. (playing a new game or editing windows media files? windows is probably the easiest choice! trying to run mathematics software developed for use by universities? might only work on linux. editing music for professional CDs? it could be that your favorite program is OSX-only.)

---

### Post by uRock on 2010-03-15
I am starting to wonder if the shift key works in every OS.

---

### Post by etnlIcarus on 2010-03-15
> **namluc said:**
> Group decision, do we love ubuntu, do we want widespread adoption?And what does this have to do with anything?

> not going to happen with that attitude.Not going to happen with the average level of support on these forums. In case you haven't noticed, the average reply to a support request is *abysmal*: people don't bother to read the OP, throw out some 1 & 1/2 sentence cookie-cutter advice that a) isn't explained well enough and b) isn't even relevant to the OP's question and is often wholly inappropriate (I've gotten into arguments with people instructing others to use CLI tools needlessly, in place of graphical ones in the *Absolute Beginner* forum and then not even having the foresight to explain what the string would do to the user's PC). A couple of years ago, it was a different matter. These days, Ubuntu users are better off getting their problems fixed somewhere like linuxquestions.org.

---

### Post by uRock on 2010-03-16
Instead of arguing with those who aren't helping in the manner you prefer you could actually pitch in and help people, too. With a post count of only 200, you couldn't be helping many people during the 4 years of being a member.

---

### Post by etnlIcarus on 2010-03-16
Oh witty. Of course, this forum isn't where I do most of my troubleshooting.

---

### Post by uRock on 2010-03-16
I try to help people as much as I can. I just think if you aren't part of the solution, then can still try.

---

### Post by DeusExM1 on 2010-03-16
You... bought a mac? lol. :popcorn: .

---

### Post by GodLikeCreature on 2010-03-16
I personally don't like Apple.  Can't be more proprietary than it is, and I personally love the freedom in Linux.

Back to the OP's rant, I am afraid I can't really help.  I have installed Linux in many machines, never experiencing most of the issues you describe.  I am sorry you have, and I wish you the best of luck with your new machine/OS.

---

### Post by mastablasta on 2010-03-16
> **ticktricktrack said:**
>  
Forums:
I stopped posting in forums a while ago, except for when I think I'm really close to the solution.

 
There are other forms of support.
 
Such as IRC channels or you can pay to get support from Cannonical - it's actually really cheap.

---

### Post by ticktricktrack on 2010-03-16
> **GodLikeCreature said:**
> I personally don't like Apple.  Can't be more proprietary than it is, and I personally love the freedom in Linux.

No, that's not true. The primary reaon why I get a Mac is because it's a Unix system WITH all the proprietary software options.

Means I have the bash, apt-get, all the open-source commandline tools and libraries and the open source stuff I work with every day: **Ruby **and **Rails**- work perfectly.

Just enhanced with TextMate, a great mouse, desktop effects that don't break stuff and some other proprietary things.

Tick

Edit: macports is more common, but apt-get works too

---

### Post by NightwishFan on 2010-03-16
I think apt-get is Debian specific, but I get what you are saying. Darwin is a microkernel right?

---

### Post by caravel on 2010-03-16
Yes apparently you can install (ported) APT tools on Mac OSX.  I'm not sure of the state of the repositories or the indeed the benefits, but the option is there.

Personally I wouldn't use a Mac of any kind, even if it was given to me.  I like to have a choice of hardware/software and I always build all of my PCs.

---

### Post by 3rdalbum on 2010-03-16
I'm sorry I don't know you, and I'm not sure about your sense of humour, but I just have to be sure: You're joking about these, right? Your later posts didn't seem to be humorous, so I don't know.

---

### Post by 3rdalbum on 2010-03-16
> **etnlIcarus said:**
> In case you haven't noticed, the average reply to a support request is *abysmal*: people don't bother to read the OP, throw out some 1 & 1/2 sentence cookie-cutter advice that a) isn't explained well enough and b) isn't even relevant to the OP's question and is often wholly inappropriate

I reluctantly have to agree here. I always see people saying "Get the output of lshw -C network and post it here so we can see what wireless card you're using", and the output of that command virtually NEVER shows the information; whereas lsusb and lspci always do.

And the number of "How do I install 64-bit Flash Player" threads where someone has posted "sudo apt-get install flashplugin-nonfree"... it makes you want to scream.

> (I've gotten into arguments with people instructing others to use CLI tools needlessly, in place of graphical ones in the *Absolute Beginner* forum and then not even having the foresight to explain what the string would do to the user's PC).

True to an extent, but I wish people wouldn't say "Open /var/apt/sources.list and add these lines". Because invariably, the person is going to put all sorts of junk into their sources.list and then post again later asking why they're getting a "Type 'sudo' unknown on line 53" error whenever they try to run 'sudo apt-get update'.

The GUI tool prevents these problems, and it comes preinstalled on Ubuntu - why won't people advise others to use it?!

---

### Post by etnlIcarus on 2010-03-16
> **caravel said:**
> Personally I wouldn't use a Mac of any kind, even if it was given to me.  I like to have a choice of hardware/software and I always build all of my PCs.

I'd screw around with it. The Macs I've used haven't been my own, so I haven't had a chance to see if I can un-n00b it. Although considering Apple, I doubt it's very mod-friendly.

---

### Post by samh785 on 2010-03-16
> **ticktricktrack said:**
> No, that's not true.
Are you saying it isn't true that he dislikes Macs? Perhaps you are rejecting the observation that Apple is (like it or not) a very proprietary based company? Surely you aren't denying that he likes Linux...

---

### Post by nigsy on 2010-03-16
"11. Installing proprietary Software such as Skype, AdobeAir 64bit is  made purposefully complicated"


I've just installed Skype on a dell netbook running Ubuntu 9.10  - Package manager, search for skype & add???

How hard is that?

On W7 > find skype website > find download & download > run > accept UAC messages (3 of them) > accept firewall messages because a new programme is trying to connect. Finally done. 

Ubuntu all the way.

---

### Post by ukripper on 2010-03-16
> **ticktricktrack said:**
> I just bought an iMac and after a couple of years I want to get all the things that I hate about Ubuntu out.

Have fun

Tick



Ok!

---

### Post by caravel on 2010-03-16
> **3rdalbum said:**
> I always see people saying "Get the output of lshw -C network and post it here so we can see what wireless card you're using", and the output of that command virtually NEVER shows the information; whereas lsusb and lspci always do.
Very true.

---

### Post by ibuclaw on 2010-03-16
> **ticktricktrack said:**
> 
Performance:
1. CPU Usage in idle: 25%
2. CPU Usage with Firefox open, idle except last.fm: 50%
3. Same as 2. after upgrade to lucid: 75%


I sure hope that you used top to get those values - as the gnome system monitor is reknowned for showing abnormally high CPU levels (self inflicted, mind you. As soon as you close the app, the CPU usage drops back down to 1-3%).

---

### Post by ticktricktrack on 2010-03-16
Hi Guys

yesterday I did a fresh lucid install on my Dads notebook to work with something until my iMac arrives.

Things that are better:
OpenGL out of the Box!
mouse speed is very good, 
multi screen setup was easy and works with 75Hz
I like the new gnome look

Problems occured:
skype installs fine, but I can't get the mic to work, well I can set alsamixer so that I can hear myself, but pulsaudio is reluctant to capture anything.

sudden crashes evers 2-5 hours
[B]
Annoyingly high CPU usage[/B]

Here's a screenshot:

Edit #123: Sorry for the image below, it took me 18 minutes to get a screenshot up here, Ubuntu makes 1.3MB screenshot and this forum reduces quality to blurry. And the image tag here isn't too smart either.

[http://img339.imageshack.us/img339/8315/screenshotjl.png](http://img339.imageshack.us/img339/8315/screenshotjl.png)

[http://twitpic.com/18xmq1/full](http://twitpic.com/18xmq1/full)

---

### Post by uRock on 2010-03-16
Are you using System Monitor or top to check CPU usage? System monitor shows higher numbers that top.

---

### Post by etnlIcarus on 2010-03-16
> sudden crashes evers 2-5 hours
Lucid isn't even released yet. It's still in Alpha. Expect crashes.
> Annoyingly high CPU usage
You've got 2 web browsers open, one of which is using Flash. Unless you're one of the minority of people with the right hardware to enable hardware acceleration in Flash, you're going to get high CPU usage.

And if ALSA is working and PulseAudio is not, uninstall pulseaudio. Last I checked, Skype doesn't require pulseaudio. It can work with any 3 of the major linux sound servers.

---

### Post by ticktricktrack on 2010-03-16
> **iRock said:**
> Are you using System Monitor or top to check CPU usage? System monitor shows higher numbers that top.

I always use top from the terminal. On the right side of my screenshot there's the top output for you.

---

### Post by ticktricktrack on 2010-03-16
> **etnlIcarus said:**
> 
You've got 2 web browsers open, one of which is using Flash. Unless you're one of the minority of people with the right hardware to enable hardware acceleration in Flash, you're going to get high CPU usage.


As you can see on ther right side of my screenshot, flash isn't the problem, it's xorg thats using it up. Besides on win7 last.fm takes 2% at best, it's not even animating anything.

---

### Post by ibuclaw on 2010-03-16
> **ticktricktrack said:**
> Hi Guys

yesterday I did a fresh lucid install on my Dads notebook to work with something until my iMac arrives.

Things that are better:
OpenGL out of the Box!
mouse speed is very good, 
multi screen setup was easy and works with 75Hz
I like the new gnome look

Problems occured:
skype installs fine, but I can't get the mic to work, well I can set alsamixer so that I can hear myself, but pulsaudio is reluctant to capture anything.

sudden crashes evers 2-5 hours
[B]
Annoyingly high CPU usage[/B]

Here's a screenshot:

Edit #123: Sorry for the image below, it took me 18 minutes to get a screenshot up here, Ubuntu makes 1.3MB screenshot and this forum reduces quality to blurry. And the image tag here isn't too smart either.

[http://img339.imageshack.us/img339/8315/screenshotjl.png](http://img339.imageshack.us/img339/8315/screenshotjl.png)

[http://twitpic.com/18xmq1/full](http://twitpic.com/18xmq1/full)

What type of graphics card do you have, and what driver are you using for it?
If you disconnect the external monitor and restart X, does the problem persist?

Am curious if it is an issue due to driver used w/ multi-monitor.

Regards
Iain

---

### Post by etnlIcarus on 2010-03-16
Ahh. I stand corrected. Apologies.

---

### Post by ticktricktrack on 2010-03-16
Thanks ibuclaw,

I seem to have narrowed the problem down. Xorg does software opengl via AMD Mesa rendering and doesn't use the graphics card at all.

There's built-in Radeon 3200, maybe I can get that working. Hardware drivers dialog does nothing, sadly.

Lol, I just thought that this setup makes ubuntu ONE BIG FLASHPLAYER!

Tick

---

### Post by madjr on 2010-03-16
@ticktricktrack

i got the mic working, actually i got 3 mics (different headsets) all working

the problem was the **input** volume is very low in **sound preferences**. also there's a **connector** option to choose from

anyway i like your desktop pic, looks really **cool**. i cant wait for final.

it doesn't matter if you gotta use mac, linux, windows or a NASA supercomputer, if your job demands it, you have to do it.

no one here is against you using a Mac, many here have 1, i had 1 and now i have a system76.

am a tinkerer and without linux i would be plain bored out of my mind.

linux still needs lots of work, but the journey, many times, is just as fun as the end result.

---

