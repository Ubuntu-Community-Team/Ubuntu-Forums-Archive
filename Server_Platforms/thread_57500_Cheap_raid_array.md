---
title: "Cheap raid array?"
date: 2005-08-16
forum: Server Platforms
---

### Post by spacemonkey on 2005-08-16
I've got a server with a few hard drives hooked up to it.  It's an old P2 server.  I use it mostly to store backups, but it also host an extremely low traffic webserver and a streaming media server.  I was in circuit city the other day and I noticed an extremely inexpensive raid card that supports 4 ATA drives.  I was wondering a few things:

First, would it be worth it to me to use raid for extra protection of my data?  Like I said, this server isn't hosting anything terribly important, mostly just backups of my desktop files and music files.  I'd hate to lose them, but it wouldn't be the end of the world for me or anything.

Second, can I hook up different sized drives to the raid card, or do they all have to be identical drives?  I have a few harddrives in the server, but they are all different sizes (hand me downs I got from old PCs, which is the reason I want raid, in case one fails on me).  I would also be adding atleast one, maybe two more drives to the raid for extra storage, if I am able to connect different sized drives.

As you can tell, I don't know a whole lot about RAID devices.  I think i could manage to set it up with some searching on the net and these forums.  My last question is....this raid device was a PCI card, that had two ATA plugs on it, each supporting two drives.  It looked kind of old, but not ancient.  It was only about $25, which is one thing that concerns me.  Am I going to be worse off storing my data on a really cheap raid device than I would be on old harddrives?

Thanks in advance for comments.


Oh, and one more thing, I know a cheapass ATA raid is going to be really slow, and not the greatest thing in the world, but as I said, this isn't a high performance server by any means, as long as it can hold my data without crashing, I'll be fine.

---

### Post by relix42 on 2005-08-16
[QUOTE=spacemonkey]First, would it be worth it to me to use raid for extra protection of my data? [/QUOTE]
This is really up to you.  Personally, I hate to lose data to drive failure no matter what the data.  And, you mentioned you store backups here - seems like that might be important.

[QUOTE=spacemonkey]Second, can I hook up different sized drives to the raid card, or do they all have to be identical drives?[/QUOTE]
All the hardware RAID cards I've seen (especially the cheap ones) require the drives to be the same size.

The other thing to watch it which chip set the RAID card uses.  Promise makes some rather cheap RAID cards, however, they're crap.

[QUOTE=spacemonkey]As you can tell, I don't know a whole lot about RAID devices.  I think i could manage to set it up with some searching on the net and these forums.[/QUOTE]
Once the hardware RAID card is setup correctly, it looks like one big drive to the OS.  So, if you can get the hardware going, the Linux side is simple.

[QUOTE=spacemonkey]My last question is....this raid device was a PCI card, that had two ATA plugs on it, each supporting two drives.[/QUOTE]
Normally, you only want one ATA device per channel in a RAID configuration because only one device can talk at a time.  So, the RAID card you saw may only support two devices - making it a RAID0/1 card.

---

### Post by Soleil-Raid on 2005-08-16
Firstly, inexpensive RAID cards are inexpensive for a reason. If it doesn't have a chunk of onboard ram, and it's own CPU, then it's almost certainly a software RAID controller with some very slow BIOS code to allow you to boot off it. My company recently purchased one of these, and I returned it, because the Linux software RAID built in to the kernel (md) was faster, easier to troubleshoot, and more importantly, didn't require closed drivers*.

If you want a bonafida RAID array, you'll have to use drives of the same size. However, there is help - LVM lets you chain a bunch of drives together, and run a RAID array on top of that, so if you happened to have say, 2x13GB, 1x80 GB, and 2x40 GB drives, you could use LVM to create two 'virtual' drives of 93 GB each, and run RAID1** across those two virtual devices. LVM disc1 being 1x13GB, and the 2 40GB's, and the other disc being a 13 and an 80 GB.

