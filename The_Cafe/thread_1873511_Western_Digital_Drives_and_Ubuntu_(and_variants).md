---
title: "Western Digital Drives and Ubuntu (and variants)"
date: 2011-11-01
forum: The Cafe
---

### Post by DunZH on 2011-11-01
I have some stories about WD drives (Western Digital), and they are not nice.

I hope to help others, as this damn company caused me a lot of hassle, wasted my time and money, and made me lose some important documents. I will never buy WD drives again, its Seagate for me from here on out.  Be forewarned, my friend, as I have been burned twice within 3-4 months and you might be too.

From what I have heard, WD has even spoken clearly that they do not care about the Linux community.  So, I ain't very happy now.

WD drives have some bug in Ubuntu, maybe only later versions.  They will become pretty much inaccessible, (ymmv), and never improve.

The SMART data of Wd drives doesn't work right, they will show a bunch of bad sectors within several months of use.  I don't actually belive the drive has bad sectors, rather its a bug or two. You can't even get a proper SMART data check to finish.

So I am twice burned, which makes me a putz because I didn't learn the first time. But anyway I want to lay this out because its bullsh*t.

At first, I bought a backup drive, a WD Elements 1TB drive.  I really needed a backup at that time, as my main box was failing.

Well, it worked just long enough for me to put my data on there, and then promptly became inaccessible.  Which screwed me because I had deleted stuff, trusting this POS drive.

Then, I had a new comp put together, and it ended up with a WD internal hard drive.  Which is my fault, to be honest.  But let me tell you, I thought maybe, as an internal it would be ok, but within 3 months the partition I made for data on the drive (not the file system) had problems and just got worse.

In both cases the problems were basically the same.  The external drive became almost completely inaccessible, in fact it wouldn't stay mounted at all, while the internal allowed data to transfer, but was just incredibly slow and caused the whole computer to slow down to a crawl.

I am not going to go on about all the problems I had. You have been warned.  Stay away from WD drives.

---

### Post by wolfen69 on 2011-11-01
This is not a help question and should have been posted in the Community Cafe.

---

### Post by coffeecat on 2011-11-01
... and with that...

*Thread moved to **The Community Cafe**.*  :)

---

### Post by PhilGil on 2011-11-01
I've had no problems whatsoever with my Western Digital 1TB drive, which I've owned for two years. In that same period of time, I've had to RMA three Seagate drives.

Moral of the story...
As storage capacity has increased, drives have become less reliable.
All the major HDD manufacturers go through periods where their products are crap.
If you want better reliability, buy commercial grade drives.
Backup, Backup, Backup.

---

### Post by mips on 2011-11-01
Pretty much luck of the draw. All brands experience failures and you honestly can't say the one brand is better than the other. Seagate recently dropped their warranties to 2 years as well.

---

### Post by cryptotheslow on 2011-11-01
No problems here with 2 x WD 320GB Blues running in a 10.04 32bit Desktop and 1 x WD 500GB Green running in a 10.04.3 64bit Server.

Previously had a Seagate 500GB that cacked itself with the now infamous BSY error due to a problem with the service sector written at the factory.

---

### Post by DunZH on 2011-11-01
The evidence of some trivial number of non-problematic drives is not proof that a problem does not exist.

Further, this is all on 11.04, not any 10.X.

The drive has trouble to mount, and SMART data is unavailable, and often reports major problems, within months of use.

The problems (from my internal experience) started when I put in a second external in at the same time.  After that, it just went to pieces.

Re-formatting doesn't even help.  When I started to have problems, I just stopped even trying to access this partition at all. Then, when the data was saved, i tried to re-format it.  And that's when the warnings started up, which I remembered from the external - 

Hard Disk Problems Detected

And like 8 of them pop up at the same time. Which, with the external, I would get 12 of them instead and no good mount.  It would unmount whenever I tried to access the data.  Damn drive took my backup data but wouldn't give up jack 2 weeks later.

So that's when I knew what was up, and didn't waste any time to replace another faulty - or buggy - WD drive. Take your pick.

---

### Post by johnnybgoode83 on 2011-11-01
I have a 3TB WD External hard drive which I have had no issues with so I can't complain.

---

### Post by PhilGil on 2011-11-01
> **DunZH said:**
> The evidence of some trivial number of non-problematic drives is not proof that a problem does not exist.The point that myself and the other posters are making is that your poor experience with a couple of WD drives is no more indicative of a systematic problem than our good experiences indicate that WD drives have no problems.

It may be that you've discovered a disk controller problem in 11.10, in which case you should file a bug report. On the other hand, you may have just had bad luck.

---

### Post by shad0w_walker on 2011-11-01
4 WD drives in my media centre. 2 x 1TB and 2 x 2TB running for a couple of years now 24/7/365. Absolutely no problems what so ever. 2 WD in my desktop. No problems at all.

I also have a custom built drive testing system at work (Built off Ubuntu kernel and initrd) that checks on average 150-200+ drives a day, mixture of all brands. No higher rate of failure on WDs than any other brand. Not bullet proof evidence, but neither is a few horror stories.

---

### Post by cariboo on 2011-11-01
I have 8 hard drives in my server, they are a mix of Seagate and WD with one Maxtor thrown in because it still works. 

Going by your metric, I would suggest that you stay away from Seagate, because I've had to RMA the same 750GiB drive twice.

---

### Post by wolfen69 on 2011-11-02
> **PhilGil said:**
> 
Backup, Backup, Backup.

Well said. With a *good* backup routine, one doesn't worry about much.

---

### Post by PC_load_letter on 2011-11-02
Just my 2 cents, I have only used WD drives since before I even started using Ubuntu 7.04. In my current desktop (running Mint 11, based on 11.04), I have like 3 WD drives inside, no problems. My wife has the "Elements" 1TB backup drive that she has been using between Windows and her Ubuntu 11.04 laptop for like 4 months now, not a single problem. 

I have had no problems accessing and running the SMART tests (short or long) on any of them. In fact I just ran the short test while typing this reply up, no errors detected, I bought this drive last March, so it was 8 months ago.

---

### Post by LowSky on 2011-11-02
I have 3 WD drives, one 1TB and two 2TB, also have a 120GB SSD from Mushkin, a 750GB from Samsung. I used to have a 500GB from seagate but I replaced it for one of the 2TB drives. Now it does back up duty. 

I have never had a drive fail me. I get that people have hardware failures, I had two bad motherboards separated over 4 years and different makes, but when someone has 3-4 drives fail in a row you have to start thinking it isn't the drive, but maybe another piece of hardware, or maybe, just maybe, the user.

---

### Post by BrokenKingpin on 2011-11-02
I have had no issues with WD drives, and I have been using them for years under Linux.

On my home server I have had 4 WD Black drives running in Raid 5 for 2 years (24/7).

With computer hardware it can always be hit or miss, from any manufacturer.

---

### Post by a2j on 2011-11-02
80% of my drives are WD. Because of their easy RMA process.
Hard drives will fail.  Yes I expect my drives to fail at some point. Its not the question of *if*, but *when*. So, to keep my data safe, I use: RAID, Backups, WD RMA, and common sense.

---

### Post by Dangertux on 2011-11-03
The WD drive in my laptop ate it today, it's less than 2 months old. I don't attribute it to the fact that it's WD though. Mostly just bad luck I've had great luck with WD in the past.

---

### Post by pbpersson on 2011-11-03
I recently had two Seagate drives that I bought that were dead when I got them.  I just switched back to WD drives and have had no problems at all.

---

