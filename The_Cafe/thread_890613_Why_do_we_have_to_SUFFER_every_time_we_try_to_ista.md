---
title: "Why do we have to SUFFER every time we try to istall Ubuntu on brand new hardware"
date: 2008-08-15
forum: The Cafe
---

### Post by gdp77 on 2008-08-15
I recently set up a rig for a friend of mine (he wanted windows XP). The hardware was Asus P5Q (P45) and AMD 4850. (the rest don't matter). After I completed the XP installation, I tried to also install Ubuntu, so he could try it.

My tries were hopeless...

There is not one piece of silicon on asus P5Q that can work with Ubuntu. sata problem, marvell problem, atheros problem (and of course 4850 problem). Not even live cd could work. I quit trying and I am asking the community:

Why Ubuntu (and linux distributions) can't boot using a "compatibility mode" when drivers are not available? I mean, how can windows XP (released 2002) boot with 2008 hardware and Ubuntu 8.04 (released some months ago) can't install with hardware released last month?

We always blame the companies that do not release drivers for linux, but windows CAN BOOT without drivers (since we install them later). Why can't linux do something similar?

---

### Post by abgemacht on 2008-08-15
You know that blue screen that appears when you first put in the Windows install disk?  That's the disk installing the necessary drivers to boot.

---

### Post by TheSlipstream on 2008-08-15
> **gdp77 said:**
>  I mean, how can windows XP (released 2002) boot with 2008 hardware and Ubuntu 8.04 (released some months ago) can't install with hardware released last month?

Wait...are you saying you did an entirely vanilla from-the-XP-install-disk and it worked perfectly? I didn't realize that was possible. I was under the impression that manufacturers or users had to put in drivers in order to make it work 100%. Which they do. Try a new, clean XP install and see if your printer works. See if your webcam works. See if your wireless card works. Now try that with Linux. Sure, maybe it won't work sometimes, but it will more often, and it's a short walk to Google and documentation.

---

### Post by gdp77 on 2008-08-15
Of course I need to install drivers AFTER installation. But at least I can install XP. The problem with linux is that u have to wait for new kernel. 

Try to install Ubuntu on a Asus P5Q (no1 mobo developer worldwide- p45) and u will understand what I am talking about. Ubuntu is good when u have mainstream 1-year-old hardware

---

### Post by SunnyRabbiera on 2008-08-15
Yes but blame the hardware makers for being pro MS

---

### Post by TheSlipstream on 2008-08-15
> **gdp77 said:**
> Of course I need to install drivers AFTER installation. But at least I can install XP. The problem with linux is that u have to wait for new kernel. 

Try to install Ubuntu on a Asus P5Q (no1 mobo developer worldwide- p45) and u will understand what I am talking about. Ubuntu is good when u have mainstream 1-year-old hardware

It won't even start? That's a bit weirder. I'm assuming there's nothing absolutely unique about this computer -- y'know, seeing as being new doesn't make the hardware undetectable -- so I have to question the integrity of your Linux install. Suggestion: Re-install, and make sure it's done right. If it still fails, chime back in.

---

### Post by abgemacht on 2008-08-15
> **gdp77 said:**
> Of course I need to install drivers AFTER installation. But at least I can install XP. The problem with linux is that u have to wait for new kernel. 

Try to install Ubuntu on a Asus P5Q (no1 mobo developer worldwide- p45) and u will understand what I am talking about. Ubuntu is good when u have mainstream 1-year-old hardware

You aren't listening to what people are saying.  Windows loads up drivers BEFORE the install.  They can only do this because the HW manufactures supply them with it.

I'm not saying that Ubuntu will work on your box, I'm just saying it isn't their fault if it doesn't.

Here's a perfect example of what happens when Windows doesn't have drivers:

[http://ubuntuforums.org/showthread.php?t=888260]("http://ubuntuforums.org/showthread.php?t=888260")

---

### Post by starcannon on 2008-08-15
So there is a laptop or 3 out there that are designed for, and only for MS products. I think the reality is that if Hardware Developers refuse to greet linux with open arms, then considering the sheer amount of hardware out there, linux can only be expected to quickly assimilate hardware that follows some sort of standard.

Perhaps someday that particular laptop will be assimilated, perhaps it won't. My lesson learned was to make note of the model, avoid it like I do SiS and VIA, and continue buying the other 99% of the hardware out there that "just works".

---

### Post by LaRoza on 2008-08-15
> **gdp77 said:**
> I recently set up a rig for a friend of mine (he wanted windows XP). The hardware was Asus P5Q (P45) and AMD 4850. (the rest don't matter). After I completed the XP installation, I tried to also install Ubuntu, so he could try it.

What? The rest is what matters!

> 
Why Ubuntu (and linux distributions) can't boot using a "compatibility mode" when drivers are not available? I mean, how can windows XP (released 2002) boot with 2008 hardware and Ubuntu 8.04 (released some months ago) can't install with hardware released last month?

If the specific drivers are not available, ubuntu does fall back on vesa or default drivers. However, hardware doesn't work on them for a reason very well.

You are asking really silly questions. Windows XP works because the hardware is built to support Windows XP and Windows Vista (most likely, very few hardware vendors will support Vista only).

Ubuntu 8.04 doesn't support it because it was released a few months ago. How can Ubuntu support hardware that exists after it was made? You said so yourself right there!

> 
We always blame the companies that do not release drivers for linux, but windows CAN BOOT without drivers (since we install them later). Why can't linux do something similar?

You want to know why? If thousands of very skilled programmers can't do this kind of magic, your griping about the lack of magic software isn't going to change anything ;)

Hardware that doesn't natively support Linux takes time after its release for drivers to be made. Does this not make sense?

---

### Post by Polygon on 2008-08-15
This is the first time ive read of a computer that woulden't actually BOOT because of new hardware. Usually people with like new vid cards or motherboards they dont have the correct drivers so stuff doesnt work, but at least it boots......

---

### Post by LaRoza on 2008-08-15
> **Polygon said:**
> This is the first time ive read of a computer that woulden't actually BOOT because of new hardware. Usually people with like new vid cards or motherboards they dont have the correct drivers so stuff doesnt work, but at least it boots......

The bios on laptops can cause problems with a bunch of things.

---

### Post by tbroderick on 2008-08-15
> **SunnyRabbiera said:**
> Yes but blame the hardware makers for being pro MS

But the PQ5, if I'm not mistaken, comes with Express Gate, so it has Linux pre-installed. I wouldn't call that 'pro MS'.

---

### Post by zmjjmz on 2008-08-15
Your title is a bit dramatic.
"we" although it means you and your friend, implies the community as a whole, regardless of whether or not they experience these problems.
"every time" is a bit odd, because this definitely doesn't happen _every_ time somebody buys a new mobo.

But I'm still surprised that Ubuntu doesn't work.
The PQ5 already has Express Gate pre-installed, so obviously the mobo is compatible with Linux.

---

### Post by mrsteveman1 on 2008-08-15
I've seen XP refuse to install because it didn't have drivers as well. In fact, when i got this thing the SATA chipset was newer than XP SP2, so there wasn't a driver for it on the CD. I had to slipstream one in just to get the thing to write the installation to the hard drive.

However, because the ubuntu livecd is also an actual installation, its quite a bit more than just an installer. It needs to have drivers for everything just to get to the main screen where you can open the installer.

If you like you can use the alternate CD which is more like the XP installer.

As for who is pro MS, the hardware makers appear to be allowing MS to include specific drivers on the install CDs, especially with Vista. That's because MS has so much influence, not because they love MS. There are some companies who have granted Canonical the rights to distribute binary firmware on the ubuntu CD as well, and i suspect that if asked a lot of them might allow Canonical to distribute binary drivers too, but thats a big no-no in the FOSS world at the moment, though Ubuntu is more sane about it than most.

---

### Post by ilrudie on 2008-08-15
Make sure you verify the checksum of the ISO you downloaded and verify that the disk burned perfectly.  I have seen a few cases where people said Ubuntu was junk and wouldn't load and the reason was they had a messed up ISO or a burn error.  Also you could try the alternate install cd as mentioned above.  It may work better for you.

---

### Post by gdp77 on 2008-08-15
when u find me a SINGLE person that installed Ubuntu (dual boot with win-there is a reason I specify this) on a P5Q then I admit I am wrong. 

In order to see SATA you must change SATA setting in BIOS but then Win won't boot. (and i need win for high end games)

Assuming that u solve first problem, then u have to deal with the **new** marvell controller. (haven't found anything close to a solution yet)

Assuming u solve problems above then u have to deal with **new** Atheros chipset.

Maybe I am overreacting because I am frustrated, but the truth is that P5Q is incompatible with current Ubuntu version. I have to wait 8.10 (hopefully)

---

### Post by zmjjmz on 2008-08-15
> **gdp77 said:**
> when u find me a SINGLE person that installed Ubuntu (dual boot with win-there is a reason I specify this) on a P5Q then I admit I am wrong. 


[http://forumubuntusoftware.info/viewtopic.php?f=8&t=1345&start=0#p12479](http://forumubuntusoftware.info/viewtopic.php?f=8&t=1345&start=0#p12479)

---

### Post by mrsteveman1 on 2008-08-15
Doesn't every ubuntu CD actually HAVE an option at boot time (As in, during ISOLINUX bootup) to load vendor drivers? I'm positive iv seen it recently.

I don't however know what the CD expects to find and where, like a flash key, and perhaps a deb package or just a .ko file? duno.

I think Canonical should push harder on that front, and DEFINITELY the Ubuntu forum and website should be leading people in the right direction as to how to add new drivers to the install in this way, since someone went to the trouble to set it all up apparently.

Perhaps a wiki page of some kind, with instructions on what one has to do to put the drivers on a flash key or something so the CD can grab them.

---

### Post by dragos240 on 2008-08-15
Doesn't make me suffer! :p

---

### Post by Dremora on 2008-08-15
> **TheSlipstream said:**
> Wait...are you saying you did an entirely vanilla from-the-XP-install-disk and it worked perfectly? I didn't realize that was possible. I was under the impression that manufacturers or users had to put in drivers in order to make it work 100%. Which they do. Try a new, clean XP install and see if your printer works. See if your webcam works. See if your wireless card works. Now try that with Linux. Sure, maybe it won't work sometimes, but it will more often, and it's a short walk to Google and documentation.

I call BS there, XP SP3 doesn't even have drivers for my SATA drives, my RAID controller, my network interface, my wifi, my video card (beyond unaccelerated 2d), or sound.

You either have to Nlite it and integrate all your drivers, or have every driver disc for everything in the system that XP can't handle.

It's not fun trying to make XP work if all you have is the XP disc, even basic stuff won't work, like the setup program most of the time. :lolflag:

---

### Post by Dremora on 2008-08-15
> **gdp77 said:**
> Of course I need to install drivers AFTER installation. But at least I can install XP. The problem with linux is that u have to wait for new kernel. 

Try to install Ubuntu on a Asus P5Q (no1 mobo developer worldwide- p45) and u will understand what I am talking about. Ubuntu is good when u have mainstream 1-year-old hardware

[IMG]http://upload.wikimedia.org/wikipedia/commons/1/12/O_RLY.jpg[/IMG]

I'll just take back my Core 2 Extreme, my 8 GB of DDR3 RAM, my Geforce 9800 with a gig of GDDR3, etc.

Because I'm not here, and I did not type this.

I don't exist..... :lolflag:

Neither does my Gigabyte P45, :P

Should make better buying decisions next time, it's probably something wrong with your ASUS firmware.

---

### Post by Redache on 2008-08-15
I had a brand new Nvidia Nforce 650i SLI mobo when it was released more than a year ago and it worked beautifully with Ubuntu, as did the 8600 I bought as well. I think it's more to do with your hardware choice rather than the hardware itself, something else could be stopping it from booting (I have no idea what though) Maybe if you list the complete spec of the PC we could help you. 

I'm fairly convinced that the new P45's aren't earth shatteringly different from their predecessors.

+ 8 Gigs of DDR3???? Holy Crap.

---

### Post by Dremora on 2008-08-15
BTW, Linux is sometimes 3 months behind whatever Intel is doing, and Ubuntu's kernel can be 8-10 months old when they make a new release (as is the case with most distros)

Try 2.6.26, you could use it in Intrepid Alpha 4, or build it yourself and make a kernel package?

---

### Post by Dremora on 2008-08-15
> **Redache said:**
> I had a brand new Nvidia Nforce 650i SLI mobo when it was released more than a year ago and it worked beautifully with Ubuntu, as did the 8600 I bought as well. I think it's more to do with your hardware choice rather than the hardware itself, something else could be stopping it from booting (I have no idea what though) Maybe if you list the complete spec of the PC we could help you. 

I'm fairly convinced that the new P45's aren't earth shatteringly different from their predecessors.

+ 8 Gigs of DDR3???? Holy Crap.

DDR3 1900

I still have two slots left, I could put in another 8 gigs, and will eventually, just to do it. B-)

[IMG]http://benchmarkreviews.com/images/reviews/motherboards/GA-EP45T-EXTREME/Intel-P45-Block-Diagram.png[/IMG]

---

### Post by Dremora on 2008-08-15
Oh, I saw someone mentioning Splashtop Linux, this is impossible on the Gigabte P45's as they still use BIOS, I believe ASUS does as well, the only ones using EFI on the P45 is MSI AFAIK.

You need EFI to run Splashtop Linux, cause BIOS can only access the first 1 MB of RAM, it's a design problem inherited from the PC XT. (Probably not a problem 25 years ago). :lolflag::lolflag:

Most BIOS firmwares are only 620-670 kilobytes, even though the file is 1 meg, the remaining 300-330K is dummy code, so the BIOS still has plenty of room to grow, EFI won't be needed for at least another 10-15 years, it's not a pressing problem here and now.

Anyway, BIOS is old and stupid, but it's also tested and simple, it is proven capable, where EFI can have lots more bugs and problems, because it's more complicated.

As long as I have a choice, I will use BIOS, it boots the PC, it does it's job and that's all. It doesn't try to become it's own operating system, complete with a networking stack. (sigh)

---

### Post by Dremora on 2008-08-15
Ugggh, I keep thinking of stuff, but to the Original Poster...

You do know that 32-bit Windows can only access at most, 2.5-3.2 gigs of RAM?

You need 64-bit Windows to do better, 64-bit Basic (the cheap one), has been crippled to only recognize 8 GB of RAM, including your video card and BIOS shadowed devices, so I would lose 1.5 gigs there (9.5 with my full 16 GB of RAM filled), to go to 16 GB you need Vista Premium, which would still take 1.5 gigs from me if I had the RAM maxed, cause of the video card and shadowing.

To use all my RAM, I would have to get Vista Business or Ultimate.

All your money are belong to Microsoft. ;)

I believe Linux can address 128 gigabytes for the time being, though that can be changed if needed later. ;)

---

### Post by zmjjmz on 2008-08-15
> **Dremora said:**
> 
I believe Linux can address 128 gigabytes for the time being, though that can be changed if needed later. ;)

