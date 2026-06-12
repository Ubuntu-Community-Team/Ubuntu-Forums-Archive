---
title: "External hard drive recommendations?"
date: 2008-02-05
forum: The Cafe
---

### Post by monge13 on 2008-02-05
Hi everybody!

I have been researching about external hard drives but I have some doubts about the correct operation of some of those units in Linux (for example Seagate and WD External Hard Drives) because in some forums there are good references; but in another sites I found very bad experiences about the use of those brands (specially seagate).
What product do you recommend me? A external hard drive or an external enclosure? Which model?
Thanks a lot for your comments and experiences about both options.

---

### Post by aysiu on 2008-02-05
I use a Lacie, and it works fine. By the way, since this is a personal preferences thread, rather than a technical support thread, I'm moving it to a more appropriate subforum.

---

### Post by lespaul_rentals on 2008-02-05
I have a Seagate, and it's great!  No problems with Linux whatsoever.  I use it to hold my music, and it's plugged in and running 24/7.  Just format it with ext3/ReiserFS/whatever and add it to your fstab, and it will mount at bootup with no issues.  Or, you can plug it in when you need it for backups or whatever.  It runs cool, too.

EDIT: It's this one right here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148233](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148233)

---

### Post by bobbocanfly on 2008-02-05
I have a Western Digital My Book Pro II 1TB RAID drive which works perfectly out of the box with Ubuntu Gutsy. Saying that i have had it for about 5 hours so i have no idea how reliable it is. I have had a Toshiba  external HD for about 5 years and only now is it beginning to fail (make weird clicking noises) when under intense pressure (Reading off 160gb of data and writing it onto my new drive).

---

### Post by az on 2008-02-05
Seagate drives usually come with a five-year warranty, where other brands give you one.

From browsing the sales flyers, putting together a drive in a usb enclosure is cheaper than buying the same size external drive.  An "external" drive is simply a drive in an enclosure.

Avoid 2.5 inch (laptop) drives.  If you want reliability, use a desktop-sized drive (3.5 inch).

Why do you need an external drive?  Is it for backups or for portability.  Do not use an external drive for both.

If you want extra reliability, don't carry around a drive; buy an internal drive, put it in your desktop and leave it there.  If you need to carry your drive around with you, make frequent backups onto a non-portable drive.

---

### Post by Superkoop on 2008-02-05
I have a Maxtor onetouch4, it works perfectly fine with Ubuntu. I don't believe the software works with Ubuntu, but that software was really useless, I never used it.

---

### Post by julian67 on 2008-02-05
I just buy bare drives and cheap caddies and fit them, takes about a minute, and it always works.  I have several laptop drives and full size drives in external cases. The enclosures are just simple USB devices so pretty much guaranteed to be fine. If you buy a branded external drive with networking capability it may use proprietary networking protocols and basically be unsatisfactory on anything except Windows, though this is not so common as most of these devices are actually using samba.

---

### Post by red_Marvin on 2008-02-05
I have two seagate freeagents 250Gb disks, I chose them based on that I've heard good things about seagate's disk quality, and the 5 year warranty is a good thing.
They look nice too.

A minor problem is that the power adaptor might give a high pitched hiss, but if my mind serves me right it tends to go away after a couple of minutes.

---

### Post by lespaul_rentals on 2008-02-05
> **Superkoop said:**
> I have a Maxtor onetouch4, it works perfectly fine with Ubuntu. I don't believe the software works with Ubuntu, but that software was really useless, I never used it.

The software that comes with external hard drives really is worthless.  I have a script I wrote that does a differential update of my entire music folder.  I just run it every now and then to transfer the new music on my main hard drive to the big collection on my external music hard drive.  I also have one for backups, just run it and the full collection on my Seagate gets copied to my backup drive.

Bash > any Windows crap

---

### Post by x0as on 2008-02-05
I've had no problems with my seagate freeagent, hd spins down if its not used for 15 minutes and spins up again when you access it so it doesn't get hot.

---

### Post by koleoptero on 2008-02-05
I have a WD my book external usb drive, formatted in ntfs, and it works with absolutely no problems both in linux and in windows. I have it connected most of the time cause that's where all my files are, and it boots at startup without me tampering with fstab or anything. Also I have had it since august, so I'd say it is reliable enough.

