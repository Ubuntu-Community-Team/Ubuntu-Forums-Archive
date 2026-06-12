---
title: "Project: Epic fix of a RAID setup"
date: 2009-10-09
forum: The Cafe
---

### Post by blueturtl on 2009-10-09
_[SIZE="6"]A logged journey to cheap-*** RAID configuration[/SIZE]_

I came into some birthday money and so now I'm going ahead with a project that I've been dreaming about for a while: RAID. For those of you who do not know, RAID is a method of using multiple disks to increase data security and performance. Not being rich and my computer being what it is this has led to a plan of epic proportions...

[SIZE="5"]Introducing the patient:[/SIZE]
[LIST]
[*]Generic ATX-case and FSP Group 300W power supply
[*]AOpen AX6BC motherboard (Slot1, Intel 440BX chipset)
[*]Intel PentiumIII 1 GHz CPU (133 FSB model)
[*]768 MB of SD-RAM (PC133, CL2)
[*]Matrox Millennium G400 video card (AGP, 16 MB VRAM)
[*]Seagate ST3120026A 120 GB PATA HDD
[*]ASUS E612 DVD-ROM
[*]Samsung SW-216B CD-RW
[*]Dual 3COM Fast EtherlinkXL network adapters
[*]M-Audio Revolution 5.1 PCI Audio
[*]ALi M5273 USB2 card
[/LIST]

[SIZE="5"]Preliminary tactical planning[/SIZE]

I have three reasons for wanting to do this RAID setup. Firstly I want to do it to learn. I want to have actually deployed RAID if that ever comes up as a job requirement. Secondly, I could use more data storage but the BIOS on my motherboard will probably bug out at disk sizes greater than 137 GB. Thirdly, I want the extra security provided. I do backups, but having a hard-disk fail would always set me back up-to a month if it happened.

So with all this in mind I started looking at what's on the market.
PATA disks and controllers are on their way out and it shows in pricing: PATA hard drives are relatively expensive and have less capacity options than their SATA counterparts. However a *real* hardware RAID SATA controller costs an arm and a leg. On the PATA side something tried and true like the LSI MegaRAID i4 is only $30 on eBay.

[SIZE="5"]The part where it gets crazy[/SIZE]
I have concocted a plan of using laptop hard drives (2.5" SATA) with the LSI MegaRAID controller. Parts list is as follows:

[LIST]
[*]LSI MegaRAID i4 Series 511 PCI - ~30&#8364; incl. overseas postage
[*]2x Seagate Momentus 5400.6 (ST9320325AS) 320 GB laptop hard drives ~99&#8364;
[*]2x 2.5"->3.5" mounting brackets and SATA->PATA converters ~12&#8364;
[/LIST]

The grand total of this scheme is just about 150&#8364; and it will accomplish the following: I will have boosted my total storage capacity to 320 GB and circumvented the BIOS limit while applying RAID1 (Mirroring). All this is done in hardware outside the operating system and as an added bonus the laptop drives are quieter and less power hungry. I have no performance expectations, but based on theoretical knowledge I would suspect two 5400 rpm drives in RAID1 mode to be slightly faster than a single 7200 rpm drive in read operations, while slightly slower when writing. This is all going to be documented of course.

I will post performance benchmark information before and after the setup has been altered.

[SIZE="5"]Risk assesment[/SIZE]
I have looked at potential problems with this process and have come up with the following scenarios:
[LIST]
[*]The LSI MegaRAID i4 is not supported by Debian/Ubuntu or will be hard to set up.
[*]The SATA->PATA converters will not work with the hard drives or the MegaRAID card.
[*]The system will not attempt to boot up via the RAID controller (old mobo).
[*]Fire rains from the sky and the world will end while I hold a scredriver in my hand.
[/LIST]

After looking at this stuff online I'm leaning towards having trouble with the SATA->PATA converters. They're really cheap and I have no idea how dependable the conversion of one interface to another is all things considered. The MegaRAID appears well supported though there are some bug reports online.

Yes, I know I'd have a higher probability of success using regular 3.5" PATA hard drives: they are available without the need for converters, spin at 7200 rpm and would probably be available with bigger capacities too. However, this is supposed to be an adventure. I'm willingly and knowingly testing the patience of the gods.

---

### Post by blueturtl on 2009-10-09
[SIZE="5"]Tests: Before[/SIZE]

I will be taking suggestions on how to benchmark the system before and after modification. New tests will be appended to this post. Results after the modification will be in a separate post entitled 'Tests: After'. For the time being I have come up with the following tests/results:

[SIZE="4"]Test1: Startup to login prompt[/SIZE]
Test is conducted under Debian 5.0.2 "Lenny".
Runlevel 2 services: acpid, atd, cron, cups, dbus, exim4, hald, nfs-common, rsync, rsyslogd, rmnologin, rc.local, sshd, statd
Took 30sec according to my watch

[SIZE="4"]Test2: Startup X.org and environment[/SIZE]
Test is conducted under Debian 5.0.2 "Lenny".
xinit runs startfluxbox script which runs the following: Fluxbox, conky, xscreensaver, urxvtd
Took 13sec according to my watch

[SIZE="4"]Test3: Firefox cold start[/SIZE]
Test conducted under Debian 5.0.2 "Lenny": Took 10sec according to my watch
Test conducted under Ubuntu 9.10 "Karmic Koala" Release Candidate: 11 sec

[SIZE="4"]Test4: hdparm -tT[/SIZE]
Test is conducted under Debian 5.0.2 "Lenny".
Command is run three times in a row, best result grabbed.

> /dev/hda:
 Timing cached reads:   394 MB in  2.01 seconds = 196.42 MB/sec
 Timing buffered disk reads:   86 MB in  3.04 seconds =  28.29 MB/sec


Test is conducted with Ubuntu 9.10 "Karmic Koala" Release Candidate.
Command is run three times in a row, best result grabbed.

> /dev/sda:
 Timing cached reads:   404 MB in  2.01 seconds = 201.37 MB/sec
 Timing buffered disk reads:   64 MB in  3.02 seconds =  21.18 MB/sec


[SIZE="4"]Test5: File transfer across LAN[/SIZE]
Test is conducted under Debian 5.0.2 "Lenny".
Ethernet speed cap is 100 MBit.
A single CD-ROM ISO image file (688 MB) is copied to and from a network source.
Read speed: 1 Min 35 sec (~7.2 MB/s)
Write speed: 1 Min 7 sec (~10.2 MB/s)

[SIZE="4"]Test6: Ubuntu startup[/SIZE]
Test is conducted with Ubuntu 9.10 "Karmic Koala" Release Candidate.
For the test my user has been set up to login automatically.
All settings at defaults.
Time is counted from exiting GRUB to the point where the desktop is ready to receive instructions.
Time measured: 38sec

I have to say I am impressed with the Ubuntu team. If you put together the Debian startup times you'll see that Ubuntu 9.10 with full blown Gnome boots up 5 seconds faster than Debian 5.0.2 with Fluxbox!

---

### Post by blueturtl on 2009-10-19
[SIZE="5"]The Parts Arrive Post[/SIZE]

Received in the mail (October 19th):
- raid controller card
- 2.5" to 3.5" bay hard drive mounts
- two PATA100 cables
- two Seagate Momentus 320 GB SATA hard drives

Received in the mail (October 20th):
- suprise part: Hercules 3D Prophet 9000 (ATi Radeon 9000) PCI video card

Received in the mail (October 23rd):
- SATA to ATA bridge chips

Further tests and the actual installation coming up. Stay tuned to find out if the whole thing was doomed from the start. :)

