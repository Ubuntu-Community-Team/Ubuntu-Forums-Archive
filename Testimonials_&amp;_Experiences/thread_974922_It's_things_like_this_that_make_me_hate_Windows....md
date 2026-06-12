---
title: "It's things like this that make me hate Windows... and make me love Ubuntu  :)"
date: 2008-11-08
forum: Testimonials &amp; Experiences
---

### Post by AFarris01 on 2008-11-08
I would just like to vent my frustrations a little bit, and share with everybody my recent experiences with trying to fix my parents' computer.

Ok, so a little background.  My parents, are both what one would consider the 'typical computer user.'  they check email, read documents, surf the web, occasionally burn cds/play games, and manage an extensive photo collection.  Their computer is a HP pavilion media desktop, that they bought brand new about 5-6 yrs ago.  It's been trouble ever since.

About a year or so back, I was talking to my dad about linux and Ubuntu, and he actually wanted me to install it on their PC, because he wanted to give it a try.  He's loved it ever since, and uses it exclusively for just about everything, except for email (which he still uses AOL for on windows... dont ask me why.) but anyway, onto my ranting...

About 2 weeks ago, my parent's computer started acting funny, randomly shutting off and whatnot, for no reason at all.  Turned out that every single capacitor on the CPU main power circuit had blown, and they needed a new motherboard.

So, after searching around for a bit, it turned out that to replace their motherboard, and keep everything else, it would have been more expensive than upgrading to a better board, better processor, and a new graphics card.  so, of course, the folks want the cheaper route, so i order up some parts and prep to repair their computer.

Well, this Thursday all the parts came in, everything tested out ok (nothing DOA) so i went ahead and swapped the parts into their computer.  I knew i was going to have issues with windows and the new hardware, because since the stupid thing kept shutting down because of the faulty capacitors, i couldn't properly prep it to receive the new hardware. however, i was a little more nervous about how Ubuntu would handle, since i had never tried a hardware change that drastic on it before.

anyway i installed all the hardware, and rebooted... whats the first thing i see? GRUB! yey i think, this is looking good so far... so I booted into Ubuntu just to check out what it would do... and it started right up, set up a new driver for the new graphics card, and off it went!  i went ahead and replaced the default driver with the proprietary driver to get the full 3D effects out of the new graphics card, rebooted, and again everything went perfect.  Hurrah!  In the space of about 30 min, i replaced 80% of the essential hardware in my parent's computer, fired it back up, and got Ubuntu back to it's previous state!  I was feeling good, but i knew the worst was yet to come.  little did i know how bad the worst would really be...

so... i braced myself and went and tried to boot windows. Black screen.  no boot logo, no error message, just a black screen.  So i'm thinking oh great, here comes a reformat.  Unfortunately, HP in their infinite wisdom decided to NOT include any windows disks with the PC my parents bought... instead, they set up some auto-recovery partition crap that 'did all the same things'  yeah...my rear end it did.  i try to use this 'recovery partition' to to a simple repair install on their installation so it would re-setup all their (new) hardware, so i could at least boot up and fix it proper.  nope, no dice.  i try the repair install, and after sittign there for 30 min waiting for it to finish, it locks up right at the end...wont go to the desktop.  terrific, probably has to do with the new hardware, right?  wrong again!  i reboot, and try again, and this time it boots up into windows normally!  but, it takes it literally 20 min to go from 'cursor on the screen' to 'icons showing up on the desktop.'  i'm already irritated at this point, but i'm figuring i had it coming anyway, seeing as how i couldnt properly prepare windows to recieve the new stuff.

Oh, but it wasnt done yet!! oh no, not at all! apparently, what HP means by 'repair install' is "We're going to re-install all the trial crap and bloatware that you didnt want, and that you uninstalled 4 years ago, all for you, and all automatically, with no say from you whatsoever!"  WHAT THE HELL!  I've spent many hours over the last few years honing their install so it would perform well on the old single core P4 they had, and in the course of a single day, HPs 'auto-recovery' bullcrap managed to dump so much software on the PC that it was bogging down a brand new dual core proc!  

