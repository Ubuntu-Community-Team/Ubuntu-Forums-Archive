---
title: "real hardware raid with ubuntu server + recommendations"
date: 2010-08-02
forum: Server Platforms
---

### Post by wall_e on 2010-08-02
Hi guys.

Can anybody help me with a couple of questions about hardware raid and ubuntu server?

From what I've read it seems as long as I use a real hardware raid controller it will work well with ubuntu server?

I'm a little confused :confused:

Having used real controllers on various video spec Mac workstations in the past I am used to the card always having some kind of accompanying drivers and management software etc.

I've read around a lot about compatability, but still struggling to find a fast raid 6 pci-e card that will do 16 drives with ubuntu.

The project I am working on is to build a video storage NAS, hence the requirement for speed and space.

I am planning on using fairly cheap 500Gb sata II drives, not SAS or anything mega high end.

Still I'd like to achieve at least 250MB/s from the array setup as raid 6.

This is just a project I am doing for fun in my spare time :)

---

### Post by arrrghhh on 2010-08-02
What information do you need?  I would say *most* hardware RAID controllers will probably work with Ubuntu/Linux, but I can't say there's any guranatee that they all will.

Do you have a particular one in mind?  Searching for Linux compatibilty should be enough, for the most part all hardware is supported thru the Linux kernel which is the same no matter what distro you choose.  So Ubuntu does not have a whole lot to do with hardware assuming the drivers are supported at the kernel level.

---

### Post by CharlesA on 2010-08-02
The controller I use is a cheap one that can only deal with RAID0,1,5 but I can get speeds up to 100MB/sec on it.

There were drivers for it as well.

If you want RAID6, it would probably be a 3WARE or ADAPTEC controller that you would be looking for.

As long as there are drivers for Linux, you should be fine.

---

### Post by wall_e on 2010-08-02
Thanks for the fast response guys.

I've been looking mid level PCI-e cards like the  Areca ARC-1260 (Areca not a brand I know much about) and slightly more expensive Highpoint RocketRAID 3560LF.

Both use a similar Intel® IOP341 chip and have 256MB cache.

Likewise both advertise linux drivers, but no specific mention of ubuntu :rolleyes:

