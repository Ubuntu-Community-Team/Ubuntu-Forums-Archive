---
title: "New server build, Disk and UPS advice."
date: 2012-08-16
forum: Server Platforms
---

### Post by eldaria on 2012-08-16
Hi all.

Long time since I been here.
Reason is probably that server has functioned well. ;-)
That is until a few weeks ago, when my old P4 10.04 LTS server died.
I suspect a recent power outage is to blame where the power came on and off several times, unfortunately this was in my absence.

Anyway a few days after, the server shut down by itself, and will not come on again.
Well I had for some time planned an upgrade anyway, so instead of trying to revive it, I decided to build a new one.

I'm hoping I can save the some of the content of the disks though, not that any critical is there, but it would be a big hassle to recreate it.

Current setup was a 5 mixed IDE/SATA disk setup, where 2 of them was in a software raid 0, (Yea I know, not safe). :-)

Anyway, my new server that is partially built, and partially in the post, will have a whole lot more space and power.

I need some advice on disk setup, and also some thoughts on UPS.

MB: Asus P8H77I Mini ITX.
CPU: Intel Core i7 3770
MEM: 16GB
System disk: Samsung 128GB SSD
Data Disks: 5x3TB WD RED
PSU: 460W

The server will do a few different tasks, Backup for other computers in the house, HTPC back-end, Virtualization, Video Surveillance server, Low traffic Web server. Well you get the idea, big mix. :-)

So I need a good disk setup.
I was first thinking about Raid-5, but read that with very big disks this is not a good idea due to re-sync time.
Then I was thinking about going ZFS, but sounds complicated.
Now i'm wondering if I should just go a two disk Raid 1, and a three disk Raid 0.
Or two disk Raid 1, with a spare and a two disk Raid 0
To balance reliability and performance.
Unfortunately I was not able to order them from different batch, so 4 disks are from the same date, and the fifth is a week newer than the rest.
I will probably try later to get some more disks, and replace them in the server so I get a better spread.
One thing that is required is data disks should be encrypted.

Any advice?


My second question is on UPS.
I have little experience in this area, and would like some advice on what to get.
I was thinking to get a UPS rated at about 500W and 8-10 minutes at full load.
My calculations are that the server will use about 100W on Idle, and up to perhaps 300W on medium load, these are pure guestimates.

My question is:
Is it possible to detect that the server is on battery instead of mains, and then execute some scipts, to turn of non critical services, and basically go to low power mode.
For example, spin down disks, switch of cpu intensive tasks, etc.
And when the battery level is low, perform a graceful shutdown.
If power comes back then it would go back to normal mode.

Is this possible, and what hardware (UPS) would you advice?

---

### Post by SeijiSensei on 2012-08-16
APC power supplies are well-supported in Linux by the [apcupsd]("https://help.ubuntu.com/community/apcupsd") daemon.  It will monitor the status of the UPS and gracefully shut the machine down if the batteries are close to exhaustion.  You can also configure it to run in a client/server mode so that all the machines in the network can be informed when the power goes out.

Like most UPS manufacturers, APC has an online configuration tool to determine how large a device you'll need.  You're probably looking at something like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16842101381).

---

### Post by bakegoodz on 2012-08-17
I agree with the above post. Do all of the APC's with USB interface with Linux now? I know some years back you would need to get the more expensive Smart-UPS line with serial interface to work with Linux.

I think RAID 10 with 4 drives would be a good option. It has fast rebuild and faster performance than RAID 5 and RAID 1. It has the possibility of surviving 2 drive failures if it is the right combination of drives that fail. All at the cost of halving your disk space.

---

### Post by SeijiSensei on 2012-08-17
Yes, the apcupsd daemon supports both serial and USB connections to the power supply.  I have a [Back-UPS 1300]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101492") here in my office that uses USB.

---

### Post by CharlesA on 2012-08-17
> **bakegoodz said:**
> I agree with the above post. Do all of the APC's with USB interface with Linux now? I know some years back you would need to get the more expensive Smart-UPS line with serial interface to work with Linux.

I think RAID 10 with 4 drives would be a good option. It has fast rebuild and faster performance than RAID 5 and RAID 1. It has the possibility of surviving 2 drive failures if it is the right combination of drives that fail. All at the cost of halving your disk space.