SO... i've spent about 10 hours since that time going back through and uninstalling all the garbage that the "recovery" dumped back on there, only to discover that it had also wiped out their .NET framework, and the SP2 and SP3 installs (the pc shipped with SP1)!!  So, after all of the purging and cleaning, and reinstalling all these essential OS patches i am JUST NOW at 11PM friday getting to re-install some of the software that they need/had to begin with (antivirus, office, anti-spyware, 7-zip, AOL etc...) I've spent a total of ~13 hours working on this computer now, ~30 min of which was spend re-configuring Ubuntu, and ~12.5 hours of it was spent trying to reconfigure Windows... and I'm STILL NOT FINISHED!!

It took me less time to install/configure Ubuntu from scratch, and reinstall all my apps, after downgrading from 64 bit to 32 bit.

I just wanted to take a little break from the endless fiddling with windows, and vent my frustrations to those who may have found it a bit entertaining.

After this experience, I can honestly say that I will find it hard to take seriously anybody who says "linux is hard to configure" or "linux takes too much tinkering to get working".  HA! I fix windows comps as a business, so speaking from experience, the difference between windows and linux is this: If something in windows breaks, you've gotta pay to have somebody fix it, if something in linux breaks, you can fix it yourself.

Sorry about the long post everybody!  Hopefully you'll find it an interesting read at least!

---

### Post by freebeer on 2008-11-08
It was interesting.  Thanks for posting.  All I can say is I feel for you... I went through the same thing but on a new machine.  30 minutes for Ubuntu, 12+ hours for Windows due to (mostly) driver issues (and I had the disks!)

---

### Post by wolfen69 on 2008-11-08
> **AFarris01 said:**
> HA! ***I fix windows comps as a business***, so speaking from experience, the difference between windows and linux is this: If something in windows breaks, you've gotta pay to have somebody fix it, if something in linux breaks, you can fix it yourself.



i hear you bro. i always give my customers a discount if they wipe windows and install linux. it's just soooo much quicker and easier (most of the time) to install linux. i'm usually done installing ubuntu in less than an hour. :D

---

### Post by ad_267 on 2008-11-08
It's so true. The people that complain about how hard Ubuntu is to install have never had to install Windows. I would've given up and told my parents they just had to use Ubuntu. :D

---

### Post by wandalalakers on 2008-11-08
> **ad_267 said:**
> It's so true. The people that complain about how hard Ubuntu is to install have never had to install Windows. I would've given up and told my parents they just had to use Ubuntu. :D

I was thinking the same thing.

---

### Post by lisati on 2008-11-08
And then there's the updates (some of which try to restart your machine when you're in the middle of trying to do something useful) and the patches from the manufacturer to fix the damage done by the updates.....

---

### Post by sloggerkhan on 2008-11-08
This post is so true.
A real windows install takes about 2 days if you count your drivers and software installs and configuration.

It's a huge reason I quit windows.

---

### Post by mobilediesel on 2008-11-08
The average Windows user has never installed Windows. It comes with their computer. I first installed Ubuntu in May of this year. I've noticed on this forum that most people who've installed Windows more than a few times end up using something other than Windows as soon as they can. Windows is only easy for those who bought a system with it already installed and pays someone else to maintain it.

I'm running Xubuntu 8.04.1 on a 700Mhz system. It performs as well as Vista did on a 3Ghz system I tested. That's just insane. 0.7Ghz Xubuntu performs as well as 3Ghz Vista.

---

### Post by AFarris01 on 2008-11-08
Thanks for the replies everybody!  glad to see not everybody is scared off by a long post :)

just as an update: last night around 1:30 or 2:00 I finally got the last of their software installed, ending with google sketch-up and MS office (my mom uses Access a lot, so i couldn't just keep them on OpenOffice...). so its finally done, more or less.  all i've gotta do now is update drivers :)

---

### Post by sc0tt10 on 2008-11-08
Lately its becoming more of a fact that the only people who like windows is the people who fix it for money. which is why I bloody love it.:D

---

### Post by Zzl1xndd on 2008-11-08
> **sc0tt10 said:**
> Lately its becoming more of a fact that the only people who like windows is the people who fix it for money. which is why I bloody love it.:D

Gotta agree with that. As my Signature says I'm an MCSA and I would never use Windows at home, but the pay is good for dealing with MS issues. At least till a get my Linux certs anyway.

---

### Post by WaeV on 2008-11-08
heh.  The other day I finally replaced my CD/DVD drive.  Ubuntu didn't even have a pop-up wondering about the change.  When I booted into XP it said "Your system has gone under radical system changes and will need to be reauthentica-" *BSOD*

