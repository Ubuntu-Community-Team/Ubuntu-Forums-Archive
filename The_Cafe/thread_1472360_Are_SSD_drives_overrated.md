---
title: "Are SSD drives overrated ?"
date: 2010-05-04
forum: The Cafe
---

### Post by ubuwatson on 2010-05-04
I think SSD drives are great, don't get me wrong: They produce lower heat, are very stable, and reduce power consumption.   Benchmarks show that these drives are blazing fast, but in real world use I was just a bit underwhelmed when I purchased the Intel 80G X25.  Maybe my expectations were just too high :confused:. 

I recently installed Ubuntu 10.04 on the Intel 80G X25 and while the operating system was very fast using this drive, there was nothing that (in all honestly) 'blew me away'.  So in an attempt to reason with the issue I decided to experiment a little (please keep in mind this was totally unscientific as instead of benchmarks, I relied on good old fashion real world everyday usage as a gauge).  I installed Ubuntu 10.04 again, this time using a brand new Western Digital 5400 rpm Scorpio Blue (250 G).  Thus far I have not really noticed any significant differences between the two drives.  Both drives are very quiet, power consumption seems par, and boot times are the same.  File operations feel just a hair slower with the WD, but only marginally so.  To further my testing, I decided to install Windows 7 on both drives just to take the OS out of the equation, but even with Windows 7, the experience was the same.   I did verify I had the latest firmware / TRIM support using Intel's own utilities.

I have since sold the SSD drive to a friend, for me the conventional hard drive was 'good enough' for my needs.  Of course the price is right with the added advantage that there is no need to worry about optimizing the drive, TRIM support working, or the drive slowing down and/or experiencing issues over time.  I don't know if this is an argument against SSD drives or a testament to just how good conventional Western Digital drives are.

---

### Post by arsenic23 on 2010-05-04
For day to day activities in linux a bit more hard disk speed isn't really ever going to be appreciated.  I know that once I boot and load my programs for the first time that they will be in memory.  I suppose if you have low memory or another reason to use swap frequently you'd notice more.

