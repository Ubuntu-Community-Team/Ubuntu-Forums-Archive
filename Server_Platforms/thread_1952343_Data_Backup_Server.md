---
title: "Data Backup Server"
date: 2012-04-04
forum: Server Platforms
---

### Post by mastablasta on 2012-04-04
What would be the best way to go into building a backup server (kind of NAS). Is it better to buy premade NAS or can one get away with Atom CPU? Can Atom CPU (** Atom D425) **with 1 GB RAM be as energy efficient as some NAS which use ARM based board and use about 25W?
 
Are there any ARM board available on the market that would be easy to install and use?
 
I was thinking that i would need something in RAID 1 array and to use it stricktly as backup server. But premade NAS boxes usually (for reason unknown to me) have a disk size limit (2 TB or 4TB in low price range). While i was thinking that with an atom board one could add a PCI controler and add more disks.
 
Can Ubuntu server do the job or would it be easier to use (i think ubuntu based) Turnkey linux or something similar like Zentyal?
 
I don't have the money saved yet, but i was trying to find something reliable yet as cheap as possible to backup family pictures and films. And would need to support windows computer loging to it. i would also prefer it to be Debian or Ubuntu based. But if it has a good GUI and is RHEL based, i can also handle it i think.
 
Currently i am copying files i thing of as backup worthy manually from main maschine to linux mashcine. a lame way, i know... but at least the data is then on 2 separate disks.

---

### Post by winh8r on 2012-04-04
Not a direct answer to your question , but there is some useful opinion on this thread which might help you to decide:

