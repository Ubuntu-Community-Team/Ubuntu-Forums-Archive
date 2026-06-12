---
title: "building a NAS / streaming server"
date: 2011-11-01
forum: Server Platforms
---

### Post by Linux&amp;Gsus on 2011-11-01
We are planning on building a NAS server to store a lot of media files with the intention to be able to stream video and audio into different rooms. Meaning, only internal network, not streaming over the internet.

I am not really familiar with the demands on streaming video and audio. Videos will be DVD quality, audio most likely MP3 files with voice only, so lower quality/bit rates can be expected.

Now, if I want to stream 5 different videos to 5 different rooms within the network, what kind of hardware do I need for that, in order to play the video smoothly?

1Gbit network is available, though I assume that 100Mbit for the client machine would be fast enough to play that type of footage, right?

What do I need to make sure 5 videos can be read off the HDDs without causing jumping sound or picture?
RAID is the obvious choice, this is needed for the amount of data to be stored, anyway. The question is, will e.g. a RAID 5 be able to handle that load, does it need a RAID 10? Or is it necessary to build 2 of these boxes with load balancing? I guess the question here is, how much can the HDDs deliver in a certain configuration?

What role do CPU and RAM play for streaming? I assume that this also depends a little bit on the system installed on the NAS.

Haven't 100% decided on the system yet, either Ubuntu server or FreeNAS. In Ubuntu I think the choice would be ext4 as file system. FreeNAS has UFS or ZFS as option. How do these compare for streaming? I understand that ZFS will be the most demanding out of these 3. But will that also make an impact on speed?

The NAS should be built with consumer hardware. Due to cost there isn't much option, I guess. The 4-Bay ready built NAS boxes are too small, and something bigger will cost quite a lot of money.
Are there any suggestions on what to look out for in terms of the hardware? Any preferred HDDs, amount of RAM, CPU, etc.

---

### Post by aeiah on 2011-11-01
without any tweaking i get about 20mb/s ftp download over my lan. what's the bitrate of your videos? if a 2 hour movie is 8gb, then thats 8000mb/120m = 66mb per minute. about 1mb/s

so really, i guess you just have to make sure your disks can read, say, 5 different things each at 1mb/s, and that your router doesn't buckle whilst sending it to 5 different clients. 

to be honest, i dont see you having much of a problem. remember, the nas isn't decoding all the videos, its just uploading files to clients.

best thing to do would be to set up a test environment with the hardware you already have. set up NFS and see what kind of upload speed it can handle (preferably different files to different clients)

---

### Post by Lars Noodén on 2011-11-01
The bus might be more important than the CPU and RAM because what you are doing is moving the data from the hard disk to the network as fast as possible.  

I'm not sure whether RAID 10 is better for long reads than RAID 5, one test shows [read performance](http://www.zdnet.com/blog/ou/comprehensive-raid-performance-report/484?pg=3) to be about the same.  [Another](http://www.tomshardware.co.uk/forum/244377-14-raid-raid-raid) shows 10 being clearly faster than 5, for smaller arrays.  

You might need multiple network interfaces so that you can get more throughput using ethernet bonding.  If they are all on the same router then this will help.

---

### Post by Linux&amp;Gsus on 2011-11-02
@aeiah
Thanks for the info, that gives hope. A single server might be more capable then I thought it would be. Actually, I doubt that the videos are anywhere near that quality. This is something I have to figure out, as I'm not working on anything video related. Most of these are actually more like recorded teaching session, so don't think as in movie or TV show. Quality does not need to be over the top.
From that point of view I think it might be doable with one NAS, as long as the HDDs can keep up with reading the data. I'll definitely will set up something to test that.


@Lars
Thanks for the info and the links. Haven't fully read through both of them, but there is good info there. I actually think that a RAID 10 might not be the best solution. Gotta do a little more research on that to see what suits best.
I thought about having 2x 1Gbit ethernet cards for the NAS, I guess that should be enough throughput. Also, in case a ethernet card breaks, a port on the switch, or a cable has an issue, I don't want the server to be down completely. These things are not really that expensive, so yes, I'm planning for 2 network interfaces.


