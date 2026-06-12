---
title: "Hard Drive to blow-up???"
date: 2005-05-13
forum: The Cafe
---

### Post by sonny on 2005-05-13
Hi... I want some of you to bring light to one question I had for some 2-3 days now. I have a friend studying electronics, most of the time (70%) he is right about the stuff he says, but a few days ago he mention that if you format your hard drive within short periods of time it might stop working or malfunction, although it could be true I'm wondering if it's really true, and if it is, is there some maximium number of times to format a HD in a predeterminated period of time, lets say a month???

I don't completly believe him becuse those things are ment to write and erease data all the time, and to format it is just to erease all of the data, isn't it?? And the are some programs from the HD manufacturers to do it by changing the cylinder 0, or something like that, maxblast for maxtor is an example.... so I think that it could be possible but if you format your HD a really high and exagerated number of times. Well I hope someone here could be able to tell me the truth, or to give me a link to a page where they test this thing and show the facts.

---

### Post by Stormy Eyes on 2005-05-14
I've never heard of such a thing, nor have I seen evidence that merely creating and destroying partitions an "excessive" number of times can destroy a hard drive.

---

### Post by WildTangent on 2005-05-14
ya, its definately not true. for once, your friend may be wrong ;)

-Wild

---

### Post by sonny on 2005-05-14
Well I'm happy to hear that... I'm gonna send him the link so he'll see it with his own two eyes...  :grin: thanks guys

---

### Post by TravisNewman on 2005-05-14
[QUOTE=sonny]Well I'm happy to hear that... I'm gonna send him the link so he'll see it with his own two eyes...  :grin: thanks guys[/QUOTE]
 I think doing FULL formats frequently is bad for it, just because it's a lot of activity. The more activity, the more wear, the more wear, the shorter the lifespan. But it's probably not enough to even matter.

---

### Post by jerome bettis on 2005-05-14
correct me if i'm wrong here (i think i am :-P) but when you format, doesn't the operating system just mark all those blocks as avaliable?  it doesn't actually write anything, the old data is still there, but the operating system doesn't care.

yes? no?

i don't remember where i heard that, but i don't think it was in one of my classes so i dunno.

---

### Post by WildTangent on 2005-05-14
[QUOTE=jerome bettis]correct me if i'm wrong here (i think i am :-P) but when you format, doesn't the operating system just mark all those blocks as avaliable?  it doesn't actually write anything, the old data is still there, but the operating system doesn't care.

yes? no?

i don't remember where i heard that, but i don't think it was in one of my classes so i dunno.[/QUOTE]
i think thats the case with a quick format, but im pretty sure a full format physically erases all of the data

-Wild

---

### Post by darkoptix on 2005-05-14
Full physical formats take a very long time. I have a 486 for that use.

---

### Post by wbeck85 on 2005-05-14
[QUOTE=darkoptix]Full physical formats take a very long time. I have a 486 for that use.[/QUOTE]
 You mean that you have a computer that is designated the formatter? So you pop out your drive, insert it in the 466 and fdisk? Does it really save much time over just formatting during an install or something? Maybe if its a like a 100+ gig drive it would matter. I suppose you could also just leave the hd into your main computer, dont mount it when you boot and then ctrl-alt-f2 (or another function button) to a virtual terminal and do a $ sudo mkfs.ext3 /dev/hdb, then switch back to X and do what ever until its done?

Less manual work involved that way, i think. But ah, does that actually work? I've never tried it, but it seems to me that it may work.

---

### Post by KiwiNZ on 2005-05-14
Format just deletes the fat table . 
If you use forensic disk recovering tools its all still there

---

### Post by TravisNewman on 2005-05-14
QUICK format just deletes the fat table, that's why it takes like 5 seconds.
FULL formats take HOURS. I doubt the fat table is that big.

You can write zero's to the whole drive 5 times and still get data with forensic disk tools.

---

### Post by KiwiNZ on 2005-05-14
I have still managed to get data back after 13 sweeps zeroing the disk.

Am I right in thinking A quick format deletes the fat table , a "full" format deletes the fat table and does a scan disk etc .

---

### Post by TravisNewman on 2005-05-14
13 sweeps? Dang.

I wonder how many sweeps you'd have to make to REALLY clear off the data?

---

### Post by WildTangent on 2005-05-14
use norton system works if you really want to get rid of the data for good

-Wild

---

### Post by TravisNewman on 2005-05-14
Lets be honest, you can get past Norton System Works or anything else for that matter. You can do 5 or 10 passes with NSW and it might be hard for forensic utilities to pull data off, but not impossible.

oh and KiwiNZ, yeah I think you're right about the quick vs full format.

---

### Post by az on 2005-05-14
man shred

---

### Post by WildTangent on 2005-05-14
[QUOTE=azz]man shred[/QUOTE]
am i the only one that thinks that sounds like a serial killer slang term? lol

is it a disk wiping utility?

-Wild

---

### Post by TravisNewman on 2005-05-14
[QUOTE=WildTangent]am i the only one that thinks that sounds like a serial killer slang term? lol

is it a disk wiping utility?

-Wild[/QUOTE]
 *LOL* yes, its a secure delete.

---