Update Oct. 23rd: pics are now properly sized...

---

### Post by CharlesA on 2009-10-19
Good luck. That's a definitely cheap setup, should work fine too.

Curious as to why you used laptop drives instead of regular 3.5" desktop drives.

> added bonus the laptop drives are quieter and less power hungry.

Outside of that, of course. The only thing I can think of is that the access time will be slower since they are 5400RPM instead of 7200, but that really shouldn't be a huge difference since they are going to be run as PATA drives. *shrugs*

I'd be interested to know the extended transfer rates to see how it would compare to my RAID array (PCIe card, SATA 7200 desktop drives)

---

### Post by blueturtl on 2009-10-19
> **CharlesA said:**
> Good luck. That's a definitely cheap setup, should work fine too.

Curious as to why you used laptop drives instead of regular 3.5" desktop drives.

Hi CharlesA!

To answer your question:
1) In the interest of science: Most notebook hard drives are only 5400 rpm whereas practically all big desktop hard drives are at least 7200 rpm. I want to see if RAID performance will compensate the lower spindle speed.
2) In my experience 7200 rpm drives vibrate enough to create a low humming background noise in a system. I'm testing if I can get rid of this background hum by using lower spindle speed drives. Since practically all desktop drives today are 7200 rpm I had to go with laptop hard drives.
3) The logical follow-up question to using SATA gets answered if you look at SATA vs. PATA hard drive pricing. For the price I got two new 320 GB SATA drives I would have gotten just one 160 GB PATA drive (in 2.5" form factor)!

I sure hope those SATA->PATA adapters are reliable. Otherwise this is going to become rather more difficult. :)

> I'd be interested to know the extended transfer rates to see how it would compare to my RAID array (PCIe card, SATA 7200 desktop drives)

Tell me how to test, and I will report back with results.

---

### Post by CharlesA on 2009-10-19
I see your point about the 5400 drives, that makes sense.

Not sure exactly how to test it. I tend to copy big chunks of data to my RAID array. (files 1GB+ in size) most ripped dvds from my dvd collection that I play on my HTPC. I guess all I did to "test" it was copy files to the array and monitor the speed it transfered at. Mine hit around 38MB/sec, but that's over a gigabit network to a RAID-5 array, so I'm sure yours will be different due to it being a RAID-1, but I'm not sure.

I kinda think that it'll be slower since you are running over a 10/100 network and using a PATA interface, but I'm curious as to how it performs. :-)

Sidenote: While I don't have any experience with PATA-to-SATA bridges, I've heard that they are more trouble then they are worth. I hope that they work out well for you.

---

### Post by miegiel on 2009-10-19
I've been using budget RAID for a long time now and I'm pretty sure I had 2 500GB disks in RAID1 in my PII with the BX chipset for a while. The RAID was just for storage, I used a separate 120GB disk for the OS. I upgraded to 3 500GB disks in RAID5 in the same machine 1 SATA and 1 PATA on a PCI SATA + PATA card and the last PATA disk on the motherboard.

By now you must have realized I don't use hardware RAID. Hardware RAID has it's advantages, but I use RAID for redundancy and I wouldn't want to depend on a single RAID card. Besides cheap RAID cards implement RAID in the driver and (unless you want to boot to the RAID array) don't really have an advantage over software RAID.

Best of luck with your experiment ;)

---

### Post by blueturtl on 2009-10-19
> Not sure exactly how to test it. I tend to copy big chunks of data to my RAID array. (files 1GB+ in size) most ripped dvds from my dvd collection that I play on my HTPC. I guess all I did to "test" it was copy files to the array and monitor the speed it transfered at. Mine hit around 38MB/sec, but that's over a gigabit network to a RAID-5 array, so I'm sure yours will be different due to it being a RAID-1, but I'm not sure.

I kinda think that it'll be slower since you are running over a 10/100 network and using a PATA interface, but I'm curious as to how it performs.

RAID1 and RAID5 are quite different. In RAID1 all the data is essentially doubled across two or more disks. Write performance should be around that of a single 5400 rpm drive or maybe a little slower because the data has to go to two disks. Read performance should however be roughly double that of a single drive (because the data can be retrieved from two disks simultaneously). RAID5 is potentially bottlenecked by parity calculation which is absent in RAID1, but regardless I'd be surprised if I ended up with better performance. Especially since you have more and faster disks.

> Sidenote: While I don't have any experience with PATA-to-SATA bridges, I've heard that they are more trouble then they are worth. I hope that they work out well for you.

I expect if something will fall short it will be the SATA bridge.

> I've been using budget RAID for a long time now and I'm pretty sure I had 2 500GB disks in RAID1 in my PII with the BX chipset for a while. The RAID was just for storage, I used a separate 120GB disk for the OS. I upgraded to 3 500GB disks in RAID5 in the same machine 1 SATA and 1 PATA on a PCI SATA + PATA card and the last PATA disk on the motherboard.