There's been some kernel hacking on getting it to recognize a terabyte.

---

### Post by Twitch6000 on 2008-08-15
> **zmjjmz said:**
> There's been some kernel hacking on getting it to recognize a terabyte.

1 TB OF RAM DUDE WHY THE **** WOULD ANYONE NEED THAT MUCH OR HOW AT THAT O.O.[/shockedrant]

Linux surprises me everyday about what it can do.

---

### Post by Dremora on 2008-08-15
> **Twitch6000 said:**
> 1 TB OF RAM DUDE WHY THE **** WOULD ANYONE NEED THAT MUCH OR HOW AT THAT O.O.[/shockedrant]

Linux surprises me everyday about what it can do.

I'm fairly sure the Big Iron Kernel can already do this.

I may be wrong...

I know Big Iron used to be an option on Ubuntu Server, but they said if you could easily count how many processor cores were in your machine, don't use it. :lolflag:

---

### Post by zmjjmz on 2008-08-15
Actually, IBM Blue Gene/L has a good 17TB of RAM.

Also, 20 years from now you will look back at that post and laugh at how clueless you were, then turn your attention back to the Augmented Reality version of Crysis 7 running at 10690p which is running on your System76 Paramecium (they ran out of multi-cellular organisms) with 4PB (Petabytes) of RAM and a 10000-core processor clocked at 2THz running in a i686 emulator on ReactOS 9.0.

