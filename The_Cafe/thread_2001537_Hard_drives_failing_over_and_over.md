---
title: "Hard drives failing over and over"
date: 2012-06-11
forum: The Cafe
---

### Post by parkland on 2012-06-11
Now this isn't a ubuntu based issue,
But I wanted to share it with you all. 
This is the 3rd time my HD has failed in my living room desktop. 
Last drive I put in, I put a double fan on it, and extra case fan, everything has been cool. (I thought heat might have been an issue).

8 current pending sector counts,
7,858,730 On the fly errors. 

1 word:
Subwoofer. 
I had read about how this might case issues, but I never thought this little computer sound system would rattle the disk enought to ever effect it. 
I have 3 other computers here... one is about 10 years old... still original disk. 
Other one 7 years old, still original disk. 

I am now pegging vibrations and noise as a serious HD killer. I think I'll put a little SSD HD in this unit, and build a storage server downstairs away from any noise or vibrations. 

Anyone have any leads or advice to HD's other than my usual tigerdirect bargain bin? lol. 

:popcorn:

---

### Post by Elfy on 2012-06-11
*Thread moved to **The Community Cafe**.*

---

### Post by roelforg on 2012-06-11
Funny, one of my systems is placed atop of a speaker with a subwoofer that's lager then my face, the same speaker i always play songs with quite a bit of bass and that computer's still going strong on the same hd it had for ages (not the original hd because i swapped it out when i got the system, like i do with every system of mine that isn't a laptop or so old that it's parts won't fit on other systems).
 
(PS. I have a 20yrs old computer with it's original hd still going strong, what's the point you're trying to make?)

---

### Post by Bandit on 2012-06-11
@OP, May I ask if you have your system on a battery backup (UPS type)?

---

### Post by jmore9 on 2012-06-11
I am still using a 6.5 or 6.something hard drive that is still going strong.  It was orginally used in an p2 300 something dell.  No noise or sluggishness.

Also have a couple of elderly 20 gigs and 40 gigs i use often for backs and test machines.  Still going fine.

Running ubuntu 12.04 with 4 drives from 200gig to 1gig ( no used ones bought all new ) and had 11.10 and 10.04 on previously.

If it is very hot near the machines i remove the side cover so more air can get out.  this works for me maybe work for you also.

---

### Post by roelforg on 2012-06-11
> **jmore9 said:**
> I am still using a 6.5 or 6.something hard drive that is still going strong.  It was orginally used in an p2 300 something dell.  No noise or sluggishness.

Also have a couple of elderly 20 gigs and 40 gigs i use often for backs and test machines.  Still going fine.

Running ubuntu 12.04 with 4 drives from 200gig to 1gig ( no used ones bought all new ) and had 11.10 and 10.04 on previously.

If it is very hot near the machines i remove the side cover so more air can get out.  this works for me maybe work for you also.

I have one 40mb hdd that's still going strong after 20yrs.

---

### Post by cariboo on 2012-06-11
@parkland, you failed to mention what make and model hard drive you are having problems with. I've had a Seagate 750GiB replaced twice under warranty, and it needs to be replaced again, fortunately, it's still under warranty until October 2013, so It's going back a third time. The first two times it failed, it was in my server,which sits on a shelf in my garage, this time around it's in an external enclosure, still connected to the server, but only used as a secondary backup device.

---

### Post by drawkcab on 2012-06-11
I never thought of that but I suppose a subwoofer could chew up a hdd over time.

---

### Post by Paqman on 2012-06-11
If heat is not the issue then I'd look at other causes. Quality of power supply, vibration and maybe dust are worth taking a look at. I suspect it's the power supply personally.

---

### Post by parkland on 2012-06-11
> **Bandit said:**
> @OP, May I ask if you have your system on a battery backup (UPS type)?


No, it is not.

---

### Post by parkland on 2012-06-11
> **cariboo907 said:**
> @parkland, you failed to mention what make and model hard drive you are having problems with. I've had a Seagate 750GiB replaced twice under warranty, and it needs to be replaced again, fortunately, it's still under warranty until October 2013, so It's going back a third time. The first two times it failed, it was in my server,which sits on a shelf in my garage, this time around it's in an external enclosure, still connected to the server, but only used as a secondary backup device.


I do believe it's a seagate. 90% sure. 

I paid a lot for it several months ago when everyone was whining about hard drive factories getting flooded or something.

---

### Post by parkland on 2012-06-11
> **Paqman said:**
> If heat is not the issue then I'd look at other causes. Quality of power supply, vibration and maybe dust are worth taking a look at. I suspect it's the power supply personally.


Heat is definately not an issue now, I can assure you. 
Once in a while, I shut her down and get all the dust out too. 

I don't get how a power issue could cause data access errors, but maybe you're right. 

Does anyone else feel like maybe the MFG's are pushing the capacities of these drives far enough to sacrifice reliability?

They should produce a low speed high reliability high capacity 6.25" HD. 4 platters and 8 TB !!! :guitar:

I'd buy one !!!

---

### Post by parkland on 2012-06-11
Yeah it was a seagate barricuda 2.0tb.

---

### Post by CharlesA on 2012-06-11
I've had some bad sectors on the drives in my RAID array, but so far the numbers have been staying put. Not too bad if I consider how many hours they have been running:

```
RAID Drive 1
SMART			PASSED
Power On Hours		23416
Reallocated Sector Ct	0
Reallocated Event Count	0
Current Pending Sector	0
Offline Uncorrectable	0

RAID Drive 2
SMART			PASSED
Power On Hours		23420
Reallocated Sector Ct	8
Reallocated Event Count	11
Current Pending Sector	0
Offline Uncorrectable	0

RAID Drive 3
SMART			PASSED
Power On Hours		23416
Reallocated Sector Ct	3
Reallocated Event Count	3
Current Pending Sector	0
Offline Uncorrectable	0
```

These are all Hitachi DeskStar (DeathStar?) 2TB drives.

---

### Post by Paqman on 2012-06-11
> **parkland said:**
> 
I don't get how a power issue could cause data access errors, but maybe you're right. 


Power supply problems can cause all sorts of weird behaviour in electronics.

---

### Post by sammiev on 2012-06-11
My HD did the same thing and I found it to be the power supply after changing the second HD. :)

---

### Post by mywai on 2012-06-11
Do you have a good size, magnetically non-shielded subwoofer?  Is your desktop right next to it?

---

### Post by Bandit on 2012-06-11
> **Paqman said:**
> If heat is not the issue then I'd look at other causes. Quality of power supply, vibration and maybe dust are worth taking a look at. I suspect it's the power supply personally.
A very good possibility. 

> **parkland said:**
> No, it is not.
Like Paqman mentioned power supply not being large enough. Also I asked about the UPS because you can have brown outs where power voltage drops lower then normal causing hardware to heat up and devices burn up/fail.

---

### Post by parkland on 2012-06-12
> **Bandit said:**
> A very good possibility. 


Like Paqman mentioned power supply not being large enough. Also I asked about the UPS because you can have brown outs where power voltage drops lower then normal causing hardware to heat up and devices burn up/fail.


Maybe I'll get a new power supply. 
I'm still thinkin of building a storage server with raid. 
Maybe I can justify it if I use network booting. 


Whats the best drive to buy with 2.0tb of room? 

I dont need high performance, just room and reliability!!!!!!!

---

### Post by parkland on 2012-06-12
Are there any really reliable big drive? 
I keep reading and it seems like every brand has more problems now than ever before.
Is it time to build a raid server and network boot 3-4 machines off it? 


Is there a ubuntu based way to mirror drives and also allow reading from different spots on both, thus reducing seek times? 
Will gigabit ethernet be fast enough? 
I think it will be. 
What raid will work best to make a 8 tb array? 

What about 2 JBOD arrays,allow reading from different spots in either array, but force writes to both?

---

### Post by Artemis3 on 2012-06-12
Try getting a quality power supply. You could also make sure your case is resistant to vibration, use rubber feet or such. The woofer should not make it fail, but it will make it under-perform. Drives tend to slow down with vibration. Well, unless you have that special kind of system some guys use in cars... Then you might as well get an SSD.

After the flooding in Thailand purchasing a drive was madness, thankfully i purchased a couple of 2tb seagates a month before the disaster for 80$ each. I believe by now prices have gone back to normal, but the very same drives were over 200$ last October.

Note: i do have an 8" subwoofer, but i calibrate the sound as close as i can to flat response.

Make sure your power socket is properly grounded, use an ups if you can after getting a quality PSU. Don't use molex to power sata adapters, make sure you new psu has all you need.

---

### Post by Bandit on 2012-06-12
> **parkland said:**
> Are there any really reliable big drive? 
Everyone here will prob tell you their own preferences on brands. If I was you I would read reviews from other people who purchased the drives. Like off Newegg or TigerDirect. Me personally I would go with Western Digital. Preferably a Caviar Blue drive, they have respectable speed and are designed to run silent, cool and continuous without issues. 

> 
I keep reading and it seems like every brand has more problems now than ever before.
Keep in mind, more people complain then those that dont. So more often then not unless people are amazed with something, only the complainers post reviews. So anything with a 4 out of 5 raiting is normally a safe bet.

> 
Is it time to build a raid server and network boot 3-4 machines off it? 

That up to you. Unless you got a 1000base-t I wouldnt.

> 
Is there a ubuntu based way to mirror drives and also allow reading from different spots on both, thus reducing seek times? 

Yes and No, yes you can set up JBOD to read from multiple partitions off seperate drives and their is also RAID setups that can boost performance and/or reliability. But none of these will boost seek times. Seek times are only increased by the rotation speed and HDD plater sizes.

> 
Will gigabit ethernet be fast enough? 
I think it will be. 

Yes

> 
What raid will work best to make a 8 tb array?

That up to you. RAID 0 is easy and good performance, RAID 1 is mirroring, RAID 5 is a mix between the previous two and RAID 1+0 (10) is a hybrid between the first two and supossed to be much better (performance and reliability) then RAID 5. 

> 
What about 2 JBOD arrays,allow reading from different spots in either array, but force writes to both?
Thats up to you. But JBOD doesnt offer performance gains. Its just a bunch of ordinary disc setup to virtually increase size.

---

### Post by CharlesA on 2012-06-12
> **Bandit said:**
> Everyone here will prob tell you their a

Keep in mind, more people complain then those that dont. So more often then not unless people are amazed with something, only the complainers post reviews. So anything with a 4 out of 5 raiting is normally a safe bet.

Pretty much. I went with the DeskStar drives cuz they were cheap, but they are not exactly "raid drives" like WD RE drives, but they have not given me any problems yet.

I don't see any reason to use RAID0, as there is no redundancy at all. If you lose one drive, you lose the entire array, which is very bad for a file server.

Also keep in mind that RAID is no substitute for backups, either.

If you have more than 3 or 4 drives, I would go with RAID6, personally.

In order to get around 8TB, you would need 6 2TB drives, or 5 3TB drives.

See here (courtesy of [rubylaser]("http://ubuntuforums.org/member.php?u=1115132"))
[http://zackreed.me/articles?tag_id=21](http://zackreed.me/articles?tag_id=21)

---

### Post by ssam on 2012-06-12
you could get something like these
[http://www.quietpc.com/products/harddrivesolutions/hd-stabiliser](http://www.quietpc.com/products/harddrivesolutions/hd-stabiliser)
to reduce the vibrations (assuming you have a spare 5.25" bay).

---

### Post by sdowney717 on 2012-06-12
> **parkland said:**
> Yeah it was a seagate barricuda 2.0tb.

That is the problem right there.
When I was looking to get a good drive I heard lots of complaints about that manufacturer, also including bad firmware causing failures.

Mine is a Hitachi HDS721075KLA330 750gb
been perfect so far. Has been powered on for 2.6 years.
This computer is on all the time

---

### Post by parkland on 2012-06-12
> **sdowney717 said:**
> That is the problem right there.
When I was looking to get a good drive I heard lots of complaints about that manufacturer, also including bad firmware causing failures.

Mine is a Hitachi HDS721075KLA330 750gb
been perfect so far. Has been powered on for 2.6 years.
This computer is on all the time



This computer is on all the time as well. 

161 day of run time. 

I just read a lot about the seagate string of bad drives, thats too bad. 

I realise a hard drive can and will eventually fail, I just want to get my hands on some that have a 1/10 chance of failing within a year, not a 1/2 chance lol.

---

### Post by parkland on 2012-06-12
Wow... now I just feel stupid. 

Just looked... old HD was a barricuda 1.5 tb, and the previous one to that also a barracuda 1.5 TB. 


I guess I'm truly a sucker.

---

### Post by Paqman on 2012-06-13
> **parkland said:**
> Wow... now I just feel stupid. 

Just looked... old HD was a barricuda 1.5 tb, and the previous one to that also a barracuda 1.5 TB. 


I guess I'm truly a sucker.

I've used (and still use) Barracudas myself, and haven't found them any less reliable than other brands.

IMO most of the major brands are of similar reliability (ie: rubbish). Spinning hard drives are inherently unreliable. The fact they cram so many tiny moving parts in with such tight tolerances is a small marvel in itself, but means they're never going to be long-lived components.

> **parkland said:**
> This computer is on all the time as well. 

161 day of run time. 


Awesome, should still be under warranty. Free replacement time!

---

### Post by AnotherMuggle on 2012-06-13
> **Bandit said:**
> Everyone here will prob tell you their own preferences on brands. If I was you I would read reviews from other people who purchased the drives. Like off Newegg or TigerDirect. Me personally I would go with Western Digital. Preferably a Caviar Blue drive, they have respectable speed and are designed to run silent, cool and continuous without issues. 


Another vote for Western Digital here, though I would recommend Caviar Black rather than Blue.  They have a 5 year warranty instead of only 2 years.

---

### Post by CharlesA on 2012-06-13
> **Paqman said:**
> I've used (and still use) Barracudas myself, and haven't found them any less reliable than other brands.

IMO most of the major brands are of similar reliability (ie: rubbish). Spinning hard drives are inherently unreliable. The fact they cram so many tiny moving parts in with such tight tolerances is a small marvel in itself, but means they're never going to be long-lived components.

Same. I have used WD, Seagate, Maxtor (back when they were still Maxtor), Hitatchi, IBM, and Samsung drives and haven't run into any issues with reliability (or lack there of) depending on brand.

---

### Post by AnotherMuggle on 2012-06-13
> **CharlesA said:**
> Same. I have used WD, Seagate, Maxtor (back when they were still Maxtor), Hitatchi, IBM, and Samsung drives and haven't run into any issues with reliability (or lack there of) depending on brand.

Samsung is the only brand of drive I've owned which has failed prematurely.  It's also the only drive I've had which has failed at all, so it doesn't mean Samsung are bad, but I wouldn't choose one again based on my own personal experience.  For this reason people will all go with what they have personally experienced whether their experience is the general rule or exeception to the rule.

---

### Post by CharlesA on 2012-06-13
> **AnotherMuggle said:**
> Samsung is the only brand of drive I've owned which has failed prematurely.  It's also the only drive I've had which has failed at all, so it doesn't mean Samsung are bad, but I wouldn't choose one again based on my own personal experience.  For this reason people will all go with what they have personally experienced whether their experience is the general rule or exeception to the rule.
That's pretty much it. I'll just blame it on personal experience and brand loyalty. ;)

Example: I've been using Seagate external drives for a long, long time and I've had no problems with them --> keep buying seagate external drives. :p

---

### Post by Paqman on 2012-06-14
> **CharlesA said:**
> That's pretty much it. I'll just blame it on personal experience and brand loyalty. ;)

Example: I've been using Seagate external drives for a long, long time and I've had no problems with them --> keep buying seagate external drives. :p

Exactly. Bottom line however is that any one individual's sample size is way too small to make any grand statements about the overall reliability of a particular brand. Even big studies such as [this one]("http://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/en//archive/disk_failures.pdf") don't find any strong correlation between manufacturer and reliability (although they do find it between certain models and reliability).

---

### Post by CharlesA on 2012-06-14
Nice link. I remember reading about that a while ago.

In any case, pick a drive, make backups and don't worry about if/when the drive dies cuz if it does, you did have a recent backup... right? ;)

---

### Post by kelvin spratt on 2012-06-14
Well I'm a bit lax never backed up and in 15 years never had a drive fail that's all brands. Running continuous has a big advantage as most components fail on start-up + every component is running at optimum temp.  
I also have a 2tb western digital green over a year and its silent.
I had a friend ask me to look a old 120gb western that was in all tence and purposes dead turned off smart data. used hirens boot disc 000000 disc then used repair bad sectors and bingo. 2 years on still  running smart data says its OK  reports failure in the past. Turned out they were not shutting-down just pulling the plug basically
My advice is fit a power supply as big as possible always better to use parts overrated than on the edge.

---

### Post by CharlesA on 2012-06-14
> **kelvin spratt said:**
> 
My advice is fit a power supply as big as possible always better to use parts overrated than on the edge.

Agreed. I try to get things like power supplies (and UPSes) with a higher wattage than I will need. That way I don't overload them and cause problems. Clean power is good power.

I'm sure it's documented somewhere, but PSUs work best when they are at around 70-80% of load. Or at least that is what I have been told.

A quick google found this:
[http://www.silentpcreview.com/article28-page3.html](http://www.silentpcreview.com/article28-page3.html)

---

### Post by stalkingwolf on 2012-06-14
I have had failing or bad PSU's do all manner of weird things.  knock out usb, on board video,pci slots and hard drives.

I have used wd,seagate,maxtor,hitachi toshiba, and fujitsu drives.  Ive used used drives and refurbished drives.  I have used the HD regenerator on the heirens disk to rescue several old drives.

I recently worked with a 6.4 gb drive (maxtor as i recall) from a computer running win98 (the first 98) and gwbasic.  cloned it to a new computer.  the original drive still works fine.
when i finished the owner had a triple boot system.  His original 98 system,
win xp, and zorin 5.2.  all with the capability of running his prized gwbasic.

He was quite happy.

---

### Post by AnotherMuggle on 2012-06-14
> **kelvin spratt said:**
> 
My advice is fit a power supply as big as possible always better to use parts overrated than on the edge.

I'm not sure I agree with this statement.  It's far more important to buy a good quality power supply.  You should pay for quality, not quantity (of power).  A lower (but adequately) rated, decent quality, PSU is far better than an overkill powered unit of lesser quality.

For example a Seasonic, Enermax or Corsair PSU is better for your system than the likes of Coolmax or Q-Tec or any unbranded model.

---

### Post by MisterGaribaldi on 2012-06-14
Ok, been eyeballing this thread now for a while.

At one point in time or another, probably all hard drive manufacturers have had either bad batches of HDDs, or a fundamental design flaw which affected one or more series of drives. It happens. That being said, if you're buying HDD after HDD, or getting warrantied replacement after warrantied replacement, and they all keep failing on you, it's much more likely your environment is doing to your HDDs what Ben Schulz's Leeroy Jenkins so famously did to his WoW party.

If I were to hazard a guess, the problem is likely to be inside your computer, unless that sub of yours is in fact unshielded and really, really close. Besides, if you don't mind my asking, why on Earth would you put a computer right next to a speaker in the first place?

I would also like to add that it's been a concern of mine for some time now whether HDDs are getting made too much "on the cheap" and so experiencing failure rates which are therefore artificially higher than they should be. Remember that your higher RPM'd HDDs (7200 and 10,000) require increasing amounts of airflow and cooling, and ideally you should, in a tower system, be looking at some kind of HDD bay fan solution to specifically manage their thermal profile. Heat absolutely can kill an HDD. Other than that, you might have a flakey PSU, and that kind of crap can kill stuff. I've had a bad PSU frag my RAM before.

Good luck!

---

