---
title: "When will we get the 4 TB or 10 TB harddisks ?"
date: 2010-12-11
forum: The Cafe
---

### Post by honeybear on 2010-12-11
Need some space, more space. Visibly 4 TB can be bought already, but man, 10 TB, for when?

---

### Post by cascade9 on 2010-12-11
You cant get a single 4TB HDD.....yet. Sometime in 2011 it should be possible, hitachi has already said they will have 4TB drives out in 2011 (and I'd bet that seagate and WD wont be far behind). 

No idea on when a 10TB single drive will be out, maybe 2016-2017?

---

### Post by Lucradia on 2010-12-11
> **cascade9 said:**
> You cant get a single 4TB HDD.....yet. Sometime in 2011 it should be possible, hitachi has already said they will have 4TB drives out in 2011 (and I'd bet that seagate and WD wont be far behind). 

No idea on when a 10TB single drive will be out, maybe 2016-2017?

You can get 20 TB for 1200 USD *snicker*

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136691](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136691)

---

### Post by forrestcupp on 2010-12-11
I just bought a 2TB external eSATA drive from Best Buy's web site for $109.  I remember spending at least $80 for a 100 GB hard drive back in the day.  It's amazing how things change.

I'm putting all of my DVDs on there.  It's hooked up to my main TV, and I can stream them over to my Xbox 360 on my 2nd TV.  Pretty cool.  I spent a lot of money just so I can be lazy. :)

---

### Post by wojox on 2010-12-11
> **Lucradia said:**
> You can get 20 TB for 1200 USD *snicker*

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136691](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136691)

That's one hell of a RAID you'd be building there. ;)

---

### Post by Donalt2010 on 2010-12-11
> **forrestcupp said:**
> I'm putting all of my DVDs on there.  It's hooked up to my main TV, and I can stream them over to my Xbox 360 on my 2nd TV.  Pretty cool.  I spent a lot of money just so I can be lazy. :)

I actually lol'd there for some reason, I like your way of thinking dude:)

---

### Post by oldfred on 2010-12-11
Windows is the bottleneck. Motherboard also need updating to UEFI. 

Apple is already all efi/gpt except when you dual boot windows and then it does a kludge of part MBR within a gpt drive.

XP only works on MBR and MBR partitioning has a hard limit of 2TiB. Even Win7 will only boot from gpt if the motherboard uses efi not BIOS.

While Linux has worked with gpt for a while, its support was not great. The just updated grub2 to work better with efi & grub2, but I am not sure if it is 100% yet. I boot BIOS with gpt without any issues.

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

---

### Post by honeybear on 2010-12-11
> **oldfred said:**
> Windows is the bottleneck. Motherboard also need updating to UEFI. 

Apple is already all efi/gpt except when you dual boot windows and then it does a kludge of part MBR within a gpt drive.

XP only works on MBR and MBR partitioning has a hard limit of 2TiB. Even Win7 will only boot from gpt if the motherboard uses efi not BIOS.

While Linux has worked with gpt for a while, its support was not great. The just updated grub2 to work better with efi & grub2, but I am not sure if it is 100% yet. I boot BIOS with gpt without any issues.

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)


wow thats not a good new what you say... I hope that grub2 can handle the 4 tera bytes...

---

### Post by CharlesA on 2010-12-11
The only way I've been able to get a 4TB partition is to use RAID. My OS drive is still on a small(ish) drive.

Anyway, we won't see single drives that large for a while.

---

### Post by cptrohn on 2010-12-11
Newegg is selling a 3TB HD now.  Not sure how it would with Ubuntu? from reading some of the reviews you have to have a 64 bit OS for it to work?  Not sure really.. but the 3TB is available to buy.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136764](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136764)

---

### Post by Dustin2128 on 2010-12-11
My guess? No later than 2014-Q2 2015

---

### Post by Lucradia on 2010-12-11
> **cptrohn said:**
> Newegg is selling a 3TB HD now.  Not sure how it would with Ubuntu? from reading some of the reviews you have to have a 64 bit OS for it to work?  Not sure really.. but the 3TB is available to buy.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136764](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136764)

That PCI bracket is a RAID conversion unit, your PC can't handle 3TB, it's why they gave you it.

---

### Post by cptrohn on 2010-12-11
> **Lucradia said:**
> That PCI bracket is a RAID conversion unit, your PC can't handle 3TB, it's why they gave you it.

?  I don't have one, I was just stating that they are selling one, and from reading the reviews it won't work at all with 32 bit versions of windows at all?

---

### Post by NCLI on 2010-12-11
Just buy six cheap 2TB HDDs and hook them up in RAID5.