---

### Post by Dremora on 2008-08-15
> **zmjjmz said:**
> Actually, IBM Blue Gene/L has a good 17TB of RAM.

Also, 20 years from now you will look back at that post and laugh at how clueless you were, then turn your attention back to the Augmented Reality version of Crysis 7 running at 10690p.

In 20 years, we'll either have holodecks, or some kind of virtual reality that you can just plug into your brain.

Of course I said that 15 years ago, but I still have 5 years left to be right. :lolflag:

---

### Post by oldsoundguy on 2008-08-15
You have to THINK on this one .. new hardware = new architecture. Since there are very few hardware manufacturers that will openly furnish their data to the Linux community because of their fear of losing MS certification, the Linux community itself has to reverse engineer in order to get that hardware to work .. (and in the main, have done a sensational job.  Albeit some makers like Broadcom and Realtec are always making changes in their buggy stuff and catching up to them is a real chore.)(Even VISTA has problems with some of those chips and requires UPDATES for the damn things to work!)
Do NOT blame the system, blame the non co-operating hardware makers.  And next time do not buy anything that contains their hardware! (Money talks!)

---

### Post by Dremora on 2008-08-15
> **oldsoundguy said:**
> You have to THINK on this one .. new hardware = new architecture. Since there are very few hardware manufacturers that will openly furnish their data to the Linux community because of their fear of losing MS certification, the Linux community itself has to reverse engineer in order to get that hardware to work .. (and in the main, have done a sensational job.  Albeit some makers like Broadcom and Realtec are always making changes in their buggy stuff and catching up to them is a real chore.)(Even VISTA has problems with some of those chips and requires UPDATES for the damn things to work!)
Do NOT blame the system, blame the non co-operating hardware makers.  And next time do not buy anything that contains their hardware! (Money talks!)

