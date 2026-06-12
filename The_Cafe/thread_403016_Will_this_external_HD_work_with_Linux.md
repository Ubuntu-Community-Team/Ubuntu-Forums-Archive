---
title: "Will this external HD work with Linux?"
date: 2007-04-06
forum: The Cafe
---

### Post by RussianVodka on 2007-04-06
I'm gona buy a USB hard drive to free up the space on my laptop. I was wondering if this HD will work out of the box with Ubuntu, and other linux distros.

[http://www.eaglebit.com/ProductDetails.asp?ProductCode=EB-250-00023&Click=14](http://www.eaglebit.com/ProductDetails.asp?ProductCode=EB-250-00023&Click=14)

Also, what would be the best file system to format it with? It's going to be used to store info from computers with both Windows and Linux operating systems. I'm guessing FAT is my only choice?

---

### Post by lukew on 2007-04-06
> **RussianVodka said:**
> I'm gona buy a USB hard drive to free up the space on my laptop. I was wondering if this HD will work out of the box with Ubuntu, and other linux distros.

[http://www.eaglebit.com/ProductDetails.asp?ProductCode=EB-250-00023&Click=14](http://www.eaglebit.com/ProductDetails.asp?ProductCode=EB-250-00023&Click=14)

Also, what would be the best file system to format it with? It's going to be used to store info from computers with both Windows and Linux operating systems. I'm guessing FAT is my only choice?

Hi,

All USB(2) devices should work with out of the box. Very rarely the might but there should always be a fix. You can 99% be sure that everything should work out right.

In terms of format; ext3 is best though not too good if windows needs to access it. perhaps vfat is better.

---

### Post by gh0st on 2007-04-06
I reckon that HDD should work fine on Ubuntu. I have a USB2.0 external disk myself which also has an inbuilt media player, it's really great I can't fault it. Here's a link - [http://www.amazon.co.uk/Freecom-Network-MediaPlayer-Drive-Included/dp/B000B5U3YM/ref=pd_sbs_ce_1/202-9879764-6194266](http://www.amazon.co.uk/Freecom-Network-MediaPlayer-Drive-Included/dp/B000B5U3YM/ref=pd_sbs_ce_1/202-9879764-6194266)

I have my drive formatted to NTFS because the media player software requires it but I still have no problem with Ubuntu. I installed ntfs-3g using [this guide]("http://ubuntuforums.org/showthread.php?t=217009") and it just popped up on the desktop when I plugged it in. Not editing of fstab or anything, all I did was add a couple of sources and do a quick upgrade to get a new version of pmount. Worth checking out if you need NTFS.

If it wasn't required I probably wouldn't use NTFS at the format, I reckon VFAT is a nice option for Linux and Windows. It's a personal choice I suppose.

---

### Post by jlk on 2007-04-06
I purchased a Freecom 400G USB 2.0 external drive a couple of  days ago.  Works perfectly with both Dapper 6.06 and Edgy 6.10.

It came "pre-formatted for Microsoft windows" which one suspects is a FAT32 or similar.  Fdisk  showed 4 partations which were deleted and re-partationed into a single large Linux (type 83) partation.  mkfs to create a new filesystem on it  and then I used rsync to back up my home directory for both of my machines which took a bit over a hour to do the initial rsync of 50G + of files.  A few minutes,  once a week from now one should see to my backup needs.

---

### Post by SunnyRabbiera on 2007-04-06
seagate is also a good brand, I would recommend one for you.

---

