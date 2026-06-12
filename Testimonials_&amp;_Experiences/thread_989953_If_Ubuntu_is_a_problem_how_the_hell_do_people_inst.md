---
title: "If Ubuntu is a problem how the hell do people install window?"
date: 2008-11-22
forum: Testimonials &amp; Experiences
---

### Post by plantje on 2008-11-22
A bit of a different story...

I am using Ubuntu for a while now. I really love it. Last week I decided to install XP next to Ubuntu to be able to play fallout3. Let the horrors start...

I cleared a partition for windows

Booting from XP CD. It didn't recognize my SATA hard disk. Had to search the driver on the internet, inject them into a XP CD image using 3th party tool, and create a new CD. Impossible for newbie...but let's go on...

First I tried to install it next to my existing Ubuntu. This doesn't work, XP messed up the Linux drive. It's not only the boot loader. Got so fed up that i decided to reinstall both XP and Ubuntu.

Ok, I got windows installed! Initially video, network and sound are not working. This is a bit of a problem as i don't have a network driver somewhere... I really thought a network driver would be included for a standard 3com  card. Anyway used my girlfriends laptop to download the driver and installed it. Nvidia video card driver was easy.  Sound card driver took a bit of searching on the internet. Although it was 180 MB package(!!!) with a lot of extra junk.

As i don't really like it when my printer is turned on and windows keeps trying to explain me it is broken because it couldn't find drivers, i decided to install this one as well. This is a HP Photosmart C4280. This driver again too large, 40 MB!  In the end I got it working. Although using this horrible software to print/scan something is a pain. 
BTW it seems the actual scanning is twice as fast in Ubuntu then in windows using the manufacture drivers.

For fun I also wanted to test my USB WIFI connection. Downloaded the drivers and it simply does NOT work. Even with the original driver I can't seem to get it working. It auto disconnects every time! I gave up!

Next thing Ubuntu. Installing is easy, next, next, next. And it is done.

Sound, network, printer and video work out of the box. get a message that there is a proprietary driver for my Nvidia, I accept.

WIFI doesn't work out of the box after a bit of searching on the internet I got it working.

Installing windows took me almost a day, Ubuntu an hour.

I am 100% sure that if people spent the same time on Ubuntu as on Windows they will love Ubuntu more. Tried to learn my girlfriend using Ubuntu, she actually likes it. I remember a friend of her coming over asking 'What a strange windows is this' she said 'No it's Linux, just like windows but a bit easier'. I really liked that :-)

---

### Post by theApokalypsis on 2008-11-22
You are right, GNU/Linux seems to be taking off (in usability and ease of installation) as opposed to years ago. I switched fully to the Debian base from Vista and never looking back. Although... thankfully.. didnt run into your issues as I used two different HD's for Vista and Ubuntu. its appalling how much more you can truly do with all the great projects created from open source.

:guitar:

---

### Post by 3rdalbum on 2008-11-22
People don't reinstall Windows; they use a system restore CD that merely re-images their hard drive to the state it was when they got the machine.

I don't know how people manage to install XP.

---

### Post by Skripka on 2008-11-22
> **3rdalbum said:**
> People don't reinstall Windows; they use a system restore CD that merely re-images their hard drive to the state it was when they got the machine.

I don't know how people manage to install XP.

I love the irony of installing XP.



With Windows XP, from the very beginning of the install you get a bluescreened background :lolflag:

---

### Post by benjgvps on 2008-11-22
If you knew anything about Windows or anything about bootloaders you would know that Windows is a dominating operating system in the way that it installs a bootloader regardless if there is one currently installed. That is why EVERY guide of installing Linux and Windows on the same machine tell you that you HAVE to install Windows first to avoid trouble and head scratching.

---

### Post by nickdbliss on 2008-11-23
I dont think i am going to install xp on my laptop ever.

---

### Post by SuperSonic4 on 2008-11-23
The most obvious answer is that people don't install windows for it is pre-installed :p
But I agree, I had to dedicate an entire hard drive to XP

---

### Post by Crafty Kisses on 2008-11-23
I'm not taking anything away from Windows XP, I think it's a fair operating system that is pretty solid, but I see stories like this time and time again, of people who install Ubuntu and then try to reinstall Windows and they're like, "Man Ubuntu is easy to install" which really amazes me to be honest. It's amazing how far Linux has come.

---

### Post by Melindrea on 2008-11-23
The biggest reasons for why I think Ubuntu is a lot easier to install than Windows:

1. Once I've installed it, assuming the drivers exist, it's automatic. I don't need to look on a whole bunch of sites to find the drivers I need. (yes, not always true, we're talking best-case scenario here =)

2. It's a lot faster than Windows to install, at least it was for me.

