---
title: "Virus trouble on XP Home"
date: 2008-10-04
forum: Windows
---

### Post by Raccoon1400 on 2008-10-04
I just finished reinstalling XP home on a friend's computer. Specs are: 768MB ram, 1.7 GHz P4, 20 GB HD. It had some sort of virus. The computer ran really slow after bootup, and froze if you tried to do things. The virus program (installed after infection), Kaspersky, could not scan the entire computer, even when in safe mode.

I reinstalled completely.
now problems are occuring again. 
Any ideas? Did the virus somehow survive the format?

Here are some messages he sent me about the computer.


> It closed once when I was looking in folders, explorer had to close. Not anymore after that.
It is primarily IE that closes. I have written this e-mail once already and have had to write it again.
I have not installed any other browser. For some reason some downloads take a lot longer than usual.
Kaspersky has not been able to do a ful scan; it got to 15% before closing itself.
These little problems are not normal.

> 
Yes, Duncan, my computer is almost like it was before you attended to it with the exception that more stuff works and it's not slow. It just freezes frequently and many other small problems have been occuring. I haven't been able to open my browser until I restarted my computer a few times. Oh, and every time I shut down, a message saying Windows Explorer needs to close, but I wasn't using that, and it freezes. Right when I'm shutting down. I'm better off holding the power button down for now.
Wasn't this computer supposed to be proper again?

---

### Post by smoker on 2008-10-04
>  I reinstalled completely.
now problems are occuring again. 
Any ideas? Did the virus somehow survive the format?


