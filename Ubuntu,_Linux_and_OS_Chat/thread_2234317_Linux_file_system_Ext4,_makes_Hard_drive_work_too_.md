---
title: "Linux file system Ext4, makes Hard drive work too hard?"
date: 2014-07-14
forum: Ubuntu, Linux and OS Chat
---

### Post by newbie4 on 2014-07-14
It's been about 3 months now since installing Ubuntu's new release, and has been okay so far except lately (started 2 weeks ago) my hard drive started producing a louder winding mechanical sound for about a second when starting or waking back up from sleep. 

I've done a lot of asking around regarding this, and finally was able to get the best clue to what happened. I talked to a tech from a tech shop and explained and described the symptom of my hard drive. He asked me how it was mounted, age, airflow, temperature, partitions, installed OS and usage. I told him exactly how it is on my system which is mounted regularly/horizontally, about 1 1/2 year old now, intake fan right in front of it (max ave. temp is 32degrees Celsius), three partitions for 2 linux OS's and Data, and regular usage (email, office, web browsing, and lots of streaming and stored multimedia, and occasional bleachbit blank space cleaner).

He immediately said that it's the start of the HDD showing wear n' tear, and it was the ext4 file system used by Linux that's wearing out my hard drive due to the file system being more scattered compared to NTFS, which NTFS can also be defragged while ext4 cannot, thus creating a fragmented way of reading and writing and heavy back n' forth movement of the hdd's arm into the spindle.

Everything made sense and though I'm not ready to give up my linux partition, I'm thinking of deleting one of the Linux partition reinstalling Ubuntu using a smaller partition, so maybe it wouldn't be so much for my poor old HDD.

I'm not in a place to buy anything right now, so does anyone have a better solution than what I'm going to try, to save and continue using this HDD?  Or my idea of deleting the other OS partition and resizing to a smaller partition for a fresh Ubuntu install good enough and will help reduce the wear n' tear?

---

### Post by Vladlenin5000 on 2014-07-14
There's not a nice way to say it: What that "tech" from the tech shop told you about EXT4 is a huge pile of bovine manure.
There are much more knowledgeable people here than me so I let them debunk that.

Meanwhile, you can keep the system as it is. A smaller partition won't wear less the disk. The usage, ie, the amount of read/write operations, is what matters regardless of the size and amount of partitions in the the same physical unit.

Please post the brand/model of the HDD. I doubt it is only 1 1/2 years old as you mentioned.

---

### Post by capscrew on 2014-07-14
> **newbie4 said:**
> It's been about 3 months now since installing Ubuntu's new release, and has been okay so far except lately (started 2 weeks ago) my hard drive started producing a louder winding mechanical sound for about a second when starting or waking back up from sleep. 

I've done a lot of asking around regarding this, and finally was able to get the best clue to what happened. I talked to a tech from a tech shop and explained and described the symptom of my hard drive. He asked me how it was mounted, age, airflow, temperature, partitions, installed OS and usage. I told him exactly how it is on my system which is mounted regularly/horizontally, about 1 1/2 year old now, intake fan right in front of it (max ave. temp is 32degrees Celsius), three partitions for 2 linux OS's and Data, and regular usage (email, office, web browsing, and lots of streaming and stored multimedia, and occasional bleachbit blank space cleaner).

He immediately said that it's the start of the HDD showing wear n' tear, and it was the ext4 file system used by Linux that's wearing out my hard drive due to the file system being more scattered compared to NTFS, which NTFS can also be defragged while ext4 cannot, thus creating a fragmented way of reading and writing and heavy back n' forth movement of the hdd's arm into the spindle.

Everything made sense and though I'm not ready to give up my linux partition, I'm thinking of deleting one of the Linux partition reinstalling Ubuntu using a smaller partition, so maybe it wouldn't be so much for my poor old HDD.

I'm not in a place to buy anything right now, so does anyone have a better solution than what I'm going to try, to save and continue using this HDD?  Or my idea of deleting the other OS partition and resizing to a smaller partition for a fresh Ubuntu install good enough and will help reduce the wear n' tear?
None of it makes sense.  Ext4 causes no more practical wear than any other file system formatting.  The disk is spinning all the time whether you are accessing data or not unless it has been put on stand by.  Ext4 doesn't need defraging, but it does have a tool to check the integrity called fsck.  If you want to check the HDD condition you can use smartmon tools.  See [here]("http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/") for information on how to do this.

From my own experience I can say my oldest disk with ext4 is over 5 years old and it performs perfectly.  I have an even older disk that I formatted with ext4 about 3 years ago that also works with no problems or noise.

---

### Post by capscrew on 2014-07-14
> **Vladlenin5000 said:**
> There's not a nice way to say it: What that "tech" from the tech shop told you about EXT4 is a huge pile of bovine manure.
There are much more knowledgeable people here than me so I let them debunk that.

