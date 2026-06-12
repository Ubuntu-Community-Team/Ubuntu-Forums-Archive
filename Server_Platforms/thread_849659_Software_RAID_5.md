---
title: "Software RAID 5?"
date: 2008-07-04
forum: Server Platforms
---

### Post by girasquid on 2008-07-04
Hello, all.

I am currently in the midst of deciding how I want to configure a new production box. I have had someone recommend to me that I use RAID 5, so that I am better protected against drive failures - and I can swap single drives out at any time I need to.

I was thinking of using Software RAID 5, by following the tutorial [here](http://bfish.xaedalus.net/?p=188).

Can software RAID 5 be used for my entire system? Are there any gotchas I need to be aware of before I do this?

Thanks,
Girasquid

---

### Post by cariboo on 2008-07-04
If you are putting this server into production, I would suggest going with hardware raid as all of the work is done on the adapter card and the management utilities are much better then software raid.

Jim

---

### Post by sjwk on 2008-07-04
The main gotcha with RAID5 is that it affects performance, particularly with the standard software RAID since the CPU has to do all the maths to ensure that all data can be reconstructed from the remaining disks.

Oh, and you should be ok if you're using SATA or SCSI disks, but if you're using PATA IDE and are using both primary and slave drives on each channel, bear in mind that if one disk fails it has a good chance of taking the second disk on that channel out too (especially if it was the master that failed).  And if you lose two disks in your array, that's everything gone...

From a performance perspective, there might be some advantage in just using RAID5 on the data areas - /home and so on, and keep the OS itself on regular disks, or RAID1.  I'd guess swap would be a bad idea on a RAID5 disk too.

Finally, I don't know how well the bootloaders cope with software RAID5, if at all.  The RAID driver isn't running at boot time so the BIOS probably can't cope with reading a kernel file from it so you may need to have /boot on a traditional disk, or maybe use a boot floppy/CD.  Not tried that myself though so I might be talking rubbish.

You could also look at a proper hardware solution.  They would typically present the array to the computer in the form of a single disk so booting shouldn't be an issue, and the processing is done on-card.  Performance still isn't as good as a straight disk, but at least it doesn't also hit the CPU.  I've got a 3ware card in one of my servers that was pretty reasonable and worked out of the box with ubuntu.

Steve.

---

### Post by girasquid on 2008-07-04
Thanks for the quick responses, everyone.

I've chosen software RAID over hardware RAID because with software RAID, I can at least be sent an e-mail if any of my disks are failing - something which, as far as I am aware, hardware RAID cannot do. As this box will be in a co-located facility, I would like to have it reporting to me if anything fails.

I am planning on using 3 SATA disks. The processor for this system will be a dual-core 2.2GHz AMD Athlon, which I've been told should handle software RAID just fine performance-wise - although if I'm wrong, please correct me sooner than later.

I recently had an issue with a mirrored system not being able to boot after disconnecting one of the drives, because of bootloader issues - is it safe to assume that bootloaders don't play nicely with RAID? If that's the case and I want to keep this system bootable, what should I do with my /boot partition? The overarching goal is to have 4 drives - 3 in RAID 5, and a last drive for backups of the data off of the other drives. Would it be safe to keep /boot and swap on the backup drive, or do I want yet another drive?

I'm only slightly experienced with Linux - how do I keep things like /home and /boot on separate drives, and still have it all work together? Is it just a matter of editing /etc/fstab(I've done that before), or something more complicated?

---

### Post by windependence on 2008-07-04
> **cariboo907 said:**
> If you are putting this server into production, I would suggest going with hardware raid as all of the work is done on the adapter card and the management utilities are much better then software raid.

Jim

Agree with cariboo here. Most large companies don't use software RAID and there is a reason. 

Yes, you can be sent an e-mail if you have the right monitoring software installed.


-Tim

---

### Post by doogy2004 on 2008-07-04
> **sjwk said:**
> Oh, and you should be ok if you're using SATA or SCSI disks, but if you're using PATA IDE and are using both primary and slave drives on each channel, bear in mind that if one disk fails it has a good chance of taking the second disk on that channel out too (especially if it was the master that failed).  And if you lose two disks in your array, that's everything gone...

