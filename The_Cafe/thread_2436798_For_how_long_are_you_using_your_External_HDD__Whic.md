---
title: "For how long are you using your External HDD ? Which brand is it ?"
date: 2020-02-13
forum: The Cafe
---

### Post by linuxyogi on 2020-02-13
I purchased a  **WD Elements Portable 2.5 inch 500 GB External Hard Disk **some 3 years back. It went bad just after 1 year of use. I felt terrible about the waste of money.

For how long are you using your External HDD ? Which brand is it ?

---

### Post by SeijiSensei on 2020-02-13
I write backups to this device every night for a couple of years now:

[https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817](https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817)

---

### Post by linuxyogi on 2020-02-13
> **SeijiSensei said:**
> I write backups to this device every night for a couple of years now:

[https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817](https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817)

The next I buy a external hdd I will definitely consider a Seagate.

---

### Post by mastablasta on 2020-02-13
a similar experience. 500 GB WD Elements. it was used to backup server OS and PC OS and few other partitions. it was kept in original packaging. suddenly i needed it and it was corrupted. that was just after about 2 years. so no warranty. i tried to troubleshoot (changed cable, scanned etc.) and complained to WD, but no good answer. i plan to smash it with a sledgehammer.

i bought a WD passport to replace it. so far it works, but who knows. it seem these are not good.

---

### Post by rbmorse on 2020-02-13
I bought an external 3.5 inch HDD caddy and a couple of iTB Western Digital WD1003FBYK hard drives about four years ago.  All still in use on a daily basis (the drives get swapped about once a week).  It's not very pretty, but I've never had good luck with "portable" external hard drives.  

I also have a couple of WD Passports, but they're very picky about which USB port they will work with, and they absolutely hate hubs, except for the one in my Dell monitor.  Haven't worked out why.

---

### Post by TheFu on 2020-02-13
2.5 inch disks are made for laptops unless they are enterprise SAS devices.

I've had good and bad luck with every drive vendor, every sort of device, over the decades.
When buying, pay attention to the warranty provided by the vendor. They make millions of each type and those with better warranties are much more likely to last at least through the warranty period.  Which disk type should be used depends on your purpose for the disk and how much abuse you give it.

Pretty much all external USB disks only have 90-1 yr warranties, because the market wants cheap over long life models.  However, sometimes there is a fortunate overlap where we can get higher quality HDDs that happen to get put inside a cheaper USB enclosure by the vendor. WD has been doing this for years to use up some of their excess Red HDDs.  If you run a NAS, you probably know about Red Drives and seek them out. These are 3.5 inch HDDs, not 2.5 inch. While we can never be 100% certain about the actual disk inside a USB enclosure without looking, often the vendor will provide hints in the model number.  There are entire threads about seeking quality Red HDDs in cheap enclosures to save $50/ea HDD for a NAS build. Look for drive **shucking**.

I use a dual eSATA "dock" which lets me drop in 1 or 2 HDDs for access using the native SATA command set, not just the USB one. There is a difference when it comes to real performance with multiple programs writing concurrently.

As for Seagate, never again.  When 750G HDDs were a thing all the way until 8TB HDDs became common, Seagate had quality and durability issues.  Early on, the company lied about the issues for a few years, which made enterprise customers avoid anything from Seagate if they could.

Every quarter, there's a company - backblaze that posts drive lifetime reports for everyone to see. They are an online storage company, buying hundreds of thousands of HDDs yearly, so they have a statistical sample unlike most of us.  Based on those reports, it appears that almost any brand making 10-12TB HDDs is doing a very good job with longevity and avoiding initial dead drives.

For 500G sized storage, I'd just get a WD Blue or Green (for backup use only), and move on.  Heck, I've bought used WD Blue 250G HDDs for $10 when I just needed some cheap storage.  3.5 inch in size.  I avoid 2.5in HDDs - no good reason why - I just do. Perhaps it is because they cost more and are slower with shorter warranty periods?

Regardless of the disk, I run smartctl tests weekly and compare the results from week-to-week so any changes over time are highlighted.

How long do I use a disk?  5 - 10 yrs, until the SMART data screams - **I'm failing**.  Since I have excellent backups, a HDD failure is just a minor inconvenience, not anything big.  At some point, my backup disk (7.6 yrs old, on 24/7/365), which holds all the versioned backups for all systems here (HOMEs OS, settings), will fail.  The SMART data for it shows it is fine, though a few CRC errors had me swap the SATA cable a few years ago.

