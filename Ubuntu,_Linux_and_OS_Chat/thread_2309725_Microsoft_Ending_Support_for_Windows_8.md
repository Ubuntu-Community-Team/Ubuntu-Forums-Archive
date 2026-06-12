---
title: "Microsoft Ending Support for Windows 8"
date: 2016-01-13
forum: Ubuntu, Linux and OS Chat
---

### Post by yetimon_64 on 2016-01-13
Source  : [[COLOR=#0000ff]Epoch Times[/COLOR]]("http://www.theepochtimes.com/n3/1939709-windows-8-microsoft-ends-support-for-3-year-old-operating-system/")
> Microsoft is ending security support for Windows 8 and older versions of  Internet Explorer—IE 8 through 10—as a part of its efforts to promote  its Windows 10 operating system.

It is way earlier than I was expecting when I brought this current laptop with win 8 on it. Though one major benefit for me is it has given me the perfect reason to free up the ~945 GiB in use by a MS Win 8 (OEM) install on this drive ...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=266712&d=1452661851[/IMG]

Soon to be MS free "again", last time was when 7's upgrade pricing was released in Australia. Only reason I've left this install of Windows on the drive for as long as I have, about 6 to 8 months, is because of this laptop being quite new hardware. I was initially unsure if all the hardware would co-operate with Ubuntu/Linux. With the xorg edgers ppa (on 14.04 LTS) and a bit of source code for the fingerprint reader discovered online, I'm glad to say it can be made to fully work; this laptop is a HP Envy 17 inch laptop.

Now to start the FUN of reinstalling Ubuntu (only needed to "fix" a few nagging "mess ups" of mine) and backing up the 2 storage drives and deleting unneeded "bloat". Looks like I'll be posting from a live image for the next few days :-). Cheers, yeti.

Edit: one line I missed while reading the article...
> Windows 8.1 will receive support until January 10, 2023 The article title is a bit misleading now I've seen that, Win 8 loses support 8.1 is supported till 2023 is a bit confusing. Yeti

---

### Post by jeff127 on 2016-01-13
It would have been a nuisance to maintain Vista, 7, 8 and 10 - they all have the same kernel (or close to it) yet require their own attention when patching. Microsoft has developed the problem of linux, too many different versions! After using Linux since September 2006 I can safely say that Linux is worth it... assuming one has the time to tinker and figure out which Linux is most suitable.

---

### Post by mystics on 2016-01-13
I was about to point out the Win 8/8.1 discrepancy, but I guess you already caught it. Personally, I always thought the two were recognized as definite separates. At the very least, the friends I know who used Windows 8 and 8.1 definitely treat the two different. (Personally, I hated Windows 8, and to me saying Windows 8.1 is better is like saying a contained sewage leak isn't as bad as one that runs amok.)

Either way, not a huge deal I would say. Next to Vista, Windows 8 is the least used of the Windows versions getting more than 1% market share. This certainly isn't going to be a Windows XP fiasco all over again. 2020 on the other hand might give Microsoft a heart attack if Windows 7 is still in the same position Windows XP was a couple years ago.

---

### Post by yetimon_64 on 2016-01-13
> **mystics said:**
> ... I always thought the two were recognized as definite separates. At the very least, the friends I know who used Windows 8 and 8.1 definitely treat the two different....

Yes I recognize the mistake now, I suppose mainly as I've only rarely used Windows since the end of Vista. Most of my time on computers in about the last 6 or 7 years is solidly linux. I only remembered the difference of the 2 when spotting the reference to 8.1 support.

Edit: still looking forward to the "clean out" :lol:

---

### Post by yetimon_64 on 2016-01-13
> **jeff127 said:**
> ... assuming one has the time to tinker and figure out which Linux is most suitable.
My favourite pastime ;)

---

### Post by QIII on 2016-01-13
Hee hee.

At this very moment I am creating a Windows VM, using my retail copy of Vista, my Win7 upgrade disk and the Win10 install media.  Could take a while.

There are just a couple of apps I want/need to use occasionally to work from home or communicate with Windows users.

Decided to sell my Windows box since it mostly just sat there.  Maybe I'll get another Odroid.

---

### Post by Bucky Ball on 2016-01-13
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Haven't used Windows in ages but, unfortunately, am about to build a new desktop for a project where it looks like it will be unavoidable. The state that Win is in at the moment, I have more decisions to make quite apart from friendly Linux hardware. I'd go for Win7. It doesn't need to be online so what does it matter? :|

(PS: There is another thread about this exact topic somewhere here which was, I think, posted yesterday.)

---

### Post by night_sky2 on 2016-01-13
Windows 8.1 was a major upgrade and fixed many bugs and some complaints about the initial Windows 8 release. It makes sense for MS to discard it since pretty much everyone who bought a W8 machine has upgraded to W8.1 or even W10 by now. I expect that the people who haven't will receive a message prompting them to upgrade as they should do.

---

### Post by yetimon_64 on 2016-01-13
> **QIII said:**
> Hee hee.

At this very moment I am creating a Windows VM, using my retail copy of Vista, my Win7 upgrade disk and the Win10 install media.  Could take a while...
A win VM is a good idea, just a pity I didn't go in for a retail version of 8.1. 

I love using Win in Virtualbox, especially running the 2 systems at the same time with the desktop integration feature turned on; accessing 2 systems from the one desktop was especially nice with Ubuntu as the desktop and access to the windows system available from the windows taskbar shown on the same desktop ... have fun :-)

---

### Post by QIII on 2016-01-13
Vista took about 30 minutes to install -- since I didn't bother with updates.  Win7 update should be fairly quick.  Then on to the free Win10 upgrade media.

---

### Post by lisati on 2016-01-13
A bit of a pain..... my day-to-day laptop, which is getting a bit old, battered, and tired, is a dual boot of Vista & Ubuntu. My other laptop is Windows 7....... :(

Mrs Lisati has promised me a new laptop later this year, so I'll have to do my homework......

---

### Post by yetimon_64 on 2016-01-13
> **lisati said:**
> ...Mrs Lisati has promised me a new laptop later this year, so I'll have to do my homework......

Yes, definitely "do your homework" (I didn't ... :lol:). Hybrid graphics and the xorg edgers ppa updating my whole system rendering it unusable on the first attempt was very messy indeed. I worked out to turn off the xorg edgers ppa after installing the video driver before any further updating to get a working driver/system (will have to manually check for driver updates with this method unfortunately).

 Also the fingerprint reader was totally unsupported by the current ppa used for it by most models. I was very lucky to find online a developer who wrote a driver as a "uni project", a forked version of libfprint, which enabled me to build from source and get it working. This got the machine, a 17 inch HP Envy laptop, fully operational. A pain in the butt, but well and truly worth the effort.

---

### Post by QIII on 2016-01-13
Win 10 installed.  Now time to turn off all the Microsoft "dig around in your business" stuff and then enter the long, dark night of updates.

---

### Post by buzzingrobot on 2016-01-13
Microsoft product support lifetimes in detail: [https://support.microsoft.com/en-us/gp/lifeselect](https://support.microsoft.com/en-us/gp/lifeselect)

---

### Post by yetimon_64 on 2016-01-13
> **buzzingrobot said:**
> Microsoft product support lifetimes in detail: [https://support.microsoft.com/en-us/gp/lifeselect](https://support.microsoft.com/en-us/gp/lifeselect) Just read that, result=:confused:. 

All the entries for **8.1** say ... > The product falls under the same lifecycle policy as Windows 8 with  support ending 1/10/2023.  However, customers have 24 months to **move to  Windows 8.1** after General Availability in order to remain supported.   See the [Windows 8.1 FAQ]("http://support2.microsoft.com/gp/lifewinfaq") for more information.  :confused: someone on 8.1 has 24 months to move to 8.1 ... what? ... :lol: ... maybe I've been using Linux too long to read a Windows information site.

---

### Post by craig10x on 2016-01-13
> **QIII said:**
> Win 10 installed.  Now time to turn off all the Microsoft "dig around in your business" stuff and then enter the long, dark night of updates.

Enjoy! I have been running windows 10 for a several months now (upgraded from windows 7) and i really am enjoying it...It is actually the first version of windows i have really liked using...:D
I think they finally got it right...;)

---

### Post by poorguy on 2016-01-13
I only use windows 7 for flight simulator x .
I did decide to go ahead and download the windows 10 upgrade on a couple of computers that were not being used. those i have shelved until i decide to use them.
I was wondering when MS was going to stop mainstream support for windows 8. there seems to be a push to get all windows users on the windows 10 platform.
Will keep Linux as my main driver as i am really comfortable with it.

life is good.
the poorguy

---

### Post by verymadpip on 2016-01-13
It's definitely a personal grouchey/hatred thing, but I'd suggest avoiding a Hewlett Packard machine for use with Ubuntu.  I think it's their implementation of UEFI, but there are workarounds.

I had a nightmare of a time trying to get a successful dual boot with a new piece of HP kit & eventually had to resign myself to keeping it as a purely Windows machine.  It's a touchscreen laptop that does bendy & twisty things so it can be a tablet if it feels like.  The thing just wouldn't shut down or restart from Ubuntu.  (I don't even know if that had anything to do with UEFI to be honest).
Then I upgraded it from Windows 8.1 to 10 & couldn't access my samba shares anymore, regardless of the hoops I jumped through.  Even the fix that worked on my Windows 10 desktop didn't help, so I rolled it back to 8.1 & it's all good.  Goodness only knows what that was all about...

I can't decide whether to upgrade my Windows 7 gaming rig to 10 or not, even though I quite like Windows 10.  I've got 4 more years of support & don't actually seem to be doing much gaming anymore.  Then I might have samba senanigans again...
My first world problems are a pain  ;-)

---

### Post by hg-knight on 2016-01-13
A Marmite O?S as per Vista, personnel usage was restricted to daughters lenovo laptop which was not pleasant

---

### Post by poorguy on 2016-01-13
> **verymadpip said:**
> It's definitely a personal grouchey/hatred thing, but I'd suggest avoiding a Hewlett Packard machine for use with Ubuntu.  I think it's their implementation of UEFI, but there are workarounds.

I had a nightmare of a time trying to get a successful dual boot with a new piece of HP kit & eventually had to resign myself to keeping it as a purely Windows machine.  It's a touchscreen laptop that does bendy & twisty things so it can be a tablet if it feels like.  The thing just wouldn't shut down or restart from Ubuntu.  (I don't even know if that had anything to do with UEFI to be honest).
Then I upgraded it from Windows 8.1 to 10 & couldn't access my samba shares anymore, regardless of the hoops I jumped through.  Even the fix that worked on my Windows 10 desktop didn't help, so I rolled it back to 8.1 & it's all good.  Goodness only knows what that was all about...

I can't decide whether to upgrade my Windows 7 gaming rig to 10 or not, even though I quite like Windows 10.  I've got 4 more years of support & don't actually seem to be doing much gaming anymore.  Then I might have samba senanigans again...
My first world problems are a pain  ;-)


I can't agree more as i have had my share of nightmares with hp computers and Linux installs. The only exception was the hp desktop that was all Intel motherboard / Intel processor / Intel integrated graphics adapter and that install went without any problems at all. Seems Linux and Intel work very well together. I just stay away from hp products unless they are free to me.

the poorguy

---

### Post by yetimon_64 on 2016-01-13
> **verymadpip said:**
> It's definitely a personal grouchey/hatred thing, but I'd suggest avoiding a Hewlett Packard machine for use with Ubuntu.  I think it's their implementation of UEFI, but there are workarounds...

Didn't check about anything including UEFI when buying, but had no problem at all with this particular laptop besides the 2 issues described to lisati in post 12, it is a standard type touch-screen laptop. Maybe I was plain lucky and fluked a good one.

> My first world problems are a pain  :wink: :biggrin:

Cheers, yeti.

---

### Post by buzzingrobot on 2016-01-13
> **yetimon_64 said:**
> Just read that, result=:confused:. 

All the entries for **8.1** say ...   :confused: someone on 8.1 has 24 months to move to 8.1 ... what? ... :lol: ... maybe I've been using Linux too long to read a Windows information site.

I think "...after General Availabilty..." aka the release date, is the key phrase.

I'm sure those things target Microsoft's corporate customers.  Lawyerly precision would be required.

---

### Post by yetimon_64 on 2016-01-14
> **buzzingrobot said:**
> I think "...after General Availabilty..." aka the release date, is the key phrase.

I'm sure those things target Microsoft's corporate customers.  Lawyerly precision would be required.

Ah yes, I think you may have picked it there. Glad to have left that " Lawyerly precision" aspect of Win myself. Used to read all the EULAs etc (yeah I know, that's a bit on the weird side ;-)) myself on installing applications in Win. I have lost that OCD like aspect of computing of mine on switching to Ubuntu in Nov. '07, much nicer now. Cheers, yeti. :-)

---

### Post by yoshii on 2016-01-14
I have two HP computers running Linux just fine.  One is an old HP EliteBook laptop which used to have 32-bit Ubuntu Studio v14.04.x installed on it and now has 64-bit Lubuntu v14.04.3 on it (which runs better).  
The other computer is a brand new HP ENVY running 32-bit Ubuntu Studio v14.04.3 

I'm not having any software problems with either of them.  They were NOT difficult to install.  _So not everyone is having HP difficulties with Linux_.  
The main thing about the EliteBook, made in 2007, is that it's BIOS is buggy according to reports on some of the Linux kernel forums.  So I needed to implement some kernel parameters to keep it from occasionally having a kernel panic during boot.  (Not every single time, just sometimes).  

I think the main common problems come from ACPI power management stuff.  With them disabled or malfunctioning, shutdowns become manual instead of automatic.  It's not really a Linux problem.  It's a BIOS thing.  Also, some models need the kernel command to tell the BIOS that it's Linux instead of assuming that it's Windows.  Also, I had better luck using legacy MBR BIOS mode instead of using UEFI.  I remember reading some controversy on the UEFI wikipedia page which gave the impression that UEFI and ACPI have not been implemented correctly and that Windows computers just work around the bugs instead of trying to fully be compatible.  Similarly, some Linux devs were expressing a lot of frustration with the BIOS and UEFI boot makers.  

Anyways, for a Linux site.  There sure is a lot of talk about Windows here.  I really don't understand why.

---

### Post by yetimon_64 on 2016-01-14
> **yoshi2 said:**
> ...

Anyways, for a Linux site.  There sure is a lot of talk about Windows here.  I really don't understand why. Basically it is a part of a lot of Linux users installs as a result of the OEM rot Win practices. I and a lot of others leave it in place (at least during warranty periods) in case of any hardware problems and to make it easier to deal with any such claims. Still haven't started my clean out since this discussion started but plan to as time permits, the sooner the better as I want the space for multiple partitions for dual booting and testing linux installs ;). 

The basic premise of this thread is a bit of a mistake on my part, not recognizing/remembering when posting the difference between win 8 / win 8.1 at the time of posting, and has turned into a win/HP discussion. I for one don't mind discussing other OSs occasionally, provided the site is happy to have it.

By the way I do agree, no bad problems with this particular HP machine. I've even tested ubuntu installs on a couple of other HP machines, one was a DV6 from memory, no problems.

---

### Post by KnownSyntax on 2016-01-15
The only reason that they removed mainstream support for Windows 8 is due to the fact that 8.1 is considered a service pack in their eyes (even going to the lifecycle page on Microsoft's official website will show that). Hence why they dropped support for Windows 8 since 8.1 was a free upgrade, so they can focus more on the modern mainstream operating systems they have out without needing to deal with issues that people shouldn't be facing using older versions.

Same for IE, since they are trying to move the focus over to their newer browser Edge so that it can fully replace IE outright (and remove the bad reputation that IE has gained over the years).

---

### Post by poorguy on 2016-01-15
Ok to be fair on the hp issues all of mine were on a few desktops and maybe some of the issues were due to the ACPI power management stuff. Can't say anything about hp laptops and linux installs.

---

### Post by verymadpip on 2016-01-15
I must also say, just to be clear & fair about my HP situation:
I'm pretty certain I could've had a more elegant dual booting laptop solution.
I was just happy to have a functioning Ubuntu partition (admittedly, no touchscreen function, but I didn't really care about that).
My primary issue with the touchscreen laptop was the fact that it would neither shutdown nor restart from Ubuntu.  I had to keep doing hard shutdowns,
which I fear are no good for HDDs.  I also found BIOS/UEFI options (whatever) on the particular model of laptop I own to be woeful in their choice.
There is always the possibility that I got a duff piece of kit, that generally jives with my kind of luck :-)  It did have to go back to the shop when one of the USB ports ceased to function...

I have a Compaq (HP) laptop from before UEFI days & dual booting was a breeze.  However, it's a low end laptop & with all such things there is always, IMO, a component which
clearly identifies it as a low end piece of kit, namely the CPU.

Also, I'm now a grumpy old HP hater.
DO NOT get me started on the HP Ipaq I own - utter junk!

Feel free to just jail me, I'm ranting like a an idiot now :-D

---

### Post by yetimon_64 on 2016-01-15
> **verymadpip said:**
> I must also say, just to be clear & fair about my HP situation:
I'm pretty certain I could've had a more elegant dual booting laptop solution.
I was just happy to have a functioning Ubuntu partition (admittedly, no touchscreen function, but I didn't really care about that).
My primary issue with the touchscreen laptop was the fact that it would neither shutdown nor restart from Ubuntu.  I had to keep doing hard shutdowns,
which I fear are no good for HDDs.  I also found BIOS/UEFI options (whatever) on the particular model of laptop I own to be woeful in their choice.
There is always the possibility that I got a duff piece of kit, that generally jives with my kind of luck :-)  It did have to go back to the shop when one of the USB ports ceased to function...

I have a Compaq (HP) laptop from before UEFI days & dual booting was a breeze.  However, it's a low end laptop & with all such things there is always, IMO, a component which
clearly identifies it as a low end piece of kit, namely the CPU.

Also, I'm now a grumpy old HP hater.
DO NOT get me started on the HP Ipaq I own - utter junk!

Feel free to just jail me, I'm ranting like a an idiot now :-D

I've had hardware issues at times, so can sympathize with your situation, its great when they work but oh so frustrating when you hit a dodgy one. And yep, "Grumpy Yeti" here when it happens :lol: 

No complaints from me with your post :-)

---

### Post by deadflowr on 2016-01-15
> [COLOR=#000000]Anyways, for a Linux site. There sure is a lot of talk about Windows here. I really don't understand why.[/COLOR]
Something has to put the OS in OS chat.;)

---

### Post by Morbius1 on 2016-01-15
I mean no disrespect but isn't this all academic.

One day after you turn off your machine and fall fast asleep Microsoft will turn on your Win8 machine and upgrade it to Win10 - you know - as a convenience to you.

---

### Post by yetimon_64 on 2016-01-15
No disrespect noted Morbius1, basically that is why even during my warranty period I am now willing to go Linux only on this hardware. I am now happy to go Linux only, just a bit earlier than I would have expected. Even though 8.1 is supported till 2023 etc the constant nagging to go to 10 annoys me. 

I have used the Win install occasionally and even enjoyed using the metro interface etc, but have no interest in the "forced upgrade to suit MS" mentality they have.  I disabled the "free upgrade to win 10" taskbar icon constantly bugging me at the start, as I had no intent at all to ever step up to 10, by removing registry and startup entries it was gone; a couple of updates later it was back with a vengeance so I quit trying to fight it. I agree that the likelihood of a "sneaky upgrade" is high, time to say goodbye to my MS partition as a result when I get the time ... soon hopefully as I have linux plans for the freed up space with multiple distros etc. 

> Something has to put the OS in OS chat.:wink: :)

Cheers, yeti.

---

### Post by mystics on 2016-01-16
> **Morbius1 said:**
> One day after you turn off your machine and fall fast asleep Microsoft will turn on your Win8 machine and upgrade it to Win10 - you know - as a convenience to you.

To my knowledge, Microsoft doesn't have plans to ever go this far, and I seriously doubt they will. They've received quite a bit of criticism for their handling of the upgrade process already. I doubt they want to deal with the PR nightmare of people suddenly finding their Windows upgraded against their will.

---

### Post by RichardET on 2016-01-16
> **QIII said:**
> Hee hee.

At this very moment I am creating a Windows VM, using my retail copy of Vista, my Win7 upgrade disk and the Win10 install media.  Could take a while.

There are just a couple of apps I want/need to use occasionally to work from home or communicate with Windows users.

Decided to sell my Windows box since it mostly just sat there.  Maybe I'll get another Odroid.

I did that, but stopped with Windows 7.

---