I'm currently running raid with 1 SCSI disk and 2 ATA disks on the same channel and I completely forgot about this risk.  Thanks for remininding me.

---

### Post by ixus_123 on 2008-07-04
The problem with software RAID is should your OS ever bork on you (for example if you are hacked) you may need to have a fresh install and mount the old array for you to copy data from.

There are 2 problems I see here

1. the os is handling the RAID, which you can't boot into for whatever reason - how to access your data?

2. Physical space.  RAID 5 is a bit of a pain to expand so plan what disk you use well.  It can take hours to expand an array.

A quicker solution is to often image th virtual disk onto a new larger array. This can be sometimes limited by physical drive bays in the host computer as you'd need 6 to do it reliably but might be able to do it in 5


Whatever you decide to do, don't RAID replace having a regular backup schedule

---

### Post by promodus on 2008-07-05
> 
I've chosen software RAID over hardware RAID because with software RAID, I can at least be sent an e-mail if any of my disks are failing - something which, as far as I am aware, hardware RAID cannot do.

You need to be more aware as that's simply not the case.
A quick look at 3ware or even highpoint you'll see those sort of features are available.

---

### Post by girasquid on 2008-07-05
Thanks for pointing out that hardware RAID can notify me when a drive is failing.

Unfortunately, a hardware RAID controller is a little bit out of my price range - while I can afford the drives for RAID 5, I'm afraid I can't afford much else just yet. 

Does anyone know if it's possible to keep the entire OS on the RAID'd drives, or will I need to use another drive for the OS, swap, etc.?

