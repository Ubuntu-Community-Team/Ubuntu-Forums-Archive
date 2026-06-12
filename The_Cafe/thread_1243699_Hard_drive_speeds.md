---
title: "Hard drive speeds?"
date: 2009-08-18
forum: The Cafe
---

### Post by billdotson on 2009-08-18
Well, the maximum speed for USB 2.0 is 60megabytes a second. 

SATA 2 is about 375 megabytes per second.

How do these speeds translate to hard drive speeds such as 7200 or 10000RPM? What about SSD drives?

I have a USB 2.0 Maxtor 3200 7200RPM drive. I have never seen the write speed (copying files) ever go above 30 megabytes a second with it. Most of the time it does 15-22. I have an Intel Core 2 Duo E6600 overclocked to 3GHz, 2 GB XMS2 DDR2 800 Corsair Ram running ar whatever bus speed the processor needs to get that fast and an asus p5b deluxe wifi-ap edition.

Is the drive being limited by the USB connection for would it go the same speed if it were hooked up to SATA? I have never tested the read and write times for my Seagate 7200.10 250GB hard drive (3 gigabit SATA I think) so I can't compare. Really though, are there really any drives that can push SATA or USB 2.0 to the limit? Are the hard drives I use my bottleneck on my PC (I use it for commercial games and have an nVidia 8800GT 512MB and a Soundblaster Audigy 4 PCI card).

Would it even matter if I got an eSATA external drive or would it be about the same speed as the USB 2.0 (I know the eSATA is capable of more than USB 2.0 but I don't know where I would find some good places to read about whether the actual drives are capable of that speed).

Also, I hear SSDs are infinitely faster on read times than traditional hard drives but slightly slower on write times. For anybody that uses SSD drives is it worth the write speed tradeoff? Will that get better?

Thanks.

---

### Post by hessiess on 2009-08-18
Yes, USB is the bottleneck with external drives.

> **billdotson said:**
> 
Also, I hear SSDs are infinitely faster on read times than traditional hard drives but slightly slower on write times. For anybody that uses SSD drives is it worth the write speed tradeoff? Will that get better?


I do not use SSD drives, but from my understanding they have a faster seek time, not faster read speed, so they are only faster when working with small files.

---

### Post by bear24rw on 2009-08-18
hdparm says my ssd reads at 200MB/s

---

### Post by billdotson on 2009-08-18
But is the drives themselves are not writing over 30 megabytes per second then they aren't even maxing out USB 2.0 right?

---

### Post by gletob on 2009-08-18
I don't know the exact method of calculation but the two factors are:

Disk Speed e.g. 5400 7200 RPM
and
Platter Density

If you have a two platter 2 TiB disk @ 7200 RPM then it will read faster than a two platter 320 GiB disk @ 7200 RPM

---

### Post by MikeTheC on 2009-08-18
Read and write caches can also be a factor in terms of improving overall performance.

---

### Post by cartman640 on 2009-08-18
> **billdotson said:**
> I have a USB 2.0 Maxtor 3200 7200RPM drive. I have never seen the write speed (copying files) ever go above 30 megabytes a second with it. Most of the time it does 15-22. I have an Intel Core 2 Duo E6600 overclocked to 3GHz, 2 GB XMS2 DDR2 800 Corsair Ram running ar whatever bus speed the processor needs to get that fast and an asus p5b deluxe wifi-ap edition.

The reason you're not getting 60MBytes/s over USB is because that is the maximum burstable speed of USB2, which you will never see in a sustained file transfer.

> SATA 2 is about 375 megabytes per second.
Close, it's actually 300MByte/s due to [8b/10b encoding]("http://en.wikipedia.org/wiki/8b/10b_encoding").

> How do these speeds translate to hard drive speeds such as 7200 or 10000RPM? What about SSD drives?
The rotational speed relates to seek time, rather than transfer speed. The a sector on a platter in a 10,000RPM drive will be under the read head in a shorter amount of time (on average) in a 10,000RPM drive than a 7,200RPM drive. The main advantage of SSD's, is that because they have no moving parts, their seek time is uniform to all locations, and usually measured in nanoseconds, rather than milliseconds with normal mechanical drives.

> Would it even matter if I got an eSATA external drive or would it be about the same speed as the USB 2.0 (I know the eSATA is capable of more than USB 2.0 but I don't know where I would find some good places to read about whether the actual drives are capable of that speed).
An eSATA drive would be faster, for the same reasons that an internal SATA drive is faster than a USB drive.

> Also, I hear SSDs are infinitely faster on read times than traditional hard drives but slightly slower on write times. For anybody that uses SSD drives is it worth the write speed tradeoff? Will that get better?
SSD's are faster, perhaps not infinitely though (~250MByte/s sustained read). The cheaper SSD's are indeed slower to write than read, but they are at least on par or better than a traditional mechanical drive. Combine this with the ridiculously fast seek times and you will have an overall faster drive.

Hope that clears some things up for you.

---

### Post by juancarlospaco on 2009-08-18
***Don't Spin your SSD!***
Cheaper SSD are better than expensive HDD on I/O speed, but low capacity.
:)

---

### Post by MikeTheC on 2009-08-19
> **juancarlospaco said:**
> ***Don't Spin your SSD!***
Cheaper SSD are better than expensive HDD on I/O speed, but low capacity.
:)

Well, thank goodness you mentioned that. I've always been kind and re-wound my hard drive after every use. Sure is good news to hear you don't have to do that any longer with solid state drives.

---

