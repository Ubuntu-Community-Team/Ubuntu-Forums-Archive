---
title: "The Linux Struggle"
date: 2024-07-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2024-07-01
I've been a "Linux" user for quite a while now.  My first delve into Linux was in 2008 with Ubuntu 8.04 "Hardy Heron."  I stuck with Ubuntu for a few years, then changed over to Kubuntu at 12.04 "Precise Pangolin".

Regardless... over the years, I have always had to dual boot Windows, due to some software or media that I needed to run.

I have been a Graphic Designer for over 20 years, and that industry uses Adobe.  So, I have a Windows Partition to be able to use that software.

Secondly, and the reason I am continuously plagued by Windows, is that I am a gamer.  Not a hard-core online gamer.  Fairly casual gamer.  I play single-player games from time to time.  I have also watched the game industry change over the years.  When Steam pushed foward with Proton, I was very impressed.  Most of my Steam library became usable in Kubuntu with just the flip of a swtich...  pretty nice.

Anyway, that's the backstory... and hopefully it will explain why I see these things:

I would love to switch ENTIRELY to Kubuntu, but there are just too many things that don't quite work well.

These are general Linux issues, not just Kubuntu:

1.  In order to run my Adobe CS6 in Linux, I have to use a virtual-machine, and run Windows... then I'm not running directly on hardware, I'm virtualizing, and the performance mostly sucks.

2.  Games, even with Proton, don't run as well as they do in Windows...  at least, the games I want to play.  Currenly, I enjoy Skyrim (SE-AE, with many mods), Horizon Zero Dawn, and Marvel's Guardians of the Galaxy, to name a few.  The performance difference between Windows and Kubuntu is around 20fps (Ryzen HX5900 CPU and 6600M GPU).  That's a pretty major difference... enough to reboot.

3.  Little things like hardware acceleration for video playback in browsers.  YouTube uses CPU and not GPU.  I just started to use Nvidia GeForce Now, to play games.  However, with the snap app, I can only get 60fps, whereas in Windows I can use GeForce Now for 120fps.

