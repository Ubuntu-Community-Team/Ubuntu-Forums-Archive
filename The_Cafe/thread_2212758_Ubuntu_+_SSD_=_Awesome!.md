---
title: "Ubuntu + SSD = Awesome!"
date: 2014-03-22
forum: The Cafe
---

### Post by help_me2 on 2014-03-22
Just got an SSD (Samsung 840 Pro) for my Ubuntu laptop, and now it screams! (also added 4gb ram for a total of 8gb, and have no swap) Chrome used to take a good 7 seconds to open, now it's 1 second. Smaller programs are almost instantaneous. I got a 256GB drive for $190 on Amazon. Prices have finally become reasonable for good sized drives. 

After doing much research, I decided upon the Samsung because it's always rated as one of the best.

I added noatime to the fstab, turned off journaling, and something else I can't remember right now. Also, contrary to popular belief, it's no longer recommended to add discard to fstab.  Google does not recommend it, along with other knowledgeable sources that I've found. [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) I just apply TRIM manually in the terminal every so often. Supposedly, TRIM will be automatic in the kernel starting with Ubuntu 14.04

Anyway, It's one of the best upgrades you can do, along with adding RAM. So glad I did. Anyone else use an SSD?

---

### Post by Jonor on 2014-03-23
SSDs certainly made a significant speed improvement on my box over HDD but i'm still not sure if 
i will regret it as log files are useful when things go wrong, so journaling is still on here.
I'd be interested to see what your fstab file looks like now, have you adjusted swappiness, perhaps that was the something else ?

---

### Post by james114 on 2014-03-23
SSD is more expensive than SATA, of course it is awesome.

---

### Post by buzzingrobot on 2014-03-23
Why no swap?  It has no impact on performance unless it is used.  It is used only when you max out RAM and the impact there is entirely beneficial. I.e., your system keeps running, albeit slowly, rather than stopping.

So, if you know for sure you will never max those 8 gigs, no problem.  But, if you ever do, you might want the swap partition.

---

### Post by BlinkinCat on 2014-03-23
> **help_me2 said:**
> I can see why people don't come here much anymore. 

P.S. I've been here since 2004.

Hi,

Why do you say that? If it is because you apparently have no views on your thread, this is because there is currently a technical problem on the forums which is being investigated.

Cheers - :P

---

### Post by ssam on 2014-03-23
> **help_me2 said:**
> 
I added noatime to the fstab, turned off journaling, and something else I can't remember right now.

disabling journalling increases the chance of data corruption if you have an unclean shutdown. The chance of wearing out an SSD is small unless you write many GB of data per day for years.

---

### Post by mattlach on 2014-03-24
> **help_me2 said:**
> Just got an SSD (Samsung 840 Pro) for my Ubuntu laptop, and now it screams! (also added 4gb ram for a total of 8gb, and have no swap) Chrome used to take a good 7 seconds to open, now it's 1 second. Smaller programs are almost instantaneous. I got a 256GB drive for $190 on Amazon. Prices have finally become reasonable for good sized drives. 

After doing much research, I decided upon the Samsung because it's always rated as one of the best.

I added noatime to the fstab, turned off journaling, and something else I can't remember right now. Also, contrary to popular belief, it's no longer recommended to add discard to fstab.  Google does not recommend it, along with other knowledgeable sources that I've found. [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) I just apply TRIM manually in the terminal every so often. Supposedly, TRIM will be automatic in the kernel starting with Ubuntu 14.04

Anyway, It's one of the best upgrades you can do, along with adding RAM. So glad I did. Anyone else use an SSD?


Agreed.   

I got my first SSD back in early 2010, and ever since there was no going back.  It's too bad most people see the need to go out and buy a new computer, when simply installing an SSD, upgrading RAM and a fresh OS install will make it feel like new.    Our CPU's are fantastically overkill for everything most people do these days, even 5 year old ones.

SSD's and RAM truly are the best upgrades for typical computer use.


