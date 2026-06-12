---
title: "The Real Test: Installing Vista on my &quot;average&quot; computer"
date: 2008-10-03
forum: Windows
---

### Post by Battie on 2008-10-03
Good afternoon.

Would you all be interested in following my little experiment?  I often defend Vista on this forum, but unfortunately my experience is limited to running it on very powerful computers--not the ones a regular home user would usually buy.  Tonight (or, more likely, tomorrow), I will be using one of the perks of being an IT employee to install Vista Enterprise on my home PC.

This computer, built over two years ago, runs Ubuntu and XP happily enough, and exceeds the recommended requirements for Vista (and passes the Upgrade Adviser with flying colors).  The (important) specs:

-AMD Athlon 64 3200+ 2.2 GHz Orleans Processor (socket AM2)
-2 GB DDR2 667 (PC2 5400) RAM
-XFX nVidia GeForce 8400 graphics card
-250 GB SATA 3 Gb/s 7200 RPM HDD
-Gigabyte GA-M55SLI-S4 AM2 NVIDIA nForce4 SLI ATX AMD Motherboard

So, this computer is not bad, but definitely not awesome.  I really want to upgrade to a dual-core, but can't afford it at the moment.  I've also been told that Vista works much better with 4 GB RAM, but since that's far above the recommended spec I think it would be cheating.

Are you interested in seeing how this goes?

---

### Post by NintendoTogepi on 2008-10-03
I'd say that computer is pretty darn good, but that's just me. :confused:

---

### Post by ebmelle on 2008-10-03
Installation should be no problem.  Enabling choice to boot all three might be a bit trickier?  I have the same three on an AMD 9600 Q core. Ubuntu with XP or Vista no problem. But, Ubuntu with XP and Vista, not so far.

---

### Post by lukjad on 2008-10-03
I would like to hear how it goes.

---

### Post by daniel_I on 2008-10-03
that beats my computer by miles, guess mine is old.


normal computer- at most 1gb ram

2.0 processor

156mb videocard

---

### Post by Sephoroth on 2008-10-03
That is still above average.  I have a Pentium D 3.0 GHz with an Nvidia 6800 (256MB) and 1 GB of RAM.  I don't know why Vista wouldn't run well on it.

---

### Post by lukjad on 2008-10-03
Well, if it doesn't, Vista's got some 'slpainin' to do!

---

### Post by Giant Speck on 2008-10-03
I only have a gig of RAM and Vista Home Premium runs pretty well on it.  It's slow at times, but so is Ubuntu at times.

---

### Post by Battie on 2008-10-03
Wonderful!  I'll keep you posted.

I've no intention of booting all three.  I play  more on my work computers than at home, so only one OS here.

My work laptop (also pretty powerful), has Vista and Wubi playing nicely.

---

### Post by Frak on 2008-10-03
On many computers, Vista is slow due to old type of ram (such as plain DIMM or DDR1) and old HD types (PATA instead of SATA, or even better, SCSI). I have a SCSI system with a Dual Core AMD at 3.2 GHz with DDR3 that runs Vista like lightning in a VM.

---

### Post by karellen on 2008-10-04
well, give it a try then let us know how it went. there shouldn't be any problems with your configuration

---

### Post by Battie on 2008-10-04
I chose to try the upgrade first.  Toward the end of the installation, I got up to get some ice cream.  When I got back, I saw the Windows Failed to Start screen.  I tried to start normally and got the very generic IRQL_NOT_LESS_OR_EQUAL BSOD.  No driver named.  Fortunately, it took a kernel memory dump, which I copied to my data partition to examine when the dust settles.

I probably could have wrestled with the problem for a while, but I just went with the easier wipe-and-reload option.  For some reason that seems to be going a lot faster too.

Wish my luck!  I think I need it after all.

---

### Post by Battie on 2008-10-04
Success!  The clean installation went quickly and without incident. Windows Update had all my missing drivers.  After I settle in I'm going to see how it is to play WoW.

---

### Post by Battie on 2008-10-04
Couple other things:

My rating is 3.6, with the lowest being graphics for Aero (though it looks and feels fine to me).

