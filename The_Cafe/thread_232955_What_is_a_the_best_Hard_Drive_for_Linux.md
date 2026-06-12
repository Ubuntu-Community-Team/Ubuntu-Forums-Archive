---
title: "What is a the best Hard Drive for Linux?"
date: 2006-08-09
forum: The Cafe
---

### Post by Johnsie on 2006-08-09
Out of Maxtor and Western Digital? Out of the two which would you consider to be most reliable and long-lasting?

---

### Post by dabear on 2006-08-09
Both? One hard drive is not better suited than the other to run ubuntu or linux in general (although sata drives has been a problem for some?)

---

### Post by ember on 2006-08-09
Samsung :)

---

### Post by tseliot on 2006-08-09
All the hard disks I have are maxtor:
2 on my desktop computer
2 on my old desktop
1 on my father's desktop
1 on my Xbox

They all work great with Linux. And they haven't let me down yet.

---

### Post by arsenic23 on 2006-08-09
Western Digital should have a longer warrenty.  So I'd go with them : )

---

### Post by Bezmotivnik on 2006-08-09
> **arsenic23 said:**
> Western Digital should have a longer warrenty.  So I'd go with them : )
Only if you pay extra for it.

WD dropped their otherwise excellent three-year free warranty. :( The last one I bought a few months ago had a one-year warranty with an insert trying to **sell** me the old three-year one. [-( 

For reasons that I don't fully understand, Maxtors seem to run *very* hot compared to my Seagates, Hitachis and WDs.  This may account for the terrible anecdotal reputation Maxtors have on tech fora for early failure.

I use them, but make sure that they have dedicated fans on them to keep the heat down.  I would never use one in, say, a non-ventilated USB enclosure.

---

### Post by Super King on 2006-08-09
I don't mean to hijack this thread, but I'm wondering what sort of problems with SATA drives and Ubuntu people are having. I ask because like the original poster I'm also searching for a hard drive to dual boot XP and Xubuntu, and was looking at this one (Seagate Barracuda).

[http://www.newegg.com/Product/CustratingReview.asp?Item=N82E16822148107](http://www.newegg.com/Product/CustratingReview.asp?Item=N82E16822148107)

---

### Post by WildTangent on 2006-08-09
SATA drives themselves aren't a problem, it's the controllers that are. Anyway, I've heard enough horror stories to steer well clear of Maxtor. I personally seem to prefer Western Digital, but I'd buy Seagate too, they're just as good. Hitachi, and Toshiba drives are sometimes more expensive because they're not as common around here. I hear Toshiba drives are very quiet.

-Wild

---

### Post by Virogenesis on 2006-08-10
seagate offer the longest warrenty but now maxtor and seagate have merged I believe maxtor now offer the same warrenty as seagate.
I have both maxtor and western digital both are great another thing to consider is how much you lose when you format.

Hitachi I don't trust.
Seagate offer 5 yr warrenty

---

### Post by mips on 2006-08-10
1. Seagate
2. Western Digital
For 3.5" drives

I personally find Maxtor to be very unreliable, seen way to many of them replaced in my lifetime.

---

### Post by 23meg on 2006-08-10
Maxtor and WD have been the two most reliable brands among all the HDs I've owned and based only on personal experience I don't think you can go very wrong with either. The worst two, in case you're wondering, have been IBM and Seagate.

You'll get good and bad opinions about every brand. My opinion: instead of questioning too deeply about reliability, concentrate on the specs (RPM, seek time, cache, capacity etc.) and whether they'll serve your purpose, and whether you have a reasonable warranty option. And then while you're using the drive, stick to the most basic principle: having backups.

---

### Post by PenguinMan on 2006-08-10
[COLOR=Purple]Personally, I use Seagate SATA HDs without any problems whatsoever. Same goes for the computers we build - only Seagate on them. I like the quality of their HDs...
[/COLOR]

---

### Post by arsenic23 on 2006-08-12
If you purchase the right model, Western Digital drives have 5 year warrenties as well.   They also run cooler then Seagate ( in most cases ).  This is why I recomend WD.

---

### Post by GuitarHero on 2006-08-12
[http://www.newegg.com/Product/Product.asp?Item=N82E16822144414](http://www.newegg.com/Product/Product.asp?Item=N82E16822144414)
That's a deal right there.

---

### Post by CREEPING DEATH on 2006-08-12
Seagate has the best warranty, are less expensive, and have an available **16mb buffer** insterad of the standard 8mb

CD

---

### Post by Cariboo1938 on 2006-08-12
> **mips said:**
> 1. Seagate
2. Western Digital
For 3.5" drives

I personally find Maxtor to be very unreliable, seen way to many of them replaced in my lifetime.I have two Maxtor SATA hard drives on the "SATA/RAID chipset Sil3112" or no "nFORCE3 ultra" running for a years without any, any! problem.

---

### Post by ubuntu_demon on 2006-08-14
Personally I like western digital. I've good experiences with these harddrives. I've never bought Maxtor so I've no experiences with their drives. But on general I think there probably isn't much difference. 

I just ordered a Western Digital 3200KS. It's a 320 GB, SATA2, 10.000rpm, 16MB cache drive. I ordered it from a duch company for 106,20 euros.

Here's a recent review of this particular harddrive :
[http://www.anandtech.com/storage/showdoc.aspx?i=2803](http://www.anandtech.com/storage/showdoc.aspx?i=2803)

Why I choose this harddrive :
-it's cheap
-it's Western Digital (good experiences with them)
-it has good performance
-accoustics and thermals are good according to te anandtech review

This will double my total harddrive capacity.

In my desktop I have a 40 GB (WD) PATA drive. My motherboard supports SATA so I'm going to install Ubuntu on this new drive and increase my computers performance a fair bit (especially boot time).

---

### Post by mips on 2006-08-14
> **Cariboo1938 said:**
> I have two Maxtor SATA hard drives on the "SATA/RAID chipset Sil3112" or no "nFORCE3 ultra" running for a years without any, any! problem.

Well good for you. In a corporate environment using compaq/hp desktops with maxtor drives I have seen so many hd failures it's scary, thats even before the warranty expired. All the replacement drives were seagate or wd with little to no problems. In my own personal capacity I have lost 3 Maxtor drives, never again.

Others might have different luck.

---

### Post by ubuntu_demon on 2006-09-17
The performance of my new WD 3200KS :

> 
$hdparm -tT /dev/sda1
/dev/sda1:
 Timing cached reads:   3840 MB in  2.00 seconds = 1921.34 MB/sec
 Timing buffered disk reads:  190 MB in  3.01 seconds =  63.11 MB/sec


The only tweak I did was that I set it to 32bit transfer in my bios.

For comparison my WD 400JB with 8mb cache :

> 
$ hdparm -tT /dev/hde
/dev/hde:
 Timing cached reads:   3700 MB in  2.00 seconds = 1851.31 MB/sec
 Timing buffered disk reads:   68 MB in  3.03 seconds =  22.48 MB/sec


---

### Post by alecjw on 2006-09-17
My Western Digital gets very hot. In fact, some of the plastic on it has melted!

---

### Post by ubuntu_demon on 2006-09-22
> **alecjw said:**
> My Western Digital gets very hot. In fact, some of the plastic on it has melted!
What model do you have ?

I'm going to check the temparature of mine (I don't have acces to my desktop currently).

---

### Post by Efros on 2006-12-13
[http://www.newegg.com/Product/Product.asp?Item=N82E16822148136](http://www.newegg.com/Product/Product.asp?Item=N82E16822148136)

I've bought two of the above, 2x 500GB 7200 RPM 16MB Cache SATA 3.0Gb/s, which come free with 2x ST3250824AS 250GB 7200 RPM SATA 3.0Gb/s all for 414 dollars wth free shipping offer open until end dec 2006

---

### Post by kuja on 2006-12-13
I personally wouldn't trust a maxtor, not one that has been put out within the last couple years anyway. The old ones always worked well for me, but I hear it's the new ones in particular that are prone to failure. I never had any problems with WD drives, but I find that my seagates run cooler(currently about 32C), and much quieter.

---

### Post by Sam on 2006-12-13
Unfortunatly I had problems with 3 Maxtor HD. With two of them there was an hardware failure and I was not able to recover the data...

I don't recommend Maxtor.

---

### Post by lyceum on 2006-12-13
I use Western Digital. They work great for mt.

---

### Post by burek on 2006-12-13
AND ...

Is it better [COLOR="Red"]IDE[/COLOR] or [COLOR="Blue"]SATA[/COLOR] ?

Thx

---

### Post by mmonahan514 on 2006-12-13
I would go with Western Digital, I have seen a lot of Maxtors go on people's computers. I work selling electronics and have seen a lot of maxtor's get returned, never seen a Western Digital get returned.


> **mips said:**
> 1. Seagate
2. Western Digital
For 3.5" drives

I personally find Maxtor to be very unreliable, seen way to many of them replaced in my lifetime.

---

### Post by mcduck on 2006-12-13
I've always placed my trust on Maxtor as not one has failed on me yet. Although people had a lot problems with DiamondMax9, mine is still fine. And I haven't heard anything bad about DiamondMax10.

But the last time I had to buy a HD I tried Samsung Spinpoint as I had heard that they are very silent disks, and indeed even when it's mounted straight to my case with no rubber or anything between I can't hear a sound when it's running. And the performance is almost as good as Maxtor's. I can highly recommend these.

I've never liked Seagates. All I've had were noisy and run very hot.

Haven't tried IBM since my old 80088 PC. Shops where I buy my hardware don't seem to sell those. And I have no experience about Western Digital. They always tend cost a bit more than other options available and I haven't found any reason to pay extra for them.

---

### Post by drphilngood on 2006-12-13
> **mcduck said:**
> ...But the last time I had to buy a HD I tried Samsung Spinpoint as I had heard that they are very silent disks, and indeed even when it's mounted straight to my case with no rubber or anything between I can't hear a sound when it's running. And the performance is almost as good as Maxtor's. I can highly recommend these....

Samsung Spinspoints are great.

edit: I mean the ones with only two large platters like the SP2504C.

---

### Post by BuffaloX on 2006-12-13
My record for the last 1½ year
I have had 5 bad Maxtor drives. ( out of 8 )
I can only recommend to stay a long way away from Maxtor.
Maxtor quality is not what it used to be, before they bought quantum.
I had one bad Seagate. (out of 4)
One bad Samsung ( out of 1 )
One bad IBM/Hitachi ( out of 3 )
Zero Bad Western Digital (Out of 4)

The IBM drive that went bad was pretty old, It jyst turned 3 years, then died.
The Samsung was faulty from day one, probably it was damaged in the post.
The seagate was also more than 3 years old.
The Maxtor drives are a spread from 80 to 200 GB drives, some of them not even a year old, one or two are more than 3 years old.

We have 4 systems running, all with good quality components, and we do not have any bad conditions, like heat, moist, static, bad power, or anything. It seems many drives today simply can't handle normal work load...
Maybe it's the power savings extra spinups, We have no pecial workloads.
The drives simply don't live up to specifications.

Maxtor used to be very reliable, but turned bad after they bought Quantum.
I have kept bying Maxtor, because I thought they would com around, and deliver the good old quality again. But I don't believe that anymore, Worst thing is I should have known better. Next drives I buy will be WD.

IBM used to be very reliable, but the quality took a dive a couple of years ago, Maybe quality is better now with Hitachi?

Seagate quality has always been up and down, impossible to predict.

Samsung I don't have so much experience with Samsung harddrives,

Western Digital has always delivered high quality drives, and they still do. They may cost you a buck or two extra, but as competing drives are now, I wouldn't buy anything else.
I could kick my own behind, for not doing it before.](*,)

---

### Post by mips on 2006-12-13
> **BuffaloX said:**
> My record for the last 1½ year
I have had 5 bad Maxtor drives. ( out of 8 )
I can only recommend to stay a long way away from Maxtor.
Maxtor quality is not what it used to be, before they bought quantum.
I had one bad Seagate. (out of 4)
One bad Samsung ( out of 1 )
One bad IBM/Hitachi ( out of 3 )
Zero Bad Western Digital (Out of 4)

The IBM drive that went bad was pretty old, It jyst turned 3 years, then died.
The Samsung was faulty from day one, probably it was damaged in the post.
The seagate was also more than 3 years old.
The Maxtor drives are a spread from 80 to 200 GB drives, some of them not even a year old, one or two are more than 3 years old.

We have 4 systems running, all with good quality components, and we do not have any bad conditions, like heat, moist, static, bad power, or anything. It seems many drives today simply can't handle normal work load...
Maybe it's the power savings extra spinups, We have no pecial workloads.
The drives simply don't live up to specifications.

Maxtor used to be very reliable, but turned bad after they bought Quantum.
I have kept bying Maxtor, because I thought they would com around, and deliver the good old quality again. But I don't believe that anymore, Worst thing is I should have known better. Next drives I buy will be WD.

IBM used to be very reliable, but the quality took a dive a couple of years ago, Maybe quality is better now with Hitachi?

Seagate quality has always been up and down, impossible to predict.

Samsung I don't have so much experience with Samsung harddrives,

Western Digital has always delivered high quality drives, and they still do. They may cost you a buck or two extra, but as competing drives are now, I wouldn't buy anything else.
I could kick my own behind, for not doing it before.](*,)

When I hear the name Maxtor I cringe, really I do. they were brought out by Seagate recently so lets hope things change for the better.

I spoke to some people at data recovery companies and the bottom line was get Seagate or Western Digital for 3.5" drives, for 2.5" get Hitachi. For some odd reason the seagate 2.5" ones are shite and I've seen it for myself. The 3.5" IBM/Hitachi drives are not that great either.

Ive had very good performance from WD but will also buy Seagate.

---

### Post by Handssolow on 2006-12-15
A Seagate here failed after about 3 weeks. It made a loudish click in the first 2 days and from then on, I was expecting it to fail which it did. Who knows the G- forces it was subjected to in the post.  I suppose it's safer to buy from a shop?

I've a Maxtor in storage. I'd used it for several months without a problem then I decided to enable Smart monitoring in the bios. Guess what a Smart error then comes up! From then at every boot a warning tells me "The hard drives is about to fail, back up your data". Eventually I took it out not so much because I thought it was going to fail but because I couldn't find a way to stop it halting at boot-up.

Agree with others that you need to watch the HD temperatures specially in the summer, failure rates will rise with temperature. I fitted an extra small fan unit.

---

### Post by PatrickMay16 on 2006-12-15
> **tseliot said:**
> All the hard disks I have are maxtor:
2 on my desktop computer
2 on my old desktop
1 on my father's desktop
1 on my Xbox

They all work great with Linux. And they haven't let me down yet.

I second this! I have two Maxtor hard disks, and they have worked great ever since I got them.

---

### Post by Redeyes_Gambit on 2006-12-15
I'm a bit of an armature PC technician and have seen waaayyyyy too many Maxtors fail to ever trust them again. Most recent failure: a Maxtor in my mother's LACIE USB external drive. I popped open the enclosure to take a look and when you moved the drive next to your ear you could hear the heads scraping across the disk surface. Not good. 

I trust Seagate for my HDD needs. I have four ANCIENT 3.2 GB Seagate drives that have been formatted who knows how many times and are STILL running hard and strong.

---

### Post by der_joachim on 2006-12-16
I've seen many Maxtors die. Especially the combination Maxtor/Compaq is a lethal one. Do not buy them. 

When I was going to buy a few SATA disks a few weeks ago, I read some reviews (sorry. Lost the URLs. Probably Tom's Hardware) and the Samsung Spinpoint disks were apparently the best. Its speed was slightly slower than the competition, but they are completely silent (!) and their temperature is very very low. I like them.

---

