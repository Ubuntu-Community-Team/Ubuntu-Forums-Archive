---
title: "Raid 5 locking up system"
date: 2012-08-25
forum: Server Platforms
---

### Post by darkapec on 2012-08-25
Hopefully someone knows the solution to this problem. 

I recently rebuilt my Raid 5 array, it contains 4 2tb drives. One drive failed and I sent it in for warranty repair. Once the drive arrived and I started the mdadm repair the raid card quit working in the PCI-X slot. 

I moved the card to a PCI slot and continued rebuilding the raid. During the rebuild all data was able to be accessed reliably. I had no problems streaming content from the raid. 

Once the raid finished rebuilding accessing the data is flaky. I am able to see all my data and fsck reports 0 errors. However once I start streaming a movie from the raid it will play for 3-5minutes and then just stop playing. 

If I attempt to access the raid via SAMBA it will lock the computer that is accessing the raid up. 

Any help would be appreciated.

Thanks
Jake

---

### Post by TheFu on 2012-08-25
a) Backup that data. Be certain you have a good current backup. If that card dies, your data is gone until you get another of the same model from the same vendor.
b) Become familiar with your RAID hardware and support programs that the vendor provides.  Those are really your main hope here.  You might want to try the card and array in a different PC to see if your motherboard is the issue.
c) Start watching all the log files for issues.  dmesg, syslog, and whatever your RAID uses. Posting the exact error messages (or googling them yourself) will yield the best answers.
d) You might want to consider using Linux software RAID at home where it isn't practical to have a spare RAID card ready.  At work, get a spare ASAP.  Software RAID is more flexible and forgiving, plus you aren't tied to whatever the hardware vendor decides you need.  I've moved software RAID between different Linux servers (very different SATA controllers) and different distros without issues.

If you want better help, **post the exact RAID card model** and **chips** here. Also **post the exact error messages from the log files**. You might want to change the title to have the RAID controller in it too.

---

### Post by rubylaser on 2012-08-25
I know Jake, and he's currently using mdadm, so it's not a hardware RAID controller.

 If you have an open PCI-Express slot, I'd really suggest you purchase a decent HBA for your disks.  Something like the [IBM BR10i]("http://www.ebay.com/itm/IBM-ServeRAID-BR10i-SAS-SATA-Controller-/280903580331?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item4167287aab") works great with disks 2TB or less and they're very cheap on Ebay.

I use (2) [IBM M1015's]("http://www.ebay.com/sch/i.html?_nkw=ibm+m1015&_sacat=0&_odkw=ibm+br10i&_osacat=0") in each of my home storage boxes (these are SATAIII capable and support disks larger than 2TB). But, since they've gained popularity, they're no longer cheap to pickup (I got mine for $60/each)

I'd take a look at iostat and iotop when you're accessing the array, and see if you can identify the bottleneck.

* If your board really support the older PCI-X standard, I'd use one of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815121009") as they've worked great for me over the years.

---

### Post by darkapec on 2012-08-26
Hey rubylaser,

I was looking into purchasing that card. I currently have a [Koutech PSA421]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816104007")

I contacted them about warranty replacement because I believe the card is bad not the motherboard slot and they are in the process of issuing an RMA number. But for the time being putting the pci-x card in the pci slot should work.

I just dont understand whats going on. I know PCI is significantly slower, but it must be fast enough to still work because they do make PCI versions of that card. 

And sure enough, yesterday I purposely degraded the RAID, then readded the drive, it is currently rebuilding and I am able to access all data problem free. Once the rebuild has finished I will check IOSTAT and IOTOP. 

Logic says the raid would perform worse during a rebuild not better. So is this an issue of the data not being properly synced in the new drive?

---

### Post by darkapec on 2012-08-26
I inserted a 3com PCI card into the PCI-X slot, it was detected just fine. So I believe this problem is simply a faulty raid card. It has held up well for nearly 2 years now and it is still covered under warranty cant really be too upset about that. Hopefully Koutech has a seamless RMA procedure. 

I will check back in and let everyone know if replacement solves this issue. 

During the rebuild IOSTAT and IOTOP are reporting very low usuage. It does not appear anything is being bottlenecked. I will check again tonight when the rebuild has finished.

---

### Post by rubylaser on 2012-08-26
Good, glad to hear it.  Please keep me posted.

---

### Post by TheFu on 2012-08-27
Just to clarify, you had a RAID card, but were using software RAID?  Basically the RAID card was just doing JBOD?

---

### Post by darkapec on 2012-08-27
> **TheFu said:**
> Just to clarify, you had a RAID card, but were using software RAID?  Basically the RAID card was just doing JBOD?

Basically yes, the reasoning is my tyan server motherboard is from the AM2 era and it only supports drives up to 1tb. I rarely push this server to its limits so I could not justify buying a new motherboard / proc etc etc just to be able to use 2tb drives. So the solution was an IO card that supported 2tb drives. And my only options for pci-x were a few RAID cards.

---

### Post by TheFu on 2012-08-27
> **darkapec said:**
> Basically yes, the reasoning is my tyan server motherboard is from the AM2 era and it only supports drives up to 1tb. I rarely push this server to its limits so I could not justify buying a new motherboard / proc etc etc just to be able to use 2tb drives. So the solution was an IO card that supported 2tb drives. And my only options for pci-x were a few RAID cards.

I understand completely.  I had a Promise Fasttrak RAID card, but the Linux drivers were only for old kernels.  That card is supported as JBOD in current kernels at the time (and today), so JBOD-only for me too.  The last system hardware upgrade let me pull that card and connect to MB SATA ports - opening a slot for something else.

I was confused since you kept calling is a "RAID card", that's all.  You did say "mdadm" was used ... adding to my confusion.  Guess I'm just confused all around. ;)

---

### Post by darkapec on 2012-08-28
ok the rebuild finished two days ago and so far I have not had any issues with the fake RAID card in the PCI slot. Here is what I think caused the card to not work correctly in the PCI slot. 

I had a parallel card in another PCI slot causing the bus speed to be split between the two cards. According to the technical documentation of this TYAN server board all PCI slots are sharing the same bus and the PCI-X slot has its own dedicated bus. 

Koutech is still RMAing the card because it is still not being detected in the PCI-X slot. But at least my raid is working until the replacement card arrives. 

It is also worth mentioning that Koutech has been a pure pleasure. One of the best RMA procedures I have had to deal with. It is at times like these when a hardware company can truly win a spot in your heart. They have won my business for life. The only other company that has been this easy to deal with has been G.Skill. Sorry for the little rant there but its nice to know there are some company's that actually stand behind there products and will do whatever they can to make the customer happy. 

Thank you all for your input, but it looks like it was a hardware issue so I will go ahead and mark this thread solved.

---