WinDBG reveals that the source of the blue screen was ALCXWDM.SYS, which is part of the RealTek AC'97 audio driver package.  I did not expect this because the adviser only flagged my video drivers as a potential problem.  However, after the clean installation my sound chip was the only thing with a (?), which Windows Update solved by downloading the latest RealTek drivers.

---

### Post by Frak on 2008-10-04
For your first attempt, it sounded like it tried to use an XP driver and a Vista driver. During this phase, one of the drivers didn't contain the default IRQ address reserves (usuall with integrated hardware) so it polled the device for an IRQ address. Once it did, it probably found an error with two peices of hardware using the same IRQ address (not bad, but they cannot interrupt at the same time). Therefore, it probably polled an NIC and a sound device and they both reserved the same interrupt time and they both did a sanity check at the same time, one via software demand and another via hardware demand.

/needless information

EDIT
and
/needless bad grammar - sorry bout that folks.

---

### Post by Battie on 2008-10-04
> **Frak said:**
> For your first attempt, it sounded like it tried to use an XP driver and a Vista driver. During this phase, one of the drivers didn't contain the default IRQ address reserves (usuall with integrated hardware) so it polled the device for an IRQ address. Once it did, it probably found an error with two peices of hardware using the same IRQ address (not bad, but they cannot interrupt at the same time). Therefore, it probably polled an NIC and a sound device and they both reserved the same interrupt time and they both did a sanity check at the same time, one via software demand and another via hardware demand.

/needless information

EDIT
and
/needless bad grammar - sorry bout that folks.

It's definitely not needless information!  This interests me! Unfortunately I'm not to adept at reading the stack frames in WinDBG yet, so I don't know that that's what happened.  It makes it a little harder, too, not to have third-party driver symbols.

Other than the BSOD, the installation and my use of it tonight have been so smooth I almost feel silly for making a thread on it.  But no news is good news, right?

WoW performs the same or very slightly better.  The only thing I'm really kicking myself over is that I forgot to back up my personal mail, which is not on the server.  I hope I didn't have anything important in there...

---

### Post by Frak on 2008-10-04
> **Battie said:**
> It's definitely not needless information!  This interests me! Unfortunately I'm not to adept at reading the stack frames in WinDBG yet, so I don't know that that's what happened.  It makes it a little harder, too, not to have third-party driver symbols.

True

> **Battie said:**
> Other than the BSOD, the installation and my use of it tonight have been so smooth I almost feel silly for making a thread on it.  But no news is good news, right?

As long as it isn't about a stolen nuclear warhead, yes.

> **Battie said:**
> I hope I didn't have anything important in there...

You can make a million dollars some other day. BUY NOW!

---

### Post by Canis familiaris on 2008-10-05
> **Battie said:**
> Good afternoon.

Would you all be interested in following my little experiment?  I often defend Vista on this forum, but unfortunately my experience is limited to running it on very powerful computers--not the ones a regular home user would usually buy.  Tonight (or, more likely, tomorrow), I will be using one of the perks of being an IT employee to install Vista Enterprise on my home PC.

This computer, built over two years ago, runs Ubuntu and XP happily enough, and exceeds the recommended requirements for Vista (and passes the Upgrade Adviser with flying colors).  The (important) specs:

-AMD Athlon 64 3200+ 2.2 GHz Orleans Processor (socket AM2)
-2 GB DDR2 667 (PC2 5400) RAM
-XFX nVidia GeForce 8400 graphics card
-250 GB SATA 3 Gb/s 7200 RPM HDD
-Gigabyte GA-M55SLI-S4 AM2 NVIDIA nForce4 SLI ATX AMD Motherboard

So, this computer is not bad, but definitely not awesome.  I really want to upgrade to a dual-core, but can't afford it at the moment.  I've also been told that Vista works much better with 4 GB RAM, but since that's far above the recommended spec I think it would be cheating.

Are you interested in seeing how this goes?

If configured well, Vista will run very well in this configuration; I think. 2GB RAM is a good point for Vista IMO.

---

### Post by rockface on 2008-10-05
> **Battie said:**
> Good afternoon.