Just remember that whatever external drive you decide to buy, always unmount it before disconnecting it.

---

### Post by herbster on 2008-02-05
I asked here a while ago this same question and grabbed a WD 500gb for about $110 and a Vantec NexStar3 enclosure for about $40. I can pop it in at eSata on my home pc or USB with my laptop at the office, it's great. And looks perty to boot :D

I have 3 partitions as ext3 and one NTFS. Just pop on the FS Driver on XP/Vista if need be and you're set for a 100% functional drive in each OS.

And that's my 3rd WD drive, I can't recommend their drives enough.

---

### Post by fedex1993 on 2008-02-05
i have a maxtor one touch IT WORKS GREAT. The software that maxtor includes the GPL source code so i can use it with linux perfect and i love the one touch feature. Thats my first my second is WD because there size and nice ness

---

### Post by SunnyRabbiera on 2008-02-05
seagate, very reliable and linux friendly

---

### Post by jpittack on 2008-02-05
Rosewill case with seagate drive, sata to usb.  Does have esata support on the rosewill, but I don't have on my laptop, thus, I only know about the usb.  Works just fine, even though the hard drive is still nfts, since I never changed it, and don't really have a choice.  It backs up two windows computers, plus my laptop with vista.

---

### Post by johndc on 2008-02-05
LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.
LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.
LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.
LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.LaCie.

WD MyBooks are complete garbage. I had to use one from work once, and it was horrible. My LaCie has never given me a problem in 3 years. It gets a bit hot, but it's small, fast, and reliable.

---

### Post by Presto123 on 2008-02-05
> **herbster said:**
> I asked here a while ago this same question and grabbed a WD 500gb for about $110 and a Vantec NexStar3 enclosure for about $40. I can pop it in at eSata on my home pc or USB with my laptop at the office, it's great. And looks perty to boot :D

I have 3 partitions as ext3 and one NTFS. Just pop on the FS Driver on XP/Vista if need be and you're set for a 100% functional drive in each OS.

And that's my 3rd WD drive, I can't recommend their drives enough.

You can actually find the whole thing together for $120 at BestBuy

[http://www.bestbuy.com/site/olspage.jsp?skuId=8475063&st=external&type=product&id=1185271084002](http://www.bestbuy.com/site/olspage.jsp?skuId=8475063&st=external&type=product&id=1185271084002)

I paid close to the same for a 320gig but that was about 6 months ago, I guess. I love mine, too.

**Edit**It's cheaper at NewEgg with free shipping. Take a look at this list here:[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=414&name=External-Hard-Drives](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=414&name=External-Hard-Drives)

---

### Post by monge13 on 2008-02-06
Hi again!

Thanks to all for your quickly response! I really appreciate it. 
I decide to buy a seagate freeagent pro 750 GB. I hope to do a good investment with this one.

Thanks!!

---

### Post by lespaul_rentals on 2008-02-06
> **monge13 said:**
> Hi again!

Thanks to all for your quickly response! I really appreciate it. 
I decide to buy a seagate freeagent pro 750 GB. I hope to do a good investment with this one.

Thanks!!

Cool.  Hope you enjoy.

---

### Post by OffHand on 2008-02-06
> **johndc said:**
> 
WD MyBooks are complete garbage. I had to use one from work once, and it was horrible. My LaCie has never given me a problem in 3 years. It gets a bit hot, but it's small, fast, and reliable.

I have got my WD MyBook for about 2,5 months now and it never failed me. I realize 2,5 months isn't very long but so far, so good.

---

### Post by johndc on 2008-02-07
> **OffHand said:**
> I have got my WD MyBook for about 2,5 months now and it never failed me. I realize 2,5 months isn't very long but so far, so good.

It's not so much that it's unreliable -- I've never had one fail -- but it is painfully slow, and has this annoying tendency to fall "asleep" after a few minutes of inactivity. It got on my nerves so much that I created a cronjob to keep it spun up. The LaCie just seems to be a better drive, quality-wise, though it is older. It's solidly built and fast.

---