---

### Post by sudodus on 2020-02-13
> **TheFu said:**
> 
I use a dual eSATA "dock" which lets me drop in 1 or 2 HDDs for access using the native SATA command set, not just the USB one. There is a difference when it comes to real performance with multiple programs writing concurrently.


+1

I use eSATA (and USB 3) external enclosures (boxes) and put high quality 'internal' 3,5 inch HDD drives into them. Lifetime as well as speed is so much better than with the cheap alternatives (I know, because I used to buy cheaper drives ...). The price is higher too, but not that much higher, and I get a much smoother ride.

Edit: It is important that the drives are not overheated, and some enclosures do not get rid of the heat well enough. It may be worthwhile to monitor the temperature.

I run a shellscript with **hddtemp** via root's crontab.

You find the package hddtemp in the repository universe.

---

### Post by linuxyogi on 2020-02-14
@Everyone 
Thanks for the replies.
The only file that I need to backup is my KeePassXC database.
Do you think a 32GB flash drive is enough for my purpose ?

---

### Post by mastablasta on 2020-02-14
> **linuxyogi said:**
> @Everyone 
Thanks for the replies.
The only file that I need to backup is my KeePassXC database.
Do you think a 32GB flash drive is enough for my purpose ?

yes a quality UBS key or good SD card will also do. it can be smaller than 32GB, unless you have a really large password database.

however, to go back to me it would not be anything unusual if the drive was being used a lot and failed. however it is strange that it failed (got corrupted), when it wasn't used at all or was used rarely. luckily it didn't have anything important on it. and i could rescue some config files to help me remember how i configure it all.

since their failure rate can be high i find the advice by salesman even more ridiculous. they had this gaming laptop, win10 preloaded with 256GB SSD drive. so i told them that it's not a big enough drive to have games on. how can this be a gaming laptop?!. i said windows can eat up 120 Gb and games can take 50 GB these days. so at best you could get maybe 4 of these AAA games. so what is the point of such a small drive? and the guy said well you can get external drive at a discount with it.

anyway most laptops here have 256 SSD inside. with win 10 preloaded this is really small tight space. maybe with linux it is kind of enough for home office stuff, but not with windows. at least they should have the 2.5 " HDD also installed. i have 500 Gb HDD at work laptop and with not that much stuff added on disk i have about 300 GB taken and about 200 GB available.

---

### Post by sudodus on 2020-02-14
A 32GB USB pendrive is not very reliable. This type of product is mass-produced and is subject to wear and corruption. It is more likely to fail without warning compared to other alternatives.

I would double the backup (using two 32GB USB pendrives) in order to decrease the risk.

[hr][/hr]
A 32 GB SSD connected via USB is a more reliable alternative (and survives mechanical shock much better than a HDD).

---

### Post by guiverc on 2020-02-14
I had a WD Elements drive purchased Dec-2018 go bad after 3 weeks; definitely under warranty but a reading of the warranty (*data becomes their property on warranty claim*) made me **not** claim... (*as I couldn't get it to function in its case to erase my unencrypted data... and opening the case voided the warranty. I realize the data-becomes-their-property on claim is possibly a so-you-can't-sue should data get leaked, but still...*)

Didn't stop me buying another; I've the latest one unopened in it's  box under this desk, and another was purchased last month too which already has data on it.  The data is worth more than the cost of the drive.

(I need it too; *idiot-insurance*, an errant `dd` ran on the wrong box recently erased a 9TB array..)

---

### Post by linuxyogi on 2020-02-14
> **sudodus said:**
> A 32 USB pendrive is not very reliable. This type of product is mass-produced and is subject to wear and corruption. It is more likely to fail without warning compared to other alternatives.

I would double the backup (using two 32 USB pendrives) in order to decrease the risk.

[HR][/HR]
A 32 GB SSD connected via USB is a more reliable alternative (and survives mechanical shock much better than a HDD).

I have registered at MEGAsync. So now I have two backups.

---

### Post by sudodus on 2020-02-14
> **guiverc said:**
> (I need it too; *idiot-insurance*, an errant `dd` ran on the wrong box recently erased a 9TB array..)

Are you still cloning with 'dd' without a safety belt? ;-)

---