3. :generally: there's not too many reboots when updating and such. I've had to do two the last few times I installed Ubuntu: One for a new core, and one for activating nVidia drivers.

---

### Post by yosumi on 2008-11-23
> **plantje said:**
> 
Booting from XP CD. It didn't recognize my SATA hard disk. Had to search the driver on the internet, inject them into a XP CD image using 3th party tool, and create a new CD. Impossible for newbie...but let's go on...

i had the exact same problem when installing XP last night.

it took me half a day to figure out the sata problem. during the XP installation, you can ONLY install sata driver from floppy. what a shame.

---

### Post by HungryMan on 2008-11-23
xp install = 6++ hours (lol If I told you why, I would have to kill you. hahaha)
ubuntu install = >30 minutes

the only thing that takes a loooooooong time in ubuntu is customization.
I seriously spent almost a whole day toying with compiz-config, installing and uninstalling apps and changing themes.:lolflag:

---

### Post by mihaimm on 2008-11-24
Question: How do you install XP on an all SATA computer (SATA CD-ROM, SATA HDD, no FDD)?
Simple Answer: You DON'T!
Complex Answer: You get an ide cdrom, ide hdd, do the install, then install sata drivers, then copy the image from the ide hdd to the sata hdd.

---

### Post by Walter_Crankite on 2008-11-24
Always install windows first, then linux.
The boot manager in windows is crappy.
Grub always identifies your windows partition. 

For the SATA, grab the correct driver.

Walter

---

### Post by borlosky on 2008-11-24
> **mihaimm said:**
> Question: How do you install XP on an all SATA computer (SATA CD-ROM, SATA HDD, no FDD)?
Simple Answer: You DON'T!
Complex Answer: You get an ide cdrom, ide hdd, do the install, then install sata drivers, then copy the image from the ide hdd to the sata hdd.

or use the sata drivers (usually on a floppy) that came with your mobo. and press F6 during windows install when it says "press F6 to install raid or 3rd party drivers" that sould get sata working on an xp install.

---

### Post by Skripka on 2008-11-24
> **borlosky said:**
> or use the sata drivers (usually on a floppy) that came with your mobo. and press F6 during windows install when it says "press F6 to install raid or 3rd party drivers" that sould get sata working on an xp install.

When was the last time I used a floppy?........... ;)

---

### Post by borlosky on 2008-11-24
> **Skripka said:**
> When was the last time I used a floppy?........... ;)

lol very true, gotta hand it to microsoft though, they know how to keep you using outdated hardware like no other.:lolflag:

---

### Post by rfarmer on 2008-11-24
> **mihaimm said:**
> Question: How do you install XP on an all SATA computer (SATA CD-ROM, SATA HDD, no FDD)?
Simple Answer: You DON'T!
Complex Answer: You get an ide cdrom, ide hdd, do the install, then install sata drivers, then copy the image from the ide hdd to the sata hdd.

Slipstreamed an XP install with correct SATA drivers since it was on a laptop with no floppy. Installing XP is very simple, just never assume it will have the necessary drivers included.

---

### Post by armandh on 2008-11-24
most got their MS OS with their computer and have no idea how to reinstall once it is toast. every high school should have a class to put an OS on a computer [you know, call it drivers ED, oops that is taken]

---

### Post by Capt. Mac on 2008-11-24
> **armandh said:**
> most got their MS OS with their computer and have no idea how to reinstall once it is toast. every high school should have a class to put an OS on a computer [you know, call it drivers ED, oops that is taken]

As much as I'd like to agree with your sentiment, your analogy is way off. Drivers Ed teaches you how to use a vehicle, not how to put it together. They teach you very little about what is actually going on under the hood of your car, just what you need to know to sit in the drivers seat and use it. [Mandatory] Computer classes in high school are a lot like this: they focus on how to use applications like MS Office or Photoshop, but not how to configure systems.

Edit: whoops misread your post, now I see you weren't comparing them at all. I thought you said "You know, like drivers ED"

---

### Post by Inxi on 2008-11-24
To HungryMan
With my appreciation of Ubuntu, it took longer to install on my PC than XP did... maybe it was because the XP partition was only 50 GB while the Ubuntu one was about 250.

