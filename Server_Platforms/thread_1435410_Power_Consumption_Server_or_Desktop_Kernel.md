---
title: "Power Consumption: Server or Desktop Kernel"
date: 2010-03-21
forum: Server Platforms
---

### Post by Geoff918 on 2010-03-21
Which kernel/install should I use for the lowest power consumption given the following?

I will be using an HP Tower for use in a dedicated server set-up. It will host a website for my small business, a PostgreSQL database, and probably an email server.

Expected system usage: Always on with few requests per day
Website: Few requests, maybe a few per week at best
Email: Similar
PostgreSQL / PHP: One to two accesses per day
SSH: Used for administrative connections

Basically, the server will need to be "always on". It will be a headless system (no monitor). I would like it to be as power friendly as possible as consuming 100s of watts per hour is a complete waste.

My tower has a 1 TB HDD, dual CPU @ 2.6 GHz w/6 GB RAM. I will be using a 64-bit kernel. I am versed at the command-line, and don't need GNOME, etc. However, seeing as the basic desktop install can incorporate all functions of any server install, I'm willing to go that route if the energy consumption would benefit me.

Thanks!!!

---

### Post by sanderj on 2010-03-21
If you're concerned about the lowest power consumption, get an Atom based system. Your TDP will then be a few Watts, instead of 100+ Watt. This will save you about 200 Euro per year on your electricity bill.

See [http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements](http://en.wikipedia.org/wiki/Intel_Atom#Power_requirements)

---

### Post by Geoff918 on 2010-03-21
Well, that may be workable. But, if I'm to buy another device I'd be more apt to purchase a plug computer like the Marvell Sheeva plug which would take a few watts per hour. And the cost would only be about $99 so it's one option.

However, given my current setup--what would be my best option for kernel? I personally fear that the server kernel may be set-up to be running full-tilt so that it's more responsive. I'm not sure of that, but I don't want to see an additional $300 on the household electric bill because I left a computer with sporadic use turned on. 

I've also considered using a laptop for this purpose, though I'm not sure if there would be problems with the laptop going to sleep or anything. I would have to trouble shoot that. In my experience so far, the laptops sometimes have trouble coming back from suspend mode. My old laptop (which would be called into service for this purpose) is a 32-bit system with 2 GB of RAM. I used a dummy system that's exactly the same make and model for tests thus far, but the dummy system has a power issue so it will run on battery for about 1.5 hours before it will burn itself out.

Thanks for any help.

---

### Post by viper250 on 2010-03-21
your computer wont use a lot of power if your power supply is big enough
for example a 400 watt power supply is capable of handling 400 watts but your system may only be using 60 watts
if you have a single hard drive 
the primary thing you want to be concerned with is prevention of dust buildup
the more heat that your system puts out equals the higher wattage use.
so cooling is important.
my own server is a dell poweredge 2800 (this guy has 8 hard drives and 2 optical drives and 9 cooling fans)(uses about 90 watts during peak activity) 
also consider the power saving features your bios may have! you may be able to set it for power saving modes

---