Would you all be interested in following my little experiment?  I often defend Vista on this forum, but unfortunately my experience is limited to running it on very powerful computers--not the ones a regular home user would usually buy.  Tonight (or, more likely, tomorrow), I will be using one of the perks of being an IT employee to install Vista Enterprise on my home PC.

This computer, built over two years ago, runs Ubuntu and XP happily enough, and exceeds the recommended requirements for Vista (and passes the Upgrade Adviser with flying colors).  The (important) specs:

-AMD Athlon 64 3200+ 2.2 GHz Orleans Processor (socket AM2)
-2 GB DDR2 667 (PC2 5400) RAM
-XFX nVidia GeForce 8400 graphics card
-250 GB SATA 3 Gb/s 7200 RPM HDD
-Gigabyte GA-M55SLI-S4 AM2 NVIDIA nForce4 SLI ATX AMD Motherboard

So, this computer is not bad, but definitely not awesome.  I really want to upgrade to a dual-core, but can't afford it at the moment.  I've also been told that Vista works much better with 4 GB RAM, but since that's far above the recommended spec I think it would be cheating.

Are you interested in seeing how this goes?

The beta of Intrepid Ibex installs and works adequately on my old Athlon 1400 with 512mb of RAM (no compiz though).

The fact that the system you describe SHOULD run Vista seems to be lost on Windows users.

---

### Post by Calmatory on 2008-10-06
> **NintendoTogepi said:**
> I'd say that computer is pretty darn good, but that's just me. :confused:
No. It is not.

The OP says "average new computer" and claims to be IT employee. In where do you sell new machines with SINGLE CORE CPU's for average customers? For example all the OEM machines have been equipped with Dual core CPU for around 18 months here, first arriving in 2005. Nowadays even the cheapest ones have Intel Pentium E2180 or such.

I call this "The **Real** Test" completely misleading and pro-linux biased. Though, here 90 % of Windows threads which include opinions, are pro-linux, usually with comments like "Windows is unstable" "Microsoft sucks" "I hate windows", which are almost never backed up with actual information, except that "I just don't like it" or "Windows crashed last night".

So, if you want to do the real test, at least put some effort on it. Get 3 GB of RAM and Core 2 Duo CPU. You can also get AMD platform, but in that case you want to skip comparing it to Ubuntu or Linux, since AMD/ATI's video drivers suck and in that case Vista is a clear winner. And so what? Thats the truth in that case. 

As an IT employee OP should be aware of how Vista acts when compared to it being ran with Single core CPU or a Dual core CPU. Though, he used term "my "average"" in the topic title, which is quite much the situation. People having old Single Core CPU's and upgrading to Vista with 512MB of RAM, but I assume that OP wanted to test with new machines. :)

Well, Vista indeed runs with Single core and even with 1GB of ram. My lapop had Vista and I used it before I bought this from my girlfriend. It was usable but the lack of RAM and slow CPU made it crawl at times, mostly with Firefox open with +20 tabs, with foobar2000 and Vista's graphics settings maxed out(she refused to disable them for the sake of performance. Women indeed like the looks the most. :(). Ubuntu however, runs flawlessly. At least flawlessly enough for me. I don't mind 2 seconds longer loading time for Firefox against what it would be with 2 GHz desktop CPU etc. No problems, faster than Vista but slower than XP. Has a great spot between the two systems. ;)

---

### Post by silve on 2008-10-06
my sisters celeron 3.0 ghz 1.5GB Ram ATA 80GB hdd runs vista ultimate pretty well...

[Ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by Sephoroth on 2008-10-06
> **Calmatory said:**
> No. It is not.

The OP says "average new computer" and claims to be IT employee. In where do you sell new machines with SINGLE CORE CPU's for average customers? For example all the OEM machines have been equipped with Dual core CPU for around 18 months here, first arriving in 2005. Nowadays even the cheapest ones have Intel Pentium E2180 or such.

That's true.  When I first read the specs I thought I saw an x2 somewhere in there.  My three year old computer has a dual core processor (Pentium D 3.0 GHz) regardless of how inefficient it is :wink:.  There still are single core computers out there but most of them tend to be netbooks (with Celerons ot Atoms).

> **Calmatory said:**
> I call this "The Real Test" completely misleading and pro-linux biased. Though, here 90 % of Windows threads which include opinions, are pro-linux, usually with comments like "Windows is unstable" "Microsoft sucks" "I hate windows", which are almost never backed up with actual information, except that "I just don't like it" or "Windows crashed last night".

I like Windows :(...I just like Linux more :).

---

### Post by Battie on 2008-10-06
> **Calmatory said:**
> No. It is not.

The OP says "average new computer" and claims to be IT employee. In where do you sell new machines with SINGLE CORE CPU's for average customers? For example all the OEM machines have been equipped with Dual core CPU for around 18 months here, first arriving in 2005. Nowadays even the cheapest ones have Intel Pentium E2180 or such. 

Ah, sorry to sound slanted.  I think I wasn't clear about my intentions.

I know my computer is no good, especially for an IT employee.  My coworkers make fun of it all the time. :-)  The problem is that I could only put in what I could afford at the time (and I recall dual-core two years ago still being a little painful to price out), and I can't quite shell out the money to upgrade the processor or anything else right now (but soon! I hope).

> I call this "The **Real** Test" completely misleading and pro-linux biased. Though, here 90 % of Windows threads which include opinions, are pro-linux, usually with comments like "Windows is unstable" "Microsoft sucks" "I hate windows", which are almost never backed up with actual information, except that "I just don't like it" or "Windows crashed last night".

So, if you want to do the real test, at least put some effort on it. Get 3 GB of RAM and Core 2 Duo CPU. You can also get AMD platform, but in that case you want to skip comparing it to Ubuntu or Linux, since AMD/ATI's video drivers suck and in that case Vista is a clear winner. And so what? Thats the truth in that case. 

As an IT employee OP should be aware of how Vista acts when compared to it being ran with Single core CPU or a Dual core CPU. Though, he used term "my "average"" in the topic title, which is quite much the situation. People having old Single Core CPU's and upgrading to Vista with 512MB of RAM, but I assume that OP wanted to test with new machines. :)

We've been using dual/quad-core PCs at work for some time now, and I've been configuring Vista on them for months.  They all run superbly.

What I meant (jokingly, really) by "real" test is that I wanted to investigate the claim made by so many that Vista won't run on "lesser" PCs well at all, even if they meet or surpass the recommended (not just minimum)  requirements.  So I wanted to see what my experience would be. And I was not disappointed.

I like Vista, and I'm glad it's on my computer now. :-)

> Well, Vista indeed runs with Single core and even with 1GB of ram. My lapop had Vista and I used it before I bought this from my girlfriend. It was usable but the lack of RAM and slow CPU made it crawl at times, mostly with Firefox open with +20 tabs, with foobar2000 and Vista's graphics settings maxed out(she refused to disable them for the sake of performance.
I believe Aero actually improves graphical performance in some cases (if the computer can actually run it) because of its optimizations, but I'll have to confirm that.[/quote]

> Women indeed like the looks the most. :().

*raises hand* Guilty.

>  Ubuntu however, runs flawlessly. At least flawlessly enough for me. I don't mind 2 seconds longer loading time for Firefox against what it would be with 2 GHz desktop CPU etc. No problems, faster than Vista but slower than XP. Has a great spot between the two systems. ;)

Of the three (XP, Ubuntu, Vista), Ubuntu was slightly slower than the rest.  Not enough to annoy me though.  It's all good fun to experiment, though.

---

### Post by Battie on 2008-10-06
> **Sephoroth said:**
> That's true.  When I first read the specs I thought I saw an x2 somewhere in there.  My three year old computer has a dual core processor (Pentium D 3.0 GHz) regardless of how inefficient it is :wink:.  There still are single core computers out there but most of them tend to be netbooks (with Celerons ot Atoms).

Haha, I wondered why you gave my machine high marks.  I know a lot of people with worse, but my specs are nothing to be proud of. :-D

---

### Post by rockface on 2008-10-06
'We've been using dual/quad-core PCs at work for some time now, and I've been configuring Vista on them for months.  They all run superbly.'

