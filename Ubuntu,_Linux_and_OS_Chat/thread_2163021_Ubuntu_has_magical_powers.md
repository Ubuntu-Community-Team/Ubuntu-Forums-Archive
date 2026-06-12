---
title: "Ubuntu has magical powers"
date: 2013-07-16
forum: Ubuntu, Linux and OS Chat
---

### Post by LT72884 on 2013-07-16
What you are about to hear is no myth or legend, but rather a tale of a young lad with a puzzle of all puzzles.

Ok, my intro is done. Here is what has happened. As of 3 months ago, my wifi card on my xp laptop stopped working. It would never show up in device manager i would flip the switch to see if that would do anything. nothing. I took the whole thing apart, still no go. So i came to the conclusion that it was physically burned out.

So, 3 months later, last week, i download a copy of 13.04. I run the live cd and had to stop the install because of a small issue. So i turned off the laptop to install at a later time. A few days later, i log into windows and out of no wheres, my wifi card is working. It connects to my AP and so far the last day or so, it has been working. Its magic i tell you.

Ok so my conclusion is that there may be a software glitch causing the issue or it really is a flaky card and its just giving me the last bit of hope it has..

any thoughts?

thanks

---

### Post by cariboo on 2013-07-17
This isn't really a support question, moved to Ubuntu, Linux and OS Chat.

---

### Post by Copper Bezel on 2013-07-17
Software glitch is very unlikely, because Ubuntu wouldn't fix that. (Is there possibly a toggle in the hardware to deactivate the card? Ubuntu could have flipped *that*.)

Just as likely, yeah, it's a last gasp of radio frequency life in between a short hiatus and the long one. = ,

---

### Post by grahammechanical on 2013-07-17
Now, it can be revealed! There is secret code in every version of Windows that detects the running of Ubuntu live session. This code triggers a 'smarten ourselves up' response in the OS as an attempt to dissuade users from over-writing Windows. :)

The install likes to have the machine connected to the network while it is installing. And there are commands in Linux to force network adapters into life. That is what most likely happened.

I have been studying the script that is used in Recovery Mode>Network and that has instructions for

a) check for existing connectivity
b) start by trying to bring everything up
c) try running dhclient on everything else.

May be the Ubiquity installer does something similar.

Regards.

---

### Post by kurt18947 on 2013-07-17
I had a somewhat related experience recently with everybody's current Windows fave, 8.  Family member bought a cheap Toshiba laptop & Logitech wireless mouse.  Plugged the mouse in and it worked as expected.  Few months later I'm helping her with a wireless networked printer issue - another Win 8 story - and she complained about buying a pack of 24 batteries and they were all bad -- her mouse worked intermittently if at all.  Hmmm, really?  Dragged out Thinkpad X61 running Ubuntu - never leave home without it when on a computer related rescue mission and plugged the mouse dongle in.  Mouse worked great, batteries are not the problem.  Hmmmm. Downloaded the driver from Logitech and now the mouse works as expected.  Users have to download and install a driver to get their common wireless mouse to work properly?  In 2013???  Really????  Uncommon hardware of course I'd expect to have to download and install proprietary drivers but a wireless mouse from Logitech?

---

### Post by Copper Bezel on 2013-07-17
We're spoiled. Horribly. Having a monolithic kernel and no meaningful commercial support both press Linux to include drivers for everydamnedthing in a base install, which isn't necessary in Windows. It'd still make the Windows UX *better*, but it's not necessary, so people ship still write their own weird drivers and ship printers and mice and USB hubs with their dumb little installer CDs.

---

### Post by LT72884 on 2013-07-18
> **Copper Bezel said:**
> Software glitch is very unlikely, because Ubuntu wouldn't fix that. (Is there possibly a toggle in the hardware to deactivate the card? Ubuntu could have flipped *that*.)

Just as likely, yeah, it's a last gasp of radio frequency life in between a short hiatus and the long one. = ,

ok we are on day 4 or 5 of the test and still wifi works. this is begining to scare me. haha. 

another conclusion i have come up with, when i noticed it actually connected, i had the dvd drive open because i didnt want to run the live session of ubuntu yet. I am wondering if the drive is physically touching the wifi card and shorting it out? 

but i still think its magic.

Kind of like the times when the printer wont work at all and then you try a simple ping and then it works....... the magic and sorcery of ping. 

however, i do need a better wifi card. the one that is built in is from 2007 and the fastest it goes is 54mbps.

---

### Post by williamwright-orsk on 2013-08-01
I found Ubuntu can do some magic. I have a Microsoft PS2 Intellimouse, it is by far the most confortable Mouse I have ever used and I connect it with a PS2 to USB converter. However, I bought a pc using Windows 8 and it would stop working for a few seconds at Login. 

After realising Windows 8 was a heap of bloated junk (20GB of Hard Drive space!) I installed Ubuntu. My Mouse works perfectly and I have had such a lovely experience with Ubuntu compared to the 13 Years I have been using Windows!

---

