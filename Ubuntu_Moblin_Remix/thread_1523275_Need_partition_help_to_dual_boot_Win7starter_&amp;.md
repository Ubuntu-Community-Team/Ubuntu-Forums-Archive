---
title: "Need partition help to dual boot Win7starter &amp; Ubuntu--Samsung N150 Plus netbook"
date: 2010-07-03
forum: Ubuntu Moblin Remix
---

### Post by karenk on 2010-07-03
I'm confused about all the partitions that came on my Samsung N150 Plus netbook.  My goal is to dual-boot Win7 and Ubuntu Netbook Edition so I need to create Ubuntu partitions, but there are already 4 partitions so how can I create one for Ubuntu and one for its swap space?

I've got a GParted screenshot from booting a Live USB as well as Windows Disk Management screenshots posted.

Can this be done without voiding the warranty and without creating recovery disks (no external dvd drive)?

Thanks for any help!!  Really want to do this today so I can take it on a short trip tomorrow, but more importantly for a longer working trip the second half of July.

---

### Post by camorri on 2010-07-03
From what I can see you have 4 primary partitions. Dumb!
You can only make four primary partitions on a drive. From what you have, you could move what ever you have on the last partition to windows, say sda3, and use that partition to install linux. Not sure, you might have to delete sda4, then re create it, and then you would  have to format sda4. This means everything for linux would  
be on sda4, no swap possible, or separating the root partition form /home. Not nice. 


With gparted you can adjust the size of sda3, after you shrink sda4, if you need more space for windoze. Make sure you have a backup of all your windoze stuff first. 

My netbook is a HP Mini 210. 160 gig drive. I blew 
  windoze away. Warranty? As long as any problems are hardware, loosing windoze shouldn't matter. 

I installed from a USB memory stick using unetbootin. 

Good luck with it. 

The way to get more partitions is to use extended partitions.

---

### Post by swallisa on 2010-07-05
Looks like a typical OEM set up.  sda1 is recovery, sda2 is boot, sda3 is winbloze and sda4 is for back up.  I would use gparted and take back the real estate myself.  lose recovery and the sda4 partition use this space for ubuntu reserve 2gb for swap and you should be good to go.

---

### Post by triwave on 2010-07-27
I had exact same situation and as already mentioned you are limited to 4 primary partitions which are all used up. You must free one of those up some how ...

What I did first time to be safe was save a complete disk image (on an external drive) just as the machine was setup from the factory since creating recovery disks would be a pain - this way if all goes to he%$# I can restore it back to the factory configuration.

Having said that, when backed up I blew away the recovery partition. I then shrank windows way down and used the free space created to make 1 extended partition with 3 logical partitions in it - one for the system (/) , one for the user folders (/home) and a 3rd for 2048MB of SWAP space. ubuntu can be installed into this configuration if you use manual partitioning instead of automatic partitioning.

Now most of my disk is dedicated to ubuntu but I can still boot into Win 7 if required.

---