> **Jonor said:**
> SSDs certainly made a significant speed improvement on my box over HDD but i'm still not sure if 
i will regret it as log files are useful when things go wrong, so journaling is still on here.
I'd be interested to see what your fstab file looks like now, have you adjusted swappiness, perhaps that was the something else ?

I wouldn't worry too much.  SSD's have come a long way, and - in the vast majority of usage cases - their write endurance will outlive the practical lifespans of the drives.

Things have improved to the point where even enterprise users don't use the highest endurance SLC drives for caching purposes anymore.  They've mostly all switched to the cheaper MLC, which - while having less endurance than SLC, is way overkill for all but the toughest of desktop work environments, unlike the early drives.  Even TLC, (cheapest and lowest endurance of the current crop of drives) like the Samsing 840 Evo is overkill for the vast majority of users.  

[According to Anandtech](http://www.anandtech.com/show/6459/samsung-ssd-840-testing-the-endurance-of-tlc-nand) a 128GB drive with the latest MLC technology will last ~35 years if you write approximately 10GB a day.   For TLC that goes down to a still overkill ~12 years.  These figures go up substantially on larger drives.   I consider myself a pretty heavy enthusiast user, and judging by my SSD monitoring tools, I write just about 10GB a day on average.   I would feel perfectly comfortable buying TLC my next time around, considering how much they have improved lately.


> **buzzingrobot said:**
> Why no swap?  It has no impact on performance unless it is used.  It is used only when you max out RAM and the impact there is entirely beneficial. I.e., your system keeps running, albeit slowly, rather than stopping.

So, if you know for sure you will never max those 8 gigs, no problem.  But, if you ever do, you might want the swap partition.

Some people are scared of the write endurance, which really isn't warranted on the latest drives.   For me - however - I just disable it as SSD's come at a cost premium, and I don't want to waste 2x my RAM on swap unless I really need it.   That being said, my desktop has 32GB of ram, so my swap would be ~64GB and that would double since I dual boot Windows 7 for those programs I still can't run under Linux.

These days I have no hard drives in any of my machines.   Just SSD's.   All my mass file storage is network attached and resides in my basement on my FreeNAS server.

---

### Post by help_me2 on 2014-03-25
> **Jonor said:**
> have you adjusted swappiness, perhaps that was the something else ?
I don't have a swap partition anymore, so no need to adjust swappiness. It's only needed if you have a questionable amount of RAM. 8gb's of RAM is more than enough for me and what I do. Even with Vbox open, I'll never use more than 4gb.

---

### Post by help_me2 on 2014-03-25
> **ssam said:**
> disabling journalling increases the chance of data corruption if you have an unclean shutdown. The chance of wearing out an SSD is small unless you write many GB of data per day for years.
Not worried, I reinstall every 6 months anyway and have a good backup too.

---

### Post by scollar1971 on 2014-03-26
Not familiar with 'Trim' can someone explain what it is? And some usage examples

---

### Post by mattlach on 2014-03-26
> **scollar1971 said:**
> Not familiar with 'Trim' can someone explain what it is? And some usage examples

Trim - while there are command line versions - is really more of a moun-time option than a command, or at least that is the smartest way to use it.

Here is my laymans explanation of why it is necessary.

The need for trim originated because of the way traditional hard drives delete files.   They simply remove the reference to them from the file allocation table, rather than physically erasing the space they occupy.   This works well for traditional hard drives as there is no performance penalty for overwriting something.    With flash ram there IS adeletion and overwriting penalty.   In the days before trim (or without trim enabled) users of SSD's would notice that their drives had really fast write speeds, up until they had filled every block on the drive once  (so essentially, if you had a 128GB drive, once your total writes had reached 128Gb) after that the drives write performance would slow down A LOT as the flash drive was needing to erase cells before writing to them.

TRIM adds this erase cycle to the file deletion process.   During drive idle times shortly after the deletion, it goes in and erases the flash, so that when it is time to write to it again, writes are fast.

There is a way to enable trim in /etc/fstab if using ext4, and it works really well, but it is not fresh in my mind right now.   If you just google it, you'll find many examples.

For further reading I recommend this [Anandtech article](http://www.anandtech.com/show/2738/).   He has done more to make complex SSD technical issues understandable to laymen like me than anyone else.

--Matt

---

### Post by QIII on 2014-03-26
Adding it to fstab is not recommended as it may be more inefficient than efficacious.

Trusty 14.04 has Trim enabled, but I still have a daily cron job running a script to trim for the moment while I wait to see what others are saying about how well it works.

---

### Post by mattlach on 2014-03-26
> **QIII said:**
> Adding it to fstab is not recommended as it may be more inefficient than efficacious.

Trusty 14.04 has Trim enabled, but I still have a daily cron job running a script to trim for the moment while I wait to see what others are saying about how well it works.

Interesting.  Do you have a source for this? (not adding to fstab, that is)  I'd like to read more details.

---

### Post by QIII on 2014-03-26
Using the "discard" option on mount in fstab combines the trim with the read/write operations and the overhead can diminish the speed advantage of the SSD.

A couple of places to look --

[http://opensuse.14.x6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.x6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

### Post by irv on 2014-03-27
SSD's are great, and I have been using one in an older Dell Laptop for over a year now. About two weeks ago I fixed up an older Dell Desktop. I added the max on RAM (4 gig) and installed a Hybried 1 TB drive. This combo give you the best of both worlds. A lot of storage and fast boot up with apps running fast. This drive cost under $100. The reason I went this way is because I got a new laptop with a Hybried drive and I like the performance. It a good way to get old computer to run like new ones.

---

### Post by mattlach on 2014-03-27
> **QIII said:**
> Using the "discard" option on mount in fstab combines the trim with the read/write operations and the overhead can diminish the speed advantage of the SSD.

A couple of places to look --

[http://opensuse.14.x6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.x6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

Interesting.

I have now read some more about this, and it seems SOME SSD's have trouble with delete performance when trim is enabled with the discard option in fstab, but not all.

I certainly noticed no difference in performance moving from discard disabled to enabled on my OCZ Vertex 4.  Performance is a great as ever.  

I - for one - would much rather have it done in small chunks as the delete operations happen, rather than in bulk all at once in a cron job, especially since my main desktop is always off when I am not actively using it, something which is not inconvenient at all when you have SSD boot times, and saves a lot of power, especially on my monster rig, with boosted voltage to reach a 4.8Ghz overclock.

I would still recommend that people add the discard option if running off of SSD's, and only disable it if they notice performance issues.

---

### Post by Paqman on 2014-03-28
> **help_me2 said:**
> turned off journaling

I have to echo the others here saying that's really not a good idea. Write endurance isn't an issue, your drive's wear levelling algorithms will take care of that. Disabling journalling puts your data at risk, and your data is probably worth more than your drive anyway.

---

### Post by help_me2 on 2014-03-31
> **Paqman said:**
> Disabling journalling puts your data at risk, and your data is probably worth more than your drive anyway.
I'm not an important person that has important things on my computer. I try not to keep much of anything on my computer, since I can view/do things on the web anytime I want. When I was younger, I was into "saving" things, but realize now those things mean very little in the grand scheme of life. 

I uploaded all of my music to Google Music, and have a couple "important" things backed up on an external drive and thumbdrive. Not worried what happens to my SSD. All I want is speed.

If you have family photos or other irreplaceable things, they shouldn't be on your working machine anyway. Put them in the cloud or on an external drive, and have fun on your everyday computer.

---

### Post by matt114 on 2014-05-27
I've just bought a Samsung EVO 840 250Gb from "PC World" (useless UK chain, but a good price, so...) based upon the reassuring summary found at the end of this extreme test review (below). I will say with utmost confidence that this has breathed a HUGE amount of digital life into my 3.5 year old, still very decent Acer X3950 (i3-550, 8Gb DDR3 ram, HD5450) :D

The loudest, if I'd even call them that, parts of this PC are now the CPU & PSU fans, and they're barely audible (the machine has never been noisy - Acer Desktops are generally almost silent).

Here's a superb and exhaustive test, upon which I made my purchase decision for the drive:

[http://us.hardware.info/reviews/4178/3/hardwareinfo-tests-lifespan-of-samsung-ssd-840-250gb-tlc-ssd-updated-with-final-conclusion-update-2-april-17](http://us.hardware.info/reviews/4178/3/hardwareinfo-tests-lifespan-of-samsung-ssd-840-250gb-tlc-ssd-updated-with-final-conclusion-update-2-april-17)

I now know why Apple are migrating all their machines to NAND - rotating disks are cheap, but SO clunky and slow - my average access time is now 0.03mS!!

---

### Post by Copper Bezel on 2014-05-27
I've been very happy with my experience with SSDs on previous machines. My present laptop uses a HDD, and I lucked out that it's a very quiet one, but I've never had a magnetic drive in a portable last more than a year and a half or so of being tossed around in my bag, and I'll definitely be switching to an SSD when this one dies. I look forward to the little speed boost, too - since it's all about loading apps and interface elements, it applies more to responsiveness while not really affecting number-crunching power at all, but that's exactly where I feel the improvement the most.

---

### Post by arapaho on 2014-10-29
I read that while partitioning SSD one must "[[SIZE=3]Reserve seven percent for overprovisioning[/SIZE]]("https://sites.google.com/site/easylinuxtipsproject/ssd")" Is that still valid for SSD from every producer?

---

### Post by mattlach on 2014-10-29
> **arapaho said:**
> I read that while partitioning SSD one must "[[SIZE=3]Reserve seven percent for overprovisioning[/SIZE]]("https://sites.google.com/site/easylinuxtipsproject/ssd")" Is that still valid for SSD from every producer?

No, that is nonsense.   Isn't true now, and hasn't ever been true for consumer SSD's.  Maybe this was necessary on some early enterprise models, but definitely not these days.

SSD's have reserved space they use for write endurance and wear leveling that you can't format.  If it is available to format it, for 99.9% of cases it makes sense to use it all.

There are some very rare use cases with high write cycles where underprovisioning still makes sense (like using an SSD as a cache device, or ZFS L2ARC device) but in typical use I wouldn't worry about it.

A typical fully formatted consumer SSD will survive way beyond its functional obsolescence under typical desktop style workloads.

The newer the drive the better, as MLC flash (and now even TLC flash) has improved greatly since the early days.

---

### Post by WinEunuchs2Unix on 2014-10-30
I don't know if it's different testing methods but I've seen speeds of 200 MB/s for the cheap SSD's to 550 MB/s+ for the expensive SSD's.

As far as life span I think they quote 40-50 GB/day for five years.

I finally got the on-board Intel 32GB mSATA III SSD caching the 500 GB SATA II HDD and the performance increase is awesome.  I used enhanceio and the speed matches Intels Smart Response Technology in Windows 7.

Yup SSD is great!

---

### Post by pqwoerituytrueiwoq on 2014-10-31
> **arapaho said:**
> I read that while partitioning SSD one must "[[SIZE=3]Reserve seven percent for overprovisioning[/SIZE]]("https://sites.google.com/site/easylinuxtipsproject/ssd")" Is that still valid for SSD from every producer?I think sandforce based drives support this allowing you to increase the overprovesioning beyond what the amount forces on you

---

### Post by Paulgirardin on 2014-11-01
I recently installed an Adata SSD.In my researching,I noted that Adata are giving the usable capacity as 64Gb instead of the usual 60Gb as they have reduced the overprovision to zero.They argue that the difference in Gb number and actual bytes amounts to around 7% anyway.

---

### Post by linuxyogi on 2014-11-04
> **mattlach said:**
> Agreed.   
I got my first SSD back in early 2010, and ever since there was no going back.  It's too bad most people see the need to go out and buy a new computer, when simply installing an SSD, upgrading RAM and a fresh OS install will make it feel like new.    Our CPU's are fantastically overkill for everything most people do these days, even 5 year old ones.

SSD's and RAM truly are the best upgrades for typical computer use.


My mainboard has SATA 2 ports which supports data transfers upto 300 MB/s but as you know the latest mainboards offer 3.2 which has a transfer speed of 1969 MB/s. So don't you think that will make a difference in performance ?

---