4.  Steam downloads are MUCH slower in Kubuntu.  I get 18 mbps normally, with a little mod (found here: [https://www.reddit.com/r/linux_gaming/comments/16e1l4h/slow_steam_downloads_try_this/?rdt=51152]("https://www.reddit.com/r/linux_gaming/comments/16e1l4h/slow_steam_downloads_try_this/?rdt=51152")) I can get the speed up to ~350mbps.  In Windows, I can get 1.9 - 2.0 Gbps without any fixes.

So, I am aware that these problems are not bugs or issues with the Linux OS's.  I believe most of these issues have to licensing codecs (like h.265/AV1) for hardware usage.  I also know that Proton/Wine is a wrapper and can cause extra steps between software and hardware, which can cause slow-down.

I also understand that there is not a native app for GeForce Now, so that the higher-end features may not be available.

The Steam problem is more than likely Steam's direct issue... which, you would think would be addressed, seeing as how they want to make their Steam Deck (Linux) work the best as possible.

So, I have really tried over the course of 20+ years to drop Windows entirely, but it feels like there is always something that causes me not to.

Since I am apparently not going to give up these things, what can be done?

---

### Post by aljames2 on 2024-07-01
Hi Shibblet, I do not have a need for the Adobe products since what I do in that area has a suitable Linux alternative. Althouth, I do pay Adobe for my daughter's use of their suite for her college work in graphic design.

For the gaming, I have found no solution to mimic my gameplay experience on the Windows box.  I do not dual boot, I just never liked the idea of welcoming Windows on my Linux hardware. So, I have a Intel 9600k w/Nvidia GTX 1070 video card.  This box has W10 with Steam games only, nothing more.  I still do some multiplayer on occassion with some old friends that I met in the late 90's when I was in a Unreal Tournament gaming clan, and we still stay in contact some.  I think the multiplay game now we play on occassion is called Destiny 2. Anyhow, I keep a windows box around just for this.

I thoroughly enjoy doing everything else in my computing life on Linux.  I don't see this "hanging on to" a Window box as a crutch, or as a Linux weakness. My perspective is the opposite, that it is a weakness of Windows, that it has lost my total & complete interest as a useful OS to me personally. I don't trust it. I use the W at work but only because that is what corporate puts in front of us. Funny, is that I have to call IT from time to time because I forgot where some stuff is in the Windows ecosystem. Thankfully, I am an independent contractor and paid commission and I am good at what I do, so they can't hold that over.

If Linux Steam gets better and if I still have the interest, then I guess that old box will be promoted to be a Linux server for me or someone else in the family for something..

Good luck!

---

### Post by VMC on 2024-07-01
I never gave it a second thought dual booting Linux, Windows. They both have their values. Some programs just run better, if not best using Windows. Why fight it. I find Wine useless. Tried it, several things about it I didn't like. I will most likely always dual boot Linux/Windows.

In my thinking, its not one-size-fits-all.

---

### Post by Irihapeti on 2024-07-01
I've been a Linux enthusiast for getting on for 20 years and spend most of my computing time using it, but I have a Windows VM as well. The reason? I was doing proof-reading for international students and I had to be able to guarantee compatibility if I was going to feel OK about asking for payment. Open/LibreOffice is fine for simpler documents, but not for some of the things these people were doing, and the last thing you need is to find something missing when you're half an hour from submission deadline.

Use what works for you, and don't worry about the "shoulds". There are no bonus points for being Windows-free (or Mac-free or whatever else it is you need to use).

---

### Post by currentshaft on 2024-07-01
> **Shibblet said:**
> 
1.  In order to run my Adobe CS6 in Linux, I have to use a virtual-machine, and run Windows... then I'm not running directly on hardware, I'm virtualizing, and the performance mostly sucks.


Use GIMP and Inkscape instead.

> **Shibblet said:**
> 
2.  Games, even with Proton, don't run as well as they do in Windows...  at least, the games I want to play.  Currenly, I enjoy Skyrim (SE-AE, with many mods), Horizon Zero Dawn, and Marvel's Guardians of the Galaxy, to name a few.  The performance difference between Windows and Kubuntu is around 20fps (Ryzen HX5900 CPU and 6600M GPU).  That's a pretty major difference... enough to reboot.


What troubleshooting have you done? My experience is the opposite: games under Proton run much better than they had on Windows.

> **Shibblet said:**
> 
3.  Little things like hardware acceleration for video playback in browsers.  YouTube uses CPU and not GPU.  I just started to use Nvidia GeForce Now, to play games.  However, with the snap app, I can only get 60fps, whereas in Windows I can use GeForce Now for 120fps.


Works fine in the browsers on my Ubuntu workstation, Chrome and Ubuntu. I can play 4K videos without an issue on my 65" TV.

> **Shibblet said:**
> 
4.  Steam downloads are MUCH slower in Kubuntu.  I get 18 mbps normally, with a little mod (found here: [https://www.reddit.com/r/linux_gaming/comments/16e1l4h/slow_steam_downloads_try_this/?rdt=51152]("https://www.reddit.com/r/linux_gaming/comments/16e1l4h/slow_steam_downloads_try_this/?rdt=51152")) I can get the speed up to ~350mbps.  In Windows, I can get 1.9 - 2.0 Gbps without any fixes.


Not a Linux issue, something is wrong with your configuration.

> **Shibblet said:**
> 
So, I am aware that these problems are not bugs or issues with the Linux OS's.  I believe most of these issues have to licensing codecs (like h.265/AV1) for hardware usage.  I also know that Proton/Wine is a wrapper and can cause extra steps between software and hardware, which can cause slow-down.


What facts lead to this conclusion? Can you share them here?

It is true effort is needed to adapt to Linux full-time. Not everyone has the discipline for it. But the result is rewarding, worthwhile and possibly exceeding most requirements.

---

### Post by coffeecat on 2024-07-02
Thread moved to ULOS

---

### Post by Shibblet on 2024-07-02
> **currentshaft said:**
> Use GIMP and Inkscape instead.
While GIMP is a decent replacement for Photoshop, and Inkscape is an "semi-acceptable" replacement for Illustrator... There is no decent replacement for InDesign.
Plus, you need to understand, I am well trained in Adobe software, and switching to these programs turns into more of a "why can't I do what I normally do..." instead of a "Let's get this done," mentality.

> **currentshaft said:**
> What troubleshooting have you done? My experience is the opposite: games under Proton run much better than they had on Windows.
Why bother troubleshooting?  That's just more time wasted.  I can just reboot my PC into Windows and run the game.

> **currentshaft said:**
> Works fine in the browsers on my Ubuntu workstation, Chrome and Ubuntu. I can play 4K videos without an issue on my 65" TV.
Does not work well for me.  I can play 1080p content with no issues.  CPU goes to about 6%-8%.  4K causes my CPU to hit 50%-60% and playback is choppy.  In either situation, the GPU doesn't do a thing, in Kubuntu.  In Windows, CPU rests at 1%-2%, and the GPU jumps up to about 15%-20% on 4K playback

> **currentshaft said:**
> Not a Linux issue, something is wrong with your configuration.
If you know an actual solution to this, there is an entire community of people who would LOVE to know.  Please share!

> **currentshaft said:**
> What facts lead to this conclusion? Can you share them here?
Absolutely.  Aside from the situations notated above, I have a prime example:  Skyrim (SE-AE).  Works great out of the box on Steam.  But I don't want to just play Skyrim, I want to mod it.  In Windows, I use ModOrganizer 2, and I install the program and start dropping the mods in.

In Kubuntu, there is an automated way to setup ModOrganizer with Steam (here: [https://github.com/rockerbacon/modorganizer2-linux-installer]("https://github.com/rockerbacon/modorganizer2-linux-installer")), and it works.  But once you install it, ModOrganizer doesn't function as well as it does in Windows.  There's some performance and stability issues.  Even then, once you get your mods all set up, and run Skyrim, the game performance is around 75% of the capability in Windows, using the exact same mods.

> **currentshaft said:**
> It is true effort is needed to adapt to Linux full-time. Not everyone has the discipline for it. But the result is rewarding, worthwhile and possibly exceeding most requirements.
This is my problem.  The effort requires sacrifice, and it's difficult to make that sacrifice knowing that the things you want to do, CAN work better and more efficiently on the exact same hardware, just by using a different OS.

The "struggle" is knowing that you could fart around with the computer for who knows how long in order to squeeze some more performance out of it to play one of your games.  But how long does it take?  How much better performance would you get?  Is it worth the trade-off?  In my opinion, the best you'll be able to do is get the game running at 80%-90% of its capability, after messing around for hours... and looming over your head the entire time is that little knowledge, that you could just boot Windows and play your game with the performance it's capable of, and not have to do anything but install it and play.

---

### Post by currentshaft on 2024-07-02
Your analysis of it being a struggle is apt, but I disagree with the conclusion that it may not be worthwhile.

Consider this: you could prevent more crime by having a policeman live in your house and watch over while you sleep, but something tells me you wouldn't like the consequences.

The analogy is fitting for Windows operating systems. The only difference is Microsoft is better at obscuring, euphemizing and otherwise externalizing these true costs from the user.

Certainly one can choose to remain willfully ignorant of this reality and it is true what they say: it will bring about bliss. Or one can mire oneself in the messy and stinky world of troubleshooting Linux, the fruits of which are less certain.

Whichever path you choose, do not let others' criticisms and judgements upset you; even a modest effort to move some computing to Linux is a noble goal and worthwhile achievement.

---

### Post by 909mjolnir on 2024-07-02
When it comes down to it, buy a second computer.  
Then the problem is solved.

---

### Post by Shibblet on 2024-07-02
> **909mjolnir said:**
> When it comes down to it, buy a second computer.  
Then the problem is solved.

How?

---

### Post by TheFu on 2024-07-03
If you weren't a professional, earning a living, I'd say to bite the bullet and switch away from anything Adobe makes. They aren't your friend. They have a history of terrible management choices and clearly don't care about security.  I've been saying this for over a decade: [https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools](https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools)

But ... if you need to work with others or have lots of training/skills with "certain" products to earn your living, then how can any reasonable person ask you to change?  Whether you knew it or not, you made a choice to use Adobe - even if you didn't know any better at the time.  That choice has shaped your life. Hopefully, it has bought a house, cars, vacations, paid for kids, etc ... all those necessities that help in our modern world.  Adobe makes their software for MacOS and MS-Windows.  Every once in a while, they've made some of their products for Linux and Unix, but I think that has mostly ended at this point.  I've bought Adobe PDF-Writer for UNIX before.  We used it as a PDF printer along with CUPS rather than buy individual licenses for every desktop.  It worked well for our 6000 users and the printer (a company, not some printing device) accepted the PDFs created by Adobe. They didn't always accept PDFs created by other software.

Linux has about 2% of the desktop market share and most of those people also have some other OS, so there is little business reason for Adobe to support Linux.  The costs in doing it would eat into their profits and in the business world, profits are very important for a public company.

I've been using Linux since 1993 both at home and at work. In all this time, I haven't been able to only have a Linux system.  A few years ago, I was getting really close.  Currently, the only non-Linux programs I **need** are related to financial and tax software.  I'm lucky in that these run fine in a virtual machine.  For about 15 minutes, every other week, I boot into a Windows VM to use the software.  5 yrs ago, I had 3 other MS-Windows-only software tools and one of them was a nice little video editor.  It only worked if running directly on hardware.  I still have a Windows laptop (from 2010) just for that software, but it hasn't been booted in about 5 yrs, perhaps longer.  It hasn't moved either.  It may not boot. IDK.

If your software is critical to your income and it requires MS-Windows to run, I'd have a dedicated machine just for that and use a KVM switch to toggle a single keyboard+mouse+monitor between the systems.  I've had a 4 port KVM for use at home since the 1990s. Completely changed my life.  I get to use a nice mouse, keyboard and my main display with any of the computers here.  1 extra port on the KVM switch is currently connected to a little Pi5 SBC as I set it up to be deployed in a media room here.  Much more convenient to do that in my home office than trying to lug around that extra crap to a projector room that is mostly controlled through 10 ft TV interfaces.

Also, I would never mix my business needs with entertainment stuff, so perhaps you need 3 computers. 
a) Work, Adobe software - MS-Windows
b) Gaming PC - MS-Windows
c) Linux desktop for daily use.

The idea that you'd risk your income over running a game just doesn't make sense to me.  Plus, with 3 computers, you can swap HDDs or temporarily use one of the others should the work computer have any issue.  Don't let your income be impacted by dumb issues that are easily solved for a few hundred $$$.

---

### Post by DuckHook on 2024-07-03
> **TheFu said:**
> If you weren't a professional, earning a living, I'd say to bite the bullet and switch away from anything Adobe makes. They aren't your friend. They have a history of terrible management choices and clearly don't care about security.  I've been saying this for over a decade: [https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools](https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools)
@Shibblet

I agree with TheFu here. Decades ago, I had a lot invested in Adobe's tools too. Had taken many courses and was pretty handy with both Photoshop and Illustrator (though more familiar with QuarkXpress than Indesign). I successfully moved to the GIMP/Inkscape/Scribus triumvirate some years ago.
> But ... if you need to work with others or have lots of training/skills with "certain" products to earn your living, then how can any reasonable person ask you to change?  Whether you knew it or not, you made a choice to use Adobe - even if you didn't know any better at the time.  That choice has shaped your life.
Again, fully agree with TheFu. Though I made the move, it was painful and disruptive. I have an irrational level of cussedness that motivated me to continue when a more reasonable person would have given up. This is not a recipe for easy living.

And while the limitations of the FOSS triumvirate are usually overstated when comparing to the Adobe triumvirate, it remains true that the number and quality of proprietary plug&#8209;ins are much higher than their FOSS counterparts. This is unavoidable: there are far fewer users of FOSS than Adobe. The gulf has closed somewhat now, but it used to be yawning, and I had to employ workarounds that a professional would consider ridiculous.

If your livelihood depends on Adobe, then that speaks for itself. Case closed.

But it isn't true either that Adobe's products are irreplaceable. It just takes a lot of time, effort, commitment and frustration.

Only you can decide if that amount of blood, sweat and tears is worth it. And you shouldn't do so based on some silly notion of Linux "purity".
> The idea that you'd risk your income over running a game just doesn't make sense to me.  Plus, with 3 computers, you can swap HDDs or temporarily use one of the others should the work computer have any issue.  Don't let your income be impacted by dumb issues that are easily solved for a few hundred $$$.
Again… +1

---

### Post by Shibblet on 2024-07-03
> **TheFu said:**
> The idea that you'd risk your income over running a game just doesn't make sense to me.  Plus, with 3 computers, you can swap HDDs or temporarily use one of the others should the work computer have any issue.  Don't let your income be impacted by dumb issues that are easily solved for a few hundred $$$.

See, the problem is, I only need the one computer.  Even though I have two...  The other one runs Linux (Kubuntu) and processes data all day.  This is why I have the other one to use when I need, without disturbing the other one's data processing.

Of course, I would never give up income over gaming.  But, they both work the best on Windows.

I can run Adobe Photoshop/Illustrator/InDesign in a VM, but with bad performance.

I agree with a lot of what you are saying.  The "struggle" is that I really don't need to run Linux.  I can do everything I need to do on a Windows computer.
That being said, I would rather run Linux, but choosing to do so makes it really difficult to do the things that I want/need to do.

> **DuckHook said:**
> I agree with TheFu here. Decades ago, I had a lot invested in Adobe's tools too. Had taken many courses and was pretty handy with both Photoshop and Illustrator (though more familiar with QuarkXpress than Indesign). I successfully moved to the GIMP/Inkscape/Scribus triumvirate some years ago.
GIMP is a really good substitute for Photoshop.  Inkscape... well, it's alright.  Scribus isn't even in the same league as InDesign.

Plus, the other problem is that all of my work is saved in Adobe format.  I think Gimp can read Photoshop files, but Inkscape and Scribus cannot read Illustrator and InDesign files.  And even when they can, they don't import correctly.

> **TheFu said:**
> I've been using Linux since 1993 both at home and at work. In all this time, I haven't been able to only have a Linux system.  A few years ago, I was getting really close.  Currently, the only non-Linux programs I **need** are related to financial and tax software.  I'm lucky in that these run fine in a virtual machine.  For about 15 minutes, every other week, I boot into a Windows VM to use the software.  5 yrs ago, I had 3 other MS-Windows-only software tools and one of them was a nice little video editor.  It only worked if running directly on hardware.  I still have a Windows laptop (from 2010) just for that software, but it hasn't been booted in about 5 yrs, perhaps longer.  It hasn't moved either.  It may not boot. IDK.

And that's the problem... At best case scenario, I am still running Windows inside Linux.  I REALLY don't want to run Windows at all, and it seems I have painted myself into a corner.

I'm starting to see Linux as the software equivalent of therapy.  It feels good at first, but then you start getting to the real issues...  You have a great new UI, no bloatware, no EULA's, no one taking your personal information...  then you start to realize that is the trade-off.

Gamers won't/can't make that trade-off.  Performance is key, no matter how amazing your system is, Gamers still want top performance.

And people stuck with proprietary software won't/can't make that trade-off either.  They need to have a system that can run their software and performs accordingly as well.

Doesn't Paul Simon sing:  Still dual-booting after all these years...

---

### Post by TheFu on 2024-07-03
Well, complaining about things we cannot change and are unlikely to be changed can feel good.  In the end, it doesn't matter. Those other organizations are going to do what they choose to do and we KNOW that Adobe will always be lead by profits when it comes to Linux. There are decades of proof for all to see related to that.

As for gaming on Linux, I suppose it depends on the type of gaming you do.  The types that I do run great on a 5 yr old Android tablet.  My 20+ yr old MS-Windows and DOS games run fast, but perhaps all the functions don't work.  Of course, there are a few that don't run - proprietary crap.

For proprietary gaming from the 2000s, I have a PS2 connected to a 120inch projector.  I've actually gotten car sick playing GTA, it is pretty immersive.  Have a few Gran Turismo versions for the PS2 as well.  For those, I use a steering wheel and peddles setup.  Also have Ace Combat 4/5 (I'm Ace level on all scenarios) and a few other of the most popular games like SOCOM and MGS.  I never finished the 2nd SOCOM. Got stuck on a specific mission and wasn't ever able to clear it.  I should have read a guide after failing over a week, but I didn't.  Life got in the way and gaming was bumped down in priority.

In the early 1990s, I did lose a few weekends completely playing the hot games of the times.  Those where MS-DOS games with EGA graphics - halfway between text "Adventure" and a FPS.  Starflight [https://en.wikipedia.org/wiki/Starflight](https://en.wikipedia.org/wiki/Starflight) was an amazing game with what seemed a nearly endless universe ( 800 planets and 240 different star systems), that ran off a 1.44 MB floppy.  I still remember getting and playing a WoW demo with a computer magazine. At the time, I was learning OOD/OOP at work so how WoW provided hundreds of different objects on the screen and managed them all was really clear to me.  That game and OOP completely changed my world/life.  Command and Conquer was similar.  I like the strategy games.  No need to fancy GPUs with those, BTW.

I suspect all of my older games have been ported to some new "track-me-please" platform like all the MS-Windows gamers use.  Because I refuse to be tracked AND I refuse to pay $0.50 for a game I've already bought, I'm not impacted by the 3rd refresh of C&C or WoW or any but LAN-only networked games.

In the late 1990s, I use to run a TF server on the internet for my friends.  Performance when almost everyone was on dial-up sucked, so I'd host LAN parties at my home using the new technology ..... wifi.  Of course, I used my desktop with a wired ethernet connection to the server while everyone else shared 11 Mbps (if that).  Sadly, my network advantage wasn't sufficient to make up for my terrible gaming.

So, if you choose different games, I be they will play fine under a VM or using DOSBOX or many of the older DOS games are available online via a web browser these days.

I would never, ever, ever, mix my work computer with my personal computer.  So many people have been burned doing that. If not by the company, then by the IRS.

---

### Post by Shibblet on 2024-07-03
> **TheFu said:**
> Well, complaining about things we cannot change and are unlikely to be changed can feel good.  In the end, it doesn't matter. Those other organizations are going to do what they choose to do and we KNOW that Adobe will always be lead by profits when it comes to Linux. There are decades of proof for all to see related to that.
I'm not complaining... I'm hoping someone will point me toward some kind of a usable solution.

> **TheFu said:**
> As for gaming on Linux, I suppose it depends on the type of gaming you do.  The types that I do run great on a 5 yr old Android tablet.  My 20+ yr old MS-Windows and DOS games run fast, but perhaps all the functions don't work.  Of course, there are a few that don't run - proprietary crap.
I do tend to buy older games.  3-5 years... (I mean, I'm still playing Skyrim)  Mostly for the cost.  But I am getting pickier and pickier with the games I actually want to play.  Most of the popular titles, I don't really care much about.  And I DEFINITELY don't want to play online games.

> **TheFu said:**
> I suspect all of my older games have been ported to some new "track-me-please" platform like all the MS-Windows gamers use.  Because I refuse to be tracked AND I refuse to pay $0.50 for a game I've already bought, I'm not impacted by the 3rd refresh of C&C or WoW or any but LAN-only networked games.
A lot of these older games are available on GoG, and work very well in Lutris.

> **TheFu said:**
> I would never, ever, ever, mix my work computer with my personal computer.  So many people have been burned doing that. If not by the company, then by the IRS.
Hmm...

---

### Post by 909mjolnir on 2024-07-05
I was better off with Windows, but I hate the Microsoft business technique which always worsens.  
I can't safely go back to Windows XP SP2, so here I am.

---

### Post by Shibblet on 2024-07-05
> **909mjolnir said:**
> I was better off with Windows, but I hate the Microsoft business technique which always worsens.  
I can't safely go back to Windows XP SP2, so here I am.

That's my problem.  I don't like what Microsoft does, or stands for.  Things like Secure Boot, Pluton, and now with the new added AI (CoPilot) coming in...  They just keep pushing me out the door.
I guess I am just going to have to sacrifice performance, and run Windows 7 in a VM.

---

### Post by him610 on 2024-07-06
> When it comes down to it, buy a second computer.
Then the problem is solved.
> How?
Mini-PCs are very affordable now with some being very capable. 
Checkout Amazon or Newegg to see what they have to offer, and don't forget a KVM switch.

---

### Post by Shibblet on 2024-07-06
> **him610 said:**
> Mini-PCs are very affordable now with some being very capable. 
Checkout Amazon or Newegg to see what they have to offer, and don't forget a KVM switch.

I still don't understand how getting a second computer helps the struggle...

---

### Post by 909mjolnir on 2024-07-08
As much as I got more work done in Windows, Linux is more fun.  
And I like customizing a lot, so I won't go back to Windows.  
This time around of distro hopping, I finally decided to let Linux really have a chance instead of fussing with WINE all the time.  
It's been gradually working out.  Linux can be good, but it does take effort.  Thankfully Linux is NOT like ChromeOS.  

ChromeOS was weird as heck.  Those computers are fun for phone apps, but the ads become a hassle, and the "one click and it's gone" Linux partition is NOT a plus ahahahahaha

---

### Post by lammert-nijhof on 2024-07-17
I moved to dual booting Windows Vista and Ubuntu 8.04 LTS in 2008. In March 2010 I started to use Windows XP in a VirtualBox VM instead.  I still use that XP VM to play the wma copies of my CDs and LPs a few times per week with WoW and TrueBass effects :).  I amplified that idea, I now also run all Linux Apps in 4 Ubuntu VMs for Social media; Banking; Multimedia and Experiments and I use 2 Windows VMs (XP and 11 Pro). The only games I use are Solitaire on my phone and Wolfenstein-3D in DOSBox.
Note that the Windows XP VM from 2010 survived 2 VBox owners; 3 Desktops and 4 CPUs.

---