By now you must have realized I don't use hardware RAID. Hardware RAID has it's advantages, but I use RAID for redundancy and I wouldn't want to depend on a single RAID card. Besides cheap RAID cards implement RAID in the driver and (unless you want to boot to the RAID array) don't really have an advantage over software RAID.

Best of luck with your experiment ;)

Thank you for your input. I'm certainly aware of the difference between software and hardware RAID. I'm under the impression that the MegaRAID controller I've purchased is a real hardware raid card (the brochure says it has the Intel i960RS I/O processor and it's own memory). The reason I wanted to go with hardware RAID is that -- as you pointed out -- software RAID would require the OS to reside on a separate disk and also because I don't want to have to deal with driver issues. AFAIK the LSI MegaRAID has mature Linux support too so it should be just plug-n-play (knock on wood). It was cheap probably because it uses a now aging ATA100 interface.

---

### Post by CharlesA on 2009-10-20
> **blueturtl said:**
> RAID1 and RAID5 are quite different. In RAID1 all the data is essentially doubled across two or more disks. Write performance should be around that of a single 5400 rpm drive or maybe a little slower because the data has to go to two disks. Read performance should however be roughly double that of a single drive (because the data can be retrieved from two disks simultaneously). RAID5 is potentially bottlenecked by parity calculation which is absent in RAID1, but regardless I'd be surprised if I ended up with better performance. Especially since you have more and faster disks.

That's probably true, but I'm curious as to the results. :D

---

### Post by Firestem4 on 2009-10-20
Edit: To clarify for the OP, RAID 1 does not increase Performance. RAID 1 creates an exact mirror, and each HDD reads/writes and accesses data in parallel. RAID1 was mainly meant for the benefit of being able to loose an entire disk. Random Access times may be slightly faster on RAID1 than a standard/other RAID configuration, but I'm not sure. Any RAID will add a slight-to-large amount of overhead. RAID1 creates more overhead since you are duplicating every read, write, access, etc. RAID5 adds more overhead due to parity. Striping has little overhead compared to any RAID configuration.

 If you want better performance than RAID0 (Striping) is the way to go since it writes bits sequentially across the spanned array. (bits 1,3, and 5 on diskA; bits 2,4, and 6 on diskB). 

Not wanting to be the devils advocate, a recent event that happened at my Company warrants this disclaimer. RAID is no excuse for a proper backup. A RAID can fail in many ways other than a physical hardware failure. So be certain to keep backing up your important data to a drive that is not permanently attached to your computer.

What happened at my company? 3 of 4 disks in a RAID5 Array failed sequentially, one after another. The hard drives are physically fine. All 4 were 15K rpm SAS drives. The logical RAID partitions failed on the drives by an unkown error. Backups were 3-4 weeks old...

On other news, I've been wanting to setup RAID 1 at home. My new gigabyte motherboard supports 0,1, and 0+1 (aka: raid 10).I'm just paranoid about a HDD dropping, so this is my main reason. :)

---

### Post by CharlesA on 2009-10-20
That is definiately a good disclaimer. I've got mine set to sync the files on the array with an external drive every hour. Unless two drives on the array go down and my external eats it, I should be good.

Minus disaster, flood, fire..etc.. ofc. I don't have a fireproof drive just yet. :P

EDIT: As for drives dropping out of the array: I've read that this is caused by the drive trying to recover data (deep recovery phase or some such thing). I've had my array up for just under a month without any issues, and I am running some desktop drives.

---

### Post by sloggerkhan on 2009-10-20
Why are you making trouble for yourself?
Just get a sata card and use mdadm.

Don't bother with unsuported specialty hardware.

---

### Post by CharlesA on 2009-10-20
> **sloggerkhan said:**
> Why are you making trouble for yourself?
Just get a sata card and use mdadm.

Don't bother with unsuported specialty hardware.

The OP wanted a cheap setup, without having to spend money on a SATA card.

---

### Post by miegiel on 2009-10-20
> **Firestem4 said:**
> ...

On other news, I've been wanting to setup RAID 1 at home. My new gigabyte motherboard supports 0,1, and 0+1 (aka: raid 10).I'm just paranoid about a HDD dropping, so this is my main reason. :)

And how paranoid are you when it comes to failing motherboards (or failing RAID cards)?

I know that if you get the same motherboard, or even a RAID card by the same manufacturer as the RAID chip on your motherboard, there is a good chance you'll get your array up again. There's even a good chance that newer hardware is still compatible with the array you made on your dead RAID chip. But still it's "only" a good chance it will still work and RAID is all about eliminating the chance you loose what you really don't want to loose (disregarding RAID 0 here).

---

### Post by sloggerkhan on 2009-10-20
> **CharlesA said:**
> The OP wanted a cheap setup, without having to spend money on a SATA card.

A sata card is cheap. $40 for a basic 4 port (newegg link below), though you can probably find cheaper, I think I've seen a 4 port card for as little as $25. 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816124028](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124028)


Way better than his convoluted scheme involving ebay and dependence on bizarre hardware. Especially considering his suspect ebay part is $30 anyway.

---

### Post by CharlesA on 2009-10-20
> **sloggerkhan said:**
> A sata card is cheap. $40 for a basic 4 port (newegg link below), though you can probably find cheaper, I think I've seen a 4 port card for as little as $25. 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816124028](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124028)


Way better than his convoluted scheme involving ebay and dependence on bizarre hardware. Especially considering his suspect ebay part is $30 anyway.

Not bad at all for a PCI card. The card I ended up getting was a PCIe, so that's probably why mine was 150 bucks. :rolleyes:

---

### Post by Firestem4 on 2009-10-20
> **miegiel said:**
> And how paranoid are you when it comes to failing motherboards (or failing RAID cards)?

I know that if you get the same motherboard, or even a RAID card by the same manufacturer as the RAID chip on your motherboard, there is a good chance you'll get your array up again. There's even a good chance that newer hardware is still compatible with the array you made on your dead RAID chip. But still it's "only" a good chance it will still work and RAID is all about eliminating the chance you loose what you really don't want to loose (disregarding RAID 0 here).