---

### Post by Crafty Kisses on 2008-11-09
I've done this with many computers I've fixed. It's true and it can get frustrating, best of luck to you.

---

### Post by PurposeOfReason on 2008-11-09
So when was that Windows fault? Sounds like a HP issue to me. Windows doesn't not give you a disk but a flawed partition (which did say it would take you back to** factory** settings.:rolleyes:). Microsoft does not put the ads/bloat on. That is the distributer. Another HP issue.

Learn who to blame. If anyone, yourself for not backing up settings/files/recovery disks etc.

---

### Post by sneakersupplier on 2008-11-09
Wholesale Jordan shoes: [Air Jordan](http://www.sneakersupplier.com)

---

### Post by AFarris01 on 2008-11-11
> **PurposeOfReason said:**
> So when was that Windows fault? Sounds like a HP issue to me. Windows doesn't not give you a disk but a flawed partition (which did say it would take you back to** factory** settings.:rolleyes:). Microsoft does not put the ads/bloat on. That is the distributer. Another HP issue.

Learn who to blame. If anyone, yourself for not backing up settings/files/recovery disks etc.

Well... first off, I was just letting off a little built-up steam from my frustrations with dealing with their computer... 
nextly, I did have backups of settings and files, although Ididn't actually need them because the so-called 'repair install' was at least successful in that respect.
I admit that i've never made a recovery disk for that computer, but thats mainly because if it gets so screwed that I actually need it, it'd probably be better off with a fresh start anyway... plus I trust my own tools far better than I trust microsoft's.

And yes, I know microsoft doesn't factory install all that bloat onto the system, but they don't frown on it either... so that's still an issue.  Still, the bulk of the bloat issue was indeed HP's fault, but my main issues with windows was the lack of handling of the new hardware... if it had a decent system in place for taking care of new hardware installations in the first place, then I wouldn't have had to deal with all of HP's crap.  

And before you say it, I *know* there are *methods* to properly prepare for a hardware swap such as that, but that wasn't an option for me seeing as how all of the capacitors on their Mobo had exploded.

All in all, I think it's still a perfectly fair comparison... the same hardware change under two separate systems in a 'typical' environment, and all details aside, one of them (ubuntu) performed very well, and the other (windows) performed poorly. 

Hats off to Linus Torvalds and all the others who made this possible, especially the Ubuntu developers... thanks guys! you rock! :guitar:

Andrew

---

### Post by armandh on 2008-11-11
> **sc0tt10 said:**
> Lately its becoming more of a fact that the only people who like windows is the people who fix it for money. which is why I bloody love it.:D

are the people [plural] assuming there are still 2 left.

when the student XP disk I was using ran out of licenses I quit. now when some one wants windows I agree if they buy it, but not the configuration or upgrades. they can wait that out.

but since I only do friends and relatives computers for free I can be as difficult as I wish.

---

### Post by presence1960 on 2008-11-15
Most computer manufacturers have been using the hidden recovery partition for years now. If you would have checked the computers documentation you would have known that you have the ability to do a burn of the restore partition to CD/DVD. Also every computer manufacturer has it set that when you do a reformat/reinstall it puts everything back to the way it was when the machine left the factory. I used to own an HP and I was slick enough to break down the files on the recovery partition and separate the Windows install from all the software which came from the manufacturer. Thus I was able to install only Windows and then reinstall only which software I wanted. I have never had a problem with that HP and it is still going strong today. When I built my machine I gave it to my daughter who is now 6. She already knows Windows better than some adults I know, and is learning OSX in school. Maybe by her teens I can turn her onto Linux, but that will be her decision. 

Maybe if you had read the documentation that came with your parents computer you may have had less of a problem. I still refer to documentation for everything not just computers because I would be arrogant and foolhardy to think I know everything regardless of how much I actually know. It isn't HP's or Microsofts fault you neglected to check out the computers documentation. No one knows everything about everything even in their field of expertise.

---

### Post by srt4play on 2008-11-15
> **WaeV said:**
> "Your system has gone under radical system changes and will need to be reauthentica-" *BSOD*

hahahahahahahhahaahahaaa  :lolflag:

OP - Be sure to image that "new" Windows system just in case!

---

