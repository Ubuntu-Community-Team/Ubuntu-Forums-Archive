---
title: "Excited / confused: building my first box"
date: 2008-07-05
forum: The Cafe
---

### Post by Erdaron on 2008-07-05
After a long time, I've finally decided to put together my new computer instead of buy a manufactured unit. I'm pretty excited, but also feeling a bit overwhelmed by all the specs I have to match to make this work.

My specs so far:
CPU: Intel Celeron 440 (2.0 GHz, single-core - it beats Sempron in straight up number crunching, and has the lowest thermal rating, 35W, of anything, both of which are important to me. Also, I'm not looking to overclock.)
RAM: 2 gig (I'm not greedy)
OS: Windows XP Pro x64 / Ubuntu 8.04 64bit
Video: something nVidia, with around 256 MB, probably 7000-series

I have some questions, though, and would really appreciate some help.

Other than newegg, where do people shop for computer hardware? I've also tried buy.com, computershopper, cdw, clubit, and geek.com, and they mostly pale in comparison to newegg, in terms of selection and ease of navigation. In particular, I'm looking for motherboards.

Is there a dramatic difference between SATA 3.0 Gb/s and SATA 1.5 Gb/s? Can I stick a 3.0 Gb/s device into a 1.5 Gb/s board and still have it work (even if not at full capacity).

And last question, are all LGA 775 motherboards and all LGA 775 CPUs compatible as long as FSB speeds are the same, or do I need to make sure the CPUs listed for the motherboard match what I have? It seems vast majority of motherboards are for Celeron D, and selection of Celeron motherboards is rather thin.

Thanks!

---

### Post by gn2 on 2008-07-05
> **Erdaron said:**
> 
CPU: Intel Celeron 440 (2.0 GHz, single-core - it beats Sempron in straight up number crunching, and has the lowest thermal rating, 35W, of anything,

Are you sure abot that TDP claim? [http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=65](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=65)

> **Erdaron said:**
> 

Is there a dramatic difference between SATA 3.0 Gb/s and SATA 1.5 Gb/s? Can I stick a 3.0 Gb/s device into a 1.5 Gb/s board and still have it work 

Any new hardware bought should be 3.0 but a 3.0 SATA2 drive is usually backwards compatible with a 1.5 board.
You would need to run a benchmark test to notice any difference.

> **Erdaron said:**
> 
And last question, are all LGA 775 motherboards and all LGA 775 CPUs compatible as long as FSB speeds are the same, or do I need to make sure the CPUs listed for the motherboard match what I have? It seems vast majority of motherboards are for Celeron D, and selection of Celeron motherboards is rather thin.

Thanks!

Socket 775 CPU's and boards should be chosen extremely carefully, you absolutely must confirm that the exact CPU will work in the board as supplied.
This can be very tricky as there are sometimes different versions of the same CPU e.g. there are three Q6600's not all of which work in all Q6600 compatible boards.
Also the board may require a BIOS upgrade to work with a certain CPU, if you don't have a CPU that will work, you can't do the BIOS upgrade. Catch 22.

---

### Post by Erdaron on 2008-07-06
> **gn2 said:**
> Are you sure abot that TDP claim? [http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=65](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=65)
Well, not anymore I'm not. I somehow missed the X2 family on my first search. Thank you for confusing me by offering more choices :D. Although I suppose this dual-core would smoke Celeron 440 in number-crunching, it even has more L2 cache. (Off to look up X2 vs Celeron reviews...)


> Any new hardware bought should be 3.0 but a 3.0 SATA2 drive is usually backwards compatible with a 1.5 board.
You would need to run a benchmark test to notice any difference.
Alright, that's good news!


> Socket 775 CPU's and boards should be chosen extremely carefully, you absolutely must confirm that the exact CPU will work in the board as supplied.
This can be very tricky as there are sometimes different versions of the same CPU e.g. there are three Q6600's not all of which work in all Q6600 compatible boards.
Also the board may require a BIOS upgrade to work with a certain CPU, if you don't have a CPU that will work, you can't do the BIOS upgrade. Catch 22.
So it basically falls to picking the right chipset, am I correct? So I should go to chip manufacturers and look at the chip compatibility lists, such as [this one from Intel]("http://processormatch.intel.com/COMPDB/SearchResult.aspx?ProcNbr=440")?

---

### Post by Mateo on 2008-07-06
I'm building my first CPU too!!  Very exciting!  I'm definitely going to make mine different from anything that's out there.

I suggest doing like me and get one of the new Asus mobos that has the instant-on OS on the board.

---

### Post by gn2 on 2008-07-06
> **Erdaron said:**
> 
So it basically falls to picking the right chipset, am I correct? 

Yes and no.

Yes you need a chipset that will play nicely with your CPU.

No, just look for a motherboard that has all the features you require and look up it's compatible CPU list to make sure that you get a CPU that's listed.

Be careful when buying AMD CPU's, the one I linked to is an Energy Efficient model, not all X2's are so cool.
You need to make sure you get the correct model number, ADD3800IAA5CU or ADD3800CUBOX

[**This**]("http://products.amd.com/en-us/DesktopCPUFilter.aspx") should help you choose, there are six AMD CPU's with a TDP of 35w

---

### Post by mips on 2008-07-06
Friends don't let friends buy Celerons or Semprons.

---

### Post by Canis familiaris on 2008-07-06
I recently built a box, pretty cheap. Here is the configuration:

Processor: AMD Athlon64 X2 4400+ 
- Really a great performer. Also very cheap and has great value for money. I would suggest for you the BE series of Athlon X2s. they are bit costlier but has much lesser TDP. Also Athlon X2s are better buys than the Pentium Dual Cores because they are available at higher speeds at the same price.
Also installation of Heatsinks in AMD processors is much easier than of Intel processors.

Motherboard: ASUS M2A-VM
- Does the job well. Even has options for Overlclocking/Overvolting. So good enough for me. However has (Integrated) ATi Radeon X1250. Bundled with motherboard and good performer.  But I think you should prefer a motherboard with integrated nVidia.

RAM: 2 X Corsair Value 1GB Ram @ 666Mhz (Latency 5-5-5-15)
- Has latency on the higher side (lower is better) but is OK and does the job well. Always look at clock speeds and latency in addition to the density.

Hard Disk: Western Digital Caviar SE16 2500AAKS
- Go with the hard disk which has highest GB/price. Also do not go below 7200rpm(I don't think below 7200rpm is available anyways). Also go for buffer density of 16MB or more. It really makes quite a difference.

Optical Drive: Samsung DVD-Writer
- Buy any DVD writer. Preferably a SATA based because it involves thinner cables and hence does not hinder airflow as much as an IDE based.

Power Supply: CoolerMaster 390W
- Buy a good power supply. It will be really beneficial on a longer run.

---

### Post by ghindo on 2008-07-06
I don't think you can (legally) obtain Windows XP anymore.

And you can do *much* better than a Celeron.

---

### Post by mips on 2008-07-06
> **ghindo said:**
> I don't think you can (legally) obtain Windows XP anymore.


[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=368&name=Operating-Systems](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=368&name=Operating-Systems)

---

### Post by Canis familiaris on 2008-07-06
@OP: Do not buy XP 64-bit. If you really want to persist with XP use XP 32bit. If you really want 64bit, use Vista x64.
Anyway that Ubuntu 64 would outperform each of these.

---

### Post by Crosbie on 2008-07-06
You'll find [this page]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia") useful in choosing your video card.  I went for the 7600GS, and it works well.

---

### Post by regomodo on 2008-07-06
`

---

### Post by Erdaron on 2008-07-06
About buying Windows - I ordered a copy on June 30th, and I already have it. I knew I wanted it, and I knew it'll be harder to get after this date, so I got it ahead of all the hardware. If I didn't want to run some work-related windows-only software (mostly CAD stuff) I probably wouldn't install windows at all.

About 64bit - I thought you could run 32-bit stuff just as well, it's just that you can also run 64-bit applications and drivers natively, which is good?

Why not a Celeron? I mean, I understand it's limited performance, but also at a limited price, which I can accept. And my laptop runs off a 1.5 GHz Celeron, and it's very smooth with 1.25 GB of RAM.

Also, I've noticed that some hardware is specified as 32-bit or 64-bit (some graphics cards). Does this make a difference for the system, or is this just the device's internal bit-width?

---

### Post by mips on 2008-07-06
> **Erdaron said:**
> 
Why not a Celeron? I mean, I understand it's limited performance, but also at a limited price, which I can accept. And my laptop runs off a 1.5 GHz Celeron, and it's very smooth with 1.25 GB of RAM.


My laptop has the exact same specs and I think it is dog slow. I promised myself i will never ever buy a celeron again in my life.

---

### Post by Canis familiaris on 2008-07-06
> **Erdaron said:**
> 
Why not a Celeron? I mean, I understand it's limited performance, but also at a limited price, which I can accept. And my laptop runs off a 1.5 GHz Celeron, and it's very smooth with 1.25 GB of RAM.

The money saved with a Celeron is not worth it even the latest Core 2 based Celerons. The Pentium Dual Cores and the Athlon X2s outperform them by a mile with little increase in price.
I think for lower budgets Athlon X2s are the best.

---

### Post by tad1073 on 2008-07-06
[FONT="Verdana"]I am wanting to build my own computer also, but after reading this thread, I am unsure about the mobo/cpu compatability.

Here is what I have so far:[/FONT]

[FONT="Verdana"]```
Western Digital VelociRaptor WD3000GLFS 300GB 10000 RPM SATA 3.0Gb/s Hard Drive - OEM
Model #:WD3000GLFS
Item #:N82E16822136260
Return Policy:Limited 30-Day Return Policy
In Stock
Note (Add)	$299.99	 	$299.99
 	
Update		GIGABYTE GA-MA790FX-DS5 AM2+/AM2 AMD 790FX ATX Ultra Durable II AMD Motherboard - Retail
Model #:GA-MA790FX-DS5
Item #:N82E16813128074
Return Policy:Limited Non-Refundable 30-Day Return Policy
Out Of Stock
   Auto-Notify
Note (Add)	$189.99	 	$189.99
 	
Update		AMD Phenom 9850 BLACK EDITION 2.5GHz Socket AM2+ 125W Quad-Core Processor Model HD985ZXAGHBOX - Retail
Model #:HD985ZXAGHBOX
Item #:N82E16819103249
Return Policy:Processors (CPUs) Return Policy
In Stock
Note (Add)	$243.00	 	$243.00
 	
Update		CORSAIR Dominator 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory Model TWIN2X2048-8500C5D - Retail
Model #:TWIN2X2048-8500C5D
Item #:N82E16820145043
Return Policy:Memory (Modules, USB) Return Policy
In Stock
Mail-in Rebate
Note (Add)	$109.00	-$20.00 Instant	$178.00
 	
Update		LITE-ON Black SATA Blu-ray DVD-ROM Drive Model DH-4O1S-08 - Retail
Model #:DH-4O1S-08
Item #:N82E16827106225
Return Policy:Standard Return Policy
In Stock
Note (Add)	$139.99	 	$139.99
 	
Update		Turtle Beach TBS-3300-01 7.1 Channels PCI Interface Montego DDL Sound Card - Retail
Model #:TBS-3300-01
Item #:N82E16829118109
Return Policy:Standard Return Policy[/FONT]
```

---

### Post by Zero Prime on 2008-07-06
To the above poster, I'm not sure about the AMD 790 chipset.  But if it makes you feel better I just ordered a mobo woth the AMD 780G chipset and read a lot of reviews before ordering.  One Linux review site tested the 780G and said it ran fantastic.  They compared it to Nvidia motherboards and the AMD board blew them away. The Gigabyte board you specified is one I believe was tested as well.  It out performed the 780G, but not by much.

---

### Post by logos34 on 2008-07-06
> **mips said:**
> Friends don't let friends buy Celerons or Semprons.

:lolflag:

Edit: and to echo what another guy said above, don't EVEN think about skimping on the power supply--it's actually your most important single component!

---

### Post by regomodo on 2008-07-06
`

---

### Post by HansKisaragi on 2008-07-06
> **tad1073 said:**
> [FONT="Verdana"]I am wanting to build my own computer also, but after reading this thread, I am unsure about the mobo/cpu compatability.

Here is what I have so far:[/FONT]

[FONT="Verdana"]```
Western Digital VelociRaptor WD3000GLFS 300GB 10000 RPM SATA 3.0Gb/s Hard Drive - OEM
Model #:WD3000GLFS
Item #:N82E16822136260
Return Policy:Limited 30-Day Return Policy
In Stock
Note (Add)	$299.99	 	$299.99
 	
Update		GIGABYTE GA-MA790FX-DS5 AM2+/AM2 AMD 790FX ATX Ultra Durable II AMD Motherboard - Retail
Model #:GA-MA790FX-DS5
Item #:N82E16813128074
Return Policy:Limited Non-Refundable 30-Day Return Policy
Out Of Stock
   Auto-Notify
Note (Add)	$189.99	 	$189.99
 	
Update		AMD Phenom 9850 BLACK EDITION 2.5GHz Socket AM2+ 125W Quad-Core Processor Model HD985ZXAGHBOX - Retail
Model #:HD985ZXAGHBOX
Item #:N82E16819103249
Return Policy:Processors (CPUs) Return Policy
In Stock
Note (Add)	$243.00	 	$243.00
 	
Update		CORSAIR Dominator 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory Model TWIN2X2048-8500C5D - Retail
Model #:TWIN2X2048-8500C5D
Item #:N82E16820145043
Return Policy:Memory (Modules, USB) Return Policy
In Stock
Mail-in Rebate
Note (Add)	$109.00	-$20.00 Instant	$178.00
 	
Update		LITE-ON Black SATA Blu-ray DVD-ROM Drive Model DH-4O1S-08 - Retail
Model #:DH-4O1S-08
Item #:N82E16827106225
Return Policy:Standard Return Policy
In Stock
Note (Add)	$139.99	 	$139.99
 	
Update		Turtle Beach TBS-3300-01 7.1 Channels PCI Interface Montego DDL Sound Card - Retail
Model #:TBS-3300-01
Item #:N82E16829118109
Return Policy:Standard Return Policy[/FONT]
```

Are you building a Windows gaming pc or a Linux pc? .. thats way overkill .. and some of those parts are a waste of money.

Take the hdd for example, you get 1 TB disc "sata3" thats like 50$ cheaper then that hdd.

And DONT get Crosiar Dominator, you can get 8 gb of Corsair XMS2 thats cheaper then those, and they are rock solid.

And buying a 7.1 card when you already have a perfectly integrate 7.1 card on the motherboard don't make sense.

---

### Post by vikramaditya on 2008-07-06
If gaming is not an issue, consider a nice "legacy" build.  Good buys can be found for doing a P4 build using yesteryear's mobo, DDR mem, EIDE drives, & old-timey AGP/PCI graphics.  Lots less chance of compatibility issues and still plenty fast with 'buntu.

---

### Post by tad1073 on 2008-07-06
> **Viiral said:**
> Are you building a Windows gaming pc or a Linux pc? .. thats way overkill .. and some of those parts are a waste of money.

Take the hdd for example, you get 1 TB disc "sata3" thats like 50$ cheaper then that hdd.

And DONT get Crosiar Dominator, you can get 8 gb of Corsair XMS2 thats cheaper then those, and they are rock solid.

And buying a 7.1 card when you already have a perfectly integrate 7.1 card on the motherboard don't make sense.

I am building a media pc and will be running Linux and maybe Windows XP. I have read too many bad reviews about Vista.

I want something that will run a 10,000 rpm, I am speed freak...

Thanks for the tip on the mem.

I guess I should read the spec's a little better. Knowing it has onboard audio I will drop the turle beach card.

---

### Post by tad1073 on 2008-07-06
Updated build wish list w/more components added.

```
mushkin 2GB 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Desktop Memory Model 991599 - Retail
Model #:991599
Item #:N82E16820146784
Return Policy:Standard Return Policy
In Stock
Note (Add)	$63.99	 	$63.99
 	
Update		Western Digital Caviar RE2 GP WD1000FYPS 1TB SATA 3.0Gb/s Hard Drive - OEM
Model #:WD1000FYPS
Item #:N82E16822136206
Return Policy:Limited 30-Day Return Policy
In Stock
Note (Add)	$239.99	 	$239.99
 	
Update		EVGA 01G-P3-N809-AR GeForce 8800GT AKIMBO 1GB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card - Retail
Model #:01G-P3-N809-AR
Item #:N82E16814130336
Return Policy:Limited 30-Day Return Policy
In Stock
Mail-in Rebate
Note (Add)	$239.99	-$10.00 Instant	$229.99
 	
Update		Thermaltake toughpower W0105RU 700W ATX12V / EPS12V Power Supply - Retail
Model #:W0105RU
Item #:N82E16817153035
Return Policy:Limited 30-Day Return Policy
In Stock
Note (Add)	$165.99	 	$165.99
 	
Update		Thermaltake SwordM VD5000BNA Black/ Silver Aluminum Extrusion ATX Full Tower Computer Case - Retail
Model #:VD5000BNA
Item #:N82E16811133049
Return Policy:Standard Return Policy
In Stock
Note (Add)	$499.99	 	$499.99
 	
Update		GIGABYTE GA-MA790FX-DS5 AM2+/AM2 AMD 790FX ATX Ultra Durable II AMD Motherboard - Retail
Model #:GA-MA790FX-DS5
Item #:N82E16813128074
Return Policy:Limited Non-Refundable 30-Day Return Policy
Out Of Stock
   Auto-Notify
Note (Add)	$189.99	 	$189.99
 	
Update		AMD Phenom 9850 BLACK EDITION 2.5GHz Socket AM2+ 125W Quad-Core Processor Model HD985ZXAGHBOX - Retail
Model #:HD985ZXAGHBOX
Item #:N82E16819103249
Return Policy:Processors (CPUs) Return Policy
In Stock
Note (Add)	$243.00	 	$243.00
 	
Update		LITE-ON Black SATA Blu-ray DVD-ROM Drive Model DH-4O1S-08 - Retail
Model #:DH-4O1S-08
Item #:N82E16827106225
Return Policy:Standard Return Policy
In Stock
Subtotal:	$1,772.93

```

---

### Post by gn2 on 2008-07-07
> **tad1073 said:**
> 
I want something that will run a 10,000 rpm, I am speed freak...


Just because it runs at 10,000 rpm doesn't guarantee that it will definitely have a significantly faster data transfer rate over a (significantly cheaper) 7200rpm drive.

[http://www.tomshardware.com/charts/3-5-hard-drive-charts/maximum-read-transfer-rate,666.html?p=2024%2C1824%2C1822%2C1823%2C1821%2C1825%2C1785%2C1801%2C1795%2C1800%2C1798%2C1797%2C1784%2C1774%2C1793%2C1772%2C1829%2C1776%2C1781%2C1778%2C1805%2C1782%2C1831%2C1769%2C1766%2C1832%2C1830%2C1783%2C1775%2C1807%2C1794%2C2028%2C1796%2C1808%2C1773%2C1771%2C1768%2C1777%2C1780%2C1770%2C1779%2C1833%2C1792%2C1828%2C1816%2C1839%2C1787%2C1814%2C1815%2C1791%2C1806%2C1802%2C1844%2C1811%2C1804%2C1847%2C1826%2C1765%2C1846%2C1803%2C1818%2C1790%2C1767%2C1819%2C1799%2C1841%2C1809%2C1817%2C1789%2C2022%2C1788%2C1786%2C1827%2C1838%2C1836%2C1835%2C1834%2C2023%2C1840%2C1820%2C1837%2C2021%2C1845%2C1842%2C1843%2C1812%2C1813%2C2029](http://www.tomshardware.com/charts/3-5-hard-drive-charts/maximum-read-transfer-rate,666.html?p=2024%2C1824%2C1822%2C1823%2C1821%2C1825%2C1785%2C1801%2C1795%2C1800%2C1798%2C1797%2C1784%2C1774%2C1793%2C1772%2C1829%2C1776%2C1781%2C1778%2C1805%2C1782%2C1831%2C1769%2C1766%2C1832%2C1830%2C1783%2C1775%2C1807%2C1794%2C2028%2C1796%2C1808%2C1773%2C1771%2C1768%2C1777%2C1780%2C1770%2C1779%2C1833%2C1792%2C1828%2C1816%2C1839%2C1787%2C1814%2C1815%2C1791%2C1806%2C1802%2C1844%2C1811%2C1804%2C1847%2C1826%2C1765%2C1846%2C1803%2C1818%2C1790%2C1767%2C1819%2C1799%2C1841%2C1809%2C1817%2C1789%2C2022%2C1788%2C1786%2C1827%2C1838%2C1836%2C1835%2C1834%2C2023%2C1840%2C1820%2C1837%2C2021%2C1845%2C1842%2C1843%2C1812%2C1813%2C2029)
[http://www.tomshardware.com/charts/3-5-hard-drive-charts/file-writing-performance,662.html?p=2021%2C2029%2C2024%2C1769%2C1782%2C1784%2C1765%2C1812%2C1803%2C1813%2C1789%2C1792%2C1827%2C1818%2C1809%2C2028%2C1816%2C1802%2C1839%2C1840%2C1770%2C1826%2C1772%2C1776%2C1790%2C1774%2C2022%2C1843%2C1846%2C1847%2C2023%2C1845%2C1844%2C1835%2C1830%2C1800%2C1832%2C1837%2C1799%2C1838%2C1836%2C1828%2C1829%2C1821%2C1817%2C1778%2C1823%2C1783%2C1825%2C1798%2C1791%2C1811%2C1807%2C1808%2C1806%2C1824%2C1766%2C1788%2C1819%2C1820%2C1797%2C1785%2C1781%2C1822%2C1805%2C1810%2C1815%2C1814%2C1804%2C1795%2C1775%2C1773%2C1777%2C1768%2C1786%2C1779%2C1771%2C1787%2C1780%2C1842%2C1793%2C1833%2C1831%2C1834%2C1841%2C1794%2C1796%2C%2C](http://www.tomshardware.com/charts/3-5-hard-drive-charts/file-writing-performance,662.html?p=2021%2C2029%2C2024%2C1769%2C1782%2C1784%2C1765%2C1812%2C1803%2C1813%2C1789%2C1792%2C1827%2C1818%2C1809%2C2028%2C1816%2C1802%2C1839%2C1840%2C1770%2C1826%2C1772%2C1776%2C1790%2C1774%2C2022%2C1843%2C1846%2C1847%2C2023%2C1845%2C1844%2C1835%2C1830%2C1800%2C1832%2C1837%2C1799%2C1838%2C1836%2C1828%2C1829%2C1821%2C1817%2C1778%2C1823%2C1783%2C1825%2C1798%2C1791%2C1811%2C1807%2C1808%2C1806%2C1824%2C1766%2C1788%2C1819%2C1820%2C1797%2C1785%2C1781%2C1822%2C1805%2C1810%2C1815%2C1814%2C1804%2C1795%2C1775%2C1773%2C1777%2C1768%2C1786%2C1779%2C1771%2C1787%2C1780%2C1842%2C1793%2C1833%2C1831%2C1834%2C1841%2C1794%2C1796%2C%2C)

As it's going to be a media centre, having as quiet a hard drive as possible is preferable.

---

### Post by Erdaron on 2008-07-09
This may sound like a silly question... is Athlon 64 X2 the same as Athlon X2?

I'm asking because newegg, which seems to have the most detailed product categorization, has separate CPU categories for Athlon 64 X and Athlon X2, but has no motherboard category for Athlon X2 (only Athlon 64 X2).

AMD website itself seems to use them interchangeably.

The only distinction I can figure out is that Athlon X2 are the energy-efficient models (also, their model numbers are xx50, whereas Athlon 64 X2 are xx00).

Is this right?

---

### Post by gn2 on 2008-07-09
> **Erdaron said:**
> This may sound like a silly question... is Athlon 64 X2 the same as Athlon X2?

Yes all Athlon X2 CPU's are 64-bit capable.

The way to tell the difference between them is the part number code.

[**This site**]("http://www.amdcompare.com/us-en/desktop/") is useful for checking what's what in the world of AMD CPU's.

---

### Post by Erdaron on 2008-07-13
This is my final build. I went with a Celeron, out of cheapness and positive personal experience with Celerons in the past. Are there any problems with this combination that I'm overlooking?

[Celeron 430 1.8 GHz CPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116039")

[Gigabyte GA-945GCM-S2C motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128076") (LGA 775 socket, 1066 / 800 MHz FSB, DDR2 667 240-pin RAM, SATA 3.0 Gb/s, PCIe x16)

[Patriot 2GB stick of RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820220296") (comes with a heat spreader)

[Excelstor 80GB SATA HDD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822210003") (I also have an IDE drive from an older computer that I can stick in this one)

[MSI GeForce 8400GS video card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127367") (it's fanless, but if it starts running too hot, I have a PCI fan I can put next to it)

[Rosewill R222-P-BK case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811147095")

[Antec EA380 power supply]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817371005") (I'm not running a whole lot of peripherals, and both CPU and HDD are low-energy - I'm actually going to buy it locally)

---

