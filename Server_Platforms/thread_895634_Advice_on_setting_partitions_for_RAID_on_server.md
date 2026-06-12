---
title: "Advice on setting partitions for RAID on server"
date: 2008-08-20
forum: Server Platforms
---

### Post by Twizzle on 2008-08-20
I am about to set up a server and would like to use software RAID. It is only a basic home server and will have the following functions:

Backup and storage of music, video and pictures.
CCTV using Zoneminder.
Possible Email server in the future.

I have three HDD's available 320Gb, 250Gb and 120Gb

I was going to have a large 250Gb RAID 1 partition for my media (so /home I guess). A 120 Gb non RAID partition as /tmp for temp files and where Zoneminder would record footage, and finally a 70 Gb non RAID partition for / and /swap.

My priority is to have my media and backup as RAID 1 so I don't loose them.

I assume that having / on a non RAID partition will mean the system may go down if the drive fails BUT my /home partition *should* still be ok and I will be able to access it by putting a new HDD in and reinstalling. The system is not critical and will not cause any real issues if it goes down for a day or two as long as the /home data is intact. My other assumption is that 120Gb gives me plenty of space for video and is again not critical. The chances of me being broken into and then the drive failing all before I get home are very small and a risk I am prepared to live with :). Also, it is only a two camera setup and so 120Gb should be plenty. (I think...)

As I was setting it up, I then thought about having a 250 Gb RAID 1 partition and using the rest of the 320Gb drive and some of the 120Gb drive to create a 70Gb RAID 1 partition.

This would then give me 250Gb RAID1, 70Gb RAID1, and 50Gb Non RAID and I could put / on the 70Gb but only have 50Gb for the CCTV. Does splitting RAID volumes like that make sense?

A bit of a rambling question I know, but I would appreciate anyones opinion / advice.

Thanks

---

### Post by alecz20 on 2008-08-20
I think if you use 2 different sized disks for Raid 1 the rest of the bigger disk remains unusable.

I am planning to do something similar in a few days, but until then I know about as much as you do. Maybe someone that did this before can shed some light as I am interested too in this subject.

---

### Post by Ximbiot on 2008-08-20
> **alecz20 said:**
> I think if you use 2 different sized disks for Raid 1 the rest of the bigger disk remains unusable.

No, as long as you have similarly sized partitions on each disk to pair up, then you can use each partition for RAID without losing access to any disk space.

There are some speed issues with software RAID with both disks on the same IDE bus, but I don't recall all the particulars.  It may be worth googling, especially if you want it to store and serve video.

---

### Post by alecz20 on 2008-08-20
Good to know Ximbiot.

Too bad Linux does not yet support hardware RAID (the one available on Intel boards)

---

### Post by fjgaude on 2008-08-20
> **alecz20 said:**
> Good to know Ximbiot.

Too bad Linux does not yet support hardware RAID (the one available on Intel boards)

I think, as time goes on, raid will be software, period. What Linux really needs is a well-thought-out GUI to manage **mdadm**. That would do it for many of us folks.

---

### Post by Lexrst on 2008-08-20
> **fjgaude said:**
> I think, as time goes on, raid will be software, period. What Linux really needs is a well-thought-out GUI to manage **mdadm**. That would do it for many of us folks.

I second that!  I'm trying to assemble a RAID1 mirror with mdadm on two ATA drives with grub/swap/boot/home residing on a SATA drive.  Not having much luck.... I could really use an intuitive GUI right now (and no, I have no problem with the CLI in most cases).

-Lexrst

---

### Post by brad8266 on 2008-08-20
I hate hardware RAID even more after the fiasco I went through today. Our Server 2003 drives lost the partitions after an attempt to rebuils a simple RAID 1 array. We used the MegaIDE mainboard embedded raid from LSI Logic, it sucks IMO. I finally got the partitons redone and now I have to work on the boot sectors.

I prefer software RAID anyday.

---

### Post by Mrwasab1 on 2008-08-20
i would go for the 250Gb RAID1, 70Gb RAID1, and 50Gb Non RAID option, but personally i wouldnt put / and /swap on the same disk, or the same partition.

---

### Post by Twizzle on 2008-08-21
Well I was playing around while waiting for replies and set it up as 250Gb RAID 1, 70Gb RAID 1 and 50Gb non RAID and so far no problems. (I get the odd {DRDY ERR} and {ICRC ABRT} at boot but from Googling, they are apparently nothing to worry about.)