Meanwhile, you can keep the system as it is. A smaller partition won't wear less the disk. The usage, ie, the amount of read/write operations, is what matters regardless of the size and amount of partitions in the the same physical unit.

Please post the brand/model of the HDD. I doubt it is only 1 1/2 years old as you mentioned.
My experience is that the bearings start to wear and the disk starts to wobble causing noise and head crash.

---

### Post by newbie4 on 2014-07-14
SEAGATE 500GB BARRACUDA 7200 RPM SATA 6Gb/s is the HDD, and it was purchased September of 2012, so yeah you're right it's a little over 1 1/2 year old.  It's 1 year and 10 months to be precise since purchasing it.

---

### Post by newbie4 on 2014-07-14
It's never ever been even close to a bump. The noise isn't constant by the way. It's just for a second or a fraction, when starting up or waking up from sleep.

---

### Post by Vladlenin5000 on 2014-07-14
> **newbie4 said:**
> SEAGATE 500GB BARRACUDA 7200 RPM SATA 6Gb/s is the HDD, and it was purchased September of 2012, so yeah you're right it's a little over 1 1/2 year old.  It's 1 year and 10 months to be precise since purchasing it.

Probably much older than that and, coincidentally, I recently replaced a similar drive whilst much older drives (Seagate and others) are still working fine. Perhaps we got a bad batch. Is yours made in Thailand too? I never had an issue with Seagates made in China or Singapore.

---

### Post by grahammechanical on 2014-07-14
A hard disk is not actually a disk but several disks called platters that are stacked one on top of the other and there is no start or end to a disk just an inner and an outer edge. If anything is going to cause excessive wear it is the need to regularly defragment the data on the disk to improve the performance of Microsoft Windows.

The Linux Ext4 files system is a journalling file system. So this is not true

