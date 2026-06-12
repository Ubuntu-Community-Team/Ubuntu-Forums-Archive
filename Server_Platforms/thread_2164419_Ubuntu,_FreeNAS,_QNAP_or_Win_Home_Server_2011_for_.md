---
title: "Ubuntu, FreeNAS, QNAP or Win Home Server 2011 for file Storage"
date: 2013-07-31
forum: Server Platforms
---

### Post by chexed on 2013-07-31
Hi everyone! I'm new to this website and new to Ubuntu. Thanks for being here!

I need to setup a file storage server. People will be writing to and from the drive all day with average reads / writes of about 100mb. Regular reads and writes of ~2 GB once or twice an hour. About 15 people will be accessing it for two different drives. *So I'm having a hard time figuring if I should build or buy two ~$400 machines or one <$800 machine.*

The problems I'm facing in addressing these issues are my lack of knowledge and a budget. Common problems I think.

I see the top options as:
**Machine I will build**
Ubuntu Server 64bit
FreeNAS
Win Home Server 2011

Specs of the machine would be:
4.1Ghz Quad Core FM2 AMD CPU-GPU-APU
16~32GB RAM
Small SSD around 64GB for OS
2x 2tb mirrored
2x 2tb mirrored

**Prebuilt NAS**
QNAP NAS ([link to prospective hardware]("http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=%2D1&IsNodeId=1&Description=qnap%204bay&bop=And&CompareItemList=%2D1%7C22%2D107%2D084%5E22%2D107%2D084%2DTS%2C22%2D107%2D109%5E22%2D107%2D109%2DTS%2C22%2D107%2D126%5E22%2D107%2D126%2DTS%2C22%2D107%2D064%5E22%2D107%2D064%2DTS%2C22%2D107%2D116%5E22%2D107%2D116%2DTS&percm=22%2D107%2D084%3A%24%24%24%24%24%24%24%3B22%2D107%2D109%3A%24%24%24%24%24%24%24%3B22%2D107%2D126%3A%24%24%24%24%24%24%24%3B22%2D107%2D064%3A%24%24%24%24%24%24%24%3B22%2D107%2D116%3A%24%24%24%24%24%24%24"))
Preinstalled no more than 1GB RAM

_What do you think the best choice is?_

Please consider I only have 2 weeks to implement a solution for our storage needs. I've only ever tinkered in Linux GUIs of varying distros, but I bought a book on PHP and learned it pretty well within about *3 months*. My gut is with Ubuntu because it seems well supported and highly configurable, but I'm worried I wont be able to learn it in time. It seems like it it's going to be tricky right from the get-go (installing it due to UEFI), then setting up two RAID 1's. I'm worried I may need to use Windows Home Server 2011, just because the interface may be more familiar to me, but then maybe it only allows 10 users or some other poor restriction. Notification of drive failure is also a must-have which is really the primary reason I even consider QNAP (little green lights).

I hope you can imagine, but not feel my stress of needing to get this done within two weeks. I'm currently reading a book on patience, ironically (or by a gift of God).

---

### Post by rubylaser on 2013-07-31
Hello :)  If you go the build it your own route, you won't need anywhere close to 16-32GB of with Ubuntu.  If you are going the FreeNAS route + ZFS, then that RAM will definitely help to make it perform better.  Can I ask why you are going with two RAID1 arrays vs. a different RAID setup (RAID5/6/ or a RAID1 made up of two 4TB drives).  Ubuntu with mdadm, smartmontools, and email alerting setup properly will work fine to give you alerts when a drive fails.  I would consider what sort of network throughput performance is expected from your users in terms of MB/s, and what does the hourly I/O look like. Also, you'll want to consider in the event of a hard drive failure if downtime to cold swap a drive is an option or not.  If it's not, you need to go with one of the higher end QNAPs that start around $800 without disks.

---

### Post by chexed on 2013-07-31
Right now we have a multi-step approach to our files.
Stage 1 - Raw files (have a server for them already)
Stage 2 - First edit (want 2tb dedicated)
Stage 3 - Final edit (want 2tb dedicated)

We need these stages, because we often have to go back a step in the edits because a customer wants something different or custom. Also, keeping these stages on separate drives allows us to plan for hardware failure. Usually when something happens, there's little lost time because we can just go back 1 edit.

Maybe I'm wrong about this, but it seems scenario 2 would perform better:
Scenario 1:
4tb Mirrored: Someones uploading 2gb & downloading 2gb at the same time.

Scenario 2:
Drive Y: 2TB Mirrored - Someone's uploading 1gb & downloading 1gb
Drive Z: 2TB Mirrored - Someone's uploading 1gb & downloading 1gb

It seems like there would be more guaranteed throughput (*2?) considering it can read from two locations at once and write to two locations at once this way. Also, the downtime to cold swap may be too much for a 4tb drive. Also 4tb drive ratings aren't up to where I feel comfortable yet! They just scare me at this point.

---

### Post by houstonbofh on 2013-07-31
If you go with FreeNAS, look at the NAS4free version.  It is the original FreeNAS developers, and has a more current FreeBSD base.  This translates to a later ZFS version and more driver support.

That said, the ZFS snapshot option is just amazing.  You may be able to do away with your separate drive concept.  It also means you can install the "OS on a USB flash drive and use the SSD for a dedicated ZIL device. (Big performance boost in iops)  Memory requirements are 1gig per TB, unless you want to use de-dupe.  (So 4-8 gig)

---

### Post by rubylaser on 2013-08-01
I would probably use ZFS for this on NAS4Free as mentioned above with two separate shares (Stage2 and Stage3).  Snapshots would be a great solution to your multiple versions, and would allow you to use four disks in, two mirrors striped together (RAID10). This would give you better IOPS potential than two standalone mirrors.  I'm sure you know this, but if all of your shares are on the same box, your throughput cap will likely be dictated by your network throughput speed rather than your backend storage volume unless you go with 10GBe or bond multiple gigabit connections.  Without one of these two setups, you will have a total of 125MB/s of throughput available to remote users via a single gigabit connection no matter how fast your storage is.  I would test the need for a ZIL before spending the money on one.

Also, all of these versions are great, but you still don't have a true backup system in place (unless you didn't mention it). I would definitely be thinking about that too.  Maybe losing days of work and rolling back to a previous version isn't that big of a deal to you, but in my industry, even a few lost hours could prevent us from submitting on multi-million dollar projects.  

Finally, I know budget is a concern, but I was building this, I would use SAS disks instead of SATA.  They are designed to perform well with multiple users accessing them instead of SATA disks that are optimized for single user, sequential operations. A 2TB SAS disk costs $189 vs ~$85-$90 for a SATA disk though, so (4) 2TB SAS disks would just about exhaust your $800 budget, so they are not really going to work in your case.

---

### Post by steve126 on 2014-05-25
I am currently running Ubuntu Server 12.04 LTS in our office.  It is easy to setup and very customizable, I just installed whatever I need to keep it simple and slim, very low resources and I even run it with a 4Gb USB stick.  Plenty of help from the internet as well as this forum.  It has been running strong since I switched from FreeNAS, which die on me TWICE due to the corrupt files of the FreeNAS OS.  QNAP is great as well if it fits your budget.

---

