---
title: "To Tom--Two More Questions"
date: 2008-05-06
forum: System76 Support
---

### Post by OrcaWave on 2008-05-06
Dear Tom,

  You said that it's OK to ask more questions, so here goes.

I thought of this tonight and I realized that these are pretty important questions.

1. Is there someway to do like 7 pass wipe (a Mac would do a 1 pass wipe, 7 pass wipe, and a 35 pass wipe, via an install disk) of the hard drive on your computers?

If so, how would one go about doing that? Would I have buy more software to wipe the hard drive? Or what?

2. Is there a way to "flash" the BIOS without having to mail the box back to you guys there in CO.?

The 9 "good months" that we had our I-Mac G-5 on the internet, I wiped the hard drive and re-installed the OS, 11 times.

He finally found a way around what I was doing, but it took him nine whole months to do it.

And I can tell you whenever I re-installed the OS, it really P.O.ed him in a big kind of way!  LOL

Secondly, the BIOS. On our HP, HP demands that you mail the box back to them, and they then charge you to flash the BIOS.

The only real way around this, is buying another mother board with a kind of generic (or non HP) BIOS on it.

That would wreck HP's little capitalist party now wouldn't it?

As it stands, there's an unremovable "smiley face" program on the BIOS of the HP that has some sort of Administrator contol over the whole box, and a keylogger in it as well.

If this should happen again, I want to know that I can solve it by myself, or with help from you guys here at the Ubuntu Forums.

It seems wrong that I cannot "flash" a BIOS, on a machine that I OWN.

Thanks again for your time. Very kind.  :)

Orca Wave

---

### Post by intrepidx on 2008-05-07
Hi Orcawave,

The program located at the below link is capable of performing a wide variety of data destruction:

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

But I note this is almost certainly irrelevant for handling the case of a compromised system.  Wiping a hard disk in this manner would be done (for example) if you were losing physical control of a disk, and wanted to ensure that nobody could recover the information it contained.  No matter what your situation, if you want to get up and running after an attack, performing a 7-pass wipe is no better than just completely re-installing your operating system.

I will leave your question about BIOS flashing to people more knowledgeable about System76 hardware, but this is not a focus many people would have in terms of Linux security.  The emphasis would be on preventing an attacker from making such changes in the first place.  A major lesson when using Linux is to never run software with more permission than it requires; for example, don't type in your root password to install a cool game/toolbar your stalker sent you.  Most of the software required by regular users is available using a package manager called Synaptic, which authenticates downloaded content.

Linux is a well tested and generally very secure operating system, and unless grossly misused will provide you with all the security you need.  I hope you seek to continue your computer education, and I encourage you to read pre-existing posts on this site, and also check out some of the great/free books that are available:

[http://www.linux.org/docs/online_books.html](http://www.linux.org/docs/online_books.html)

---

### Post by thomasaaron on 2008-05-07
> 1. Is there someway to do like 7 pass wipe (a Mac would do a 1 pass wipe, 7 pass wipe, and a 35 pass wipe, via an install disk) of the hard drive on your computers? If so, how would one go about doing that? Would I have buy more software to wipe the hard drive? Or what?

Not that I'm aware of. I'll defer to Intrepidx on that one.

> 2. Is there a way to "flash" the BIOS without having to mail the box back to you guys there in CO.?

It is entirely possible for you to flash the bios on your computer. However, I also do not recommend it unless System76 requests it as a bug fix. The reason is that flashing the BIOS has the potential to completely and irrevocably hose your computer. BIOS flashing is not that hard to do. But it's also not that hard to do wrong.

When a bios update is necessary, we provide instructions. And if you hose a computer doing an un-recommended bios update, it can't be covered under warranty.

Also, most BIOS updates are for improvements in running Windows on the system. Many of them have little or no effect on Linux.

> If this should happen again, I want to know that I can solve it by myself, or with help from you guys here at the Ubuntu Forums.
It seems wrong that I cannot "flash" a BIOS, on a machine that I OWN.

We differentiate between "cannot" and "do it at your own risk." Again, we will from time to time recommend bios updates. If you had an emergency situation, we could probably give you some instructions for flashing it. That said, if it were not a recommended update, I'm not sure that we could cover it under warranty if you did it wrong and hosed the motherboard. I'd have to check with my supervisors on that one. My best guess is that they would take it on a case-by-case basis.

That said, you are absolutely right. It is YOUR machine. And the rights and responsibilities of ownership are yours.

---

### Post by OrcaWave on 2008-05-07
Believe me Tom, I WON'T do ANYTHING that would cause our new machine to get messed up.

And I will ALWAYS ASK you guys there at System 76 before I do anything, when (or IF) I need help with our new box!

Hopefully, the way that I'm gonna set up this machine and the various "barriers" in front of the machine (between it and the internet) will be very, very, very hard to get through.

$6,000.00 spent on computers, and computer repairs, is ENOUGH!

Thanks to both of you for answering.

Orca Wave

---