Are there any more hints?
What HDDs would be up for the job, suggestions regarding Ubuntu server vs FreeNAS (yes, yes, I know this is a Ubuntu forum :) I do expect the bias, but some real world user experience on both, or similar systems, would be nice...). What about file system, how much RAM is enough or when is it becoming overkill (though I understand that ZFS on FreeNAS would need around 1GB RAM for 1TB HDD storage, no matter of the demand of the I/O).
It would just be great to get some real world experience.

---

### Post by arrrghhh on 2011-11-02
> **Linux&Gsus said:**
> Are there any more hints?
What HDDs would be up for the job, suggestions regarding Ubuntu server vs FreeNAS (yes, yes, I know this is a Ubuntu forum :) I do expect the bias, but some real world user experience on both, or similar systems, would be nice...). What about file system, how much RAM is enough or when is it becoming overkill (though I understand that ZFS on FreeNAS would need around 1GB RAM for 1TB HDD storage, no matter of the demand of the I/O).
It would just be great to get some real world experience.

Well, I have a really similar setup to you - minus the 5 clients thing.  The most I've had running is my PS3 streaming via UPnP, and my girlfriend's laptop streaming something else over samba.  No hiccups to speak of.

What are the clients?  How would you be streaming to them?  If there's any transcoding involved, forget it.  If you're just making the files avaiable and 'streaming' over SMB or NFS or even UPnP, I would *think* it would be fine.  I can't say for sure, as I've never actually tried - that and my server is pretty beefy, on a gigabit LAN.

---

### Post by CharlesA on 2011-11-02
> **arrrghhh said:**
> Well, I have a really similar setup to you - minus the 5 clients thing.  The most I've had running is my PS3 streaming via UPnP, and my girlfriend's laptop streaming something else over samba.  No hiccups to speak of.

What are the clients?  How would you be streaming to them?  If there's any transcoding involved, forget it.  If you're just making the files avaiable and 'streaming' over SMB or NFS or even UPnP, I would *think* it would be fine.  I can't say for sure, as I've never actually tried - that and my server is pretty beefy, on a gigabit LAN.
I'm running a RAID-5 and streaming to two or three clients over Samba, no hiccups here either. There might be a little bit if one of the clients is going over wireless, but otherwise nothing big.

---

### Post by Lars Noodén on 2011-11-02
@CharlesA, what, if any, kind of load does software RAID 5 put on the CPU?  The articles I found were kind of weak on that information.

---

### Post by CharlesA on 2011-11-02
> **Lars Noodén said:**
> @CharlesA, what, if any, kind of load does software RAID 5 put on the CPU?  The articles I found were kind of weak on that information.
Not much usually, but I am using the same box as a VM host, so it can vary a bit.

I do notice that if I am doing transfers to/from USB, it kicks the load up a bit.

---

