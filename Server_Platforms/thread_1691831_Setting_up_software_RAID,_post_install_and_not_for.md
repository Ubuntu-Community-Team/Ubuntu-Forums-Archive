---
title: "Setting up software RAID, post install and not for / or booting"
date: 2011-02-20
forum: Server Platforms
---

### Post by Demented ZA on 2011-02-20
I'm currently planning a new server. My questions are:


[LIST=1]
[*]Is RAID 5 correct for what I want to do?
[*]I found [this]("http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/") guide for setting up my raid post install, however some steps are done in Gnome Parted, but I won't be running a gui. Any advice/or other articles that you could recommend?
[*]What virtual machine platform should I use? I would like USB support, as well as have the guest be able to access the RAID partition. I assume doing it through samba/network would be the best?
[/LIST]


My Planned server setup:

-Intel Quad Core with Virtualization
-4GB Ram
-Two network cards (firewall)
-One 500GB HDD for Ubuntu server (root, boot, swap, /home)
-5 x 2TB Sata6G Seagate HDD's (RAID 5/4/3 for whatever data)
-3 Sunix 2 port Stata6G PCIe RAID controller cards [http://www.sunix.com.tw/product/sata2600.html](http://www.sunix.com.tw/product/sata2600.html)


I will install Ubuntu Server 64 Bit and will be running the machine headless.
The server will be running my firewall/mail server, as well as samba for sharing the data on the Raid partition. I'm also planning on running Windows 7 virtual guest os via virtualbox/vmware/kvm for some light windows programs like an accounting package.

My reasoning behind the above setup:

Cost is an issue, and I'm using some of what I've got plus acquiring some additional hardware. The drives will be purchased seperately from each other ensuring they are from different batches as to reduce the likelyhood of more than one drive failing at once. Also, I will only start with 3 drives, and then later grow the raid partition by another 2 (maybe).

The Sunix RAID cards are probably not true hardware raid, but I will only be  using them to connect the HDD's with SATA6G and have mdadm do software  raid. The Sunix cards are for taking advantage of the Seagate's SATA 6Gbps transfer speeds, nothing more.

I chose software RAID, as it is cheaper, and with the Quad Core CPU I shouldn't lose too much CPU cycles from a machine that will (except for firewall, mail and virtual machine) be otherwise dormant. Another reason for software raid is independence from a physical raid controller, should it fail.

The type of files being stored on the raid partition will vary in size from documents (excel, word, artwok for being published on websites etc to video files up to about 15 GB, I'm guessing). Documents and small files will be worked on directly over network, whereas video files will only be backed up on the server, and occaisionally viewed from the server over network.

Any pointers, advice would be appreciated.

---

### Post by rubylaser on 2011-02-20
Sounds like you've thought this through.  I wouldn't worry about buying PCI-e cards to take advantage of SATAIII speeds.  No current splindle disk on the market can come close to maxing out SATAII let alone III.  Some solid state drives can come close to maxing out SATAII, but you're going for storage, not raw speed (multi drive SSD array).

If your motherboard has 6 SATAII ports, you can use those with no problem with mdadm, and you will see no speed difference between those ports and the 6G ports.  I would suggest also using NFS to share.  You'll see better throughput via NFS or CIFS at least in my experience.

Those are a few pointers to start.  Hope that helps.

---

### Post by Demented ZA on 2011-02-20
Awesome advice, thanks! I have put some thought into it, because as I mentioned, cost is an issue, and i would like to stretch my moola as far as I "technically" can.

On the SATA cards; You are making sense. I guess I woun't use the sata cards then for the raid, but I'm going to get at least one just to play around with, and then when I'm done, use it to add extra ports to my server since the board I'm using has only 5 sata ports. (5xraid+1 standalone = need 6 ports).

As for NFS, I've never used it before, though I've seen it mentioned in passing on the forums and guides about other topics. I'll definately have to do some studying up. How would you suggest I go about implementing this? Would you suggest any reading material, or should I just Google it?

Its for tidbits like this that I post on the formums, cause one can only Google if you know what question to ask, but if you don't know enough to form a question, thats a whole different ballgame.

I'm still wondering about the raid though. I did my homework, but as I'm not an experienced expert with upper levels of raid, I'm open to debate.

Your advice is much appreciated, thx!

---

### Post by koenn on 2011-02-20
re 2- : run 'parted'  in a shell

---

### Post by YesWeCan on 2011-02-20
You haven't mentioned data security. Is this important? Are you intending to regularly back up this array?
I strongly recommend you do not assume that because you are using "RAID" that you have good protection. Do not take this for granted. Get informed.
I consider RAID 5 to be the least reliable of the standard RAIDs and I personally consider it to be a false economy and I would never trust my critical data to it. IMO RAID 6 is significantly more reliable. RAID 10 is best. :)

---

### Post by koenn on 2011-02-20
> **Demented ZA said:**
> 
As for NFS, I've never used it before, though I've seen it mentioned in passing on the forums and guides about other topics. I'll definately have to do some studying up. How would you suggest I go about implementing this? Would you suggest any reading material, or should I just Google it?
Here's how I got started with NFS : 
[http://users.telenet.be/mydotcom/howto/linuxsbs/linuxnetworking.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/linuxnetworking.htm)

---

### Post by koenn on 2011-02-20
> **YesWeCan said:**
> I consider RAID 5 to be the least reliable of the standard RAIDs 
Ha,  opinions. Do you also have a reasoning behind this, and eg explain why RAID5 would be *less reliable* then RAID1 ?

> **YesWeCan said:**
> IMO RAID 6 is significantly more reliable. RAID 10 is best. :)
Last thing i heard, RAID6 also comes with a significant performance penalty on write. 

and RAID10 the best ? define "best"; faster than RAID0 ? better storage efficiency than RAID5 ? more fault tolerant than RAID6 ?

---

### Post by rubylaser on 2011-02-20
I'd say for large storage sets, you can rule out RAID1 not based on reliability, but because you'll just waste a bunch of space.  And, if you're planning on using mdadm, I'd rule out RAID10, because it doesn't support growing an existing RAID10 array (unless, you never plan on adding more disks).

RAID10 is great, because you don't have a massive resync time if a disk fails, but it does require a lot of wasted hard drive space.  In your scenario, I would choose, and have choosen for myself RAID6.  Does it have a write penalty, sure.  But, I can still write to my array at over 200MB/s, so this is more than adequate for my purposes, plus I have the benefit of 2 parity disks.  With 5 2TB disks, your re-sync time is going to be lengthy in the even of a failure, and you'd hate to lose another disk and your array with RAID5 while it rebuilds.

---

### Post by rubylaser on 2011-02-20
In regards to NFS, if you want to mount NFS shares in Windows, you'll need to install Windows Services for Unix on Windows XP, or Client Services for NFS on Windows 7.  The previous guide for NFS is good, and here's the one I used to follow.
[http://www.debianhelp.co.uk/nfs.htm]("http://www.debianhelp.co.uk/nfs.htm")

---

### Post by Demented ZA on 2011-02-20
@YesWeCan, Thank you for your input. I have considered RAID 6 quite  carefully. While RAID 6 has double the parity of RAID 5, it has two  other penalties that come with it:

[LIST]
[*]Reduced performance VS RAID 5 due to additional parity calculations and
[*]20% loss of purchased storage capacity used for parity
[/LIST]

The  pro's (added parity) and the cons (mentioned above) make RAID 5/6  fairly even contenders. In order to decide, I had to consider what I'm  going to be storing on them. 

The estimated storage topography is based on my existing server and looks like this:


[LIST]
[*]~ 100Gb Documents/pictures (Office Files e.g. word, excel, html, jpg, bmp, pdf, cpp, etc)
[*]~ 2 TB Large Files (Video, Clonezilla HDD Clones, CD/DVD ISO's, Downloaded Software
[*]Free Space for growth
[/LIST]
While assesing the data, I made the following observations:


[LIST]
[*]The  relatively small cumulation of office files, is the only real  irreplacable data. Since this is less than 0.2TB, this is easy to backup  regularly off the array as we are currently doing this and I intend to  keep doing this. We have two drives, one is kept off site. The one  on-site goes home at night, and the one at home is brought to office  next mourning. These are kept in sync with rsync and a cron job.
[/LIST]

[LIST]
[*]All  large files are replacable, even the video. We make sure that all video  is backed up to two sets of Verbatim dual layer discs. The one goes to  our customers, and the other is kept as backup. Having them on the RAID  array is more for convenience, archive and reference. Same goes for the  ISO's and software, etc.
[/LIST]

[LIST]
[*]I can afford to take the  system offline while rebuilding a failed drive, since the server is not  mission critical in such a way that business can't continue for a few  hours to a week (As long as it would take replace the drive and rebuild  the data)
[/LIST]

[LIST]
[*]Since I am buying my drives over time from  different vendors, I'm minimising chances of having more than one drive  fail at the same time, since they won't be of the same batch.
[/LIST]

[LIST]
[*]I  have also taken proper measure such as a decent Antec case (Twelve  Hundred) for cooling of the hardware and an Antec 1200 Truepower Power  supply to help regulate power and prevent surges. The Server will also  be connected to its own Line-R 1200 VA line conditioner.
[/LIST]
According  to a study intel published early 2005 and another one in 2009, one can  see that drive failure (At least amongst Seagate, Western Digital and  two other manufacturers) has reduced significantly. In 2005, the study  showed that out of 5 drives, data recovery operations would be neccesary  every 2.3 years. This is an estemated average of the sum of all drive  manufacturers, devided by the number of manufacturers. It therefore  stands to reason that by selecting a reputable brand such as Seagate or  Western Digital, in the year 2011, drive failure is mathematically less  likely.

I also opted to go for 5900 rpm green power drives as  they spin slower and scale speed depending on load. This reduces wear on  mechanical parts and produces less heat, providing even furhter  longevity.

The verdict, RAID 5 wins i would think, no?

@koenn:

> Ha,  opinions. Do you also have a reasoning behind this, and eg explain why RAID5 would be *less reliable* then RAID1 ?

I suppose RAID 5 _can be_ considered _less reliable_  than RAID 1. Both arrays can survive one drive failing, but neither can  survive two simultanous media failures. In the event of RAID 5, the  more drives you have, the higher the likeliehood of failure, and the  more likely you are to have more than one drive fail at a time (about  11% increase of risk per drive, calculated guess based on intel's  figures). With that said, the performance benefits of RAID 5 over RAID 1  more than makes up for the increased risk in speed critical  environments. Also, a well maintained RAID 5 array can help alleviate  the chances of a disaster, by implementing preventative maintenance.  Almost every RAID array has its place, but it depends on what the  demands of the intended implementation will be.

@rubylaser, thanks! I was just going to ask about Windoze since most our desktops run Windows 7.

once again, thank you guys for your input :-)

---

### Post by Demented ZA on 2011-02-20
> **rubylaser said:**
> In regards to NFS, if you want to mount NFS shares in Windows, you'll need to install Windows Services for Unix on Windows XP, or Client Services for NFS on Windows 7.  The previous guide for NFS is good, and here's the one I used to follow.
[http://www.debianhelp.co.uk/nfs.htm](http://www.debianhelp.co.uk/nfs.htm)

Helpfull guide. With this and the one koenn posted, I should be sorted.

Is this what you meant with Windows NFS Client?
[[IMG]http://img41.imageshack.us/img41/5515/32424416.png[/IMG]]("http://img41.imageshack.us/i/32424416.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by YesWeCan on 2011-02-20
> **koenn said:**
> Ha,  opinions. Do you also have a reasoning behind this, and eg explain why RAID5 would be *less reliable* then RAID1 ?
Well, you'll find lots of opinions in a public web forum. To successfully recover a RAID 1 you have to successfully read one drive. To successfully recover a RAID 5 you must successfully read more than one drive. Unless your RAID 5 has only 2 drives, but then it would have the same capacity and be more complex. RAID 5 rapidly becomes less reliable the more disks you add and it has more complex failure modes.

> Last thing i heard, RAID6 also comes with a significant performance penalty on write.
Yes. I am not commenting on speed.

> and RAID10 the best ? define "best"; faster than RAID0 ? better storage efficiency than RAID5 ? more fault tolerant than RAID6 ?
I am specifically opining about data security.

---

### Post by rubylaser on 2011-02-20
I'm a little fuzzy, on your intentions, you mentioned wanting to avoid a write penalty, then you pick Green drives? (Among the slowest available).  You'll want to avoid those drives like the plague, if you intend to use mdadm.  They will constantly be timing out, and causing your array to re-sync.  This will shorten their lifespan, by causing them to work hard during the constant rebuilds.  Just do a search on this forum for green drives mdadm if you don't believe me.

I'm glad to hear you've mapped out your data use, and have a backup policy in order.  To me the small $ cost of an additional drive to build a RAID6 array far outweighs the negative aspects of losing 1 spindle.  But, that's my opinion, and you need to choose what's right for your scenario.

Yes, that's exactly what I'm talking about for NFS :)

---

### Post by YesWeCan on 2011-02-20
> **Demented ZA said:**
> @YesWeCan, Thank you for your input.My only intention is to urge you to think it through. It seems you have so that's great. :)

> According  to a study intel published early 2005 and another one in 2009
I would like to read those. Have you got a reference?

> The verdict, RAID 5 wins i would think, no?
It entirely depends on your specific trade-offs. Me, given a choice of R5 or R6, I would always buy the extra drive.

> I suppose RAID 5 _can be_ considered _less reliable_  than RAID 1. Both arrays can survive one drive failing, but neither can  survive two simultanous media failures.
Strictly speaking, and this matters, R5 can survive only 1 and R1 can survive between 1 and half your disks.
> In the event of RAID 5, the  more drives you have, the higher the likeliehood of failure, and the  more likely you are to have more than one drive fail at a time (about  11% increase of risk per drive, calculated guess based on intel's  figures).
The key is what assumption you make about the odds of any one disk failing during the resync and what your goal is, if any, for the probability of recovering your array from a disk failure.
> With that said, the performance benefits of RAID 5 over RAID 1  more than makes up for the increased risk in speed critical  environments.
Not compared to RAID 1+0.
> Also, a well maintained RAID 5 array can help alleviate  the chances of a disaster, by implementing preventative maintenance.
So can any RAID.

---

### Post by Demented ZA on 2011-02-20
> **YesWeCan said:**
> My only intention is to urge you to think it through. It seems you have so that's great. :)

[COLOR=Blue]I still value the input, as you are mentioning very valid points.[/COLOR]

I would like to read those. Have you got a reference?

[COLOR=Blue]I'm looking it up again now.[/COLOR]

It entirely depends on your specific trade-offs. Me, given a choice of R5 or R6, I would always buy the extra drive.

[COLOR=Blue]Interesting point.[/COLOR]

Strictly speaking, and this matters, R5 can survive only 1 and R1 can survive between 1 and half your disks.

[COLOR=Blue]Well stated.[/COLOR]

The key is what assumption you make about the odds of any one disk failing during the resync and what your goal is, if any, for the probability of recovering your array from a disk failure.

[COLOR=Blue]I think i'm too tired to understand that sentence fully. (3 AM, lol).[/COLOR]

Not compared to RAID 1+0.

[COLOR=Blue]I didn't compare it to RAID 1+0 (or RAID 10), but I agree.[/COLOR]

So can any RAID.




:-kHmm. You raise an interesting point. Between what you and rubylaser said, and I quote:

> then you pick Green drives? (Among the slowest available).  You'll want  to avoid those drives like the plague, if you intend to use mdadm.  They  will constantly be timing out, and causing your array to re-sync.  This  will shorten their lifespan, by causing them to work hard during the  constant rebuilds.

I'm suddenly reconsidering. I did not know this about the green drives. I read [this]("http://www.overclockersclub.com/reviews/barracuda_green_2tb/12.htm") and [this]("http://hothardware.com/Reviews/Seagate-Barracuda-Green-2TB-Hard-Drive-Review/?page=9") article which showed some promise. But I couldn't find much on using them in raid setups.

This is very good to know.
According to the [RAID Wiki]("http://en.wikipedia.org/wiki/RAID"), RAID 6 needs a minimum of 4 drives. But if one fails, it becomes a temporary RAID 5-like array untill that drive is replaced. Or at least thats how it is described in laymans terms on a previous post I read. Can RAID 6 be set up with 3 drives to add the 4th later?

What exactly are the performance costs assosciated with RAID 6 vs RAID 5 in your experience?

---

### Post by YesWeCan on 2011-02-20
Yes, mdadm allows you to set up a RAID6 with one drive missing, indefinitely. That's a good idea.

My characteristically confusing sentence boils down to:
What minimum odds do you want that you will recover your array if a drive fails?
Then go from there.
Some folks gloss over this and just assume their odds will be so close to 100% as makes no..erm...odds. But if one does the maths and tries to consider all the ways things can fail and their correlation, they might be surprised.

---

### Post by SeijiSensei on 2011-02-20
> **YesWeCan said:**
> Me, given a choice of R5 or R6, I would always buy the extra drive.

Drives are cheap; data are priceless.

I've had the misfortune of losing two of the three drives in a RAID5 without proper backups.  It's not an experience I'd like to relive.

---

### Post by Demented ZA on 2011-02-21
This is gonna screw up my budget though. Seagate doesn't seem to make any standard 7200rpm 2Tb drives. [Look at this list.]("http://www.seagate.com/www/en-us/products/internal-storage/") My only hope is western digital. Look at the [first drive on this list]("http://www.wdc.com/en/products/products.aspx?id=100"). Unfortunately this WD drive is selling for almost double of the drives I went for initially. (But it would be cheaper than buying the wrong drives to start off with.)

---

### Post by YesWeCan on 2011-02-21
> **rubylaser said:**
> I'm a little fuzzy, on your intentions, you mentioned wanting to avoid a write penalty, then you pick Green drives? (Among the slowest available).  You'll want to avoid those drives like the plague, if you intend to use mdadm.  They will constantly be timing out, and causing your array to re-sync.  This will shorten their lifespan, by causing them to work hard during the constant rebuilds.  Just do a search on this forum for green drives mdadm if you don't believe me.
Is this because of NCQ? [http://en.wikipedia.org/wiki/Native_Command_Queuing](http://en.wikipedia.org/wiki/Native_Command_Queuing)
I thought I read somewhere that it can be disabled.

---

### Post by rubylaser on 2011-02-21
No, it's a design "feature" of the green drives to go into a low power state. As result, they aren't available to the array, and mdadm drops them.  They'll constantly cause the array to re-sync.  Here's a perfect example from another thread I'm posting in.
[http://ubuntuforums.org/showthread.php?t=1681924]("http://ubuntuforums.org/showthread.php?t=1681924")

And, yes, NCQ can easily be disabled like this...
```
echo 1 > /sys/block/sda/device/queue_depth
```
But, that won't help the drives from falling out of the array.

 Another drive you could consider is the Hitachi 2TB drive.  They're not Advanced Format, and are designed to run 24x7.
[http://eshop.macsales.com/item/Hitachi/0S02861/]("http://eshop.macsales.com/item/Hitachi/0S02861/")
And, Newegg has the non-retail version of this drive for $119.00, but it sounds like from the reviews that their shipping of these drives has caused some failures for people, so I'd probably spend the extra $8/ drive for the retail packaged version.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145298&cm_re=hitachi_7k2000-_-22-145-298-_-Product]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145298&cm_re=hitachi_7k2000-_-22-145-298-_-Product")

I assume you where looking at these drives [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148681&Tpk=seagate%202tb%20green]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148681&Tpk=seagate%202tb%20green")
So, there's not a massive difference in price.

---

### Post by YesWeCan on 2011-02-21
I read that
```
hdparm -B 255
```
disables Advanced Power Management features of a hard disk. Perhaps this applies to these green drives?
[http://linux.die.net/man/8/hdparm](http://linux.die.net/man/8/hdparm)

---

### Post by rubylaser on 2011-02-21
I've had people try that in the past too.  It doesn't seem to help.  I've just recommended to avoid the green edition drives with mdadm, to ensure a happy user experience.

---

### Post by YesWeCan on 2011-02-21
The world is moving inexorably towards avoiding power waste. I find it hard to believe this power saving mode feature cannot be disabled. Perhaps the linux drivers need to catch up.

---

### Post by rubylaser on 2011-02-21
Sure, it is, but if you're wanting to save power, why are you running a multi disk RAID array that's always on?  If you want to save power, I'd suggest a technology that allows the disks to actually spin down when not in use, like Unraid. Green edition drives like this [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136514]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136514") will also work fine in Unraid.
[http://www.lime-technology.com/wiki/index.php?title=Hardware_Compatibility]("http://www.lime-technology.com/wiki/index.php?title=Hardware_Compatibility")

And the linux driver doesn't need to catch up. This behavior isn't isolated to mdadm, many hardware controllers have problems with these drives.  They experience the same problems of failing out of arrays.  That's why all hard drive companies make enterprise drives for RAID arrays.

---

### Post by psusi on 2011-02-21
> **rubylaser said:**
> I'm a little fuzzy, on your intentions, you mentioned wanting to avoid a write penalty, then you pick Green drives? (Among the slowest available).  You'll want to avoid those drives like the plague, if you intend to use mdadm.  They will constantly be timing out, and causing your array to re-sync.  This will shorten their lifespan, by causing them to work hard during the constant rebuilds.  Just do a search on this forum for green drives mdadm if you don't believe me.

This is absolutely untrue.  mdadm does not know or care if drives go to sleep; the disk driver wakes them back up when they are accessed.  Plenty of people put their drives to sleep in a raid array.  Also the green drives do not go to sleep by default; they just lower their rpm and unload the head when idle.  Some hardware raid cards get pissy and will drop the drive if it does not respond quickly, which often happens with these drives when they slow down and unload the head, but mdadm does not suffer from this defect.

---

### Post by YesWeCan on 2011-02-21
@rubylaser
So are you saying mdadm is just for 24/7 pro users?

These days, RAID is not just for corporate data centres. Thanks to linux, the ordinary man in the street (ie: me) can enjoy its features too. I take power saving seriously and I think the advent of green hardware is, in principle, very good. So why shouldn't ordinary users be able to make a RAID array of eco disks?

Ubuntu RAID (which seems to be mdadm by default) should accommodate power saving modes gracefully. If you don't want power saving then linux RAID should allow you to disable it in the drives.

If it doesn't then it needs to catch up.

---

### Post by YesWeCan on 2011-02-21
> **psusi said:**
> This is absolutely untrue.  mdadm does not know or care if drives go to sleep; the disk driver wakes them back up when they are accessed.  Plenty of people put their drives to sleep in a raid array.  Also the green drives do not go to sleep by default; they just lower their rpm and unload the head when idle.  Some hardware raid cards get pissy and will drop the drive if it does not respond quickly, which often happens with these drives when they slow down and unload the head, but mdadm does not suffer from this defect.
Sounds good. :)
So what are all these problems folks are talking about with green drives and mdadm?

---

### Post by rubylaser on 2011-02-21
Wow, those are two rather heated responses.
> So are you saying mdadm is just for 24/7 pro users?
Absolutely not, I've used at home for years on commodity hardware, and it's never let me down.  It's obviously drastically cheaper than a hardware solution, and I love the ease with which I can put an array in a different system.

Psusi if you can tell me how to "properly" spindown an mdadm disk, I'd love to hear how.  I've tried to do this many times, and the disks either never spin down, or don't re-initialize properly.  Normally, the smart daemon was the cause as it would check on the disks periodically and wake them back up as result.  I've tried posts like this, but still have similar results as stated above. [http://www.interphero.com/?p=90]("http://www.interphero.com/?p=90")

Also, there are tons of people on this forum and Google that could use your insight to get these Green drives working properly with mdadm as well.  If you have a cure for this very common problem, I'm sure tons of people (myself included) would love to run these green drives in RAID arrays.

---

### Post by YesWeCan on 2011-02-21
> **rubylaser said:**
> Wow, those are two rather heated responses.
Sorry about that! I didn't mean to scorch you. O:)
I am such a hypocrite: I should know better than to generate unecessary heat! :P

---

### Post by YesWeCan on 2011-02-21
@ psusi and rubylaser
While we are both here, I have been exploring write intent bitmaps. I came across this article: [http://blog.liw.fi/posts/write-intent-bitmaps/](http://blog.liw.fi/posts/write-intent-bitmaps/)
Do you think its performance impact estimates are realistic?

---

### Post by rubylaser on 2011-02-21
No big deal:)  I'm fine with being wrong if that's the case, I've been trying to share info from my own experience for the OP.  I'd love to be able to use green disks or at a minimum get my 8 disk array to spindown.  That'd save a fair amount of energy if I could get it working properly.

---

### Post by rubylaser on 2011-02-21
Here's what I mean.  I have all of these drives all set to spindown at the same time, and only half of them actually do.
```
root@fileserver:/storage# hdparm -C /dev/sdb
/dev/sdb:
 drive state is:  active/idle

root@fileserver:/storage# hdparm -C /dev/sdc
/dev/sdc:
 drive state is:  active/idle

root@fileserver:/storage# hdparm -C /dev/sdd
/dev/sdd:
 drive state is:  active/idle

root@fileserver:/storage# hdparm -C /dev/sde
/dev/sde:
 drive state is:  active/idle

root@fileserver:/storage# hdparm -C /dev/sdf
/dev/sdf:
 drive state is:  standby

root@fileserver:/storage# hdparm -C /dev/sdg
/dev/sdg:
 drive state is:  standby

root@fileserver:/storage# hdparm -C /dev/sdh
/dev/sdh:
 drive state is:  standby

root@fileserver:/storage# hdparm -C /dev/sdi
/dev/sdi:
 drive state is:  standby

```

---

### Post by psusi on 2011-02-21
With, or without raid, you need to get the system to stop touching the disk for it to spin down.  The laptop-mode-tools package contains scripts to help with this.

The linux-raid mailing list frequently has people talking about both of these subjects.  You might also notice that WD states that the green drives are ONLY suitable for use in software or motherboard fakeraids ( because of the buggy hardware raid drop out ).

I only have one green drive at home, but have an old pair of 36 gb first gen WD raptors in a raid0 that I almost never spin up these days.  I don't even mount them usually since I got the SSD.

---

### Post by Demented ZA on 2011-02-21
I'm also quite keen on getting green power working as I think it a noble cause, but right now I can't afford to purchase anything thats gonna give me greif. I'm very curious to know more about the green drives and gettin them working on raid without issues and still saving power. i think a lot of valid points were mentioned, and experience has taught me that especially in the opensource community, a solution will be found as Linux has almost always been quick to adapt.

As for the drives, I took the plunge and am getting [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136792") drives. Yes they are twice the price, but its all that is available to me in my country at my suppliers and what they have stock of.

---

### Post by YesWeCan on 2011-02-21
> **Demented ZA said:**
> As for the drives, I took the plunge and am getting [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136792") drives. Yes they are twice the price, but its all that is available to me in my country at my suppliers and what they have stock of.
Good choice! (he says, being the carbon-squandering but proud owner of 4 Caviar Blacks).

---

### Post by rubylaser on 2011-02-21
Thanks, I'll check out the laptop-mode-tools package.  This is from the linux-raid archives. I guess some discs spinning down are better than none, but I'll continue to strive toward getting all of the inactive disks to spindown.

I have 3 of the 1TB versions of those WD disks in my array, so I hope they work well for you.

---

### Post by Demented ZA on 2011-02-21
> **rubylaser said:**
>  I guess some discs spinning down are better than none, but I'll continue to strive toward getting all of the inactive disks to spindown.

I have 3 of the 1TB versions of those WD disks in my array, so I hope they work well for you.

Are these the ones you are having problems with spinning down?

I hope they work for me. How are they working for you? How would you rate them?

I'm hopefully getting them tomorow. Can't wait!

Oh, And I'm only getting three, building a RAID 6 array with a missing disk till my supplier gets more stock.

---

### Post by rubylaser on 2011-02-21
No, actually all three of them are disks /dev/sd[ghi] in my previous post, so they spindown just fine.  It's hard to rate them individually, as I have them as part of an 8 disk RAID6 array, with some older WD WD1001FALS drives and Seagate ST31000340AS drives.  But here are some hdparm numbers for the three types of drives, so you can compare...
```

[COLOR="Red"]1TB Western Digital WD1002FAEX[/COLOR]
root@fileserver:~# hdparm -tT /dev/sdg
/dev/sdg:
 Timing cached reads:   1106 MB in  2.00 seconds = 552.73 MB/sec
 Timing buffered disk reads:  382 MB in  3.01 seconds = 126.77 MB/sec

[COLOR="red"]1TB Seagate ST31000340AS[/COLOR]
root@fileserver:~# hdparm -tT /dev/sdb
/dev/sdb:
 Timing cached reads:   1082 MB in  2.00 seconds = 540.80 MB/sec
 Timing buffered disk reads:  300 MB in  3.02 seconds =  99.48 MB/sec

[COLOR="red"]1TB Western Digital Black WD1001FALS-0 (older model)[/COLOR]
root@fileserver:~# hdparm -tT /dev/sdd
/dev/sdd:
 Timing cached reads:   1098 MB in  2.00 seconds = 548.44 MB/sec
 Timing buffered disk reads:  322 MB in  3.02 seconds = 106.75 MB/sec
```

As you can see, it's the fastest of my 3 drive types by a rather significant margin.

---

### Post by SeijiSensei on 2011-02-21
> **YesWeCan said:**
> Thanks to linux, the ordinary man in the street (ie: me) can enjoy its features too.

I suspect the "ordinary man in the street" is not running Linux. If he even cares about RAID, he might do what I did and buy an external device with multiple drives and RAID capability.

I've set up my share of RAIO devices in Linux, but I also enjoy being able to plug my Maxtor drive with RAID1 into a machine without further ado.

---

### Post by ashikaga on 2011-02-21
> **rubylaser said:**
> If you have a cure for this very common problem, I'm sure tons of people (myself included) would love to run these green drives in RAID arrays.
Likewise, I'm all ears! :)

---

### Post by psusi on 2011-02-22
Yep, the ordinary man is running Windows which has little to no software raid support, hence the rise of fakeraid.

---

### Post by Demented ZA on 2011-03-13
just an update, I've gotten 3 Separate Western Digital Caviar Sata 3 (6GB/s) drives. Not the green drives, 7200RPM drives.

I also Got an intel Sandybridge Core i5 2500K CPU. I'm just waiting on my motherboard, [Asus P8P67-M]("http://www.asus.com/product.aspx?P_ID=hcyfdEpZcMvFkTNm"), ETA end of the month.

I decided to go for the Core i5 2500k because its blazing fast and a very decent overclocker. However this is not my main reason, I want it for its integrated GPU. I know on a discrete board, the GPU is not utilized, but it seems like it holds some interesting prospects for running a virtual machine that can take advantage of the GPU :popcorn:
When I get my hardware, I'll build my system and report back here.

---

### Post by psusi on 2011-03-13
> **Demented ZA said:**
> just an update, I've gotten 3 Separate Western Digital Caviar Sata 3 (6GB/s) drives. Not the green drives, 7200RPM drives.

You mean the blue or the black?  The green also runs at 7200 rpm, it just slows down to 5400 when idle.

> **Demented ZA said:**
> I also Got an intel Sandybridge Core i5 2500K CPU. I'm just waiting on my motherboard, [Asus P8P67-M]("http://www.asus.com/product.aspx?P_ID=hcyfdEpZcMvFkTNm"), ETA end of the month.

Got the same setup last month.  Been pretty happy with it overall, but I still have not managed to get Asus to accept my but report that their bios screws up the ACPI P-state table whenever you overclock.  At the stock B-CLK of 100.0 MHz, you get a cpu frequency table from 1600 to 3200 MHz.  Whether you go to 100.1 MHz or 107 MHz, it does not matter; instead of computing the correct frequencies, it just passes a table that still starts at 1600 MHz and goes up to 5800 MHz.

---

### Post by rubylaser on 2011-03-13
Sounds like a great setup.  After seeing the low power draw at idle, I've been thinking seriously about upgrading the hardware in my fileserver at home, and going with a Sandy Bridge processor.   How does your speed compare to what is replaced, and what is your use case?

---

### Post by disabledaccount on 2011-03-13
> **psusi said:**
> You mean the blue or the black?  The green also runs at 7200 rpm, it just slows down to 5400 when idle.Nope, green series spins at constant speed just a bit above 5400rpm. That's WD fault (or intentional allusion) which makes peoples think that green has variable speed. You can google for results of speed measurements. It's also very easy to confirm by measuring and comparing average access time.

---

### Post by Demented ZA on 2011-03-13
Its the WD Caviar Black. I'll be getting more, I just want to spread them out so as to avoid them being part of the same or related batch to lessen chances of simultaneous failure.

I'm quite amped. At the moment I'm running Ubuntu Server on a Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz, 2 cores with 1 Gb Ram. Its not running RAID or any virtual Machines, so its doing what it has to pretty fast. Its set up to be a firewall with ADSL Line bonding (load balancing), mail server, and a basic web server.

Well pretty soon I'll be in the same boat as you with regards to over clocking. 

I'm building it into an Antec 1200 case, with an Antec 1200 80-Plus power supply. The case has space for 12 Hard Drives. 13 If I add an SSD, that can mount in front of the PSU's 120mm fan. So Lots of cooling in that case.
I modified the side panel, cut it out neatly and lined it with grommet edging. Got a nice sheet of plexiglass covering now. Much clearer and scratch resistant. It now allows me to see clearly and unhindered into the machine.

The case is getting mounted against the wall above my workstation. All I have to do is decide on a colour scheme. I already replaced all the fans, including the top 200mm case fan with red led fans. Just want to bring some UV's in, some sleeving and a nice CPU cooler :guitar:

---

### Post by Demented ZA on 2011-03-13
If that is the case, then given what has been discussed in this thread, it might explain a lot...

> **tomazzi said:**
> Nope, green series spins at constant speed just a bit above 5400rpm. That's WD fault (or intentional allusion) which makes peoples think that green has variable speed. You can google for results of speed measurements. It's also very easy to confirm by measuring and comparing average access time.

---

### Post by disabledaccount on 2011-03-13
> **Demented ZA said:**
> Well pretty soon I'll be in the same boat as you with regards to over clocking. I like overklocking - I've overclocked every PC in my home, and I mean OVERCLOCKED - with serious MB modifications in power sections. But server overclocking is suicide, unless You don't care about stability. There is no software that can test and ensure stability after OC. Besides too heavily overclocked PC can be slower due to cache errors and thermal throttling - and it's very hard to estimate OC limit, cause it depends on application - especially due to different load of SIMD and FPU hardware in real situations.

---

### Post by rubylaser on 2011-03-13
Are you planning on running some virtual machines or encoding videos on this new box?  Virtual Machines would be the main benefit for me to upgrade.  I have an AMD 240e dual core processor, and it's a little long in the tooth for running multiple virtual machines.

Which model number of Blacks did you purchase?

---

### Post by Demented ZA on 2011-03-13
I understand the aspects involved with overclocking and reliability. I'm not building this system with the aim of overclocking though. The aim is to build a server system with the ability to run RAID and Virtual machines. I'm going for the 2500k for its speed, low power and the prospect of being able to use the built in GPU. I decided to go for the 'k' processor (unlocked multiplier) as I think having the ability to over clock is good to have if I ever get into a situation where I need some more juice.

As for stability, this will be my own server. I'm using it for my own company, but if it were to fail, it won't be catastrophic for me. The server is extremely nice to have, but I don't *NEED* it. I told myself I'll play around with it, and then when I'm done and I've set it up, I'll disconnect my good old faithful albeit 64bit machine, and connect this one in its stead.

@rubylaser, yes, I wanna run virtual machines. \\:D/ I want to try and see if I can run a virtual machine, to make use of the dedicated GPU embedded in the chip to do Graphics Virtualization. The reason: just for the sake of it :p. I suppose if I get it working, I'll use it to rip video etc because I can. I mainly want to be able to remote desktop into a windows 7 Virtual machine and have it running speedy for browsing for downloads/torrents and the like. It might sound overkill, but its for a use-case study. Also, I'm used to having a computer I can remote desktop into, browse and start a torrent/ download, and disconnect, and having the download independent from my or any other machine. Also, downloads are sent to a single area, and all my data is kept centralized on the network, as well as accessible from anywhere.

---

### Post by Demented ZA on 2011-03-13
Oh, sorry, drive model is [WD2002FAEX]("http://www.wdc.com/en/products/products.aspx?id=100")

---

### Post by disabledaccount on 2011-03-13
Demented ZA: that's ok - You have been warned ;) I just know that many users are reporting bugs from unstable hw. After all, You don't have to report anything, but keep it in mind.

---

### Post by Vegan on 2011-03-13
WD on a software RAID, that is scary. Especially given all the dead WD disks I have.

I loath software RAID. Its begging for trouble.

---

### Post by Demented ZA on 2011-03-13
Deleted. Double post.

---

### Post by Demented ZA on 2011-03-13
> **tomazzi said:**
> Demented ZA: that's ok - You have been warned ;) I just know that many users are reporting bugs from unstable hw. After all, You don't have to report anything, but keep it in mind.

To re-iterate, I have overclocked before, and I understand the impact it can have on stability. I do not intend to run the server overclocked. I just want the option, should I do something crazy that needs more speed/power, and I don' feel it justified to spend the money to upgrade. So I probably never will overclock this system, except for maybe when I get it and its not doing anything important yet.

And even if I do overclock; as always, I believe in a stable overclock. My definition of overclocking is not pushing the limits. I'm fairly conservative when I overclock, and I follow the rules: small increments, tested over time. I'm sure that a stable overclock can be achieved with this system and the right memory, timings, voltage adjustments, multiplier adjustments, stable current and decent cooling.

I appreciate your heads up though :)

---

### Post by rubylaser on 2011-03-13
```
WD on a software RAID, that is scary. Especially given all the dead WD disks I have.
```

I don't know what sorts of trouble you've had with software RAID in the past, but I've used it for years in many different applications on various platforms without a problem.  I've also used it with Western Digital disks with no problem.  Did you monitor the SMART status on your drives and RMA the defective one's?  I can't imagine having a stack of disks laying around that are dead.  Either the environment is too hot, or the case isn't dampening vibrations and killing the drives.

Demented ZA, I have ( 3 ) of the 1TB versions of these drives in my home RAID6 array, they've worked great for me. I hope you enjoy your new setup, it sounds very nice :)

---

### Post by psusi on 2011-03-13
> **rubylaser said:**
> Sounds like a great setup.  After seeing the low power draw at idle, I've been thinking seriously about upgrading the hardware in my fileserver at home, and going with a Sandy Bridge processor.   How does your speed compare to what is replaced, and what is your use case?

My system is currently drawing 128 watts with all 3 rotational disks ( 1 1.5 tb green and a pair of first generation 36 gb raptors ) on standby.  Also have a 64 gb ssd, and a radeon hd 3850 in there.  Monitor is not part of that load.

> **tomazzi said:**
> Nope, green series spins at constant speed just a bit above 5400rpm. That's WD fault (or intentional allusion) which makes peoples think that green has variable speed. You can google for results of speed measurements. It's also very easy to confirm by measuring and comparing average access time.

Since the manufacturer states that it is variable speed, I'm inclined to believe them.  If there is an experiment that says otherwise, please cite it.  I would be interested in analyzing it and trying to reproduce the results.

---

### Post by disabledaccount on 2011-03-14
> **psusi said:**
> Since the manufacturer states that it is variable speed, I'm inclined to believe them.  If there is an experiment that says otherwise, please cite it.  I would be interested in analyzing it and trying to reproduce the results.This is comon misunderstanding - WD have never said that Green has variable speed - they say that intelli power is fine-tuned for each particular model, so spindle speed may vary across models.
One of thousants of reviews:
[http://www.legitreviews.com/article/1077/4/](http://www.legitreviews.com/article/1077/4/)
- look at access times.
There were accurate measurements based on noise and vibration frequency spectrum, but I can't find it now.

---

### Post by rubylaser on 2011-03-14
Thanks for the update psusi.  For a brief second, my eyes popped out when I read your system was drawing 128 watts with your disks in standby.  Then I saw that you had an ATI 3850 GPU in there.  I've read those can draw up to 100 watts by themselves at idle.  So, taking that portion out, because I won't need a discrete GPU for my application, this looks like a very lower power consumption solution.

---

### Post by psusi on 2011-03-14
> **tomazzi said:**
> This is comon misunderstanding - WD have never said that Green has variable speed - they say that intelli power is fine-tuned for each particular model, so spindle speed may vary across models.
One of thousants of reviews:
[http://www.legitreviews.com/article/1077/4/](http://www.legitreviews.com/article/1077/4/)
- look at access times.
There were accurate measurements based on noise and vibration frequency spectrum, but I can't find it now.

I could have sworn that I had read a spec on wdc's web site that specifically said it was variable from 5400-7200, but now I can't seem to find it.  At any rate, there's nothing in that article that indicates it is only 5400 rpm.  To measure that you need to do a same sector read and measure the latency.  For 5400 rpm it should be around 11.1 ms, and for 7200 rpm should be around 8.3 ms.  I'll have to try and test mine tonight and see what difference tuning the performance settings makes.


> **rubylaser said:**
> Thanks for the update psusi.  For a brief second, my eyes popped out when I read your system was drawing 128 watts with your disks in standby.  Then I saw that you had an ATI 3850 GPU in there.  I've read those can draw up to 100 watts by themselves at idle.  So, taking that portion out, because I won't need a discrete GPU for my application, this looks like a very lower power consumption solution.

Yes, it does draw a lot of juice.  The 2.6.38 kernel can read the temperature of the thing and it's been idling at 60-80 C.

Oh, and for comparison, my old Athon 64 5000+ Black edition system with the same hardware ( other than mobo, cpu, ram of course ) drew 220 watts idle.

---

### Post by Demented ZA on 2011-03-14
I want a kill-o-watt tto, so I can measure my power consumption. 

I agree with rubylazer, if I had a lot of a certain type of hardware failing constantly, I'd start suspecting problems elsewhere, like power supply or heat/cooling/ventilation.

@rubylaser, I know, you mentioned your drives previously in this thread. Thats why I decided to go with the WD Caviar Black in the first place, lol. That, and they were good value for money considering price/Mb, speed, reliability (reviews).

I've always been a Seagate fan, but I've never had anything against WD. As for hard drives in general, I believe they should be kept cool, properly mounted in a sturdy case, with rubber dampeners if they'll fit, and a decent power supply. A line conditioner also helps to even out power and prevent over voltage and mild surges from mains.

I have a rule: never buy a used HDD. Or even rely on a used HDD. You never know where its been or what its been through. Data is far too priceless, and so is my time.

Also, unfortunately overclocking can cause damage, as SATA is probably most sensitive to overclocking. Although there are steps one can take depending on your motherboard and SATA controller.

I've owned and worked with plenty (countless) drives in my life, and I haven't had nearly as many failures as my buddies.

---

### Post by psusi on 2011-03-14
> **Demented ZA said:**
> 
A line conditioner also helps to even out power and prevent over voltage and mild surges from mains.

Your PSU properly regulates the voltage to the drive.  So called line conditioners are also widely known to be useless junk appliance stores bilk clueless consumers with; they do nothing.  A UPS on the other hand, is always a handy thing to have.

> **Demented ZA said:**
> Also, unfortunately overclocking can cause damage, as SATA is probably most sensitive to overclocking. Although there are steps one can take depending on your motherboard and SATA controller.

It is theoretically possible for overclocking to damage the sata controller, but I have never heard of that happening.  It is not possible for it to damage the drive, at least not directly.  I suppose if you overclock and that causes the temperature inside the case to up up 15 degrees then that isn't so great for the drive.

---

### Post by Demented ZA on 2011-03-14
> **psusi said:**
> Your PSU properly regulates the voltage to the drive.  So called line conditioners are also widely known to be useless junk appliance stores bilk clueless consumers with; they do nothing.  A UPS on the other hand, is always a handy thing to have.

Actually, line conditioners in conjunction with a decent power supply can help a lot. Although a line conditioner does some of what the power supply does, it doesn't hurt to attain the most stable power flow possible. It buffers current to oversized capacitors, and then releases it steadily. Most fluctuations are evened out by this process. In doing this, it helps protect the PSU, and prolongs its life because the schelec doesn't get burned off the copper wire that's wrapped around the transformer of the power supply, and thus slows down reduction of efficiency.

A ups is rather the useless bit of hardware. Unless its a line interactive ups, it does not perform conditioning. It sits passively in parallel to your PC, and charges. Only when the power fails, does the ups kick in. In this split second, between loss of power, and the ups kicking in, you have a slight dip in power going to the pc.

Similarly, when the power comes back on, the pc is not protected from that initial surge, except for a fuse in the UPS, and even then, these fuses are not wussy fuses, as they often have to carry a load from three or four devices. So they allow that bad jolt to go through, without blowing, as its maybe just under the tolerance of the fuse. 

In my country, UPS's are sold like mad whenever there are brownouts, not because people want half an hour to save their word or excel documents before lighting a candle and hunting for a torch, but rather because they want to protect their hardware from failing.

So many so called "IT techs" have sold ups's under the premise that it will "protect your pc from surges", only to have the customer ask "but why did it fail?? I have a UPS connected to it???"

Fluctuating and surging current is what wreaks havoc with a PC. This is what line conditioners try to prevent.

Passive ups's, only protect your work, and allows you to shut down cleanly after saving.

Line interactive/active UPS's perform the best of both worlds; they regulate power, they give you some battery to cleanly shut down, however, they are usually (much) more expensive.

---

### Post by psusi on 2011-03-14
> **Demented ZA said:**
> Actually, line conditioners in conjunction with a decent power supply can help a lot. Although a line conditioner does some of what the power supply does, it doesn't hurt to attain a stable power flow. It buffers current to oversized capacitors, and then releases it steadily. Most fluctuations are evened out by this process.

The capacitors are not large enough to buffer any significant amount of energy; they are just there to smooth out high frequency noise on the line, which the PSU has its own ( larger ) caps and inductors for.  About the only thing that cares about high frequency noise is cheap stero equipment with terrible power supplies in the 70s and early 80s.

> **Demented ZA said:**
> A ups is rather the useless bit of hardware. Unless its a line interactive ups, it does not perform conditioning. It sits passively in parallel to your PC, and charges. Only when the power fails, does the ups kick in. In this split second, between loss of power, and the ups kicking in, you have a slight dip in power going to the pc.

Not having your computer shut down and loose your work every time there is a power glitch is the *opposite* of useless.  The split second gap to switch to battery does not bother your PSU one bit; it has enough capacitance to ride right through it.

> **Demented ZA said:**
> Similarly, when the power comes back on, the pc is not protected from that initial surge, except for a fuse in the UPS, and even then, these fuses are not wussy fuses, as they often have to carry a load from three or four devices.

No, when the power comes back on it is not routed to the PC until the UPS decides it's good.  Just the same, the PSU in your PC ( and any UL listed device ) is designed to handle that just fine, which is why you don't see them blowing out all the time.

> **Demented ZA said:**
> So many so called "IT techs" have sold ups's under the premise that it will "protect your pc from surges", only to have the customer ask "why did it fail if I have a UPS connected to it???"

Got a source for this?  Most UPSes come with a warranty to replace any connected equipment that it fails to protect, and they wouldn't do that if such failures were common.

> **Demented ZA said:**
> Fluctuating and surging current is what wreaks havoc with a PC. This is what line conditioners try to prevent.

As does a UPS.  When the voltage gets too high, they either switch to battery or adjust their auto transformer to step the voltage back down.

---

### Post by Demented ZA on 2011-03-14
> **psusi said:**
> the capacitors are not large enough to buffer any significant amount of energy; they are just there to smooth out high frequency noise on the line, which the psu has its own ( larger ) caps and inductors for.  About the only thing that cares about high frequency noise is cheap stero equipment with terrible power supplies in the 70s and early 80s.
[COLOR=blue]
[check the description here.]("http://www.apc.com/products/family/index.cfm?id=67") or just google line conditioner.[/COLOR]

not having your computer shut down and loose your work every time there is a power glitch is the *opposite* of useless.  The split second gap to switch to battery does not bother your psu one bit; it has enough capacitance to ride right through it.

[COLOR=blue]i didn't say it was useless. I'm just saying people here are price sensitive and would rather lose that bit of work than have to replace a hardware (motherboard/power supply, etc), and have prolonged periods of down time because something is blown. I've seen many cases where customers have older pc's like pentium 4's. A blown motherboard today results in having to replace just about the whole pc. That's quite costly in just about any household.[/COLOR]

no, when the power comes back on it is not routed to the pc until the ups decides it's good.  Just the same, the psu in your pc ( and any ul listed device ) is designed to handle that just fine, which is why you don't see them blowing out all the time.

[COLOR=blue]this is only the case with line interactive or active ups's. A passive ups is as the name says; passive.[/COLOR]

got a source for this?  Most upses come with a warranty to replace any connected equipment that it fails to protect, and they wouldn't do that if such failures were common.

[COLOR=blue]personal experience. Lots of it. As for warranty to replace any connected equipment, it is never enforced here, and there is no way to prove that any blown device has been connected to the ups.[/COLOR]

as does a ups.  When the voltage gets too high, they either switch to battery or adjust their auto transformer to step the voltage back down.

[COLOR=blue]again, this is only true for active ups's, not for common passive ups's[/COLOR].

---

### Post by disabledaccount on 2011-03-14
> **psusi said:**
> I could have sworn that I had read a spec on wdc's web site that specifically said it was variable from 5400-7200, but now I can't seem to find it.  At any rate, there's nothing in that article that indicates it is only 5400 rpm.  To measure that you need to do a same sector read and measure the latency.  For 5400 rpm it should be around 11.1 ms, and for 7200 rpm should be around 8.3 ms.  I'll have to try and test mine tonight and see what difference tuning the performance settings makes.And you are right - there was such kind of misleading information in WD specs, but it has been removed about year ago - as an effect of widely confirmed fact that this is not true and to not scary potential buyers. And this arcticle (among thousatns of others) shows exactly that this drive spins at lower speed:
- proportionally higher access time
- proportionally lower sequential read (and this is the same 660GB/platter technology)

Besides, dynamic change of about +50%/-30% of speed is just impossible - if you realize that head fly height compensation was designed to reduce change of head dimensions between write and read cycles (different power dissipation and temperature), then such big change in rotational speed can be compared to switching between flying Boeing and Cesna. It would be also inefficient due to dramatically higher power needed for accelerating/decelarating the platters, comparable to startup inrush currents.

...this has to be clearified:
> **psusi said:**
> When the voltage gets too high, they either switch to  battery or adjust their auto transformer to step the voltage back  down.No, UPS-es don't have auto-transformers. In fact, only cheap/low power UPS-es have classic transormers built-in. Proffessional /high quality/true-sinus UPSes usually implements PWM technique, but every UPS can be destroyed when input voltage is too high or by powerfull surges. Good UPS will die without killing connected devices.

---

### Post by Vegan on 2011-03-14
[http://www.windows-it.tk/papers/raid.php]("http://www.windows-it.tk/papers/raid.php")

Read it closely and you will learn lots.

---

### Post by rubylaser on 2011-03-14
> Read it closely and you will learn lots.
What will we learn?

> Windows has the capability of building an array from several disks. This is also available with Linux. The array is secondary to the system disk and its used for data storage. Such capability comes from servers.

Such software arrays provide no protection from the system disk failing. When the OS fails, it also takes down the array. Recovery is hard to impossible.

...That you seem to provide info that is completely wrong, and backed up with nothing... Software RAID is dead simple to recover unless you've lost more disks that your parity protects you from.  This fact is the same with hardware RAID.  You seem that motherboard RAID is superior as well to software RAID as well...

> If you use motherboard RAID you have the same level of protection as a discrete card. RAID 5 will be slower then a dedicated card but it will be tolerant.

This statement is true for software RAID too and I wouldn't say it's slower either in most use cases (network is the bottleneck, not the disk throughput).  If it's a tech paper, provide benchmarks, and real world examples, otherwise it's just paper full of your opinions. After reading this I'm left wondering if you've only tried Windows crappy software RAID, and not actually tried mdadm on Linux.

---

### Post by Vegan on 2011-03-14
I need more disks to do that, I would love to show the differences.

I like RAID6 as its 2 disk safe

---

### Post by psusi on 2011-03-15
Please don't put your reply inside the quote brackets.  They are for quoting, not replying.

> **Demented ZA said:**
> 
check the description here. or just google line conditioner.

This is basically the UPS without the battery.  Is it actually much cheaper than the equivalent rated UPS?  They don't even bother selling these in the US.  I suppose if the price difference were enough and you frequently have out of range voltage then it would be worth it.  A decent UPS though is only around $100, and I've been using the same one for about 8 years now.

> **Demented ZA said:**
> i didn't say it was useless.

You actually DID say it was useless.  It is right there in your post I quoted.

> **Demented ZA said:**
> I'm just saying people here are price sensitive and would rather lose that bit of work than have to replace a hardware (motherboard/power supply, etc),

Fortunately, you get both from a UPS.  Given how cheap a surge protector is, one isn't a bad idea if you don't have a UPS, but any UL listed PSU will already protect the rest of the system.  You might loose the PSU, but not the motherboard.

> **Demented ZA said:**
> this is only the case with line interactive or active ups's. A passive ups is as the name says; passive.

No, it is not; it is the case for ALL UPS.  It is standby in that once it connects to mains, the pc is directly connected to mains ( except for an auto transformer doing some basic voltage step up/down on many models ) rather than the inverter.  When the UPS kicks over to battery, the PC is NOT connected to mains and so is not affected by conditions there.  They also power up in battery mode and only switch to mains once they decide mains power is ok.

> **Demented ZA said:**
> personal experience. Lots of it. As for warranty to replace any connected equipment, it is never enforced here, and there is no way to prove that any blown device has been connected to the ups.

Handwaving and anecdotal evidence.  There are MANY people with experience the other way.  You also don't need to prove that the blown device has been connected; you just have to register for the warranty coverage.

I live in Orlando, Florida.  We get more lightning strikes than anywhere else in the world.  Nobody here uses line conditioners.  Some people use just a surge protector, and a very few use a UPS, yet blown equipment from surges is fairly rare.

> **Demented ZA said:**
> again, this is only true for active ups's, not for common passive ups's

Wrong again.  The absolute cheapest off brands may not, but most decent ones do.  I'm pretty sure every APC standby model does, and my trusty old cyberpower 1000 AVR definitely does.  Voltage regulation with a multi tap auto transformer does not require a full line interactive design and is quite cheap to implement, since you need the transformer anyhow and it doesn't cost hardly anything to add a few extra taps.

---

### Post by psusi on 2011-03-15
> **tomazzi said:**
> 
- proportionally higher access time
- proportionally lower sequential read (and this is the same 660GB/platter technology)

Higher average access time for a random access pattern does not necessarily mean lower rpm, though the sequential read with same area density is a pretty strong indicator.  I'd still like to see a same sector read test to eliminate the track to track seek time though.

> **tomazzi said:**
> Besides, dynamic change of about +50%/-30% of speed is just impossible - if you realize that head fly height compensation was designed to reduce change of head dimensions between write and read cycles (different power dissipation and temperature), then such big change in rotational speed can be compared to switching between flying Boeing and Cesna. It would be also inefficient due to dramatically higher power needed for accelerating/decelarating the platters, comparable to startup inrush currents.

That does make sense.

> **tomazzi said:**
> ...this has to be clearified:
No, UPS-es don't have auto-transformers. In fact, only cheap/low power UPS-es have classic transormers built-in. Proffessional /high quality/true-sinus UPSes usually implements PWM technique, but every UPS can be destroyed when input voltage is too high or by powerfull surges. Good UPS will die without killing connected devices.

I suppose it isn't really proper to call it an auto transformer, but none the less, many do have a multi tap transformer they can use to step the voltage up/down a bit without switching to the inverter.  If you hit pretty much anything with 50kV, you will release the magic smoke, but a UPS will not be damaged by say, 300V, so I guess it depends on what you mean by "too high" ;)

> **rubylaser said:**
> 
This statement is true for software RAID too and I wouldn't say it's slower either in most use cases (network is the bottleneck, not the disk throughput).  If it's a tech paper, provide benchmarks, and real world examples, otherwise it's just paper full of your opinions. After reading this I'm left wondering if you've only tried Windows crappy software RAID, and not actually tried mdadm on Linux.

Indeed, and in terms of performance, fakeraid is exactly the same as software raid, because it IS software raid.

---

### Post by disabledaccount on 2011-03-15
> **psusi said:**
> I suppose it isn't really proper to call it an auto transformer, but none the less, many do have a multi tap transformer they can use to step the voltage up/down a bit without switching to the inverter.  If you hit pretty much anything with 50kV, you will release the magic smoke, but a UPS will not be damaged by say, 300V, so I guess it depends on what you mean by "too high" ;)I haven't seen such solution - but it is possible. Most transformer-based UPSes don't use coil taps switching - voltage spikes and surges are filtered by special passive filter with varistors or (newer)TVS beeing the main component. If voltage is too low or too high for programmed period, then UPS disconnects power grid (switching to battery).

> **psusi said:**
> Indeed, and in terms of performance, fakeraid is exactly the same as software raid, because it IS software raid.In fact, many "hardware raid controllers" are soft-raids, with the only difference that they are built as separate embedded systems placed on PCI-X/E card. :)

> **rubylaser said:**
> After reading this I'm left wondering if  you've only tried Windows crappy software RAID, and not actually tried  mdadm on Linux.
+1. Me too...

---

### Post by psusi on 2011-03-15
> **tomazzi said:**
> I haven't seen such solution - but it is possible. Most transformer-based UPSes don't use coil taps switching - voltage spikes and surges are filtered by special passive filter with varistors or (newer)TVS beeing the main component. If voltage is too low or too high for programmed period, then UPS disconnects power grid (switching to battery).

Yes, it isn't used for spikes, but for prolonged line over or under voltage, many UPS just switch the transformer tap rather than switch to battery.  Not all do, but many do.  This is what most manufacturers are referring to when they label the product as AVR or automatic voltage regulation.

---

### Post by disabledaccount on 2011-03-15
Could You tell what is exact model/type of Your UPS?
You see, such approach makes sense with really heavy loads, several kilowatts and more. For small loads voltage conditioners are built of magnetic amplifiers - because this allows linear regulation.

---

### Post by psusi on 2011-03-15
> **tomazzi said:**
> Could You tell what is exact model/type of Your UPS?
You see, such approach makes sense with really heavy loads, several kilowatts and more. For small loads voltage conditioners are built of magnetic amplifiers - because this allows linear regulation.

That is a much more expensive and inefficient solution.  Exact regulation is not important, so the simple multi tap transformer approach is used.  I have a CyberPower 1000 AVR ( not made any more ).  It has dual 8 AH batteries which gives it a good run time.  The newer models of that load rating seem to use a single 9AH battery.  I guess they just don't make 'em like they used to.

---

### Post by disabledaccount on 2011-03-16
> **psusi said:**
> That is a much more expensive and inefficient solution.  Exact regulation is not important, so the simple multi tap transformer approach is used.  I have a CyberPower 1000 AVR ( not made any more ).  It has dual 8 AH batteries which gives it a good run time.  The newer models of that load rating seem to use a single 9AH battery.  I guess they just don't make 'em like they used to.Nope, magnetic amplifiers can reuse existing transformer windings with only few additional components. Unfortunatelly CyberPower don't provide any consitent informations or datasheets for their AVR technology - so my question is: have you checked Your UPS internal circuits?
I don't want You to belive in my words only, so let's look to APC whitepapers:
[http://www.ptsdcs.com/whitepapers/58.pdf](http://www.ptsdcs.com/whitepapers/58.pdf) - APC provides voltage regulation by reconverting power grid voltage (page 10) what is not available in low-end off-line models (page 9)
And here You have complete describtion how voltage conditioning is implemented in today's UPSes (using magnetic amplifiers and PWM)
[http://eepel.snu.ac.kr/~ghks95/papers/ias2004-2.pdf]("http://eepel.snu.ac.kr/%7Eghks95/papers/ias2004-2.pdf") - page2, fig.1 3-phase version, page4, fig.5 - single phase simplified schematic.

---

### Post by psusi on 2011-03-16
It looks like APC's "Pro" series has the AVR.  I had thought that it filtered down into their entire line, but I guess their cheapest models don't have it.

It looks like I was mixing up my terminology a bit.  It looks like you are correct, the pro series is a "line interactive" UPS.  When you said that before I was thinking fully online UPS, but according to Wikipedia, "line interactive" just means standby with the multi tapped autotransformer.

Outside the consumer UPS world (like inverters for solar/wind power), "interactive" means something more than just a multi tap transformer.  I guess the UPS marketing guys flubbed it a bit and it has now become common usage there.

---

### Post by Demented ZA on 2011-03-17
> **psusi said:**
> Please don't put your reply inside the quote brackets.  They are for quoting, not replying.

OK, sorry about that, was tired when I posted, hadn't had much sleep.


> 
This is basically the UPS without the battery. Is it actually much cheaper than the equivalent rated UPS?  They don't even bother selling these in the US.  I suppose if the price difference were enough and you frequently have out of range voltage then it would be worth it.  A decent UPS though is only around $100, and I've been using the same one for about 8 years now.
Yes, these basically perform the same function as the interactive part of an interactive type UPS, minus the battery, and yes, here in South Africa they are a fair bit cheaper to acquire, and to maintain as they have no batteries, than their UPS counterparts. Batteries are fairly expensive here, and they seem to only last about 3 years. Line conditioners have also been overlooked by many, so the demand hasn't pushed up the price.

UPS's here are fairly expensive. Its like real estate that rose after discovery of gold. We started having regular brownouts due to our incompetent government thinking that maintenance on our generators in power plants are a senseless waste of money and that it belongs in other better places like pockets of government officials.

Price wise, a line conditioner is around R300, and a 300 kva ups is around R800, and that is for the cheap models, mainly Mecer and Proline (locally manufactured brands).

> 
You actually DID say it was useless.  It is right there in your post I quoted.
Well yes I did. Sorry about that. I missed it when I replied. Again, I was tired. With that said, I meant it in a different context, although, admittedly I suppose I wasn't being clear:

To quote myself:
```
A ups is rather the useless bit of hardware.
```The emphasis is on the word rather. At least in our market/economy. I agree with you that being able to save work is not useless, and in fact a requirement for some users/business. I just meant that the average South African can _rather_ afford to lose the little bit of work he/she was busy with, compared to the loss of downtime, convenience, and cost of repair. When you buy a product to perform one function, but it performs another, (useful) function that you do not use, it is still useless to you, or useless compared to the function you need. That function in South Africa is to protect ones equipment. This is what users ask for when they end up with a UPS. They ask for something to protect their computer, and the answer from sellers, is a UPS, and since people are price sensitive, they buy the cheapest, and aren't advised the pitfalls and caveats.

> 
Fortunately, you get both from a UPS.  Given how cheap a surge protector is, one isn't a bad idea if you don't have a UPS, but any UL listed PSU will already protect the rest of the system.  You might loose the PSU, but not the motherboard.
The UPS's that we deal with that have already been sold, are not UL listed. We open them up to replace the battery, and you can see they are very basic: 12V battery, transformer, relay, inverter. These are definitely not auto transformers like we see in the more expensive APC active UPS's.

> 
No, it is not; it is the case for ALL UPS.  It is standby in that once it connects to mains, the pc is directly connected to mains ( except for an auto transformer doing some basic voltage step up/down on many models ) rather than the inverter.  When the UPS kicks over to battery, the PC is NOT connected to mains and so is not affected by conditions there.  They also power up in battery mode and only switch to mains once they decide mains power is ok.
While the UPS is in standby mode, is the PC not vulnerable to fluctuations? I don't know how accurate it is, but looking at a motherboard BIOS with overclocking features and power reporting, the voltages clearly fluctuate while on mains. When that same PC is running off just a ups, even a cheap one, the voltages seem to stabilize substantially by comparison.

> 
Handwaving and anecdotal evidence.  There are MANY people with experience the other way.  You also don't need to prove that the blown device has been connected; you just have to register for the warranty coverage.
For the common UPS that I am referring to, we have no _such_ service. You get a thin 1 page pamphlet in the box, with a legal disclaimer that claims that you will be able to claim up to a limit for damaged equipment that was connected to the device, subjective to an investigation from an official of, or nominated by the manufacturer. There is no registration.

I suppose APC is a little different, but we don't really get issues from them, so I can't really comment. I can say that most people don't use them, as they tend to be more expensive, and as a result more scarce (supply and demand).

> 
I live in Orlando, Florida.  We get more lightning strikes than anywhere else in the world.  Nobody here uses line conditioners.  Some people use just a surge protector, and a very few use a UPS, yet blown equipment from surges is fairly rare.
Well a line conditioner would hardly be my proposed solution to prevent lightning damage. A surge protector plug or a ups (because of its fuse) would be my suggestion. Specially protection with RJ11 support for telephone wires, as that's where most equipment blows through when we have lightning storms.

As for mains electricity, our power is fairly unstable here at the moment. It never used to be until last year. Its slowly improving as repairs are made. But brownouts are accompanied by surges during times of load shedding. These surges are spillage from adjacent power grids. Sometimes we experience no loss of power, but come to discover devices are not working for no apparent reason. Other times, you can just stare at lights to see them flicker between dim and bright, to know that power is acting up.


> 
Wrong again.  The absolute cheapest off brands may not, but most decent ones do.  I'm pretty sure every APC standby model does, and my trusty old cyberpower 1000 AVR definitely does.  Voltage regulation with a multi tap auto transformer does not require a full line interactive design and is quite cheap to implement, since you need the transformer anyhow and it doesn't cost hardly anything to add a few extra taps. Not sure what (absent quote) you are referring to. As for the rest of the paragraph, I suppose what you are referring to as "the absolute cheapest off brands..." is probably our norm, or average. With that said, look at point 2.1 and point 2.2 of the [Wiki page about UPS's]("http://en.wikipedia.org/wiki/Uninterruptible_power_supply"). The common UPS's I have been referring to are passive ups's, or as Wiki refers to them, offline. According to their definition:

> The offline / standby UPS (SPS) offers only the most basic features,  providing surge protection and battery backup. The protected equipment  is normally connected directly to incoming utility power. When the  incoming voltage falls below a predetermined level the SPS turns on its  internal DC-AC inverter circuitry, which is powered from an internal  storage battery. The SPS then mechanically switches the connected  equipment on to its DC-AC inverter output. The switchover time can be as  long as 25 milliseconds depending on the amount of time it takes the  standby UPS to detect the lost utility voltage. The UPS will be designed  to power certain equipment, such as a personal computer, without any  objectionable dip or brownout to that device.A look at the first sentence suggests that a UPS that does anything remotely relating to regulation of power, doesn't fit under the description of an off-line/standby UPS. Unless you feel the wiki is wrong, then feel free to [U][contribute and correct the Wiki]("http://en.wikipedia.org/w/index.php?title=Uninterruptible_power_supply&action=edit&section=3").
[/U] 
With that in mind, your statement;
> I'm pretty sure every APC standby model does, and my trusty old cyberpower 1000 AVR definitely does. does not account for the fact that what you are referring to, is, by definition a hybrid design, and not _just_ a passive/standby/off line design. Furthermore, I was referring to absolute passive/standby/off line designs, vs  active/line interactive designs.

To wrap it up, my point is that, I run a support company, and we have to constantly explain to customers why the UPS they had bought had not protected them from a flurry of surges. Then, we have to advise them that they have to take their grief up with the manufacturer, even though that is as productive as punching a brick wall, bare fisted, just because they were duped into buying a cheap ups because the salesman wanted to make a quick buck, rather than advising them of better alternatives, simply because he doesn't know of any, and doesn't care to find out.

In our economy, a line conditioner is money better spent than an over-appraised, cheap-quality, passive UPS, if all you want to do is add some protection for your precious hardware, and you don't mind losing up to 5 minutes of work, since, by our advice and configuration, that's how long ago word auto-saved your letter to your mom, or Outlook drafted your invoice to a customer for the business you run from home.

---

### Post by psusi on 2011-03-18
> **Demented ZA said:**
> While the UPS is in standby mode, is the PC not vulnerable to fluctuations? I don't know how accurate it is, but looking at a motherboard BIOS with overclocking features and power reporting, the voltages clearly fluctuate while on mains. When that same PC is running off just a ups, even a cheap one, the voltages seem to stabilize substantially by comparison.

If the motherboard voltage fluctuates by more than 2-3%, then you have a bad PSU.  The whole job of the PSU is to provide reliable power to the rest of the system no matter what is going on with the mains.  Its supplied voltage should never fall outside the normal range.  The PSU should regulate correctly when mains fluctuates by at least +/- 10-15% ( most can take anywhere from 90-260v ), and rather than provide wrong voltage to the system, it shuts down when mains gets too far out of spec.

> **Demented ZA said:**
> For the common UPS that I am referring to, we have no _such_ service. You get a thin 1 page pamphlet in the box, with a legal disclaimer that claims that you will be able to claim up to a limit for damaged equipment that was connected to the device, subjective to an investigation from an official of, or nominated by the manufacturer. There is no registration.

Sounds like you need to buy the APC model instead of the local gov't backed one ;)

> **Demented ZA said:**
> To wrap it up, my point is that, I run a support company, and we have to constantly explain to customers why the UPS they had bought had not protected them from a flurry of surges. Then, we have to advise them that they have to take their grief up with the manufacturer, even though that is as productive as punching a brick wall, bare fisted, just because they were duped into buying a cheap ups because the salesman wanted to make a quick buck, rather than advising them of better alternatives, simply because he doesn't know of any, and doesn't care to find out.

Again, it sounds like you are dealing with a defective UPS from a disreputable manufacturer.  You will not get those results with a proper one from someone like APC.

---

### Post by disabledaccount on 2011-03-19
I suppose that in every country there are defined standards for power grid voltage quality, and agreements on what percentage of power outage time is allowed. Power grid owner is responsible for damages caused by over/undervoltage and for lost of profit due to power outages and equipment lost.

Cheap UPSes are good choice for protection against occasional power outages.
In case of bigger networks (eg. whole building) It is far better solution to buy one big UPS with redundant (hot-swapable) inverters, control modules, etc.

---

### Post by Demented ZA on 2011-03-23
> **psusi said:**
> If the motherboard voltage fluctuates by more than 2-3%, then you have a bad PSU.  The whole job of the PSU is to provide reliable power to the rest of the system no matter what is going on with the mains.  Its supplied voltage should never fall outside the normal range.  The PSU should regulate correctly when mains fluctuates by at least +/- 10-15% ( most can take anywhere from 90-260v ), and rather than provide wrong voltage to the system, it shuts down when mains gets too far out of spec.

Bad PSU or not, this could still have been prevented or reduced by stabilizing power. A line conditioner would help, same as an active design APC UPS. Instead, these people have been sold an average UPS (not APC)-- by definition, one that doesn't regulate power. Again, because it is the norm. By the way, mention APC all you want, APC is not the average ups. APC is a high quality product, and by definition means it is by no means average.

> 
Sounds like you need to buy the APC model instead of the local gov't backed one ;)
Why? Its not like APC will extend their protection policy to us?
Please visit the [APC Ecuipment Protection Policy (EPP) knowledge base article]("http://emea-en.apc.com/app/answers/detail/a_id/1393/kw/claim"). Right at the bottom of the page it says, and I quote:
> 
*Note: The EPP is only available in the United States and Canada.*
 Last time I checked, the United States and Canada doesn't make up 50% or  more of the world. Thus, it shall seem that not having a proper EPP in the rest of the world would not be so uncommon after all ;)

Without an EPP,  APC just becomes an overly expensive brand, given the added price padding because of supply and demand. It might be good quality, but it won't be good value for money. As mentioned earlier, price is an issue, but that is not just the case in SA.

Also, one needs to get hold of these, and since the Leading retailers here don't sell APC, how is the average man in the street going to know about APC or even get hold of one?

Furthermore, if users don't need to save data in an event, but they would just prefer to protect their equipment, and as I said, UPS's are rediculously expensive here and price is an issue, why on earth would I sell a customer an APC UPS at a premium, with an EPP that doesn't cover SA? And this after the customer's previous UPS didn't do the job? Customers would have serious trust issues. "That's what the last guy said" comes to mind. 

I can just sell an APC line conditioner at a fraction of the cost and be done with it.

How does this not make sense?

> 
Again, it sounds like you are dealing with a defective UPS from a disreputable manufacturer.  You will not get those results with a proper one from someone like APC.I was talking about passive UPS's (the average). Again, that means it won't regulate power because it is not intended to. So if it doesn't regulate power, erm, isn't it doing what its designed to do and nothing more? How does that make it faulty? 

I'm talking about the average situation. Your talking about the ideal (APC + Regulation + EPP). Two very different plains.

I have nothing against selling (decent) UPS's, if the situation calls for it, and it can be afforded/justified.

---

### Post by psusi on 2011-03-24
> **Demented ZA said:**
> Bad PSU or not, this could still have been prevented or reduced by stabilizing power. A line conditioner would help, same as an active design APC UPS. 

Yes, you can make up for a crap PSU with a line conditioner, but rather than buy extra equipment, why not just get a proper PSU?

> **Demented ZA said:**
> Why? Its not like APC will extend their protection policy to us?
Please visit the [APC Ecuipment Protection Policy (EPP) knowledge base article]("http://emea-en.apc.com/app/answers/detail/a_id/1393/kw/claim"). Right at the bottom of the page it says, and I quote:
 Last time I checked, the United States and Canada doesn't make up 50% or  more of the world. Thus, it shall seem that not having a proper EPP in the rest of the world would not be so uncommon after all ;)

It doesn't really matter if you actually have the warranty or not; my point was that it does protect your equipment or they wouldn't offer the warranty.

> **Demented ZA said:**
> Without an EPP,  APC just becomes an overly expensive brand, given the added price padding because of supply and demand. It might be good quality, but it won't be good value for money. As mentioned earlier, price is an issue, but that is not just the case in SA.

I agree that they are overpriced, which is why I find other vendors that also make a quality, but less expensive, product.

> **Demented ZA said:**
> I can just sell an APC line conditioner at a fraction of the cost and be done with it.

How does this not make sense?

It does make sense.  Or you can just sell them a PSU that isn't crap.  But I guess if that's what you've got to work with down there, then you gotta do what you can with what you've got.

---