I'm not that paranoid about my Motherboard. I've had motherboard's go bad before, yes. But I if my raid goes bad then I'll have my data backed up somewhere. I listen to my advice when I state that a raid is no excuse for a proper backup. But I hate having to restore my system, which is why I would bother with a mirrored raid. If one drive fails, I still have the 2nd operational.

If my motherboard does die than I can replace it with another Gigabyte Motherboard that uses the same SATA RAID Controller, if I can't then i'll rely on my backups.

---

### Post by blueturtl on 2009-10-21
> **Firestem4 said:**
> Edit: To clarify for the OP, RAID 1 does not increase Performance. RAID 1 creates an exact mirror, and each HDD reads/writes and accesses data in parallel. RAID1 was mainly meant for the benefit of being able to loose an entire disk. Random Access times may be slightly faster on RAID1 than a standard/other RAID configuration, but I'm not sure.

Thank you for posting. This was very informative. I was under the impression that in a RAID1 system if a big file was to be read, it would be retrieved half and half from both disks resulting in a 50% reduction in read latency. If this is not the case then woe is me, because I'll be on a 5400 rpm system.

> **Firestem4 said:**
> Any RAID will add a slight-to-large amount of overhead. RAID1 creates more overhead since you are duplicating every read, write, access, etc. RAID5 adds more overhead due to parity. Striping has little overhead compared to any RAID configuration.

Will there be overhead with a hardware based RAID controller? In software solutions, the main CPU will always handle the parity calculation and data routing.

> **Firestem4 said:**
> If you want better performance than RAID0 (Striping) is the way to go since it writes bits sequentially across the spanned array. (bits 1,3, and 5 on diskA; bits 2,4, and 6 on diskB).

I would get a total storage capacity of 640 GB and better read and write performance! Striping is a very real possibility for me. However striping carries an additional risk: if either of the two disks fail, I will lose the data on both. Talk about hard choices.

> **Firestem4 said:**
> Not wanting to be the devils advocate, a recent event that happened at my Company warrants this disclaimer. RAID is no excuse for a proper backup. A RAID can fail in many ways other than a physical hardware failure. So be certain to keep backing up your important data to a drive that is not permanently attached to your computer.

What happened at my company? 3 of 4 disks in a RAID5 Array failed sequentially, one after another. The hard drives are physically fine. All 4 were 15K rpm SAS drives. The logical RAID partitions failed on the drives by an unkown error. Backups were 3-4 weeks old...

I agree. I guess the reason I came up with RAID was that I only do backups every couple of months and RAID would provide me with a little additional security that would also be transparent (with mirroring, I would essentially automatically backup every new file I create/save). RAID is a good solution for us lazy types. I still do have a separate external disk solely for backup purposes.

> **Firestem4 said:**
> On other news, I've been wanting to setup RAID 1 at home. My new gigabyte motherboard supports 0,1, and 0+1 (aka: raid 10).I'm just paranoid about a HDD dropping, so this is my main reason. :)

Good luck!

> A sata card is cheap. $40 for a basic 4 port (newegg link below), though you can probably find cheaper, I think I've seen a 4 port card for as little as $25.

I acknowledge this. However I think a real hardware RAID card will cost much more. Software RAID is a good solution if you got a Core2 Duo, but I think my poor old rig would just die if it had to handle the overhead on the main CPU for each read/write. The only reason I use SATA drives is that PATA drives are becoming rare and expensive.

If this gamble of mine (combining a cheap PATA RAID card with cheap SATA HDDs) pays off I'll be glad. But I understand why you might think I'm crazy. :)

--

I've already put out a poll so if you guys want to help me decide wether to go with RAID0 (Striping) or RAID1 (Mirroring) please let me know by posting your thoughts below. If I could afford two more disks, I'd probably do mirroring+striping but for the time being I'm stuck with the choices below:

RAID0
- combines two 320 GB disks in to a 640 GB mega volume!
- read and write performance will increase significantly
- if EITHER disk fails, all data gone bye bye

RAID1
- two 320 GB disks make just one 320 GB volume
- read performance slightly better than single disk, small write penalty
- if one disk dies, all data still safe and system will still run

I'm seriously contemplating between these two for the time being (the SATA bridge chips are still in the mail).

Thanks everyone! :)

---

### Post by CharlesA on 2009-10-21
All RAID configurations except RAID-0 (which isn't really "RAID") have overhead.

Personally if I had to choose between RAID-0 and RAID-1, I'd go with RAID-1.

---

### Post by sloggerkhan on 2009-10-21
> **blueturtl said:**
> 

I acknowledge this. However I think a real hardware RAID card will cost much more. Software RAID is a good solution if you got a Core2 Duo, but I think my poor old rig would just die if it had to handle the overhead on the main CPU for each read/write. The only reason I use SATA drives is that PATA drives are becoming rare and expensive.

If this gamble of mine (combining a cheap PATA RAID card with cheap SATA HDDs) pays off I'll be glad. But I understand why you might think I'm crazy. :)

--
Thanks everyone! :)

Software raid isn't that cpu intensive. I saturate my 100 megabit ethernet network pulling from a software raid V running on a 1.2 or so ghz single core amd sempron and without any appreciable cpu load. Likewise, even when copying internally, limiting factor is not the cpu.

---

### Post by Exodist on 2009-10-21
I have had RAID setup many times. I have two WD Raptor hard drives.

Here is how to setup the array software wise.

First get the Alternate CD.

Plug both up, you dont have to change anything in the BIOS like you would windows.

When the CD boots and you get to the partition setup. 
- On sda make two partitions first /boot for about 3GB. Other partition RAID.
- On sdb make two partitions first /swap for about 3GB. Other partition RAID.
- Set sda as bootable drive with /boot containing your boot info. This will let you boot the array.
- Set the RAID array to RAID# of your choose, I use stripping (RAID0) for performance.
- Also if you have another drive you use as home directory just set the other drive like I have (sdc, WD Cavier 320GB) as /home.

Unless the setup CD is screwed up like the last release up Debian this normally setups very quickly and without a headache.

---

### Post by blueturtl on 2009-10-22
> **sloggerkhan said:**
> Software raid isn't that cpu intensive. I saturate my 100 megabit ethernet network pulling from a software raid V running on a 1.2 or so ghz single core amd sempron and without any appreciable cpu load. Likewise, even when copying internally, limiting factor is not the cpu.

