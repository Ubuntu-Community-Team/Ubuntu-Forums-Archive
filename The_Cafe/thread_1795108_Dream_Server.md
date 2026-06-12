---
title: "Dream Server?"
date: 2011-07-02
forum: The Cafe
---

### Post by ClientAlive on 2011-07-02
Ok, I'll start this out with:

1X) SUPERMICRO H8QGi-F - motherboard - SWTX - Socket G34 - AMD SR5690/SR5670/SP5100 - Socket G34

4X) AMD Opteron 6100 Series 6176 SE 2.3GHz Socket G34 12-Core 45nm Processor

32x) 16 GB registered ddr3 1333

And just one of these: [http://www.physorg.com/news785.html](http://www.physorg.com/news785.html)

[http://colossalstorage.net/home_entangled.htm](http://colossalstorage.net/home_entangled.htm)

:D

---

### Post by Legendary_Bibo on 2011-07-02
> **ClientAlive said:**
> Ok, I'll start this out with:

1X) SUPERMICRO H8QGi-F - motherboard - SWTX - Socket G34 - AMD SR5690/SR5670/SP5100 - Socket G34

4X) AMD Opteron 6100 Series 6176 SE 2.3GHz Socket G34 12-Core 45nm Processor

32x) 16 GB registered ddr3 1333

And just one of these: [http://www.physorg.com/news785.html](http://www.physorg.com/news785.html)

[http://colossalstorage.net/home_entangled.htm](http://colossalstorage.net/home_entangled.htm)

:D

I would take one of [these](http://www-03.ibm.com/systems/bladecenter/hardware/servers/ps703704/specs.html)

---

### Post by ClientAlive on 2011-07-02
> **Legendary_Bibo said:**
> I would take one of [these](http://www-03.ibm.com/systems/bladecenter/hardware/servers/ps703704/specs.html)


Nice . . .

---

### Post by jerenept on 2011-07-02
Pure-FTPD, Apache, OpenSSH, Webmin, MPD (HTTP), Privoxy.

---

### Post by Dustin2128 on 2011-07-02
> **Legendary_Bibo said:**
> I would take one of [these]("http://www-03.ibm.com/systems/bladecenter/hardware/servers/ps703704/specs.html")
64Mb cache, mmmm....

---

### Post by ilovelinux33467 on 2011-07-02
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/15351-15351-3328412-241644-4222584-4231377.html]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/15351-15351-3328412-241644-4222584-4231377.html")

---

### Post by Bandit on 2011-07-02
Ubuntu LTS (any recent version) w/ PVM and MPI installed. A.k.a: Beowulf

[My current Box]("https://picasaweb.google.com/exodist2009/MyPCNov2009#5604882071418563618") with a CPU and RAM upgrade, plus the 12 kits below to make a [beowulf cluster server]("http://en.wikipedia.org/wiki/Beowulf_cluster"). 

1x Cisco Small Business SFE2000 Switch 10/100Mbps + 1000Mbps - $379.99
12x MSI 760GM-P33 AM3 AMD 760G Micro ATX AMD Motherboards - $54.99ea
13x AMD Phenom II X6 1100T Black Edition Thuban 3.3GHz, 3.7GHz Turbo 6 x 512KB L2 Cache 6MB L3 Cache Socket AM3 125W Six-Core Desktop Processors - $189ea.
14x G.SKILL Ripjaws Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory kits - $69.99kit
12x Antec EarthWatts Green EA-380D Green 380W Continuous power ATX12V v2.3 / EPS12V 80 PLUS BRONZE Certified Active PFC Power Supplys - $44.99ea 
Plus a big roll of Cat6 cable and connectors.

Build a plexiglass en-closer for the boards and power supplies. 
Set all board to netboot, plus install the PVM and MPI software. Enjoy.

Your looking at 12CPUs, 6 cores each for 72 cores total plus my machine which would have 6 cores also. 78cores total.
With 9MB of cache per CPU for combined (L2&3) 117MB!
96GB of RAM on the 12 boards plus 16 on main box for 112GBs of total RAM.

If you take my current box with est price of $600 and add the cost of upgrades and additional hardware. Your looking at $5617 before tax and shipping cost. Not bad for a small super computer. :D

---