Oh, lookit that, I have an 8 TB HDD, and in a week, I'll have a 10 TB HDD :KS

```
Disk /dev/md0: 8001.6 GB, 8001584889856 bytes
2 heads, 4 sectors/track, 1953511936 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 262144 bytes
Disk identifier: 0x00000000

```

So your answer is: Now. ;)

---

### Post by forrestcupp on 2010-12-11
> **Donalt2010 said:**
> I actually lol'd there for some reason, I like your way of thinking dude:)

Well, if you're talking about me being lazy, it wasn't really good thinking.  It takes *a lot* of time and work to rip 120 DVDs to a hard drive.  I think I have about 10 or 12 done so far.  It's still awesome, though. ;)

---

### Post by CharlesA on 2010-12-11
> **forrestcupp said:**
> Well, if you're talking about me being lazy, it wasn't really good thinking.  It takes *a lot* of time and work to rip 120 DVDs to a hard drive.  I think I have about 10 or 12 done so far.  It's still awesome, though. ;)

I've ripped the 200 something dvds I've got and it took a long, long while.

Haven't even touched any of the TV series I have on dvd either, just the movies.

---

### Post by MisterGaribaldi on 2010-12-12
I remember reading as a kid the novel to Star Trek II. There was a scene in there between Carol and David Marcus where they were talking about the size of the software they'd written for the Genesis project, and when one or the other had commented the software was 20 megabytes, someone exclaimed "Jesus! The program that swallowed Saturn!"

The funny thing is that so many things are larger than 20 MB now it isn't funny. I was just d/l Firefox Mobile tonight and it's 22 MB (well, the installer is).

So, I wonder what this says about the bloat trend in the future... :P

---

### Post by asifnaz on 2010-12-12
> **MisterGaribaldi said:**
> I remember reading as a kid the novel to Star Trek II. There was a scene in there between Carol and David Marcus where they were talking about the size of the software they'd written for the Genesis project, and when one or the other had commented the software was 20 megabytes, someone exclaimed "Jesus! The program that swallowed Saturn!"

The funny thing is that so many things are larger than 20 MB now it isn't funny. I was just d/l Firefox Mobile tonight and it's 22 MB (well, the installer is).

So, I wonder what this says about the bloat trend in the future... :P
Mr. Bill Gates said in 1984 :
  The largest                                        hard disk we will ever require is 16 MB

---

### Post by cascade9 on 2010-12-12
> **Lucradia said:**
> You can get 20 TB for 1200 USD *snicker*
  
  [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136691](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136691)
  
  *snicker* You obviously missed 'single drive'. Its been possible to build 10TB RAID arrays for years, and even longer for 4TB, so I dont think that RAID arrays is what the OP was asking about.  
  
 > **oldfred said:**
> Windows is the bottleneck. Motherboard also need updating to UEFI. 
 
 Apple is already all efi/gpt except when you dual boot windows and then it does a kludge of part MBR within a gpt drive.
 
