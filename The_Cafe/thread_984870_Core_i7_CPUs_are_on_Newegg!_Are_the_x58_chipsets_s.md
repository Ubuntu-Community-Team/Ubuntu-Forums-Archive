---
title: "Core i7 CPUs are on Newegg! Are the x58 chipsets supported?"
date: 2008-11-17
forum: The Cafe
---

### Post by kernelhaxor on 2008-11-17
Here are the awesome CPUs:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343%201051744913&name=LGA%201366](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343%201051744913&name=LGA%201366)

I wanted to ask if the x58 chipset motherboards which support the above CPUs work with Linux?

---

### Post by Starclopsofish on 2008-11-26
My "is it possible to live without windows" experiment has been an enormous success at school this semester. I'm currently in the process of purging Microsoft's malware form my life entirely. Only problem is my motherboard is completely opposed to letting me use linux on my desktop.

Well.... time to upgrade anyway! :) In the interest of furure-proofing I was holding out for a Nehalem-based system. Been scouring the net for any news of compatibility on these new boards and have found nothing so far. If anyone has any info about this or knows where to find it I'd VERY much appreciate the heads-up!

---

### Post by toupeiro on 2008-11-27
We are putting RHEL4U6 on Nehalem based HP xw8600's.  If that old of a distro can run on it, I would imagine ubuntu 8.10 to have no issues whatsoever.

---

### Post by Skripka on 2008-11-27
Dang...of the 11 LGA1366 mobos on NewEgg, most have 6 RAM slots.....dang.  It's a good things I don't have $600 laying around.

---

### Post by Starclopsofish on 2008-11-27
> **toupeiro said:**
> We are putting RHEL4U6 on Nehalem based HP xw8600's.  If that old of a distro can run on it, I would imagine ubuntu 8.10 to have no issues whatsoever.

Still reeling from dealing with this Foxconn piece of crap, I'm really hoping I can get somebody's experience with a specific board. (not a server board though :lolflag: )

This Gigabyte one looks pretty appetizing. (i.e. comparatively cheap) Does Gigabyte typically support Linux well?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128366](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128366)

---

### Post by toupeiro on 2008-11-27
> **Starclopsofish said:**
> Still reeling from dealing with this Foxconn piece of crap, I'm really hoping I can get somebody's experience with a specific board. (not a server board though :lolflag: )

This Gigabyte one looks pretty appetizing. (i.e. comparatively cheap) Does Gigabyte typically support Linux well?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128366](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128366)

I've got my eyes on the Asus P6T Deluxe...  I've priced together a pretty killer complete core i7 system for under 1,500..  now I'm just trying to see if I can put together 1,500... :P  Might wait until after the holidays.

the 6 ram slots are because of the new memory architecture of the core I7's triple channel memory controller.  It can still operate in single channel like the older dual-channel systems that aren't paired into the right slots, but with the price of ram, why would you? :)

---

### Post by Skripka on 2008-11-27
> **Starclopsofish said:**
> Still reeling from dealing with this Foxconn piece of crap, I'm really hoping I can get somebody's experience with a specific board. (not a server board though :lolflag: )

This Gigabyte one looks pretty appetizing. (i.e. comparatively cheap) Does Gigabyte typically support Linux well?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128366](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128366)

I personally really think that is a poor layout for a main board....Unless you're using single slot GPUs without a cooling duct-you're either goilg to lose 1 or both PCI slots, or have to do some very crafty cabling for both IDE/FDD headers (who puts both at the bottom of a board anyway?) as well as a USB header.

Granted they are squeezing in multiple GPU rails, 6 RAM slots etc....but still it is a poor layout, methinks.

---

### Post by Starclopsofish on 2008-11-27
> **Skripka said:**
> I personally really think that is a poor layout for a main board....Unless you're using single slot GPUs without a cooling duct-you're either goilg to lose 1 or both PCI slots, or have to do some very crafty cabling for both IDE/FDD headers (who puts both at the bottom of a board anyway?) as well as a USB header.

Granted they are squeezing in multiple GPU rails, 6 RAM slots etc....but still it is a poor layout, methinks.

Well I'm not really looking to SLI or Crossfire. Ideally, I'll just use my GeForce 8800 GTX. (Been goin strong since Jan. 2007 ;) ) And probably eventually upgrade to the Radeon 4870 or ATIs next-gen card if their drivers continue to improve. The sound card I'm looking at is a PCIe, so I'm not really worried about the PCI slots.

---

### Post by uljanow on 2008-11-27
IMHO the Asus P6T Deluxe mainboard might work out of the box with ubuntu since it uses splashtop which is a tiny linux OS stored on a SSD. But it might be required to use the audio drivers that are available on Asus' website.

Nehalem is very promising. The cheapest CPU i7-920 is even faster than the Core 2 Extreme QX9770 which costs 1,000 EUR more. The only downside is expensive DDR3 RAM.

---

### Post by SunnyRabbiera on 2008-11-27
> **uljanow said:**
> IMHO the Asus P6T Deluxe mainboard might work out of the box with ubuntu since it uses splashtop which is a tiny linux OS stored on a SSD. But it might be required to use the audio drivers that are available on Asus' website.

Nehalem is very promising. The cheapest CPU i7-920 is even faster than the Core 2 Extreme QX9770 which costs 1,000 EUR more. The only downside is expensive DDR3 RAM.

prices are bound to drop soon though

---

