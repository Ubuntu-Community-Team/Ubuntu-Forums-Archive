---
title: "Comparison of Various File Systems"
date: 2008-12-19
forum: The Cafe
---

### Post by The_Orig on 2008-12-19
**Introduction**
I have three computers at three different locations. One has just Ubuntu and the other two are dual-booting with Ubuntu and Windows (I have to have my games :D). Understandably, I got tired of synchronizing data between five operating systems so I decided to purchase an external hard drive to solve the issue. I planned to keep all my data that I needed on it and all would be swell. Inevitably, I began to wonder what would be the best file system to format the drive with. So with some advice and prodding from a friend, I decided to put together a small test and post the results on the Ubuntu Forums in the hopes that someone else could use them. I also decided to throw in some other file systems for comparison.

**File Systems Tested**
[LIST]
[*]EXT3
[*]ReisferFS
[*]XFS
[*]NTFS (Windows)
[*]NTFS (Linux)
[/LIST]

I have NTFS included twice because I wanted to see if there was any noticeable different between how Windows dealt with NTFS and how the 3G driver did. I did the test the exact same way except I was in Windows instead of Ubuntu. The results were interesting ;).

The following quote from Wikipedia explains why I didn't test EXT4:
> On Oct 11, 2008, the patches that mark ext4 as stable code were merged in the Linux 2.6.28 source code repositories, marking the end of the development phase and recommending its adoption.

Notice the recommending part. I only wanted to test File Systems that were widely supported and in use. That and it's not an option in GPARTED ;). I didn't test Reisfer4 for the widely supported reason stated above (I can't use GPARTED as my excuse here :P).

**Test Format**
I wanted my test to cover  small files (such as text documents), medium-ish files (such as music in MP3 format), and large files (such as DivX movies and such). I took this into account when I wrote some code that would do the following:

[LIST=1]
[*]Make X directories in the external
[*]Make one file in each of the X directories
[*]Write Y amount of data to each file
[*]Read all data from each file
[*]Delete all X files
[*]Delete all X directories
[/LIST] 

X specifies the number of directories (and subsequently the number of files) to be created, and Y specifies the size of each file in bytes. I saved the time it took for each operation and compared each file system on its performance making directories, making files, writing to files, reading from files, deleting files, deleting directories, and it's overall performance.

I decided to do all my tests with 10,000 directories/files and file sizes of
[LIST]
[*]1 KiB (To Test Small Files)
[*]1 MiB (To Test Small-ish Files)
[*]3 MiB (To Test Medium-ish Files)
[*]1 GiB (To Test Larger Files) (Tested with only 100 directories/files for obvious space reasons.)
[/LIST]

The test drive was formatted using GParted. It should be noted that nothing else was accessing the test drive while tests were going on. Also, a Totem Movie player was constantly playing a movie during all testing (It was a great way to occupy my time while I waited :P), but besides that nothing was running.

My test code is attached for your use/perusal. It's in Java to make it as portable as possible for everyone that wants to use it.

**Test System**
The computer I used had the following specs:

Hardware:
[LIST]
[*]Intel Core 2 Duo E6700
[*]2 GB OZC DDR2 PC5400
[*]Asus P5LD2
[*]WD SATA 200 GiB Interal Hard Drive
[*]Lacie eSATA 500 GiB External Hard Drive (Test Drive)
[*]NVidia 7950 GX2
[/LIST]

Software:
[LIST]
[*]Ubuntu 8.10 Intrepid Ibex with latest updates (Defaults)
[*]OpenJDK Java 6
[*]GParted
[*]Windows XP Professional SP3
[/LIST]

**Results**
All my results are in the attached Results_And_Code.zip archive. I've included them in the .odt and .pdf file format. You should be able to open the pdf file almost anywhere. You can open the odt file format with open office which comes with Ubuntu by default. Or, if you are on another distro or OS you can download it for free from this [***_SITE_***]("http://www.openoffice.org/").

I hope my work can help someone else :). Cheers!

EDIT: The PDF is fixed :P

---

### Post by SomeGuyDude on 2008-12-19
Reiser's pretty blazing. I'm on XFS now and it certainly feels more responsive. May have to make another switcheroo next time...

---

### Post by binbash on 2008-12-19
where is EXT4 :/

---

### Post by david_lynch on 2008-12-19
Good work - those results are pretty much in line with what I've seen, at least as regards reiser vs other linux filesystems. But, the long term picture for reiser is not exciting at this point. Hopefully ext4 will mature quickly, but in the long run I'm looking forward to btrfs

---

### Post by The_Orig on 2008-12-19
The following quote from Wikipedia explains why I didn't test EXT4:
> On Oct 11, 2008, the patches that mark ext4 as stable code were merged in the Linux 2.6.28 source code repositories, marking the end of the development phase and recommending its adoption. Notice the recommending part. I only wanted to test File Systems that were widely supported and in use. That and it's not an option in GPARTED ;).

I didn't test Reisfer4 for the same reasons as above (I can't use GPARTED as my excuse here :P).

---

### Post by vikramaditya on 2008-12-19
Reiser is frothingly insane, but hey, he coded a mean FS! :D

---

### Post by handy on 2008-12-19
Thanks for spending the time & going to the trouble of doing the tests & posting. :-)

I don't suppose there is a reader for the zipped output?

I screen shot or shots of it would be nice for those of us that don't want to have to install OO.o to view what I'm sure is very interesting data. :-)

---

### Post by Bracken on 2008-12-19
Very nice test!  Thank you for providing this information for our perusal (and making those graphs!).