I'll take your word for it.

> I have had RAID setup many times. I have two WD Raptor hard drives.

Here is how to setup the array software wise.

First get the Alternate CD.

Plug both up, you dont have to change anything in the BIOS like you would windows.

When the CD boots and you get to the partition setup.
- On sda make two partitions first /boot for about 3GB. Other partition RAID.
- On sdb make two partitions first /swap for about 3GB. Other partition RAID.
- Set sda as bootable drive with /boot containing your boot info. This will let you boot the array.
- Set the RAID array to RAID# of your choose, I use stripping (RAID0) for performance.
- Also if you have another drive you use as home directory just set the other drive like I have (sdc, WD Cavier 320GB) as /home.

Unless the setup CD is screwed up like the last release up Debian this normally setups very quickly and without a headache.

Great. Now I have a backup plan in case this crazy scheme fails. I'll just have to trade the MegaRAID card for a cheap SATA PCI adapter.

---

### Post by blueturtl on 2009-10-23
[SIZE="6"]The project begins![/SIZE]

As of today I have all the parts necessary to complete the project. However I quickly discovered my first unanticipated problem:

The [JMicron JM20330]("http://www.jmicron.com/JM20330.html") based bridge chips only support SATA 1.0 and the hard drives I bought are SATA2 models.

I quickly find out reading the [product manual for the hard drives]("http://www.seagate.com/staticfiles/support/disc/manuals/notebook/momentus/5400.6%20(Wyatt)/100528359e.pdf") that a jumper needs to be set for the drives to operate in SATA1 mode. A regular sized jumper doesn't fit. I scoured the box for included jumpers but there were none!

After driving around the town and visiting all the computer shops I could find I only had one jumper (they wouldn't even sell me any, apparently the smaller ones are so rare!) and I would need two, so I decided to make my own from a regular sized one. Luckily not much modification is needed; after taking of the protective plastic layer, the jumper already fits the SATA drive.

The project can proceed!

For the time being I have completed backing up all my data to the external drive and am beginning the remaining benchmarks. After benchmarks are complete, I will start the RAID installation. Posts with pictures will follow after I have the system online again... Wish me luck. :guitar:

---

### Post by CharlesA on 2009-10-23
Spiffy. I've used SATA II drives at SATA I speeds before, but they were Western Digital drives that automatically detect transfer speed. Not sure if those seagate drives do the same. At least you were able to set them up using the jumper. :-)

Keep us updated!

---

### Post by blueturtl on 2009-10-23
[SIZE="6"]Installation report part 1:[/SIZE]

Time to get my hands dirty.
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/001_before.jpg[/IMG]

I begin by inserting the MegaRAID adapter into the system. At this point I thought I shouldn't go further without knowing if the system will actually boot so I did.
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/002_megaraid_bios.jpg[/IMG]
Success, going once!

Time to dig out the drives. I attach the mounts and the SATA converter and plug one hard-disk in to test what will happen.

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/003_desktop_vs_laptop.jpg[/IMG]
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/004_pata_adapter1.jpg[/IMG]
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/005_pata_adapter2.jpg[/IMG]
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/006_hdd_mounts.jpg[/IMG]
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/007_hookuptest.jpg[/IMG]
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/008_test_success.jpg[/IMG]
Success, going twice!

To be continued...

---

### Post by blueturtl on 2009-10-23
I start working on permanently attaching the disks to my case. Unfortunately I didn't quite think through the installation and end-up having to reapply the mounts. The adapters portrude outward a little too much for me to be able to close up:
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/009_whoops.jpg[/IMG]

I finally get everything in properly.
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/010_drives_installed.jpg[/IMG]

One of the PATA100 cables is a little difficult to fit on to the RAID card, but other than that everything goes smoothly... Until I realize the hard disks are reported to be of size ~130 GB roughly:

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/011_uh-oh_drivesize_incorrect.jpg[/IMG]

Augh! I thought the card supported larger disks. It turns out the firmware of the card is an older revision so I head to the LSI support site for the latest BIOS/firmware.

After updating the firmware I have run into a brick wall:
The system will POST, but I cannot get into the MegaRAID BIOS. If I hit the CTRL+M key, it will hang the system. If I don't the system will eventually attempt to boot via the motherboard.

It is getting late and I don't want to do anything rash, so I'm leaving this for tonight. Feel free to post possible solutions or ideas... For now my [best lead]("http://blog.edseek.com/archives/2004/04/01/ami-now-lsi-megaraid-express-466-ultra-2/") is to get the DOS driver package (which supposedly has an executable file that will allow you to access the BIOS) and attempt to access the MegaRAID settings with a boot disk.

[SIZE="3"]Is this the end? Stay tuned. ;)[/SIZE]

edit: I will resume this project on monday, a surprise trip came up...

---

### Post by CharlesA on 2009-10-25
Perhaps try flashing it with a newer BIOS version, but not the latest?

I can't really think of what would cause it to hang, could be that it's trying to detect the drives, have you tried booting with no drives attached?

---

### Post by blueturtl on 2009-10-26
[SIZE="6"]Installation report part 2:[/SIZE]

After arriving home I first head to the LSI website. They have drivers for DOS listed so I download those, unzip the package and BINGO: megaconf.exe. So I then start the system with a boot floppy (I have kept mine around, no need to go hunting for one) while burning megaconf.exe to a cd-rw disk.

After system is ready I insert the disk and run megaconf.exe only to find...

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/012_hooray_for_dos.jpg[/IMG]

... that it works perfectly. :) This is a big relief. The hard disk capacity reported is 305 gigs, but you have to remember boys and girls that marketing gigabytes are smaller than real-life gigabytes. That is a 320 GB hard disk is really a hard disk of 320 000 000 bytes, and would indeed be 320 GB except that 1 GB = 1024 MB, 1 MB = 1024 KB etc. So if you devide that 320 000 000 bytes with 1024 enough times to get a GB count, you'll realize it is pretty much 305 GB. Long story short I now have access to the full capacity of the drives.

I start configuration of the drives by selecting them with my arrow keys and hitting space to toggle them as part of the array...

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/013_array_creation1.jpg[/IMG]

