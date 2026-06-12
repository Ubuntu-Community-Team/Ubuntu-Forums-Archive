---
title: "Can single drive from a RAID 1 mirror be accessed as a normal drive?"
date: 2008-09-17
forum: Server Platforms
---

### Post by crystaline on 2008-09-17
I'm planning to setup a new file server for my home office with a couple of SATA hard drives in a RAID 1 array, most likely connected to the motherboard's onboard RAID controller (I havn't chosen the hardware yet). If one hard drive goes down, the other one will keep my data available until I can get a replacement and I can easily pick up a replacement drive the same day from any local computer store... all good.

However, if the server's motherboard was to die, obviously I can't access my data at all until the drives are setup on a new PC / motherboard so I need to be prepared for this scenario. A matching motherboard may not be something that I can replace without waiting for one to be delivered, so would I be able to plug my existing RAID array into any make/model of new motherboard that has a hardware RAID controller? Is a RAID array somehow tied to the model of RAID controller it was setup on?

Also, would I be able to simply plug one of the RAID drives into my (non-raid) desktop PC, or laptop via USB caddy, and use it like any other ext3 partitioned drive in a non-raid way?

---

### Post by windependence on 2008-09-18
I haven't tried this but since the data is not striped, I would think the answer would be yes. The odds of a mobo going bad in my experience is slim to none if it has been running for a week or two already and has been "burned in". You have a greater chance of the hard drive going. You should consider getting one more drive and using RAID5. You'll get better performance with fault tolerance, and with say three 500GB drives you get 1 TB usable space.

The other thing you have to ask is do you really need RAID? Modern hard drives will go some 300,000 hours between failures. If you keep the drive cool it will probably outlast what you are doing. Just make sure you have good backups either way because RAID is NOT a substitute for backups.

-Tim

---

### Post by crystaline on 2008-09-18
Hi Tim, thanks for the reply.

In the past, I wouldn't have considered motherboard issues but I have had the misfortune in losing two from desktop PCs over the last few years and it's made me a bit more paranoid than maybe I need to be, lol. Although chances of it happening again on any particular PC are pretty slim odds, I'd at least like some advance knowledge of how best to deal with it. It just worries me that if a RAID array is tied to a particular make/model of motherboard controller, it could take me more than a few hours, possibly days to get a replacement matching motherboard if possible at all.

The main thing I'm looking to do is minimise down time in the event of pretty much any component failing, be it hard drive, motherboard, cpu, ram, etc. I do have automated nightly backups in place, but RAID could save me losing an afternoon's work if one drive did go down and this is pretty important to me as I'm self-employed and a day restoring data from backups is a day I can't do any other work, etc. For this reason, and because it's so cheap to do these days, I would really like RAID as an extra safety net.

As for RAID 1 vs RAID 5, I have to admit I was initially planning on a 3 hard drive RAID 5 setup, but changed my mind really because I thought RAID 1 would be much simpler to manage in the long run, especially if I can just rip one of the drives out and plug it into any PC and have direct access to all the data in an emergency. I'm guessing that this definately wouldn't be possible on a RAID 5 setup, as no single drive would have a complete copy of all data.

At the end of the day, I'm after long term simplicity, as close as I can get to the simplicity of running a non-raid server, but with the benefits of data being mirrored on the fly. Performance isn't too much of an issue as it's most often just going to be me accessing it and nothing too intensive at that. Finally, cost isn't a big factor either as hard drives are cheap (and huge!!) these days.

If someone could just confirm that at least data from a RAID 1 drive can be accessed without problems by a simple non-RAID SATA controller if needed, then that would be nice to know for the future. I had previously considered a proprietary NAS box with RAID support, but that worries me even more as I know some of these use their own filesystems and would be even harder to recover from in the event of something going pop. Plus, I require server to run subversion which rules out any affordable NAS that I know of.

---

### Post by anderswestrup on 2008-09-18
If you use software based RAID1 it is no problem to use one of the drives directly in another computer. But hardware based RAID could use some extra partitions or blocks to store raid parameters, so I'm not sure if that works in all cases.

What kind of hardware RAID are you planning to use? Most motherboards with SATA RAID isn't really hardware raid, it is mostly some BIOS additions to support booting from both devices...

---

### Post by crystaline on 2008-09-18
Ahhh, thanks for the reply. What you say about hardware RAID is kind of what I feared. I was ideally hoping each drive would appear just as a completely standard ext3 (or similar) filesystem, but what you say makes sense. I think maybe I should scrub any ideas I had that a hardware RAID 1 drive is going to be useable elsewhere without a lot of fiddling.

If I forget about trying to be able to use a single drive from a RAID array in an emergency, and just treat RAID for exactly what it is, that again  opens the doors to RAID 5... Hmmmm, is RAID 5 much fiddler to setup than RAID 1?

As for type of hardware RAID controller, I'm not too sure yet to be honest. Part of my reason for posting this thread was to try and get a feel for best practices and maybe some advice on particular kit. I wasn't aware that some motherboards do it via some BIOS hacks so this is something I'll have to read up on more. I ruled out software RAID as I've read it is easier to corrupt data as compared to hardware RAID?

---

### Post by anderswestrup on 2008-09-18
One of the problems with hardware raid is that if the raid controller fails you must get a new compatible controller. If you use software raid this is not a problem. I don't see why it would be easier to get corrupted data with software raid, unless you compare with highend raid controllers with battery backed cache memories.

If you go with software RAID5, remember that you cannot have RAID5 on the /boot partition (grub or lilo doesn't support reading from RAID5), so create a small RAID1 partition for /boot and a big RAID5 for the rest.

And one more thing: I'm not sure if it is an issue to mount a disk from a hardware based raid1 separately, I just said that it *could* be a problem, and different raid hardware could behave differently

---

### Post by crystaline on 2008-09-18
Thanks anderswestrup, this is starting to make a bit more sense to me now.

Would you say software RAID is generally pretty reliable nowadays? I was scared off from it when I first considered it year or two back, but I've read of plenty of people using it without problems now and it's something I could even setup with my present hardware. I know it takes a bit of a CPU hit, but my fileserver's CPU rarely breaks into a sweat anyway. And as for speed, how would software RAID generally compare to hardware RAID read/write times? Or to a non-raid drive for that matter?

---

### Post by Krupski on 2008-09-18
> **windependence said:**
> I haven't tried this but since the data is not striped, I would think the answer would be yes.

For what it's worth... individual drives from a RAID 1 (mirror) array that were setup using MDADM *can* be accessed individually.

I tried it - it works.

Just don't WRITE anything to one drive or the array will have to re-sync if the drives are put back into RAID service.

-- Roger

---

### Post by crystaline on 2008-09-18
> **Krupski said:**
> For what it's worth... individual drives from a RAID 1 (mirror) array that were setup using MDADM *can* be accessed individually.

I tried it - it works.

Just don't WRITE anything to one drive or the array will have to re-sync if the drives are put back into RAID service.

-- Roger

Thanks for clarifying that Roger. As you're using MDADM already, can you vouch for it's general stability and reliability? And do you notice any significant load on the CPU doing it in software?

---

### Post by Krupski on 2008-09-18
> **crystaline said:**
> Thanks for clarifying that Roger. As you're using MDADM already, can you vouch for it's general stability and reliability? And do you notice any significant load on the CPU doing it in software?

Yes I am using MDADM for a home file server box. One box has two 1TB drives setup as RAID-1 and the other box has four 1TB drives setup as RAID 0+1. The OS is Ubuntu Server 64 bit v8.04.1

MADAM seems to be very stable. I have had zero problems with it.

Performance-wise, the bottleneck is always the hard drives. When I push the drives to the max (copying multiple files from multiple sources all at once), the CPU usage barely creeps up above idle.

Now, RAID 5 (which I don't use) and other RAID levels that do parity and checksumming (i.e. more CPU intensive RAID algorithms) will probably consume more CPU power... I don't know how much though.

Hope this answers your question.

-- Roger

---

### Post by fjgaude on 2008-09-18
I've been using, testing mdadm for over two years with good results. I use raid5 in a four-drive array.

My system is a dual-core Intel E8400 that's very fast, with 4GB of RAM. The CPU usage during write-heavy array access is moderate, like 15% total.

Not knowing what your intended useage will be it is hard to say how the CPU performance might be.

Using raid5 increasing data throughput over a single drive, like one drive's performance times the number of drives minus one. For example, if one drive has a 70MB/sec throughput, than a three-drive raid5 will have 140MB/sec, if your controller bus is other than PCI. Both PCI-X and -E will give you over 350MB/sec if your array is large enough.

Let us know what you decide... many folks here have lots of **mdadm** experience, a very good program but one that has a steep learning curve, if you know what I mean. <smile>

---

### Post by crystaline on 2008-09-18
Thanks Roger, that's very informative!

I'm going to order a new pair of SATA drives reasonably soon so I think I'm going to initially setup a software RAID 1 server with them and experiment with that. I was tempted to build a low power server, maybe based on the Intel Atom so it's nice to know CPU load isn't really an issue.

---

### Post by crystaline on 2008-09-18
> **fjgaude said:**
> 
Not knowing what your intended useage will be it is hard to say how the CPU performance might be.


It's my intention that the server will run Ubuntu Server (I run Ubuntu on all my desktop/laptop PCs so it's what I'm most familiar with) to provide SAMBA, NFS and Subversion services to myself and maybe one other person as part of a small web development business. It's to replace my ageing ~1.2GHz, 256MB RAM CentOS server which actually served me very well, but is now moving on to digital retirement. I was also hoping to eventually use it as an office IMAP mail server too, again serving only 2 or 3 people.

> **fjgaude said:**
> 
Using raid5 increasing data throughput over a single drive, like one drive's performance times the number of drives minus one. For example, if one drive has a 70MB/sec throughput, than a three-drive raid5 will have 140MB/sec, if your controller bus is other than PCI. Both PCI-X and -E will give you over 350MB/sec if your array is large enough.

RAID 5 does sound very attractive from the speed point of view, definitely something I'm going to consider, but would RAID 1 not also give a similar speed boost? Have to admit, I'm still leaning towards RAID 1 because it sounds simpler to setup! But then, I don't mind getting my hands dirty if RAID 5 will be sufficiently beneficial... :)
 
> **fjgaude said:**
> 
Let us know what you decide... many folks here have lots of **mdadm** experience, a very good program but one that has a steep learning curve, if you know what I mean. <smile>

Thanks, I'll certainly do that. I only heard about mdadm for the first time in the last couple of weeks so I've got plenty of learning to do!

Many thanks!

---

### Post by fjgaude on 2008-09-18
Raid1 is mirroring, with no speed increase because no stripping.

Let us know what the CPU is on the new server.

---

### Post by crystaline on 2008-09-18
> **fjgaude said:**
> Raid1 is mirroring, with no speed increase because no stripping.

Let us know what the CPU is on the new server.

I had presumed because it was mirrored, data requests could be spread between the two drives, effectively doubling access times, but I guess that's what striping is for... Hmmm, makes me sway back over to RAID 5 now! :)

I have been thinking about Atom processors because of their lower power usage. I'd like to build a low power and quiet server if possible, as it will be idle for long periods of time and nothing too intensive going on even at peak times. But if I'm talking RAID 5, with three drives then I don't know how 'low power' I'm going to get it and not sure if the Atom will be up the job.

Many months ago, when I first planned to replace my file server, it was going to be a non-raid VIA processor based Mini-ITX affair, but I'll forget about that for now because I really can't see that handling everything I want it to any more. If anyone has suggestions for something with a bit more horsepower but still quiet and lower power, I'd be very grateful.

---

### Post by fjgaude on 2008-09-18
Just to let you know, you cannot boot off of a software raid5 array.

A three-drive raid5 with three big, like terabyte, drives likely will work fine with a CPU clock of about 1.2 GHz. Now to get the double one-drive throughput, your drive controller will have to be better than PCI, which would give you about 110 MB/sec for three 70 MB/sec drives in raid5.

Things to study about software raid:

 [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Good luck!

---

### Post by crystaline on 2008-09-18
> **fjgaude said:**
> Just to let you know, you cannot boot off of a software raid5 array.

A three-drive raid5 with three big, like terabyte, drives likely will work fine with a CPU clock of about 1.2 GHz. Now to get the double one-drive throughput, your drive controller will have to be better than PCI, which would give you about 110 MB/sec for three 70 MB/sec drives in raid5.

Things to study about software raid:

 [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Good luck!

Thanks for the info fjgaude, and thanks for the links too! They look very useful and I'll read through them this evening.

---

### Post by windependence on 2008-09-19
> **crystaline said:**
> I had presumed because it was mirrored, data requests could be spread between the two drives, effectively doubling access times, but I guess that's what striping is for... Hmmm, makes me sway back over to RAID 5 now! :)

I have been thinking about Atom processors because of their lower power usage. I'd like to build a low power and quiet server if possible, as it will be idle for long periods of time and nothing too intensive going on even at peak times. But if I'm talking RAID 5, with three drives then I don't know how 'low power' I'm going to get it and not sure if the Atom will be up the job.

Many months ago, when I first planned to replace my file server, it was going to be a non-raid VIA processor based Mini-ITX affair, but I'll forget about that for now because I really can't see that handling everything I want it to any more. If anyone has suggestions for something with a bit more horsepower but still quiet and lower power, I'd be very grateful.

There's two schools of thought when talking about RAID. You have your hardware RAID proponents (me) and your software RAID proponents. I have to say I have come a long way to accepting software RAID, and I have to say that each has it's own advantages. 

With hardware RAID, in my production boxes, I eliminate the controller failure argument by keeping a spare RAID controller on hand. Problem solved. I have to say that I can't remember the last time a RAID controller failed in the thousands of servers we have where I work. It certainly can and does happen. One of the advantages of hardware RAID is that it's simple. Simple to set up and simple to maintain. That's the tradeoff for having to use a separate controller card. With hardware RAID, you install your drives, boot up and enter the controller config much like you enter the BIOS of your motherboard. From there, you select what kind of RAID you want i.e. RAID5, etc., and then add the drives to the array. Done. Battery backup on high end cards allows faster journalled rebuilds and battery-backed write-back cache may improve write throughput also

Software RAID is a little more involved and this is why I'm gonna say for you I think hardware RAID would be better for two reasons. You said yourself that you don't want to be fudging around rebuilding stuff if it breaks. Some here will shoot me for saying this but with software RAID it will take you longer to fix a problem than hardware RAID. For proof, just go through the last 5 pages of this forum (about 1 week of posts) and see how many "My software RAID is hosed" threads you can find. I doubt you will find any hardware RAID threads. Also, if you are going to use a low power CPU, software RAID takes CPU cycles because the work is being done on your CPU and not on the RAID card.

As for RAID5 vs RAID1? Hands down RAID5. The advantage is you have peformance and fault tolerance all in one. You can lose one drive and just keep going. With RAID1 you lose half the space with no performance increase.

For low power and quiet, I recommend AMD's Cool 'n Quiet technology. Yes, I am biased because I am an AMD partner but I have to tell you the boxes are really quiet with the modern fans. You can hardly hear them run. They're cheaper too. As for the hard drives, really, all the people here seem to think these things take a huge amount of power for some reason. In reality it's miniscule.

Some articles of interest:

[http://searchstorage.techtarget.com/expert/KnowledgebaseAnswer/0,289625,sid5_gci1153747,00.html](http://searchstorage.techtarget.com/expert/KnowledgebaseAnswer/0,289625,sid5_gci1153747,00.html)

[http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html)

[http://www.linuxplanet.com/linuxplanet/tutorials/4349/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4349/1/)

-Tim

---

### Post by crystaline on 2008-09-19
Tim, that's just the kind of advice I was looking for! :) Thank you for explaining it to me so well.

As you suggested, I have scanned through previous posts along with some general googling and software RAID does give me the impression that it's certainly going to be: 1) more difficult to setup and with a steeper learning curve, and 2) in case of problems, more time consuming and difficult to remedy.

So, I've now got it clear in my head that I'm going to build a 3 drive RAID 5 array, connected via a decent hardware RAID controller (and with an identical controller as spare). I don't know yet if I'll be able to get all of this into a slighter bigger than average mini-ITX (medium-ITX???) case which would be nice, but with the RAID logic handled by the controller card I can still go for a lower power Intel Atom or AMD Cool 'n Quiet processor and not have to worry about lots of CPU cycles dealing with every read/write request. Sounds great to me so far!

If anyone could recommend some decent controller cards (that don't cost the Earth) that would be smashing. And if anyone out there is doing something similar in a relatively compact, quiet and low power case/motherboard/controller/cpu setup I'd also love to hear how you've got on and with what hardware you'd recommend!

One other thing I remember reading; I've heard it suggested that you should use drives from different suppliers or even different manufacturers to minimise the possibility you get two or more drives from the same batch, just in case you're unlucky enough to get a bad batch. Is this going over the top or is it recommended practice?

Again, thanks for all your help, I've found this an incredibly useful thread.

---

### Post by fjgaude on 2008-09-21
I just noticed a test of the latest Adaptec raid controllers, the quickest, the ASR-3405 costs $2800.00 and has about the same throughput as my software raid5 array, both 4-drives, about 200MB/sec.

[http://www.xbitlabs.com/articles/storage/display/adaptec-controllers.html](http://www.xbitlabs.com/articles/storage/display/adaptec-controllers.html)

All the lower priced controllers in the $300 to $600 range cannot compete.

So the future seems to point to PCI-E SATA running from motherboard controllers. That's true right now for workstations.

Linux software raid is moving to set the path to high performance, open source, at low prices.

---