> [COLOR=#000000] the ext4 file system used by Linux that's wearing out my hard drive due to the file system being more scattered compared to NTFS, [/COLOR]

> [COLOR=#252525][FONT=sans-serif]these filesystems employ allocation techniques designed to keep fragmentation under control at all times.[/FONT][/COLOR][COLOR=#252525][FONT=sans-serif] As a result, defragmentation is not needed in the vast majority of cases.[/FONT][/COLOR]

The fact that Windows file system needs degragging to improve performance is also proof that it is the windows file system that is scattering data all over the disk/plattters.  So, if you have Windows on this disk then look no further for your culprit.

[http://en.wikipedia.org/wiki/Defragmentation](http://en.wikipedia.org/wiki/Defragmentation)

[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

Regards.

---

### Post by stalkingwolf on 2014-07-14
i have a 160 gb maxtor that is 8-9 years old. it still works but reads bad so i quit using it. it has had ext 3 and 4 on it for years. i also have a very old 10 gb that still works.

Most "techs" in shops will tell you that what ever issue you are having is the fault of linux/ubuntu.  Ive even had a couple tell me that linux was a virus and would cause catastrophic failures.  I guess they figure if they get you back to windows they gain a new customer.

---

### Post by Bucky Ball on 2014-07-14
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Find a new 'technician' (and I use the term loosely). What they've told you is known in the business as 'FUD'. Here's a loose description of what that is:

[https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt](https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt)

What we don't know about makes us frightened so we want others to feel the same. Unless we are willing to learn, that is. Why would your techie want to know anything about 'EXT' partitions (whatever the heck they are) when they're safe, secure and comfortable making a living out of NTFS, HFS and FAT? Best to work up some FUD to put others off these EXT things and then maybe they won't ask pesky questions I'm not qualified to answer. ;)

---

### Post by philinux on 2014-07-14
> **newbie4 said:**
> SEAGATE 500GB BARRACUDA 7200 RPM SATA 6Gb/s is the HDD, and it was purchased September of 2012, so yeah you're right it's a little over 1 1/2 year old.  It's 1 year and 10 months to be precise since purchasing it.

If you're using unity click the dash and search for disks. Run that and check the s.m.a.r.t data. From Gear icon menu top right.

I have a desktop thats about 5 years old which makes a similar noise. I thought it might be the fan. Anyway all is fine with the smart data.

---

### Post by oldfred on 2014-07-14
This is were there is some minor advantage (and it is minor) to a smaller / (root) partition of 20 or 25GB. Then the main system files are closer together on drive. That data is scattered is ok as with Linux entire file is fully written together, rarely fragmented so one read for each file is all that is required. 
The newer TB sized drives do make this more of an issue as not that many years ago drives were not that large. And default install should now change to separate / & /home if drive is very large.

With Windows each file is not rewritten but added or more data is located elsewhere on drive creating fragments, sometime many. If you regularly defrag drive you greatly help Windows work better. But few Windows users do that.

---

### Post by Bucky Ball on 2014-07-14
I always have the OS on a small partition on its own, no personal data. Always done it that way because of the reasons outlined by oldfred. If the OS is in a 20Gb partition (mine are mostly 15Gb) rather than a 500Gb partition the hard drive arm doesn't have far to search and there's not wide open spaces to spit data. Even better if your data partitions are on a separate drive all together. Old school, a throw back to old technology and old Windows days, but that's the way I swing. ;)

I've only recently stopped using an 80Gb drive for Win and Ubuntu(s) with all other data 'offshore' (replaced the 80Gb HDD with a 120Gb SSD).

---

### Post by newbie4 on 2014-07-14
Everyone, thank you all for your replies.  I've done my own research and found out that these barracuda HDD's have been known to make a quick 0.2 sec. winding noise at startup/power on. I found the exact symptom as someone described in a Seagate forum, and while people do not think it's normal, nobody appears to have any solution to it either.  On the same note however, noone reported their HDD to have failed either.  Many suggested that perhaps it's mainly a quality issue rather than defect.  A post commented that it can be compared to an economy car vs. luxury car in terms of a quiet ride.  
So from what I've gathered, this HDD I've got is just low quality, otherwise should be fine.
And for that tech from the shop, as someone posted, he may be was really just trying to discourage me and lead me on to a possible sale for an upgrade.  I did notice they were pushing SSD's afterall at the time of my visit.
Bye all.

---

### Post by ssam on 2014-07-15
Maybe the guy heard about an old issue and thought it was still a problem. A few years ago there was an issue with some hard drives on linux which result in an excessive number of spin up spin down cycles ( [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) ). It generated a few over exaggerated "linux kills hard disks" stories in the tech press, but has been long fixed.

There was also the atime updates thing. In the past every time a file was read the access time metadata was updated. This was a standard thing on unix, so it took a while for people to realise that it mostly was not worth it (only a few applications use atime) and it degraded performance. The defaults were changed so that atime got less frequent updates, and there is a noatime option to disable it completely.

In terms of fragmentation ext4 is pretty advance. It has some fancy techniques like delayed allocation ( [https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Delayed_allocation](https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Delayed_allocation) ) to reduce fragmentation. There is a defrag tool for ext4, but not many people bother using it because its not a big issue. The future linux file system BTRFS has autodefrag, which detects and defrags files in th background.

---

### Post by /ADM on 2014-07-15
It is not just Barracuda drives, my Seagate drive sometimes makes a 'clicking' sound during / after writing data (copying files etc).  Not all the time, but it's normal too.  

I never trust so called 'techs' in stores, IMO they are about as knowledgeable as a bag of frogspawn.

---

### Post by stalkingwolf on 2014-07-15
and in many cases store techs are required to push the company program as it were.  hard sell what ever the company is pushing that week.

---

### Post by cariboo on 2014-07-15
Seagate drives do go bad, I had a 750GIB drive that was replaced 4 times under warranty, before I gave up on it. I had it formatted as an XFS file system, and so far it is the only drive I've ever owned that was that unreliable. I have a server with 8 drives of vary sizes, and makes, all formatted as XFS except for the / partition on the first drive which is formatted as ext4. The only other drive I had a problem with is the Western Digital Blue 1TiB which failed on me after about six months, and was replaced under warranty, and has been running for the last 2 years with zero problems.

---

### Post by fkkroundabout on 2014-07-16
^ it's a seagate.

[solved]

[IMG]http://blog.backblaze.com/wp-content/uploads/2014/01/blog-fail-drives-manufacture.jpg[/IMG]
[IMG]http://blog.backblaze.com/wp-content/uploads/2014/01/blog-survival-drives-by-month.jpg[/IMG]
edit: added conclusion. and would like to add: my personal experience with other peoples' hard drives correlates with the above, well

[http://blog.backblaze.com/2014/01/21/what-hard-drive-should-i-buy/](http://blog.backblaze.com/2014/01/21/what-hard-drive-should-i-buy/)

---

### Post by ssam on 2014-07-16
> **fkkroundabout said:**
> ^ it's a seagate.
[http://blog.backblaze.com/2014/01/21/what-hard-drive-should-i-buy/](http://blog.backblaze.com/2014/01/21/what-hard-drive-should-i-buy/)

And the conclusion of that page

> **What Drives Is Backblaze Buying Now?**

We are focusing on 4TB drives for new pods. For these, our **current favorite is the Seagate** Desktop HDD.15 (ST4000DM000). We’ll have to keep an eye on them, though. Historically, Seagate drives have performed well at first, and then had higher failure rates later.

All drives can fail. Make sure you have back up, keep receipts so you can return the failed drives.

---

### Post by LastDino on 2014-07-16
You may need disk change but you definitely need a technician change.

---