I am curious as to why you would not put / and /swap on the same partition - is it just a speed thing?

---

### Post by Mrwasab1 on 2008-08-21
> **Twizzle said:**
> Well I was playing around while waiting for replies and set it up as 250Gb RAID 1, 70Gb RAID 1 and 50Gb non RAID and so far no problems. (I get the odd {DRDY ERR} and {ICRC ABRT} at boot but from Googling, they are apparently nothing to worry about.)

I am curious as to why you would not put / and /swap on the same partition - is it just a speed thing?

yes its purely a speed thing. If the server needs to use the swap for any reason, it will slow down any other read/write requests which may be in the process. 

Memory is stores in pages, when you are installing something and happen to run out of memory, it will search for the least used page of memory and dump it on the swap area, it will do this while it is attempting to write data to the disk at the same time.

This goes for running programs too. If you are booting or running applications or anything which calls out to your RAM, when it fills up, it will nominate its least used pages and dump them in the swap area.

On some occasions you can have whats known as thrashing. Where a page is dumped onto the disk, then back to the RAM, then back to the disk and so on, seriously reducing performance. Seriously enough to cause a system halt. But this is and extreme.

It is suggested to have the swap on a different disk from what Ive been taught. Some put it on different partitions but on the same disk, which really has the same effect in the end from what Ive been told.

In saying this, my server has 4gb of ram and has never needed to swap, so i simply don't use it. But if i did, it is suggested that you make the swap half of your current memory. So if you have 1gb, make is 500mb. But i say be generous and make it at least 2gb, unless you know your applications wont need that much. 

Edit: damn typos

---

### Post by windependence on 2008-08-21
> **fjgaude said:**
> I think, as time goes on, raid will be software, period. What Linux really needs is a well-thought-out GUI to manage **mdadm**. That would do it for many of us folks.

Even though I am softening to the idea of software RAID ;) I cannot agree with this statement. There are still quite a few advantages to hardware RAID, and in a production or enterprise environment, simply keeping a spare RAID card on hand goes a long way toward recovering from a RAID failure.

To the OP, Linux most certainly does support hardware RAID, TRUE hardware RAID, not software on a card RAID as some built in RAID controllers are today on consumer mother boards. On server class hardware, the built in controllers work very well. If you want to use an add-on card, 3Ware makes a great card that had worked with every distro I have tried with it. Stay away from Highpoint, Promise, and some other "consumer" cards. Most of them are just software RAID on a card.

-Tim

---

### Post by windependence on 2008-08-21
> **brad8266 said:**
> I hate hardware RAID even more after the fiasco I went through today. Our Server 2003 drives lost the partitions after an attempt to rebuils a simple RAID 1 array. We used the MegaIDE mainboard embedded raid from LSI Logic, it sucks IMO. I finally got the partitons redone and now I have to work on the boot sectors.

I prefer software RAID anyday.

The problem you experienced is most likely a WINDOZE problem. It is well documented on the web for quite a few RAID controllers, Windows continually tries to load it's own driver.

IMHO, I'll take hardware RAID any day to software RAID until I can prove otherwise.

[http://www.pcguide.com/ref/hdd/perf/raid/conf/ctrlSoftware-c.html](http://www.pcguide.com/ref/hdd/perf/raid/conf/ctrlSoftware-c.html)

[http://www.adaptec.com/en-US/_common/campaign_links/_links/Hardware_SoftwareRAID_WP?mc=portal_HwSwWP](http://www.adaptec.com/en-US/_common/campaign_links/_links/Hardware_SoftwareRAID_WP?mc=portal_HwSwWP)

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

-Tim

---

### Post by fjgaude on 2008-08-21
> **windependence said:**
> Even though I am softening to the idea of software RAID ;) I cannot agree with this statement. There are still quite a few advantages to hardware RAID, and in a production or enterprise environment, simply keeping a spare RAID card on hand goes a long way toward recovering from a RAID failure.


Look, I said "someday", as time goes by, when software raid has a good GUI, one that is shallow in learning-curve. It's all coming because of the multi-core CPUs and fast, fast memory. Intel says their 8-core CPU, 32 nm, will be out before the end of the year. Next is the 22 nm, with 16 cores, late next year. Software raid can support thru-puts, TPS, I/O, as fast if not faster than hardware raid cards now.

---