I am looking at picking up [this motherboard](http://www.satacomputer.com/product.php?productid=4510&cat=55&page=1), which mentions RAID 5 in it's summary - does this mean that I will be able to set up hardware RAID 5 without buying a separate controller? If that's the case, I will definitely be looking into hardware RAID.

---

### Post by fjgaude on 2008-07-05
The raid that is on motherboards is usually called **fakeraid**, because the setup uses the CPU to do much of the work, XORing etc... you can use such for raid5 only if you use Windows, because there is no driver for Ubuntu or Linux in general. For raid0 and raid1 there is **dmraid**, and many use it successfully.

The controllers on the motherboard are usually used for the drives in a software raid setup under Ubuntu, using **mdadm**, which handles just about all the raid configurations, including raid5 and raid6, along with raid0, raid1, and raid10.

Considering hardware failure, if the motherboard dies so does all the things that it controls, including hardware raid cards, adapters. For small raid setups with six drives a modern multicore CPU running at 2.4GHz or higher and fast memory, 800MHz or faster takes care of the workload of raid5 nicely with usually plenty of clock cycles remaining for multitasking.

No matter what approach you take with raid always make backups of important data on an array. I make at least two, one onto another computer. It's a good idea to have really important data saved at another physical site. <sigh>

---

### Post by girasquid on 2008-07-05
Thanks for the information, fjgaude - that clears up a lot.

From what I can understand, you're telling me that Ubuntu/Linux won't be able to boot off of hardware RAID 5 at all - is software RAID the only other viable option that doesn't involve buying a RAID controller? Do you think it's an okay idea to have 1 drive that houses the OS, swap, and backups, and then 3 in RAID 5?

Thanks for clearing this up for me.

---

### Post by fjgaude on 2008-07-05
> **girasquid said:**
> Thanks for the information, fjgaude - that clears up a lot.

From what I can understand, you're telling me that Ubuntu/Linux won't be able to boot off of hardware RAID 5 at all - is software RAID the only other viable option that doesn't involve buying a RAID controller? Do you think it's an okay idea to have 1 drive that houses the OS, swap, and backups, and then 3 in RAID 5?

Thanks for clearing this up for me.

Yes, that's the hot-ticket to ride... boot from one drive and have all the data on the raid5. Backup to another drive... please! Having raid array is no protection really from failure, virus, etc. It does add speed and one-drive failure protection.

You might like to read this, especially to the end: [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

The more knowledge we have the better to serve.

---

### Post by girasquid on 2008-07-05
Thanks for the link - it's an interesting(and informative) read.

I'm still not really sure what to do, from a configuration point of view.

This box is going to be a web/subversion server, and I'd like to have as much protection as possible(backups, RAID, etc.) if Bad Things happen.

Does anyone have any recommendations? I had RAID 5 suggested, and now it's beginning to sound like what I want to do is this:

3 drives in RAID 5 (software)
1 drive for bootables
1 drive for backups

Is there a better way? Is there a more optimal configuration for a server?

---

### Post by fjgaude on 2008-07-05
Well, with four to five drives that's about as good as you can do. The bootable drive could be have a backup partition, meaning one less drive.

Use rsync, grsync, unison to backup often, daily. The raid5 with three drives will read data twice as fast as one drive, write it at about the speed of one drive.

With modern big drives, the fast kind using perpendicular heads, first or second generation, you could have a very large amount of storage that is reliable, somewhat fault tolerant, and you haven't spent much money.

Sounds good to me... maybe Tim (windependence) will have other suggestions.

Let us know how you are doing.

---

### Post by girasquid on 2008-07-05
Okay, thanks for the advice - if I were to put the backup partition onto the bootable drive and thus trim my requirements down to 4 drives, how long would it take to recover if it was the bootable drive that failed?

I'm looking at using 500GB SATA Seagate Barracudas for this, with 32MB cache - if that helps at all.

If I'm going to be doing software RAID, do I need to worry at all about finding a motherboard that does RAID5, or will the kernel and software be handling all of that for me?

---

### Post by fjgaude on 2008-07-05
> **girasquid said:**
> Okay, thanks for the advice - if I were to put the backup partition onto the bootable drive and thus trim my requirements down to 4 drives, how long would it take to recover if it was the bootable drive that failed?

[COLOR="Navy"]Well, it would take as long as it takes to install the OS. Maybe an hour...[/COLOR]

I'm looking at using 500GB SATA Seagate Barracudas for this, with 32MB cache - if that helps at all.

[COLOR="Navy"]That's the fastest SATA, 105MB/sec thru-put, you can buy. Good![/COLOR]

If I'm going to be doing software RAID, do I need to worry at all about finding a motherboard that does RAID5, or will the kernel and software be handling all of that for me?

[COLOR="Navy"]No, just get one that has enough SATA ports, most new ones have six or eight these days. And for sure you need to have those posts working off the PCI-E bus, which I think all new-generation MBs have. I think the Intel P35 types are the best, from all the studies I've seen.[/COLOR]


Anything more?

---

### Post by girasquid on 2008-07-05
As far as I know, that's about it - what do I gain by having the SATA posts work off of the PCI-E bus?

Are there any other special considerations I need to take into account for my intended usage(web/subversion server)?

Also, as one last concern - if I put my backups onto a backups partition on the bootable drive, what would you recommend if that drive happens to fail? I'd like to keep two weeks of backups available, and I'm a little concerned that if the bootable + backups drive failed, I wouldn't have that. Is offsite backups the best way around this, or is there a better/alternate approach?

---

### Post by fjgaude on 2008-07-05
> **girasquid said:**
> As far as I know, that's about it - what do I gain by having the SATA posts work off of the PCI-E bus?

[COLOR="Navy"]Speed, the newest drives are nearly as fast as the old PCI bus, at 133MB/sec. Your three-drive raid5 will have a read thru-put of about 210MB/sec.[/COLOR]

Are there any other special considerations I need to take into account for my intended usage(web/subversion server)?

[COLOR="Navy"]Nothing coming from me... Tim is the server guy around here. I'm the software raid person. <smile>[/COLOR]

Also, as one last concern - if I put my backups onto a backups partition on the bootable drive, what would you recommend if that drive happens to fail?

[COLOR="Navy"]Using the Ubuntu Server liveCD put the new OS on a partition the same size as before... for a server, likely no more than a 4GB partition works. Of course you need to have purchased a new drive first. Then copy all the raid5 data back to the newly created partition for backup on the boot drive. With the server OS you likely will use **parted**, **fdisk**, or **cfdisk** (the latter is the one I usually use) to partition and ready the drives. Make sure you make the raid disks **fd**, autodetect Linux raid, types.[/COLOR]

Sounds like you have lots of learning ahead of you... Good luck... there's always folks here that wish to help with issues and the like.

---

### Post by girasquid on 2008-07-05
Great - thank you for all the help.

It will be a week or two before I get the drives together and get to work on this, as I've blown through my equipment budget for this week getting the other bits together - but thanks for everything. You've cleared up a lot and given me a lot to chew on.

You mentioned using the liveCD to put the new OS onto a partition the same size as before - would it be wise to partition 5GB for the server, and then have 495GB left for backups, or would you recommend a different scheme?

---

### Post by fjgaude on 2008-07-05
Sure, 5GB for the system OS is fine... lots of room for updates and reducing the possible framentation that might come with many such updates.

With only 495GB for backup you might consider using the less expensive 250GB, 32-MB cache, Seagates for your three-drive raid5 array. The NT drives over the AT versions has been stated by Seagate to be fine for servers and their needed reliability. The price is almost the same between the two.

All the 32MB-cache Seagates are of the second-generation type, 105MB/sec versus 70 thru-put.

Is this a home project or for customers, clients?

---

### Post by girasquid on 2008-07-05
I'm planning on using it as the server behind a customer/client based offering eventually - although right now, it's more of a home project until it's set up the way I want it to be.

The 500GB drives were chosen because that way I was relatively sure that it would take me a long time to run out of space via web/subversion usage - as this is going to be a server for a web-app more than hosting, I only have to worry about my own hard-drive usage.

---

### Post by fjgaude on 2008-07-05
Okay, go for it... and good luck in whatever you try, do.

---

### Post by windependence on 2008-07-05
> **girasquid said:**
> Thanks for the information, fjgaude - that clears up a lot.

From what I can understand, you're telling me that Ubuntu/Linux won't be able to boot off of hardware RAID 5 at all - is software RAID the only other viable option that doesn't involve buying a RAID controller? Do you think it's an okay idea to have 1 drive that houses the OS, swap, and backups, and then 3 in RAID 5?

Thanks for clearing this up for me.

Well yes, if it was hardware RAID you certainly could boot from that drive but I wouldn't suggest it. You should try to keep your OS dirve separate. You could use a very small dirve for the OS (I have some 8 gig drives here) and then put your data on the RAID array. I ususally put my document roots on the RAID for faster access time.

Certainly it would be OK to set it up the way you are suggesting. The cahnces of all your drives going at once are slim. If your OS/backup drive goes, you still have your data on the RAID array, although I would prefer to see hardware RAID here as it would be faster to recover if your OS drive went bad. With software RAID, you would have to rebuild your array once you had the OS reloaded after a failure. You might want to take an image of that drive once you get it set up the way you want it so that if you did have a failure, you coud just image the new drive and be in business fast.

-Tim

---

### Post by vpsville on 2008-07-06
> **girasquid said:**
> 
Does anyone know if it's possible to keep the entire OS on the RAID'd drives, or will I need to use another drive for the OS, swap, etc.?


You can definately put the entire OS on a RAID array.  

A software raid doesn't just fail when 2 disks go down, it also fails if the bios has a bug, or if the motherboard fries, or if the memory has errors etc.  Even an overheating machine can screw up a software raid beyond repair.

Whatever you have, make sure you back it up onto another machine, it may save your sanity some day.

---

### Post by windependence on 2008-07-06
Excellent points. I know we have some software RAID fans here, but consider this: enterprises don't use software RAID. I have worked for several Fortune 500 companies and NONE of them has ever considered this. I think it's fine for a hobby or home server, but for mission critical stuff, and this includes any business stuff, spring for the hardware controller.

-Tim

---

### Post by fjgaude on 2008-07-06
We can see that experience with software raid is sometimes lacking... **mdadm** is solid... we can have the motherboard fail, take out the array drives put them into another MB into random controller slots, make sure mdadm is loaded and do an **--assemble --scan** and the array is up and running. No rebuilding, re-sync necessary.

Any hardware failure from CPU, power supply, motherboard, will take down simple hardware or software raid. By simple we point to non-cluster, auto mirroring of whole servers, etc.

For small installations software raid is the inexpensive way to go. A raid card costs over $300 and is no more reliable than going the full software route, in fact we have now added another complex hardware failure point. I do believe we are dealing with having to educate ourself with how mdadm works and how to use its features. It took me months to fully understand how to handle all the situations we came across... with hardware raid I never had such issues, it was easy.

---