After toggling the drives I hit enter and a configuration screen pops up. The only thing I change about the default behaviour is read-ahead which is 'adaptive' instead of 'normal'. This means that if the controller detects a large number of ordered reads it will attempt read-ahead which should increase performance.

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/014_array_creation2.jpg[/IMG]

Two physical drives from a single logical drive in RAID1:

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/015_array_creation3.jpg[/IMG]

I learn after trying to quit that the array must be initialized before it can be enabled, so I head to the initialization menu. Hit F10, and it does it's thing:

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/016_array_init1.jpg[/IMG]
[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/017_array_init2.jpg[/IMG]

Didn't take 2 seconds. I guess this step is more crucial for higher levels of RAID.

Excited to see what would happen I reboot the computer with the Ubuntu 9.10 Release Candidate disk inside.

---

### Post by blueturtl on 2009-10-26
Unfortunately, there's something wrong with the system: when it's time to partition the hard-drive I get a fairly scary error message.

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/018_ubuntu_karmic_install.jpg[/IMG]

At this point I become a little worried. It's an old card sure, but I'd expect support for it to be perfected by now, not deprecated. I download and burn the latest stable Debian 5.0.3 Lenny and run it's installer (I was using Lenny on this system anyway, but would have liked to dual-boot Ubuntu for at least testing purposes).

By the time I get to the partitioning tool I'm reminded why I migrated to Debian in the first place. It often works when Ubuntu doesn't!

[IMG]http://www.saunalahti.fi/~anmodino/comps/longbottom/epic_raidproject/019_debian_lenny_install.jpg[/IMG]

There are perks to stability I guess. I have now partitioned the drive (left space for Ubuntu or another distribution) and installed Debian successfully. No errors, no hiccups. Everything seems to work just fine.

I am yet to run many tests, but the system doesn't seem any slower than it was before at least. Also the laptop drives are inaudible period. The Seagate desktop drive was quiet, but with these babies it feels like my system is running without any hard-disks. There are no audible sounds whatsoever. Also adding to the creepy feeling is the fact my hard-disk indicator led no longer works. I guess that's because it's connected to my motherboard.

I will set everything back the way it was and post some after benchmarks for you guys as soon as I have the time. For now, the wife expects some family time from me. :)

---

### Post by sloggerkhan on 2009-10-27
Ubuntu text or server install probably would have gone the same as Debian install.

---

### Post by blueturtl on 2009-10-27
> Ubuntu text or server install probably would have gone the same as Debian install.

I will be looking into that. This is not the first time I've had trouble with the partitioning faze of Ubuntu installation. Though I have to add that for typical hardware Ubuntu usually works flawlessly. It's these 'epic fixes' I got lying around here that are troublesome. :)

---

### Post by CharlesA on 2009-10-27
Nice quick fix!

---

### Post by blueturtl on 2009-10-27
[SIZE="5"]Tests: After[/SIZE]

I've decided to include both the 'before' and 'after' tests in this post for easy comparison.
[COLOR="Blue"]Blue[/COLOR] indicates before RAID and [COLOR="Red"]red[/COLOR] indicates after. Let's get started shall we. ;)

[SIZE="4"]Test1: Startup to login prompt
[/SIZE]Test is conducted under Debian 5.0.3 "Lenny".
Runlevel 2 services: acpid, atd, cron, cups, dbus, exim4, hald, nfs-common, rsync, rsyslogd, rmnologin, rc.local, sshd, statd
[COLOR="Blue"]Time to reach login screen: 30sec[/COLOR]
[COLOR="Red"]Time to reach login screen: 42sec[/COLOR]

Notes: Single 7200 rpm disk beats a RAID1 array consisting of two 5400 rpm disks. However there is a delay right after GRUB before the system starts loading that was not there pre-RAID. I suspect based on later tests that the load time is actually the same when it depends on disk I/O.

[SIZE="4"]Test2: Startup X.org and environment[/SIZE]
Test is conducted under Debian 5.0.3 "Lenny".
xinit runs startfluxbox script which runs the following: Fluxbox, conky, xscreensaver, urxvtd
[COLOR="Blue"]Time once X is fully loaded: 13sec[/COLOR]
[COLOR="Red"]Time once X is fully loaded: 12sec[/COLOR]

Notes: Within margin of error. Either no speed difference, or minor victory for RAID1.

[SIZE="4"]Test3: Firefox cold start[/SIZE]
Test conducted under Debian 5.0.3 "Lenny":
[COLOR="Blue"]Time measured: 10sec[/COLOR]
[COLOR="Red"]Time measured: 12sec[/COLOR]

Test conducted under Ubuntu 9.10 "Karmic Koala":
[COLOR="Blue"]Time measured: 11 sec[/COLOR]
[COLOR="Red"]Time measured: 13 sec[/COLOR]

Notes: Retested Firefox cold start after realizing certain apps may load it's dependencies. As a result the speed difference between RAID and non-RAID is now negligible. It appears the RAID causes exactly two seconds of delay when comparing the results from both operating systems.

[SIZE="4"]Test4: hdparm -tT[/SIZE]
Test is conducted under Debian 5.0.3 "Lenny".
Command is run three times in a row, best result grabbed.

> [COLOR="Blue"]/dev/hda:
Timing cached reads: 394 MB in 2.01 seconds = 196.42 MB/sec
Timing buffered disk reads: 86 MB in 3.04 seconds = 28.29 MB/sec[/COLOR]

> /[COLOR="Red"]dev/sda:
 Timing cached reads:   408 MB in  2.01 seconds = 203.41 MB/sec
 Timing buffered disk reads:   60 MB in  3.03 seconds =  19.83 MB/sec[/COLOR]


Test is conducted with Ubuntu 9.10 "Karmic Koala".
Command is run three times in a row, best result grabbed.

> /[COLOR="Blue"]dev/sda:
 Timing cached reads: 404 MB in 2.01 seconds = 201.37 MB/sec
 Timing buffered disk reads: 64 MB in 3.02 seconds = 21.18 MB/sec[/COLOR]


> /[COLOR="Red"]/dev/sda:
 Timing cached reads:   410 MB in  2.01 seconds = 204.18 MB/sec
 Timing buffered disk reads:  108 MB in  3.03 seconds =  35.69 MB[/COLOR]