Just to add to Seiji's advice, I haven't run into an APC unit that didn't want to work with apcudpd.

The one I have on my server is this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16842101419](http://www.newegg.com/Product/Product.aspx?Item=N82E16842101419)

RAID10 is mirrored striping, so that should be able to handle 2 drives going out.

I prefer RAID6 for large arrays, or RAID5 for smaller ones. The one I am running now is a 3 disk RAID5 array.

As always backup, backup, backup.

---

### Post by cryptotheslow on 2012-08-17
I'm not sure if this applies to WD Red drives, however on both WD Green and Blue drives I have had problems with the heads continually loading and unloading. Basically the drive parks the heads to save a little power and then along comes the ext4 journalling process and kicks it back into life - this cycle repeats every few seconds leading to a massive Load Cycle Count racking up very quickly.

Install smart tools and keep an eye on value 193 Load_Cycle_Count with:

```
sudo smartctl -A /dev/sda | grep "^193"
```

The WD Green in my little 10.04 server went way over its quoted service limit for cycle counts in only about 4 months before I came to know about it while investigating something else.

There is a tool available to stop the drive parking the heads all the time here:
[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

That worked fine for me on my Greens and Blues. 

Only use it if you come across the problem with your Reds - and as with everything, use it at your own risk. I cannot attest to its suitability for Red drives, just that it worked for me on Green and Blue.

---

### Post by bakegoodz on 2012-08-17
After having several drives fail in a RAID array and then pass a full diagnostic, I researched and found that you need drives with firmware designed for RAIDs. WD Raid edition, WD RED, and Seagate Constellation drives have this firmware. Of coarse they charge more, WD Reds are pretty reasonable, but with a 3 instead of 5 year warranty. I miss when you could hack a WD Black to be a Raid edition.

---

### Post by CharlesA on 2012-08-17
> **bakegoodz said:**
> After having several drives fail in a RAID array and then pass a full diagnostic, I researched and found that you need drives with firmware designed for RAIDs. WD Raid edition, WD RED, and Seagate Constellation drives have this firmware. Of coarse they charge more, WD Reds are pretty reasonable, but with a 3 instead of 5 year warranty. I miss when you could hack a WD Black to be a Raid edition.
Desktop drives have worked fine for me on my home server.

For enterprise use, I would get RE drives, obviously.

---

### Post by bakegoodz on 2012-08-17
You may get away with desktop drives in a RAID. In my experience I had to wipe, sector scan the "failed" drive and then rebuild too many times. The chances of another failure during rebuild is pretty uncomfortable, especially drives over 1 TB.

---

### Post by CharlesA on 2012-08-17
> **bakegoodz said:**
> You may get away with desktop drives in a RAID. In my experience I had to wipe, sector scan the "failed" drive and then rebuild too many times. The chances of another failure during rebuild is pretty uncomfortable, especially drives over 1 TB.
That's true, which is why you have a backup of your array in case it goes down. ;)

I've had a couple of my drives develop bad sectors but it hasn't dropped out of the RAID, which is a good thing.

*knocks on wood*

---

### Post by kgatan on 2012-08-17
If you want to be sure your data is safe and also be able to relax during a rebuild id suggest a raid 5 build on your nas and save the other two disks for a striped backup server.

Since you are considering encryption I guess that you fear possible theft which means no raid in the world will save your data so backup is really your only choice.

Sure everything CAN fail at the same time but at least that possibility is very slim.

Regarding raid approved disks, I don't have any bad experience what so ever with consumer disks. I have had a few builds that have been running for years without any issues.


The apcups daemon logs all events on the APC. I think that you can set up scripts for different events but I'm not sure. Check the documentation on their website.

If you just want to mess around with virtualization i'd recommend VirtualBox headless with phpvirtualbox as web management gui.
Not the best virtualization for a server but I ran it for years on a 10.04 server while experimenting with different OS's and without any issues.

---

### Post by CharlesA on 2012-08-17
> **kgatan said:**
> 
If you just want to mess around with virtualization i'd recommend VirtualBox headless with phpvirtualbox as web management gui.
Not the best virtualization for a server but I ran it for years on a 10.04 server while experimenting with different OS's and without any issues.

+1. I use that setup now, but I have heard KVM is easier on resources, but I don't feel like messing with a working setup.

---

### Post by rubylaser on 2012-08-17
> **CharlesA said:**
> 
RAID10 is mirrored striping, so that should be able to handle 2 drives going out.


Not quite true in all scenarios.  If you lost both drives from the same mirror, you could lose the whole array.  Personally, I use RAID6 + backups at home for anything I couldn't cope with losing.

---

### Post by trundlenut on 2012-08-17
Another vote for APC here.  Works great and I have it setup to email me when the power goes out - though I needed to remember to plug the broadband router into the ups as well so that I actually got the email if I was out of the office.

---

### Post by CharlesA on 2012-08-17
> **rubylaser said:**
> Not quite true.  If you lost both drives from the same mirror, you could lose the whole array.  Personally, I use RAID6 + backups at home for anything I couldn't cope with losing.
Owie.

I would +1 RAID6. ;)

---

### Post by eldaria on 2012-08-19
Hi all, 

Thank you for all the advice, I did not realize there were any replies and did not get any notifications.

After a lot of back and fourth the server is installed, I went for a RaidZ with 5 drives, and the OS, L2ARCH and ZIL on the SSD.
I will add an extra or two disks down the road as a hot spares, connected on USB3, I will probably be  swapping out the drives in the array to get some distribution on productions dates.

For Backup, well this is one of my backup destinations. ;-) For really important data I have already a distributed backup system in place with data saved on several locations.