Gee, that must be why Intel and AMD are the ones writing all the drivers to make their chipsets work.

Gosh, they're so evil and wicked, I'd rather trust this mostly fictitious community of benevolent driver writers that have problably never written a line of code for the features of my motherboard chipset.

Seriously though, don't look a gift horse in the mouth, or we'll be back to circa 2000 where Linux only worked if all the moons in the universe aligned and shone down on your magical hardware that happened to be identical to a Linux developer's. :lolflag:

People don't remember how terrible Linux used to be, to try and run on a factory built PC, if you even managed to get it to boot at all, you were lucky. :lolflag:

---

### Post by psusi on 2008-08-15
Man I wish the clueless fanboys would just keep quiet, it really just is a disservice to the community.  You all need to read the OP over again and notice that he points out that Windows also does not have the new drivers to run the new hardware, yet it somehow manages to at least boot up and let you install the drivers.  His question of how Windows can do this and Linux can't ( sometimes ) is legitimate.

The answer to that question is that Windows and any given specific Linux kernel ( there are a billion of them, stemming from all of the different kernel versions times the many different configurations they were built with ) use the hardware in subtly different ways.  Likewise there are a million different bits of hardware out there that have quirks that screw them up and fail to comply with standards in some way or another.  That leads to some combinations of quirky hardware that will get hosed up even when used in a way they should support.