To quote page... [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

> Hardware-RAID: A special controller used to build RAID. RAID hardware faster, no CPU overload and can be used for any OS

.. this is basically what leads me to believe what Arrrgh is saying.

I'm currently running 10.04 server serving up 2 x 1.2TB of space RAID 5 via 2 old 3Ware Escalade 7000-8's, but these really struggle with Raid 5 :(

Each array is 8 ATA 133 drives - The 7000-8's are fast ish with RAID 0, but I can't risk dropping back to no redundancy.

---

### Post by arrrghhh on 2010-08-02
> **wall_e said:**
> .. this is basically what leads me to believe what Arrrgh is saying.

I speak the truth friend!  :D  

But what they mean by "can be used for any OS" is no matter how you setup the RAID array, it will be operating system agnostic if that makes sense.  Essentially software RAID is setup by the OS - therefore very dependent on the OS, and if you dual-boot then each operating system will have to have its own software RAID array setup.

With hardware RAID, it's setup and managed by a separate piece of hardware, hence the reason I say it's operating system agnostic.  Doesn't matter if you dual-triple or whatever boot, the RAID controller is what manages the RAID array, so it's not dependent on the OS to have the RAID array setup.  Sorry if I made that confusing, I tried to say it in a few different ways so that if one didn't make sense, hopefully the others would :p


If they both have linux **kernel** you should be fine.  Did a quick google search, an it looks like the RocketRaid is supported at the kernel level, but the other card *may* not be.  I am by no means an expert on this however, and it was a *very* quick googling ;)

[http://manpages.ubuntu.com/manpages/hardy/man4/arcmsr.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/arcmsr.4.html)

That is what I dug up about that Areca card that made me suspicious of actual kernel support.  Nothing positive one way or the other.  Heck if you can't find anything definitive on their site, call up their support!  See if they support Linux at the kernel level, or if there's a patch.  Either way if the manufacturer's site lists Linux support you should be fine with Ubuntu - there just may be some hoops you have to jump thru if their drivers are not supported in the Linux kernel that Ubuntu runs (which is usually a version or two behind 'bleeding edge'...)

---

### Post by CharlesA on 2010-08-02
It looks like there are some linux drivers for that card: [http://www.highpoint-tech.com/USA_new/series_rr3500.htm](http://www.highpoint-tech.com/USA_new/series_rr3500.htm)

Most notably drivers for Debian 5.2 and Ubuntu 9.04.

The card I am using allows you to build the drivers from source, maybe shoot them an email and see if that's possible for that one you want.

---

### Post by wall_e on 2010-08-03
Well guys I did what you said and called a couple of places up.

3Ware were the most helpful that I spoke to and as it turns out ubuntu has fairly good support for them out of the box.

In a slight change of plan I've decided to opt for an older (used) 3Ware 9550SX-12SI to prove the concept works before buying into anything expensive.

What I'm doing is serve shares created on my ubuntu server via AFP.

I am using Avahi to advertise the service via bonjour to the Mac's in my network.

This makes the NAS really easy to mount on the Mac side.

Right now I'm just trying to figure out if there will be any bottle necks in the system.

The above card is PCI-X 133, the server is dual Xeon (old schoolp4 style) and I'll be creating a bonded gigabit trunk (3 NIC's) to the switch.

I know the chips are not exactly quick, but surely if I'm using hardware RAID they don't really need to do a lot.

Ultimately if I can get some reasonable performance out of this thing then I'll give it an overhaul with some newer hardware. PCI-Express RAID as mentioned before and a decent board/chips etc.

Managed to squeeze 120 MB/s from 1x Escalade 7000-8 today, which is reasonable, so I'm hopeful for the system with 12 SATA drives and a better controller :)

---

### Post by spookware on 2010-08-05
I recommend the Areca cards. It is hard to beat their integrated web server for management of the array. Compared to something like one of the LSI megaraid cards where you have to use LSI's awful host based management application. 

So if you want your raid to be easy to manage the Areca cards are far and away the best options.

---

### Post by skyhigh1001 on 2010-08-08
I am currently in the process of setting up a server using the Areca 1680IXL-12 RAID controller card, and while looking for some information on how to set this up properly found this relevant forum discussion.

The server is setup with 1 Intel X25-V 40 GB SATA SSD drive for the operating system partiations, and 12 Seagate Constellation ES 2 TB SATA drives for a total of 24 TB of data storage (20TB after the RAID 6 overhead).

I just installed Ubuntu 10.4 on the server.  During the install I had the Areca RAID controller plugged into the server, but all the raid drives were unplugged to make sure that Ubuntu installed on the Intel SSD drive.

I powered off the box, plugged in all the RAID drives, and brought it up again, but when it came back up and I run "df" I only see the Intel X25-V drive and partitions.

This is my first Ubuntu server installation and I am not sure if there is some utility I need to run to check for new hardware or how to find if the the Areca adapter is being recognized by the kernel.

I read on the Ubuntu site at [http://manpages.ubuntu.com/manpages/lucid/man4/arcmsr.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/arcmsr.4.html) that the Areca 1280 adapter is supported by the arcmsr driver.  I have been searching the forums looking for information on whether this driver is already included in the kernel or if I need to do something to install it.

Any pointers on how to confirm if the driver is loaded and recognizing the hardware, or any information on steps I need to take to get Ubuntu to recognize the RAID drives would be greatly appreciated.

---

### Post by skyhigh1001 on 2010-08-08
I did find that lsmod is showing that the arcmsr driver is loaded.  So the kernel apparently does include the arcmsr driver and is correctly detecting that the Areca RAID controller is present and loading the driver.

However the "df" command still isn't showing me the RAID disks.

---

### Post by CharlesA on 2010-08-08
Are they mounted?

Try running this:

```
sudo fdisk -l
```

---

### Post by skyhigh1001 on 2010-08-09
Thanks that helped.  When I run the "sudo fdisk -l" command it displays the raid drive as /dev/sdb so it looks like I need to format a partition on this drive as the next step.

I would like to use the LVM support so that I can expand the size of this volume as needed in the future.  I am actually only starting with 6 of the drives (12 TB) in the server and will be adding the additional drives and expanding the RAID set size as I need the additional space.

I will read up on how to use fdisk and the LVM support.

---

### Post by skyhigh1001 on 2010-08-09
I tried to setup the partition on the RAID drives using cfdisk and fdisk. But eventually figured out that these utiltiies cannot create a partition larger than 1.3 TB.  I then tried to make the partition bigger using a gparted live CD, but gparted also got errors every time it tried to make a partition bigger than 1.3 TB or expand an existing partition bigger than 1.3 TB.

In the end I found an article at [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html) which explained that I could use parted and change the type of the partition table being used to a gpt type partition table.

I was then able to create the large partition.

I also read up on the ext4 vs. ext3 file system and found that part of the new functionality in the ext4 file system was to support larger volume sizes so I created an ext4 file system instead of ext3.

I think that the gparted live CD must have been getting errors because the partition table type was not gpt, and it didn't figure out that it needed to change the partition table type to gpt in order to make the large partition.

---

