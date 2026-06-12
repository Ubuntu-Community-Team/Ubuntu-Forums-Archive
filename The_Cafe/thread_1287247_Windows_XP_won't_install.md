---
title: "Windows XP won't install"
date: 2009-10-09
forum: The Cafe
---

### Post by tbrminsanity on 2009-10-09
I've encountered a very rare site today.  I was setting up my parents new computer and it wouldn't take Windows XP at all (the install process always ended with a blue screen of death).  My father bought the computer from a dealer in Israel (something I advised against but my dad saw a deal and jumped on it).  It's a Lenovo Desktop (sorry I don't remember the modle number).  After numerous different attempts to try install Windows XP (My mother refuses to use ANY other OS because she couldn't be bothered to take the time to learn anything else), I decided to check if there was a problem with the hardware.  I put in my father's Kubuntu CD and installed Kubuntu 9.04 (without a hitch).  When I tried to install Windows XP again over Kubuntu, I got the same BSOD (ARGH!!!).  

Does anyone know why Windows would fail to install but Kubuntu installs without any problems at all?  This is a fairly new Lenovo Desktop (there wasn't any dust at all on any component inside the box), but it is a Jewish model (I say this as it came with a Hebrew keyboard, and the manual was in English and Hebrew).  Is Windows region coded?  How can I install Windows on this damn machine (sorry running Kubuntu or ANY other OS is not an option, I wish it was but it isn't)?

---

### Post by jeremyswalker on 2009-10-09
IMO, the hard drive may have bad sectors. In my experience, Linux tends to play nicer in such a situation than Windows.

I actually just had a similar situation at work. Windows kept giving me BSOD. So, I installed Ubuntu to check things out. Ubuntu was fine, not even a hiccup. After further investigation with smartmontools, I discovered bad sectors on the drive.

---

### Post by cariboo on 2009-10-09
I would suggest you install Vista or wait until Oct 29th and grab a copy of Windows 7, it wouldn't surprise me if there was some weirdness in the bios to stop XP from being installed.

---

### Post by fmartinez78228 on 2009-10-09
This is probably meant for a Windows forum, but I've recently have had problems with the "Blue Screen of Death". My best suggestion would be to research the error message on the blue screen and see what you come back with. You can also check Windows HCL site to see if the hardware installed is compatible. Maybe the the foreign parts but that's a real stab in the dark... LOL
[http://www.microsoft.com/whdc/hcl/default.mspx](http://www.microsoft.com/whdc/hcl/default.mspx)
hope this helps.

---

### Post by Tipped OuT on 2009-10-09
It's the drivers.

---

### Post by hobo14 on 2009-10-09
> **cariboo907 said:**
> I would suggest you install Vista or wait until Oct 29th and grab a copy of Windows 7, it wouldn't surprise me if there was some weirdness in the bios to stop XP from being installed.

That's a joke right?

---

### Post by cariboo on 2009-10-09
That's usually a good reason for a blue screen, but if it is a white box oem copy of XP it should install without blue screening. Drivers for sound video and networking will probably have to be installed to get everything to work properly, unless the hardware is so new that there are no XP drivers available.

---

### Post by hoppipolla on 2009-10-09
> Windows XP won't install

Yay! lol :)

---

### Post by MasterNetra on 2009-10-09
> **cariboo907 said:**
> That's usually a good reason for a blue screen, but if it is a white box oem copy of XP it should install without blue screening. Drivers for sound video and networking will probably have to be installed to get everything to work properly, unless the hardware is so new that there are no XP drivers available.

Low cost computer at a discount with new hardware? Usually don't happen. ^.^

---

### Post by cariboo on 2009-10-10
I recently set up a system with an ECS all-in-one motherboard with the cpu soldered to the mb, the manufacturer didn't have any XP drivers available for the audio device. This motherboard with cpu retails for about $80.00CDN, that's pretty cheap to me. :)

---

### Post by Firestem4 on 2009-10-10
Where is the blue screen happening during the Windows XP installation or Setup? The most common problem is that you need to load SATA drivers for the hard drives. If you do not have sata drivers than there is another problem. having more information would be helpful.

---

### Post by abhilashm86 on 2009-10-10
btw what work your parents need to do in computer?? if its basic things, word, brosing and stuff, show them a demo for 10 min, it should be good with ubuntu:) 
sorry if i'm wrong!! i did this for many people who were afraid of virus, slowdowns and stuff near my home........

---

### Post by RichardLinx on 2009-10-10
Run Dban and wipe the HDD completely, then try install WindowsXP. Might work..

Edit: You were installing it on an NTFS or Fat file system, right?

---

### Post by Exodist on 2009-10-10
> **cariboo907 said:**
> I would suggest you install Vista or wait until Oct 29th and grab a copy of Windows 7, it wouldn't surprise me if there was some weirdness in the bios to stop XP from being installed.