Manufacturers make sure that they don't have any quirks that kill the one or two builds of Windows that they have to worry about before they release it, but sometimes there are other quirks that get triggered by the slightly different way some specific Linux kernel operates.  That is why SOME new hardware falls down and goes boom when you try to boot a Linux system on it.  Most of the time though, it doesn't fall on its face and you manage to do at least as well, if not better, than a 4 year old Windows release.

Oh, and I used to develop ReactOS several years ago.  I wrote some core parts of the kernel and low level libraries before I decided that the entire Windows philosophy is flawed and Linux is the future, and have been contributing to Ubuntu and other open source projects when I can find the time.

---

### Post by kernelhaxor on 2008-08-15
Interesting points made by several people.  I guess hardware manufacturers are to take most of the blame.

So, what is the best solution?  To stay away from latest hardware?  (I personally was going to buy a P43 mobo with 4850, now I know I should wait)

---

### Post by Dremora on 2008-08-15
> **psusi said:**
> Man I wish the clueless fanboys would just keep quiet, it really just is a disservice to the community.  You all need to read the OP over again and notice that he points out that Windows also does not have the new drivers to run the new hardware, yet it somehow manages to at least boot up and let you install the drivers.  His question of how Windows can do this and Linux can't ( sometimes ) is legitimate.