After reading and comparing prices I went for a CyberPower CP1500AVRLCD.
It has Linux divers, and documentation and It also had a good price for a 1500VA that only the SMX editions of APC had, and from the acupsd site, it says not to get the SMX editions due to incompatibility.

---

### Post by bakegoodz on 2012-08-21
Wow ZFS on Linux? How well is that working?

---

### Post by eldaria on 2012-08-22
> **bakegoodz said:**
> Wow ZFS on Linux? How well is that working?

So far so good (I think). :-)
I was a bit concerned about the speed, but it was all in my head.
It seems ZFS like RAM, and lots of it. and it can be seen why.
When staying with file sizes that are within memory, it is lightning fast.

I was also seeing a strange behavior where writing was faster than reading in some configurations, but again is suspect this was due to me not doing it correctly.

I will probably have to tweak it a bit, I think I reinstalled a few times before settling with a config I liked.
And for a few days it has been running good, I guess I will see how it works over time.

```
sudo zpool status -v
  pool: z1pool
 state: ONLINE
 scan: scrub in progress since Wed Aug 22 06:18:20 2012
    5,31G scanned out of 1,50T at 143M/s, 3h2m to go
    0 repaired, 0,35% done
config:

	NAME                                             STATE     READ WRITE CKSUM
	z1pool                                           ONLINE       0     0     0
	  raidz1-0                                       ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0055446    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053866    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053751    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0076270    ONLINE       0     0     0
	    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0054484    ONLINE       0     0     0
	logs
	  scsi-SATA_SAMSUNG_SSD_830S0XYNEAC667938-part7  ONLINE       0     0     0
	cache
	  scsi-SATA_SAMSUNG_SSD_830S0XYNEAC667938-part8  ONLINE       0     0     0

errors: No known data errors

```

```
sudo zpool iostat -v z1pool
                                                    capacity     operations    bandwidth
pool                                             alloc   free   read  write   read  write
-----------------------------------------------  -----  -----  -----  -----  -----  -----
z1pool                                           1,50T  12,1T  1,63K      0   201M      0
  raidz1                                         1,50T  12,1T  1,63K      0   201M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0055446        -      -    989      0  50,4M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053866        -      -    873      0  51,0M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0053751        -      -    680      0  50,5M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0076270        -      -    784      0  50,7M      0
    scsi-SATA_WDC_WD30EFRX-68_WD-WMC1T0054484        -      -    785      0  51,6M      0
logs                                                 -      -      -      -      -      -
  scsi-SATA_SAMSUNG_SSD_830S0XYNEAC667938-part7   176K  13,9G      0      0      0      0
cache                                                -      -      -      -      -      -
  scsi-SATA_SAMSUNG_SSD_830S0XYNEAC667938-part8  79,1G     8M      0      0      0      0
-----------------------------------------------  -----  -----  -----  -----  -----  -----

```

---