I am sure they do, I am sure they do (A rhetorical answer just in case you ask me why I'm repeating myself in the same sentence).

Ubuntu Heron/Gutsy and the latest beta of Intrepid (who thinks up these monikers needs a new occupation) install and work on all my single core computers (a similar point I made not too long ago). 

Vista needs (after a service pack and many updates) at least 1gb of RAM, 15 to 20 gb of hard drive space (for system restore etc), Dual-Core CPU and above with a decent GPU to run Aero, and nobody here even questions this?

Linux does a whole lot more with a whole lot less, but even I admit Linux can be crap. Is it that Linux users expect more, or that Windows users will accept anything Microsoft tells them.

I guess this is not the place to start a new thread, but my question is this. To all those that purchased a copy of Vista, by OEM or retail, will you also go out and purchase Windows 7?

---

### Post by rune0077 on 2008-10-06
> **rockface said:**
> The beta of Intrepid Ibex installs and works adequately on my old Athlon 1400 with 512mb of RAM (no compiz though).


Mmm, so what? In case you missed it, this thread has absolutely nothing to do with Intrepid. I read it because I wanted to read about Vista being tested, and I couldn't care less what Intrepid will or will not run on in that regards.

> **Calmatory said:**
> 
So, if you want to do the real test, at least put some effort on it. Get 3 GB of RAM and Core 2 Duo CPU. 


When I ran Vista, I only had 2 gigs of RAM and it ran blazingly fast with Aero and all. Not a hitch or a bump. It was a pretty good dual core, though, so that might have made a difference. 2 gigs should be enough (in fact, 32 bit Vista only utilizes 2 gigs, doesn't it?)

---

### Post by rockface on 2008-10-06
> **rune0077 said:**
> Mmm, so what? In case you missed it, this thread has absolutely nothing to do with Intrepid. I read it because I wanted to read about Vista being tested, and I couldn't care less what Intrepid will or will not run on in that regards.



When I ran Vista, I only had 2 gigs of RAM and it ran blazingly fast with Aero and all. Not a hitch or a bump. It was a pretty good dual core, though, so that might have made a difference. 2 gigs should be enough (in fact, 32 bit Vista only utilizes 2 gigs, doesn't it?)

'Mmm, so what? In case you missed it, this thread has absolutely nothing to do with Intrepid.'

You missed my point, as many Windows users do. I can install the next version of Ubuntu (Intrepid, for all it's faults and is in beta) on an 'average computer', the genesis of this thread. The specification of this PC I did enclose in my response (Athlon 1400 with 512mb of RAM). I can not do this with Vista that is a good 18 months old from release, and has at least one service pack and many megabytes of updates.

The title of this thread is 'The Real Test: Installing Vista on my "average" computer'. I gave specifics, is this not good enough? Or is it a little more fundamental.

Linux functions at lesser thresholds than Vista does (but not XP). This makes it appetizing (is that a word) to the low cost netbook crowd.

What defines 'average'? 'When I ran Vista, I only had 2 gigs of RAM and it ran blazingly fast with Aero and all.' You proved my point with more eloquence and insight than anything I could have ever conceived.

I salute you.

---

### Post by rune0077 on 2008-10-06
> **rockface said:**
> 
You missed my point, as many Windows users do. I can install the next version of Ubuntu (Intrepid, for all it's faults and is in beta) on an 'average computer', the genesis of this thread. The specification of this PC I did enclose in my response (Athlon 1400 with 512mb of RAM). I can not do this with Vista that is a good 18 months old from release, and has at least one service pack and many megabytes of updates.


I think you're the one missing the point. First, I'm not a Windows user. I have used Vista in the past, it's a great OS, but it's not on my computer right now (and not likely going back). But, there's absolutely no need to discuss Intrepid here. This thread is not about whether Ubuntu will run on a computer or not. You're trying to prove a point that seems very irrelevant to the thread. It's like if someone asked you "can you cook an egg in 5 minutes" and you replied "I can bake a cake in 10 minutes". There's no correlation at all.

So, let's talk Vista, let's keep Ubuntu out of the conversation.

---

### Post by rockface on 2008-10-06
> **rune0077 said:**
> I think you're the one missing the point. First, I'm not a Windows user. I have used Vista in the past, it's a great OS, but it's not on my computer right now (and not likely going back). But, there's absolutely no need to discuss Intrepid here. This thread is not about whether Ubuntu will run on a computer or not. You're trying to prove a point that seems very irrelevant to the thread. It's like if someone asked you "can you cook an egg in 5 minutes" and you replied "I can bake a cake in 10 minutes". There's no correlation at all.

So, let's talk Vista, let's keep Ubuntu out of the conversation.

'So, let's talk Vista, let's keep Ubuntu out of the conversation.'

Talk Vista you say, ok I am game.

---

### Post by Old_Grey_Wolf on 2008-10-06
Part of the problem with Vista is that retailers are selling laptop computers with Vista Home Premium that do not have a graphics card/integrated graphics chip that can support the Aero interface. I bought such a laptop computer and returned it. I did some research and bought one that could.

I finally bought an inexpensive laptop computer with a dual core 1.7GHz processor with 1GB of RAM. It does run Vista Home Premium with Aero enabled. It slows down at times; however, if the only OS I was familiar with was Microsoft Windows, I probably wouldn't know the difference. In other words, it is probably fine for the average Microsoft Windows user. 

I would be interested in the results of this experiment if it is for average computers and average users. I have been using Ubuntu exclusively (except for fixing MS Windows boxes) for a little over a year; therefore, I can no longer call myself "the average computer user". When I started using Ubuntu, I discovered that a computer I considered old actually had a dual core processor. So, I think the average computer does incluse a dual core processor.

And I do emphasize the word average.

---

### Post by Frak on 2008-10-06
I got Vista to run on Virtual PC for Mac on the PPC...

Boots in an hour, but it runs...

/offtopic

---

### Post by Battie on 2008-10-06
> **Old_Gray_Wolf said:**
> Part of the problem with Vista is that retailers are selling laptop computers with Vista Home Premium that do not have a graphics card/integrated graphics chip that can support the Aero interface. I bought such a laptop computer and returned it. I did some research and bought one that could.

Just curious, do you recall it having a Vista Capable logo, or a Vista Premium Ready logo?  When I was studying for the MCITP there was a lot of discussion of how Vista Capable didn't necessarily mean "can run Aero", but I thought it seemed terribly deceptive to the user.

> I finally bought an inexpensive laptop computer with a dual core 1.7GHz processor with 1GB of RAM. It does run Vista Home Premium with Aero enabled. It slows down at times; however, if the only OS I was familiar with was Microsoft Windows, I probably wouldn't know the difference. In other words, it is probably fine for the average Microsoft Windows user. 

I would be interested in the results of this experiment if it is for average computers and average users. I have been using Ubuntu exclusively (except for fixing MS Windows boxes) for a little over a year; therefore, I can no longer call myself "the average computer user". When I started using Ubuntu, I discovered that a computer I considered old actually had a dual core processor. So, I think the average computer does incluse a dual core processor.

And I do emphasize the word average.

I am feeling increasingly embarrassed for posting my spec here. :-D

I think most people I know around here are either updating their computers constantly, or running on things four or more years old.  That's why I judged my machine as somewhere in the middle.

And I agree that it would have been more interesting if it were an "average" user doing this.  I was thinking a little more about my attempt to upgrade before going with a wipe.  I know very well that on XP performing a similar upgrade could be a terrible thing to do, but I'd hope the process was better on Vista.  Instead, my machine was rendered unbootable (it couldn't go to Safe Mode, because setup had not completed).  I kind of wish that when I'd realized that a wipe was imminent that I'd tried the roll back to XP option just for kicks.

---

### Post by Battie on 2008-10-06
Also, I'm sort of afraid my title came off far more pretentious than I meant it to.  I was just having a bit of fun while satisfying a genuine curiosity I had about Vista's performance.  I'm glad to see so much interest though!

I haven't been talking about Ubuntu much here simply because I don't feel as comfortable judging what it was doing on my computer.  I've mentioned that performance was comparable to both Windows versions, but I don't know what to make of it because I don't understand what's under Ubuntu's hood was well, especially it's memory management.

I would be happy to have a discussion of how Vista manages its resources versus how Ubuntu does.

---

### Post by EnGorDiaz on 2008-10-06
i have been on linux and unix systems now even longer than i had xp or vista installed im never going to ever look at windows again well i do when i have my laptop out thats because i need diagnostic and rescue cds for work

---

### Post by EnGorDiaz on 2008-10-06
> **Battie said:**
> 
I would be happy to have a discussion of how Vista manages its resources versus how Ubuntu does.

thats would be a very interesting topic something i would actualy look at

---

### Post by NintendoTogepi on 2008-10-07
> **Calmatory said:**
> No. It is not.



I suppose I'm used to my three year old computer/laptop. It sucks supposedly, but I really haven't noticed anything wrong with it. Runs lightning fast, and I can still play any new PC games I desire. (although not on the highest settings, but I'm not a graphics wh*** :D)

Specs:

1.6GHz Pentium M Processor
NVidia GeForce Go 6800, 256MB
2048MB of RAM

---

### Post by Calmatory on 2008-10-07
> **NintendoTogepi said:**
> I suppose I'm used to my three year old computer/laptop. It sucks supposedly, but I really haven't noticed anything wrong with it. Runs lightning fast, and I can still play any new PC games I desire. (although not on the highest settings, but I'm not a graphics wh*** :D)

Specs:

1.6GHz Pentium M Processor
NVidia GeForce Go 6800, 256MB
2048MB of RAM

Well, even though the parts OP described are new, they are not fast. They are the from value segment and are quite much the cheapest possible ones. :) Nowadays one can build a Quad core, 4GB ram and fairly decent GPU(HD4670) system for less than $450. Back then 3 years ago dual core CPU(Athlon64 X2) alone cost that $400.

Things change. :)

---

### Post by Calmatory on 2008-10-07
> **rockface said:**
>  

Vista needs (after a service pack and many updates) at least 1gb of RAM, 15 to 20 gb of hard drive space (for system restore etc), Dual-Core CPU and above with a decent GPU to run Aero, and nobody here even questions this?


Please note that Aero or system restore is not mandatory. Compiz also requires decent GPU to run well. Besides, 20 GB is quite much nothing as nowadays all OEM machines have at least 160 GB of disk space, usually 320 or 500 GB. I've never had more than 80 GB and I doubt I need any more. :)

It is clear that Linux is more flexible, efficient and faster. But how does Ubuntu compare to Vista? Or to XP, which is still the most used Windows version?

One reason for the bloatness of Windows could be the legacy support and wide range of supported devices from pre-2000 to this day.

Edit: Accidentally double posted. :|

---

### Post by Old_Grey_Wolf on 2008-10-07
> **Battie said:**
> Just curious, do you recall it having a Vista Capable logo, or a Vista Premium Ready logo?  

It had a Vista logo of some kind. That's all I remember. At the time I didn't know there was a difference. The vendor advertised it as having Vista Home Premium pre-installed on it. However, when I tried to enable the Aero interface, Vista informed me that I would have to upgrade my graphics card to enable the feature. I was planning to use it to dual boot with Ubuntu. I considered loading Ubuntu anyway. That thought left my mind quickly; because, I was so angry. I didn't get what I though I had paid for. I returned it immediately.

---

### Post by RoyalShrubber on 2008-10-08
> **rockface said:**
> 
Vista needs (after a service pack and many updates) at least 1gb of RAM, 15 to 20 gb of hard drive space (for system restore etc), Dual-Core CPU and above **with a decent GPU to run Aero**, and nobody here even questions this?

Recently I've been playing with opensuse (11) and compiz fusion on my laptop. 

Laptop has integrated cr*p that is radeon mobility x1250. Nothing fancy, but it got basic 3D acceleration, enough that it can run full aero without problems (ok flip3d runs at say 15 fps with 10 windows open, but that's still good). 

Back to compiz. I've installed it and it's running poorly, sometimes gui is not responsive, I also had to turn off certain effects like 'live' resizing of windows (windows get resized only when I release mouse button, because it's too slow otherwise). Maybe worthy of mentioning - Aero unlike default Compiz runs effects antialiased and with some image interpolation technique that is not 'nearest neighbour'. Then I also had problems getting video running - the only option was unaccelerated path through X, no facy xv or opengl. So it's not only slow, it visually looks worse too.

Maybe it's because MS spent time optimizing Aero for integrated cards or cards with shared memory and foss guys haven't, but Aero really beats the living **** out of Compiz on my constrained system. 


(that's just my experience though, of course I don't expect aero to run better on every system.)

---

### Post by Battie on 2008-10-08
> **Old_Gray_Wolf said:**
> It had a Vista logo of some kind. That's all I remember. At the time I didn't know there was a difference. The vendor advertised it as having Vista Home Premium pre-installed on it. However, when I tried to enable the Aero interface, Vista informed me that I would have to upgrade my graphics card to enable the feature. I was planning to use it to dual boot with Ubuntu. I considered loading Ubuntu anyway. That thought left my mind quickly; because, I was so angry. I didn't get what I though I had paid for. I returned it immediately.

I would have returned it too.  Though I've been defending Vista here I quite agree that the early marketing was (perhaps not deliberately) deceptive.  Though it's documented that Vista Capable doesn't mean it will run Aero and other cool stuff, I don't think that was made clear enough to shoppers, and that's not fair.

---

### Post by Calmatory on 2008-10-08
Isn't it OEM's fault in that case? E.g. build a system which is incapable of running the software it is built for. Quite wrong to accuse MS for that?

---

### Post by Battie on 2008-10-08
> **Calmatory said:**
> Isn't it OEM's fault in that case? E.g. build a system which is incapable of running the software it is built for. Quite wrong to accuse MS for that?

Yes, their fault too.  Really just the lack of end-user education makes me unhappy, but that could be a topic in itself (and then we could start blaming people who don't educate THEMSELVES...).

---

### Post by rockface on 2008-10-08
> **RoyalShrubber said:**
> Recently I've been playing with opensuse (11) and compiz fusion on my laptop. 

Laptop has integrated cr*p that is radeon mobility x1250. Nothing fancy, but it got basic 3D acceleration, enough that it can run full aero without problems (ok flip3d runs at say 15 fps with 10 windows open, but that's still good). 

Back to compiz. I've installed it and it's running poorly, sometimes gui is not responsive, I also had to turn off certain effects like 'live' resizing of windows (windows get resized only when I release mouse button, because it's too slow otherwise). Maybe worthy of mentioning - Aero unlike default Compiz runs effects antialiased and with some image interpolation technique that is not 'nearest neighbour'. Then I also had problems getting video running - the only option was unaccelerated path through X, no facy xv or opengl. So it's not only slow, it visually looks worse too.

Maybe it's because MS spent time optimizing Aero for integrated cards or cards with shared memory and foss guys haven't, but Aero really beats the living **** out of Compiz on my constrained system. 


(that's just my experience though, of course I don't expect aero to run better on every system.)

'(that's just my experience though, of course I don't expect aero to run better on every system.)'

I'm glad you included this final statement in your post. I have had compiz-fusion working on a 32mb Geforce 2 MX on a Mandriva beta, but alas not under any version of Ubuntu.

ATI has better Windows drivers than for Linux, the whole world and his dog know this as fact. Is it coincidence that the ancient Geforce  mentioned above is an Nvidia based card? Nvidia have reasonable Linux drivers and I doubt Aero would work with this piece of legacy hardware. 

The 'radeon mobility x1250' is still superior technology when compared to the Geforce 2 MX, nobody can argue against this.

Not being overwhelmed by either Compiz or Aero, I suppose they both have their place. I would tend to turn them off anyway.

---

### Post by hell_prince on 2008-10-13
Well I have an Athlon 64 3000+ 1.8ghz and 1gb Ram DDR400, and a 120 Samsung ATA hdd drive and a GeForce 8500GT PCI-e... Well Vista Ran Pretty well here... But erm with my games was  little harsh.. Guess why? 1gig of ram :P Rest was pretty good here... everything worked well... Not as smooth as my "Ubunty" but yeah reasonably well...

Oh forgetting some Blu screens but yeah it was not so bad experience :P

---