### Post by Linux&amp;Gsus on 2011-11-03
I just tried a FreeNAS setup with some hardware I have here at home. At first I had problems creating shares for others to access those, but eventually I got NFS working, SAMBA hasn't come alive yet. But as I'm new to FreeNAS, I'll keep trying.
I put up some of my videos and played on 2 Linux laptops 4 videos, so 2 on each. It played without a problem, good sound (funny seeing 4 pictures and hearing 4 different sounds at once, when a quiet part in one of them doesn't fit with the sound of the loudest, at any give time...) smooth playing, no problems as far as I can see. All that on a 100MBit network, server 100Mbit, a Modem/Router/4-Port-Switch with 100Mbit, and the 2 laptops.

In the server I have 2 80GB HDDs striped, those are 2 old IDE (P-ATA, not SATA!!) drives, a P4 3.2GHz and 768MB RAM.
RAM was maxed out, which shouldn't really be that surprising with that amount of RAM. CPU and system load don't seem to be an issue.


@arrrghhh
The clients will mainly be ThinClients, connected to a Windows Terminal Server (2008 R2). Don't ask for the server specs, I'm not managing that thing. But I guess I better check with the guys that the network interface on the server can handle this without problems and not slowing down other people.
Also, no transcending is will happen on that NAS, it really is only the storage space.

@CharlesA
Am I assuming correctly that you are talking about a software RAID, rather then a hardware RAID?


All in all, I guess the big decisions to make would then be what system to use for the NAS, which RAID level suits the needs best, and the file system.
The more I read up on it, the more actually also a RAID 0+1 seems like an option. 2 sets of striped disks. If I understand that correct a RAID 5 will be able to handle the load just fine. On the other hand, again if I understand that correct, if a disks fails the RAID will be rather slow, until the failed drive is replaced and the RAID rebuilt. While the 0+1 can share the load between the 2 stripes but if 1 disk fails the other set is still operating at full speed. In other words this would be decision of cost vs speed, specifically in the event of a HDD failure. Which of these 2 are easier and/or faster to rebuild?


Since I'm not going to handle this machine in the long run, what would you guys think is easier to manage for someone who manages Windows Terminal Server. A Ubuntu server or something more dedicated like a FreeNAS?
I almost tend towards the FreeNAS, due to the web interface, which seems pretty nice and clear, and has almost only relevant options to set regarding to the task at hand. While an Ubuntu server might be more flexible, I don't think it would be needed.

---

### Post by Lars Noodén on 2011-11-03
> **Linux&Gsus said:**
> The more I read up on it, the more actually also a RAID 0+1 seems like an option. 

RAID 01 is not as robust as RAID 10, they're opposites.

---

### Post by CharlesA on 2011-11-03
> **Linux&Gsus said:**
> 
@CharlesA
Am I assuming correctly that you are talking about a software RAID, rather then a hardware RAID?

Running a cheap hardware RAID card on my box. Haven't really messed with software RAID all that much.

---

### Post by a2j on 2011-11-03
my RAID6 server can do over 100MB/s reads. That is more than enough to play 8+Gb video files. Sometimes, 1Gbs network is the bottle neck.

---

### Post by rubylaser on 2011-11-03
> **a2j said:**
> my RAID6 server can do over 100MB/s reads. That is more than enough to play 8+Gb video files. Sometimes, 1Gbs network is the bottle neck.

Gigabit ethernet is capable of 125 MB/s.  Bluray movies tend to max out bitrate around 40 Mb/s (or around 5 MB/s).  Unless you have defective hardware, gigabit ethernet is not the bottleneck for a streaming media server, unless you're trying to stream high bitrate content to ALOT of users.

---

### Post by aeiah on 2011-11-03
> **Linux&Gsus said:**
> 
I almost tend towards the FreeNAS, due to the web interface, which seems pretty nice and clear, and has almost only relevant options to set regarding to the task at hand. While an Ubuntu server might be more flexible, I don't think it would be needed.

you could look at the capabilities of [webmin]("http://www.webmin.com/"), but you're probably right, you might not need the added capabilities of a full linux server, ubuntu or other. all you're really doing is creating a file storage server after all and FreeNAS is probably a good bet

---

### Post by maikel.b on 2011-11-03
Hello,

Consider to use an Ethernet card  with 1000M-bits.

And use 2 or 1 good router, then you will be able to stream without any problems.

Kind regards.

And don´t forget to buy this stuff :popcorn:

---

### Post by Linux&amp;Gsus on 2011-11-05
Thank you all that is great info. Thumbs up.


> **Lars Noodén said:**
> RAID 01 is not as robust as RAID 10, they're opposites.
Yes, that's right, they are very different. But at first I thought I can't do what I want/need to do with RAID 10, hence my thoughts regarding RAID 01. I'm not overly familiar in this area, so it took me a 2nd look to realise that there is actually no problem with having 6 or 8 disks as one big volume. So, yes, RAID 10 is more robust.



> **CharlesA said:**
> Running a cheap hardware RAID card on my box. Haven't really messed with software RAID all that much.
I see. So the controller card is doing most the processing for the RAID, if I understand that correct. I'll definitely go with a software RAID.

Does anyone know, is there much difference in processing needs for RAID 0, 1, 5, 10?



> **aeiah said:**
> you could look at the capabilities of [webmin]("http://www.webmin.com/"), but you're probably right, you might not need the added capabilities of a full linux server, ubuntu or other. all you're really doing is creating a file storage server after all and FreeNAS is probably a good bet
I know Webmin, use it all the time. It's far more capable then I need in my little network at home. However, this isn't so much about me and since I thought the NAS doesn't need all the other general server capabilities and possibilities it might be easier for a person who is used to MS to not have all the extra stuff in a web interface. Also prevents from playing around where people shouldn't. :D
So, for plain storage of data FreeNAS actually seems more attractive to me, in this case. Unless there is a point I'm missing. But I guess it would do the job just fine.




> **maikel.b said:**
> Hello,

Consider to use an Ethernet card  with 1000M-bits.

And use 2 or 1 good router, then you will be able to stream without any problems.

Kind regards.

And don´t forget to buy this stuff :popcorn:
I'm planing for 2 Gigabit interfaces, the server room has 4 Cisco Gigabit switches, I think that isn't the issue.
Rather, I'm getting a little more worried about the Terminal Server, which has to process all that information, incl. network throughput.
Of course, the popcorn needs to go on the shopping list. I doubt, though, that the average computer shop would have that. :D




Now, I have another few hardware questions.
After having established that there isn't much processing power needed, I thought that a Atom based system should be able to handle the task just fine. However, I'm having trouble finding a suitable board. Is that just me, or is there nothing available on the consumer market?
Please note, that is in Australia, I don't now about others countries, but only Australian shops are relevant here.
I found 1 board with an integrated Atom D525 (Dual 1.8GHz), that can handle 8GB RAM, has 4 SATA connectors, Gigabit LAN, and 1x PCI port. All others have even more limitations like max 4GB RAM, or only 2 SATA connectors.
However, I'm looking into 2 network interfaces and minimum 6xSATA better 8xSATA. So, I am either limited to 4xSATA with adding another network card, or I only have the onBoard LAN and add a SATA controller.
Is there anything I'm doing wrong in searching, or is something a little more capable simply not existing?

Speaking of SATA controller.
From what I hear, if a hardware RAID card breaks it needs to be replaced with the exact same model, otherwise the RAID is very likely lost. Is that the same with simple SATA controller cards, without RAID? Can they just be replaced by any other controller or does it need to be the same? And how about a RAID card when it's just used as SATA controller with software RAID?

Regarding hard drives.
I read somewhere that WD Caviar Green are not recommended for any RAID configuration. Is that true (why?) or is that rather a marketing comment to get people to buy drives for a few bucks more?


Sorry for the tons of questions. You might have noticed that I'm kind new to all this. My "server" needs, so far, could all be covered with any plain old hardware, with a HDD or 2.
So, I'm not entirely familiar with all aspects of this kind of stuff.

Thanks for any advice and help. It's highly appreciated.

---

### Post by CharlesA on 2011-11-05
> **Linux&Gsus said:**
> I see. So the controller card is doing most the processing for the RAID, if I understand that correct. I'll definitely go with a software RAID.

Does anyone know, is there much difference in processing needs for RAID 0, 1, 5, 10?

I doubt it's doing any processing at all, since it is a [fairly cheap card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053&Tpk=highpoint%20rocketraid%202640x1") and doesn't have any on-board memory and processors.

I just got it because it was cheap, had a linux driver and I didn't want to bother with using fakeRAID on the mobo or inside the OS itself.

Not sure on processing needs, but I do know if you use RAID 5, it needs to calculate parity, so it might take a little bit more processing power then RAID 1 or 10.

Please don't use RAID 0, unless the data you have is either backed up or you don't care about it, since if one drive goes out, you'll lose the whole array.

EDIT: I think the hardware raid card has to be replaced with either the exact model or one very similar otherwise it won't see the array.

In my case, I didn't want to deal with that if I swapped motherboards and the management tools for that were pretty much "set it in the BIOS and pray" since the software to configure it for Windows only - so I'd have to use mdadm anyway. Going hardware was just less work for me. :p

---

### Post by Linux&amp;Gsus on 2011-11-05
RAID 0 will kinda be the last option. Unless the storage space is really needed I'd prefer something like RAID 10 or 5. My problem, though, seems to be that I have trouble finding affordable hardware, specifically motherboards, with enough SATA connectors.
6 SATA Might not so much be a problem with a full sized board, but something small, Atom based, I can't find more then 4x.
Less then 6 drives is pretty much out of question, I'd say. In this case I don't see that a RAID 10 would work, as I'd "lose" 50% of the storage. So, with 2TB drives it gives 6TB storage, this might be a bit tight. RAID 5 gives 10TB. If RAID 10 I'll need at least 8 drives. Meaning, I almost don't get around a controller card.
However, I was hoping to build that on a budget as much as possible, since there might be another machine needed to build a HDD backup server.
Time will tell, I guess.

---

### Post by CharlesA on 2011-11-05
> **Linux&Gsus said:**
> RAID 0 will kinda be the last option. Unless the storage space is really needed I'd prefer something like RAID 10 or 5. My problem, though, seems to be that I have trouble finding affordable hardware, specifically motherboards, with enough SATA connectors.
6 SATA Might not so much be a problem with a full sized board, but something small, Atom based, I can't find more then 4x.
Less then 6 drives is pretty much out of question, I'd say. In this case I don't see that a RAID 10 would work, as I'd "lose" 50% of the storage. So, with 2TB drives it gives 6TB storage, this might be a bit tight. RAID 5 gives 10TB. If RAID 10 I'll need at least 8 drives. Meaning, I almost don't get around a controller card.
However, I was hoping to build that on a budget as much as possible, since there might be another machine needed to build a HDD backup server.
Time will tell, I guess.

Yeah the size factor would cause problems too. I found that out when trying to build a "cheap" HTPC (which failed miserably)

Are you wanting to run a micro ATX/Atom board for a reason?

With 6 to 10 drives, I wouldn't think space would be a problem for a full sized ATX board.

My home server is running a Core2Duo with 6GB of RAM and a 4TB RAID5 array - the drive array cost more then the rest of the components, but when I got them, 2TB drives for around 200 bucks a piece.

---

### Post by Linux&amp;Gsus on 2011-11-05
Well, I was thinking about an Atom based system after realising that I really don't need any processing power. So, why waste power and money on something like an Athlon, Phenom, i3, etc. if an Atom will do the job just fine. After some research, most of those NAS devices one can buy have an Atom processor, as well. But as I said, I can't find a suitable board for that. I guess that I'll have to go back to the Core2Duo or Athlon type CPU.

But even for those motherboard I can't find anything beyond 6 SATA connectors. As far as I know I can only have 1 device per connector, not like with the IDE where I have 2 drives on one connector. And yes, all my desktop type computers are still IDE. :D

Price for HDD, I hear you. Here they are around AU$200.
I found a Seagate Baracuda 2TB for AU$195, Baracuda Green for AU$210
Western Digital 2TB Caviar Black for AU$336, Caviar Green AU$206

Do you happen to know if it actually true that WD Caviar Green are not suited for any RAID configuration? I was reading that somewhere but I'm not sure if I should believe that or if it's to get people to buy more expensive drives.

---

### Post by CharlesA on 2011-11-06
> **Linux&Gsus said:**
> 
Do you happen to know if it actually true that WD Caviar Green are not suited for any RAID configuration? I was reading that somewhere but I'm not sure if I should believe that or if it's to get people to buy more expensive drives.

I heard the same, but I don't have any of those drives.

The ones I am using in my server are [Hitachi drives]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145298").

They've got a total of around 18K power-on hours with no problems. *knocks on wood*

But yeah, I was going to go with an atom type board at first, but decided to just go with a 65W dual core instead since I couldn't find a board with all features I wanted.

---

### Post by Linux&amp;Gsus on 2011-11-06
Found a Hitachi Deskstar 2TB for AU$191.
A Samsung I saw for AU$152, but this is a slow spinning (5400RPM) drive. Not sure if that matters so much in a RAID 10.

---

### Post by CharlesA on 2011-11-06
> **Linux&Gsus said:**
> Found a Hitachi Deskstar 2TB for AU$191.
A Samsung I saw for AU$152, but this is a slow spinning (5400RPM) drive. Not sure if that matters so much in a RAID 10.
I've read that 5400 and 7200 drives have very little difference in regards to speed, but I use 7200 drives myself.

The 5400 drives would consume less power and run cooler then the 7200s, obviously.

---

### Post by rubylaser on 2011-11-06
I'm a fan of the Hitachi 5K3000 drives.  They're 5400 RPM drives are that not advanced format,  and they work great in a mdadm array.  The power usage difference is worth going with the slower spinning drive as a few of these in a RAID array will easily saturate a gigabit connection anyways.

---

### Post by Linux&amp;Gsus on 2011-11-07
It's pretty much as I thought. Laptop drives usually are 5400RPM but for the love of me I don't recognise any speed difference to a desktop with similar specs.

Thanks to you guys I got a lot more understanding of all this. The biggest problem right now is to pick the right hardware, finding good prices, etc. Since, as far as I could find for now, 2TB HDDs are just under $200, a 8-10 disk system would be roughly $1600 - $2000 for the disks alone. Hardware is comparably pricey in Australia. So, I gotta see if we do this in 1 or in 2 stages for the full system.

Thanks again, all, for your help.

---

### Post by CharlesA on 2011-11-07
Yeah, the drives are going to be the expensive part, but I suggest buying them all at once so you don't have to worry about different models. Not sure if that makes any difference, but I try to get the same model for each drive in the array.

---

### Post by rubylaser on 2011-11-07
I would suggest you buy them from different places, so you don't get them all from the same batch.  This helps to avoid the case, where you have problems with one drive, so you're likely to have problems with all of them.

---

### Post by Linux&amp;Gsus on 2011-11-08
I wouldn't have thought that different drives in an array would cause trouble. Actually I was thinking about getting e.g. 4-5 Seagate and 4-5 Hitachi. Exactly for the reason rubylaser mentioned.
Is that something that could cause a problem? I don't know about that "advanced format" you were talking about. But I would have thought that HDD is HDD for the OS, that brand and model might have an influence on the quality and speed but not on the operation, as far as the OS is concerned. But please tell me more if that is not the case.

---

### Post by CharlesA on 2011-11-08
> **Linux&Gsus said:**
> I wouldn't have thought that different drives in an array would cause trouble. Actually I was thinking about getting e.g. 4-5 Seagate and 4-5 Hitachi. Exactly for the reason rubylaser mentioned.
Is that something that could cause a problem? I don't know about that "advanced format" you were talking about. But I would have thought that HDD is HDD for the OS, that brand and model might have an influence on the quality and speed but not on the operation, as far as the OS is concerned. But please tell me more if that is not the case.

I'm not sure if it's a myth or not but I've always been told to use the same size and model of drives in a RAID array. In regards to what ruby said, try to get the same model drive from a different retailer and go from there, that way you won't have all your drives from the same lot.

As for the advanced format drives - I haven't run into that yet, since I went out of my way to find spare drives that used 512byte sectors instead of 4K byte sectors, since my current drives use 512 bytes sectors and I have no idea what mixing them would do.

---

### Post by Linux&amp;Gsus on 2011-11-08
I see. I wasn't really aware that there is/was a change in sector size.

Of course, different size wouldn't make sense in a RAID, as the smallest drive set the max space per drive used. I wouldn't worry that if all drives are 2TB, there might be a few megs or so difference.
However, what a different sector size would do, I don't know, I don't even know why the sector size was changed. :D

Anyways, thanks for the info.
So, I'll rather look at different sources for the drives.

---

### Post by rubylaser on 2011-11-08
> **CharlesA said:**
> I'm not sure if it's a myth or not but I've always been told to use the same size and model of drives in a RAID array. In regards to what ruby said, try to get the same model drive from a different retailer and go from there, that way you won't have all your drives from the same lot.

As for the advanced format drives - I haven't run into that yet, since I went out of my way to find spare drives that used 512byte sectors instead of 4K byte sectors, since my current drives use 512 bytes sectors and I have no idea what mixing them would do.

With mdadm, the model doesn't matter, but you'll want to use partitions to ensure that your array members are all equal sizes.

You can mix and match advanced format with non-advanced format drives, but in the case of the advanced format drives, you'd want to create the partitioned with the sectors aligned for the 4K drive. Like this...
```
fdisk -H 224 -S 56 /dev/sda
```
If you use the Hitachi drives, you don't need to worry about advanced format, because they are standard 512 byte sector drives.

---

### Post by Linux&amp;Gsus on 2011-11-08
Thanks rubylaser, good to know.

---

### Post by CharlesA on 2011-11-08
> **rubylaser said:**
> With mdadm, the model doesn't matter, but you'll want to use partitions to ensure that your array members are all equal sizes.

You can mix and match advanced format with non-advanced format drives, but in the case of the advanced format drives, you'd want to create the partitioned with the sectors aligned for the 4K drive. Like this...
```
fdisk -H 224 -S 56 /dev/sda
```

Thanks for the command. That's good to know! Does it work for hardware raid too ?

> 
If you use the Hitachi drives, you don't need to worry about advanced format, because they are standard 512 byte sector drives.

Also, thanks for that, I didn't know that.

---

### Post by rubylaser on 2011-11-08
> **CharlesA said:**
> Thanks for the command. That's good to know! Does it work for hardware raid too ?


If you use them in passthrough mode it should work, I've never tried with them in a RAID array though, so I'm not sure.

---

### Post by CharlesA on 2011-11-08
> **rubylaser said:**
> If you use them in passthrough mode it should work, I've never tried with them in a RAID array though, so I'm not sure.
Ok thanks.

---

### Post by a2j on 2011-11-08
> **rubylaser said:**
> Gigabit ethernet is capable of 125 MB/s.  

sure. hard drives are also capable of 300MB/s, but when was the last time anyone was able to get those *theoretical* limits?

---

### Post by rubylaser on 2011-11-08
> **a2j said:**
> sure. hard drives are also capable of 300MB/s, but when was the last time anyone was able to get those *theoretical* limits?

I'm not sure what you mean about theoretical on either of those examples.  Here's an iperf I ran just now on a busy office network...
```
admin ~ $ iperf -c 10.1.1.75
------------------------------------------------------------
Client connecting to 10.1.1.75, TCP port 5001
TCP window size: 65.0 KByte (default)
------------------------------------------------------------
[  4] local 10.1.1.155 port 57730 connected with 10.1.1.75 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.08 GBytes   **931 Mbits/sec**
```

That's over 116 MB/s.  I routinely get between 115-121 MB/s across a single NIC to any of our work fileservers, and my home fileserver.  Sure, that's not quite 125 MB/s but it's REALLY close :)

And any [newer, quality, SSD]("http://macperformanceguide.com/Reviews-SSD-OWC-Mercury_Extreme-6G-fill-volume-mbp.html") can read and write WELL above 300 MB/s, that's why the SATAIII interface exists now to support speeds of up to 750 MB/s on a single interface.

---

### Post by a2j on 2011-11-08
yes, reading from SSD wont get you anymore than 125MB/s, because of 1Gb/s network, even though its capable of 275MB/s or more. that is what I meant in my original post.

---

### Post by Linux&amp;Gsus on 2011-11-08
a2j, I know what you mean. But isn't that exactly the reason behind a server? To have a machine that is more capable then any single client could be, thus having multiple network interfaces (even a 10Gbit interface if needed), HDDs, etc. so that you wont hit the limits of the the different components and therefore you can 100% saturate multiple clients?

If you need that kind of speed to 100% saturate multiple clients and you hit the limits of the server you might be in trouble anyway, right? Because in that case you have no headroom. Meaning, the question is, do you actually want to hit the the theoretical limits of the server?
For some situations this might not be a problem and you get much closer to the limit and therefore make more use of the theoretical maximum capabilities of the server, you waste less money on headroom. In other situations you don't actually want that to happen and you oversize so that you have enough (power, speed, space, what ever your needs are) in reserve for when it's required.

See in my case, I don't want to hit that limit. I want that server to be able to stream audio and video data to multiple clients and have enough redundancy to still be able to do so, even if, say, a network interface is down. Meaning, any old ethernet card or even thinking of having the server wireless will not do. While I wont saturate the 2x 1GBit interfaces, I still can have the machine fully operating if one of them fails, for what ever reason that might be.
The same is true for the HDDs. I wont hit the theoretical limit of the drives, and I actually don't want to.

---

