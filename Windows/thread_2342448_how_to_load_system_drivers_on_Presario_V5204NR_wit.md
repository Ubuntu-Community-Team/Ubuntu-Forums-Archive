---
title: "how to load system drivers on Presario V5204NR with Zorin OS9"
date: 2016-11-06
forum: Windows
---

### Post by ceemer on 2016-11-06
My Newbie question...any assistance welcome!
We have a physically healthy Compaq Presario V5204NR laptop (V5000 series) with Celeron M CPU (not the usual AMD chips), 2GB RAM, otherwise stock.
It had WinXP--which got corrupted. I got it to work again with Zorin OS9 and some fiddling. This erased all WIN stuff, plus OEM drivers. 
But...daughter needs to use XP, dislikes Linux.
I learned to create 18.5 GB NTFS partition w/ Gparted--space enough for drivers,XP, and Word.
Zorin still working OK.
XP will not install because it can't find factory drivers--which I can't figure out how to install. I think I succeeded in burning them from a website to CD. That's as far as I can get.
Surely there's a way. But my skill with Linux is...limited. 
I did search extensively...but nothing I found does squat.

Any thoughts, anybody?
Thanks in advance,
"ceemer"

---

### Post by howefield on 2016-11-07
I'm pretty sure that you know that XP is hopelessly unsupported now and not a great choice of system ?  

Which drivers is the machine looking for that prevents it from installing, is it sata drivers for the hard disk ?

The normal way to dual boot in this sort of scenario would be to install Windows first then Linux, you will probably need to fix grub doing it the other way round.

---

### Post by ceemer on 2016-11-07
Thanks for reply!
1. Machine can't find HDD--I infer it's looking for SATA driver(s), since the computer has a 60GB SATA.
2. Yes, XP is all you said. But I own it, hate Win8/10, and Can't afford a Win7 install. Hence my choice. OS9 isn't an optimal district...but it is the one that made the Presario "open up" again. No version of Ubuntu or Mint that I tried did that, alas.
My problems are doubtless due to lack of fluency in Linux. It's not easy for an old guy with zero experience in coding, and no idea where a "Linux logical" start point for learning is. Apologies for ignorance.
3. Yes, I know loading Linux alongside a working Windows setup is "normal" and easy. But the XP that WAS loaded was totally messed up and would not restore...so I gave up and did full erase//install of (finally) Zorin. That worked.
I keep thinking, if I find a way to insert the proper system drivers, XP will be accepted, and I can push on from there. But it isn't working out that way.
Woould it be smarter to use Gparted to format the whole disk in NTFS and then try other things?

---

### Post by howefield on 2016-11-07
> **ceemer said:**
> Machine can't find HDD--I infer it's looking for SATA driver(s), since the computer has a 60GB SATA.

That sounds about right.

> Yes, XP is all you said. But I own it, hate Win8/10, and Can't afford a Win7 install. Hence my choice. OS9 isn't an optimal district...but it is the one that made the Presario "open up" again. No version of Ubuntu or Mint that I tried did that, alas.

Sure, your machine, your choices.

> My problems are doubtless due to lack of fluency in Linux. It's not easy for an old guy with zero experience in coding, and no idea where a "Linux logical" start point for learning is. Apologies for ignorance.

Well no, this isn't about a lack of fluency in Linux, this is purely a windows problem.

> Yes, I know loading Linux alongside a working Windows setup is "normal" and easy. But the XP that WAS loaded was totally messed up and would not restore...so I gave up and did full erase//install of (finally) Zorin. That worked.

That is not what I was getting at or said, I'm saying that installing Windows will over write the grub boot loader meaning you will only be able to boot to Windows, until you fix that issue. Not a huge deal but one that will need to be addressed.

> I keep thinking, if I find a way to insert the proper system drivers, XP will be accepted, and I can push on from there. But it isn't working out that way.
Woould it be smarter to use Gparted to format the whole disk in NTFS and then try other things?

It would be smarter to use another windows computer to create the diskette containing the hard disk drivers that XP needs to proceed with the installation. The driver on the HP site, assuming that I am looking at the correct one looks like an .exe file which probably self extracts to a diskette (floppy drive?) and will need to be created with a windows machine.

---

### Post by ceemer on 2016-11-07
Kind thanks for your patience.

I can make a diskette, but don't have external diskette drive (Compaq lacks one). Have tried downloading drivers from HP, burning to CD, then trying to run each therefrom. Must be doing it wrong...no success. I'm positive my ignorance is getting in the way. Since I now live in the boonies, can't locate anyone savvy about Linux.

you're entirely correct about XP. But...I feel that if I can get somewhere with it, I'll have a better grasp of various essentials. 

Another imaginable option I thought about...I have a complete old Windows 98 set. At one point, XP was a viable "upgrade" for it. But even to me, that seems a bit of a stretch.

I'll look around and see if I can find an external floppy drive to try your advice. 
The practical side of me says, this is a ridiculous project. The rest of me hates to give up for lack of trying.
Thanks again.

---

### Post by howefield on 2016-11-08
There used to be a way of integrating the drivers into the XP installation media using nLite. Don't know if it is still around or available but might be worth looking into. You'd still need another Windows computer to use it though.

---

### Post by ceemer on 2016-11-08
Thanks for your patient assistance.
Found a Wiki alleging it's possible, via Win7, to create a bootable flash drive onto which I can load e.g. drivers. I'll try it this week sometime, with wife's Win7 PC, and see. Might do the trick.
Also found USB diskette drives on the 'bay...didn't even know they exist. Would rather not add to my mound of archaic gear, but if's an option, so thanks for the hint.
All this would be obviated if MS hadn't quit supplying downloads of legitimately owned but loused up OS's. Blast them anyway.(Or, if I could coax the family to get used to Linux...)
If I have luck with the above, I'll report back on what worked.
Thanks again and be well.

---

### Post by ceemer on 2016-11-09
Dear Mr. Howefield,
I have sourced a USB floppy drive (since I still have lots of diskettes). It'll be here in a week or so. I shall try as you suggest...a bootable floppy with the SATA drivers, hoping I'm finding the right ones. 
But here's my conceptual problem. I've already failed 3 times to load drivers that I thought were burned to a bootable CD. They don't seem to "know where to go." I formed an NTFS primary partition in Zorin. Another source said that was necessary, and it makes sense. 
So, I'm missing a step or two--and this is my ignorance in play. 
As I have no other option but to prevail upon your kindness,
how the dickens shall I force these drivers to settle into the right place, so that my Windows disk can find them and deploy?
if I can get that far, I believe I can carry on. 
Sorry for the bother.

---