Notes: Somewhat interesting results. Understandably cached reads favor the RAID because it has a better controller and because presumably the cache mechanisms on the SATA hard drives are better. However with buffered reading the system just can't keep up with the higher rpm single disk solution. This probably confirms what an earlier poster said about RAID1 not actually increasing read performance. I'm left puzzled as to why Ubuntu's pre-RAID result is so much closer to the RAID setup with Debian and why did Ubuntu score higher with the RAID. :-k Maybe something to do with how Ubuntu treated my previous disk as SCSI (/dev/sda vs /dev/hda on Debian)? The after result has to be a quirk.

[SIZE="4"]Test5: File transfer across LAN[/SIZE]
Test is conducted under Debian 5.0.3 "Lenny".
Ethernet speed cap is 100 MBit.
A single CD-ROM ISO image file (688 MB) is copied to and from a network source.
[COLOR="Blue"]Read speed: 1 Min 35 sec (~7.2 MB/s)
Write speed: 1 Min 7 sec (~10.2 MB/s)[/COLOR]

[COLOR="Red"]Read speed: 1 Min 31 sec (~7.6 MB/s)
Write speed: 1 Min 7 sec (~10.2 MB/s)[/COLOR]

Notes: Clearly write speed is either unaffected or then the network is bottlenecking this test. Read speed would suggest a slight advantage for the RAID1 array even though I expected a higher rpm drive to do better for large files.

[SIZE="4"]Test6: Ubuntu startup[/SIZE]
Test is conducted with Ubuntu 9.10 "Karmic Koala".
For the test my user has been set up to login automatically.
All settings at defaults.
Time is counted from exiting GRUB to the point where the desktop is ready to receive instructions.
[COLOR="Blue"]Time measured: 38sec[/COLOR]
[COLOR="Red"]Time measured: 50sec[/COLOR]

Notes: Same odd delay that appeared under Debian is also present in Ubuntu. Maybe this has to do with the MegaRAID card.

[SIZE="5"]Summary:[/SIZE]
Without having done these tests I doubt I would be able to tell the difference between the set ups as they are. Also benchmark data was inconclusive in some ways. I feel that if I repeated the tests the end-results might just as well favor today's loser.

All-in-all I have to say the whole project has been a success:
[LIST]
[*]I've more than doubled my /home disk capacity.
[*]I've enhanced security (one drive may fail without taking anything with it).
[*]I've reduced system noise (inaudible seek and no hum/whine).
[*]I've been able to retain performance and system stability.
[/LIST]

p.s. Ubuntu test results will be appended later if I can get the system set up.

edit: As of November 4th, I've included the results from Ubuntu 9.10.

---

### Post by miegiel on 2009-10-27
Regarding your network copy tests; on a 100Mbit/s network your max speed is a little over 10Mbyte/s. Theoretically it's 12.5Mbyte/s if 1Mbyte is 1,000,000 bytes, but there's always about 15-20% protocol overhead. If the network isn't the bottleneck usually the disks write speed to your machine or the disks write speed on the remote machine is the bottleneck.

---

### Post by cascade9 on 2009-10-27
Just a few details- 

> **blueturtl said:**
> 1) In the interest of science: Most notebook hard drives are only 5400 rpm whereas practically all big desktop hard drives are at least 7200 rpm. I want to see if RAID performance will compensate the lower spindle speed.
2) In my experience 7200 rpm drives vibrate enough to create a low humming background noise in a system. I'm testing if I can get rid of this background hum by using lower spindle speed drives. Since practically all desktop drives today are 7200 rpm I had to go with laptop hard drives.


1- Not true, actually. The WD 'green power' drives are all 5400. 
2- Pretty much. You can avoid this by isolation or suspending the drives, but thats not a fun job. 

Also, just in case you dont know, rotation speed is just one thing that impacts drive performance. Cache matters, but dont forget that the closer you go to the spindle, the worse the performance. Thats why all drives have speed drops as you get futher into the disk

Also, if your comparing results from your ST3120026A hooked up to the 440BX IDE controller, dont forget that it is only ATA/UDMA 33, and ATA 100/133 would give you some speed increase. 

BTW, theres an interesting little test with RAID here- 

