---
title: "Disk Power On Hours"
date: 2011-01-16
forum: Server Platforms
---

### Post by Vegan on 2011-01-16
My Acer machine has accumulated a bit over 40,000 operating hours on the hard disk over its life.

The disk is fine but I was wondering how many hours I can expect out of it?

---

### Post by CharlesA on 2011-01-16
I thought the MTBF was something like 100,000 hours?

In any case, if you keep an eye on bad sectors and whatnot, you should be fine until the disk dies.

Just be sure you have backups. :)

---

### Post by hansolo4949 on 2011-01-16
You should be just fine. I had an OLD toshiba laptop from about 2001 that I had been using continuously throughout the years,(probably had OVER 100,000 hours on it) and it just died a year ago, and i'm not even sure that was because of hdd failure. You should be just fine with your computer, as long as you don't maltreat the hdd, and periodically run a disk check on it to make sure it doesn't have any bad sectors and whatnot. As charlesa said, you should make backups regularly so just in case it dies on you, you'll be prepared:).

---

### Post by hansolo4949 on 2011-01-16
You should be just fine. I had an OLD toshiba laptop from about 2001 that I had been using continuously throughout the years,(probably had OVER 100,000 hours on it) and it just died a year ago, and i'm not even sure that was because of hdd failure. You should be just fine with your computer, as long as you don't maltreat the hdd, and periodically run a disk check on it to make sure it doesn't have any bad sectors and whatnot. As charlesa said, you should make backups regularly so just in case it dies on you, you'll be prepared:).

---

