---
title: "Recovering data from hard drive?"
date: 2009-03-25
forum: The Cafe
---

### Post by miggols99 on 2009-03-25
I have an WD Caviar SE (WD2500JS) which has recently failed. I turned on the computer to find it couldn't boot at all, not even past the BIOS. The hard drive clicked a few times, then it turned off. Is there any way to recover the data?

Unfortunately, there weren't any 'symptoms' to it dying, so I didn't get a chance to back it up. There weren't any strange noises coming from it before or anything like that...and the previous backups have been a bit wacky - loads of files don't copy over for some reason..

---

### Post by tom66 on 2009-03-25
Pop it into another PC and see what happens...

---

### Post by ramjet_1953 on 2009-03-26
Try Hiren's Boot CD.
It is a stand Alone CD that you boot from and has loads of disk utilities for recovering data.

You just download the iso and burn it to a disk, making sure that you burn it as an iso and also that you burn it slowly.

Here's a download link:

[http://www.givemesolution.org/my-software-collection/36-my-software-collection/48-hirens-bootcd.html](http://www.givemesolution.org/my-software-collection/36-my-software-collection/48-hirens-bootcd.html)

Regards,
Roger :)

---

### Post by az on 2009-03-26
> **miggols99 said:**
> I have an WD Caviar SE (WD2500JS) which has recently failed. I turned on the computer to find it couldn't boot at all, not even past the BIOS. The hard drive clicked a few times, then it turned off. Is there any way to recover the data?


Is it *detected* by the bios?  It's important to know when your computer freezes during bootup.  If it crashes trying to detect your drive, there is no other option than to open up your drive - something that you can't do yourself and which (therefore) costs a lot of money.

If the drive is detected, there is hope that you can use data recovery software to read the drive.

You can use Ubuntu-Rescue-Remix as a standalone live OS to try to recover the data or you can install ubuntu-rescue-remix-tools from another Ubuntu computer by adding this ppa to your software channels:

[https://launchpad.net/~arzajac/+archive/ppa](https://launchpad.net/~arzajac/+archive/ppa)


apt sources.list entries

deb [http://ppa.launchpad.net/arzajac/ppa/ubuntu](http://ppa.launchpad.net/arzajac/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/arzajac/ppa/ubuntu](http://ppa.launchpad.net/arzajac/ppa/ubuntu) intrepid main

Install the software and then image the disk using Gnu ddrescue.  If you get a complete image, you can mount it as a regular filesystem.  If not, you can can data-carve most of your data from the image.

See here:
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Good luck.

---

### Post by pwnst*r on 2009-03-26
boot with a Knoppix live CD, transfer files via USB

---

### Post by aeiah on 2009-03-26
if it spins up you can probably access it with a livecd. if not then you could take a screwdriver to it and try your luck. my dad, who isn't massivley computer savvy but is good with all aspects of DIY managed to open up his hdd, find that the platter head had jammed and fix it for long enough to get his data off.

if your data is worth paying sums of money for a disk repair / recovery service then it might be best to do that though, rather than poke around yourself.

---

### Post by mal_conductor on 2009-03-29
Try test disk and/or photorec.

These are my notes on these applications:
[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

### Post by cariboo on 2009-03-29
If your drive is dying during post, remove it from the computer and put it in the freezer for a couple of hours, after it is cold hook it up and try to access it.

Jim

---

### Post by NorthernSuze on 2009-04-02
Thank you for the freezer suggestion.  My /home sata drive went flaky and a good percentage of the data I was pulling off it was corrupted. I was able to recover an unbacked up portion of my data after putting it out the front door and running the cables back to my computer.

-14C weather in what for most of the world has is spring has its perks!:lolflag:

Thank you!
Suzanne

---

### Post by mips on 2009-04-02
> **NorthernSuze said:**
> 
-14C weather in what for most of the world has is spring has its perks!

I would hate to live where you live :shock:

---

### Post by NorthernSuze on 2009-04-02
@ mips
Believe me I look like your avatar at this time of year.  There is still enough snow out there to loose a Rottweiler in.  Snow drifts still above my head ... hands go to cheeks ... mouth opens in a silent scream ... is that a snowflake I see?!?!

Cheers
Suzanne

---

### Post by mips on 2009-04-03
> **NorthernSuze said:**
> @ mips
Believe me I look like your avatar at this time of year.  There is still enough snow out there to loose a Rottweiler in.  Snow drifts still above my head ... hands go to cheeks ... mouth opens in a silent scream ... is that a snowflake I see?!?!

Cheers
Suzanne

Lol, rather you than me.

I have a friend that emigrated to Toronto that also hates the cold. Guesse what his first job was when he just got there? Yip, shoveling snow :biggrin:

---