[http://blogs.zdnet.com/Ou/?p=484&page=1](http://blogs.zdnet.com/Ou/?p=484&page=1)

---

### Post by blueturtl on 2009-10-27
> **miegiel said:**
> Regarding your network copy tests; on a 100Mbit/s network your max speed is a little over 10Mbyte/s. Theoretically it's 12.5Mbyte/s if 1Mbyte is 1,000,000 bytes, but there's always about 15-20% protocol overhead. If the network isn't the bottleneck usually the disks write speed to your machine or the disks write speed on the remote machine is the bottleneck.

True. This explains why I didn't get any indication of the write penalty RAID1 is supposed to inflict upon me. The read performance seemed a tad low for both the single drive and the dual drives in the RAID array, but can probably be factored to the rest of the system and not the disks. Had that result been the same I would have suspected that too was a network bottleneck but as it appears, the RAID array was able to up the transfer rate just enough for it to be out of the margin of error.

> 1- Not true, actually. The WD 'green power' drives are all 5400.
2- Pretty much. You can avoid this by isolation or suspending the drives, but thats not a fun job.


Thanks for your input. On #1, I was not aware of the WD 'green power' hard drives. They were not available at any of the local stores/vendors I was looking at. Now I know they exist.

I agree with you on #2. I've tried some quite elaborate tricks to cut down disk noise (the humming / spindle whine) being the loudest noises in today's drives and I have to say nothing has really worked out. If the disk is properly attached instead of just sitting on something soft it will vibrate and the vibration noise will depend on the computer case.

> **cascade9 said:**
> Also, just in case you don't know, rotation speed is just one thing that impacts drive performance. Cache matters, but don't forget that the closer you go to the spindle, the worse the performance. That's why all drives have speed drops as you get further into the disk

Also, if your comparing results from your ST3120026A hooked up to the 440BX IDE controller, don't forget that it is only ATA/UDMA 33, and ATA 100/133 would give you some speed increase.

This test was in no way scientific. There are way too many small changes that could account for the speed differences perceived (PATA vs. SATA, ATA100 vs. ATA33, SATA->PATA translation, 5400 rpm vs. 7200 rpm, drive mechanics & cache)... The reason I initially wanted to do performance benchmarks was that I was under the false impression that a RAID1 would boost disk performance by reading files half & half, simultaneously from both disks. However this turned out not to be the case.


> **cascade9 said:**
> BTW, theres an interesting little test with RAID here-

[http://blogs.zdnet.com/Ou/?p=484&page=1](http://blogs.zdnet.com/Ou/?p=484&page=1)

Thanks. I'll add that to the reading list.

---

### Post by cascade9 on 2009-10-28
> **blueturtl said:**
> Thanks for your input. On #1, I was not aware of the WD 'green power' hard drives. They were not available at any of the local stores/vendors I was looking at. Now I know they exist.

I agree with you on #2. I've tried some quite elaborate tricks to cut down disk noise (the humming / spindle whine) being the loudest noises in today's drives and I have to say nothing has really worked out. If the disk is properly attached instead of just sitting on something soft it will vibrate and the vibration noise will depend on the computer case.

This test was in no way scientific. There are way too many small changes that could account for the speed differences perceived (PATA vs. SATA, ATA100 vs. ATA33, SATA->PATA translation, 5400 rpm vs. 7200 rpm, drive mechanics & cache)... The reason I initially wanted to do performance benchmarks was that I was under the false impression that a RAID1 would boost disk performance by reading files half & half, simultaneously from both disks. However this turned out not to be the case.

Hmmm, I would have thought that the WD GP drives would be everywhere, they are easier to get here than a WD 7200RPM drive, but obviously not. 

Theres a few tricks I've found that help. Suspension works very well, but its not exactly fun to setup. An easier one is (and I'm being serious) to slightly stretch the drive cage, glue in some old bike innner tube, and bolt the drive back in. I've also found that making the drive heavier can help, a bit of thermal paste on the top of the drive and zipties holding an old slot 1 CPU onto the HDD cooler has taken the edge of the noise in my expereince. Or you can glue it down with thermal paste (or even epoxy with a lot of aluminum or brass powder in the mix...ask if you can have some from a keycutting place). Be carefull not to block the air holes in the drive though.

You might find RAID5 faster, even with overheads. Depends on your controller and CPU power though.

---

### Post by blueturtl on 2009-10-29
> **cascade9 said:**
> Hmmm, I would have thought that the WD GP drives would be everywhere, they are easier to get here than a WD 7200RPM drive, but obviously not. 

There's a few tricks I've found that help. Suspension works very well, but its not exactly fun to setup. An easier one is (and I'm being serious) to slightly stretch the drive cage, glue in some old bike inner tube, and bolt the drive back in. I've also found that making the drive heavier can help, a bit of thermal paste on the top of the drive and zipties holding an old slot 1 CPU onto the HDD cooler has taken the edge of the noise in my experience. Or you can glue it down with thermal paste (or even epoxy with a lot of aluminum or brass powder in the mix...ask if you can have some from a key cutting place). Be careful not to block the air holes in the drive though.

You might find RAID5 faster, even with overheads. Depends on your controller and CPU power though.

The Finnish market of 5 million people at work. You'd be surprised at some of the things we just can't get in here.

What you suggest for noise reduction sounds a little extreme even for me. However based on your suggestion I placed a metallic stapler on the computer case and it made the hum even less audible. Sometimes little things make all the difference. :)

As for RAID5, it probably would offer me superior capacity and performance. I just don't have the money or case room to go ahead with it. I could do RAID3 by adding just one more disk, but I'm not sure it's worth the effort.

--

For people interested in putting cheap SATA drives into a PATA based system, [this is the adapter I used]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=250474161300&ssPageName=STRK:MEWNX:IT"). It works just fine and it has a jumper for master/slave setup.

---

### Post by cascade9 on 2009-10-29
5 million, thats more than there is in my state (and australian states are huge). There is a total population of 22 million, but its a huge country-

[http://www.ga.gov.au/education/geoscience-basics/dimensions/aus-size-compared.jsp](http://www.ga.gov.au/education/geoscience-basics/dimensions/aus-size-compared.jsp)

Surprising that you would have troubles getting some parts, but thats importers for you. 

'Extreme', LOL. Yeah, probably. I build a water cooled system some years ago, in the days of screaming 5000 RPM CPU fans. I was really impressed at how much quieter it was, but since the CPU fan got changed to something pretty much silent, the hdd noises started driving me insane. I think I've tried most the noise solutions I've seen online for hdds since then (though I'm pretty sure I figured out the 'add mass to the hdd' myself). 

You can run RAID 5 on 3 discs. Actually, IIRC, you can run a 2 disc RAID 5 setup with mdadm. It will run as slowly as RAID 1, btu you can expand it with more discs.

---

### Post by blueturtl on 2009-10-30
Update.

I have managed to install Ubuntu 9.10 There was something wrong with the combination of my cd-rw disks, cd-writer and dvd-reader because when I first tried the alternate installer cd I was getting random read errors! I then tried another cd-rw disk and it too was a no go. Strange since the disks have been fine til now.

Anyway, I checked the md5sums on the ISO files and ended up trying the burn process once more so that I did a full blanking of the disk before burning. After that it worked! Weird. This might actually be why the Ubuntu installer failed earlier.

I now have the OS installed and will update the benchmark post with Ubuntu's results as soon as I figure out how to boot it (I did not want GRUB2, so now I have no way to boot the installed Ubuntu)!

---

### Post by blueturtl on 2009-11-04
Final post.

I was finally able to append the Ubuntu benchmarks. It took some persistence on my part because I was adamant on not having GRUB2 in my MBR (which in turn complicated things a bit). In the end I went with GRUB1 which required me to reinstall Ubuntu on EXT3 (GRUB1 does not support EXT4).

So to clarify, the benchmarks with a single disk were run with Ubuntu 9.10 Release candidate and EXT4 whereas the benchmarks on the RAID were run with Ubuntu 9.10 (Final release) and on EXT3.

Also the bug that appeared in the release candidate installer originally was most probably due to a bad burn. The release version of Karmic had no problem partitioning the RAID array. As far as I can tell, no stability problems have resulted from the MegaRAID. As it stands, Ubuntu has crashed once (probably due to something else) and Debian is yet to crash.

This concludes my RAID report. Thank you all for participating.

---