### Post by guiverc on 2020-02-14
> **sudodus said:**
> Are you still cloning with 'dd' without a safety belt? ;-)

Yeah, I'm a slow learner....  :eek:

(or maybe just an *unplanned* backup-restoration *testing* opportunity  :p )

---

### Post by TheFu on 2020-02-14
> **guiverc said:**
> I had a WD Elements drive purchased Dec-2018 go bad after 3 weeks; definitely under warranty but a reading of the warranty (*data becomes their property on warranty claim*) made me **not** claim... (*as I couldn't get it to function in its case to erase my unencrypted data... and opening the case voided the warranty. I realize the data-becomes-their-property on claim is possibly a so-you-can't-sue should data get leaked, but still...*)

Didn't stop me buying another; I've the latest one unopened in it's  box under this desk, and another was purchased last month too which already has data on it.  The data is worth more than the cost of the drive.

(I need it too; *idiot-insurance*, an errant `dd` ran on the wrong box recently erased a 9TB array..)

This is an example for why all portable, external, HDDs need to use LUKS encryption.  With LUKS, you wouldn't mind sending the disk in for warranty reasons.

---

### Post by mastablasta on 2020-02-17
> With LUKS, you wouldn't mind sending the disk in for warranty reasons.

good point. never really though about that.

mine is still getting smashed or drilled through though. :)

---

### Post by vidtek on 2020-02-17
One of our local retailers here in the UK went belly up a year ago Maplin Electronics.  I bought a couple of 4tb external Seagate Backup Plus usb3 2 1/2inch drives for £50 each.

I ripped them out of their enclosures and they are used weekly (rotated) to back up my main 4tb 3 1/2 inch in my desktop.  One has already got signs of bad sectors after being used once a fortnight.  I use a Turbo Leopard dual sata clone enclosure, removing the data drive from the desktop, it takes about 6 hours for 3.5tb of data to copy.  I also run a nightly backup using rsync using this enclosure's usb3 connection.
All my multimedia is on a separate 5tb 3 1/2 inch drive (with no backups) I really don't care if I lose that.

I have lots of old hdd's lying around with archive material ranging from my original database3 programme I wrote in 1984 with all my customer data on it when I ran my tv/video repair business in Western Australia.   Wouldn't be allowed now with data protection etc, all addresses, phone numbers and equipment details of each customer, about 20,000 of them, it is now totally useless of course.

---

### Post by mastablasta on 2020-02-17
> **vidtek said:**
> 
I use a Turbo Leopard dual sata clone enclosure, removing the data drive from the desktop, it takes about 6 hours for 3.5tb of data to copy.  I also run a nightly backup using rsync using this enclosure's usb3 connection.


you create 3.5 TB of data a week?

---

### Post by vidtek on 2020-02-17
> **mastablasta said:**
> you create 3.5 TB of data a week?

Haha, No the cloning dock is just that - it clones the whole drive.:biggrin:

---

### Post by TheFu on 2020-02-17
Versioned backups rock.
```
$ sudo rdiff-backup --list-increment-sizes  nextcloud
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Feb 16 02:50:11 2020         9.06 GB           9.06 GB   (current mirror)
Sat Feb 15 02:50:10 2020         10.9 MB           9.07 GB
Fri Feb 14 02:50:09 2020         14.2 MB           9.09 GB
Thu Feb 13 02:50:10 2020         14.9 MB           9.10 GB
Wed Feb 12 02:50:10 2020         15.8 MB           9.12 GB
Tue Feb 11 02:50:10 2020         15.1 MB           9.13 GB
...
Fri Nov 22 02:50:14 2019         14.7 MB           10.4 GB
Thu Nov 21 02:50:11 2019         15.8 MB           10.4 GB
Wed Nov 20 02:50:13 2019         15.3 MB           10.4 GB
Tue Nov 19 02:50:12 2019         15.3 MB           10.4 GB

```
First backup is like an rsync, but all after that are just a few minutes each and add just the change data and metadata for any changes to permissions.
Last night, the versioned back for that system was:
```
no crontab for tf

INFO: Backing up .... --include /root --include /etc --include /usr/local --include /var/www --include /opt --include /var/lib/mysql --include /var/lib/znc --include /home    to 
               backups@romulus::/Backups/nextcloud/
INFO: Removing backups older than 90D.
INFO: Backup Start: Mon Feb 17 02:50:01 EST 2020
INFO: Backup End: Mon Feb 17 02:55:06 EST 2020
INFO: Backup Job Complete.
```
So, about 5 minutes total, including capturing some configuration data pre-backup and removing the old .  That machine runs nextcloud, wallabag and znc.  The summary report for just the backup task alone:
```
=== Time for Backups to nextcloud === 
StartTime 1581925810.00 (Mon Feb 17 02:50:10 2020)
EndTime 1581926082.31 (Mon Feb 17 02:54:42 2020)
ElapsedTime 272.31 (4 minutes 32.31 seconds)
TotalDestinationSizeChange 7797725 (7.44 MB)

```
Daily, automatic, versioned, backups.  The large number of tiny files are what slow this backup down. rsync is slower, BTW.

