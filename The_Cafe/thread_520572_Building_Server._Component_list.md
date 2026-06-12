---
title: "Building Server. Component list"
date: 2007-08-08
forum: The Cafe
---

### Post by realalehunter on 2007-08-08
Hi, Iv been tasked with building a new file server from for work which will allow us to store all our documents on, run an internal webserver and svn version control.

We want about 1.5 TB of storage and have decided on raid 5. I have devised a list of stuff and would just like to get peoples opinions of anything I might have missed and component compatibility etc. It will be running Ubuntu and I am planning on using the built in Linux raid software.

The list is:

****************************************
Foxconn P35A motherboard. £76.27
[http://www.cclonline.com/product-info.asp?product_id=13952&category_id=251&manufacturer_id=0&tid=p35a](http://www.cclonline.com/product-info.asp?product_id=13952&category_id=251&manufacturer_id=0&tid=p35a)
The spec says it SATA Support -5 x SATA.Anyone know if I Will be able to just plug them in and use the Linux software Raid

****************************************
Intel Core 2 Duo E6750 processor 2 x 2.66GHz,1333 FSB, 4MB L2 Cache £125.37
[http://www.cclonline.com/product-info.asp?product_id=14959&category_id=249&manufacturer_id=0&tid=bx80557e6750](http://www.cclonline.com/product-info.asp?product_id=14959&category_id=249&manufacturer_id=0&tid=bx80557e6750)

*****************************************
4 * 500GB Western Digital Caviar SE16 WD5000KS 4 * £68.98 = £275.92
[http://www.cclonline.com/product-info.asp?product_id=6624&category_id=112&manufacturer_id=0&tid=wd5000aaks](http://www.cclonline.com/product-info.asp?product_id=6624&category_id=112&manufacturer_id=0&tid=wd5000aaks)

*****************************************
Coolermaster Hyper L3 CPU Cooling fan for the CPU £22.37
[http://www.cclonline.com/product-info.asp?product_id=7078&category_id=99&manufacturer_id=0&tid=rr-lch-p9e1](http://www.cclonline.com/product-info.asp?product_id=7078&category_id=99&manufacturer_id=0&tid=rr-lch-p9e1)

*****************************************
Antec Atlas Server Case, £87.71 inc VAT comes with 550W power supply.
[http://www.cclonline.com/product-info.asp?product_id=10548&category_id=53&manufacturer_id=0&tid=0761345-01701-5](http://www.cclonline.com/product-info.asp?product_id=10548&category_id=53&manufacturer_id=0&tid=0761345-01701-5)

*****************************************
RAM (found some compatible on crucial.com). 2GB kit (1GBx2), Ballistix Tracer 240-pin DIMM (with LEDs), DDR2 PC2-5300 memory module is UK equiv of £75.
[http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=9049FA5FA5CA7304](http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=9049FA5FA5CA7304)

******************************************
48x Samsung CD-ROM Drive £7.95 [http://www.cclonline.com/product-info.asp?product_id=242&category_id=117&manufacturer_id=0&tid=ts-5192c/iblh](http://www.cclonline.com/product-info.asp?product_id=242&category_id=117&manufacturer_id=0&tid=ts-5192c/iblh) for installing the OS.


Note that the case comes with a power supply and we can borrow a screen, keybourd and mouse from another compuer as we will only need them to set it up and then we will just leave it alone.

Thanks for any help

---

### Post by SeanTater on 2007-08-08
If you are planning on using this server mainly for storage, then you might consider more memory, as memory access is much faster than disk. Of course, if this server is not under heavy load or the files are gargantuan, this will not make much difference.
You could probably save some electricity if you use something like a Via instead of Core 2 (the average Via uses about 3 to 7 watts instead of 60 to 120 or so, at the expense of having 1/4 the speed). But the disks will be using more electricity than the processor anyway, so that difference will probably be neglegible.

---

### Post by Zuph on 2007-08-08
Please get a hardware RAID solution.  It will be much more stable, much more flexible, and will make it dead easy to change to a different OS if you ever need to.

---

### Post by realalehunter on 2007-08-08
Thanks for your feedback Sean. Getting more Ram won't be a problem I could double it to be 4Gig. I will have a look into Via, will that be compatible with the motherboard.

Cheers, Matt

---

### Post by mips on 2007-08-08
Get a Tyan motherboard or server.

Why not simply buy an off the shelf server ?

---

### Post by realalehunter on 2007-08-08
Hi Zuph, Iv had a look into both hardware and software Raids and there seems to be very mixed opinions on which is best (except for fake raid which everyone agrees is rubbish)

Do you use a hardware Raid yourself. I was looking at LSI Logic SATA MegaRAID

---

### Post by realalehunter on 2007-08-08
> **mips said:**
> Get a Tyan motherboard or server.

Why not simply buy an off the shelf server ?

Any reason why Tyan?

We were origionally going to buy a server but my boss wants to build us to build one to save money and have the experience of building one.

---

### Post by lintoolman on 2007-08-08
I would suggest two things.

A separate OS hard drive.  It doesn't have be large size

Change the cd drive to a dvd drive.

---

### Post by ephesius on 2007-08-08
Might I suggest a 15000 rpm Raptor drive for the os.

---

### Post by mips on 2007-08-08
> **realalehunter said:**
> Any reason why Tyan?


From what I gather they are very good server boards and highly recommended.

I would also go for a hardware base RAID solution like Adaptec etc.

---

### Post by realalehunter on 2007-08-08
Il have a look into another disk for the OS and a hardware raid. 

Thanks

---

### Post by SeanTater on 2007-08-08
Via isn't a processor in the same sense as AMD and Intel. It's built into the motherboard, so Via is both the motherboard and the processor..  Most of their motherboards are usually low end because of their performance. However, they have very low electrical needs and need no fans because they produce almost no heat, so they are totally silent.

All in all -- I imagine the core 2 duo and double the memory is what you are looking for..

---

### Post by realalehunter on 2007-08-08
Thanks Sean. 

If I were to go with the setup that I listed but with double the ram and the OS on its own seperate hard drive and used an  Adaptec or LSI Logic raid, would everything be compatable? 

I need to look into the good and bad points between the 2 raids as they both seem to have pretty good reviews.

Thanks

---

### Post by SeanTater on 2007-08-08
Honestly, I have never used RAID, but I read (a little) on it, so what is going to be the most difficult is defining "hardware". Almost all of them have some type of "Hardware acceleration" that ends up not helping at all and just makes configuration more difficult. You will have to ensure that it is not "acceleration" and that it actually virtualizes the array, at least that is the way I understand it.

From the looks of it you have a very capable setup. It should fit the bill quite well.

---

### Post by realalehunter on 2007-08-09
Right after recommendations from people I have made a revised list. This includes a hardware raid card, slightly downgraded processor, cheaper RAM, different cooler and hard drives and also an extra drive for the OS. Let me know your opinions please.




3ware 9650SE-4LPML PCI Express Lanes: 4 SATA II Controller Card RAID Levels 0, 1, 5, 10, Single Disk, JBOD &#8211; Retail
$395.00 from
3ware store [http://store.3ware.com/?category=10&subcategory=8&productid=9650SE-4LPML](http://store.3ware.com/?category=10&subcategory=8&productid=9650SE-4LPML) or in UK [http://www.wizardprice.com/products/9650SE-4LPML/KIT.3W](http://www.wizardprice.com/products/9650SE-4LPML/KIT.3W)
£216.52




48x Samsung CD-ROM Drive [http://www.cclonline.com/product-info.asp?product_id=242&category_id=117&manufacturer_id=0&tid=ts-5192c/iblh](http://www.cclonline.com/product-info.asp?product_id=242&category_id=117&manufacturer_id=0&tid=ts-5192c/iblh) for installing the OS.
£7.95




Foxconn P35A motherboard. from cclonline. 5 Sata, CPU socket 775. RAM support Dual Channel DDR2 1066(oc) / 800 / 667 x 4 DIMMs, Max 8GB
[http://www.cclonline.com/product-info.asp?product_id=13952&category_id=251&manufacturer_id=0&tid=p35a](http://www.cclonline.com/product-info.asp?product_id=13952&category_id=251&manufacturer_id=0&tid=p35a)
£76.24




Intel CPU Core 2 Duo E6750 2.66GHz 1333FSB LGA775 4MB cache Retail inc.Fan (3yr Manufacturers Warranty)
[http://www.microdirect.co.uk/(19964)Intel-CPU-Core-2-Duo-E6750-266GHz-1333FSB.aspx](http://www.microdirect.co.uk/(19964)Intel-CPU-Core-2-Duo-E6750-266GHz-1333FSB.aspx)
£116.91



RAM Geil Ultra DDR2 2.0GB PC6400 Dual Channel memory kit (2 x 1GB) * 2 800MHz (4-4-4-12) +Aluminium heat spreader
[http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=14777](http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=14777)
£64.61 * 2 =
£129.22




4* 500GB Samsung SATA II 300 Hard Disk Drive 16MB cache 7200rpm oem from [http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=16077&source=PriceGrabber](http://www.microdirect.co.uk/ProductInfo.aspx?ProductID=16077&source=PriceGrabber)
4 * £61.09 = £244.36



1 * 80GB Samsung HD080HJ SATA II 300 Hard Disk Drive 7200rpm 8MB cache oem for the OS from [http://www.microdirect.co.uk/(10273)80GB-Samsung-HD080HJ-SATA-II-300-Hard-Disk.aspx](http://www.microdirect.co.uk/(10273)80GB-Samsung-HD080HJ-SATA-II-300-Hard-Disk.aspx)
£27.38



Serial ATA Power Splitter for the fith operating system hard drivehttp://www.netshop.co.uk/productcategorydetail.aspx?categoryid=53771
£2.29



Arctic Cooling Freezer 7 Pro P4 upto 4.4GHz (socket 775) from [http://www.microdirect.co.uk/](http://www.microdirect.co.uk/) 11433 Arctic-Cooling-Freezer-7-Pro-P4-upto-44GHz.aspx
£15.92




Antec Atlas Server Case, inc VAT comes with 550W power supply.
[http://www.cclonline.com/product-info.asp?product_id=10548&category_id=53&manufacturer_id=0&tid=0761345-01701-5](http://www.cclonline.com/product-info.asp?product_id=10548&category_id=53&manufacturer_id=0&tid=0761345-01701-5)
£87.71


Nvidia 
128MB MSI 7100GS
[http://www.cclonline.com/product-info.asp?product_id=13019&category_id=256&manufacturer_id=0&tid=nx7100gs-td128e](http://www.cclonline.com/product-info.asp?product_id=13019&category_id=256&manufacturer_id=0&tid=nx7100gs-td128e)
£23.46 


TOTAL SO FAR
Around £950

Thanks

---

### Post by regomodo on 2007-08-09
> **Zuph said:**
> Please get a hardware RAID solution.  It will be much more stable, much more flexible, and will make it dead easy to change to a different OS if you ever need to.

i was going to the same thing with an LSI megaraid card but people kept recommending a software raid. The main reason being is that if the hardware fails and you can't get another card you are screwed. However, if you fakeraid in ubuntu you just have to swap the drives in a different comp. That's what i've been advised but not implemented. Have to wait until next month before i make my own fileserver. I'll be experimenting on running the OS on CF card+adapter and using x4 500GB drives of differing manufacturing date. Some reccommend different manufacturers but i like the samsung sata spinpoints. They're quiet and i already have 2 of them.

---

### Post by realalehunter on 2007-08-09
Forgot about a graphics card. Iv added one to the list

---

### Post by mips on 2007-08-09
> **realalehunter said:**
> Forgot about a graphics card. Iv added one to the list


Why ATI ? One would hope most people have learned the hard way by now.

---

### Post by realalehunter on 2007-08-10
> **mips said:**
> Why ATI ? One would hope most people have learned the hard way by now.

Just because its really cheap and I will only really need  to use it to initially set the system up. Whats wrong with ATI, do you reckon I will have a hard time getting it working or something?

---

### Post by mips on 2007-08-10
> **realalehunter said:**
> Just because its really cheap and I will only really need  to use it to initially set the system up. Whats wrong with ATI, do you reckon I will have a hard time getting it working or something?

Driver wise they have a pretty bad reputation in Linux. Just search this forum for ATI and you will see what i mean. If you are going to spend the money you might as well get a nVidia card. That same site has one for about 3 pounds more than the ATI.

---

### Post by realalehunter on 2007-08-10
Ah right ok, Il get one of those then. Thanks for your help.

---

