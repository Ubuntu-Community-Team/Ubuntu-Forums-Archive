---
title: "Storage recommendations? (1TB, network, external)"
date: 2008-11-13
forum: The Cafe
---

### Post by PartisanEntity on 2008-11-13
Hello everyone,

I'd like to ask what experiences you have had with the different hard disk brands out there.

I am planning to buy a 1TB external hard disk (for storage: ubuntu & mac), preferably with networking capability (i.e plug in to a router).

Any recommendations?

---

### Post by binbash on 2008-11-13
2.5 or 3.5?

I have 2 matrox one touch minis for my personal use at my notebooks and they are perfect at cooling.(2.5) and my partner using this one (pretty cool, network etc) : 

[http://www.naaptol.com/buy-online/WO-best-shopping-deals-W13666O/computers_-_peripherals/storage_devices/hard_disk_drives/seagate_storcenter_pro_nas_150d.html](http://www.naaptol.com/buy-online/WO-best-shopping-deals-W13666O/computers_-_peripherals/storage_devices/hard_disk_drives/seagate_storcenter_pro_nas_150d.html)

---

### Post by PartisanEntity on 2008-11-13
I'm looking for 3.5

---

### Post by notwen on 2008-11-13
I've used Fantoms and Lacies for my whole life(5 drives) and not had any of them die.  I'm currently using 2 1TB ext Lacies for media/data backups.  As far as the NAS support, you're on your own, I use mine strictly for backups and have never looked into a NAS setup.  Best of luck to you.  =]

[Lacie Ethernet Disk Mini]("http://www.lacie.com/products/product.htm?pid=11072") (500GB/1TB)
 [Fantom G-Force MegaDisk NAS]("http://store.fantomdrives.com/general/prodDisplay.asp?CatID=137&ProdID=546") (1TB)

---

### Post by mips on 2008-11-13
I would happily recommend Seagate or WD to anyone.

---

### Post by waapwoop1 on 2008-11-13
Look up QNAP.

they have really good NAS storage solutions. thinkng of getting one for myself. Built in ftp server, web server, streaming server to ps3/xbox, and lots of other stuff.... and low power consumtion. means i won't have to leave pc on any more. Also supports RAID if you get two or more bays.

---

### Post by billgoldberg on 2008-11-13
I've heard that the new Lacie 1tb network drives are very good from a friend of mine (the one with the nice design, at least that's what they claim).

---

### Post by PartisanEntity on 2008-11-14
Thank you for the recommendations and ideas so far. My budget is around &#8364;300, so I hope I will find a balance between quality and funcationality.

---

### Post by pp. on 2008-11-14
I think you should study the drives and the enclosures separately.

LaCie and similar brands sell their own enclosures with different interfaces such as firewire, USB and Ethernet. They all use drives by the ever same few manufacturers.

The firewire and USB ones are straightforward in their usage. They are, however, not what you are asking in your OP.

Practically all of the network drives come with some variant of Linux and Samba. LaCie apparently carries some models with XP. 

I've had no issues whatsoever with a linksys NSLU2 server and two external USB drives except for the fact that the USB drives are 'always on' and hence keep on consuming electrical power. I keep having 'issues' with the synology NAS device such as strange access restrictions and characters supported in file names.

As regards the actual drives used in those devices, they all appear to be of comparable quality. You might want to watch for drives which prefer being run for long times at a stretch vs those which do not mind being powered up and down rather frequently. However, I have not yet seen any statistics on that topic.

Afterthought: The synology also fails at doing daily backups to an USB disk because the disk is in powersaving mode and takes too long to wake up.

---

### Post by Paqman on 2008-11-14
> **waapwoop1 said:**
> Look up QNAP.

they have really good NAS storage solutions. thinkng of getting one for myself. Built in ftp server, web server, streaming server to ps3/xbox, and lots of other stuff.... and low power consumtion. means i won't have to leave pc on any more. Also supports RAID if you get two or more bays.

I've got one of their TS-209 NASs, highly recommended.

Linux-based, RAID1 with hot swappable drives, so you can put as much storage as you need or your budget permits. Print server, auto backups, UPnP media server, and a very thorough web interface including SMART for the drives, etc. Plus it'll do a  lot more stuff that I don't bother with (IP security cameras, external FTP access, web server)

You can SSH into the box easily too, and i've found QNAP support to be very helpful the one time I needed them. They're also actively developing the platform, there's been several improvements in functionality through firmware updates since i've owned mine.

Sucks about 10-15W, and has active fan monitoring and a sleep mode, so it's quiet and dirt cheap to run.

---