### Post by billdotson on 2009-08-19
Rewinding hard drive? Huh? Are you talking about taking the platter out and messing with it manually on a regular basis? I would have no idea in **** how to do anything that detailed to a computer part. The most "advanced" thing I have done is solder a usb plugin connector back to the leads on a media bay. Not very technical..

Any place you can go to learn about this type of stuff? I have heard allaboutcircuits.com is a great spot to learn about AC, DC and basically anything circuitry/electronics wise (they have a whole book with included beginner projects in it).

---

### Post by MikeTheC on 2009-08-19
> **billdotson said:**
> Rewinding hard drive? Huh? Are you talking about taking the platter out and messing with it manually on a regular basis? I would have no idea in **** how to do anything that detailed to a computer part. The most "advanced" thing I have done is solder a usb plugin connector back to the leads on a media bay. Not very technical..

Any place you can go to learn about this type of stuff? I have heard allaboutcircuits.com is a great spot to learn about AC, DC and basically anything circuitry/electronics wise (they have a whole book with included beginner projects in it).

Oh yes, I have to spin it all the way back to the beginning after a solid day of use. It helps to save wear and tear on the needle.

---

### Post by dtoronto on 2009-08-19
Don't forget SAS or SCSI which runs ~400mbps at around 15000rpm

---

### Post by billdotson on 2009-08-20
Mike, I have never heard such of a thing before. By the time a good drive messes up under normal use shouldn't it be time to buy a bigger one anyway?

---

### Post by gn2 on 2009-08-21
> **MikeTheC said:**
> Oh yes, I have to spin it all the way back to the beginning after a solid day of use. It helps to save wear and tear on the needle.

Setting the arm counterbalance weight properly helps with that too.

---

### Post by billdotson on 2009-08-21
Speaking of hard drives, if you set your BIOS to ACHI and do hot swapping do you have to eject them in the OS or can you just yank em? Does hot swapping not cause data damage?

---

### Post by JohnFH on 2009-08-21
> **MikeTheC said:**
> Oh yes, I have to spin it all the way back to the beginning after a solid day of use. It helps to save wear and tear on the needle.

Do you do that manually yourself?  I have a trick I use.  Take out the platters, turn them upside down, replace them, turn on the drive to spin it to reverse the day's use, and then take out the platters and turn them the right way up again.  Don't forget that last part otherwise then next time you use the drive, all your filenames will be backwards!

---

### Post by cascade9 on 2009-08-21
> **dtoronto said:**
> Don't forget SAS or SCSI which runs ~400mbps at around 15000rpm

SAS 300 has the same max speed as SATA 300. Ultra-640 SCSI is faster, but there isnt that much U-640 stuff around (quick search engine use and I couldnt even find a U-640 drive, they are all U-320 still) No idea on where you got '400mbps'...thats more than SCSI-320, SATA or SAS will take as far as I know. 

Seagate Cheetah 15K.6-
[http://hothardware.com/Articles/Seagate-Cheetah-X156-Hard-Drive/](http://hothardware.com/Articles/Seagate-Cheetah-X156-Hard-Drive/)

15K.7, 15K.6, 15K.5 and 15K.2 (SAS, SAS2, SCSI)
[http://sacklun.ch/?p=22](http://sacklun.ch/?p=22)

> **billdotson said:**
> Is the drive being limited by the USB connection for would it go the same speed if it were hooked up to SATA? I have never tested the read and write times for my Seagate 7200.10 250GB hard drive (3 gigabit SATA I think) so I can't compare. Really though, are there really any drives that can push SATA or USB 2.0 to the limit? Are the hard drives I use my bottleneck on my PC (I use it for commercial games and have an nVidia 8800GT 512MB and a Soundblaster Audigy 4 PCI card).

Yeah, in some ways the Hdd system is normally the bottleneck. But that depends on what your bottlenecking over....if its game performance, then Hdd speeds will matter less than CPU/RAM/Video speed.

> **billdotson said:**
> Would it even matter if I got an eSATA external drive or would it be about the same speed as the USB 2.0 (I know the eSATA is capable of more than USB 2.0 but I don't know where I would find some good places to read about whether the actual drives are capable of that speed). 

Like cartman640 said, a Esata drive is faster. Even some old ATA-100 drives are capaable of pushing USB 2.0 max 'burst' speed, virtually any SATA2 drive will be slowed up by running on USB 2.0. Esata should, in theory, be as fast as SATA internal. It probably wont work like that, but whats a few MB/sec between friends? 

BTW, no single drive will push SATA2 at anythign like max rate, but if you want to raid, its easy to go past SATA2 max bandwidth-
[http://www.xbitlabs.com/articles/storage/display/adaptec-raid-asr5805_8.html](http://www.xbitlabs.com/articles/storage/display/adaptec-raid-asr5805_8.html)

Yes, thats 8x hdds @ RAID 0 @ aprox 900MB/sec. Not really pratical, but blazing fast :D 

For max perfomance, without going to the bank for loan for a SATA2 raid card and a truckload of drives, you could get -

SSD (faster than a 7200 by a long shot, but expensive) 
WD raptor drive (10K SATA2, not as fast, but much cheaper per GB), 
RAID SATA2 (more of a sod-around, but with enough drives and a good controller, pretty fast) 
Or some slightly 'exotic' hardware-

[http://www.hyperossystems.co.uk/](http://www.hyperossystems.co.uk/)
[http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2180](http://www.gigabyte.com.tw/Products/Storage/Products_Overview.aspx?ProductID=2180)

---