XP only works on MBR and MBR partitioning has a hard limit of 2TiB. Even Win7 will only boot from gpt if the motherboard uses efi not BIOS.
 
 While Linux has worked with gpt for a while, its support was not great. The just updated grub2 to work better with efi & grub2, but I am not sure if it is 100% yet. I boot BIOS with gpt without any issues.
 
 GPT info
 [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
 [http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
 MBR details including 2TiB limit and GPT link
 [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
 [http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
 
 Yes, all true. Well, you dont need UFEI to run the 3TB WD drives (thats why they give you a host bus adapter with the drives) 

> **CharlesA said:**
> The only way I've been able to get a 4TB partition is to use RAID. My OS drive is still on a small(ish) drive.

Anyway, we won't see single drives that large for a while.

From what hitachi was saying in may 2010, they should have 4TB drives out already. Obviously they've hit some snags, but AFAIK they are on track for a release sometime in 2011. Not that far away at all.

> **cptrohn said:**
> ?  I don't have one, I was just stating that they are selling one, and from reading the reviews it won't work at all with 32 bit versions of windows at all?

Newegg reviews are untrustable. The 3TB drives will work with 32bit vista and win7 (not as a boot drive though), just not XP at all (even 64bit XP). 

[http://www.storagereview.com/western_digital_caviar_green_3tb_review_wd30ezrsdtl](http://www.storagereview.com/western_digital_caviar_green_3tb_review_wd30ezrsdtl)

---

### Post by CharlesA on 2010-12-12
> **cascade9 said:**
> 
From what hitachi was saying in may 2010, they should have 4TB drives out already. Obviously they've hit some snags, but AFAIK they are on track for a release sometime in 2011. Not that far away at all.

Nice. I remember someone saying that they had hit the limit with 512byte sectors, which is why they moved over to 4096byte sectors.


> [http://www.storagereview.com/western_digital_caviar_green_3tb_review_wd30ezrsdtl](http://www.storagereview.com/western_digital_caviar_green_3tb_review_wd30ezrsdtl)

Thanks for the link. :)

---

### Post by Paqman on 2010-12-12
> **NCLI said:**
> Just buy six cheap 2TB HDDs and hook them up in RAID5.


+1.

If you want lots of storage, a big RAID array on your network is a much better way to go than trying to stuff moosive disks into a single machine. They're scalable, accessible to your whole network, faster, redundant, and you can slap a blindingly fast little SSD into the client machines. Much better way to compute IMO. 

Redundancy is a biggy for me, too. I don't trust spinning hard drives as far as I can throw em. There's no way i'd put important data onto a single drive.

---

### Post by CharlesA on 2010-12-12
> **Paqman said:**
> 
Redundancy is a biggy for me, too. I don't trust spinning hard drives as far as I can throw em. There's no way i'd put important data onto a single drive.

That's my thing as well, I've known a few people who have lost data when their drive went out (and they didn't have backups -.-)

In my case, I save stuff to the local machine, which is synced with my server and then copied to backup media..

I've got issues. :lolflag:

---

### Post by Paqman on 2010-12-12
> **CharlesA said:**
> 
In my case, I save stuff to the local machine, which is backuped to my server and then copied to backup media..


I trust the RAID array on my NAS to cover for single point failures of drives, and I mirror the array to a spare drive once a month to cover for a failure of the NAS's RAID hardware/software. I should be doing it to an offsite location really, but i've not found an economical offsite solution for 750GB of data.

---

### Post by CharlesA on 2010-12-12
> **Paqman said:**
> I should be doing it to an offsite location really, but i've not found an economical offsite solution for 750GB of data.

Same here. The closest I can get is throwing my data on an external drive and placing it somewhere offsite. 

If I was actually doing that, I'd definitely want to encrypt the backups.

---

### Post by NCLI on 2010-12-12
> **CharlesA said:**
> That's my thing as well, I've known a few people who have lost data when their drive went out (and they didn't have backups -.-)

In my case, I save stuff to the local machine, which is synced with my server and then copied to backup media..

I've got issues. :lolflag:
Just setup a RAID6, that should give you plenty of redundancy.

---

### Post by CharlesA on 2010-12-12
> **NCLI said:**
> Just setup a RAID6, that should give you plenty of redundancy.

Server is running RAID5 atm, I don't really have any reason to move to RAID6 (yet). ;)

---

### Post by The Real Dave on 2010-12-12
Theres gonna be a limit to how bit a magnetic harddrive can get. There's only so dense a platter can be and only so many platters that can be put in a drive without it becoming ridiculous. 

Solid state though, will keep getting bigger and bigger.

On a side note, I just picked up a 1TB WD Green for €61 :P

---

### Post by talz13 on 2010-12-13
> **The Real Dave said:**
> Theres gonna be a limit to how bit a magnetic harddrive can get. There's only so dense a platter can be and only so many platters that can be put in a drive without it becoming ridiculous. 

Solid state though, will keep getting bigger and bigger.

On a side note, I just picked up a 1TB WD Green for €61 :P

This just in! 5.25" hard drives make a comeback!

---

### Post by Spice Weasel on 2010-12-13
> **talz13 said:**
> This just in! 5.25" hard drives make a comeback!

I'd pay extra for a 5.25" drive with a built in heatsink and fan. It would be beastly and probably last much longer.

---

### Post by The Real Dave on 2010-12-13
> **Spice Weasel said:**
> I'd pay extra for a 5.25" drive with a built in heatsink and fan. It would be beastly and probably last much longer.

You can get little 5.25 cradles for 3.5 inch drives, with fans, often with controllers and screens on the front

---

### Post by cascade9 on 2010-12-14
> **Spice Weasel said:**
> I'd pay extra for a 5.25" drive with a built in heatsink and fan. It would be beastly and probably last much longer.

I wouldnt want a fan, but a heatsink might be nice. Though I just use old slot 1 celeron 266 heatsinks on my hdds now :lolflag: 

BTW, if they did move back to 5.25'' HDDs I'd guess we would be pushing 6-7TB for single drive now. Transfer speeds on the outer part of the platter would be insane for a mechanical HDD as well.....

---

