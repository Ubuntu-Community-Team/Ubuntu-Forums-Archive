---
title: "Newbie wants to build high end server"
date: 2009-10-03
forum: Server Platforms
---

### Post by Momonishiki on 2009-10-03
Hi,

This is my first venture into the Linux forum and I am a Linux virgin.  I want to build a high performance storage server to take the place of my Synology NAS that is currently attached to my home network.

For hardware, I'm thinking of using a Tyan Tomcat board along with a Suzuka processor.  On my existing desktops, I'm using 3Ware RAID cards (9650SE).  I'm unsure as to if the on-board RAID of the Tyan is up to the task or if I should use a RAID card?  I'm planning to use 2 WD RE4 drives in RAID 1 with a plan to add another pair as my storage needs increase.

My biggest concern is that if I build this and install 64 bit Ubuntu Server, will I be able to file share across my network to my 2 Windows XP desktops, 1 XP laptop, and other networked peripherals, or will I get it built and then find great difficulty in setting up file sharing?  Note, I ask this question as someone comfortable building and overclocking Windows desktops, but who has no knowledge whatsoever of writing code or anything like that.

I've seen some guides for building a home NAS elsewhere.  However, they are always focused on someone who wants a mini-ITX solution or who wants to use various other low end components.  My goal is to end up with something where I can transfer big directories of video or photo files back and forth to the server and be pleased with the performance.  The Synology NAS is not up to the task at all.

Also, I realize this is the Ubuntu forum, but if there is another distribution better able to accomplish my goals I would of course appreciate being pointed in the right direction.

Thanks in advance for assistance!

---

### Post by undecim on 2009-10-03
Yes, you can share files easily with windows computers using samba. Samba gives you network folders that you can access from windows, or even map to drive letters.

I think you will find Ubuntu Server will work for what you need.

---

### Post by Lars Noodén on 2009-10-03
You won't need heavy processing power for serving files with samba.  

Some of the NAS appliances run very low power CPUs, so you could get by with something much more reasonably priced or save your money for drives.

You can see the specs for one of the Synology products here:
[http://www.synology.com/enu/products/DS109/spec.php](http://www.synology.com/enu/products/DS109/spec.php)

Some kind samba users can collect stats into a log file for you for a 24 hour period using vmstat to see where the load is:

```

vmstat 10 8640 > /var/tmp/vmstat.log &

```

The output collected in vmstat.log can be imported into a spreadsheet to find highs, lows, averages, etc.

---

### Post by Copernicus1234 on 2009-10-03
I agree with Lars Noodén. There is no need to have a lot of processing power for just a file server.

Put the money into disk performance instead.

And its not very difficult to set up Samba file sharing. These days there is tons of information available. You can [start here]("https://help.ubuntu.com/community/SettingUpSamba") if you like.

---

### Post by Lars Noodén on 2009-10-03
> **Momonishiki said:**
> 
 My goal is to end up with something where I can transfer big directories of video or photo files back and forth to the server and be pleased with the performance.  


You may want to look at RAID 0, then, or RAID 10 or 50.  The bottleneck for your proposed system will more likely be the data bus / IO than the CPU or perhaps even RAM.

Also calculate your bandwidth for your LAN and make sure the server, router/switch and your clients all have gigabit ethernet or faster.

---

### Post by mixmaster on 2009-10-03
I'm currently building a fileserver based on the tranquilpc BBS2.  This has a dual-core atom with 2Gb memory and can hold up to 5 drives in tool-free bays.  My 2x2Tb RAID 1 array is synching as I write this and I will migrate up to RAID 5 as my needs increase.  The enclosure is an 8" cube and can take a similar eSata extension enclosure with 5 more bays if you are daft enough to use that - personally I'd prefer another 5-driver server.

I'm using software raid as my needs are write-occasionally read-frequently (WORF ?).  If you have heavy write-access then software RAID 5 might be a performance bottleneck (this is speculation - I have no benchmarks).

With your requirements I agree with the previous suggestion that the LAN may be your bottleneck.

---

### Post by Momonishiki on 2009-10-03
Thanks for all the replies.

My home LAN is Gigabit end to end, so I don't think my LAN is currently the bottleneck.

As an experiment, I ran HD Tune on my current desktop with the processor running at 1.5Ghz and at my standard 4Ghz (see attached).  There is an impact to file transfer performance depending on system processing power, but it is relatively small even in such an extreme example.

---

### Post by windependence on 2009-10-04
You'll almost never get full gig speed out of a gig NIC. I use FreeNAS and bind together three NICs for tons of throughput. As some have stated, processor doesn't matter once you get above 1GHz and more than one core is just waste. Spend money on your controller and disks. If you have money to spend, you could go SAS instead of SATA, or even solid state with enough disks if speed is your goal. FreeNAS is built on FreeBSD which IMHO performs better than Linux for this kind of thing.

-Tim

---

### Post by houstonbofh on 2009-10-04
Another vote for FreeNAS and a lot of disks for speed. Very easy to set up, totally open, and cheap.

---

