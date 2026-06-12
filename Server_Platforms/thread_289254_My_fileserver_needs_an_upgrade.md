---
title: "My fileserver needs an upgrade"
date: 2006-10-30
forum: Server Platforms
---

### Post by Abild on 2006-10-30
Hi

My fileserver is in serious need for an upgrade.

Currently i have 4 160gb Hitachi 7K250 on a Promise SX4000 controller with 128mb cache. The disks are set up in RAID 5. The disks and the controller have now endured more than 2 1/2 year of 24/7 operation. So I'm getting increasingly concerned about how much longer they will live. I would like to replace all of the disks before the first one dies so i wont have to buy an outdated replacement disk. I'm also starting to run out of disk space.

Also I'm currently stuck with windows on my file server because I've formatted the RAID array as NTFS. All my other computers are now running Linux. I was also forced to set up a second server for web, FTP etc with Linux. I want to get rid of that one as well now so i will only have one server with Linux.

Reliability is my top requirement, price is important to. Performance isn't that important since most data will be transfered over a 100mbit network.

Currently I'm thinking of buying 4 320gb Hitachi T7K500 and a Promise SATA300 TX4 controller and set them up in RAID 5 with Linux software RAID. I don't know how reliable Hitachi drives are but I currently have 9 Hitachi drives in use (all form the 7K250 series) with the oldest being about 3 years old. None of them have crashed on me yet. I'm considering software raid over Hardware raid because it's cheaper and because it can be expanded beyond the number of disks supported by one controller. It's also not bound to a specific RAID controller

In my search for a SATA controller I also found a Stlab 4-port SATA150 controller. It doesn't support SATA300, NCQ, TCQ or any other fancy stuff but it's about 1/5 of the price of the Promise controller. After all a HD controller is not a very complex peace of hardware. Stlabs controllers consists of a Silicon Image chip put on top of a pretty much standardized circuit board. What are you thoughts about this. Any reason why i should go with the more expensive Promise controller?

The alternative solution is, of course, that i buy 4 P-ATA hd's and keep using my current Promise controller but I'm feeling quite bad about investing in P-ATA drives today. Would that in your opinion be preferable?

I wanted to ask you guys what you think about the above. Would you have done anything different?

I've also got some miscellaneous questions

1) The two servers i mentioned earlier have the following specs: Compaq deskpro <something> 1,7ghz p4 (the old Willamette), 256 MB good old SD RAM, 17gb SCSI disks and the other is a Dell Dimension 8100 with 1,5ghz Pentium 4 (also Willamette), 256mb RD-RAM. The biggest difference is RD vs SD ram (I can always swap the cpu's). Does RD provide any significant performance increase compared to SD?
I can't decide on which one to choose. Which one would you have chosen? The chosen one will undergo a ram upgrade.

2) Does anyone know what sort of performance i can expect from software raid 5 and how much cpu power does the parity calculations require?

3) Which file system is best suited for servers? ext3, ReiserFS or something else? I'm using ReiserFS on all my desktops and I'm quite happy with it, but i don't know whats best for servers.

Thanks in advance

---

### Post by blind0wl on 2006-10-30
Hi Abild,

RD over SD isnt a huge factor in the RAM stakes, I suppose the only difference is that RDRAM has a memory bandwidth of about 2gig, which in effect increases performance of applications, but then you need to weigh up whether the extra 200Mhz of CPU grunt versus the type of RAM your using outweighs each other and also the use of the server, if its a file server the benefits of RDRAM isnt going to help you :D 

Software RAID in my opinion is terrible, but then Im used to hardware RAID and the benefits it gives.  If cost is an issue, then I suppose you dont have much choice.  If your using software RAID on a high output file server...watch out for the CPU cycles (especially RAID5), which is inherently slow in the first place.

Again the file system will depend on the types of files your going to be serving or storing on the server.  If you have a lot of small files...reiserfs would be perfect for it, whereas proven stability would probably require ext3.

Dont know if I answered any of the questions you posed, but I hope it helped in any case

Cheers
Blindy

