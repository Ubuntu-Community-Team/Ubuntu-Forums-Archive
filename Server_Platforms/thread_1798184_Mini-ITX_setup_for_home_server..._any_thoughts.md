---
title: "Mini-ITX setup for home server... any thoughts?"
date: 2011-07-06
forum: Server Platforms
---

### Post by Saorex on 2011-07-06
Hi everyone. After dropping the idea of using a plug computer as home server (NAS, web server, etc.), I decided to go with a "cheap" mini-ITX setup, on which I'll install Ubuntu Server. Here's what I have for now. I'll have to add an HDD into that. I'm not 100% sure about the case/PSU, but I'm looking for a fanless system and choices are limited.

Mobo + CPU
Intel BOXD525MW MINI-ITX Intel Atom D525
[http://www.bestdirect.ca/products/231408/BOXD525MW/Intel/](http://www.bestdirect.ca/products/231408/BOXD525MW/Intel/)

RAM
Corsair CMSO4GX3M2A1333C9 4GB 2X2GB DDR3-1333 CL9-9-9-24
[http://www.bestdirect.ca/products/223894/CMSO4GX3M2A1333C9/CORSAIR/](http://www.bestdirect.ca/products/223894/CMSO4GX3M2A1333C9/CORSAIR/)

Case + PSU
Apex MW-100 MINI-ITX Case
[http://www.bestdirect.ca/products/177558/MW%2D100/Apex%20Computer%20Technology/](http://www.bestdirect.ca/products/177558/MW%2D100/Apex%20Computer%20Technology/)

Any idea on how I could improve my setup without changing the price (now $190 + taxes) too much would be appreciated. Thanks!

---

### Post by rubylaser on 2011-07-06
Your Mobo+CPU link is pointed to the case rather than the motherboard. How much storage are you wanting to keep in this system? I ask, because that motherboard only has 2 SATA heads, and adding controller cards, via PCI can be painfully slow.

---

### Post by volkswagner on 2011-07-06
You may want to verify if that board can take a 4Gig RAM module.  Specs on Newegg.com say max RAM is 4Gig, with two slots, the larger chip may or may not be accepted.  I'd recommend getting a dual channel setup with 2x2gig.

---

### Post by ThePol1 on 2011-07-06
> **rubylaser said:**
> Your Mobo+CPU link is pointed to the case rather than the motherboard. How much storage are you wanting to keep in this system? I ask, because that motherboard only has 2 SATA heads, and adding controller cards, via PCI can be painfully slow.

Rubylaser is right on -- I have the same MOBO and case at home and struggled with how to add more than 2 HDs to the system while keeping it cool. I ended up adding 1 system disk to the case and then adding a Rosewill 5-bay eSATA tower to the system with 4 2TB green drives. Embarrassingly, I didn't realize the MOBO only had a PCI slot (and not PCI-E). This limited my choices of controllers since the MOBO doesn't support Native Command Queue (NCQ). I found the Syba SD-SATA2-2E2I to work well for my purposes. With the green drives over a GB network using SAMBA I get 40 Mb/sec sustained transfers.

I struggled for a week or two with some system lockups with that MOBO under load. Things would lockup so completely that there weren't any log messages produced. I found that Intel had released a firmware update that fixed everything. My system has been up 6 months now 24/7 and is rock solid. Hope this info helps!

---

### Post by Saorex on 2011-07-06
...link fixed.

Thanks for the tip about the RAM. It was about 2AM when I wrote that post, and I forgot about that detail when selecting RAM. You're totally right, it should be 2x2. I just changed to link to some Corsair RAM.

About storage, right now I only need something like 150GB. I suppose I'll fit a 1TB or 2TB disk in there, but right now, I'll use a disk I already have at home.

---

### Post by Saorex on 2011-07-06
> **ThePol1 said:**
> Rubylaser is right on -- I have the same MOBO and case at home and struggled with how to add more than 2 HDs to the system while keeping it cool. I ended up adding 1 system disk to the case and then adding a Rosewill 5-bay eSATA tower to the system with 4 2TB green drives. Embarrassingly, I didn't realize the MOBO only had a PCI slot (and not PCI-E). This limited my choices of controllers since the MOBO doesn't support Native Command Queue (NCQ). I found the Syba SD-SATA2-2E2I to work well for my purposes. With the green drives over a GB network using SAMBA I get 40 Mb/sec sustained transfers.

I struggled for a week or two with some system lockups with that MOBO under load. Things would lockup so completely that there weren't any log messages produced. I found that Intel had released a firmware update that fixed everything. My system has been up 6 months now 24/7 and is rock solid. Hope this info helps!

Just read your post. Thanks a lot, this confirms I'm on the right path.

---

### Post by ThePol1 on 2011-07-06
> **Saorex said:**
> Just read your post. Thanks a lot, this confirms I'm on the right path.

Glad to help! Just make sure to update the firmware when you get the MOBO. :)

---

### Post by balderdk on 2011-07-07
yeah i would like to add, i have the same mobo and had some troubles with the server hanging on reboot, (after it did all the usual shutdown it went to a black screen and did nothing) but it's fixed by upgrading the bios :)

I have bought a [Lian li]("http://www.lian-li.com/v2/en/product/product06.php?pr_index=480&cl_index=1&sc_index=25&ss_index=64") cabinet where there is room for 6 x 3.5 and 1 x 2.5 and 1 x 5.25 now it has 2 fans so it's not silent but i didn't expect it to be with that amount of hdd's in anyway :)

I installed a 4 port sata raid controller to get enough space :)

---

### Post by cbanakis on 2011-07-07
Not that this will help.  (A bit over your budget)
(You may want to consider my MB and Processor though, the Atoms are great for netbooks, not so much for servers depending on the application)

But I used a Mini ITX to build my home server, so I thought I'd share my setup.  (Bragging Rights)

Heres a fancy picture of my fancy server :smile:

[http://i340.photobucket.com/albums/o...akis/photo.jpg]("http://i340.photobucket.com/albums/o344/cbanakis/photo.jpg")

Whats in the box...

20x [http://www.newegg.com/Product/Produc...82E16822148337]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148337") $70 each
(You can get whatever drives, but STAY AWAY from WD drives unless they are enterprise drives)

4x [http://www.newegg.com/Product/Produc...-015-_-Product]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816132015&cm_re=port_multiplier_esata-_-16-132-015-_-Product") $200 each

1x [http://www.newegg.com/Product/Produc...-036-_-Product]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115036&cm_re=port_multiplier_esata-_-16-115-036-_-Product") $185

1x [http://www.newegg.com/Product/Produc...82E16811133093]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811133093") $65
(I drilled a 4" hole on top and mounted a 120mm fan instead of installing a cdrom)

1x [http://www.newegg.com/Product/Produc...82E16813500042]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500042") $90

1x [http://www.newegg.com/Product/Produc...82E16819116367]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116367") $70

1x [http://www.newegg.com/Product/Produc...82E16820220396]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820220396") $60

1x [http://www.newegg.com/Product/Produc...82E16820233122]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122") $79

Total Price Tag
$2748.70

Total Capacity at RAID5
26TB

It would probably be much cheaper to build it now though.
I built this setup a long time ago.
(Only have 9TB free now :( )

---

### Post by cbanakis on 2011-07-07
> **Saorex said:**
> Hi everyone. After dropping the idea of using a plug computer as home server (NAS, web server, etc.), I decided to go with a "cheap" mini-ITX setup, on which I'll install Ubuntu Server. Here's what I have for now. I'll have to add an HDD into that. I'm not 100% sure about the case/PSU, but I'm looking for a fanless system and choices are limited.

Mobo + CPU
Intel BOXD525MW MINI-ITX Intel Atom D525
[http://www.bestdirect.ca/products/231408/BOXD525MW/Intel/](http://www.bestdirect.ca/products/231408/BOXD525MW/Intel/)

RAM
Corsair CMSO4GX3M2A1333C9 4GB 2X2GB DDR3-1333 CL9-9-9-24
[http://www.bestdirect.ca/products/223894/CMSO4GX3M2A1333C9/CORSAIR/](http://www.bestdirect.ca/products/223894/CMSO4GX3M2A1333C9/CORSAIR/)

Case + PSU
Apex MW-100 MINI-ITX Case
[http://www.bestdirect.ca/products/177558/MW%2D100/Apex%20Computer%20Technology/](http://www.bestdirect.ca/products/177558/MW%2D100/Apex%20Computer%20Technology/)

Any idea on how I could improve my setup without changing the price (now $190 + taxes) too much would be appreciated. Thanks!

You may want to consider my case too

1x [http://www.newegg.com/Product/Produc...82E16811133093]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811133093") $65
(I drilled a 4" hole on top and mounted a 120mm fan instead of installing a cdrom)

Not as pretty, but cheaper, you wont be limited to low profile add-on cards, and it has a 200W power supply instead of 60W.  (Not Fan-less Though :( )

---

### Post by Groodles on 2011-07-07
Just my 2c, but what you're looking at is way over powered for a simple fileserver.

Do you really need to buy new hardward to run the tasks you want?  This is linux, not windows. ;)

---

### Post by Saorex on 2011-07-10
Thanks for sharing your setups guys, great ideas and realizations in there!

@Groodles: I know I don't need all that power (even if it's not that much for today's standards), and I know I don't have to buy new hardware. But the fact is that I also need to save space. This little box will an old Pentium 4 in a mid-tower case (which I'm giving to a friend).

Finally, you never when you'll need some extra power for, let's say, ripping my own blu-ray disks.

---

