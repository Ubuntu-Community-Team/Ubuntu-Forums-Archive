---
title: "Getting new laptop HDD via warranty. Will they screw me over, just reformat it?"
date: 2009-12-14
forum: The Cafe
---

### Post by MaxIBoy on 2009-12-14
If you see this crossposted in multiple forum websites, it's because I'm really frantic about this, not because I have no faith in this one. 

My laptop hard drive has bad blocks. Luckily only my root partition was hit (home directory is fine, all the important files are intact,) but I'm going to need a new one.

I have a two year warranty which will expire sometime in late March or early April, I'm not sure exactly but I could check. It has traditionally taken over a month for the full process of getting a laptop back from the repair depot, so time is of the essence.

Now, some background on the competence of this company's (Toshiba's) particular repair organization: When I sent it the last time, they reformatted my Ubuntu installation because "The damaged motherboard corrupted the Windows system files." I'm worried that I will get the same "repair" this time, and *I'll get it back with a brand new Vista installation on the same old broken hard drive.* Since the warranty is so close to expiring, I can't risk the chances of getting screwed over.

So, I have a few questions.

[LIST]
[*]Has anyone been in a similar situation? If so, what happened? Details (manufacturer, which depot you sent it to, etc.) would also be nice.
[*]What do you recommend I do or say to get them to replace the drive?
[*]What do you recommend I do or say if they do not replace the drive?
[*]Is there some kind of serial number or something which I could use to verify that they have replaced it (preferably without opening up the computer.)
[/LIST]

Thanks!
-Max.

---

### Post by Icehuck on 2009-12-15
> **MaxIBoy said:**
> If you see this crossposted in multiple forum websites, it's because I'm really frantic about this, not because I have no faith in this one. 

My laptop hard drive has bad blocks. Luckily only my root partition was hit (home directory is fine, all the important files are intact,) but I'm going to need a new one.

I have a two year warranty which will expire sometime in late March or early April, I'm not sure exactly but I could check. It has traditionally taken over a month for the full process of getting a laptop back from the repair depot, so time is of the essence.

Now, some background on the competence of this company's (Toshiba's) particular repair organization: When I sent it the last time, they reformatted my Ubuntu installation because "The damaged motherboard corrupted the Windows system files." I'm worried that I will get the same "repair" this time, and *I'll get it back with a brand new Vista installation on the same old broken hard drive.* Since the warranty is so close to expiring, I can't risk the chances of getting screwed over.

So, I have a few questions.

[LIST]
[*]Has anyone been in a similar situation? If so, what happened? Details (manufacturer, which depot you sent it to, etc.) would also be nice.
[*]What do you recommend I do or say to get them to replace the drive?
[*]What do you recommend I do or say if they do not replace the drive?
[*]Is there some kind of serial number or something which I could use to verify that they have replaced it (preferably without opening up the computer.)
[/LIST]

Thanks!
-Max.

Run a drive fitness test and see what the results are. If the error code says defective device then have it replaced. IF you get it replaced you will need to send them the old drive. They will not transfer your data over so be sure to back up the files and erase your drive if need be. Error code 0x72 is what you hope to get as that means the drive is garbage.

I've worked with Dell, HP, and IBM and it's always the same thing. Hard Drives die all the time especially laptop drives. It's not something out of the ordinary and you could probably just get away telling them you ran the test and give them the error code.

---

### Post by tom66 on 2009-12-15
Just make a backup of whatever files you can salvage. If your home directory is OK, you should be able to copy it.

---

### Post by handy on 2009-12-15
They have to continue the warranty to the March or whenever; its not worth their while to have to do the job twice, potentially loose a customer as well.

HDD cost *_us_* next to nothing these days.

---

### Post by soni1770 on 2009-12-15
i bought a dell laptop preinstalled with ubuntu and when it came the hdd was trash, turned out it was formated to fat32????  of all things. i told them i knew this meant the hdd was second hand.  they did send someone out straight away with a new HDD so i decided not to return the laptop, plus i really didn't want to buy one with windows

---

### Post by JBAlaska on 2009-12-15
A friend of mine sent his Toshiba in for a dead MB, left all his personal data on the HD. when he got it back, they had re-imaged his HD...When he called, furious about it they said it was "Standard procedure" to re-image all HD's when a laptop came in for a MB replacement!..Like WTF??

When you call to get your RMA number, tell them that your laptop is mission critical (To keep your job, etc) and you will be using a "Loner" HD in it.

Bottom line, just send them the HD, you may have to talk to a supervisor or 2 but be firm and don't take no for a answer!

Good luck!

---

### Post by MaxIBoy on 2009-12-15
Just an update:

I tried installing another OS over the root partition as a temporary measure until I can get it repaired. Didn't work. I tried deleting the root partition and creating a new one. Didn't work. I tried putting it in different spots to see if I could "work around" the bad spots. Didn't work.

Turns out, I get I/O errors whenever I do anything whatsoever with the partition table. When I booted from a Mint 8 CD, A warning popped up saying that the hard drive had "many bad sectors" (over 500!) Probably the results from the S.M.A.R.T. tests I ran earlier.

This is encouraging to me. I think that they will have no success if they even *try *to re-image the drive, so they will be forced to give me a proper replacement.

Hopefully the OEM installation process won't gloss over the errors or anything, but it's looking good. And I can still read my home dir just fine from a liveUSB, I will commence backups this evening.


Thanks for the replies!







PS: The last time I tried opening up my laptop, I cut my fingers on the sharp plastic edges and didn't really get anywhere anyway. That thing was *not* intended for dis-assembly, and the HDD is buried deep in the guts of it. I offered to send it without a hard drive last time (because I didn't want to go to the trouble of restoring everything from backup,) but the representative said that was against their policy.

I'm sure I could convince them to let me just send in the hard drive and keep the rest of the machine, but I really just don't want to deal with the red tape.

---

### Post by Andrew1122 on 2012-12-21
Yeah this si good suggestions i just want to need your help that i am looking for a custom build laptop looked at a few on line but they dont offer me all i am looking for so does anyone here know where i can get on online please budget £650 £700 It must have a 17" screen, bluetooth, windows 7 premium, either an i5 or i7 processor......

---

### Post by kurt18947 on 2012-12-21
> **Andrew1122 said:**
> Yeah this si good suggestions i just want to need your help that i am looking for a custom build laptop looked at a few on line but they dont offer me all i am looking for so does anyone here know where i can get on online please budget £650 £700 It must have a 17" screen, bluetooth, windows 7 premium, either an i5 or i7 processor......

This is a 3 year old thread and your post has nothing to do with content.  Maybe do some research or start a new thread?

---

### Post by KiwiNZ on 2012-12-21
The HDD crashed and so has this thread

---