Of course those drives are still very good for many tasks.  Disk access intensive games see vast improvements from them (or so I'm told).  Also database work that requires constant heavy read/writes will see a decent gain.

---

### Post by snowpine on 2010-05-04
I haven't had the opportunity to try an SSD in a desktop yet, but I can tell you that for netbooks, SSDs are the way to go... I have 2 similar spec netbooks, one with HDD, one with SSD... the SSD model is noticably quieter and cooler.

---

### Post by ubuwatson on 2010-05-04
> **snowpine said:**
> I haven't had the opportunity to try an SSD in a desktop yet, but I can tell you that for netbooks, SSDs are the way to go... I have 2 similar spec netbooks, one with HDD, one with SSD... the SSD model is noticably quieter and cooler.

I actually did these tests on my Acer netbook.  I haven't noticed any appreciable difference in temperature.  Noise wise the SSD is completely silent, but then again the WD is hard to hear unless in a silent room.  I agree their are differences, but nothing that convinces me, maybe that's just me....

---

### Post by ubuwatson on 2010-05-04
> **arsenic23 said:**
> For day to day activities in linux a bit more hard disk speed isn't really ever going to be appreciated.  I know that once I boot and load my programs for the first time that they will be in memory.  I suppose if you have low memory or another reason to use swap frequently you'd notice more.

Of course those drives are still very good for many tasks.  Disk access intensive games see vast improvements from them (or so I'm told).  Also database work that requires constant heavy read/writes will see a decent gain.


I think you hit the nail on the head and I believe this is why benchmarks don't really give us the real world perspective.  Day to day use (internet browsing, organizing pictures, etc) doesn't really show any appreciable gains using the SSD drive over a standard HD.  Considering netbooks themselves are not typically used for heavy loads of production work, it seems obvious to me that the 'SSD drives are perfect for netbooks' slogan is a tad hard to swallow, but then again it's based on how I used the machine and other experiences are probably different.

---

### Post by arsenic23 on 2010-05-04
> **ubuwatson said:**
> 'SSD drives are perfect for netbooks'

I think people who say that are speaking purely in terms of a gain in battery life; or mostly in terms of a gain in battery life.

---

### Post by snowpine on 2010-05-04
> **arsenic23 said:**
> I think people who say that are speaking purely in terms of a gain in battery life; or mostly in terms of a gain in battery life.

Also lower heat, lower noise, and more durable (due to no moving parts).

Most OEM netbook SSD's are not the "good" kind (too expensive) so there is no performance benefit. But noise, heat, durability, and battery life are nothing to sneeze at. :)

---

### Post by paulisdead on 2010-05-04
I'm actually pretty impressed with the pair of 40GB Intel SSDs I grabbed when newegg had them on sale.  They're not RAIDed, just one for win7 and one for Ubuntu.  Windows 7 actually has a reasonable startup time, and Ubuntu's startup time is insanely fast.  The old boot drive was 10K RPM velociraptor, so it's not like I was coming from some 5400RPM notebook drive or anything.  Apps like firefox and thunderbird open up right away, and nautilus is much snappier, even when browsing across NFS, since all those video thumbnails are loaded off the SSD.

My question to those of you who are unimpressed with their SSDs, are you running your whole /home partition on a hard disk?  That's how I initially had mine setup, and I could tell when it was having to wait to pull config files off the hard drive.  So the startup time for apps like firefox and thunderbird wasn't much better.  Once I did some rearranging of things, and got all those config files and email on the SSD, things got snappier.

Maybe my expectations weren't as high, but I got what I expected out of my purchase.

Admittedly, it is a hassle that they didn't include a 2.6.33 kernel with Lucid, so you have to upgrade in order to get trim working.  Not sure if this is still needed for Lucid, but I upgraded hdparm as well.

---

### Post by maestrobwh1 on 2010-05-04
I had a 32 GB MLA (cheaper) type drive and I put it in my IBM thinkpad and installed Lucid.  EXT4

It boots really fast.  The boot splash does not even have time to come up.

It is slow only when doing something requiring a significant disk write (upgrading packages for instance).  It made the laptop a bit lighter.  The drive is not drop sensitive.  The machine does not vibrate at all.

I don't think there is anything huge you will gain from using an SSD if those items are not important to you.  I never really noticed a huge gain in battery life but I could push an extra half hour out of the machine.

---

### Post by dlradlt on 2010-05-08
> **maestrobwh1 said:**
> I had a 32 GB MLA (cheaper) type drive and I put it in my IBM thinkpad and installed Lucid.  EXT4

It boots really fast.  The boot splash does not even have time to come up.

It is slow only when doing something requiring a significant disk write (upgrading packages for instance).  It made the laptop a bit lighter.  The drive is not drop sensitive.  The machine does not vibrate at all.

I don't think there is anything huge you will gain from using an SSD if those items are not important to you.  I never really noticed a huge gain in battery life but I could push an extra half hour out of the machine.

once the price starts dropping SSD's will be a major boost for mobile devices.

 That half hour of extra time your talking about equates to a 20 to 35 percent decrease in power consumption if its a full size thinkpad your talking about. and for mobile devices that extra half hour makes a big difference.

next big deal is the decrease in heat generated my wifes net-book gets so hot that its uncomfortable to hold on my lap.

IMHO SSD's are not ready for the consumer mass market yet because of their limited storage capacity and high cost per GB 

overrated no overpriced yes

L8r

---

### Post by andrewabc on 2010-05-08
SSD are not overrated.
When a cheap netbook HDD gets 50mb/s read/write and SSD can get 200mb/s read, 100mb/s write, that makes a big speed difference.

Expensive, sure. But if you want faster speed it is worth it. Store your data on HDD. OS/apps on SSD.

Somewhat of a myth that SSD don't generate much heat.
[Heat Output Results](http://benchmarkreviews.com/index.php?option=com_content&task=view&id=333&Itemid=60&limit=1&limitstart=13)
To be fair it was a crappy SSD being reviewed.

---

### Post by chappajar on 2010-05-08
> **andrewabc said:**
> SSD are not overrated.
When a cheap netbook HDD gets 50mb/s read/write and SSD can get 200mb/s read, 100mb/s write, that makes a big speed difference.

Expensive, sure. But if you want faster speed it is worth it. Store your data on HDD. OS/apps on SSD.

Somewhat of a myth that SSD don't generate much heat.
[Heat Output Results]("http://benchmarkreviews.com/index.php?option=com_content&task=view&id=333&Itemid=60&limit=1&limitstart=13")
To be fair it was a crappy SSD being reviewed.

That test was done with both disks ''idling''. I suspect the differences would show when the disks are working hard, and the HDD temperatures go through the roof.  

EDIT: I missed this quote from that test article before:  > Although **the heat produced by SSD's under load is usually the same as what the Hard Disk Drive generates at idle**, ...

---

### Post by handy on 2010-05-08
No, just overpriced.

---

### Post by 0011235813 on 2012-03-18
Yes and no.
SSDs are **far** superior technology to HDDs, they are much quieter, use virtually no energy, are more durable and do not require defrag. But most of all, they are much faster than HDDs. A properly configured SSD is about two times faster than a 7200rpm HDD, let alone a 5400rpm one. And let me tell you, that anyone who claims that they are NOT faster doesn't have a proper test (I'm not being nasty when I this OK?). I use Ubuntu on a 7200rpm drive computer and a 5200rpm computer. The boot time on the 7200rpm is pretty good (even with encrypted /home directory), the 5200rpm one is downright a turtle. I have seen W7 on an SSD boot in 15 secs, crapware filled Windows! Boot faster than my *buntu on the 7200rpm!

Now let me tell you why the apparent experiences of people who see no difference between SSDs and HDDs. The result is of a phenomena called "bottlenecking" ; Essentially, the computer is only as fast as it's slowest component, so having a slow old CPU, or more likely, slow RAM, is the main reason. Also, a slow motherboard can slow the computer down.

Yes, SSDs are expensive, so a Hybrid drive is probably a good compromise. And yes they are superior; the question is, is having a very fast boot and fast loading programs important to you?

---

### Post by Elfy on 2012-03-18
Old thread closed.

---