The answer to that question is that Windows and any given specific Linux kernel ( there are a billion of them, stemming from all of the different kernel versions times the many different configurations they were built with ) use the hardware in subtly different ways.  Likewise there are a million different bits of hardware out there that have quirks that screw them up and fail to comply with standards in some way or another.  That leads to some combinations of quirky hardware that will get hosed up even when used in a way they should support.

Manufacturers make sure that they don't have any quirks that kill the one or two builds of Windows that they have to worry about before they release it, but sometimes there are other quirks that get triggered by the slightly different way some specific Linux kernel operates.  That is why SOME new hardware falls down and goes boom when you try to boot a Linux system on it.  Most of the time though, it doesn't fall on its face and you manage to do at least as well, if not better, than a 4 year old Windows release.

Oh, and I used to develop ReactOS several years ago.  I wrote some core parts of the kernel and low level libraries before I decided that the entire Windows philosophy is flawed and Linux is the future, and have been contributing to Ubuntu and other open source projects when I can find the time.

I already told him, try Linux 2.6.26, it's semi easy to get Intrepid running.

Intel has added a ton of drivers and such since 2.6.24

Also, I read the ReactOS FAQ, they've spent over 10 years or however long and still have a pre-alpha that looks like it will continue going nowhere.

They make arguments for the NT kernel vs. Linux on security.

They would be better served by giving up, Microsoft has thousands of programmers, ReactOS maybe has a couple dozen, they're not only not keeping up, they're having to go back and fix just as much of their code as they add in any given release.

---

### Post by gdp77 on 2008-08-16
> Man I wish the clueless fanboys would just keep quiet, it really just is a disservice to the community. You all need to read the OP over again and notice that he points out that Windows also does not have the new drivers to run the new hardware, yet it somehow manages to at least boot up and let you install the drivers. His question of how Windows can do this and Linux can't ( sometimes ) is legitimate.

That's exactly my point. Thank you!!!

The fanboys here should realize that I am an Ubuntu fan. Due to lack of time I do not help the community by developing, but I have helped at least 50-60 users (here in Greece) to switch to Ubuntu from windows. My frustration comes from the fact that I have no way to install Ubuntu at my friend's system (the one with Asus P5Q and 4850). It simply is a no go with 8.04.

---

### Post by Dremora on 2008-08-16
> **kernelhaxor said:**
> Interesting points made by several people.  I guess hardware manufacturers are to take most of the blame.

So, what is the best solution?  To stay away from latest hardware?  (I personally was going to buy a P43 mobo with 4850, now I know I should wait)

Well, latest hardware is probably only going to be well supported with a recent kernel, Hardy's kernel is nearly 10 months old now I think, some stuff has been backported, but there's still thousands of patches that it doesn't have.

It's always a trade off between stability and new features, if you can get away with using the stable kernel, you should.

I'd say Intrepid is practically guaranteed to support that board even if Hardy doesn't.

Or, use your own kernel...

---

### Post by PryGuy on 2008-08-16
> Why do we have to SUFFER every time we try to istall Ubuntu on brand new hardwareExcuse me? Almost all the time everything works fine for me on new machines. I'm a system administrator, mind you. You generally can have problems with AMD/ATI hardware. Yet the fact that you do not have to install additional drivers in most cases greatly reduces installation time.

---

### Post by SomeGuyDude on 2008-08-16
I'm using Ubuntu because I had no errors. Every piece of hardware works on my machine except the little wireless LED.

Anyway, if you want to talk fun, try downgrading from Vista to XP. Or putting Vista on an XP machine that isn't "Vista ready". Oh yeah, that's right, it will never, ever work.

---

### Post by Dremora on 2008-08-16
> **PryGuy said:**
> Excuse me? Almost all the time everything works fine for me on new machines. I'm a system administrator, mind you. You generally can have problems with AMD/ATI hardware. Yet the fact that you do not have to install additional drivers in most cases greatly reduces installation time.