---

### Post by Abild on 2006-10-30
Thanks for your reply

[QUOTE=blind0wl]RD over SD isnt a huge factor in the RAM stakes, I suppose the only difference is that RDRAM has a memory bandwidth of about 2gig, which in effect increases performance of applications, but then you need to weigh up whether the extra 200Mhz of CPU grunt versus the type of RAM your using outweighs each other and also the use of the server, if its a file server the benefits of RDRAM isnt going to help you  [/QUOTE]
I think I'll go with the Compaq then. SD is much cheaper than RD.

[QUOTE=blind0wl]Software RAID in my opinion is terrible, but then Im used to hardware RAID and the benefits it gives. If cost is an issue, then I suppose you dont have much choice. If your using software RAID on a high output file server...watch out for the CPU cycles (especially RAID5), which is inherently slow in the first place.[/QUOTE]
I have also used nothing but hardware RAID in my life and I'm really happy with my current promise controller. I just find the flexibility and inexpensiveness of software RAID attractive. As i write in my original post performance is not that important since all file transfer is going through a 100mbit LAN connection. The CPU cycles consumed by software raid do concern me. Do you have any estimate on how much CPU power raid 5 will use?

[QUOTE=blind0wl]Again the file system will depend on the types of files your going to be serving or storing on the server. If you have a lot of small files...reiserfs would be perfect for it, whereas proven stability would probably require ext3.[/QUOTE]
I almost entirely store big files and stability is an important factor for me, so I'll probably go with ext3. I'm also a bit concerned with the future of ReiserFS after SUSE ditched support and Hans Reiser is under arrest for murdering his wife.

---

### Post by blind0wl on 2006-10-30
As far as CPU cycles go, I couldnt tell you off hand for RAID 5, however looking through google, I did come across this [http://www.beowulf.org/archive/2002-March/006575.html]("http://www.beowulf.org/archive/2002-March/006575.html")

Looks like at a peak he might be hitting ~90% usage with similar hardware CPU etc, also found another article, stating that if your not going to use the server as a workstation, by doing multiple tasks it should not be a problem at all.

Cheers

Blindy

---

### Post by Abild on 2006-10-31
> **blind0wl said:**
> As far as CPU cycles go, I couldnt tell you off hand for RAID 5, however looking through google, I did come across this [http://www.beowulf.org/archive/2002-March/006575.html]("http://www.beowulf.org/archive/2002-March/006575.html")

Looks like at a peak he might be hitting ~90% usage with similar hardware CPU etc, also found another article, stating that if your not going to use the server as a workstation, by doing multiple tasks it should not be a problem at all.

Cheers

Blindy

I've been looking for a review like that for a while. I do not, however, think that I'll be suffering from that intensive CPU usage. Partly because I only have 4 hard drives. Parity calculations for 4 hard drives must be much lighter than parity calculations for 10 HD's. And partly because I only will transfer data over a 100mbit network.

I'm thinking of upgrading to 1000mbit in the future. Then it might become a problem. Also because the PCI bus gets overloaded.

---

### Post by Abild on 2006-11-01
up

---

### Post by ktulu1115 on 2006-12-24
Not sure if you built it yet or not, but I'd have to say favorable things about RAID5 in software on Linux.

I just built one out of an old system I had laying around - Athlon64 3200+ w/ 1gb DDR400 RAM.  It runs like a hot knife through butter - 4 x 320gb drives in an array, giving 960GB total.  OS is installed on another set of older RAID1 40gb drives.

CPU usage barely climes above 25% - even benchmarking with Bonnie++ at 200mb/s didn't fully tax out the CPU.  Either of those machines should handle it no problem, just add extra RAM for caching.

I'd recommend the Coolermaster iTower930 if you're gonna go SATA RAID - great hotswap case for a decent price.  As far as filesystems go, if you're anything like me and have lots of media (AVI, MP3, etc) - I'd say go XFS...  it's designed for streaming large quantities of multimedia at a steady rate.  Used myself for years now on my desktop storage drive and never been disappointed.

---