### Post by PartisanEntity on 2008-11-26
So I have been looking around, and at the moment I have this in mind:
[http://www.lacie.com/de/products/product.htm?pid=11090](http://www.lacie.com/de/products/product.htm?pid=11090)

Anyone have any experience with it? Any issues with Linux compatibility?

Also, I would be accessing it through wifi, so I guess transfer speeds won't be that fast, but for backups it should be no problem, right?

---

### Post by grazed on 2008-11-26
> **PartisanEntity said:**
> So I have been looking around, and at the moment I have this in mind:
[http://www.lacie.com/de/products/product.htm?pid=11090](http://www.lacie.com/de/products/product.htm?pid=11090)

Anyone have any experience with it? Any issues with Linux compatibility?

Also, I would be accessing it through wifi, so I guess transfer speeds won't be that fast, but for backups it should be no problem, right?

assuming you're going to be on a G network, it will be very slow if the the backups are past a few gigs.

under -perfect- circumstances you'll have 54Mbits per second, which comes out to about 6.75MB per second. then it hits your drive, which would probably write at around 4-5MB per second. so, a 10 gig backup would take over half an hour under the best case scenario. =/

investing in a wired gigabit NIC and router may be a better choice for speed. OR a wireless N router and card which can transmit in upwards of 200Mbit per second

---

### Post by mips on 2008-11-26
In English, [http://www.lacie.com/uk/products/product.htm?pid=11090](http://www.lacie.com/uk/products/product.htm?pid=11090)

---

### Post by mips on 2008-11-26
[http://ubuntuforums.org/showthread.php?t=939081](http://ubuntuforums.org/showthread.php?t=939081)

You have the option of FTP access or using SAMBA.

---

### Post by PartisanEntity on 2008-11-26
> **grazed said:**
> assuming you're going to be on a G network, it will be very slow if the the backups are past a few gigs.

under -perfect- circumstances you'll have 54Mbits per second, which comes out to about 6.75MB per second. then it hits your drive, would probably write at around 4-5MB per second. so, a 10 gig backup would take over half an hour under best case scenario. =/

investing in a wired gigabit NIC and router may be a better choice for speed. OR a wireless N router and card which can transmit in upwards of 200Mbit per second

Hmm 30 mins for 10GB, I think I can live with that. Due to space limitations I currently do not have the option to connect with anything other than wifi (G).

My backups will be around 1GB (my /home folders).

---

### Post by PartisanEntity on 2008-11-26
> **mips said:**
> [http://ubuntuforums.org/showthread.php?t=939081](http://ubuntuforums.org/showthread.php?t=939081)

You have the option of FTP access or using SAMBA.

Thank you for the link mips, I discovered that thread and posted there too.

So compatibility is covered.

Does anyone here have experience with LaCie drives, are they reliable?

---

### Post by grazed on 2008-11-26
> **PartisanEntity said:**
> Hmm 30 mins for 10GB, I think I can live with that. Due to space limitations I currently do not have the option to connect with anything other than wifi (G).

My backups will be around 1GB (my /home folders).

oh in that case, no worries. 1GB over -g will go by in no time. =)

---

### Post by mips on 2008-11-26
> **PartisanEntity said:**
> 
Does anyone here have experience with LaCie drives, are they reliable?

I have no experience with LaCie but I do know that their products have a good reputation.

---

### Post by handy on 2008-11-26
> **mips said:**
> I would happily recommend Seagate or WD to anyone.

I would add Hitachi to the list, they bought & took over IBM drives, which I used to consider the best.

---

### Post by pp. on 2008-11-26
> **mips said:**
> I have no experience with LaCie but I do know that their products have a good reputation.

I have been using two 160GB lacie drives for a couple of years without the slightest problem at all. I have now retired them because of my bad conscience. I had them always 'on' even when I was not at home. However, those were just USB drives and not SAN boxes.

---

### Post by notwen on 2008-11-26
> **PartisanEntity said:**
> Does anyone here have experience with LaCie drives, are they reliable?

Refer to post #4 in this thread. =p  I've had my 2 current 1TB drives for around 2 years w/o any issue.  I still have my 3 other ext hdds(2 fantoms & 1 lacie) ranging in size from 320-750GB and all are still working and I use them regularly, atleast once a week or more.

---

### Post by PartisanEntity on 2008-11-27
Hello all,

Again thank you for the feedback. I bought the drive today and set it up. Accessing it through my MacBook was fine. Now I am trying to access it through Ubuntu 8.04 and that is not working as smoothly as I thought it would.

Places > Connect to Server > FTP (with logon)

I enter my ftp access data.

It then pops open a window showing both the myshare and openshare folders.

When I open these folders they appear empty, even though I have placed test files in them.

Any ideas?

---

### Post by pp. on 2008-11-27
You bought not a disk drive but a server. Therefore, it has facilities to manage user privileges, I presume. 

Silly question: Why do you access that device with FTP? I'd have assumed that you'd try accessing them as windows shares first.

However, granting users privileges would still apply.

---

### Post by PartisanEntity on 2008-11-27
> **pp. said:**
> You bought not a disk drive but a server. Therefore, it has facilities to manage user privileges, I presume. 

Silly question: Why do you access that device with FTP? I'd have assumed that you'd try accessing them as windows shares first.

However, granting users privileges would still apply.

Sorry you are right, I keep calling it 'disk' but I mean the server of course :)

Well, it worked after I installed the Lacie Network Agent in Ubuntu, now I am able to access file on there.

---

### Post by notwen on 2008-11-27
Just curious which did you end up going w/?  Just in case I end up getting a NAS in the future.  =]

---

### Post by PartisanEntity on 2008-11-27
The LaCie Network Space 1TB [link]("http://www.lacie.com/uk/products/product.htm?pid=11090")

The software is available in three versions, for Mac/PC/Linux

Configuration of the NAS is done through the web platform.

---

### Post by oblidor on 2010-05-01
> **pp. said:**
> I think you should study the drives and the enclosures separately.

LaCie and similar brands sell their own enclosures with different interfaces such as firewire, USB and Ethernet. They all use drives by the ever same few manufacturers.


For God's sake, don't get some LaCie crap. It is all design and nothing for the functionality. I bought a Network Space 1Tb and I got a whooping 1.2Mb/s transfer rate. Apart from that the device never powers down or wakes up on lan. What a piece of crap! I opened the "design" box and yanked that SATA HDD to put it in a stationary.

LaCie is for design fanatics IMNSHO

---