Worst advice ever..   Sorry. It really is.



1) Check the drive for errors. If no errors go to 2, else fix errors.
2) Try to low level format the drive, it may have something in the MBR preventing another version of windows being installed. I have seen this with prebuilts.

Also another thought, what version of XP are you installing? Does it have any service packs preinstalled on the CD. I have seen some original versions of XP with no service packs not install on some hardware do to driver and hardware issues.

---

### Post by Teber on 2009-10-10
the other hardware issue could just be a faulty ram chip. this has been known to cause blue screens. 

however. i know of a lenovo desktop computer where windows xp would seem to be somewhat different...

if this sounds like gibberish, the fault would be entirely mine :)

---

### Post by perce on 2009-10-10
Check if the Windows disk has any problem. If it doesn't, there are only two reasonably solutions: either you install Ubuntu and tell your parents that's all what they can get, or return the computer because it obviously has a problem. You are not supposed to have fix hardware problems in a newly purchased item.

I suggest the second option, because if there are hardware problems, they may arise in Ubuntu too, sooner or later.

---

### Post by Exodist on 2009-10-10
> **perce said:**
> Check if the Windows disk has any problem. If it doesn't, there are only two reasonably solutions: either you install Ubuntu and tell your parents that's all what they can get, or return the computer because it obviously has a problem. You are not supposed to have fix hardware problems in a newly purchased item.

I suggest the second option, because if there are hardware problems, they may arise in Ubuntu too, sooner or later.

You may want to take in the fact that its a used system at a discount.

---

### Post by SkyNet2029 on 2009-10-10
A blue screen at installation can also be caused by an invalid HAL being initialized during setup. 
During the first phase of setup.. the bit about pressing F6 to install drivers..
Press F5 here to specify a non-standard HAL.
You may have to just go through each one before you find the one that worls for this machine. (the wrong ones will BSOD while initializing the hives for the registry.

---

### Post by jonian_g on 2009-10-10
For me, it is not a hardware failure. It is a WinXP failure.
Since the computer works with another OS, then the hardware is fine.

If your mother insists for windows then you might want to try installing Vista or 7.

---

### Post by Teber on 2009-10-10
on further thought: i think we should show some respect for the OP's mother. he certainly does, and so he should seeing how much he owes to her.

i really respect the OP for giving his father sound advice and going to a lot of trouble to solve this issue.

mefears there are only two options? make a last ditch effort to install xp or condemn the computer to recycling?

edit: please note buyer and seller seem to live on different continents

---

### Post by I-75 on 2009-10-10
If one exists, try to find a reinstall disc from the manufacturer. 

 Second, if using a older XP disc (installs on PATA/IDE only) on a modern computer with a SATA hard drive..it won't work unless you load the SATA drivers first (usually from a floppy). 

Third, get a fairly recent XP  disc as this would have the SATA drivers built into the OS. 

 As far as computers or OS's with region differences. The only possible differences would be language or maybe DVD playback.

Is the XP disc scratched? Is it a legit disc? Is the CD/DVD player working correctly? 

 Why would Karmic work and XP doesn't? The only possible conclusions is the XP disc is defective. Or the XP disc doesn't support SATA (and your computer has a SATA hard drive).

---

### Post by noelvh on 2009-10-10
It is in MHO the hard drive. I have run into this with SATA hard drives. You may have to get the SATA drivers from the Lenovo web site. During the install there will be an option to load drivers by perssing F6 key. You should be able to load them on a floppy and add them to the install. There may also be SATA options in the BIOS, and simply changing them could help the install. 
I know this can drive you nutz, but I think if the drive is not bad loading the correct drivers during the install will fix this issue.

Noel

---

### Post by tbrminsanity on 2009-10-10
> **cariboo907 said:**
> I would suggest you install Vista or wait until Oct 29th and grab a copy of Windows 7, it wouldn't surprise me if there was some weirdness in the bios to stop XP from being installed.

This is defiantly NOT an option.  My mother ONLY uses Windows XP and NOTHING else.  We had to fight with her for almost a year to switch from Win 95 to XP and even then I had to make XP look and run as close to 95 as I could before she finally gave in.  If ReactOS was in full productions I would consider that (as it has a Win 95 look and feel) but Vista and Win 7 are defiantly out.

---

### Post by Jimleko211 on 2009-10-10
Why not replace the hard drive?  The consensus on a few posts were bad sectors, so go in there and just replace the hard drive.  It'll set you back a few hundred dollars or something but it's better than wasting money on a comp that your parents won't even use.

---

### Post by jeremyswalker on 2009-10-10
> **Jimleko211 said:**
> Why not replace the hard drive?  The consensus on a few posts were bad sectors, so go in there and just replace the hard drive.  It'll set you back a few hundred dollars or something but it's better than wasting money on a comp that your parents won't even use.

A few hundred dollars?? Last I checked, new hard drives were as low as $30 - $40.

---

### Post by AnarchyCow on 2009-10-10
I would agree with Noelvh on Checking the SATA drive operation settings in the BIOS.
Often with newer computers, sometimes the SATA drive operation comes shipped with the "AHCI" or "RAID" settings. Try to change it to IDE? I've had multiple BSOD's at my work because the Drive Operation was set incorrectly for the install media present.
I'd imagine that installing the SATA drivers would also resolve this issue if you want to use "AHCI" mode instead of "IDE".

TBH, I do not personally know the difference between the two, maybe a performance difference, or something, but that should resolve the issue usually (Considering that the BSOD occurs during installation)

And I highly doubt that this computer would be able to run Vista very well at all. It is a memory hog. :P. I run it on my main computer, just because it's hard for me to game with Ubuntu, and my Ubuntu box has a Pentium 4, 1GB of ram, and a onboard gfx D:

---

### Post by Tipped OuT on 2009-10-10
> **Teber said:**
> the other hardware issue could just be a faulty ram chip. this has been known to cause blue screens. 

however. i know of a lenovo desktop computer where windows xp would seem to be somewhat different...

if this sounds like gibberish, the fault would be entirely mine :)