### Post by hansolo4949 on 2011-01-16
Oh, yikes, triple post again. I seem to try and post at the worst times...this is the 3-4th double+ posting a have had in a ROW.:( sorry everyone

---

### Post by Vegan on 2011-01-16
I learned long ago that disks are far from perfect. So thanks to the forum here, I have a script that backs up everything daily.

This way if anything happens, I can roll back instantly.



I have an old Toshiba notebook, but its disk broke rendering the machine dead. The optical disk is also toast meaning an external drive is needed.

---

### Post by disabledaccount on 2011-01-19
Vegan:
What is your hdd type/model?
It looks like You have one of those "superb" firmware that counts minutes or internal clock ticks instead of hours (f.e. most of Samasung drives just don't follow SMART specs).

40000h means 4.5 years **continous** work, or ~10 years of heavy (for laptop) usage...

---

### Post by psusi on 2011-01-19
> **tomazzi said:**
> Vegan:
What is your hdd type/model?
It looks like You have one of those "superb" firmware that counts minutes or internal clock ticks instead of hours (f.e. most of Samasung drives just don't follow SMART specs).

40000h means 4.5 years **continous** work, or ~10 years of heavy (for laptop) usage...

Good point.. I've got a server thats been running 24/7 for 4.5 years to get a drive to count that high.

---

### Post by CharlesA on 2011-01-19
Well, I checked one of the drives I have hooked up and it's got something like 11,000 power-on hours.

If you've had it a while, it will add up.

---

### Post by CharlesA on 2011-01-19
Well, I checked one of the drives I have hooked up and it's got something like 11,000 power-on hours.

If you've had it a while, it will add up.

---

### Post by ZenMasta on 2011-01-19
How do you see this information?

---

### Post by Vegan on 2011-01-19
```
sudo apt-get install smartmontools
```

---

### Post by psusi on 2011-01-19
> **CharlesA said:**
> Well, I checked one of the drives I have hooked up and it's got something like 11,000 power-on hours.

If you've had it a while, it will add up.

Yea, I just checked my old first gen 10,000 rpm WD raptors that I realized the other day are now 7 years old and they have 12,853 hours on them.

---

### Post by Vegan on 2011-01-20
My disk is in service 24/7/365 except when I had to reinstall Linux last year when a problem screwed the database.

---

### Post by disabledaccount on 2011-01-20
Number of power-on-hours tells nothing about disk condition - can You show full SMART report? What is your hdd model?

---

### Post by Vegan on 2011-01-21
```
Location 	SATA device A 	Drive size 	149.05 GB
Make and model 	ATA ST3160021A 	Supports SMART? 	Yes
SMART enabled? 	Yes 	Passed drive check? 	Yes
Additional SMART attributes
Offline data collection status 	Offline data collection activity was completed without error.
Auto Offline Data Collection: Enabled.
Self-test execution status 	The previous self-test routine completed without error or no self-test has ever been run.
Total time to complete Offline data collection 	430 seconds.
Offline data collection capabilities 	SMART execute Offline immediate.
Auto Offline data collection on/off support.
Suspend Offline collection upon new command.
Offline surface scan supported.
Self-test supported.
No Conveyance Self-test supported.
Selective Self-test supported.
SMART capabilities 	Saves SMART data before entering power-saving mode.
Supports SMART auto save timer.
Error logging capability 	Error logging supported.
General Purpose Logging supported.
Short self-test routine recommended polling time 	1 minutes.
Extended self-test routine recommended polling time 	111 minutes.
Raw Read Error Rate 	243018004
Spin Up Time 	0
Start Stop Count 	2
Reallocated Sector Ct 	0
Seek Error Rate 	862521725
Power On Hours 	40395
Spin Retry Count 	0
Power Cycle Count 	1439
Temperature Celsius 	46
Hardware ECC Recovered 	243018004
Current Pending Sector 	0
Offline Uncorrectable 	0
Multi Zone Error Rate 	0
Data Address Mark Errs 	0
```

---

### Post by tgalati4 on 2011-01-21
Keep the drive cool and clean, use a decent UPS.

---

### Post by disabledaccount on 2011-01-22
Vegan: Your hdd is Seagate, but I'm still curious what model exactly (>hdparm -A)
For Seagate this report is ok - you should't have problems for long time.

---

### Post by Vegan on 2011-01-22
St3160021a

Given the disk is a 160GB model, and that there are 8760 hours in a year. My disk has been in continuous service since it was new.

It never rests as there are far too many Apache requests.

---

### Post by disabledaccount on 2011-01-23
I though so - Barracuda 7200.7 - almost immortal hdd :) I wouldn't be surprissed if your motherboard dies first (due to aging of capacitors).

---

### Post by Vegan on 2011-01-23
Interesting, so the Barracuda 7200.7 series are rock solid disks. Nice to know that my disk will keep on ticking.

Curious to see if more recent offerings are as reliable?

My current disk is large enough for my web server, I wonder how many hours I can rack up on it?

I have a WD disk in the junk box should this die. Its 80 GB but it has hardly any hours on it.

---

### Post by disabledaccount on 2011-01-24
Unfortunatelly there is no "gold rule" for choosing HDD today. After famous 7200.7 Seagate started to manufacture not-so good 7200.8-10 and 11,12 had terrible bugs in firmware that caused hundreds of thousands devices to fail. (I'm curious who's buying their drives now)
 I would say that from desktop hdd's WD is still most trustworthy - very low failure rate, real SMART support (the only manufacturer that follows specs to the letter), full (S)ATA command set support (f.e. you can do many tricks with hdparm such as tunning power management, AAM, etc)

---

### Post by psusi on 2011-01-24
> **tomazzi said:**
> 
 I would say that from desktop hdd's WD is still most trustworthy - very low failure rate, real SMART support (the only manufacturer that follows specs to the letter), full (S)ATA command set support (f.e. you can do many tricks with hdparm such as tunning power management, AAM, etc)

WD has been having some serious failure rates with the EARS series lately, and the elements line of external drives are being shipped with a subtly invalid format, apparently because the enclosure makes the drive appear slightly smaller than it is.  They also do not support the power on in standby command, though they have a jumper for doing that.

---

### Post by disabledaccount on 2011-01-24
> **psusi said:**
> WD has been having some serious failure rates with the EARS series lately, and the elements line of external drives are being shipped with a subtly invalid format, apparently because the enclosure makes the drive appear slightly smaller than it is.So I said "there is no gold rule" - every manufacturer sometimes  releases faulty models. Baracuda 11 and 12 is just extreme case.
> **psusi said:**
> They also do not support the power on in standby command, though they have a jumper for doing that.This is misunderstanding - the jumper allows to control PM by software or to override software config. This is very important if You have to move hdd to some ****** mobo/controller that don't supoport Power-on-in-standby - without this jumper you won't be able to use drives with that option enabled.

---

### Post by psusi on 2011-01-24
> **tomazzi said:**
> This is misunderstanding - the jumper allows to control PM by software or to override software config. This is very important if You have to move hdd to some ****** mobo/controller that don't supoport Power-on-in-standby - without this jumper you won't be able to use drives with that option enabled.

It rejected the command to enable it originally so I set the jumper and then it just does it -- stays in standby on power up.  Of course, the kernel still seems to wake the darn thing when coming out of suspend for some reason I have yet to track down and kill.

Now that I look again, hdparm -I does list it as a supported feature, but the star in the enabled column is missing.  Is there something you have to do to enable it ( other than -s )?

---

### Post by Vegan on 2011-01-24
I should mention my old WDC 500 GB disk did not make it to 20,000 hours before it failed completely.

[http://www.windows-it.tk/papers/disk-reliability.php]("http://www.windows-it.tk/papers/disk-reliability.php")

I was very disappointed that it died as it was not all that old.

I cannot afford to buy disks with that crappy life.

---

### Post by disabledaccount on 2011-01-25
psusi:
I've tested it long ago with 4xWD160JD and it worked, so I don't know why Your settings disapeared. Have you tried to set "keep settings over reset" flag ?

vegan: You can't judge particular model on the basis of one failure. HDD's life depends on hundreds of factors - nobody have good formula to predict even percentage of failures.

HDD failures research results (by Google):
[http://labs.google.com/papers/disk_failures.pdf](http://labs.google.com/papers/disk_failures.pdf)

---

### Post by cascade9 on 2011-01-25
> **CharlesA said:**
> I thought the MTBF was something like 100,000 hours?

In any case, if you keep an eye on bad sectors and whatnot, you should be fine until the disk dies.

Just be sure you have backups. :)

MTBF is misused, and at best an educated guess- 

> To illustrate this misunderstanding, the death rate for 25-year-old people is about 0.1% per year. This is equivalent to an MTBF of 800 years, but few of us expect to last that long.

Snip!

Remember, without decades of experience to call upon to measure MTBF, it is just a calculation based on a set of assumptions about the components used in the product. Different methodologies will use different sets of assumptions.[http://electronicdesign.com/article/power/mtbf_and_reliability_a_misunderstood_relationship_in_solar_photovoltaics.aspx](http://electronicdesign.com/article/power/mtbf_and_reliability_a_misunderstood_relationship_in_solar_photovoltaics.aspx)

Yes, I know, the article focus is solar panels, but the points raised on MTBF apply to computers as well.

---

### Post by CharlesA on 2011-01-25
> **cascade9 said:**
> MTBF is misused, and at best an educated guess- 

Figured as much.

You can make statistics say anything you want. ;)

---

### Post by psusi on 2011-01-25
> **tomazzi said:**
> psusi:
I've tested it long ago with 4xWD160JD and it worked, so I don't know why Your settings disapeared. Have you tried to set "keep settings over reset" flag ?


It did not disappear; the drive rejected the command like it did not support it.  This seems to make sense since hdparm -I shows that command set as not being enabled ( listed, but no * in the enabled column ), so the question is, how to enable it?

MTBF does not mean that is how long your drive will last.  It means that if you have 10,000 drives and average their life span, it should be about the MTBF.

---

### Post by cascade9 on 2011-01-25
> **psusi said:**
> MTBF does not mean that is how long your drive will last.  It means that if you have 10,000 drives and average their life span, it should be about the MTBF.

No, it doesnt. Lots of hardware (and other things!) have a MTBF far, far bigger than the predicted lifespan. Or even the 'omg we didnt think it would last that long' lifespan.

---

### Post by psusi on 2011-01-25
> **cascade9 said:**
> No, it doesnt.

Yes, it does.  See [http://en.wikipedia.org/wiki/MTBF](http://en.wikipedia.org/wiki/MTBF).

---

### Post by cascade9 on 2011-01-25
> **psusi said:**
> Yes, it does.  See [http://en.wikipedia.org/wiki/MTBF](http://en.wikipedia.org/wiki/MTBF).

No, it doesnt. Even that wikipedia link say that (in statisticese)- "MTBF can be calculated as the [arithmetic mean]("http://en.wikipedia.org/wiki/Arithmetic_mean") (average) time between [failures]("http://en.wikipedia.org/wiki/Failure") of a system". Or, to put it another way- 

> MTBF sounds simple: the total time measured divided by the total number of failures observed. For example, let's wring out a new generation of 2.5-in. SCSI enterprise hard drives. We run 15,400 initial units for 1,000 hours each (thus our tests take a little less than six weeks), and we find 11 failures. The MTBF is (15,400 x 1,000) hours/11, or 1.4 million hours. (This is not a hypothetical MTBF; it represents current drive technology in 2005.)

What does this calculation really mean? An MTBF of 1.4 million hours, determined in six weeks of testing, certainly doesn't say we can expect an individual drive to operate for 159 years before failing. MTBF is a statistical measure, and as such, it can't predict anything for a single unit. We can use that MTBF rating more accurately, however, to calculate that if we have 1,000 such drives operating continuously in a data centre, we can expect one to fail every 58 days or so, for a total of perhaps 19 failures in three years.

[http://features.techworld.com/operating-systems/1944/mtbf-what-lifespan-can-you-expect/](http://features.techworld.com/operating-systems/1944/mtbf-what-lifespan-can-you-expect/)

Like that quote above said, a MTBF of 1,400,000 does not translate to a lifespan of 159 years. It means that (averaged) if you are running 1,000 drives, you can expect one failure every 1400 hours (58days) in the 'constant failure rate' part of the lifespan. 

Once out of the 'constant failure rate' part of the lifespan, failure rates will get a lot higher. I'd doubt that even 1% of drives with a MFBT of 1,400,000 will even get close to 160 years of use.... 

The example used in post #26  is actually a rephrasing of a classic MTBF borderline rant, here- 

[http://www.faqs.org/faqs/arch-storage/part2/section-151.html](http://www.faqs.org/faqs/arch-storage/part2/section-151.html)

Well worth a read.

---

### Post by psusi on 2011-01-25
What the hell?  That is a completely useless number then.  Who gives a crap what the failure rate is at the bottom of the bathtub?  Failure includes the whole life of the drive, not just the part after you throw out infant mortality and everything that reaches its expected lifetime.  You want to know where the edge of the bathtub is.

Of course, that is also the number they use to determine the length of their warranty.

---

### Post by cascade9 on 2011-01-25
> **psusi said:**
> What the hell?  That is a completely useless number then.  Who gives a crap what the failure rate is at the bottom of the bathtub?  Failure includes the whole life of the drive, not just the part after you throw out infant mortality and everything that reaches its expected lifetime.  You want to know where the edge of the bathtub is.

Thats more polite than my reaction when I got my head around MTBF. I agree 100%.

---

### Post by Vegan on 2011-01-25
I can show how MTBF is misleading, its not hard. 

What I am looking at is something like LD50 where 50% of disks are dead after some period of time.

LD50 is a far more revealing value, at the point where 50% are dead will allow a simple differential equation to plot the expected survival rate at any point.

This only assumes an exponential decay rate. This is widely used in population studies, so substitute disks for people.

---

### Post by Vegan on 2011-01-27
So who has the more than 40K hours like my disk does?

---

### Post by CharlesA on 2011-01-27
I'm only up to about 12K hours.

---

### Post by cascade9 on 2011-01-28
> **Vegan said:**
> So who has the more than 40K hours like my disk does?

Is it a competition? :lolflag: 

I'll try to check the old scsi RAID setup in a few days, I'm pretty sure that had some stupid amount of hours on it.

---

### Post by Vegan on 2011-01-28
In light of the suggestion my disk in nearly invincible, I was curious to see what else came close.

---

### Post by disabledaccount on 2011-01-29
This drive (WD AL2540 - see attachment) does't support SMART, but it still works in some very old and very unique Siemens computer (S5 PLC on AT bus) - I can only estimate it's power on hours - about 100'000 (Machine is never turned off, air conditioned). I had occasion to made the picture during replacement of ATA controller card that have died abut 3 years ago.

---

### Post by Vegan on 2011-01-29
I have some Fujitsu disks that show power on minutes/seconds rather than hours. They are in a box of spares in case the web server disk breaks.

I have a 80GB WD disk which has < 10,000 hours on it, so its next up for a spare.

---

### Post by Vegan on 2011-01-29
> **tomazzi said:**
> This drive (WD AL2540 - see attachment) does't support SMART, but it still works in some very old and very unique Siemens computer (S5 PLC on AT bus) - I can only estimate it's power on hours - about 100'000 (Machine is never turned off, air conditioned). I had occasion to made the picture during replacement of ATA controller card that have died abut 3 years ago.

That is curious that a paddle board would croak.

I backup my Acer daily so if it blows up I am ready to fix it.

The 160 GB disk is plenty of room for my needs. Only my chess site wants more space.

---

### Post by Vegan on 2011-02-04
I see that on my Windows box my system disk has racked up a lot of hours too.

The 320 GB disk has 18,000 hours, the 500 GB disk has 22,000 hours on it. Both disks are Seagate.

I am now building a table for disks in the shop so I can build better statistics.

---

### Post by CharlesA on 2011-02-04
You, sir are nuts! :lol:

---

### Post by Vegan on 2011-02-04
I have cleaned up my page on hard disks, now it has a chart.

Operational disks are green, dead are red and spares are blue

[http://www.windows-it.tk/papers/disk-reliability.php]("http://www.windows-it.tk/papers/disk-reliability.php")

As I get more disks the table and chart will be expanded.

I also linked to Wikipedia for technical articles.

---

### Post by CharlesA on 2011-02-04
Nice chart. :)

---

### Post by Vegan on 2011-02-04
Thanks, I think that in time its going to be the most telling.

Picture = 1000 words? About right for a corporate graphic.

---

### Post by Vegan on 2011-02-20
So now the disk is up to 41,000 hours and still ticking.

Brand new 500 GB Seagate disk, DOA


I have this 20 GB Fujitsu but I do not know that the POH value is actually measuring? 

Is it in minutes? Seconds?

---

### Post by Vegan on 2011-04-05
More hard disks on the chart, and updated the graphic too.

[http://www.windows-it.tk/papers/disk-reliability.php](http://www.windows-it.tk/papers/disk-reliability.php)

Always looking for more storage, I am one who like backups of the backups of the backups

---

### Post by matt_symes on 2011-04-05
Hi

> **Vegan said:**
> More hard disks on the chart, and updated the graphic too.

[http://www.windows-it.tk/papers/disk-reliability.php](http://www.windows-it.tk/papers/disk-reliability.php)

Always looking for more storage, I am one who like backups of the backups of the backups

This is an interesting thread that i have been following from the start.

Your statistics are fascinating. Please keep reporting them.

Kind regards

---

### Post by Vegan on 2011-04-09
That page has become a popular destination on my IT site.

To do it justice, I need a vast number of disks and more USB thermometers.

The Linux box is now well past 42,000 hours and it seems to be invincible.

---