unless any viruses were on another partition, and reinfected the new windows install, or were on backed up data restored to the windows partition without being checked, the computer should be free of viruses. to be sure try an online scan here:
[http://housecall.trendmicro.com/](http://housecall.trendmicro.com/)

i suspect though that it may be a hardware problem, i would check the memory, and hard drive first, with memtest off the ubuntu live-cd, and download a diagnostic from the hard drive manufacturer to check the integrity of the drive. 'drive fitness test' is excellent for checking hard drives also, you can download and burn a bootable version from here: [http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

best of luck

---

### Post by Raccoon1400 on 2008-10-04
> **smoker said:**
> unless any viruses were on another partition, and reinfected the new windows install, or were on backed up data restored to the windows partition without being checked, the computer should be free of viruses. to be sure try an online scan here:

The computer did have two external hard drives connected.
However, the computer IS much better that before reinstallation.

---

### Post by hansdown on 2008-10-04
Hi Raccoon1400.

IE is an open door for executables.

Have you tried firefox, or other browsers?

---

### Post by Raccoon1400 on 2008-10-04
> **hansdown said:**
> Hi Raccoon1400.

IE is an open door for executables.

Have you tried firefox, or other browsers?

He is using safari now, and it has crashed a few times, but I think it was better that IE.

---

### Post by hansdown on 2008-10-04
> **Raccoon1400 said:**
> He is using safari now, and it has crashed a few times, but I think it was better that IE.

Apple browsers may be = IE.

---

### Post by lisati on 2008-10-04
It might be an idea to check if the computer can be started up with Ubuntu and a virus scan done from there.

---

### Post by Raccoon1400 on 2008-10-04
> **lisati said:**
> It might be an idea to check if the computer can be started up with Ubuntu and a virus scan done from there.

I tried booting the ubuntu cd after I reinstalled to get drivers for internet, the only live cd that worked was dsl.

---

### Post by stinger30au on 2008-10-04
if your really worried a virus may have survived a format of the hdd, dban is the program to run, it will destroy the data for good and you wont get the data back in a big hurry

[http://www.dban.org/](http://www.dban.org/)

---

### Post by Raccoon1400 on 2008-10-04
> **stinger30au said:**
> if your really worried a virus may have survived a format of the hdd, dban is the program to run, it will destroy the data for good and you wont get the data back in a big hurry

[http://www.dban.org/](http://www.dban.org/)

At this point, is seems more likely it reinfected from the external drives, at least partially reinfected.

---

### Post by smoker on 2008-10-05
> **Raccoon1400 said:**
> I tried booting the ubuntu cd after I reinstalled to get drivers for internet, the only live cd that worked was dsl.

a windows virus won't stop a live-cd from booting up. if the ubuntu cd is burned ok, and the cd drive is working ok, then i would check the rest of the hardware for faults.

---

### Post by Raccoon1400 on 2008-10-05
> **smoker said:**
> a windows virus won't stop a live-cd from booting up. if the ubuntu cd is burned ok, and the cd drive is working ok, then i would check the rest of the hardware for faults.

It booted to a certain point and stopped, like most of the other live CDs.

---

### Post by Ptero-4 on 2008-10-06
That's probable bad RAM. As others said, run the memtest tool off you DSL disc.

---

### Post by Raccoon1400 on 2008-10-13
Results from memtest86+
Here is the email my friend sent.
Is there a problem, because even though there are no errors, pass is 0 too.


> Okay I managed to do the test. When I did it it looked like this:


Memtest86+ v1.70 : Pass
Pentium 4 (0.18) 1695 MHz : Test
L1 Cache: 8k 11853 MB/s : Test #
L2 Cache: 256k 11853 MB/s : Testing:
Memory: 767M 509 M/s : Pattern
Chipset: Intel i845 (ECC: Disabled) / FSB: 99MHz


Walltime     Cached      RSudMem    MemMap   Cache     ECC     Test   Pass    Error    ECC Error


(00:00:00)   (      )            (       )         (      )          On         Off      STD    0           0            0


So I guess there were no errors as none came up that I know of. It did several tests but I stopped it when I saw the same one again, but the 'Pass' was only at 44%.


Alright? What now?


What do you make of it?

---

### Post by smoker on 2008-10-13
> **Raccoon1400 said:**
> Results from memtest86+
Here is the email my friend sent.
Is there a problem, because even though there are no errors, pass is 0 too.

memtest runs eight separate tests in rotation, and once the eight tests are completed it will count as one pass. your friend should at least let memtest run until all eight, ie, one pass, is completed before regarding the memory as ok, though, generally, the longer the test is left to run the better!

some of the symptoms you mentioned earlier could also be related to a poor power supply, or over heating, i would check these possibilities out also (obviously with the power off!): check the cpu and heatsink is free of dust, check case fans, if any, are clear, power supply fan also. sometimes you can check the temps of the cpu in the bios. the easiest way to check a power supply is to swap it for another known working one, if you have one handy. if you or your friend aren't comfortable delving inside the case, then don't, take it to a local shop and have them check everything out.

best of luck

---

### Post by Raccoon1400 on 2008-10-13
> **smoker said:**
> memtest runs eight separate tests in rotation, and once the eight tests are completed it will count as one pass. your friend should at least let memtest run until all eight, ie, one pass, is completed before regarding the memory as ok, though, generally, the longer the test is left to run the better!

some of the symptoms you mentioned earlier could also be related to a poor power supply, or over heating, i would check these possibilities out also (obviously with the power off!): check the cpu and heatsink is free of dust, check case fans, if any, are clear, power supply fan also. sometimes you can check the temps of the cpu in the bios. the easiest way to check a power supply is to swap it for another known working one, if you have one handy. if you or your friend aren't comfortable delving inside the case, then don't, take it to a local shop and have them check everything out.

best of luck

He said he did do all of the tests.

What doesn't make sense is this:
this machine was fine, and then it got the virus.
then after the format these issues started happening.
Did the hardware start to act up immediately after the reinstall?

---

### Post by 3rdalbum on 2008-10-14
I don't believe it's a virus. It's probably a hardware problem. Windows users tend to scream "I've got a virus!" whenever anything unusual happens.

The computer is not overclocked, is it?

---

### Post by smoker on 2008-10-14
> **Raccoon1400 said:**
> He said he did do all of the tests.

What doesn't make sense is this:
this machine was fine, and then it got the virus.
then after the format these issues started happening.
Did the hardware start to act up immediately after the reinstall?

memtest only checks ram. hardware can gradually fail over time, so may not be immediately apparent, or it can fail instantly. the older the computer the more likelihood that hardware faults will develop,

---

### Post by Raccoon1400 on 2008-10-14
Kaspersky was telling us about some intrusion before we whiped it clean.
He also thought he got a virus but could think of anything he downloaded that could have done it. He thought it was from leaving it connected with no virus protection.

---

### Post by Raccoon1400 on 2008-10-15
Also, if this was hardware, then why would the reinstall have made a diffence?
Before it was extremely slow, not apps just crash often.

---

### Post by I-75 on 2008-10-15
Found this interesting thread on virus that may affect the BIOS.

[http://techrepublic.com.com/5208-11193-0.html?forumID=81&threadID=201438](http://techrepublic.com.com/5208-11193-0.html?forumID=81&threadID=201438)

---

### Post by smoker on 2008-10-15
> **I-75 said:**
> Found this interesting thread on virus that may affect the BIOS.

[http://techrepublic.com.com/5208-11193-0.html?forumID=81&threadID=201438](http://techrepublic.com.com/5208-11193-0.html?forumID=81&threadID=201438)

sounds like he has either prepared his bios flash floppy on an infected pc, and therefore infected the floppy, or, more likely, he was connected to the net during the new install.

---

### Post by Raccoon1400 on 2008-10-15
There were a couple weird things the BIOS was doing. To boot a CD, I had to boot something, reboot with the disk, instead of just inserting disk and powering up.
And also, I couldn't get into BIOS settings, even though I hit the right key. Maybe it would have worked if I tried it while rebooting instead of powering up.

---

### Post by Raccoon1400 on 2008-10-15
> **smoker said:**
> sounds like he has either prepared his bios flash floppy on an infected pc, and therefore infected the floppy, or, more likely, he was connected to the net during the new install.

The comments seem to confirm the existence of such a virus.

---

### Post by oldsoundguy on 2008-10-15
> **Raccoon1400 said:**
> Kaspersky was telling us about some intrusion before we whiped it clean.
He also thought he got a virus but could think of anything he downloaded that could have done it. He thought it was from leaving it connected with no virus protection.

Enough said!  It is Windows.  Clicking on a JPG can install a piece of malware if you weren't properly protected in the first place. (an ativirus program alone is NOT sufficient protection!)

It sounds as if he MAY have installed a boot sector virus or even one that got into the bios.  (why you have to password protect the bios in Windows at ALL TIMES.)

You have been spinning your wheels on this for too long! Time to take it to a shop!  They have all of the test software there and should be able to fix it as long as it turns on and there is a POST screen.

Then, just maybe, your friend will quit listening to the "safe OS" BS that comes out of Redmond and take the necessary prevention measures that have to be done if you are to run Windows and take it on line.(giving the devil his due .. Vista is one he** of a lot more secure than XP .. but runs like cra*!)

---

### Post by Raccoon1400 on 2008-10-15
> **oldsoundguy said:**
> Enough said!  It is Windows.  Clicking on a JPG can install a piece of malware if you weren't properly protected in the first place. (an ativirus program alone is NOT sufficient protection!)
What else? A firewall. My machines are firewalled by a router and internet switch.

I didn't know you could get a virus just by opening a JPG. Scary.

---

### Post by oldsoundguy on 2008-10-15
For Windows you need:

A GOOD anti-virus (Norton and McAfee do NOT qualify as GOOD.)
A firewall (at least the one for Windows will keep you from getting hacked, it will not, however. prevent installed items from phoning home. (no recommendation here at present as my computers live behind a hardware firewall in my network.)
A hijack blocker (I like Spyware Guard)
A spyware blocker (I like both Spyware Blaster and SUPERAntiSpyware and usually install both to live on a machine.  Enabling the immunize portion of Spyware Blaster and NOT using Tea Timer))
Pop up blocker (the Google toolbar will suffice for IE but do not install the Google Desktop).
Better yet, go with FireFox as a browser and add some additional protection to IT such as No Script, Ad Blocker Plus and W.O.T. at a minimum)

Some clean up programs ... I use them ALL on the Windows machines that land here for fixing.: (all are FREE)
Ad-Aware 2008
A-Squared FREE
CCleaner
Glary Utilities (the registry repair in this one is almost as good as any paid program you could buy!)
MalwareBytes

Of course, you have to keep all of those updated at least once a week and do scans at least once a week if you spend more than 20 minutes on line surfing. (figure about 4-6 hours of wasted time thanks to Windows .. Linux be lookin' better now, don't it!)

---

### Post by Raccoon1400 on 2008-10-15
> **oldsoundguy said:**
> For Windows you need:

A GOOD anti-virus (Norton and McAfee do NOT qualify as GOOD.)
A firewall (at least the one for Windows will keep you from getting hacked, it will not, however. prevent installed items from phoning home. (no recommendation here at present as my computers live behind a hardware firewall in my network.)
A hijack blocker (I like Spyware Guard)
A spyware blocker (I like both Spyware Blaster and SUPERAntiSpyware and usually install both to live on a machine.  Enabling the immunize portion of Spyware Blaster and NOT using Tea Timer))
Pop up blocker (the Google toolbar will suffice for IE but do not install the Google Desktop).
Better yet, go with FireFox as a browser and add some additional protection to IT such as No Script, Ad Blocker Plus and W.O.T. at a minimum)

Some clean up programs ... I use them ALL on the Windows machines that land here for fixing.: (all are FREE)
Ad-Aware 2008
A-Squared FREE
CCleaner
Glary Utilities (the registry repair in this one is almost as good as any paid program you could buy!)
MalwareBytes

Of course, you have to keep all of those updated at least once a week and do scans at least once a week if you spend more than 20 minutes on line surfing. (figure about 4-6 hours of wasted time thanks to Windows .. Linux be lookin' better now, don't it!)


Holy Crap! I'm glad I do most stuff on Linux!!!

Any Idea about the firewall capabilities of a Rogers USB high speed cable modem are? Does it count as a firewall?

What about Kaspersky and AVG?
He bought Kaspersky after the problems started, and I recently switched from Norton to AVG free.

---

### Post by oldsoundguy on 2008-10-15
Both Kapersky (the PAID version) and AVG (the FREE version are good AV programs .. as is Avast (free)(as a resident)

Almost any good router will furnish a solid firewall.  But you do have to update the flash now and again.

I do some fix-'em-ups for friends with Windows problems and I do set up their new machines (removing all the crap ware and trial ware and cripple ware that comes with any pre-installed Windows box) .. there is a program that does most of the removal called pcdecrapifier that will remove all but trial AV and the Windows CaCa that have clocks attached .. (will die unless paid for!)

Plus I still run a pair of Windows XP boxes .. one in my guest room for .. GUESTS .. I also use that one for video instruction and a sync for my PDA/GPS units (which run Windows Mobile) .. and I have a melt your eyeballs Windows machine in the media room for ... tah dah ... MEDIA!  (and for running a boatload of Adobe programs that I paid a bundle for and want to get my bucks worth out of them!)

---

### Post by Raccoon1400 on 2008-10-15
My friend agrees that it's time to take this thing into the shop.

Here are some specs if they are useful.
The computer is a refurbished Compaq.


> 1394 EEEE card (firewire slot)
High-speed USB ports
Had Windows 2000 and for awhile BOTH Windows 2000 and XP
A DVD drive and burner (also reads CDs and everything else, basically)
512MB of RAM.
A (connected) 250GB SimpleDrive External Storage Device
A (connected) 500GB SeaGate External Storage Device.


---

### Post by Thelasko on 2008-10-16
> **oldsoundguy said:**
> For Windows you need:

A GOOD anti-virus (Norton and McAfee do NOT qualify as GOOD.)
A firewall (at least the one for Windows will keep you from getting hacked, it will not, however. prevent installed items from phoning home. (no recommendation here at present as my computers live behind a hardware firewall in my network.)
A hijack blocker (I like Spyware Guard)
A spyware blocker (I like both Spyware Blaster and SUPERAntiSpyware and usually install both to live on a machine.  Enabling the immunize portion of Spyware Blaster and NOT using Tea Timer))
Pop up blocker (the Google toolbar will suffice for IE but do not install the Google Desktop).
Better yet, go with FireFox as a browser and add some additional protection to IT such as No Script, Ad Blocker Plus and W.O.T. at a minimum)

Some clean up programs ... I use them ALL on the Windows machines that land here for fixing.: (all are FREE)
Ad-Aware 2008
A-Squared FREE
CCleaner
Glary Utilities (the registry repair in this one is almost as good as any paid program you could buy!)
MalwareBytes

Of course, you have to keep all of those updated at least once a week and do scans at least once a week if you spend more than 20 minutes on line surfing. (figure about 4-6 hours of wasted time thanks to Windows .. Linux be lookin' better now, don't it!)
Nahh, you don't need half of that stuff.

Three simple words: "[Limited User Account]("http://www.microsoft.com/protect/computer/advanced/useraccount.mspx")"

I've heard good things about [NOD32]("http://www.eset.com/products/nod32.php"), and use Firefox with[ Ad-Block Plus.]("https://addons.mozilla.org/en-US/firefox/addon/1865")

---

### Post by Thelasko on 2008-10-16
If it's a BIOS problem, just go to the [manufacturer's website]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&docname=c00007682") and download the utility to flash it.  It's probably best to do this from a CD or floppy that runs at bootup.

---

### Post by oldsoundguy on 2008-10-16
> **Thelasko said:**
> Nahh, you don't need half of that stuff.

Three simple words: "[Limited User Account]("http://www.microsoft.com/protect/computer/advanced/useraccount.mspx")"

I've heard good things about [NOD32]("http://www.eset.com/products/nod32.php"), and use Firefox with[ Ad-Block Plus.]("https://addons.mozilla.org/en-US/firefox/addon/1865")

Right .. and just how are you to limit a user account on a computer that is NOT under your control?  

I FIX just such trashed Windows boxes where they get the thing from Best Buy and just plug them in .. never cleaning, fixing, updating or protecting the things from day one!

I fixed just such a computer for a guy that had his two out of control teenage kids living with him.  I put on all of the protection. (over 4000 pieces of malware removed!)

Boy .. on line gamer
Girl .. chatty Kathy.

They disabled all of the protection because it was preventing them from accessing their favorite sites that "all their friends go to."  Machine was dead in the water within 3 weeks after repair.  I told the guy to have the kids take it into a shop and pay SHOP RATE (not what I charge) to have the computer fixed .. he just unplugged it and sold it! Bought himself a laptop and keeps it in his truck locked up!

And remember many people are terrified that if they use something on their computer that is not approved by MS, the machine will blow up!

---

### Post by smoker on 2008-10-16
> **Raccoon1400 said:**
> My friend agrees that it's time to take this thing into the shop.

let us know how he gets on?

---

### Post by Thelasko on 2008-10-17
> **oldsoundguy said:**
> 
I fixed just such a computer for a guy that had his two out of control teenage kids living with him.  I put on all of the protection. (over 4000 pieces of malware removed!)

Boy .. on line gamer
Girl .. chatty Kathy.

They disabled all of the protection because it was preventing them from accessing their favorite sites that "all their friends go to."  Machine was dead in the water within 3 weeks after repair.  I told the guy to have the kids take it into a shop and pay SHOP RATE (not what I charge) to have the computer fixed .. he just unplugged it and sold it! Bought himself a laptop and keeps it in his truck locked up!
Or, you set the machine up so only Dad has the administrator password, and then the kids can't install/uninstall anything they want because they have "user" level accounts.  Now the kids can use the machine to do their homework.
problem solved!

---

### Post by oldsoundguy on 2008-10-17
I didn't think his kids were that stupid! .. my mistake, but trying to set up an administrator account would have been a stretch for dad!  Dad drives a truck, and spends his free time with a fishing pole or a rifle in his hands, if you catch my drift.  And I told the kids (one 16 year old boy one 18 year old girl) (treating them like grown ups) that the protection would keep them on line and working. (like talking to a WALL)
The VERY LAME excuse of "but all my friends use that site" does not wash!

Just remember that if it were not for the creations that come out of Redmond, coupled with the average IQ of most Windows users, most computer repair shops would be out of business and there would be little need for IT's to manage Windows based enterprise systems.  We do have Bill and Paul and the crew to thank for stimulating the economy, creating useless jobs and moving money around.

---

### Post by fiddledd on 2008-10-17
> **oldsoundguy said:**
> I didn't think his kids were that stupid! .. my mistake, but trying to set up an administrator account would have been a stretch for dad!  Dad drives a truck, and spends his free time with a fishing pole or a rifle in his hands, if you catch my drift.  And I told the kids (one 16 year old boy one 18 year old girl) (treating them like grown ups) that the protection would keep them on line and working. (like talking to a WALL)
The VERY LAME excuse of "but all my friends use that site" does not wash!

Just remember that if it were not for the creations that come out of Redmond, coupled with the average IQ of most Windows users, most computer repair shops would be out of business and there would be little need for IT's to manage Windows based enterprise systems.  We do have Bill and Paul and the crew to thank for stimulating the economy, creating useless jobs and moving money around.

And yet you never thought to set up LUAs for them, very odd considering the risk of running as an administrator in any OS.

Incidentally I'd like to see the figures from the studies that were conducted to record the IQs of Windows users, or was it just a biased opinion.

---

### Post by oldsoundguy on 2008-10-17
each had their own user account .. just that they also had access to the main account and could get in there (anyone can bypass the restrictions once the password is known, even though I did not set that up).

AS to the IQ .. I just judge by the amount of really dumb questions (not really questions but pleas for help .. no such thing as a dumb question if it really IS a question) that we get on another board where I help with maintenance problems for Windows users.  Especially the responses we get back.  One would think that a lot of users have severe difficulty in even writing their name.  K.I.S.S. (keep it simple, stupid) on that board is the RULE not the exception.
And MOST of those issues that come there are those of total lack of protection and safe internet practices. (with the "nobody told me" response.)

The inside joke is that most should have to take a drivers test to buy a computer .. and most would fail the first time.

---

### Post by fiddledd on 2008-10-17
> **oldsoundguy said:**
> each had their own user account .. just that they also had access to the main account and could get in there (anyone can bypass the restrictions once the password is known, even though I did not set that up).

AS to the IQ .. I just judge by the amount of really dumb questions (not really questions but pleas for help .. no such thing as a dumb question if it really IS a question) that we get on another board where I help with maintenance problems for Windows users.  Especially the responses we get back.  One would think that a lot of users have severe difficulty in even writing their name.  K.I.S.S. (keep it simple, stupid) on that board is the RULE not the exception.
And MOST of those issues that come there are those of total lack of protection and safe internet practices. (with the "nobody told me" response.)

The inside joke is that most should have to take a drivers test to buy a computer .. and most would fail the first time.

But that's not stupidity, that's lack of education.

If a new Linux user isn't educated they may well install software from a non trusted source, and be unaware that they may compromise their installation. 

They may also visit a phishing site and have their identity stolen, or their bank account emptied.

Education is the answer, not mockery.

---

### Post by oldsoundguy on 2008-10-17
Old adage: "You can lead a horse to water but you can't make him drink."  THAT is the problem.

---

### Post by Raccoon1400 on 2008-10-17
> **oldsoundguy said:**
> 

The inside joke is that most should have to take a drivers test to buy a computer .. and most would fail the first time.

I'll have to agree with that. My first computer that was connected to the internet was windows ME, and I downloaded a ton of free screensavers and stuff like that. After it was into the shop to be whiped clean, it was okay, but still not great.

---