No, I had that happen to me before. I had a faulty RAM chip, started up Windows XP, and got an instant BSOD and corrupted my MBR.

---

### Post by Skripka on 2009-10-10
> **tbrminsanity said:**
> This is defiantly NOT an option.  My mother ONLY uses Windows XP and NOTHING else.  We had to fight with her for almost a year to switch from Win 95 to XP and even then I had to make XP look and run as close to 95 as I could before she finally gave in.  If ReactOS was in full productions I would consider that (as it has a Win 95 look and feel) but Vista and Win 7 are defiantly out.

All I will say is that by letting her get stuck in her ways, she's only doing a disservice to herself.  The only constant is change.  Sooner or later she'll have to, she might as well get over it now.

---

### Post by CharlesA on 2009-10-10
Set the SATA drives to use IDE instead of AHCI and see if that lets windows install and boot without a BSoD.

---

### Post by SACHINVD on 2009-10-10
try installing XP on another partition except C

---

### Post by quinnten83 on 2009-10-10
> **tbrminsanity said:**
> I've encountered a very rare site today.  I was setting up my parents new computer and it wouldn't take Windows XP at all (the install process always ended with a blue screen of death).  My father bought the computer from a dealer in Israel (something I advised against but my dad saw a deal and jumped on it).  It's a Lenovo Desktop (sorry I don't remember the modle number).  After numerous different attempts to try install Windows XP (My mother refuses to use ANY other OS because she couldn't be bothered to take the time to learn anything else), I decided to check if there was a problem with the hardware.  I put in my father's Kubuntu CD and installed Kubuntu 9.04 (without a hitch).  When I tried to install Windows XP again over Kubuntu, I got the same BSOD (ARGH!!!).  

Does anyone know why Windows would fail to install but Kubuntu installs without any problems at all?  This is a fairly new Lenovo Desktop (there wasn't any dust at all on any component inside the box), but it is a Jewish model (I say this as it came with a Hebrew keyboard, and the manual was in English and Hebrew).  Is Windows region coded?  How can I install Windows on this damn machine (sorry running Kubuntu or ANY other OS is not an option, I wish it was but it isn't)?

Hvent read the rest of the thread yet, but if it is a lenovo you need to change the HD to compatibility mode in the bios, otherwise windows will not take.

---

### Post by tbrminsanity on 2009-10-11
> **Skripka said:**
> All I will say is that by letting her get stuck in her ways, she's only doing a disservice to herself.  The only constant is change.  Sooner or later she'll have to, she might as well get over it now.

There are people in this world that will never change no matter what.  It is our job as IT professionals to adapt to them, unfortunately.  I know what your saying but some people are so set in their ways that they will never change their mind (like try convince a Catholic Cardinal that Islam is the one true religion, it just isn't going to happen no matter how good your argument is).

This is where I see Open Source as more attractive to non-technical people.  If I teach someone to get use to Linux and it is user friendly enough that they don't face any problems in their day to day lives, then they can stay in their little rut indefinitely (even though their system is constantly updating to the latest protocols every day in the background).  I've tried to ease my parents to Linux in the past (my father runs it on all his laptops so that was a partial success) but I really need to train my mother in all the different programs before she will switch over.  Currently my plan is to slowly replace her old Windows programs with FLOSS equivalents (that run on both Windows and Linux).  The $0 price tag helps, along with the guarantee that the UI won't change drastically overnight.  It's a long road though.

---