To OP
Tell me about it. I reinstall (completely, I don't use System Restore) Windows XP about every 6 months to clean up the system (be it registry crap, invisible virus/trojan/spyware, or just average slowness that Windows likes to collect), and every time I do it, there is one problem or another.

My old computer had all these video driver issues.
If you don't install SP2 right away you can forget about it.
My new computer required some super specific Realtek Audio Driver for sound. As a result, the 3 days I failed to find that driver I have finished the whole entire DooM III without sound. My new computer also wanted some specific ATI drivers that I had trouble finding. The printer driver... which bugged and kept telling me my printer is not plugged in.
And don't even get me started on the wireless card issues................
Fortunately, over the years I stopped being an idiot and collected all my drivers and SP2 on a CD. But next time I get a new computer, it will all start over again (and I get computer from newegg, e.g., no OS pre-installed).

Ubuntu... bless it. I installed it, and it put everything I ever needed on it at once. Printer driver, scanner driver... sound driver. I had internet the moment it finished installing. It showed the official ATI driver in my face. It has Firefox. It has Pidgin. OpenOffice. My fear with Linux was that it wouldn't recognize my hardware and I'd have to pick the net in search of drivers with long names of Linux kernel pathways and what not. Well, Linux improved over the years.

---

### Post by Therion on 2008-11-24
**Reinstalling XP:** (And this is using my slipstreamed install CD with sata drivers and SP3):  About about a half-day job.  I'd say ~6 hours to do the full blown XP install itself, get online, *Activate* XP, install WGA et al, so I can then download *more* updates and patches (rebooting as necessary of course!), install essential software packages like MS Office and then download updates for THAT, more rebooting... Arrrrgh.  The next several hours are spent installing additional software (anti-virus, spyware checker, defrag app, et al) and ***then***, finally, tweaking and customizing everthing.  

**Hardy Heron:** From fresh install to fully "tricked out" in about two hours.

---

### Post by Inxi on 2008-11-24
> **SuperSonic4 said:**
> But I agree, I had to dedicate an entire hard drive to XPWhy? I just gave it a little piece and installed Ubuntu on the remaining space.

---

### Post by Tamlynmac on 2008-11-24
I totally agree. I've read many a testimonials that bash Ubuntu because they had trouble installing it. Often it's directly related to hardware and of course they never investigate for compatibility prior to installation. Yet they hold Windows up as the basis for their comparison.

I can't count how many times I've installed Windows (pick a version) and spent exorbitant amounts of time searching for drivers (that may or may not work) or mindlessly waiting for updates to complete only to find something failed after the update. I get frustrated when reading statements that note how Ubuntu failed to install and is a piece of (fill in your own expletive). Upon investigation it relates directly to hardware and the installer just _assumed_ that their system was totally compatible. Every windows program including the OS generally documents system requirements and expects the installer to read and understand said requirements. However, that doesn't apply to Ubuntu - It Just Works". Don't know how many times I've read that. Seems a double standard applies - if Windows fails install due to hardware incompatibility that's acceptable - if Ubuntu fails due to hardware incompatibility "It Sucks". A lack of understanding and investigation on an installers part, doesn't equate IMHO to a issue with Ubuntu.

Sorry for being so blunt. I'll endeavor to be more sympathetic (to those that can't read or chose not to) in the future. Well, I will try.

---

### Post by borlosky on 2008-11-24
> **Tamlynmac said:**
> I totally agree. I've read many a testimonials that bash Ubuntu because they had trouble installing it. Often it's directly related to hardware and of course they never investigate for compatibility prior to installation. Yet they hold Windows up as the basis for their comparison.

I can't count how many times I've installed Windows (pick a version) and spent exorbitant amounts of time searching for drivers (that may or may not work) or mindlessly waiting for updates to complete only to find something failed after the update. I get frustrated when reading statements that note how Ubuntu failed to install and is a piece of (fill in your own expletive). Upon investigation it relates directly to hardware and the installer just _assumed_ that their system was totally compatible. Every windows program including the OS generally documents system requirements and expects the installer to read and understand said requirements. However, that doesn't apply to Ubuntu - It Just Works". Don't know how many times I've read that. Seems a double standard applies - if Windows fails install due to hardware incompatibility that's acceptable - if Ubuntu fails due to hardware incompatibility "It Sucks". A lack of understanding and investigation on an installers part, doesn't equate IMHO to a issue with Ubuntu.

Sorry for being so blunt. I'll endeavor to be more sympathetic (to those that can't read or chose not to) in the future. Well, I will try.

well said sir! when i first gave ubuntu a try, i had many issues with the video card i was using, and was only able to boot into safe mode, and was about to give up when i stumbled upon the forums here, and after about 5 mins of searching, the issue was just the video card itself (something with that specific chipset apparently), swapped it for a newer video card, bam, worked like a charm.

---

### Post by trekguy on 2008-11-24
A friend of mine wiped his hard drive, and wanted his XP reinstalled, and he also wanted to try the Ubuntu OS that I was bragging up.  So, doing XP FIRST, I spent most of a day on the XP install, including downloading service packs, etc...his disk came with SP 1.  Then, when that was done, I spent about 40 minutes installing Hardy Heron. :biggrin:

---