---

### Post by mastablasta on 2020-02-18
> **vidtek said:**
> Haha, No the cloning dock is just that - it clones the whole drive.:biggrin:

ok i thought you are into some film business or something. 

then you actually just need versioned backups. they are super fast. as The fu demonstrated.

aside from CLI utilities there are GUIs that will setup the scripts. they would then do incremental backups. 

Areca & Duplicati seemed to work best when i tried them out (though i did seek something that would work on linux and windows). 

but for example if you just experiment with system on the drive then snapshots using BTRFS or ZFS4linux might be faster. or virtual machines.

---

### Post by TheFu on 2020-02-18
snapshots alone aren't backups.  They are a method to freeze specific blocks so that a backup tool can get a 100% quiesced backup.  Snapshots are handy for a few other uses, like being able to roll back a recent update/change.

Please don't confuse what virtualbox calls a snapshot with what ZFS, LVM, and btrfs call snapshots.

Also, before deciding to use btrfs, some light reading: [https://wiki.debian.org/Btrfs#Warnings](https://wiki.debian.org/Btrfs#Warnings)

---

### Post by Tadaen_Sylvermane on 2020-02-20
Ive got a couple 2tb usb 3.0 drives holding media and snapraid parity on my server. Haven't had a fail in 3 years. My dad keeps his media and data on a pair of usb 2.0 drives on his mac. As far as I know those drives are at least 8 or 9 years old now with no trouble. I think the fact that these drives almost never physically move contributes to longevity.

---

### Post by vidtek on 2020-02-21
> **mastablasta said:**
> ok i thought you are into some film business or something. 

then you actually just need versioned backups. they are super fast. as The fu demonstrated.

aside from CLI utilities there are GUIs that will setup the scripts. they would then do incremental backups. 

Areca & Duplicati seemed to work best when i tried them out (though i did seek something that would work on linux and windows). 

but for example if you just experiment with system on the drive then snapshots using BTRFS or ZFS4linux might be faster. or virtual machines.

I guess I'm just an old fart with old-fashioned ideas.  :(  Hard drives are so cheap nowadays, and I don't have a lot else to spend my money on, I sure 'aint gonna leave it all to my avaricious Chinese/Aussie daughter-in-law...:evil:.....

I just like the certainty of a another physical identical clone I can lay my hands on......but I also have cloud backups of my 'photos and wills[-o<.....

---

### Post by freebird54 on 2020-02-28
I'm a bit of the old-school type as well - which means that along with the fact that they have never (yet) failed me I have USB2.0 externals. 2 of them are Seagate 2Tb 'Expansion Desk' drives, from 2008 and 2010 (approx) and the third is an Iomega 1tb that I inherited from my sister - I think it is from around 2005 (to augment zip and Jaz drives). They are relegated to backup status now (as I run hi-cap drives internally) and have never blinked as yet - although it is a pain that their SMART system doesn't report temperatures I don't expect that overwork will trouble them!

Freebird54

---

### Post by lammert-nijhof on 2020-03-10
I bought a Samsung 320GB external drive in 2009. After a while I swapped it with my Seagate 160GB laptop drive. The Samsung drive was ~2 times as fast with a throughput of ~80MB/s instead of ~50MB/s, but it had 10 bad sectors. Probably the reason, why a fast drive ended up in an USB 2.0 enclosure. With the new drive Vista started to get somewhat useable. When that laptop died in 2017, I moved that drive in 2019 to my backup server, a Pentium 4 HT. It is now used with FreeBSD and ZFS and its is working together with 2 IDE desktop HDDs and another 320GB laptop HDD on a SATA-1 plug :). 