[http://ubuntuforums.org/showthread.php?t=1948025]("http://ubuntuforums.org/showthread.php?t=1948025")

Hope this helps.

---

### Post by mastablasta on 2012-04-04
sorry i see no relevant opinion in the mentioned thread. 
 
There is nothing regarding Atom processors and it's use in server maschine.
 
important for me is low power consumption, price, stability/realiability.
 
when i finnaly decide to make/get one i do not intend to use old boxes with high power consumption.
 
i saw a. thread in another forum article where someone made it using this CPU, BSD based FreeNAS and 2 160 GB disks in software raid. got power consumption to 21 W idle and a little over 35 W when running. this looks promising.
 
any option to get this kind of experience on linux with larger drives? how well does software raid do? the mobo doesn't have raid it seems, but has a PCI slot which i could use for RAID controler if HW RAID is better. i have zero experience in this area.
i use desktop only and a pay for hosting linux server (with LAMP).

---

### Post by rubylaser on 2012-04-04
An Atom processor will be fine, although the new Sandy Bridge processors and the Zacate platform both have very low power consumption.  Personally, I always build my own machines, and Ubuntu/Debian + mdadm (software RAID) is perfect for the task.

It's probably easier to provide advice if we know your goal in terms of storage space (now and potential in the future), and what your budget is (does this include the need to buy hard disks or not). And, I'd make sure I bought a motherboard that had a PCI-Express slot.  This would allow you in the future to use an HBA like the IBM m1015 to support up to 8 hard disks and would accommodate disks larger than 2TB and still get good throughput (PCI will be a bottleneck for you if you have more than 1 disk on the bus).

---

### Post by darkod on 2012-04-04
Depending on where you live and what HP sells there, one interesting idea could be the HP Microserver.

I was studying components and saving money for the same project myself, until one day I received an offer email to buy HP Microserver with:
AMD N36L low power CPU (there are versions with N40L too)
1GB of RAM (2 slots taking up to 8GB total I think)
250GB SATA 3.5" disk (it has 4 caddies for up to 4 3.5" disks)
Gb ethernet
2 low profile expansion slots (don't remember now whether both were PCI-X or PCI-X + PCI)
Nice cube case

It was way cheaper than what ever I could come up with myself, especially with the offer. If you start picking components one by one, yes they are hand picked, but will cost you way more. This HP did the job for me and you still has the option to create your dream ubuntu server with it.

I bought earlier WD My Book World Edition and was really disappointed with what it can do. For example, the built in torrent client was getting stuck as soon as it starts downloading. I guess the cpu and memory on that couldn't take it. So after a while I started making plans for my own ubuntu server. Something as above will use more power than ARM but the options you get are way beyond what most devices will do.

PS. It was this model: [http://www.pccomponentes.com/hp_proliant_microserver_amd_athlon_ii_n36l_1gb_250gb.html](http://www.pccomponentes.com/hp_proliant_microserver_amd_athlon_ii_n36l_1gb_250gb.html)

---

### Post by rubylaser on 2012-04-04
> **darkod said:**
> Depending on where you live and what HP sells there, one interesting idea could be the HP Microserver.

I was studying components and saving money for the same project myself, until one day I received an offer email to buy HP Microserver with:
AMD N36L low power CPU (there are versions with N40L too)
1GB of RAM (2 slots taking up to 8GB total I think)
250GB SATA 3.5" disk (it has 4 caddies for up to 4 3.5" disks)
Gb ethernet
2 low profile expansion slots (don't remember now whether both were PCI-X or PCI-X + PCI)
Nice cube case

It was way cheaper than what ever I could come up with myself, especially with the offer. If you start picking components one by one, yes they are hand picked, but will cost you way more. This HP did the job for me and you still has the option to create your dream ubuntu server with it.

I bought earlier WD My Book World Edition and was really disappointed with what it can do. For example, the built in torrent client was getting stuck as soon as it starts downloading. I guess the cpu and memory on that couldn't take it. So after a while I started making plans for my own ubuntu server. Something as above will use more power than ARM but the options you get are way beyond what most devices will do.

PS. It was this model: [http://www.pccomponentes.com/hp_proliant_microserver_amd_athlon_ii_n36l_1gb_250gb.html](http://www.pccomponentes.com/hp_proliant_microserver_amd_athlon_ii_n36l_1gb_250gb.html)

+1 The HP Microserver is a great solution and is a power miser as well.  This would be a wonderful solution for mdadm.  I needed to use more hard drives than I could fit in the microserver case, so they've never been a good solution for me at home. Although, the [N40L]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859107052") is the newer version.  It does support up to 8GB of RAM, but that would be unnecessary unless you want to use ZFS on this box instead of mdadm.

Here's a [video]("http://www.youtube.com/watch?v=2zbjGywEkTA") of the N40L with 2 hard drives with the disks both spinning.  With them spun down, this should be a great solution.

---

### Post by mastablasta on 2012-04-04
they sell it for 374 EUR here stuck with 2 GB ram. what a rippoff. i know computer equipment here (as everything else) is more expenive that in "normal" EU countries, but sometimes they go overboard. i wonder what happens with all the gear they can't sell since they never really have electronic device sales with a 50% discount and such. I checked a few other videos about this microserver and they are indeed very neat and nice maschines.

anyway the option i had a look at came arorund 400 EUR including disks. but with that old intel atom and would need a raid contorler for propper raid and 420 W PSU (because all PSU with lower W and cheaper do not have enough sata plugs. it would use about the same power between 21 and 30 W.

I was thikning of using 2 x 2TB disks in RAID1 for starters which are the main cost as i do not have them. WD green  cost about 120 EUR each here. i would use this for data storage like maybe a weekly backup from computer drivers.


for now i have 30 GB data that really need a backup (and i created DVDs for most of it already) and about 15 GB i transfered to external drive that is at my father's place. I guess the data is relatively low at the moment, but this is because i use an old 5 Mpixel camera that can make 480x640 videos :-) but sometime in the near future i am hioping to get a better camera that will also make propper HD videos. i read this can increase data quite a lot. so i would be preparing for the future with a bigger HDD's.

It seems though that all solutions due to hard disk price and wishes end up at arorund 350-400 EUR. was checking if i take 1 TB hard drive but they are only 18 EUR less than 2 TB drives.

would it make sense to go for some other solution? at the moment i have 2 desktops. one is widnows XP with 160 Gb drive and 1 TB drive and the other one is a Kubuntu linux with 60 GB ATA and 750 GB WD green sata drive.

was thinking i could add racks to linux maschine, but the problem is again that racks cost 24 each and disk costs the same and i would also need to change the PSU since this one is old with only 1 SATA plug. and slowly but surely i am again close to 330 EUR. hmm...

edit: i found N36L (if they actualyl have stock for it) and are sellign it for 235 EUR here. :-(

---

### Post by rubylaser on 2012-04-04
> **mastablasta said:**
> they sell it for 374 EUR here stuck with 2 GB ram. what a rippoff. i know computer equipment here (as everything else) is more expenive that in "normal" EU countries, but sometimes they go overboard. i wonder what happens with all the gear they can't sell since they never really have electronic device sales with a 50% discount and such. I checked a few other videos about this microserver and they are indeed very neat and nice maschines.

anyway the option i had a look at came arorund 400 EUR including disks. but with that old intel atom and would need a raid contorler for propper raid and 420 W PSU (because all PSU with lower W and cheaper do not have enough sata plugs. it would use about the same power between 21 and 30 W.

I was thikning of using 2 x 2TB disks in RAID1 for starters which are the main cost as i do not have them. WD green  cost about 120 EUR each here. i would use this for data storage like maybe a weekly backup from computer drivers.


for now i have 30 GB data that really need a backup (and i created DVDs for most of it already) and about 15 GB i transfered to external drive that is at my father's place. I guess the data is relatively low at the moment, but this is because i use an old 5 Mpixel camera that can make 480x640 videos :-) but sometime in the near future i am hioping to get a better camera that will also make propper HD videos. i read this can increase data quite a lot. so i would be preparing for the future with a bigger HDD's.

It seems though that all solutions due to hard disk price and wishes end up at arorund 350-400 EUR. was checking if i take 1 TB hard drive but they are only 18 EUR less than 2 TB drives.

would it make sense to go for some other solution? at the moment i have 2 desktops. one is widnows XP with 160 Gb drive and 1 TB drive and the other one is a Kubuntu linux with 60 GB ATA and 750 GB WD green sata drive.

was thinking i could add racks to linux maschine, but the problem is again that racks cost 24 each and disk costs the same and i would also need to change the PSU since this one is old with only 1 SATA plug. and slowly but surely i am again close to 330 EUR. hmm...

edit: i found N36L (if they actualyl have stock for it) and are sellign it for 235 EUR here. :-(

The N36L isn't a bad machine buy any means.  That's still expensive compared to buying in the States, but not as bad as 400 EUR :)   I'd save a really spend your money to get something that's expandable rather than trying to save some money in the short run.

FYI, I have a T3i camera, and the 1080p video that it produces is 4GB per 12 minute clip. But, if I compress it with Handbrake, it greatly reduces the filesize.  My entire home movie folder is around 100GB at this point, so not huge by any means.

Another option could be to go with one of the services that buys in the States and then ships it to you.

---

### Post by mastablasta on 2012-04-05
Is the NL36L very quiet?
 
i was thinking that for starters maybe i could use the single 250 GB disk that comes with it and later when i have more money get the 2 additional disks and set them up in raid array. that is possible right?
 
the build-it-myself option is kind of similar, however i just like the way that HP made it easy to install new disks inside the box. though if i wanted to upgrade i guess HP server components could get pricy.

---

### Post by darkod on 2012-04-05
Yes, the whole device is quiet. And if you plan to make it headless server, you can always stick it in some corner/cupboard (just make sure it has ventilation, not in entirely closed space).

I would say it makes less noise than any middle range PSU you will buy to make your own box. Unless you spend like 100€ for a super silent PSU, the Microserver will make less noise.

Don't worry about HP server components, you don't need them. All four HDD slots come with the "rails" (plastic caddies) inside them. You just need to slide it out, install the HDD into it, and slide it back. It uses standard 3.5" SATA disks, so you can install which ever disk you choose to buy.

Even though the 1GB DDR3 it comes with is ECC, when I was investigating prior to buying I saw on google people have installed standard non-ECC DDR3 modules (which are cheaper) and it worked without any issues. So you can upgrade RAM on the cheap too. Even if you decide to go with ECC you have modules from Kingston which are usually much cheaper than HP branded ones.

I can't see which component will be expensive. The most important is HDD and RAM and there you are covered.

Yes, you could add disks later and create mdadm array without any issues. I also started with the original 250GB because I bought it sometimes November when the disks went really expensive because of the Thailand floods. Prices have come down now slightly, but still not to pre-flood levels. I doubt they ever will. When I think a 1TB Samsung was 42€ and I didn't grab couple of them.... :( I am now looking at 2 x 2TB options but the disks are still like 110€-120€ a piece...

---

### Post by mastablasta on 2012-04-05
Thank you for all the information. I still have some reading to do and some money to save/earn. and also some energy consumption calculations to make since server usually is running non-stop. I just know i should do something about backups and approach them more systematicly.
 
The disk prices probably won't go down. At least not any time soon. Because there are now only a few manufatures left (2 or 3) due to recent mergers. Oligopolly is never good for consumers. And to think disks now fail relatively often compared to the old days. I mean i have an IDE disk since 1998 that is still working without any mistakes or one from 93' can still boot up and do it's job using win95...

---

### Post by CharlesA on 2012-04-05
> **rubylaser said:**
> An Atom processor will be fine, although the new Sandy Bridge processors and the Zacate platform both have very low power consumption.  Personally, I always build my own machines, and Ubuntu/Debian + mdadm (software RAID) is perfect for the task.

It's probably easier to provide advice if we know your goal in terms of storage space (now and potential in the future), and what your budget is (does this include the need to buy hard disks or not). And, I'd make sure I bought a motherboard that had a PCI-Express slot.  This would allow you in the future to use an HBA like the IBM m1015 to support up to 8 hard disks and would accommodate disks larger than 2TB and still get good throughput (PCI will be a bottleneck for you if you have more than 1 disk on the bus).

Huge +1 to this. I was looking toward an Atom solution to my home server because it was originally intended to be used as a file server only, but has expanded to being a VM host among other things.

The (new) box I have is pretty quiet but I'm pretty sure it doesn't exactly sip electricity. An atom would blow that out of the water, but I haven't seen any quad core Atoms. ;)

As for backups, I just rsync from my raid array to an external drive and leave it at that.

---

### Post by mastablasta on 2012-04-06
well i found this: [http://www.tomshardware.co.uk/forum/263468-14-feeenas-atom-d425-performance-power](http://www.tomshardware.co.uk/forum/263468-14-feeenas-atom-d425-performance-power)
 
It seems the whole thing uses about the same as HP microserver, though atom could be a bit faster. don't know. but those were the days when 2 Tb disks were sitll cheap :-/ i think to me the disks are the biggest cost and i have to think about if the whole thing is even worth it right now.
 
questions: 
does this kind of server need a UPS?
Does this kind of micro server need a separate drive for OS or can i add a 250 GB disk make them both in RAID1 and have the OS on it as well as do backups?
these ARM NAS devices they sell here for 90 EUR diskless (for example: for example: [http://sharecenter.dlink.com/products/DNS-320](http://sharecenter.dlink.com/products/DNS-320) ) - what kind of OS they use? can one change change their OS or is it stored in some kind of ROM. they seem to be preety energy efficient, though weaker CPU and less RAM.

---

### Post by darkod on 2012-04-06
The UPS is your choice and does not have anything to do with the server machine. If this is only a home server, I can't see any benefit of a UPS, except if you have very bad electricity supply and want the UPS to even out the spikes in voltage.

If the plan is the server to continue working on the UPS when the power goes down, no other computer will work in your home anyway, so who will access the server?

The OS can be where ever you want. You could get another 250GB disk, make a raid1 mdadm array and put the / partition there, use the rest for your data partitions. You don't need a dedicated separate OS disk unless you want to have one.

I would say the NAS devices have their OS in their firmware. They are not planned to install an OS yourself. Unless there are some hacks around, you would need to investigate that for the specific model. So yes, the resources will be limited to the ARM CPU and the small memory the NAS has.

---

### Post by rubylaser on 2012-04-06
I would encourage you to use a UPS if you're going to do software RAID.  Running RAID1, you won't have to worry about the RAID5/6 write hole, but a statefull shutdown via UPS is always better than the pull the plug out of the wall, power outage effect.

The only simple NAS device that I can think of off the top of my head that will let you change the OS is the Linksys Network Storage Link NSLU2.  But, it's around $200, and the microserver has much more expandability potential than that.

---

### Post by CharlesA on 2012-04-06
> **rubylaser said:**
> I would encourage you to use a UPS if you're going to do software RAID.  Running RAID1, you won't have to worry about the RAID5/6 write hole, but a statefull shutdown via UPS is always better than the pull the plug out of the water power outage effect.

A controlled shutdown is much being than a hard shutdown. If you value your data, get a UPS.

---