I'm really pretty sure that it has more to do with running a kernel that might be 8-12 months old than any particular fault of Intel, AMD, whoever...

---

### Post by mrsteveman1 on 2008-08-16
> **Dremora said:**
> 

People don't remember how terrible Linux used to be, to try and run on a factory built PC, if you even managed to get it to boot at all, you were lucky. :lolflag:

hmm that wasn't a haiku but it was...something :D

---

### Post by mrsteveman1 on 2008-08-16
As far as i know, even Windows XP, Vista and every other common OS can't magically interact with new drive chipsets in native SATA mode without a driver being on the installer cd. Some chipsets (or bios?) can be put into emulation mode but i believe that just emulates an older IDE chipset it DOES have the driver for.

This is always going to be a problem, it's a problem with XP all the time, and it will probably be a problem with Vista soon as well.

It really is this simple: New hardware requires new drivers, which don't come on the ________ installer cd until a new one is released. Fill in the blank with your choice of OS and it will be true in most if not all cases.

---

### Post by Hilipatti on 2008-08-16
What are you talking about? :P

I bought my new computer this spring and I had 0 problems with Ubuntu, everything worked straight out of the box (bought it in parts though). You only have to check linux-compatibility first before you buy anything and if you do, you'll have zero problems. Plus this helps because you can vote for linux-support with your wallet..

It's kind of worth noting that I also bought pretty much bleeding edge parts.
And I also bought pretty much mainstream parts, not some unknown-"linux manufacturer" parts.

---

### Post by Marshal0505 on 2008-08-16
My Ubuntu works nearly flawlesly with my P5Q PRO and i'm extremely pleased with this board.Only trouble I had was with the lan driver.But nothing google can't fix.

---

### Post by Warpnow on 2008-08-16
Guys!

Why do we have to SUFFER every time we try to install a new video game.

I mean, shouldn't companies like ID and Interplay design their games to WORK with OUR hardware! Christ!

/me is trying to figure out why Doom 3 won't play on his pentium 2 250mhz w/128mb of pc100 RAM and an intel 4mb video card.

:lolflag:

---

### Post by newguy1950 on 2008-08-17
> **gdp77 said:**
> I recently set up a rig for a friend of mine (he wanted windows XP). The hardware was Asus P5Q (P45) and AMD 4850. (the rest don't matter). After I completed the XP installation, I tried to also install Ubuntu, so he could try it.

My tries were hopeless...

There is not one piece of silicon on asus P5Q that can work with Ubuntu. sata problem, marvell problem, atheros problem (and of course 4850 problem). Not even live cd could work. I quit trying and I am asking the community:

You really should have researched before you bought. After learning it the hard way (JMicron IDE Controller), I do that every time now. Of course, I got screwed this time, too, because the Intel ICH10R chipset wouldn't work okay (cost me about 20 hours of work to find a good solution), but I checked sound and network chips before and they both work on 2.6.26 without a fuss so far. Treat it is as a learning experience.

> **gdp77 said:**
> Why Ubuntu (and linux distributions) can't boot using a "compatibility mode" when drivers are not available? I mean, how can windows XP (released 2002) boot with 2008 hardware and Ubuntu 8.04 (released some months ago) can't install with hardware released last month?

We always blame the companies that do not release drivers for linux, but windows CAN BOOT without drivers (since we install them later). Why can't linux do something similar?

Curious. I have an ASUS P5Q-E, and the live CD works. It's a pain in the [COLOR="Black"]a[/COLOR]ss to get it installed right (SATA issues with ICH10R / P45, see [http://ubuntuforums.org/showthread.php?t=890604&highlight=p5q](http://ubuntuforums.org/showthread.php?t=890604&highlight=p5q) if you want to find out how I did it). Though mine is an Intel system.

As far as your question goes, why you have to suffer every time you install Ubuntu: You (or he) don't. Don't use it.

Stop recruiting people that way. It will never work, they'll just [COLOR="Black"]b[/COLOR]itch and moan and blame you for their system not working. If they can't install it themselves, they can wait another 6 months for a new release.

---

