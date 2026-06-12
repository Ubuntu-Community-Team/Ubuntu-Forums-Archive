---
title: "Should I upgrade my Phenom II X4 B97 to a Ryzen 3 2200G?"
date: 2019-02-28
forum: The Cafe
---

### Post by lammert-nijhof on 2019-02-28
My system is a 2008 HP dc 5850, it still works great and I'm looking for valid excuses to buy a Ryzen. The system has:

[LIST=|INDENT=2]
[*]4-core AMD Phenom II X4 B97 at 3.2 GHz and 95 Watt;
[*]8 GB 800MHz DDR2 (maxed out according specs);
[*]128 GB SPCC SSD with 3 old striped HDDs (1 TB, 500 GB and 2.5" 320 GB);
[*]SATA-3 PCIe card on PCIe 2.0 (5 Gbps, so less than 500 MB/s left for the SSD);
[*]USB 3.0 PCIe Card and a front panel (2 + 2 plugs);
[*]GeForce 8400GS (1 GB and a whopping 16 CUDA cores) for HD videos (no games).
[*]2008 22" Monitor, Fujitsu/Siemens LW22 (vga only; 1680 x 1050 at 60 Hz)
[*]and the original;
[LIST]
[*]300 Watt power supply;
[*]DVD R/W;
[*]4 SATA-2 connectors
[*]Integrated audio;
[*]Integrated USB 2.0 (6 + 2 plugs);
[*]integrated 1 Gbps Ethernet;
[*]HP motherboard with integrated video;
[*]Mini tower.
[/LIST]
[/LIST]
Ubuntu Mate 18.04 boots in 23 seconds from SSD with the Zeta File System (ZFS). All my Linux Virtual Machines (XFCE to KDE, Gnome-3) boot in between 15 and 24 seconds from ZFS. The SSD and HDDs do use ZFS in a 3-level storage hierarchy (memory cache 2 GB; SSD cache 45 GB and 3 striped HDDs 1.82 TB). All HDDs and caches are LZ4 compressed giving a space and IO speed advantage of a factor ~2.0 for the VMs. The caches store twice the number of compressed bytes, all HDDs together can store say ~3 TB (ISOs, videos, photos and music are already compressed and are skipped by LZ4). 

The effective IO throughput (number of bytes read/written by the user program) for e.g. the virtual machines is now; 

[LIST]
[*]striped HDDs reach 2 x ~200 = ~400 MB/s;
[*]SSD cache 2 x ~400 = ~800 MB/s (hit rates ~25% after a while) and
[*]memory cache exceeds 1 GB/s also on DDR2 (hit rates a steady 90%).
[/LIST]
I'm curious how this 3-level storage hierarchy would run on a future Ryzen with PCIe 3.0 for SSD cache; DDR4 3000 MHz for memory cache; 16 GB of RAM and the 2200G is almost twice as fast as the Phenom. However playing with VMs, I only get 100% CPU loads on the Phenom II, if I update the Windows 7 VM and Windows 10 VM at the same time. Also my video loads can be relatively easily handled by this PC, I almost never load the GeForce over 50% in both space and throughput. 

The 2008 HP could die of old age at any moment, so that is the only objective reason, I have to upgrade. The only complaints are:

[LIST]
[*]This week the small fan on the video card stopped working, so that card runs now up to 90°C (max < 127°C).
[*]The monitor started to show burn-in signs last year.
[*]The case fan starts to get noisy occasionally.
[/LIST]
The two 3.5" HDDs have ~6 years on the SMART clock, but have no bad sectors and the 2.5" one reports 1½ years of usage and has 1 bad sector. Since the caching has hit rates of >90%; the HDD, do no perform that much work anymore and they share that workload more or less equally.

I need some good reasons to spend $400

---

### Post by Tadaen_Sylvermane on 2019-02-28
One reason could be the electric bill. That old machine probably draws twice as much juice?

Fans and screens can be replaced. Don't need a total system upgrade for those.

For me, a computer is to old when it can't do its job efficiently anymore. If it is causing problems then its upgrade time. No rush if its not.

---

### Post by bitsnpcs on 2019-02-28
Hello lammert-nijhof,

Some consideration to think of could be -
if your computer expired unexpectedly and you had to go to the cybercafe for nn hours each night to complete a project ?
It would not be relaxing to be at the cybercafe for 8 hours each night, do their chairs have sufficient back support, is its temperature exactly how you like, are there distraction there ?
There is the risk to your safety traveling home afterwards at 2am, you would have additional costs of possibly travel, and also the price to rent the space.
If you walk or run there, there is still a travel costs as you need to check out the runners, as they will wear out quicker with the extra miles each day, and factor in the extra food you will need to eat to cover the nutition burned off during the run. Extra food means extra wc, this involves hygiene products, and the costs of water used.
In a very short time it will be more than the cost of the new machine. 

So it is therefore logical & sensible to buy the Ryzen, as you will be saving money.

---

### Post by QIII on 2019-02-28
> as you will be saving money.

Only notionally saving money in a fantasy fictional world where an outlandish series of events leads to your being accosted on a subway on your way home from a cyber cafe at 2 am in your running shoes, with your bar of soap and nutrient bars in your backpack.

My opinion:  If it's working for what you need it to do, don't bother spending your money.  New or old, electronics can give up the blue smoke at any time.  New hardware is not always a guarantee of long service.  Having a Maserati does you no good if all you do is drive your kids to school and go to the supermarket weekly.  If an old beater will do that much, spend the money on something else you like -- or save it.

---

### Post by mastablasta on 2019-03-01
i have a Athlon 3200 (single core) with 4GB ram, probably similar platform but older. i had to replace GPU, PSU and hard drive (they failed). other than that it still works and does the job. it is even faster now that i added Linux next to windows XP (which is still used for old games). at that time when i  bought it i was just after something cheap and later i planned to replace the CPU with phenom, but by the time i got the money to make the change, phenoms were no longer sold. so i got stuck with this one. i planned to replace it with something new, as i expected it to die out soon, but it just wont' do that. and since it all works for my needs, i continue to use it.

also electricity is relatively cheap. at least here, the biggest costs on electricity bill is "output power" and taxes. i think that when people start saving and using more energy efficient stuff, electricity companies needed to find other source of revenue so they increased price on other things. so now if you buy a device that uses 100 W less, you need about 15 years before the purchase pays off. and as we all know it due to unsustainable economies that is producing appliances that lasts no more than 5 year (most only 2 or 3), who would invest into a power saving device? this really is ridiculous.

---

### Post by lammert-nijhof on 2019-03-01
> **mastablasta said:**
>  at that time when i  bought it i was just after something cheap and later i planned to replace the CPU with phenom, but by the time i got the money to make the change, phenoms were no longer sold. 

I replaced my original 3-core Phenom X3 8600b (2.3 GHz), which is an AM2 processor with an AM3 Phenom II, which I bought in 2017 for $35 on Ebay. My motherboard was AM2+ so it supported AM2 processors and many of the first AM3 processors.

Electricity is very expensive in the Dominican Republic, my energy costs (electricity + cooking gas) are the same or more than in Europe (electricity + natural gas for cooking and heating). A Ryzen 3 2200G has a TDP of 65 Watt and my Phenom II has 95 Watt, so that will help somewhat and I can drop the video card, that uses somewhere between 30-50 watt. Of course that power gain of 60-80 Watt only occurs at high loads, most of the time it will be significantly less. To reduce electricity costs, I suspend the display after 10 minutes and  the PC after ½ hour. Ubuntu Mate resumes a suspended PC within a few seconds.

However Lower electricity costs; Let save on average 40 Watt for 12 Hours equals 480 Wh/day and 14.4 KWh per month at RD$ 11/kwh = RD$ 160 or US$3. I just can buy one local beer (700ml) in a pub for that. Airco is my problem not PCs.

Maybe, I should see it as hobby and hobbies cost money for no good reasons.

---

### Post by lammert-nijhof on 2019-03-01
> **bitsnpcs said:**
> Hello lammert-nijhof,
if your computer expired unexpectedly and you had to go to the cybercafe for nn hours each night to complete a project ?

I'm retired, so I don't have any serious projects, only hobby projects. Every other summer my wife and I often go to family in Europe for say 2 months and for that purpose I bought last time in Europe a 2nd hand 2011 laptop. That laptop has 85% of the performance of my desktop and it also has 8 GB and a 1 TB SSHD. That laptop has exactly the same content as my desktop. At home I rsync my desktop data weekly to the laptop SSHD. In case of a failing desktop, I could connect the 22" display to my laptop and continue my hobby projects on my laptop. 

That laptop could take an i7 processor and 16 GB of memory, but that i7 would be ~$100+ and the memory ~$80. The i7 would increase performance with 50-100% dependent on the model, equal to the Ryzen 3 2200G (90%), but it would be the definitive end of any upgrade possibilities. Besides:
[LIST]
[*] I experienced that laptops have a shorter life than desktops, if used as daily driver and
[*]I would need at least an additional USB-3.0 3.5" enclosure to keep backups on the same level.
[/LIST]
A new Ryzen 3 2200G desktop would cost me twice that price, but it has endless step-by-step upgrade possibilities for the many years ahead, if needed through Ebay after 2021. 
So I have rational reasons not to upgrade the laptop instead, but not yet any good reason to upgrade my desktop.

Maybe, I should see it as hobby and hobbies cost money for no good reasons.

---

### Post by poorguy on 2019-03-01
> **lammert-nijhof said:**
>  
The 2008 HP could die of old age at any moment, so that is the only objective reason, I have to upgrade. The only complaints are:

[LIST]
[*]This week the small fan on the video card stopped working, so that card runs now up to 90°C (max < 127°C). 
[*]The monitor started to show burn-in signs last year. 
[*]The case fan starts to get noisy occasionally. 
[/LIST]

Wait until the HP dies of old age and then look for a replacement.

Replace the case fan cheap repair.

When the fan on one of my graphics card failed I bought a fan that fit on top of the heat sink and used small zip ties to secure the replacement fan to it.
Yes it is an unorthodox method although works very well and you may have to buy a fan header connector to molex connector cable.

Live with the monitor if it's usable.

---

### Post by lammert-nijhof on 2019-03-03
I'm not really worried about the fan situation, since the case is open on the site next to the wall. The video card runs between 70- 90°C but it is supposed to allow up to 127°C according to the lm-sensors read-out. The case fan did run fine last month, but does not do much anymore, since the case is open. The other temps are very good, all between 40-66°C.

For a new PC I have a nice midi tower, I can buy a 600W Chinese power supply here for $12 and I will not even use 200 Watt, the motherboard is $80, the 2200G $95 and the memory is getting cheaper each month. I re-use my disks without any change or re-installation.

---

### Post by poorguy on 2019-03-03
> **lammert-nijhof said:**
> I can buy a 600W Chinese power supply here for $12 and I will not even use 200 Watt,
Perhaps I'm out of line and if so the tell me.

I would be very leery of a 600W power supply Chinese or any Country for $12.00 as I doubt it's capable of 600W and I've seen to many failed cheap power supplies take out motherboards.

---

### Post by mastablasta on 2019-03-04
> **poorguy said:**
> Perhaps I'm out of line and if so the tell me.

I would be very leery of a 600W power supply Chinese or any Country for $12.00 as I doubt it's capable of 600W and I've seen to many failed cheap power supplies take out motherboards.

min 80 bronze PSU is the way to go otherwise you are just wasting power and heating it all up for no good reason (unless you need some extra warmth for when it's raining outside :) )


have you looked into mini ITX boards and boxes? they are also easy to upgrade and use less power (usually). though it costs at bit more at the start. since you are calculating it all, maybe it might be worth having a look.

---

### Post by lammert-nijhof on 2019-03-05
I use the same power supply in an old Pentium 4 PC without any problems. And I was wrong about the price $12 is for the 500 Watt version, 600 Watt is $17 :). I'm buying it in the largest local computer shop and they can't afford to sell complete garbage. I would never use such a power supply with any gaming video card, but I will only use it with the integrated video of a 65 Watt 2200G, 3 HDDs, 1 SSD, motherboard, one case fan and 2 x 8 GB DDR4, say 150 Watt full load. 

In my current system I need 220 Watt from a 2008, 300 Watt Dell power supply, that seems riskier than 150 Watt from a new 500 Watt Xtech power supply..

---

### Post by mastablasta on 2019-03-06
the problem of poor power supply is that it might use 600 W and could give power output of 300 W. while the good ones will give 550 W or so.

[https://en.wikipedia.org/wiki/80_Plus](https://en.wikipedia.org/wiki/80_Plus)

---

### Post by lammert-nijhof on 2019-03-06
As an electrical engineer I can tell you that the difference of 300 watt has to go somewhere. Energy does not just disappear, the difference between input power and output power must be evaporated as heat. Since that same Xtech power supply used with my Pentium 4 has not turned into a 300 Watt radiant heater, I do not worry about that. The real problem is that such a power supply, if used to say 80% of its specified limit, could suddenly die, due to overloading/overheating of one of its weaker components and the effects of such sudden disruption could kill the motherboard. With a max load of 150 Watt being 25% of the specified power, it will not overload any of its components, so I do not really worry about it. 

It is like with cars. I once had an old Fiat Ritmo, a car with a bad name with respect to reliability. I used that 8 year old car with a 1100cc engine to drive >1000 km to Spain (35°C/95°F in summer) and to avoid overheating I limited my speed to 110 km/h. I never did drive the in France allowed speed of 130 km/h nor the car's top speed of 150 km/h. The car survived the 2 x 1000 km, because it never exceeded 60% of its max power.

A 550W power supply from Corsair through Newegg would cost me $60 and another $23 in transport and sales tax. Newegg has cheaper power supplies for $30, but from an unknown brand too. For the price difference between Corsair and Xtech power supplies I could almost afford a second motherboard. I take my chances with one of the local 600 Watt ($17) or 500 Watt ($12) Xtech power supplies.

---

### Post by lammert-nijhof on 2019-03-06
Thanks to everybody for the discussion. I'm sure now, there are no rational reasons to upgrade or replace my PC, but I will do so to celebrate my birthday in May.  

I buy a B450 motherboard in March with at least 1 NVME place and a VGA connector for my old 22" monitor. In April I will buy the Ryzen 3 2200G almost twice the speed of my Phenom II and in May I will buy 2 x 8 GB of DDR4 (3200 MHz), hoping prices will have dropped somewhat more. I already have a nice classical case, I'll pickup a Xtech power supply and move my 3 HDDs and 1 SSD to the new system.

---

### Post by mastablasta on 2019-03-07
> **lammert-nijhof said:**
> Thanks to everybody for the discussion. I'm sure now, there are no rational reasons to upgrade or replace my PC, but I will do so to celebrate my birthday in May.  


seems like a good reason to me. 

enjoy and be sure to report back on how it went (user experience, out of the box or not...) once you get all the specs and hardware  together.

---

