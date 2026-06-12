---
title: "Suggestions on external backup device for laptop"
date: 2010-04-20
forum: System76 Support
---

### Post by samalex on 2010-04-20
Hi,

I usually use my wife's WD MyBook to backup my laptop, but I'd like to find something smaller and more portable.  Can someone suggest a good 500 GB drive, whether eSATA, Firewire, or USB 2.0, that works outta the box with Linux?

Also can any of these formats - eSATA, Firewire, or USB 2.0 - be powered from the laptop?  I'd hate to have to lug around a power cable, so just curious.

Take care and thanks for any suggestions --

Sam

---

### Post by bill516 on 2010-04-20
samalex, I have a WD 500 Gig My Passport with me at the moment as I travel.  I usually carry it in a pocket in my computer bag,though it fits in a shirt pocket as well.  It runs off the USB port, so there is no power brick.

Two issues:  It comes set up on the assumption that you are running Windows and so you will use embedded Windows backup software on the drive.  For Linux you can and should go to the WD website and disable the WD software.  Problem is that you cannot remove it so you do lose some capacity on the drive.  Tolerable, but you do lose it.

Second issue:  The USB cord is a bit short and you need you be careful.  If you boot an operating system from it and it disconnects accidentally your computer will get very confused!  So if you are using a laptop be careful about picking it up when the drive is attached.  (That is an official OOPS.)

I keep mine formatted to FAT32 so that I can move between whatever operating systems I am running at the moment.  It serves very well as a backup device.  Reliable and quiet.

As I recall I bought the drive for a little less than $100 from one of the big-box stores.  (Best Buy maybe?

Good hunting!

---

### Post by gamerchick02 on 2010-04-20
I have a Western Digital Passport 250 gig drive.

I noticed the software on it and did a full format when I got the drive, so I didn't notice any decrease in size.

Why does something as simple as an external drive need windows drivers/software to "work"?

Either way, I found mine at Circuit City (on sale) before its demise a couple years ago. Used it with my old desktop, and it's sitting on the desk behind my laptop with backups run every day.

Amy

---

### Post by rogerpittman on 2010-04-20
I use a Seagate FreeAgent external drive to back up the data on my laptop. Mine is a 350 GB model, but I believe there's a 500 GB version as well. It runs off the USB port and is completely silent.

---

### Post by jml on 2010-04-20
I have two WD Passport drives both 250 gig.  Very reliable, fast enough for my needs and are powered from the USB port.  No power bricks needed.  Very satisfied with them.

Joe

---

### Post by Morbius1 on 2010-04-20
My wife bought one of these for her MacBook: [http://eshop.macsales.com/shop/firewire/on-the-go](http://eshop.macsales.com/shop/firewire/on-the-go)

You might not like the looks but it's appears to be almost indestructible. It's got a heat sink on the thing that could break a window. You can get models that accommodate USB2 or FireWire                         800/400 + USB 2.0.

At the time she bought hers it was available with a WD Scorpio Black HDD. It seems they switch drives from time to time so I don't know what's available now. All of the interfaces can be bus powered. The other thing about it is that it opens up so you can replace / upgrade the drive later. In fact they sell just the enclosure if you have a spare 2.5" drive.

It's formatted for a Mac ( site caters to apple owners ) but it's simple enough to format it to whatever you want.

---

### Post by samalex on 2010-04-21
Thanks for the replies... I'll probably check out the WD Passport and Seagate FreeAgent at my usual haunts (NewEgg, Altex, BestBuy, etc). 

And yeah I'll format the thing as soon as I get it, which is what I had to do with the WD MyBook we use now.  I don't need any proprietary software/drivers on the thing.

Take care --

Sam

---

### Post by bgreenaway on 2010-04-22
I bought a 500 MB WD Passport Essential from Best Buy to use on my System76 PanP5, and it did not last even a month before failing. Got it replaced and the second one failed after three months. After returning that, I went for a Toshiba 1TB, which has performed perfectly. Maybe a bad batch, I do not know, but I am now wary of WD products.

---

### Post by TheFu on 2010-04-22
I bought a 2.5" WD SATA drive and a no-name 2.5" external USB enclosure ($14) that uses USB for power. It is slow, but doesn't require an external power supply. It has a power supply if you want more speed.

Then I use `dd` to mirror the disks at the dev level, not the partition level. I end up with a drive that can be swapped into the laptop if there is a failure.  `dd` created the partition table, file systems, files and all data exactly as it existed on the source drive, byte for byte. The down side is it copies everything every time. Use this just the first time.  The great thing about `dd` is that it doesn't care about the data or file system. I've cloned NTFS, FAT32, EXT3, swap, and JFS partitions on the same physical disk.

For data backups, I'd just mount the partition to be backed up under /backup and use `rsync` if a data mirror is all I want.  For real, scheduled, nightly, incremental, automatic backups, I use rdiff-backup to a server on my LAN. [http://jdpfu.com:82/2009/10/24/linux-home-backup-with-rdiff-backup](http://jdpfu.com:82/2009/10/24/linux-home-backup-with-rdiff-backup). I keep 90 days of incremental HOME backups that way. The overhead for all those versions is about 10% for me, but YMMV. On company servers, I use rdiff-backup for VMs and have had to restore them completely. It works.

---

### Post by samalex on 2010-04-22
TheFu,

I use a mixture of rsync and tar.  rsync is used for photos, MP3s, etc, but I like to tar my documents and coding projects so I have revisions.  I have used 'dd' before doing system-wide upgrades so i can roll back my system just incase, but I wouldn't use 'dd' for routine backups.

Take care --

Sam

---

