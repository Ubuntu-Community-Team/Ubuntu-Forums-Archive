---
title: "Building a Terabyte Server ?"
date: 2005-07-08
forum: Server Platforms
---

### Post by MemoryDump on 2005-07-08
Hi all,

I'm starting to plan out building my very own linux terabyte storage server!

I need some suggestions/help in deciding which way I should go.

I want to build this server so it'll last me for years to come! It'll house all my music collection (mp3.. legit of course from my personal collection) .. I was thinking of ripping my DVD collection as well and storing them on this baby as well. I also have all my personal documents I'd like stored.. downloads, isos, and especially my Digital Photographs! (gigs of them)
so this server needs to be pretty quick, reliables, secure, stable and safe.. oh and redundance

Here's what I was thinking:
- raid5?
- 5x? 250GIG 8MB WD or Maxtor or Seagate SATA or ATA drives.?
- ubuntu or fedora core 4
- sata or ata controller card ?? (which one would be best?)
- cpu/mobo/ram?
- case?
- p/s?

I have an old P3 850 (i think) with 513MB sitting in my basement collecting dust running fc3 right now. I though about using it to hook up this RAID array. Perhaps I should consider using an external case for the drives? (which one though?)

I also though about using my current Antec Case I have which has a 430W P/S and plently of room for drives. (i could always build another workstation later)

I'm trying to keep the costs as low as possible. So anything to save me $$ is a huge plus!

I'd need some details!

thanks in advance!
-MD

---

### Post by LordHunter317 on 2005-07-08
I would do the following:
[list][*]**Hardware** SATA raid.  This doesn't mean an onboard controller on a mobo either.  This means a $300-500 dollar offering from the likes of LSI and 3Ware.  LSI makes some very nice 6 and 8-port hardware SATA controllers.[*]RAID-5 will be fine for you needs[*]If you do 8-drives, 430W *may* be pushing the supply, it depends on how good it is.  If it's an Antec, you'll probably be fine, but you'll need a peak draw of 2A on the 12V rail for each drive to handle spinup.  Check the specifications before you buy all your drives.[*]Distribution won't really matter for this[*]It may be worthwhile to look at a cheap NAS solution, or something like Apple's XServe RAID.[/list]

---

### Post by MemoryDump on 2005-07-08
this is a fun project.. and I do realize it'll cost me between $1500 and $2000 (and I'm paying in Canadian dollard!! DOH!)

Here are some things I am considering:

Promise SuperSwap 4100
[http://www.promise.com/product/product_detail_eng.asp?segment=undefined&product_id=120](http://www.promise.com/product/product_detail_eng.asp?segment=undefined&product_id=120)

FastTrak S150 SX4-M
[http://www.promise.com/product/product_detail_eng.asp?segment=RAID%20HBAs&product_id=124](http://www.promise.com/product/product_detail_eng.asp?segment=RAID%20HBAs&product_id=124)

I'm looking at getting 4x WESTERN DIGITAL 320GB SERIAL SATA 7200RPM 8MB CACHE HARD DRIVE (WD3200JD)

Using RAID5 I could get a nice 960GIG server running. I would add a seperate 40GIG IDE drive to run the OS on it.

I'm still debating if I should built a new system to run it. (mobo/cpu/ram/case/ps/etc)

Like I mentioned before I have my Antec Tower with a Antec 430PS in it. It's got plenty of room and fans in there so I wouldn't need the Promise SuperSwap (even though it would be sweet)

If I were to build a new station.. what would be some suggestions? AMD? Intel? Speeds? Ram? Mobo?

I'll be keeping you all informed on how it goes ;)

thxs
-MD :P

---

### Post by LordHunter317 on 2005-07-08
That Promise card isn't real hardware RAID, and I would avoid it.  The extra cost to get a 6-port LSI SATA controller (even if you don't use all 6 ports) would likely be worth it, if you have the money to spend.

If you don't, then just get the cheapest 4 port card you can find (or 2 2-port ones) and use linux software RAID.

---

### Post by crmanski on 2005-07-08
I liked what I saw on slashdot a couple of weeks ago...
[http://www.inventgeek.com/Projects/poormansraid/poormansraid.aspx](http://www.inventgeek.com/Projects/poormansraid/poormansraid.aspx)
A modification of this to meet your needs might work for you.

---

### Post by Mr. Electric Wizard on 2005-07-08
Another thought...
Buffalo makes a NAS called the TerraStation that has 1,000 gigs, and has a fully configurable RAID, all the way from 0 to 5.
All this for $1,000!

---

### Post by relix42 on 2005-07-08
I've built many of these type of machines before (800MB - 4TB) with Fedora Core - I'm preparing to reinstall one with Ubuntu and see how it performes.  My recommendations for a 1TB or so box:

* **3Ware Serial ATA RAID Adapter **- Available in 4, 8 or 12 port cards.  WIll *very nicely* handle the RAID and well supported in any Linux flavor.  Recovers nicely from drive deaths, but, RTFM the bool before adding your new drive back in and do it properly.  The cards are very conservative (i.e. will shut off a flaky drive and leave it off in order to protect your data.)
* **Avoid Promise like the plague** - I've worked about 6 different versions - all were flaky under both Linux and Windows.  Promise will always "promise" that the next BIOS update will fix all your problems - I'm still waiting.
* **Do not forget to properly scale your power supply** for the load of hard drives.  You should insure that you have enough power as well as even power - read a few reviews of power supplies and look at the raitings for consistency of power on the different rails under load.
* **Get a mainboard **that is really designed for running this type of hardware - go at least entry level server board - don't go with a workstation board - you'll have problems.
* And, as always, get an enclosure that will properly cool your system running this type of hardware.  If you want to go a bit upscale, Chenbro makes cases that are perfect for what you are doing.

Hope this helps.

---

### Post by MemoryDump on 2005-07-08
I'm looking at this card now:
 	
[MegaRAID SATA 150-6](http://www.lsilogic.com/products/megaraid/sata_150_6.html)
Looks pretty sweet. :) $388+tax/shipping in Canada.

Again, I think I'll put in 4x 250GB or 320GB SATA drives with 1x 40GIG IDE drive for the OS. (or maybe 2 small SATA drives on the 2 spare ports of the card.. hmmm)

even though the CHENBRO would be sweet to have it's a little out of my price range. Maybe if I were building a data centre I'd be on the right track :p

I have this case right now as my Workstation. I was thinking of using it as my new storate server.
[Antec PLUS1080AMG with 430W TruePower P/S](http://www.antec.com/us/productDetails.php?ProdID=91082)
It's got several fans in it to keep everything cool and plenty of room to mount the drives.
The specs are:
P4 2.36 processor with a [Asus P4P800-Deluxe Board](http://usa.asus.com/prog/spec.asp?m=P4P800%20Deluxe&langs=09) with 1 gig of RAM.

or I was thinking of building another box from scratch..  however I need some ideas for a good drive enclosure for 4 or 6 SATA drives.. That's why I was considering the [SuperSwap 4100](http://www.promise.com/product/product_detail_eng.asp?segment=undefined&product_id=120) from Promise..

thxs
-MD

---

### Post by Mr. Electric Wizard on 2005-07-08
I, along with several of my friends have had good luck with Promise...

---

### Post by marcovanbeek on 2005-08-13
Hi there,

Be careful with partitions over 2TB. Above that you need to run a 64bit version of the OS, and ther are quite a few pitfalls, including only being able to use parted as the partition software, having to change the standard partition table type to gpt (normally the partition table is only 32 it) and (and this is the bit I still have to check in Ubuntu) the kernel needs ‘Large Block Device’ support enabled.

However, the good news is that the 3ware 9000 series is supported by the kernel (>2.6.9) so is supported "out of the box" by Ubuntu 5.04. Have a look here for some useful information:

[http://www.3ware.com/KB/article.aspx?id=11920](http://www.3ware.com/KB/article.aspx?id=11920)
[http://www.3ware.com/KB/article.aspx?id=13431](http://www.3ware.com/KB/article.aspx?id=13431)

Regards,

Marco

---

### Post by pcd927 on 2005-08-13
what Im suggesting is go to ebay find somthing

---

### Post by Brian Puccio on 2005-08-13
Distro doesn't matter, I had a spare machine doing this for me for over a year (had an LSI 150-6 card in it) and I had no issues, everything just worked. Since then I've moved on to a [smaller unit](http://www.newegg.com/Product/Product.asp?Item=N82E16822155306) which I picked up for $850 on sale.  A lot quieter and probably uses a whole lot less electricity.

---

### Post by Gog on 2005-08-22
Word of warning for anyone tempted by the buffalo NAS' .... the raid5 is a (very poor) software implementation. I got around 5MB/s write (on a gig lan without jumbo frame support) Enabling jumbo frames will up it a bit, but don't expect anything remotely approaching gigE speeds. Reading, to be expected, was a good deal faster

---

### Post by tom-ubuntu on 2005-09-01
I've got plans on building a new fileserver aswell. My old 720gb raid is running out of space....

How do you calculate how much power the powersupply needs?

---

### Post by topslakr on 2005-09-07
I have a 1.5TB Server running Raid 5 on a broadcom bc4852. The supported os's are Suse, Fedora, and Red Hat. I wasn't happy with the stabilty of core 3 so i decied to give the SDK pkg for the modules a try. Took me all of about 2 mins to get the module for the card compiled and ready to go. The 4852 has been rock solid and since i got rid of core3 the server has been as well. The broadcom card handles 6 250GB sata drive giving me a little over 1.1TB after formatting ect and the transfer speeds are great. The system also has some other software raid arrays bringing me up to 1.56TB. Since i compiled the modules myself I have been thrilled with the performance and the stability. The card was a bit pricy but for the feature list I think it was worth it. I'd recommend the card only if your willing to compile the modules though. Its very simple, just download and un tar the pkg then rename Makefile_2.6 or Makefile_2.4 to Makefile depending on you kernel version and run make then make install. A quick depmod -a and you ready to modprobe it and your done. Less steps to do that then it took to install the modules Broadcom offered for core 3 and Suse. I had to work for 45 minutes every time core 3 crashed to get the array to show up in linux, just refused to see it. Now with the drivers I compile by hand the array is mounting with fstab no problems.

There's My Two Cents...

Robert

---

### Post by phrozen on 2005-09-14
id say up your ram from 1gb to at least 2gb, if i was doing it id do 3-4gb
as for processer id would go for an AMD but when intel releases its new line of chips i may chnage my mind about that one, but for now i would go for the AMD, for one its got 64bit support and i think they are faster and better in general

---

