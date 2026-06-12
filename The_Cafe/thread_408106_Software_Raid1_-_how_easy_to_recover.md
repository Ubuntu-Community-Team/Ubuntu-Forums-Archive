---
title: "Software Raid1 - how easy to recover?"
date: 2007-04-12
forum: The Cafe
---

### Post by fotski on 2007-04-12
Hi all,  I understand the concepts of RAID1 and am looking at setting up Ubuntu 6.10 at home as network server.  On it I'm planning to setup 2 160Gig disks with RAID1 - setup is not an issue (practised in vmware server :D) 
The raid drives will hold everyone's pictures, music and documents.

My query is:
What if for some reason the drive that holds ubuntu runs off died (which I don't plan to mirror)?
How would i be able to access the data on these drives?

Would I be able to mount them on another system and access the data?

EDIT: ok after reading my question again I realised I could have tested this in VMware too!  I will try and test if I get time over the next few days but if someone has a quick answer or link to an answer apreciate it ...

---

### Post by Polygon on 2007-04-13
RAID 1 means that if you have two hard drives, whatever is on hard drive one will be mirrored exactly on hard drive two

so if hard drive one dies, then you can use hard drive two as its a complete and exact mirror of hard drive one

so if you have ubuntu + music/files/pics/videos/whatever on hd1, and you have set up raid 1 correctly if it dies, your data is still mirrored and safe, i think you just swap out the drives and get a new one, it might be a bit slow at first as it has to mirror a lot of data to a fresh drive, but it should work fine

---

### Post by fotski on 2007-04-13
yes thats true, I understand that concept.
My query is more what if the pc I had my raid disks on died?
If I then mounted the original drives or just one of the original drives on another pc - can I and how would I recover the files on it?
Could I just mount it as a normal drive?

---

### Post by dmizer on 2007-04-13
i've not ever had to do this, but you can test it yourself by putting an ubuntu live cd in and booting to it.  the effect will be the same and you won't have to pull the drives out.  boot to your live cd and see what it's like to browse the drives configured with software raid.

that said ... i suggest against using raid of any kind.  raid 1 instantly backs up any changes, so if a file is accidently deleted ... it's STILL accidently delteted.  there was a fantastic article i read on this a while back ... wish i could find it again.  but basically all you're looking at with a raid1 server is a server with half the space and twice the cost.

---

### Post by kragen on 2007-04-13
ha, I remember the headaches I had trying to get a software raid-0 working with ubuntu! :D So many guides, but it was still a massive headache.

The joke is that now I fully understand it, and it really couldn't be simpler, although half of the problem was that all the tools and commands used in the guides were based on something other than mdadm...

I might have to have a go at writing something up myself...

---

### Post by dmizer on 2007-04-13
found the article ... [http://www.pugetsystems.com/articles?&id=29](http://www.pugetsystems.com/articles?&id=29) give it a good read if you're seriously considering using raid.  especially if you're considering using software raid rather than hardware raid.

---

### Post by RandomJoe on 2007-04-13
dmizer, I read the article and I would agree with it only to a point - certainly for most people it isn't worth having a _hardware_ RAID configuration.  Going software RAID drops the cost and part count that much more, so it's less "overhead".  Note I mean true software RAID handled 100% by the kernel, _not_ "FakeRAID" using the cheesy RAID chipsets on many motherboards!  

Personally, I still think RAID is worth it in certain situations.  The cost of a second hard drive to mirror my desktop is very low, and it gives me full protection from one drive dying.  Sure, I'm SOL if the machine itself craters or both drives get zapped, but that's not the typical failure mode I see.  Granted, I also very seldom see hard drive failures, but unlike the article's suggestion the warning I get from a drive before it does die is seldom soon enough - I have almost always found some files that were lost before I noticed the signs the drive was dying.  I _have_ had a drive in my server's RAID5 array die one day while I was at work.  But everything kept going on the other three drives, I replaced it and rebuilt the array.  No loss at all.

As to the original question, I have moved my RAID5 array between computers without issue.  Being software RAID, it isn't dependent on any particular controller.  The partitions are given the 'fd' Linux RAID partition type and the kernel recognizes them and does the right thing.  Haven't done that with a RAID1, but it shouldn't be any different.  (You may not be able to boot from it, of course.  I usually have a separate boot drive for the OS, although this desktop boots off the RAID1 array as well.)

But I do still backup everything to another archive.  My desktop and laptop get backed up to an archive directory on the server's RAID array.  And data that lives only on the server gets backed up to a couple of Firewire drives.  (The array is 1TB, so I need more than one.)

---

### Post by dmizer on 2007-04-13
> **RandomJoe said:**
> dmizer, I read the article and I would agree with it only to a point - certainly for most people it isn't worth having a _hardware_ RAID configuration.  Going software RAID drops the cost and part count that much more, so it's less "overhead".  Note I mean true software RAID handled 100% by the kernel, _not_ "FakeRAID" using the cheesy RAID chipsets on many motherboards!

well, what the article says to that ... and what i agree with is ... if you're not willing to put up the money for real hardware raid, then perhaps your need for a raid array is not so urgent as to validate it's use (kernel based software raid or otherwise).  in such a case, it's cheaper and just as secure to make regular archival backups to dvd or other static media ... which (as you've pointed out) you should be doing anyway.

i also get the impression (no real proof) that raid has a tendency to make casual admins easily procrastinate on their static archives because it gives a feeling of security that doesn't necessarily exist.

to be sure ... there ARE situations where raid is a benefit.  but i would argue that such situations should be able to justify the investment in a hardware solution.

---

### Post by saulgoode on 2007-04-13
> **dmizer said:**
> well, what the article says to that ... and what i agree with is ... if you're not willing to put up the money for real hardware raid, then perhaps your need for a raid array is not so urgent as to validate it's use (kernel based software raid or otherwise)

I disagree. How is "real hardware RAID" better than software RAID? Maybe in the Microsoft world it would be, but under Linux all that software RAID implementation requires is editing two files (RAIDTAB and one of your startup RCs). The processor load demanded is quite negligible (certainly made up for with increased throughput). As opposed to H/W RAID, there is no risk of the H/W failing, you can have dynamic resizing (with LVM), and it is much easier to recover your data (without having to worry about one-off or even proprietary partition formats).

The article makes some good points and I would tend to agree with it for users who are not interested in the administration aspects of their machine (and certainly this would apply to the customers of Puget Systems); but S/W RAID is a powerful tool which allows Linux users to fine-tune their system and eliminate one of the biggest bottlenecks for data manipulation.

---

### Post by dmizer on 2007-04-13
> **saulgoode said:**
> I disagree. How is "real hardware RAID" better than software RAID? Maybe in the Microsoft world it would be, but under Linux all that software RAID implementation requires is editing two files (RAIDTAB and one of your startup RCs). [snip]
that's like saying that there's no difference between a software modem (winmodem) and a hardware modem.  just because software raid is easy to implement doesn't mean it is as competent.

> As opposed to H/W RAID, there is no risk of the H/W failing, you can have dynamic resizing (with LVM), and it is much easier to recover your data (without having to worry about one-off or even proprietary partition formats).
there's two problems with this ... first, you're assuming that a $400 hardware raid controller is more prone to failure than software raid.  second, you suggest that you can't have lvm or proprietary partitions on hardware raid.  both of which are just flat wrong.

> [snip] but S/W RAID is a powerful tool which allows Linux users to fine-tune their system and eliminate one of the biggest bottlenecks for data manipulation.
raid1 which the op is (correctly) discussing will INCREASE the write times, not eliminate bottlenecks, other raid levels only increase drive performance and throughput in limited situations.

---

### Post by saulgoode on 2007-04-13
> **dmizer said:**
> that's like saying that there's no difference between a software modem (winmodem) and a hardware modem.  just because software raid is easy to implement doesn't mean it is as competent.

I am not saying there's no difference, I am saying that less hardware means less potential for hardware failure. A software modem would, all things being equal, be more reliable than having additional hardware to support modem functionality. The problem with winmodems is the proprietary nature of their drivers, not that the drivers are implemented in software.

> **dmizer said:**
> there's two problems with this ... first, you're assuming that a $400 hardware raid controller is more prone to failure than software raid.  second, you suggest that you can't have lvm or proprietary partitions on hardware raid.  both of which are just flat wrong.

I was basing my comment on the empirical data of the site you cited: RAID1 "being 15-20 times more likely to have a problem". If that increased failure rate is not owing to their usage of hardware RAID, to what can it be attributed (and why would it be relevant to their discussion)?

I will accept your word that LVM is "doable" on a hardware RAID; though, since the kernel is unaware of the physical partitioning of the disks, I fail to see how it would be as flexible as LVM+S/W RAID.

---

### Post by djamu on 2007-04-13
mmm seeing this thread is becoming a little off topic :D 
still i'd like to comment on hardware vs software RAID.

As being someone who has setup & maintained ( !? what is there to maintain )multi TB fileservers ( for 3D production studios ) in the past I understand the people ( & resellers ) who favor hardware RAID's.


The most overlooked issue against hardware RAID, aside from not having RAID6 + hotspares is following  - I assume you have your smb or whatever config files somewhere on a USB stick or something -
Once your precious hardware controller dies, there's no way to get your data back online until you have a ( identical brand ! ) new controller. If you where that careless to use a so called onboard hardware controller ( yeah that's right ), you might even be so unlucky of never finding that brand and type of MOBO again. there goes your data ... end of story.