The big problem with having lots of ATA drives on a P2 is that you end maxing out your PCI bus. Most computers from that era (and IIRC many K7 and P4's) attach the ATA controller to the PCI bus, which has  a hard limit of 133 MB/Second***. This sounds like a lot until you have four drives in a RAID5 software array hammering away at the PCI bus. This isn't fatal, but is something to keep in mind.

Finally, if you do go down the RAID route, there's a bit in the howto where they talk about only attaching one drive to each port. I've tried it, they aren't kidding. It's _really_ slow if you have two drives on a cable, and one of them is RAID'd.

* I'm not normally too worried about closed drivers, but when it comes to something as important and simple as storage, I tend to distrust companies whose code is too crap to let into the open.

** I think LVM has stuff to do this automagically when it comes to mirroring. 

*** 64bit / and faster than 33 MHz PCI buses not withstanding. These don't tend to turn in most PC's though.

---

### Post by spacemonkey on 2005-08-16
Well I didn't think software raid would be an option, due to the slow PC.  I'll go back to circuit city tonight and read a little more about the device they had.  Find out if it is really hardware raid or not.  I'll also check to see if it requires the same sized drives.  because if it does, I may not be able to do this, as I don't want to drop a ton of cash on it.  One thing I know for certain about the device however, is that it said you could attach 4 drives on the two ATA plugs, whether or not that causes an extreme slow down like your talking about, I don't know.  I'll post again when I get back.

---

### Post by LordHunter317 on 2005-08-16
[QUOTE=spacemonkey]  I was in circuit city the other day and I noticed an extremely inexpensive raid card that supports 4 ATA drives.[/quote]This isn't a real RAID card, so don't even bother with it. 

If you're not willing to shell out ~$300 USD, just use the kernel MD RAID driver.

> First, would it be worth it to me to use raid for extra protection of my data? Generally, it's useful for online data.  It means you can stay up and running even when a disk fails.

That being said in a home, I wouldn't use it on a machine that's mostly being used as a backup staging device.  You're are taking backups to tape or CD/DVD and saving them aren't you?

> I'd hate to lose them, but it wouldn't be the end of the world for me or anything.Hrm, sounds like you're not.  Better investment is tape or a DVD+-RW drive and a boatload of media.


> Second, can I hook up different sized drives to the raid card, or do they all have to be identical drives?It's pointless if they're not the same size, and for max performance, they should all be the same model drive.

[quote=Soleil-RAID]However, there is help - LVM lets you chain a bunch of drives together, and run a RAID array on top of that, so if you happened to have say, 2x13GB, 1x80 GB, and 2x40 GB drives, you could use LVM to create two 'virtual' drives of 93 GB each, and run RAID1** across those two virtual devices. LVM disc1 being 1x13GB, and the 2 40GB's, and the other disc being a 13 and an 80 GB.[/quote]And get terrible performance to boot, plus I wouldn't trust RAID 's semantics in this situation to work in this situation.

> This sounds like a lot until you have four drives in a RAID5 software array hammering away at the PCI bus. This isn't fatal, but is something to keep in mind.The reality is that having two drives on the same IDE channel is a bigger performance problem.

---

### Post by spacemonkey on 2005-08-16
Well I'm not going to shell out $300 for it, as I said, it's not that important.  As I said, performance isn't a huge issue.  I don't want it to be terribly slow, but this being on a P2 machine, I don't think I little performance hit will be that big of a problem.  

Anyways, I went back to the store.  It's an Adaptec 1200A, [newegg](http://www.newegg.com/Product/Product.asp?Item=N82E16816103134)  has it for 50, but circuit city had it for 19, which is why it caught my eye.  Also, if this card is crap, or will be worse than software raid on my P2, would getting a PCI ATA card work for me?  I could run one or two drives off the motherboard (without doubling up on the IDE plugs), then a 3rd and 4th on the PCI ATA card.  Something like that anyways.  What exactly does the software raid do?  Remember it's a P2, and I've got no intention of upgrading that, as this is a free machine I put together from spare parts.

Thanks for the help!

---

### Post by Rohan on 2005-08-17
> If you want a bonafida RAID array, you'll have to use drives of the same size. However, there is help - LVM lets you chain a bunch of drives together, and run a RAID array on top of that, so if you happened to have say, 2x13GB, 1x80 GB, and 2x40 GB drives, you could use LVM to create two 'virtual' drives of 93 GB each, and run RAID1** across those two virtual devices. LVM disc1 being 1x13GB, and the 2 40GB's, and the other disc being a 13 and an 80 GB. 

Would this be possible with RAID 5, once you lose a drive.. how will you get the LVM virtual drives rebuilt?

---

### Post by nad on 2005-08-20
I have found cheap adaptec controllers better than other manufacturers. Even if you do not use the raid features of this card, having two more IDE channels for $19 is a good deal.

Keep in mind that using software raid, you are combining partitions, not drives, into the raid level of your choice (I assume raid1 is what you wish to do), therefore, size, make, model, geometry and manufacturer are not an issue. As a matter of fact, some admins will swear by using drives from different manufacturers to further reduce the possibility of data loss from failure due to a batch of poor drives.

So, the combination of 2 additional IDE channels and software raid is a great solution.

---

### Post by LordHunter317 on 2005-08-21
[QUOTE=nad]Keep in mind that using software raid, you are combining partitions, not drives, into the raid level of your choice (I assume raid1 is what you wish to do), therefore, size, make, model, geometry and manufacturer are not an issue.[/quote]Just not true.

Try building a RAID array using two partitions of different sizes: the extra space in the larger partition will simply be wasted.

Make/model still matter for optimum performance.  Of course, if you need that, you should be using hardware RAID anyway.

---

### Post by nad on 2005-08-21
[QUOTE=LordHunter317]Just not true.

Try building a RAID array using two partitions of different sizes: the extra space in the larger partition will simply be wasted.

Make/model still matter for optimum performance.  Of course, if you need that, you should be using hardware RAID anyway.[/QUOTE]

I may not have been clear here, but I was referring to drives, not partitions, in my reference to size.

"Make/model still matter for optimum performance." Huh? If he was truly interested in optimum performance, yes. He would shell out ~USD300 for a true raid card and a set of state-of-the-art scsi drives. HIs interest here is to optimize his existing equipment at minimal cost.

---

### Post by LordHunter317 on 2005-08-21
[QUOTE=nad]I may not have been clear here, but I was referring to drives, not partitions, in my reference to size.[/quote]No, that was clear and you're still wrong.

Partition size does matter.  Yes, Linux MD RAID doesn't require the drives to be the same size (unless you use the whole drive as the underlying physical device), but it does requires the partitions to be the same size.

If you provide it with physical devices (be it partitions or whole drives) that are different sizes, then the only the size of the smallest space will be used on **all** devices.

Yes, this does mean that if you have a 80GB drive and a 120GB, you can use 80GB of the 120GB for RAID and the last 40 for something else, if you really wanted to.  But if you use the whole disk for both (or 1 big partition), you'll waste 40GB.

So no, partition size does matter very much.

---

### Post by nad on 2005-08-21
Are you being deliberately obtuse lordhunter or do you just like to see yourself in print.

This is a thread about hardware use, not specific technique to implement a configuration.

My reference to size regarding drives stands on its own. Your implication that I was refering to partition size is immaterial.

---

### Post by LordHunter317 on 2005-08-21
[QUOTE=nad]Are you being deliberately obtuse[/quote]No, but I'm beginning to think you are.

> This is a thread about hardware use, not specific technique to implement a configuration.And I didn't talk about anything specific.  What I said applies to all cases.

> My reference to size regarding drives stands on its own.No, that's not what you said:> Keep in mind that using software raid, you are combining partitions, not drives, into the raid level of your choice (I assume raid1 is what you wish to do), therefore, **size**, make, model, geometry and manufacturer are not an issue (emphasis mine).Which gives the impression the size of the drive **and** the partition don't matter at all, when in fact, it does.  Which one matters is totally dependent on what devices you place in your array.

You may not like that, but it's truth.  In logical terms, it does not follow just because Linux MD RAID can use partitions as physical devices, that the size of the disk the partition is on does not matter.

This (which is what your post claims) can be easily disproven: one does not have to use partitions as physical devices, and MD will use only the size of the smallest physical device in an array on all devices. 

If you try to use /dev/hda (120 GB) and /dev/hdb (80GB) as RAID devices, which is legal, you will waste 40GB of space in /dev/hda.

Size does matter, depending on what you want to do.  Even still, your post would be alot more clear and nonconfusing had you made it clear that when using partitions, the partitions should be the same size.  It's not clear from your post you understand that, and people believe really dumb things about RAID, so it's really paramount to be as clear and explicit as possible.

> Your implication that I was refering to partition size is immaterial.I umm, never implied you were.  I think I very clearly noted that you were talking about the physical drive and that you were wrong **anyway**.

---