However that Samsung ex-external drive is still the fastest of the four and it still has 10 bad sectors!

---

### Post by 21Jerry on 2020-06-21
I'm moving away from WD drives.  I must have 10TB of WD SATA drives sitting around that have stopped all together or failed to reassign sectors.  One is a 4TB that I barely used and then found it only had a 1yr warranty. On the other hand, I have a ton of seagate drives going back to 20Gig 10K RPM drives that are still working. I have a quantum fireball and I think it might have been my first drive???  Still works, I think it is 8Gig.  I had three WD drives go bad within a few months of each other in a raid array (striped, bummer). They were 1TB drives, all crossed the 36 month line and then started failing.  I thought I had a power or memory problem but I confirmed it was the individual drives.  The other thing that bugs me is that the 'green' drives, I think, can't be used in simple raids.  Something about timing out?  I can't remember.  They have a parameter I thought you could set to not time-out but it didn't help.

I can go on for hours about the WD My Cloud problems I had before giving up.

---

### Post by ereagle33 on 2020-07-01
I am using a Seagate Momentus (ST9500325AS, 500GB, 2.5 inch, 5400 rpm, 8MB cache) drive that I bought from Newegg in 2010. It is my main media drive for recordings on my HTPC (Intel Atom, NVIDIA ION, MythTV) and has been running 24/7 since 2010. I went with the 2.5 inch for power reasons and for quiet and the 5400 rpm is plenty quick enough to record and/or stream 1080 video. Seagate is my choice.

Oh... *external *HDD... in that case...

I have two Seagate Freeagent Go drives from 2008... 320GB and 640GB. Don't get used a lot, but have been moved to newer USB 3.0 enclosures and are used regularly for backup and as a transfer medium for media files between an HTPC and a desktop. Seagate is still my choice.

---

### Post by kurt18947 on 2020-07-01
I bought a toolless 3.5" USB3 enclosure and a 1 TB. Seagate AV HD for around $50 total. It uses external power so is pretty fast and I can swap HDs as I need to. That in combination with an Rsync GUI does what I need it to do. I just back up data and some config info, I don't worry about drive imaging when I can have a functional fresh install in less than 30 minutes.

---

### Post by mastablasta on 2020-07-03
is USB 3 as fast as SATA3 (transfer speed)? i tried to get this information in wiki and it seem like they have simlar speed.  i see there are external SSD drives available and nvme drives with almost double transfer speed of SSD drive. pricey, but fast. might solve the issue for laptops with small drives (256 GB) and no expansion slot in them.

---

### Post by sudodus on 2020-07-03
@mastablasta,

In the actual case you have to benchmark the devices to get accurate results, because there can be many bottlenecks.

As a general statement, yes, the USB 3 connection can be quite fast, and I have a good experience from running the operating system from an SSD via USB 3.

---

### Post by uninvolved on 2020-07-04
I have a couple of 1 tb WD drives that must be 10 years old by now. One has a couple hundred sectors gone bad - but it has been at that level for years. 

They get used fairly often - but are old enough that they don't get used for anything truly essential. They get rotated around and spend time on-site and off-site as a part of my backup process. In my case, I have ample backups, so if those drives go south it's unlikely to be a major issue - so long as it is caught within a 30 day period (which it should be). 

I have no idea how they've managed to last this long.

This is the worst of the two:    
[http://pix.toile-libre.org/upload/original/1593884501.png](http://pix.toile-libre.org/upload/original/1593884501.png)

Like I said, I have no idea how it has lasted as long as it has. As you can see, it stays powered on quite a bit.

---

### Post by kurt18947 on 2020-07-05
> **mastablasta said:**
> is USB 3 as fast as SATA3 (transfer speed)? i tried to get this information in wiki and it seem like they have simlar speed.  i see there are external SSD drives available and nvme drives with almost double transfer speed of SSD drive. pricey, but fast. might solve the issue for laptops with small drives (256 GB) and no expansion slot in them.

I have an NVMe drive on an Asrock MoBo. The NVMe doesn't 'feel' much faster in daily use than a SATA III SSD. I'm just an ordinary desktop user, no large file transfers which is one place NVMe is supposed to shine. The size difference should be a big help on portable devices. It'll be interesting to see how much difference PCIe 4 will make.

---