I'm curious about the two NTFS tests.  Does this test show that if you formatted the drive NTFS you would have fast access under Linux but slow access under Windows?  If so, would it also be in your best interest to test the times of ext3, ReiserFS, and XFS on Windows?   

Also, are there (current) tools for writing to ReiserFS or XFS under Windows?  I did a bit of Googling but haven't found any recent tools.  Using ReiserFS wouldn't do you much good if only one of your OSes supported it. :?

---

### Post by The_Orig on 2008-12-20
I added the other file systems for others to use and for comparison. I'll let everyone draw their own conclusions from the data :).

---

### Post by billgoldberg on 2008-12-20
That's what I expected.

I've been using ReiserFS now for a year or so and it's great.

I just hope it will continue to live on after it's crazy main coder went to jail.

PS: the pdf file didn't look very well on evince (document viewer)

---

### Post by The_Orig on 2008-12-20
Sorry, the open office pdf maker leaves something to be desired >.< I've fixed the problem now and uploaded the new pdf.

---

### Post by handy on 2008-12-20
> **The_Orig said:**
> Sorry, the open office pdf maker leaves something to be desired >.< I've fixed the problem now and uploaded the new pdf.

Thanks so much for doing that for us, it was very interesting to view.  The graphs certainly make comparison easy don't they?

I would have liked to have seen how JFS shaped up in your test, as I use it everywhere except /boot.

Is RieserFS commonly used in NAS devices?  Reason I ask is I'm planning on building NAS quite soon.

---

### Post by mips on 2008-12-20
> **handy said:**
> 
I would have liked to have seen how JFS shaped up in your test, as I use it everywhere except /boot.



I suspect slightly slower than XFS but with less CPU overhead.

---

### Post by Pogeymanz on 2008-12-20
That was really cool. I'm surprised at two things:

1. That Reiser is so much faster than the other guys. Wow.

2. That NTFS Windows was so much faster with the 1GiB files. How in the world did they do that?

Is there any reason you didn't include JFS? That's a very strong filesystem too.

---

### Post by _sAm_ on 2008-12-20
> **handy said:**
> 
I would have liked to have seen how JFS shaped up in your test, as I use it everywhere **except /boot**.

Can you tell me why you are not using it for /boot?

---

### Post by The_Orig on 2008-12-20
Actually, I probably should have included JFS too. As Yoda would say, "HOW EMBARRASING"!. :)

---

### Post by smartboyathome on 2008-12-20
> **_sAm_ said:**
> Can you tell me why you are not using it for /boot?

Probably because Grub Legacy can't boot from JFS partitions.

---

### Post by handy on 2008-12-20
> **_sAm_ said:**
> Can you tell me why you are not using it for /boot?

I use ext2 for /boot

I'm sure I've set up distro's in the past & you had no choice but use ext2 for /boot, I have carried on the tradition, I probably new why once, but I have forgotten at the mo'. ;-)

***[Edit:]** I just read smartboyathome's post above, I suspect that also may have a little something to do with it too. * :lolflag:

---

### Post by TBOL3 on 2008-12-20
Woa, why do we use ext3 then, why not use NTFS for Linux?  I know that it needs defraying, but ext3 needs to do a system check every 30 boot ups or so anyway, so why not?

---

### Post by snova on 2008-12-20
> **TBOL3 said:**
> Woa, why do we use ext3 then, why not use NTFS for Linux?  I know that it needs defraying, but ext3 needs to do a system check every 30 boot ups or so anyway, so why not?

Because most of NTFS is a mystery. As far as I know, we still cannot create partitions or do many advanced operations. There's a lot of missing functionality there.

And Ext3 doesn't defrag, it runs consistency checks. That's more than can be said for NTFS.

---

### Post by init1 on 2008-12-20
> **TBOL3 said:**
> Woa, why do we use ext3 then, why not use NTFS for Linux?  I know that it needs defraying, but ext3 needs to do a system check every 30 boot ups or so anyway, so why not?
Because NTFS is a proprietary FS. 
BTW, EXT3 doesn't need to be checked that often, but it's a good idea. Automatic checking can be disabled, but it's not recommended. I've heard that NTFS partitions should be checked every month or so with Scandisk.

---

### Post by MaxIBoy on 2008-12-21
I'm a convert! I'm picking Reiser next time!


My next computer (we're talking at least two years in the future) is going to have a huge number of high-capacity SSDs in a RAID. Combine that with ReiserFS, and I will have instant-on! It's going to be great.

---

### Post by The_Orig on 2008-12-21
Haha, go for it! I'm glad my work did something for ya'. :)

---

### Post by handy on 2008-12-21
> **MaxIBoy said:**
> I'm a convert! I'm picking Reiser next time!


My next computer (we're talking at least two years in the future) is going to have a huge number of high-capacity SSDs in a RAID. Combine that with ReiserFS, and I will have instant-on! It's going to be great.

I've been researching before building a NAS & I sure wish I could afford to buy high-capacity SSDs to use in it.  I think it will be a few years before I can afford them.

When you can buy a S-ATA_2 1Tb Seagate Barracuda at 7200rpm with 32Mb of caching RAM for around $150- aus, you can't compare that to spending over twice that amount of money for a quarter of the amount of storage.

MaxIBoy, when you get around to setting up your SSD's you will find that you won't need to be using RAID for speed, only maybe for data security.  We will know by then how safe our data is in an SSD.  Many kinds of security measure possibilities will be explored, I expect that we will end up using SSDs that have effective methods to protect our data built in. 

Speed & security, I like it. :-D

---