### Post by Hyper Tails on 2008-11-24
Yea I hated installing vista
because:
1) it wanted the entire harddrive to itself (F-ing hog)
2) I had to delete ubuntu :'(

Install vista first or vista will be mad

---

### Post by Ripfox on 2008-11-24
> **3rdalbum said:**
> People don't reinstall Windows; they use a system restore CD that merely re-images their hard drive to the state it was when they got the machine.

I don't know how people manage to install XP.

Dude, it's no easy task to be taken for granted. :lolflag::lolflag::lolflag:

---

### Post by starcannon on 2008-11-24
I agree, and have really felt this way about things truly and completely for quite some time now; arguably it has really been very evident since Ubuntu 7.10, with each new release becoming easier. I too recently did a windows xp install on a fairly standard laptop, just getting the sata drivers was a nightmare, I almost gave up, it literally took me an entire weekend to track down all the windows xp drivers for the laptop, but eventually I pulled it off. The same laptop running Ubuntu 8.10, 45minutes to install and a quick 5 minutes to set up the nvidia 8400m gs video card (I like the drivers from the nvidia website best so it takes me a quick couple downloads); everything though truely works outta the box under Ubuntu. Vista, oy vey, 6 hours to install, then post install requires downloading every driver for every chip/set on the motherboard. 
> **plantje said:**
> A bit of a different story...

I am using Ubuntu for a while now. I really love it. Last week I decided to install XP next to Ubuntu to be able to play fallout3. Let the horrors start...

I cleared a partition for windows

Booting from XP CD. It didn't recognize my SATA hard disk. Had to search the driver on the internet, inject them into a XP CD image using 3th party tool, and create a new CD. Impossible for newbie...but let's go on...

First I tried to install it next to my existing Ubuntu. This doesn't work, XP messed up the Linux drive. It's not only the boot loader. Got so fed up that i decided to reinstall both XP and Ubuntu.

Ok, I got windows installed! Initially video, network and sound are not working. This is a bit of a problem as i don't have a network driver somewhere... I really thought a network driver would be included for a standard 3com  card. Anyway used my girlfriends laptop to download the driver and installed it. Nvidia video card driver was easy.  Sound card driver took a bit of searching on the internet. Although it was 180 MB package(!!!) with a lot of extra junk.

As i don't really like it when my printer is turned on and windows keeps trying to explain me it is broken because it couldn't find drivers, i decided to install this one as well. This is a HP Photosmart C4280. This driver again too large, 40 MB!  In the end I got it working. Although using this horrible software to print/scan something is a pain. 
BTW it seems the actual scanning is twice as fast in Ubuntu then in windows using the manufacture drivers.

For fun I also wanted to test my USB WIFI connection. Downloaded the drivers and it simply does NOT work. Even with the original driver I can't seem to get it working. It auto disconnects every time! I gave up!

Next thing Ubuntu. Installing is easy, next, next, next. And it is done.

Sound, network, printer and video work out of the box. get a message that there is a proprietary driver for my Nvidia, I accept.

WIFI doesn't work out of the box after a bit of searching on the internet I got it working.

Installing windows took me almost a day, Ubuntu an hour.

I am 100% sure that if people spent the same time on Ubuntu as on Windows they will love Ubuntu more. Tried to learn my girlfriend using Ubuntu, she actually likes it. I remember a friend of her coming over asking 'What a strange windows is this' she said 'No it's Linux, just like windows but a bit easier'. I really liked that :-)

---

### Post by Tamlynmac on 2008-11-24
I'm so glad to hear I'm not the only person that's spent hours finding and installing Windows drivers. For the longest time I actually thought it was just my own ineptitude. As my wife often loving points out - I'm not the sharpest tool in the shed. But as many others I've found installing Ubuntu to be simple and for the most part painless. 

The sad part is now I no longer have the excuse of remaining in the (peaceful and quiet) computer room for hours cleaning up Windows (viruses, spyware, registry issues, etc.). I actually had a small TV in that room and watched ball games while waiting for our systems to complete these processes. Ever since we installed Ubuntu her honey-do list has substantially grown in size. Hmmm For every positive in life there seems to be a negative.:lolflag:

---

### Post by SunnyRabbiera on 2008-11-25
Yeh installing windows XP is such a pain, sure it might seem that XP has great support because it is pre installed but when you have to install it from scratch...
I rather spend 2 days coding Gentoo's older builds sometimes!

---

### Post by sneeks on 2008-11-25
> **SunnyRabbiera said:**
> Yeh installing windows XP is such a pain, sure it might seem that XP has great support because it is pre installed but when you have to install it from scratch...
I rather spend 2 days coding Gentoo's older builds sometimes!

you are a masochist !!!!!
even i wouldn't attempt that..

---

