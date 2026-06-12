---
title: "Anyone running Ubuntu 13.04 on HP ProLiant DL360 G5?"
date: 2013-07-08
forum: Server Platforms
---

### Post by legolas_w on 2013-07-08
Hello,

I am wondering if anyone here knows whether Ubuntu 13.04 would work on HP ProLiant DL360 G5 without any problem or extra tweaking or not?

Thanks.

---

### Post by CharlesA on 2013-07-08
I don't have one of those, but is there a reason you want to run 13.04 instead of 12.04 (which is a LTS)?

---

### Post by legolas_w on 2013-07-08
I want to use it as a file server for my media system. Though I am still unsure because I dont know how noisy and load those things are. Do you know whether putting it in a closet shield the room from the noise of such a server?

---

### Post by CharlesA on 2013-07-08
> **legolas_w said:**
> I want to use it as a file server for my media system. Though I am still unsure because I dont know how noisy and load those things are. Do you know whether putting it in a closet shield the room from the noise of such a server?

It should, but then you might run into heat/airflow issues. I have my server sitting in my dining room/living room and the noise isn't too bad, but I'm not running a 1U or 2U, so I cannot comment on the noise factor.

I have worked with some of the Dell servers (2U) at work and they can get a bit loud when you first turn them on, but after they boot the fans slow down a bit.

If you are going for a file server, go with a LTS release (IMHO at least) as they are supported for 5 years. 12.04 will be supported until April of 2015.

---

### Post by rubylaser on 2013-07-08
> **CharlesA said:**
> If you are going for a file server, go with a LTS release (IMHO at least) as they are supported for 5 years. 12.04 will be supported until April of 2015.
+1

If you are going to buy a server to act as a home fileserver, I would definitely not suggest a 1U server with 2.5" SAS drives.  If you want a good value in a well built machine, the [HP DL180 G6]("http://www.ebay.com/itm/HP-PROLIANT-DL180-G6-STORAGE-SERVER-CONFIGURE-TO-ORDER-CTO-RAILS-TRAYS-1-x-PSU-/111107320882?pt=COMP_EN_Servers&hash=item19de832c32")'s are pretty hard to beat.  Throw in an HBA like the [IBM M1015]("http://www.ebay.com/itm/IBM-ServeRAID-M1015-RAID-Controller-6-Gbps-SAS-SATA-LSI-SAS9220-8i-FRU-46M0861-/251300670569?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item3a82afec69") or [IBM BR10i]("http://www.ebay.com/itm/IBM-ServeRAID-BR10i-PCI-e-8-Port-Controller-Sata-SAS-/161049144715?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item257f46ed8b") flashed to IT mode and use mdadm or SnapRAID, or go with a hardware RAID card of your choosing (these normally came with an HP 410.  

Once the DL180's are done booting, they aren't ridiculously loud.  You'd just need to buy [(1) Intel Xeon L5520]("http://www.ebay.com/itm/INTEL-XEON-Quad-Core-Processor-L5520-2-26GHz-8MB-5-86-SLBFA-/141007597712?pt=CPUs&hash=item20d4b53090"), and a couple GB of RAM, and you'll have a great server that's actually designed to be a fileserver.  Or, go with any other standard ATX case fileserver setup over a 1U server :)

---

### Post by legolas_w on 2013-07-08
I have some external hard drives which currently hold my entire media files. I was thinking that I can connect them to the 1u server and then share them over the network. I am not looking for adding internal hard drives. On the other hand, living in europe, I dont have that many options in the second hand market and this HP ProLiant DL360 G5 is the first one I found in past three weeks.I was also thinking to take out the actual hard disk from the external drive box and put them in the server slots but I dont know about compatibility of the hard disks and the server. 

Currently the main question for me is the noise level, if it is noisy then the whole buying it will be nullified.

Thanks for the comments.

---

### Post by rubylaser on 2013-07-08
1U server almost always = noise.  You have a bunch of 40mm fans spinning fast, so noise is the result.  Also, almost all modern 1U servers use 2.5" SAS drives, and your external hard drives are likely 3.5" drives, so they won't fit inside this server.  I would definitely just build around a standard ATX case before trying to buy and use a 1U server at home.  The HP Microserver or a [Celeron 847]("http://www.amazon.co.uk/C8HM70-I-Motherboard-On-Board-Celeron-Windows/dp/B00A2EPGRQ/ref=pd_sim_sbs_computers_3/277-9348471-3081110") based system will both likely be cheaper and be far less noisy.

---

### Post by CharlesA on 2013-07-08
> **rubylaser said:**
> 1U server almost always = noise.  You have a bunch of 40mm fans spinning fast, so noise is the result.  Also, almost all modern 1U servers use 2.5" SAS drives, and your external hard drives are likely 3.5" drives, so they won't fit inside this server.  I would definitely just build around a standard ATX case before trying to buy and use a 1U server at home.  The HP Microserver or a [Celeron 847]("http://www.amazon.co.uk/C8HM70-I-Motherboard-On-Board-Celeron-Windows/dp/B00A2EPGRQ/ref=pd_sim_sbs_computers_3/277-9348471-3081110") based system will both likely be cheaper and be far less noisy.

+1. We have a 1U Core2Quad at work that we used for ESXi.. that thing is frigging LOUD. I think it's got 3 40mm fans that push a ton of air, but they are super loud.

---

### Post by newbie-user on 2013-07-09
1U servers are always loud, unless you get one of those atom-based mini-servers. I have two DL360s and they're just about as loud as any other 1U server. Unless you have a basement in which to put your server, the DL360 will certainly be too loud for a small closet. Too loud and too hot.

---

### Post by Vegan on 2013-07-09
I found that the bigger 4U chassis with 120mm fans are a lot less noise. Best bet is to create a closet and provide a cooling solution such as ventilation or outright AC

---

### Post by newbie-user on 2013-07-11
> **Vegan said:**
> I found that the bigger 4U chassis with 120mm fans are a lot less noise. Best bet is to create a closet and provide a cooling solution such as ventilation or outright AC

A 4U is pretty much a regular mid tower. Those can be a lot quieter than 1Us because there's more space inside the case for heat to dissipate. In a 1U, it's a tight fit, so the heat would just sit there, hence the high rpm fans to push the hot air out.

---