With soft. RAID & a spare computer lying around ( and not to many disks ) you'll always manage to get your data back online faster than you'll be able to run to the nearest shop. 
I had this once in a production studio > downtime 17 min. includes : fresh install 6.06 + swapping drives + smb.conf dump..... 
if your drives are ok. it's actually much faster as your old system will most likely boot in your new hardware ( as opposed to that micro$oft stuff )...




back to the original question.

> 
Originally Posted by fotski
My query is:
What if for some reason the drive that holds ubuntu runs off died (which I don't plan to mirror)?
How would i be able to access the data on these drives?


You can boot from RAID 1 ( and only that type ) as drives hold identical information.
So why not using a small 1gb mirrored partition to hold your system.
GRUB will only make 1 of these bootable so you'll have to copy your MBR to the other disk(s) ( after the install :D )
use 
```

dd if=/dev/hda of=/dev/hdb bs=448 count=1

```
don't use "bs=512" as the last 64 bytes hold your partition table ( if your layout is identical you can just do that )

This way if any of your disks dies it will always boot.


An advanced setup example ( the one I use for my servers ) is following setup.
Totally carefree server..
- 15 x 400GB raw storage on dedicated fileserver - RAID 6 + 1 hotspare 
- real capacity 12 x 400 = 4.8 TB 
all disks have an identical partitioning layout with 4 partitions.

1st partition sdx1 ( sda1 / sdb1 / ....
> 100MB as RAID1 mounted as /boot  > to boot from any of those 
gives plenty of space to hold any kernel update

2nd partition sdx2
> 100MB as RAID6 + 1 hotspare = 1.2GB system mounted as / 
( standalone server, right ? ) you can use ramfs to load system in RAM 

3rd partition sdx3
> 100 - 200 MB RAID6 + 1 hotspare  > swap 
( if plenty of ram just skip this, for sure if it's just a cifs / smb server )

4th partition sdx4
xxx GB as RAID6 + 1 hotspare storage mounted as /whatever

 -you do plan on making a dedicated fileserver right ?. I would strongly object against using a desktop with fstab UUID's. Do yourself a favor and manually mount your arrays if you really plan on using it on a desktop, as the USB automounter ( usb scsci disks ) can screw up your array ( I had this already a couple of times ), because shifting of drive letters may occur, or worse on of your disks's RAID superblocks gets the wrong ID on next boot.
[http://ubuntuforums.org/showthread.php?t=405782]("http://ubuntuforums.org/showthread.php?t=405782")

It's not that bad, but very annoying as you might not understand what's going on.
( worst case is that you have to resync your disks )
If ever something happens like that, remember that your data is never lost as long as long as your disks aren't fried...


I use these a lot ( you need edgy -2.6.17 kernel -or a kernel that has the sata_mv module ), they come cheap at around 100$ / piece, real bargain good quality software SATA2 controller, that can be used with quite good result in 32 bit PCI slots
[http://www.supermicro.com/products/accessories/addon/AoC-SAT2-MV8.cfm]("http://www.supermicro.com/products/accessories/addon/AoC-SAT2-MV8.cfm")

if you really, really want hardware RAID or better performance ( +400MB/s, :D  I doubt if anyone at home has 10Gbs / myrinet etc...  )  you can add the ZERO-RAID controller - if you want for example a 64 disk array ( grinn ) 
(i'm not affiliated, i'm just  a happy customer )

have fun

Jan

---

