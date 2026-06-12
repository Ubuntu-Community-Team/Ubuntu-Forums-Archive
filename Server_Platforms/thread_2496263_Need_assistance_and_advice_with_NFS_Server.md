---
title: "Need assistance and advice with NFS Server"
date: 2024-03-20
forum: Server Platforms
---

### Post by sgt-mike on 2024-03-20
This is kind of Hardware based question based. As it deals with the configuration of the server I thought this would be the best place for this to land. 

Raid configuration will be ZFS Raidz in alignment with Raid 5 / 6 just have not decided on which yet.

The Computer is a Dell Optiplex 3010 (MT mid tower) so I am limited by the available PCIe slots (3 PCI-e 1x slots, and 1- PCI-e 16x slot) I know a OLD system. 

I have entertained the Idea of a PCI-e 1X card then use a 20 port expander, that met with the thought of flooding the PCI-e  1x bus. So I pretty much threw that thought out of my head as a folly and not worth considering.

I am considering the LSI SAS 9300-16i  16 Port controller for this system. As I understand this is not a expander,  
The system will boot from the MB Sata ports.  

What I have not settled on is the Drives I will use:
SAS , 2.5" SATA Enterprise, or Enterprise SSD's which will drive the form factor of the Cages I'll install in the 2x -5.25" bays.

I have been looking at the Icy Dock 8 bay ( SAS/SATA compatible Express cage MB038SP) which will support up to a 7mm height 2.5" drive this setup x 2 will afford me plenty of bays for expansion. My thoughts here are Enterprise class SATA SSD's.

OR If I go with SAS OR most SATA enterprise class mechanical hard drive the Icy Dock 8 bay cage is thrown out the system modification I'm looking hard at.  this will reduce that to a 4 Bay cage (again ICY Dock SAS / SATA) that is SAS / Sata capable. This observation is the fact that most of the Mechanical drives (SAS or Sata) I'm seeing are approx 19mm in height.I have not noticed any offering of a SATA or SAS enterprise Class drive in a 9.5mm or smaller form factor.

Advice on which drives technology / controllers / cages vendors - cost here is a major factor is what I'm seeking.

What I have not entertained is the use of large capacity 3.5" sata drives (8TB and higher)  because of the loss of advertised TB vs the actual available. Another reason is that I will max out at 5 drives 2 exposed in the 5.25" bays 3 hidden within the system vs all drives exposed via the 5.25" bays. I really like the Idea of accessing the drives without opening the case, preference mainly. My thought of the multiple 2.5" drives is that I would lose less to overhead (actual vs advertised capacity) than large capacity 3.5" drives I have NOT done the math on this so I could be VERY WRONG.

---

### Post by MAFoElffen on 2024-03-23
I use ZFS RAIDZ2. Can lose up to 2 array members at one time, and still go on.

Your first factor for consideration is what is your priority of storage? Reads or writes?

Second is your budgetary constraints. It all costs money.

There are many options for storage locations. If you want to access drives without having to open the case, I would consider a different case. I have an old Cooler Master Cosmos S case for my workstation. It has 10 x exposed 5-1/2" slots. For drive bays, I use one 4x3-1/2" drive hot-swap cage... that takes up 4 slots. Then I use two 6x2-1/2" drive cages. That gives me room for 4x3-1/2 drives, and 12 2-1/2 drives... that can all be accessed without opening the case.

I have 12 fans in that case to cool the drives, CPU and GPU. That is important when you start adding many drives.

If your main focus is for being a media server, then a set of large HDD's is fine. All it will do most of the time is just reads. 

I have used many SAS drives in the past. They run at 10K RPM, are fast and dependable. I have personally never had one fail. But they cost a lot. You can cut down your costs by using enterprise factory re-certified drives. It's hard to find very large SAS drives, size-wise. SAS controllers will support both SAS and SATA HDD's. SAS drives rated at the same speed as SATA will be faster, as there are more data paths.

SSD drives are fast and dependable. Their cost has dropped dramatically for 8TB sized SSD drives and smaller. It will drop more as the above 20T ssd's become more common.

NVMe is just fast (Big Period). It is more and more common to find NVMe at 4TB and lower.

You can get creative with ow to add controllers and data paths. A good PCIe x16 lane 8 port SAS controller is 12Gbs and supports 128 drives. But if you never plan to use SAS drives, a good SATA HBA will do for HHD and SSD, for a lot cheaper. PCie x1 M.2 cards with an M.2 to SATA3 adapter will support 6 SATA drives...

The next point of bottleneck contention lies with the motherboard's PCIe bus generation and the speed of it. You didn't say what your's was (Brand and model) , nor the Gen of.

I could go on for pages... Even write your a book on it. Because you have not set any boundaries or limits of scope. Maybe you should limit your scope a bit to get this more focused and directed.

---

### Post by MAFoElffen on 2024-03-23
Just just saw the Dell Optiplex 3010 MT as you base. My condolences.

Remember where I said your bottleneck would be the Gen # speed of your PCIe lanes?

First invest in another used motherboard on EBay and go from there...

That board is PCIe Gen 2. That means your max speed would be around 500 MB/s for PCIe x1... 
```

This is the theoricial maximum PCIe speeds by both PCIe generation and number of lanes, but note that due to system overhead and other hardware characteristics, real word numbers will be about 15% lower, and not exceed the rated speeds of the storage device itself.

PCIe Revision   x1 Lane    x2 Lane    x4 Lane    x8 Lane    x16 Lane
=============   ========   ========   ========   ========   ========
1.0/1.1         250 MB/s   500 MB/s   1 GB/s     2 GB/s     4 GB/s
2.0/2.1         500 MB/s   1 GB/s     2 GB/s     4 GB/s     8 GB/s
3.0/3.1         1 GB/s     2 GB/s     4 GB/s     8 GB/s     16 GB/s
4.0/4.1         2 GB/s     4 GB/s     8 GB/s     16GB/s     32 GB/s
5.0             4 GB/s     8 GB/s     16 GB/s    32 GB/s    64GB/s

```
Even your PCIe x16 is maxed out at 6.8 GB/s (max - 15%). But that is sort of a misnomer. That board has an H61 chipset ([https://ark.intel.com/content/www/us/en/ark/products/52806/intel-h61-express-chipset.html](https://ark.intel.com/content/www/us/en/ark/products/52806/intel-h61-express-chipset.html)). That chipset supports PCIe Gen 2.0 and a max of 6 lanes (so x1, x2, & x4 slots). But then again, that Dell MB does have what they say is a PCIe x16 slot. It only supports 4 SATA ports, which that is why that board only has 4 SATA ports.

Your bus will be saturated.

It is what it is. I think for a NAS, you should invest in a MB of at least PCIe Gen 3 for s starting foundation... Then you could think about many drives, and not worry as much about the I/O throughput.

---

### Post by sgt-mike on 2024-03-24
> **MAFoElffen said:**
> Just just saw the Dell Optiplex 3010 MT as you base. My condolences.

Remember where I said your bottleneck would be the Gen # speed of your PCIe lanes?

First invest in another used motherboard on EBay and go from there...

That board is PCIe Gen 2. That means your max speed would be around 500 MB/s for PCIe x1... 
```

This is the theoricial maximum PCIe speeds by both PCIe generation and number of lanes, but note that due to system overhead and other hardware characteristics, real word numbers will be about 15% lower, and not exceed the rated speeds of the storage device itself.

PCIe Revision   x1 Lane    x2 Lane    x4 Lane    x8 Lane    x16 Lane
=============   ========   ========   ========   ========   ========
1.0/1.1         250 MB/s   500 MB/s   1 GB/s     2 GB/s     4 GB/s
2.0/2.1         500 MB/s   1 GB/s     2 GB/s     4 GB/s     8 GB/s
3.0/3.1         1 GB/s     2 GB/s     4 GB/s     8 GB/s     16 GB/s
4.0/4.1         2 GB/s     4 GB/s     8 GB/s     16GB/s     32 GB/s
5.0             4 GB/s     8 GB/s     16 GB/s    32 GB/s    64GB/s

```
Even your PCIe x16 is maxed out at 6.8 GB/s (max - 15%). But that is sort of a misnomer. That board has an H61 chipset ([https://ark.intel.com/content/www/us/en/ark/products/52806/intel-h61-express-chipset.html](https://ark.intel.com/content/www/us/en/ark/products/52806/intel-h61-express-chipset.html)). That chipset supports PCIe Gen 2.0 and a max of 6 lanes (so x1, x2, & x4 slots). But then again, that Dell MB does have what they say is a PCIe x16 slot. It only supports 4 SATA ports, which that is why that board only has 4 SATA ports.

Your bus will be saturated.

It is what it is. I think for a NAS, you should invest in a MB of at least PCIe Gen 3 for s starting foundation... Then you could think about many drives, and not worry as much about the I/O throughput.

Looking over your post and a bit of searching most of the MB's I'm seeing are using that same chipset H61.

The Mainboard I'll be pulling out of that case is a Mini-ATX. 

Now if I go to the 4th Gen Intel processor and ditch the I5 3rd Gen processor with the Optiplex board, and go to the I7-4790K there is what I'm seeing two real good possible MB both mini-ATX .

1st Option is the MSI B45M-E45 which I'm running one of those on my Windows Box for my CNC. (which prior to setting it upfor the CnC I had Ubuntu desktop on it ran like a top)
```

CPU
Support
&#9632; 4th Generation Intel® Core&#8482; i7 / Core&#8482; i5 / Core&#8482; i3 / Pentium® /Celeron® processors for LGA 1150 socket
Chipset
&#9632; Intel® B85 Express Chipset
Memory Support
&#9632; 4x DDR3 memory slots supporting up to 32GB
&#9632; Supports DDR3 1600/ 1333/ 1066 MHz
&#9632; Dual channel memory architecture
&#9632; Supports non-ECC, un-buffered memory
&#9632; Supports Intel® Extreme Memory Profile (XMP)
Expansion Slots
&#9632; 1x PCIe 3.0 x16 slot
&#9632; 2x PCIe 2.0 x1 slots
&#9632; 1x PCI slot
Onboard Graphics
&#9632; 1x HDMI port, supporting the maximum resolution of 4096x2160@24Hz, 24bpp/ 2560x1600@60Hz, 24bpp/ 1920x1080@60Hz, 36bpp
&#9632; 1x VGA port, supporting a maximum resolution of 1920x1200 @ 60Hz
&#9632; 1x DVI-D port, supporting a maximum resolution of 1920x1200 @ 60Hz
Storage
&#9632; Intel® B85 Express Chipset
- 4x SATA 6Gb/s ports (SATA1~4)
- 2x SATA 3Gb/s ports (SATA5~6)
- Supports Intel® Rapid Start Technology, Intel® Smart Connect Technology*
* Supports Intel Core processors on Windows 7 and Windows 8.
USB
&#9632; Intel B85 Express Chipset - 4x USB 3.0 ports (2 ports on the back panel, 2 ports available through the internal USB 3.0 connector)
- 8x USB 2.0 ports (4 ports on the back panel, 4 ports available through the internal USB connectors)
Audio
&#9632; Realtek® ALC887 Codec - 7.1-Channel High Definition Audio
LAN
&#9632; 1x Realtek® 8111G Gigabit LAN controller
Back Panel Connectors
&#9632; 1x PS/2 keyboard port
&#9632; 1x PS/2 mouse port
&#9632; 4x USB 2.0 ports
&#9632; 1x HDMI port
&#9632; 2x USB 3.0 ports
&#9632; 1x VGA port
&#9632; 1x DVI-D port
&#9632; 1x LAN (RJ45) port
&#9632; 3x audio jacks
Mainboard connections
&#9632; 1x 24-pin ATX main power connector
&#9632; 1x 4-pin ATX 12V power connector
&#9632; 4x SATA 6Gb/s connectors
&#9632; 2x SATA 3Gb/s connectors
&#9632; 2x USB 2.0 connectors (supports additional 4 USB 2.0 ports)
&#9632; 1x USB 3.0 connector (supports additional 2 USB 3.0 ports)
&#9632; 1x 4-pin CPU fan connector
&#9632; 1x 4-pin system fan connector
&#9632; 1x 3-pin system fan connector
&#9632; 1x Clear CMOS jumper
&#9632; 1x Front panel audio connector
&#9632; 2x System panel connectors
&#9632; 1x TPM module connector
&#9632; 1x Serial port connector
&#9632; 1x Parallel port connector
&#9632; 1x Chassis Intrusion connector
I/O Controller
&#9632; NUVOTON NCT6779 Controller Chip
Hardware Monitor
&#9632; CPU/System temperature detection
&#9632; CPU/System fan speed detection
&#9632; CPU/System fan speed control
BIOS
Features
&#9632; 1x 64 Mb flash
&#9632; UEFI AMI BIOS
&#9632; ACPI 5.0, PnP 1.0a, SM BIOS 2.7, DMI 2.0 
```

Or a Supermicro X10SLM-F 

```

Feature X10SLM-F 
PCH  
Intel C224 Exp 

PCI-E Slot 
1 PCI-E 3.0 x8 in x16,
1 PCI-E 3.0 x8,
1 PCI-E 2.0 x4 in x8

DIMM Support
Up to 32GB ECC UDIMM DDR3- 1600MHz

LAN CTRL
 Dual GbE LAN Ports 1xi210AT, 1xi217LM

COM 
One COM Port
One COM Header

SATA 
4 SATA 6.0Gbs
2 SATA 3.0Gbs

RAID    RAID 0/1/5/10 (See pages 2-37 and 2-38 for details)
USB Support
4 USB 3.0 Ports,
6 USB 2.0 Ports

IPMI
 IPMI 2.0 (X10SLM-F) 

```

Unless I'm missing something in the specs I'm preferring the supermicro board  what are your thoughts. What is causing me to kinda pick it over the MSI is the 2 PCI-E 3.0 slots versus one on the MSI. 
Thoughts & opinions please

---

### Post by sgt-mike on 2024-03-24
> **MAFoElffen said:**
> Just just saw the Dell Optiplex 3010 MT as you base. My condolences.

Remember where I said your bottleneck would be the Gen # speed of your PCIe lanes?

First invest in another used motherboard on EBay and go from there...

That board is PCIe Gen 2. That means your max speed would be around 500 MB/s for PCIe x1... 
```

This is the theoricial maximum PCIe speeds by both PCIe generation and number of lanes, but note that due to system overhead and other hardware characteristics, real word numbers will be about 15% lower, and not exceed the rated speeds of the storage device itself.

PCIe Revision   x1 Lane    x2 Lane    x4 Lane    x8 Lane    x16 Lane
=============   ========   ========   ========   ========   ========
1.0/1.1         250 MB/s   500 MB/s   1 GB/s     2 GB/s     4 GB/s
2.0/2.1         500 MB/s   1 GB/s     2 GB/s     4 GB/s     8 GB/s
3.0/3.1         1 GB/s     2 GB/s     4 GB/s     8 GB/s     16 GB/s
4.0/4.1         2 GB/s     4 GB/s     8 GB/s     16GB/s     32 GB/s
5.0             4 GB/s     8 GB/s     16 GB/s    32 GB/s    64GB/s

```
Even your PCIe x16 is maxed out at 6.8 GB/s (max - 15%). But that is sort of a misnomer. That board has an H61 chipset ([https://ark.intel.com/content/www/us/en/ark/products/52806/intel-h61-express-chipset.html](https://ark.intel.com/content/www/us/en/ark/products/52806/intel-h61-express-chipset.html)). That chipset supports PCIe Gen 2.0 and a max of 6 lanes (so x1, x2, & x4 slots). But then again, that Dell MB does have what they say is a PCIe x16 slot. It only supports 4 SATA ports, which that is why that board only has 4 SATA ports.

Your bus will be saturated.

It is what it is. I think for a NAS, you should invest in a MB of at least PCIe Gen 3 for s starting foundation... Then you could think about many drives, and not worry as much about the I/O throughput.

Looking over your post and a bit of searching most of the MB's I'm seeing are using that same chipset H61.

The Mainboard I'll be pulling out of that case is a Mini-ATX.  Correction Micro-ATX. 

Now if I go to the 4th Gen Intel processor and ditch the I5 3rd Gen processor with the Optiplex board, and go to the I7-4790K there is what I'm seeing two real good possible MB both mini-ATX .

1st Option is the MSI B45M-E45 which I'm running one of those on my Windows Box for my CNC. (which prior to setting it upfor the CnC I had Ubuntu desktop on it ran like a top)
```

CPU
Support
&#9632; 4th Generation Intel® Core&#8482; i7 / Core&#8482; i5 / Core&#8482; i3 / Pentium® /Celeron® processors for LGA 1150 socket
Chipset
&#9632; Intel® B85 Express Chipset
Memory Support
&#9632; 4x DDR3 memory slots supporting up to 32GB
&#9632; Supports DDR3 1600/ 1333/ 1066 MHz
&#9632; Dual channel memory architecture
&#9632; Supports non-ECC, un-buffered memory
&#9632; Supports Intel® Extreme Memory Profile (XMP)
Expansion Slots
&#9632; 1x PCIe 3.0 x16 slot
&#9632; 2x PCIe 2.0 x1 slots
&#9632; 1x PCI slot
Onboard Graphics
&#9632; 1x HDMI port, supporting the maximum resolution of 4096x2160@24Hz, 24bpp/ 2560x1600@60Hz, 24bpp/ 1920x1080@60Hz, 36bpp
&#9632; 1x VGA port, supporting a maximum resolution of 1920x1200 @ 60Hz
&#9632; 1x DVI-D port, supporting a maximum resolution of 1920x1200 @ 60Hz
Storage
&#9632; Intel® B85 Express Chipset
- 4x SATA 6Gb/s ports (SATA1~4)
- 2x SATA 3Gb/s ports (SATA5~6)
- Supports Intel® Rapid Start Technology, Intel® Smart Connect Technology*
* Supports Intel Core processors on Windows 7 and Windows 8.
USB
&#9632; Intel B85 Express Chipset - 4x USB 3.0 ports (2 ports on the back panel, 2 ports available through the internal USB 3.0 connector)
- 8x USB 2.0 ports (4 ports on the back panel, 4 ports available through the internal USB connectors)
Audio
&#9632; Realtek® ALC887 Codec - 7.1-Channel High Definition Audio
LAN
&#9632; 1x Realtek® 8111G Gigabit LAN controller
Back Panel Connectors
&#9632; 1x PS/2 keyboard port
&#9632; 1x PS/2 mouse port
&#9632; 4x USB 2.0 ports
&#9632; 1x HDMI port
&#9632; 2x USB 3.0 ports
&#9632; 1x VGA port
&#9632; 1x DVI-D port
&#9632; 1x LAN (RJ45) port
&#9632; 3x audio jacks
Mainboard connections
&#9632; 1x 24-pin ATX main power connector
&#9632; 1x 4-pin ATX 12V power connector
&#9632; 4x SATA 6Gb/s connectors
&#9632; 2x SATA 3Gb/s connectors
&#9632; 2x USB 2.0 connectors (supports additional 4 USB 2.0 ports)
&#9632; 1x USB 3.0 connector (supports additional 2 USB 3.0 ports)
&#9632; 1x 4-pin CPU fan connector
&#9632; 1x 4-pin system fan connector
&#9632; 1x 3-pin system fan connector
&#9632; 1x Clear CMOS jumper
&#9632; 1x Front panel audio connector
&#9632; 2x System panel connectors
&#9632; 1x TPM module connector
&#9632; 1x Serial port connector
&#9632; 1x Parallel port connector
&#9632; 1x Chassis Intrusion connector
I/O Controller
&#9632; NUVOTON NCT6779 Controller Chip
Hardware Monitor
&#9632; CPU/System temperature detection
&#9632; CPU/System fan speed detection
&#9632; CPU/System fan speed control
BIOS
Features
&#9632; 1x 64 Mb flash
&#9632; UEFI AMI BIOS
&#9632; ACPI 5.0, PnP 1.0a, SM BIOS 2.7, DMI 2.0 
```

Or a Supermicro X10SLM-F 

```

Feature X10SLM-F 
PCH  
Intel C224 Exp 

PCI-E Slot 
1 PCI-E 3.0 x8 in x16,
1 PCI-E 3.0 x8,
1 PCI-E 2.0 x4 in x8

DIMM Support
Up to 32GB ECC UDIMM DDR3- 1600MHz

LAN CTRL
 Dual GbE LAN Ports 1xi210AT, 1xi217LM

COM 
One COM Port
One COM Header

SATA 
4 SATA 6.0Gbs
2 SATA 3.0Gbs

RAID    RAID 0/1/5/10 (See pages 2-37 and 2-38 for details)
USB Support
4 USB 3.0 Ports,
6 USB 2.0 Ports

IPMI
 IPMI 2.0 (X10SLM-F) 

```

Unless I'm missing something in the specs I'm preferring the supermicro board  what are your thoughts. What is causing me to kinda pick ot over the MSI is the 2 PCI-E 3.0 slots versus one on the MSI. 
Thoughts & opinions please

kept looking at the Supermicro and it's chipset looks like the i7 4790K isn't supported. 
But the the Xeon e3 1200 v3 and the i3 core fourth gen are. Which in my opinion is a performance hit.

---

### Post by MAFoElffen on 2024-03-24
MSI & SuperMicro are both my go-to's.

But on a budget (low-cost), looking at what you can salvage from your old system to re-use, and getting yourself a good foundation...

Your choice of CPU I7-4790K is a good choice, and the integrated iGPU will save you money and slots.

Ditch the case. This one is $75: [https://www.ebay.com/itm/234813129991?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1i4UkiHmMSoiSBKPG5TP1CA76&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=234813129991&targetid=1529493989662&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1529493989662&abcId=9316496&merchantid=6296724&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQAylyDViGH5X7Sds1NwlXkguTODuWZq5XUHQ2o7VYhI86sjo9x380ohoCtXcQAvD_BwE](https://www.ebay.com/itm/234813129991?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1i4UkiHmMSoiSBKPG5TP1CA76&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=234813129991&targetid=1529493989662&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1529493989662&abcId=9316496&merchantid=6296724&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQAylyDViGH5X7Sds1NwlXkguTODuWZq5XUHQ2o7VYhI86sjo9x380ohoCtXcQAvD_BwE)
That is a full-tower for $75 with plenty of room for storage and whatever you what to throw at it. Has plenty of room to grow.

Motherboard for that CPU would be socket FCLGA1150:

First Choice would be this SuperMicro:
[https://www.ebay.com/itm/394548025962?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=394548025962&targetid=1529314447670&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1529314447670&abcId=9316496&merchantid=113290357&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA23QYTU7UazA8PMeYZajWgVYUgxuuW7dGOFiv4O8XNPlgl_lE2yHFxoC5y8QAvD_BwE](https://www.ebay.com/itm/394548025962?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=394548025962&targetid=1529314447670&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1529314447670&abcId=9316496&merchantid=113290357&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA23QYTU7UazA8PMeYZajWgVYUgxuuW7dGOFiv4O8XNPlgl_lE2yHFxoC5y8QAvD_BwE)
Spec's: [https://www.supermicro.com/en/products/motherboard/x10sae](https://www.supermicro.com/en/products/motherboard/x10sae)

Pro's has 8 SATA Ports... 
Con's has 2 PCI slots, which is hard to find useful cards for these days. The PCIe x1 slots are Gen 2.0.


Second choice would be this MSI:
[https://www.ebay.com/itm/255668410651?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1RVeWUyRaT52arVRjPm7woA10&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=255668410651&targetid=1585159290171&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20389486948&mkgroupid=154370925111&rlsatarget=pla-1585159290171&abcId=9316498&merchantid=561566805&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA0FYMRYJrlwrWUrWC7han7-Oigl9RiHwtoadJFUCcwCv6ecq7_-sxRoCR_YQAvD_BwE](https://www.ebay.com/itm/255668410651?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1RVeWUyRaT52arVRjPm7woA10&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=255668410651&targetid=1585159290171&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20389486948&mkgroupid=154370925111&rlsatarget=pla-1585159290171&abcId=9316498&merchantid=561566805&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA0FYMRYJrlwrWUrWC7han7-Oigl9RiHwtoadJFUCcwCv6ecq7_-sxRoCR_YQAvD_BwE)
Specs: [https://www.msi.com/Motherboard/B85-G43-GAMING/Specification](https://www.msi.com/Motherboard/B85-G43-GAMING/Specification)

That was the best board I could find used for what you are wanting to do. Is ATX, and will fit that case.

Con's. Has 3 PCI slots. the 2 Pcie x1 slots are gen 2.0

*** Now if you went with 5th Gen Intel i7-5970K for $30:
[https://www.ebay.com/itm/166470907642?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=166470907642&targetid=1531876731998&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1531876731998&abcId=9316496&merchantid=6296724&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA3i6wuqWZ6iiNlB5KC1ZMTJr-jNsFAO4J9f5E3G5AIA9jEnga4g8bRoCclMQAvD_BwE](https://www.ebay.com/itm/166470907642?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=166470907642&targetid=1531876731998&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1531876731998&abcId=9316496&merchantid=6296724&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA3i6wuqWZ6iiNlB5KC1ZMTJr-jNsFAO4J9f5E3G5AIA9jEnga4g8bRoCclMQAvD_BwE)

Then thing open up with that socket LGA-2011-v3 motherboard:
Also DDR3 but... supports up to 64GB RAM, and all the PCIe slots should all be gen 3 (mostly)....

This is the best choice I found:
SuperMicro:
[https://www.ebay.com/itm/295998742304?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1KAIGESFYSVCJFcNQvy3RQQ47&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=295998742304&targetid=1585159292571&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385105599&mkgroupid=150744488839&rlsatarget=pla-1585159292571&abcId=9316499&merchantid=5301995045&gad_source=4&gclid=CjwKCAjwnv-vBhBdEiwABCYQA8p5SDpILj1wXN2PsfZ1RZ_uMV3ra4UJcvAGM5EJSMMNOOU6DeI8kBoCpCgQAvD_BwE](https://www.ebay.com/itm/295998742304?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1KAIGESFYSVCJFcNQvy3RQQ47&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=295998742304&targetid=1585159292571&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385105599&mkgroupid=150744488839&rlsatarget=pla-1585159292571&abcId=9316499&merchantid=5301995045&gad_source=4&gclid=CjwKCAjwnv-vBhBdEiwABCYQA8p5SDpILj1wXN2PsfZ1RZ_uMV3ra4UJcvAGM5EJSMMNOOU6DeI8kBoCpCgQAvD_BwE)
Spec's: [https://www.thomas-krenn.com/en/wiki/Supermicro_X9SRL-F_Motherboard](https://www.thomas-krenn.com/en/wiki/Supermicro_X9SRL-F_Motherboard)
Pros:  2x PCI-E 3.0 x8 (in x16) slots, 2x PCI-E 3.0 x8 (in x8) slots, 2x PCI-E 3.0 x4 (in x8) slots, 1x PCI-E 2.0 x4 (in x8) slot. 64 GB non-ECC RAM. 6x SATA3 ports, 2x SATA2 ports.

---

### Post by MAFoElffen on 2024-03-24
My recommended would be the case ($75), the 5th Gen Intel i7 ($30), and the last SuperMicro Board. Notice that board says $99.99 or Best Offer. Make him an offer. Doesn't hurt to try right?

Then you could do what you wanted to do in your first post. Plenty of room for growth over time, without fighting anything to make it work... That would be a great foundation to build on top of for a NAS. 

Like i said, room for storage drives are your priority. Then PCIe and SATA bus generation speeds. That has the PCie slots to support any storage controllers and any network NICs you might need to support your network shares in the future.

---

### Post by sgt-mike on 2024-03-24
I really Like the idea of the 5th Gen i7  alot......
While I have not read all the way through your last two post.... 
I re-read where you wrote : could go on for pages... Even write your a book on it. Because you have  not set any boundaries or limits of scope. Maybe you should limit your  scope a bit to get this more focused and directed.                 "
That prompted me to hurry up and post this.

Needs for the NAS/NFS server???
 ... easy to back up data From a media Server... up load ISO's of install disk, Photos ,  and for me to learn on ... 

Actually It will Probably be heavier on the read side vs the write side.   


I know you lean towards the RaidZ2 vs the RaidZ....   but up till last night after I posted I really didn't know Exactly how the  Zpool worked ... and I think I have just enough knowledge to be silly and dangerous haha. But the way I understand it I can form a zpool from a Raidz and a Raidz2 vdev (hopefully I stated that correctly)

BTW 
      I have earmarked the Items you highly advised to round up at the end of this month (payday -- Military disabled retiree) and will start rounding up the components.
I Absolutely love this case you found ------"Ditch the case. This one is $75: [https://www.ebay.com/itm/23481312999...hoCtXcQAvD_BwE]("https://www.ebay.com/itm/234813129991?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1i4UkiHmMSoiSBKPG5TP1CA76&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=234813129991&targetid=1529493989662&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1529493989662&abcId=9316496&merchantid=6296724&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQAylyDViGH5X7Sds1NwlXkguTODuWZq5XUHQ2o7VYhI86sjo9x380ohoCtXcQAvD_BwE")
That is a full-tower for $75 with plenty of room for storage and whatever you what to throw at it. Has plenty of room to grow."  

The price is great until I got to the shipping ---- WOW $103.00   ,,,, I've shipped machine guns way cheaper than that. 
I'll  buzz / email the seller and see what's up with that. But then again I've seen cases for over $300 without PSU's not counting the shipping. (just sticker shock is all I expected about half that amount until I looked) so I just might need to "suck it up buttercup" and the more I mull it over and type it's getting way easier a pill to shallow (shipping cost). 
For a PSU I was thinking a modular 1000 to 1200W (corsair maybe??) 
I thank you from the bottom of my heart on your research and posting those items.

---

### Post by MAFoElffen on 2024-03-24
With priority on reads for media (movies, photos, music)... SAS would be overkill. So would SSD or NVMe. But in the same sentence, you mentioned "backups to", then your priority changes to "network transfer speeds and writes". <--- Depends what types of backups (full, incremental or differential), and how large the files are.

TrueNAS and other NAS systems really push ZFS. I challenge you to learn ZFS. I think it is really worthwhile to learn and use. It is fast and dependable. It is easy to use, as long as you learn a few commands to use it, and keep up with a few things.

Read posts in this Forum from 1fallen and I on ZFS and see for yourself. Both of us help here with ZFS use and work behind the scenes to keep things going for it for Ubuntu. It uses a COW filesystem, which means Copy-On-Write (confirm the write, before committing it). It is a Volume Manager, sort of like LVM.

What i like about it, is that, like LVM, I can make changes to it, or do maintenance, while the filesystem is Live. For RAIDZ, if you look at this on my server:
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool
[sudo] password for mafoelffen: 
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:21:04 with 0 errors on Sun Mar 10 00:45:05 2024
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

```
That pool (datapool) is a 5x 2 TB SSD RAIDZ2 Array, with one 2 TB NVMe with a partition used as a hardware read cache (L2ARC), and another partition used as a hardware read cache (SLOG). They are SATA3, and the i/o speeds are benchmarked at
```

TEST_WRITE: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s] 
TEST_WRITE: (groupid=0, jobs=1): err= 0: pid=861190: Tue Feb 13 07:54:18 2024
  write: IOPS=872, BW=873MiB/s (915MB/s)(10.0GiB/11736msec); 0 zone resets
    slat (usec): min=121, max=1734, avg=407.70, stdev=273.42
    clat (nsec): min=1198, max=7534.3M, avg=35377576.92, stdev=412853630.65
     lat (usec): min=135, max=7535.0k, avg=35785.57, stdev=412876.22
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    6], 20.00th=[    6],
     | 30.00th=[    6], 40.00th=[    8], 50.00th=[   11], 60.00th=[   15],
     | 70.00th=[   16], 80.00th=[   18], 90.00th=[   21], 95.00th=[   31],
     | 99.00th=[   46], 99.50th=[   49], 99.90th=[ 7550], 99.95th=[ 7550],
     | 99.99th=[ 7550]
   bw (  MiB/s): min=  548, max= 4800, per=100.00%, avg=2215.33, stdev=1465.65, samples=9
   iops        : min=  548, max= 4800, avg=2215.33, stdev=1465.65, samples=9
  lat (usec)   : 2=0.02%, 4=0.03%, 250=0.03%, 500=0.04%, 750=0.07%
  lat (usec)   : 1000=0.03%
  lat (msec)   : 2=0.21%, 4=0.41%, 10=45.43%, 20=40.48%, 50=12.95%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=446, max=446, avg=446.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  446],  5.00th=[  446], 10.00th=[  446], 20.00th=[  446],
     | 30.00th=[  446], 40.00th=[  446], 50.00th=[  446], 60.00th=[  446],
     | 70.00th=[  446], 80.00th=[  446], 90.00th=[  446], 95.00th=[  446],
     | 99.00th=[  446], 99.50th=[  446], 99.90th=[  446], 99.95th=[  446],
     | 99.99th=[  446]
  cpu          : usr=3.69%, sys=29.50%, ctx=13527, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=873MiB/s (915MB/s), 873MiB/s-873MiB/s (915MB/s-915MB/s), io=10.0GiB (10.7GB), run=11736-11736msec
TEST_READ: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1)
TEST_READ: (groupid=0, jobs=1): err= 0: pid=861236: Tue Feb 13 07:54:20 2024
  read: IOPS=8006, BW=8006MiB/s (8395MB/s)(10.0GiB/1279msec)
    slat (usec): min=77, max=511, avg=123.68, stdev=39.18
    clat (nsec): min=1240, max=9849.2k, avg=3827351.26, stdev=1161532.91
     lat (usec): min=111, max=10188, avg=3951.21, stdev=1197.20
    clat percentiles (usec):
     |  1.00th=[ 2212],  5.00th=[ 3326], 10.00th=[ 3359], 20.00th=[ 3425],
     | 30.00th=[ 3425], 40.00th=[ 3458], 50.00th=[ 3490], 60.00th=[ 3490],
     | 70.00th=[ 3523], 80.00th=[ 3589], 90.00th=[ 4686], 95.00th=[ 7308],
     | 99.00th=[ 7635], 99.50th=[ 7832], 99.90th=[ 8225], 99.95th=[ 8848],
     | 99.99th=[ 9634]
   bw (  MiB/s): min= 6522, max= 8928, per=96.49%, avg=7725.00, stdev=1701.30, samples=2
   iops        : min= 6522, max= 8928, avg=7725.00, stdev=1701.30, samples=2
  lat (usec)   : 2=0.04%, 4=0.01%, 250=0.10%, 500=0.10%, 750=0.10%
  lat (usec)   : 1000=0.14%
  lat (msec)   : 2=0.43%, 4=87.92%, 10=11.17%
  cpu          : usr=0.23%, sys=99.37%, ctx=1, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=8006MiB/s (8395MB/s), 8006MiB/s-8006MiB/s (8395MB/s-8395MB/s), io=10.0GiB (10.7GB), run=1279-1279msec

```
I know: "Show me the data!" --> "Just the facts mame..."

Like LVM, you can always add vdevs to a pool (without any RAID) to increase your storage space. But-- Putting disks into striped arrays not only ensures some protection for data integrity, but also improves the I/O performance greatly.

If you search my username on "zfs raidz performance" you'll find a thread were we tuned someones PCIe gen2 with RAIDZ3 to be able to do local network backups at around 550-575 MBs sustained writes on very large files... (Faster on smaller files.)

---

### Post by sgt-mike on 2024-03-25
Yes, very interested in the open zfs,RAIDZ and Z2  and really I don't know enough to actually ask good questions (yet). 

But from what little I have read thus far it looks very promising. 

Back to the  Server purpose outside the ISO's for installing operating systems or drive images of say my 1TB laptop or the wife's 500gb laptop, the largest files will probably be in the 1 to 4Gib range.(media data) for write on the NAS/NFS/Backup Server. 

The reason I mentioned the SAS and SATA Enterprise class (2.5") configurations is because what I have seen in the spinning disk SAS or SATA the drive height / Thickness is about 19 mm or so . Now that would drive the Cage configuration to a 4 drive in a 5.25" external bay. 

But Like you stated on the SSD's Enterprise class whether SAS / SATA that is a skinny 7mm height  which would allow either a 6 drive or 8 drive in each 5.25" External bay. I like the 8 drive best as it would allow 6 members and 2 spares for that cage to be in that array. 

NVMe Ive seen those cage at 8 drives per cage and yep they are just stupid fast. 

On the large 3.5" disk (over 8TB  )it gets really frustrating at the advertised vs the actual capacity, I know why that is but still when you lose a TB or more per drive before it get's into an array . But that is the fact of life I guess. Price point wise they might be cheaper IDK just have not applied math to if for cost saving.

---

### Post by sgt-mike on 2024-03-25
> **MAFoElffen said:**
> 

*** Now if you went with 5th Gen Intel i7-5970K for $30:
[https://www.ebay.com/itm/166470907642?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=166470907642&targetid=1531876731998&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1531876731998&abcId=9316496&merchantid=6296724&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA3i6wuqWZ6iiNlB5KC1ZMTJr-jNsFAO4J9f5E3G5AIA9jEnga4g8bRoCclMQAvD_BwE](https://www.ebay.com/itm/166470907642?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=166470907642&targetid=1531876731998&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1531876731998&abcId=9316496&merchantid=6296724&gad_source=1&gclid=CjwKCAjwnv-vBhBdEiwABCYQA3i6wuqWZ6iiNlB5KC1ZMTJr-jNsFAO4J9f5E3G5AIA9jEnga4g8bRoCclMQAvD_BwE)

Then thing open up with that socket LGA-2011-v3 motherboard:
Also DDR3 but... supports up to 64GB RAM, and all the PCIe slots should all be gen 3 (mostly)....

This is the best choice I found:
SuperMicro:
[https://www.ebay.com/itm/295998742304?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1KAIGESFYSVCJFcNQvy3RQQ47&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=295998742304&targetid=1585159292571&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385105599&mkgroupid=150744488839&rlsatarget=pla-1585159292571&abcId=9316499&merchantid=5301995045&gad_source=4&gclid=CjwKCAjwnv-vBhBdEiwABCYQA8p5SDpILj1wXN2PsfZ1RZ_uMV3ra4UJcvAGM5EJSMMNOOU6DeI8kBoCpCgQAvD_BwE](https://www.ebay.com/itm/295998742304?chn=ps&_trkparms=ispr%3D1&amdata=enc%3A1KAIGESFYSVCJFcNQvy3RQQ47&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=295998742304&targetid=1585159292571&device=c&mktype=pla&googleloc=9033423&poi=&campaignid=20385105599&mkgroupid=150744488839&rlsatarget=pla-1585159292571&abcId=9316499&merchantid=5301995045&gad_source=4&gclid=CjwKCAjwnv-vBhBdEiwABCYQA8p5SDpILj1wXN2PsfZ1RZ_uMV3ra4UJcvAGM5EJSMMNOOU6DeI8kBoCpCgQAvD_BwE)
Spec's: [https://www.thomas-krenn.com/en/wiki/Supermicro_X9SRL-F_Motherboard](https://www.thomas-krenn.com/en/wiki/Supermicro_X9SRL-F_Motherboard)
Pros:  2x PCI-E 3.0 x8 (in x16) slots, 2x PCI-E 3.0 x8 (in x8) slots, 2x PCI-E 3.0 x4 (in x8) slots, 1x PCI-E 2.0 x4 (in x8) slot. 64 GB non-ECC RAM. 6x SATA3 ports, 2x SATA2 ports.

Dug a little deeper into this board before fully committing although it's the correct socket doesn't support the i7, but supports the Xeon E5-1600 or the Xeon E5-2600  (4-8 cores)
Not sure how the Xeon stack up against the i7-4790K,  i7-5970K, or i7-6700K .

I have heard of the Xeon's but honestly don't know if for my purpose would this beat the i7's or stick with the i7 idea

---

### Post by MAFoElffen on 2024-03-28
I would stay with that i7-5930K. That is late 5th Gen Haswell-e, socket LGA2011-r3. Which yes, that socley also supports Xeon. Lets see, chipset X99...

[https://www.ebay.com/itm/395091391415?_trkparms=amclksrc%3DITM%26aid%3D1110006%26algo%3DHOMESPLICE.SIM%26ao%3D1%26asc%3D20231107084023%26meid%3D1e4e53ca8de2409aab795c48dcbf2478%26pid%3D101875%26rk%3D2%26rkt%3D12%26sd%3D305291805964%26itm%3D395091391415%26pmt%3D1%26noa%3D0%26pg%3D4429486%26algv%3DSimplAMLv11WebTrimmedV3MskuWithLambda85KnnRecallV1V2V4ItemNrtInQueryAndCassiniVisualRankerAndBertRecallWithVMEV3CPCAutoWithCassiniEmbRecallManual%26brand%3DASUS&_trksid=p4429486.c101875.m1851&itmprp=cksum%3A3950913914151e4e53ca8de2409aab795c48dcbf2478%7Cenc%3AAQAJAAABcLSVkHmTL63bebovD9RfpraPWbY9f4anjbziTIaEIOVXg2DWhVLks3Lfqff9vxxfjIh4XEXusIehlT2iEH8%252BCxXNySMxlDIQJ3g86%252Bx3AAIAq9gznqdGSR72ksP41kjzPN1reUbVsJuld0S4i4qXlQfTmkMeIJTCXTM8mLpr7ju2fMvruDu87ZX%252B4bShOvD%252B4s%252BgDJwI1DJaYWJiyL7MDX234XBi98q9OxV91fT0vb1hEQT78Xnuq%252BZiF%252FjSsEu7J4Ez7B2svKfuTilmTn4Dw6G5KA0njJskI%252BLISWJ3DIzcf%252F1WPLwAJ34YDRUuVlQcvbSgpYoAXIuOlQ55X70ROXt6o0fVWHaT4dPsfGyalfIy%252BkIuKfCcEqhA%252BAFnYZ1uODhn8sB%252F%252BvQuDiUYKFuQT1%252BmU3Fs18GECOBsMO1Mtf8phZBYhNmvdg1a03T%252BXGrATJXnwmm%252Bjm8HXF9JqUy%252BRdjZXn08Z4wqLXvCau%252FfQXgG%7Campid%3APL_CLK%7Cclp%3A4429486&epid=215929381&itmmeta=01HT2D4QCH9NTAEP2YHXZ7CX5A](https://www.ebay.com/itm/395091391415?_trkparms=amclksrc%3DITM%26aid%3D1110006%26algo%3DHOMESPLICE.SIM%26ao%3D1%26asc%3D20231107084023%26meid%3D1e4e53ca8de2409aab795c48dcbf2478%26pid%3D101875%26rk%3D2%26rkt%3D12%26sd%3D305291805964%26itm%3D395091391415%26pmt%3D1%26noa%3D0%26pg%3D4429486%26algv%3DSimplAMLv11WebTrimmedV3MskuWithLambda85KnnRecallV1V2V4ItemNrtInQueryAndCassiniVisualRankerAndBertRecallWithVMEV3CPCAutoWithCassiniEmbRecallManual%26brand%3DASUS&_trksid=p4429486.c101875.m1851&itmprp=cksum%3A3950913914151e4e53ca8de2409aab795c48dcbf2478%7Cenc%3AAQAJAAABcLSVkHmTL63bebovD9RfpraPWbY9f4anjbziTIaEIOVXg2DWhVLks3Lfqff9vxxfjIh4XEXusIehlT2iEH8%252BCxXNySMxlDIQJ3g86%252Bx3AAIAq9gznqdGSR72ksP41kjzPN1reUbVsJuld0S4i4qXlQfTmkMeIJTCXTM8mLpr7ju2fMvruDu87ZX%252B4bShOvD%252B4s%252BgDJwI1DJaYWJiyL7MDX234XBi98q9OxV91fT0vb1hEQT78Xnuq%252BZiF%252FjSsEu7J4Ez7B2svKfuTilmTn4Dw6G5KA0njJskI%252BLISWJ3DIzcf%252F1WPLwAJ34YDRUuVlQcvbSgpYoAXIuOlQ55X70ROXt6o0fVWHaT4dPsfGyalfIy%252BkIuKfCcEqhA%252BAFnYZ1uODhn8sB%252F%252BvQuDiUYKFuQT1%252BmU3Fs18GECOBsMO1Mtf8phZBYhNmvdg1a03T%252BXGrATJXnwmm%252Bjm8HXF9JqUy%252BRdjZXn08Z4wqLXvCau%252FfQXgG%7Campid%3APL_CLK%7Cclp%3A4429486&epid=215929381&itmmeta=01HT2D4QCH9NTAEP2YHXZ7CX5A)
Specs look good: [https://motherboarddb.com/motherboards/1647/X99-A%20II/](https://motherboarddb.com/motherboards/1647/X99-A%20II/)

If you did go with a Xeon 2600 series CPU... This board:
[https://www.amazon.com/MACHINIST-Motherboard-Support-Channel-X99-RS9/dp/B094CWF5BT/ref=asc_df_B094CWF5BT/?tag=hyprod-20&linkCode=df0&hvadid=532535399205&hvpos=&hvnetw=g&hvrand=17571027491197996451&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033513&hvtargid=pla-1398305581341&mcid=3e0bf0eeb95f35bbab73b96cef1547f0&gclid=Cj0KCQjwqpSwBhClARIsADlZ_TnTuXy9SfvnPAgLPYqDyTuxVVv7f_tp-ZDjBQRaDIz0b-r9miJOB6saAoQ1EALw_wcB&th=1](https://www.amazon.com/MACHINIST-Motherboard-Support-Channel-X99-RS9/dp/B094CWF5BT/ref=asc_df_B094CWF5BT/?tag=hyprod-20&linkCode=df0&hvadid=532535399205&hvpos=&hvnetw=g&hvrand=17571027491197996451&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033513&hvtargid=pla-1398305581341&mcid=3e0bf0eeb95f35bbab73b96cef1547f0&gclid=Cj0KCQjwqpSwBhClARIsADlZ_TnTuXy9SfvnPAgLPYqDyTuxVVv7f_tp-ZDjBQRaDIz0b-r9miJOB6saAoQ1EALw_wcB&th=1)
This look like it is has 2 M.2 slots, which one is PCIe and the other SATA. The M.2 SATA, you could use M.2 to 6x SATA, which would then give you 6 more SATA ports... But you would have to check the manual to ensure using that port didn't disable any of the onboard SATA ports. That is a thing sometimes. That board also uses DDR4 memory.

Then back to X99 boards...
[https://www.ebay.com/itm/186301396265?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=186301396265&targetid=1530885249288&device=c&mktype=pla&googleloc=9033513&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1530885249288&abcId=9316496&merchantid=113390167&gad_source=1&gclid=Cj0KCQjwqpSwBhClARIsADlZ_TnmEGJZWDloYj5s0fKMOy9qLpwUS0F3RsHY_Ufjw4OYke7AEkhSf44aAm0IEALw_wcB](https://www.ebay.com/itm/186301396265?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=186301396265&targetid=1530885249288&device=c&mktype=pla&googleloc=9033513&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1530885249288&abcId=9316496&merchantid=113390167&gad_source=1&gclid=Cj0KCQjwqpSwBhClARIsADlZ_TnmEGJZWDloYj5s0fKMOy9qLpwUS0F3RsHY_Ufjw4OYke7AEkhSf44aAm0IEALw_wcB)

---

### Post by sgt-mike on 2024-03-28
OK, then LOL....... kinda what I thought on the 5th Gen i7 vs the Xeon 2600 series. 

In my searches found a real good deal (auction) on a Intel Xeon E-2697 v2 Dell T7610 that supports two CPU's, of course ships with just one cpu and 48 GB ram. But propriety out the tail end I could go on about the cons 1 external 5.25 drive bay limited drive bays, In my mind wasn't worth the effort. What got me to find it was that sometimes it was actually cheaper to get the CPU (4th to 8th gen)  with a old Dell motherboard.  

80ish dollars on a Motherboard doesn't blow the budget. Nice find on the board.

---

### Post by sgt-mike on 2024-03-30
been deeply researching the processor you mentioned and it really stands out 6 cores....
Looking over the Motherboards I noticed none have onboard video.  This caused me to ponder something.
I understand that I can utilize a GPU in a headless server and configure it to actually engage. 
The question is does the GPU actually assist in processing Files in a NAS/NFS setup?  I can see where the GPU could really help a media server.





Update on progress
Did Locate a 1000Watt PSU  
[https://www.ebay.com/itm/145658965432?mkevt=1&mkpid=0&emsid=e12061.m3112.l9735&mkcid=26&ch=osgood&euid=5c1cd5e49f5b421a9a3a8e22ddd39228&bu=43161714504&osub=-1%7E1&crd=20240330091645&segname=12061](https://www.ebay.com/itm/145658965432?mkevt=1&mkpid=0&emsid=e12061.m3112.l9735&mkcid=26&ch=osgood&euid=5c1cd5e49f5b421a9a3a8e22ddd39228&bu=43161714504&osub=-1%7E1&crd=20240330091645&segname=12061)

Did find the same case you pointed out for less on the shipping. 
Had a CPU / Motherboard on a buy now (vendor had 2) , and before I could click on the buy somebody else snatched both....

---

### Post by MAFoElffen on 2024-03-30
You still need a GPU of some type, even in headless. <-- Some Motherboards that will work headless. Others, if the POST looks for a video source, it stops at a fatal order if it doesn't see one. So I would say, yes, but not always true.

With 5th Gen Intel boards, since they usually have a legacy PCI port there, I would throw in a cheap VGA PCI card so it had something to find. But with i7-xxxx-K, the "K" say it has in-chip iGPU... Are yo referring to Xeon Chips?

I have a DELL T720, with dual Xeons. The board has an onboard GPU. That also has 18 2.5" SAS hot-swap bays. If you are talking about the complete system... Go for it. But if for just the mtoherboard... That board will not fit in an aftermarket case. The form-factor and cabling is proprietary to Dell PE.

---

### Post by sgt-mike on 2024-03-31
I've pretty much given up on the Xeon processors only basically because I  don't know enough about them, and been going the route of  i7-5930K  or later gen. in my search,  and the processors I'm looking at,  all  have CPU graphics support. Even if the main board doesn't have onboard  video card. I know that some sort of video is needed even in headless be  it a onboard chipset or add on card.

The question I have  is not relating to anything but does the GPU such as a Geforce dedicated  GPU with processor giving a advantage over a standard Video card be it  onboard or added. And if so how much is the advantage (like is it worth  the added cost of the GPU). 

I'm not wording my response to my question clearly.  Let me try in another way.

OK  in a media server I can see where a added  Geforce GPU (or a radeon insert any brand, think gamer's version here)  with a internal cpu & dedicated ram,  will it greatly enhance the  server with encoding / decoding files to play to the tv (I'm aware  that that can be disabled and just serve files, I have mine decoding to  the TV).

Now in just serving files role such as  a NAS/NFS server does. Will  adding a GPU with dedicated cpu / ram aid in the process of serving  files enough to justify the cost?  versus just a plain onboard video  or cheap add-on card using the Main CPU (think i7-4790K as a baseline).

Now with that said even though I used the i7-4790K as a question I'll be looking for a more capable processor such as the i7-5930K or better in the build. Just have not located the cpu/motherboard at the price point I want to pay...... yet.

I did order that case you pointed out in your post, although different supplier I got it for basically what that guy wanted for shipping so that was a win / cost savings. as well as a 1000 watt PSU to sit in there.

---

### Post by MAFoElffen on 2024-03-31
I use Plex Server for my media server. I have an NVidia GTX 1650ti in mine. Along with another slot for my storage controller. My son and others here have moved from Plex to JellyFin. I would consider that GPU as mid-range, and doesn't break the bank. It does what it needs to do.

Along the lines of your question, from Plex: [https://support.plex.tv/articles/200250347-transcoder/](https://support.plex.tv/articles/200250347-transcoder/)

Same for JellyFin: [https://jellyfin.org/docs/general/administration/hardware-acceleration/](https://jellyfin.org/docs/general/administration/hardware-acceleration/)

So yes, it helps.

But be aware, that for a NAS for a media Server, then you need at least 2x PCIe x16 slots. One for a GPU and One for a HBA disk storage controller, so you add many drives. 

Just saying, keep that in mind.

Or just have the NFS shares hosted there, and the Media Server running on another machine with a good GPU (another option).

Mine is on my Workstation, which is dual-boot... Where Plex Server comes up in both Ubuntu & in Windows. That way, whichever it is booted as, my wife can still have access to the media server. Have to keep her happy.

---

### Post by sgt-mike on 2024-04-02
Yes when I brought up the Media Server,  mine it is it's own machine  having it's own files / CPU / GPU / ram locally serving the TV only.  

It was only for a comparison vs just serving files as two separate machine. 

That  is why I brought up the NAS/NFS machine and GPU question, which will be  it's own machine dedicated to just that function a file server. It will  catch the backup's (this is in addition to the backup's I have on  external drives) from the media server, and other computers. I was  wondering if a high speed GPU (by high speed GPU i mean any board that  exceeds the normal onboard controller / just a vga card) actually helps a  lot in just serving files.  And is it's extra processing enough  tradeoff to justify cost .So my take away is yes within reason from your  response. That NVidia GTX 1650 is along the I was thinking of, if the  main board I chose doesn't have a decent onboard controller, not  overkill yet enough to aid in the machine's function.  

The Pcie  slot dilemma you mentioned is another reason that I asked the question,  mentally I'm trying to look ahead  At how many slots and what type will  be needed.
While at the end having a empty slot or two.

The  HBA's ... I was thinking 16 ports or higher each one (HBA Card) in  addition to what the Main Board has. With plans to populate 2 slots at  the least, yet leaving room (slot) to add a additional if needed. 
2 HBA'a at 16 ports each will allow 4 - 2.5" 8 bay cages or 8 - 4 bay cages.

My  vision of the NAS/NFS is not to run 24x7, but as needed, which means  once I set it up I'll look at /into wake on lan function. Or just walk  over to it and turn it on if that function is not supported before need  /use.

---

### Post by MAFoElffen on 2024-04-05
Dang. I wrote you a post last night... With lots of links for 12 port LSI SAS HBA cards @ EBay. And don't see it now.

The best deal I found for you was this one:
[https://www.ebay.com/itm/204148621555?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=204148621555&targetid=2290620803403&device=c&mktype=pla&googleloc=9033510&poi=&campaignid=20688831350&mkgroupid=158250977497&rlsatarget=pla-2290620803403&abcId=9326636&merchantid=101984566&geoid=9033510&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQszPiITEZa_xnjclEe086aZYYQMw6pFFyHFJEd4j1-7L1ci3q9WL9uBoCsSsQAvD_BwE](https://www.ebay.com/itm/204148621555?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=204148621555&targetid=2290620803403&device=c&mktype=pla&googleloc=9033510&poi=&campaignid=20688831350&mkgroupid=158250977497&rlsatarget=pla-2290620803403&abcId=9326636&merchantid=101984566&geoid=9033510&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQszPiITEZa_xnjclEe086aZYYQMw6pFFyHFJEd4j1-7L1ci3q9WL9uBoCsSsQAvD_BwE)

It is PCIe x8 gen 3.0. The 4 port SAS cables usually run about $18 each. 4 x4 = 16. That card supports SAS/SATA.

On GPU for a files server. No doesn't matter. The onboard -GPU is fine. It's just a file server. For that matter, if you wanted to store your media files there is an NFS share, it will be fine. <-- Then your media server can cannect to the file, and it's GPU can help with decoding...

For a file server, your priorities are storage pools, disk I/O and network throughput... And the ability to add more and more storage as needed. Then the ability to manage that storage.

The types of disks depend on what they will be used for and the priority of the I/O, whether reads or writes, and how large 'the files' are.

HDD is good for mass media and backups... Though too slow a disk, and your backups will take longer. 20TB Recertified Enterprise HDD drives are cheap. Even if you look into Recert'ed "lots" of SAS drives...

There is this:
[https://www.ebay.com/itm/264167188175?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=264167188175&targetid=2282899792497&device=c&mktype=pla&googleloc=9033513&poi=&campaignid=20938509022&mkgroupid=154882361170&rlsatarget=pla-2282899792497&abcId=9367438&merchantid=118916553&geoid=9033513&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQs9eDkcOfcBHNn6iouezp0HjVwbqMT5AByk2w-iULcbWLzHjx3go78RoC0uQQAvD_BwE](https://www.ebay.com/itm/264167188175?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=264167188175&targetid=2282899792497&device=c&mktype=pla&googleloc=9033513&poi=&campaignid=20938509022&mkgroupid=154882361170&rlsatarget=pla-2282899792497&abcId=9367438&merchantid=118916553&geoid=9033513&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQs9eDkcOfcBHNn6iouezp0HjVwbqMT5AByk2w-iULcbWLzHjx3go78RoC0uQQAvD_BwE)

Just an example, but... Big investment outlay out-front. New 15K rpm SAS drives 20x 600GB = $1100. That comes out to $50 each. But that is only a little over 11 TB total.

This one is a lot of 10 new SAS 600GB drives which comes out to about $59 each:
[https://www.ebay.com/itm/254530176280?_trkparms=amclksrc%3DITM%26aid%3D1110006%26algo%3DHOMESPLICE.SIM%26ao%3D1%26asc%3D262498%26meid%3De0c2491348614db38851bb3a3c8b2772%26pid%3D101224%26rk%3D4%26rkt%3D5%26sd%3D264167188175%26itm%3D254530176280%26pmt%3D0%26noa%3D1%26pg%3D4429486%26algv%3DDefaultOrganicWebV9BertRefreshRanker%26brand%3DSeagate&_trksid=p4429486.c101224.m-1](https://www.ebay.com/itm/254530176280?_trkparms=amclksrc%3DITM%26aid%3D1110006%26algo%3DHOMESPLICE.SIM%26ao%3D1%26asc%3D262498%26meid%3De0c2491348614db38851bb3a3c8b2772%26pid%3D101224%26rk%3D4%26rkt%3D5%26sd%3D264167188175%26itm%3D254530176280%26pmt%3D0%26noa%3D1%26pg%3D4429486%26algv%3DDefaultOrganicWebV9BertRefreshRanker%26brand%3DSeagate&_trksid=p4429486.c101224.m-1)

This is a 5-pack of Factory Refurbished 20TB 7200k Enterprise SATA HDD's: [https://www.amazon.com/Seagate-Exos-7200RPM-5-Pack-Enterprise/dp/B0CKS32PTN/ref=asc_df_B0CKS32PTN/?tag=hyprod-20&linkCode=df0&hvadid=677903220948&hvpos=&hvnetw=g&hvrand=16361069529211915720&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033513&hvtargid=pla-2244679454123&psc=1&mcid=44dba8c99cf13e88b127282cb105a76c&gad_source=1](https://www.amazon.com/Seagate-Exos-7200RPM-5-Pack-Enterprise/dp/B0CKS32PTN/ref=asc_df_B0CKS32PTN/?tag=hyprod-20&linkCode=df0&hvadid=677903220948&hvpos=&hvnetw=g&hvrand=16361069529211915720&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033513&hvtargid=pla-2244679454123&psc=1&mcid=44dba8c99cf13e88b127282cb105a76c&gad_source=1)

That comes out to about 57 TB of usable storage in RAIDZ2. Refurb'ed 20TB enterprise drives run about $250 each. But you can find 12 TB refurb'ed Enterprise drives at NewEgg for $99 each...
[https://www.newegg.com/seagate-exos-x14-st12000nm0538-12tb/p/1Z4-002P-022C7?item=9SIA5ADJZF0288&source=region&nm_mc=knc-googlemkp-pc&cm_mmc=knc-googlemkp-pc-_-pla-goharddrive-_-hard+drives-_-9SIA5ADJZF0288&utm_source=google&utm_medium=paid+shopping&utm_campaign=knc-googlemkp-pc-_-pla-goharddrive-_-hard+drives-_-9SIA5ADJZF0288&id0=Google&id1=19482421907&id2=146598832444&id3=&id4=&id5=pla-2275542440526&id6=&id7=9033513&id8=&id9=g&id10=c&id11=&id12=CjwKCAjwwr6wBhBcEiwAfMEQs-cncKzM2SwyCFtNGqOaoPSZUkJPuht9qEBlTZlsRr3gYfr3GQTgfBoCqpwQAvD_BwE&id13=&id14=Y&id15=&id16=643915474301&id17=&id18=&id19=&id20=&id21=pla&id22=100715614&id23=online&id24=9SIA5ADJZF0288&id25=US&id26=2275542440526&id27=Y&id28=&id29=&id30=1603825120928049848&id31=en&id32=&id33=&id34=&gclsrc=aw.ds&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQs-cncKzM2SwyCFtNGqOaoPSZUkJPuht9qEBlTZlsRr3gYfr3GQTgfBoCqpwQAvD_BwE](https://www.newegg.com/seagate-exos-x14-st12000nm0538-12tb/p/1Z4-002P-022C7?item=9SIA5ADJZF0288&source=region&nm_mc=knc-googlemkp-pc&cm_mmc=knc-googlemkp-pc-_-pla-goharddrive-_-hard+drives-_-9SIA5ADJZF0288&utm_source=google&utm_medium=paid+shopping&utm_campaign=knc-googlemkp-pc-_-pla-goharddrive-_-hard+drives-_-9SIA5ADJZF0288&id0=Google&id1=19482421907&id2=146598832444&id3=&id4=&id5=pla-2275542440526&id6=&id7=9033513&id8=&id9=g&id10=c&id11=&id12=CjwKCAjwwr6wBhBcEiwAfMEQs-cncKzM2SwyCFtNGqOaoPSZUkJPuht9qEBlTZlsRr3gYfr3GQTgfBoCqpwQAvD_BwE&id13=&id14=Y&id15=&id16=643915474301&id17=&id18=&id19=&id20=&id21=pla&id22=100715614&id23=online&id24=9SIA5ADJZF0288&id25=US&id26=2275542440526&id27=Y&id28=&id29=&id30=1603825120928049848&id31=en&id32=&id33=&id34=&gclsrc=aw.ds&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQs-cncKzM2SwyCFtNGqOaoPSZUkJPuht9qEBlTZlsRr3gYfr3GQTgfBoCqpwQAvD_BwE)
 
Be aware that the warranty on Seagate Factory Refurbished Exos X14 Enterprise drives is 2 years, compared to 3 years new.
 
You can find deals if you shop around. And with the hardware foundation more open, you have a lot more choices open to you with what you can do.

If ZFS RAIDZ2, I would start out at vdevs of RAIDZ2, and add each of those vdevs of the same. At 12 TB each for 5 drives, that comes out to 34 TB per each vdev @ $495 per vdev, or $14.50 per TB of storage and fairly fast enterprise drives. If you need more, then later on, add another vdev of 34 TB RAIDZ2 when you can afford it, to that same pool.

Is an investment...

---

### Post by sgt-mike on 2024-04-05
yeah the thing I did not cover is the budget  ($300.00 a month)... that  will determine how soon this will take effect to get the server somewhat  even close to completion.
The power supply (1000watt)  arrived today, looks to be in really good shape (have not tested it yet) 
Xtreme Gear XG-H1000 PCI-E Cable 120mm Fan ATX 12V Gaming PC  1000W Power Supply [https://www.ebay.com/itm/145658965432](https://www.ebay.com/itm/145658965432)

The case   (Cooler Master HAF 922 High Air Flow Mid Tower PC Case -5 external 5.25" bays, 5-3,5" internal Bays) [https://www.ebay.com/itm/315101475632](https://www.ebay.com/itm/315101475632)  has not been shipped yet maybe sometime in 3 weeks that individual will get off his tail and get it going LMAO. 

Looking  at the drives you posted (3.5" format) would cause me to change the cage  format that I was thinking in the external 5.25" bays. I was thinking of  cages that housed 2.5" drives in each. But that is not a bad thing as a  3 bay 5 drive cage would be nice as well.  Or even a mix if I use the 3  bay (5.25")  5 drive (3.5') cage with a singe 1 bay (5.25") 8 drive  2.5" (I was thinking SSD's here) or even down to 4 drive 2.5" (be that  enterprise spinning disk or even SSD's)  would still allow me a single  5.25" empty external bay.  Versus the orginal Idea of all the 5.25"  external bays being setup for 2.5" drives. 


" The best deal I found for you was this one: [https://www.ebay.com/itm/20414862155...BoCsSsQAvD_BwE]("https://www.ebay.com/itm/204148621555?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=204148621555&targetid=2290620803403&device=c&mktype=pla&googleloc=9033510&poi=&campaignid=20688831350&mkgroupid=158250977497&rlsatarget=pla-2290620803403&abcId=9326636&merchantid=101984566&geoid=9033510&gad_source=1&gclid=CjwKCAjwwr6wBhBcEiwAfMEQszPiITEZa_xnjclEe086aZYYQMw6pFFyHFJEd4j1-7L1ci3q9WL9uBoCsSsQAvD_BwE")   "
That was along the line I was looking at  (LSI) I like the ability to switch between SATA /SAS as I haven't truly landed on that yet .
 If I was to go to enterprise class sata with that controller doesn't mean I cant upgrade to SAS later when a good buy comes along (which I like the throughput speed of SAS vs SATA).
  
Currently I'm watching this mobo cpu combo  
[https://www.ebay.com/itm/235504627362?epid=14026291047&itmmeta=01HTPN91SD52XFN1GZN855396G&hash=item36d52b6ea2:g:RCMAAOSwkqJmDa~L&itmprp=enc%3AAQAJAAAA4EM89CtWuGKJJE5Q04FcmIgWQh%2BAUbeLDQQ5hNLxn4s51qt4ywAEvbi9sbIpzNDcVT4vXs%2F8ntCpr4a40KGTIZgAqGN5dqG%2BOlgLwky5ilc0VHE38PnMmanMaJHU7pX7ZuuEGp%2BpievLKk8KhJqH%2F8UXxRPkkyTRSgQeiiq2KIBrQh7LfCSTYKCL%2FLgibKE3qpSUwWCNGixtB2oqw%2BEE4NcfFWtQdWlPHyfvKN7NwkAJ8n93MrjvOWIJrRwGSkW%2BaFU%2BkAXv5by0uUzvxOeJjBJGYqMSaPnE8Ab9q7Lsl9pe%7Ctkp%3ABk9SR_acpNXVYw](https://www.ebay.com/itm/235504627362?epid=14026291047&itmmeta=01HTPN91SD52XFN1GZN855396G&hash=item36d52b6ea2:g:RCMAAOSwkqJmDa~L&itmprp=enc%3AAQAJAAAA4EM89CtWuGKJJE5Q04FcmIgWQh%2BAUbeLDQQ5hNLxn4s51qt4ywAEvbi9sbIpzNDcVT4vXs%2F8ntCpr4a40KGTIZgAqGN5dqG%2BOlgLwky5ilc0VHE38PnMmanMaJHU7pX7ZuuEGp%2BpievLKk8KhJqH%2F8UXxRPkkyTRSgQeiiq2KIBrQh7LfCSTYKCL%2FLgibKE3qpSUwWCNGixtB2oqw%2BEE4NcfFWtQdWlPHyfvKN7NwkAJ8n93MrjvOWIJrRwGSkW%2BaFU%2BkAXv5by0uUzvxOeJjBJGYqMSaPnE8Ab9q7Lsl9pe%7Ctkp%3ABk9SR_acpNXVYw)

down  side I see is micro -atx .....I glanced at published benchmarks as a  workstation /gaming/etc looks to be OK for the use as a server.
also watching this one 
[https://www.ebay.com/itm/186370066517?epid=215929381&itmmeta=01HTH7VTZQK9AMDHY5PFZ0Z2SN&hash=item2b64858855:g:~TQAAOSwPdRmCPLE&itmprp=enc%3AAQAJAAAAwFcmv2UHsG9YeC%2B8KNpXT8%2FR1YzHz%2BM299vIpTyYWwNW%2Febe%2FSod5rhJisca2coDGsSkMJx2X2I0wdX%2B6Wp6Vre1zYbrH8lnHA%2FqCKZyc8RcJsf5v%2Bsg15mtZzQPwwc9GZEL0KVt89%2FxWuCnBkWqVG%2BtEO6QpwEm3jh5iKlHUzghD0e4gwqRZt%2BuR4OMIkwXoJNXClCPN2oOeHBUZwUrAHp22rMRHLEkpnL68wXKXBZ046xTtvNzjw2%2BdZof7elEtA%3D%3D%7Ctkp%3ABk9SR4Cw76fUYw](https://www.ebay.com/itm/186370066517?epid=215929381&itmmeta=01HTH7VTZQK9AMDHY5PFZ0Z2SN&hash=item2b64858855:g:~TQAAOSwPdRmCPLE&itmprp=enc%3AAQAJAAAAwFcmv2UHsG9YeC%2B8KNpXT8%2FR1YzHz%2BM299vIpTyYWwNW%2Febe%2FSod5rhJisca2coDGsSkMJx2X2I0wdX%2B6Wp6Vre1zYbrH8lnHA%2FqCKZyc8RcJsf5v%2Bsg15mtZzQPwwc9GZEL0KVt89%2FxWuCnBkWqVG%2BtEO6QpwEm3jh5iKlHUzghD0e4gwqRZt%2BuR4OMIkwXoJNXClCPN2oOeHBUZwUrAHp22rMRHLEkpnL68wXKXBZ046xTtvNzjw2%2BdZof7elEtA%3D%3D%7Ctkp%3ABk9SR4Cw76fUYw)

which will put on the search for cpu (i7-59XXK) and a cooler as well as RAM. but it is a ATX. 

That is just two of the 5 or 6 I'm watching on ebay as well as Goodwill...

Cages: 
I'm currently biding on this one [https://www.ebay.com/itm/186369791608?itmmeta=01HTAXS56VQFTZ2G57SPTCWCFJ&hash=item2b64815678:g:HsoAAOSwezJmCIc4&itmprp=enc%3AAQAJAAAAwCuILoEl5XmrDDXdzBECMP1Z6F4nxm7f7CfZq6ntgoUA0SfLIY%2B6T3kUiXW9oO1GkKw%2FKMZtPLjq38sHh0EpA5XsXdAWQUJMYH9yu9NsC8XSZLDdJeBBLa7xSPTkZ2DjMV5RmzN2tKMz%2FxlG9tbTIA4%2FmMOG%2Bse%2B5z4IJhZhWz4Qm8O8FNv4yq%2F%2BGhEyZzPTxDZ3utZKRrhbyVHJJXw1WX480N6WkgiS7t0MMoIyTP5o8q1ZWwicu1XghFRHd5aOZg%3D%3D%7Ctkp%3ABk9SR-7T5N3SYw&autorefresh=true](https://www.ebay.com/itm/186369791608?itmmeta=01HTAXS56VQFTZ2G57SPTCWCFJ&hash=item2b64815678:g:HsoAAOSwezJmCIc4&itmprp=enc%3AAQAJAAAAwCuILoEl5XmrDDXdzBECMP1Z6F4nxm7f7CfZq6ntgoUA0SfLIY%2B6T3kUiXW9oO1GkKw%2FKMZtPLjq38sHh0EpA5XsXdAWQUJMYH9yu9NsC8XSZLDdJeBBLa7xSPTkZ2DjMV5RmzN2tKMz%2FxlG9tbTIA4%2FmMOG%2Bse%2B5z4IJhZhWz4Qm8O8FNv4yq%2F%2BGhEyZzPTxDZ3utZKRrhbyVHJJXw1WX480N6WkgiS7t0MMoIyTP5o8q1ZWwicu1XghFRHd5aOZg%3D%3D%7Ctkp%3ABk9SR-7T5N3SYw&autorefresh=true)  

but  I know I can get the same thing (different manufacturer) from Newegg  for $69.00 + shipping new (both are sata/sas capable ebay & newegg),  but my thoughts was that the small SSD's installed within the posted  one on ebay could serve as a cache (provided they are faster than the other vdevs) , even if the drives are used they  might be ok enough to get started. But I'm not going any higher than new  cost even if it has drives. I mean heck 120gb ssd drives are cheaper  today. 
I looked at the 5.25" cages for 3.5" drives price point is  slightly higher, but not by much.  I'm not stuck on the 2.5" drive  format. and would happily stick them (3.5" ) in. 


Flipping back to the  Mother board I like the idea of the operating system sitting on a M2  slot NvME 60gbs or so separate from the ZFS array's.

34TB is probably way more than I need ..... but then again .... when I needed a truck to tow with    I bought a 3500 (1 ton) ....  storage capacity is like a truck's towing capacity  - there is no such thing as too much.

looked that the vendor on ebay you pointed out for the 500gb they do have a offering of 10 - 300gb 3.5" sas for a little above $300,00  which might be a start point based on my budget then grow it from there. Just a thought or rather a option not what i plan doing.


Added on April 6th 
   while watching that cage I pretty much decided to kinda go a  different route in filling the external drive bays. now focused on the  Motherboard /CPU/ cooler , I did find a i7-59030K processor at a not too  bad of a price. just need to nail that motherboard down.

---

### Post by MAFoElffen on 2024-04-06
The ASUS X99 is ATX and has all the ports you need for expansion down the road...

---

### Post by sgt-mike on 2024-04-08
In  my haste, I completely forgot /confused with a different Asus board   that the Asus X99-A and I7-5900K that I have obtained / ordered doesn't  come with a onboard graphics... oops lol NP. 
I'm sure I can either  find one, or use one that is plugged into a system that I have (the  Nvida Geforce GTX 10XX Founders edition comes to mind as that system  would default to the onboard graphics system if  need be ) to validate  the MB / processor /PSU is in good working order upon arrival of the  items, before installation into the case. Will just need need to pick up  some RAM (DDR4, most my existing systems have DDR3) before testing  components as well as a CPU cooler. 

I did go to pcpartspicker web site to see what the  estimated wattage draw would /might be with the max number of drives,  etc,  just to ballpark. the estimate. The results was 751 Watts or so.  The 1000 Watt PSU I picked up should be good to go. I just wish that the  site did not have SAS drives greyed out thus causing me to use SATA  drives for the estimate. 

Now once the items test good to go, I  plan on running the operating system (Ubuntu Server 22.04.4 LTS) on the  m.2 NvME slot provided, separate from the ZFS pools which will reside on  SAS/SATA drives. 
I was looking at as small as possible in capacity /cost NvME . 

[COLOR=#0000ff]Now here is where I have a actual question is there any brand name of NvME I should avoid ? 
I do understand that the OS will only need roughly < 2Gbs  of space, so I was thinking 32-64ish would be more than enough.  

Per the manual it  on page 1-22 it states on the following information to that M.2 socket
"  This socket allows you to install an M.2 (NGFF) SSD module. .....This  socket supports M Key and type 2242/2260/2280/22110 storage  devices......"  Just in case anybody needs specifics in order to answer  the question. [/COLOR]


In closing like I said there is really only 1 question, and that is there a brand of NvME to avoid? 

And by that a brand that just doesn't work well with Linux or has a higher than normal failure rate in your individual experience.

---

### Post by sgt-mike on 2024-04-08
I did find this in the correct manual.. I originally down loaded the manual for the Asus X99-A II , the correct one is Asus X99-A ......
 "M.2 Support*
This motherboard features the M.2 slot, which shares bandwidth with PCI Express 3.0 x4 slot
to speed up data transfer up to 32 Gb/s. This helps enhance the performance of your SSD
(Solid State Drive) that is dedicated only to the operating system.
* Supports PCIe Mode only "

so if I am reading and comprehending correctly  I can ONLY use 1 at a time  M,2 Or PCI Express  Which if understand it is also called a U.2 in the manual.  


The great thing about typing and posting  all this for is the ability for me to go back read over this and realize what should be obvious
I had posted two NvME's and then deleted them they was PCIe ver 4.0 x 4 slot if I had not done this, I probably wouldn't have caught it until I had ordered  it.
my board is PCIe version 3.0 x 4 slot

OK back to searching......
For  a PCIe 3.0x4 lane  NvME ...

1.Corsair Force MP500 120 GB M.2-2280 PCIe 3.0 X4 NVME Solid State Drive
didn't find a Amazon listing
Power tech review   [https://www.techpowerup.com/228667/corsair-unveils-the-force-series-mp500-m-2-nvme-pcie-ssds](https://www.techpowerup.com/228667/corsair-unveils-the-force-series-mp500-m-2-nvme-pcie-ssds)

2.  Intel Optane P1600X 58 GB M.2-2280 PCIe 3.0 X4 NVME Solid State Drive
[https://www.amazon.com/Intel-Optane-Memory-PCIe-80mm/dp/B06XSMTN31/ref=sr_1_1?crid=27VFUPD6ARCF3&dib=eyJ2IjoiMSJ9.ygqNdBHuOoW6ywFrkiI5X5CrXbti1zXEVi-5Qoc82U96rkUn4F5Fx8D88UO5yTN_HI_wcexLkpm7ewmzB7moN0jgV4Ln70cUYSouglTE9Rvaki47mI2rQGYzznkL0dM7BfU_cuKuNkOBqJmc3DFKAJDpvmbeni7XrdAnmJVOZn-AsV4h-bKeSF_9GtuBZTYZqT19CUtPBg7wgOf9leCLDBF-WKruMKAdSoiie3LA9P655yXZn4MAmncg0bo1NEPNpqd-H-4pKiM6m16MgpXGTy_E7koKZaQ7FtKD02XOC44.PJmJg9JduJceK8YL-cYROGLn9cemcho0NaQKe9Rp3U4&dib_tag=se&keywords=Intel%2BOptane%2BP1600X%2B58%2BGB%2BM.2-2280%2BPCIe%2B3.0%2BX4%2BNVME%2BSolid%2BState%2BDrive&qid=1712645055&sprefix=intel%2Boptane%2Bp1600x%2B58%2Bgb%2Bm.2-2280%2Bpcie%2B3.0%2Bx4%2Bnvme%2Bsolid%2Bstate%2Bdrive%2Caps%2C405&sr=8-1&th=1](https://www.amazon.com/Intel-Optane-Memory-PCIe-80mm/dp/B06XSMTN31/ref=sr_1_1?crid=27VFUPD6ARCF3&dib=eyJ2IjoiMSJ9.ygqNdBHuOoW6ywFrkiI5X5CrXbti1zXEVi-5Qoc82U96rkUn4F5Fx8D88UO5yTN_HI_wcexLkpm7ewmzB7moN0jgV4Ln70cUYSouglTE9Rvaki47mI2rQGYzznkL0dM7BfU_cuKuNkOBqJmc3DFKAJDpvmbeni7XrdAnmJVOZn-AsV4h-bKeSF_9GtuBZTYZqT19CUtPBg7wgOf9leCLDBF-WKruMKAdSoiie3LA9P655yXZn4MAmncg0bo1NEPNpqd-H-4pKiM6m16MgpXGTy_E7koKZaQ7FtKD02XOC44.PJmJg9JduJceK8YL-cYROGLn9cemcho0NaQKe9Rp3U4&dib_tag=se&keywords=Intel%2BOptane%2BP1600X%2B58%2BGB%2BM.2-2280%2BPCIe%2B3.0%2BX4%2BNVME%2BSolid%2BState%2BDrive&qid=1712645055&sprefix=intel%2Boptane%2Bp1600x%2B58%2Bgb%2Bm.2-2280%2Bpcie%2B3.0%2Bx4%2Bnvme%2Bsolid%2Bstate%2Bdrive%2Caps%2C405&sr=8-1&th=1)

Toms Hardware website [https://www.tomshardware.com/news/intel-launches-optane-ssd-p1600x](https://www.tomshardware.com/news/intel-launches-optane-ssd-p1600x)

3. HP EX900 120 GB M.2-2280 PCIe 3.0 X4 NVME Solid State Drive
[https://www.amazon.com/HP-EX900-Internal-2Yy42Aa-ABC/dp/B07B2Z3ZXR/ref=sr_1_1?crid=2JQC05CEHP1T3&dib=eyJ2IjoiMSJ9.EcX54gNJ9UpeARtRmVsnw0mbjuVUSsLeAyo1ZkY9Ek7u8eHC5xqayjRimCXkpePFwTcuLmz_R54Bj39iWd7MlmbWI9ei622rqVfBfx37WHqmrPY4rWyJpItequUHjXsHyAPDM8KV7EzXf4ZEZZyKSEzzqz5Y0WPijKMcNEHBRuDBXrBhfrnkf23to7YhUpQJX90mtIdmcKnB-_fWFka4IjMF7qBK5qFJkbZ64fXJzAg.mQ5ktEkWlsjTg2CDESamsCxBFYYBfRc2fzDud8k7y0w&dib_tag=se&keywords=HP+EX900+120+GB+M.2-2280+PCIe+3.0+X4+NVME&qid=1712644887&sprefix=hp+ex900+120+gb+m.2-2280+pcie+3.0+x4+nvme+%2Caps%2C375&sr=8-1](https://www.amazon.com/HP-EX900-Internal-2Yy42Aa-ABC/dp/B07B2Z3ZXR/ref=sr_1_1?crid=2JQC05CEHP1T3&dib=eyJ2IjoiMSJ9.EcX54gNJ9UpeARtRmVsnw0mbjuVUSsLeAyo1ZkY9Ek7u8eHC5xqayjRimCXkpePFwTcuLmz_R54Bj39iWd7MlmbWI9ei622rqVfBfx37WHqmrPY4rWyJpItequUHjXsHyAPDM8KV7EzXf4ZEZZyKSEzzqz5Y0WPijKMcNEHBRuDBXrBhfrnkf23to7YhUpQJX90mtIdmcKnB-_fWFka4IjMF7qBK5qFJkbZ64fXJzAg.mQ5ktEkWlsjTg2CDESamsCxBFYYBfRc2fzDud8k7y0w&dib_tag=se&keywords=HP+EX900+120+GB+M.2-2280+PCIe+3.0+X4+NVME&qid=1712644887&sprefix=hp+ex900+120+gb+m.2-2280+pcie+3.0+x4+nvme+%2Caps%2C375&sr=8-1)

Power Up tech
[https://www.techpowerup.com/ssd-specs/hp-ex900-120-gb.d417](https://www.techpowerup.com/ssd-specs/hp-ex900-120-gb.d417)


I like what I read on the Intel Optane while not the fastest but the latency and caching is attention grabbing .... the Cost I like...  just not sure if's a good choice and at $15.00  and after writing this part I find this white Paper from Intel addressing that exact Drive 
[https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://cdrdv2-public.intel.com/754692/PUBLIC-optane-ssd-p1600x-series-for-boot-drives-paper.pdf&ved=2ahUKEwjfn73v3LSFAxVtLkQIHYVjDDcQFnoECBUQAw&usg=AOvVaw0r3Zj0HVuSgXf0hCsbYw5r](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://cdrdv2-public.intel.com/754692/PUBLIC-optane-ssd-p1600x-series-for-boot-drives-paper.pdf&ved=2ahUKEwjfn73v3LSFAxVtLkQIHYVjDDcQFnoECBUQAw&usg=AOvVaw0r3Zj0HVuSgXf0hCsbYw5r)

I think I will go this route UNLESS sage advice says something like ohh it won't work as after I read that I was tipped over the edge, Also recalling that marketing departments also write that not the IT guys building developing.   
Well looks like my small campfire got peed on (only because the Chipset predates the Optane, not a big deal)
[https://community.intel.com/t5/Intel-Optane-Solid-State-Drives/Intel-Optane-32GB-Compatible-with-LGA-2011-v3-CPUs/m-p/285396#M1867](https://community.intel.com/t5/Intel-Optane-Solid-State-Drives/Intel-Optane-32GB-Compatible-with-LGA-2011-v3-CPUs/m-p/285396#M1867)

---

### Post by MAFoElffen on 2024-04-08
Well, you are receiving this (keep this manual for your reference): [https://dlcdnets.asus.com/pub/ASUS/mb/LGA2011/X99-A_II/E11090_X99-A_II_UM_WEB.pdf?model=x99a_ii](https://dlcdnets.asus.com/pub/ASUS/mb/LGA2011/X99-A_II/E11090_X99-A_II_UM_WEB.pdf?model=x99a_ii) 

This Silicon Image Orion Expansion card is what Dell uses for their Servers and Desktops to add a DVI-D port to their computers (only $10):[s]
 [https://www.ebay.com/itm/234266310913?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=234266310913&targetid=2204425646629&device=c&mktype=pla&googleloc=9033512&poi=&campaignid=20422342946&mkgroupid=150704843414&rlsatarget=pla-2204425646629&abcId=9318251&merchantid=127669641&geoid=9033512&gad_source=1&gclid=Cj0KCQjwq86wBhDiARIsAJhuphkVhRhv8NIGLAPhB0DLDPvFXtDz_TuC0cobYgazMAUrDg5aHj45rEEaAjU_EALw_wcB](https://www.ebay.com/itm/234266310913?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=234266310913&targetid=2204425646629&device=c&mktype=pla&googleloc=9033512&poi=&campaignid=20422342946&mkgroupid=150704843414&rlsatarget=pla-2204425646629&abcId=9318251&merchantid=127669641&geoid=9033512&gad_source=1&gclid=Cj0KCQjwq86wBhDiARIsAJhuphkVhRhv8NIGLAPhB0DLDPvFXtDz_TuC0cobYgazMAUrDg5aHj45rEEaAjU_EALw_wcB)
[/s]
Dang... Use that one as an example. That comes with a low profile slot plate. You rwould need a high-profile DVI-D plate... Wait 1. [s]Here is a high profile one for $49. (You could still shop around, now that you know what you are looking for.)
[https://www.ebay.com/itm/325779600557?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=325779600557&targetid=1531876742398&device=c&mktype=pla&googleloc=9033512&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1531876742398&abcId=9316496&merchantid=116335927&gad_source=1&gclid=Cj0KCQjwq86wBhDiARIsAJhuphmtTDioC0-ftU7ZERyX9rkLcpn0loCBfiRgtZQCrbiq0BnJ6YoaTXcaApYsEALw_wcB](https://www.ebay.com/itm/325779600557?chn=ps&norover=1&mkevt=1&mkrid=711-117182-37290-0&mkcid=2&mkscid=101&itemid=325779600557&targetid=1531876742398&device=c&mktype=pla&googleloc=9033512&poi=&campaignid=20385089669&mkgroupid=151067932066&rlsatarget=pla-1531876742398&abcId=9316496&merchantid=116335927&gad_source=1&gclid=Cj0KCQjwq86wBhDiARIsAJhuphmtTDioC0-ftU7ZERyX9rkLcpn0loCBfiRgtZQCrbiq0BnJ6YoaTXcaApYsEALw_wcB)
[/s]
Let's see if I still have one of the Dell PN's... 
EDIT: Here you go. Dell branded, high-profile, $10:
[https://www.ebay.com/itm/334596182760?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=334596182760&targetid=2204425646629&device=c&mktype=pla&googleloc=9033512&poi=&campaignid=20422342946&mkgroupid=150704843414&rlsatarget=pla-2204425646629&abcId=9318251&merchantid=127669641&geoid=9033512&gad_source=1&gclid=Cj0KCQjwq86wBhDiARIsAJhuphklFQe0j4xV9tQTct6BGqehSIP4TRJ72_86l8KCSsYctnK5f-Sfn7YaAhxWEALw_wcB](https://www.ebay.com/itm/334596182760?chn=ps&norover=1&mkevt=1&mkrid=711-166974-028196-7&mkcid=2&mkscid=101&itemid=334596182760&targetid=2204425646629&device=c&mktype=pla&googleloc=9033512&poi=&campaignid=20422342946&mkgroupid=150704843414&rlsatarget=pla-2204425646629&abcId=9318251&merchantid=127669641&geoid=9033512&gad_source=1&gclid=Cj0KCQjwq86wBhDiARIsAJhuphklFQe0j4xV9tQTct6BGqehSIP4TRJ72_86l8KCSsYctnK5f-Sfn7YaAhxWEALw_wcB)

Your PCIe x16-3 slot is only x4 lane... Put it in that slot. You wouldn't be using that x4 slot for a storage controller anyways. LOL

It will see any Intel i915 based GPU and adding output of that video through it's port. That way you are using the iGPU video from your CPU... (It's usually used to add a video port.)

---

### Post by sgt-mike on 2024-04-10
------------------Update Apr 13th 2024---------
Conducted testing of Motherboard/CPU components before case arrival and installation. All tested good to go .
I used the GTX10XX Geforce GPU for testing only into bios screen. Now to get the Video card /HBA that you pointed out to dedicate to that Motherboard. 
As well as populating the board with max RAM after a Bios update. 

-------------------------Added Apr 15th--------------

Did a little more research into the MB. Found a interesting part dealing with the M.2 Slot which is sort of mentioned in another post on here  [https://ubuntuforums.org/showthread.php?t=2496339](https://ubuntuforums.org/showthread.php?t=2496339) 
going through the PCIe x16 slots in the manual . Seems slot 4  (x16_4) shares band width with the M.2 slot and is disabled when the M.2 slot is utilized. 
So if I use the M.2 slot as a boot device as I had originally planned.  I lose one X16 slot, or if the slot is needed I could shift the boot device to a SSD/Sata via the 10 onboard sata connections.

This isn't really a problem as I could configure to boot from either just need to plan. 
so I install a LSI SAS  controller (LSI 9300-16i 16 port)  in X16 _ 1 slot and another LSI 9300-16i 16 port  in  X16 _2 slot, that leaves slot X16_3 for Video /GPU. If  NvME is installed then X16_4 (which is actually X4) is disabled.  
Which the two HBA's will allow me 32 sas ports plus I have 10 sata ports unused. 
Now I could just use a 4 port HBA with the 16 Port HBA which will allow 20 sas ports and the 10 sata ports. which is more than the case can house either way. So there isn't a down side These configurations only leaves me with two PCIe X1 slots available.

Or I could boot from a sata port with a drive similar to this [https://www.ebay.com/itm/204254322665?itmmeta=01HVCY23EVHVDJDA4X9A9ZZR0P&hash=item2f8e819fe9:g:b-4AAOSw~qlk-iTe&itmprp=enc%3AAQAJAAAAwKVDrQq8ktLSPoSLod3Ph15368xdAC534Ct72cmv3yiicBe2JtHmb5ZJIiFrNSeRLhp53Kl6nu%2FZwUCGdnWMSyaZZdEWNgaoPxvBGltp%2BF7%2FB2j4ZsUqVR%2B%2FyNOjsjROfdr2TAV9R4FeASQHDWd1BNLghsI5VErxC1Edgrahu9SKoWbsH8cbv90glYQ8lzq97NETIFtLNpDINg1OtGj1SGo1XVYojZXMyg5Mu%2BojNCD%2BXQqoRnKjZeKIFMIVvp7Y%2Bg%3D%3D%7Ctkp%3ABk9SR8q3iJ7bYw](https://www.ebay.com/itm/204254322665?itmmeta=01HVCY23EVHVDJDA4X9A9ZZR0P&hash=item2f8e819fe9:g:b-4AAOSw~qlk-iTe&itmprp=enc%3AAQAJAAAAwKVDrQq8ktLSPoSLod3Ph15368xdAC534Ct72cmv3yiicBe2JtHmb5ZJIiFrNSeRLhp53Kl6nu%2FZwUCGdnWMSyaZZdEWNgaoPxvBGltp%2BF7%2FB2j4ZsUqVR%2B%2FyNOjsjROfdr2TAV9R4FeASQHDWd1BNLghsI5VErxC1Edgrahu9SKoWbsH8cbv90glYQ8lzq97NETIFtLNpDINg1OtGj1SGo1XVYojZXMyg5Mu%2BojNCD%2BXQqoRnKjZeKIFMIVvp7Y%2Bg%3D%3D%7Ctkp%3ABk9SR8q3iJ7bYw)
That means I could put the video card in X16_4 slot freeing up one x16 slot in the HBA's & video / GPU configuration listed above

Either way of booting Linux both options is still faster than a spinning sata drive. 

Thinking this through as I type all of this I'm wondering if the safest bet wouldn't be the Enterprise SSD Sata configuration versus the NvME M.2, even though the NvME would be blistering in speed. 
Remembering I'm talking boot devices not the ZFS vdev's drives here.
Thoughts and which way would you lean?

P.S. I'm not whining over the loss of the X16 slot as I honestly don't think it will affect me down the road.

---

### Post by sgt-mike on 2024-09-13
Just a update ... 
Life has put a temp hold on the completion of this NAS. BUT now the project NAS is trudging forward.
I had to do a bit of repair on the case, installed the PSU (1000 watt), the Motherboard, located /installed a missing I/O shield, NvME drive (256 GB for the base operating system). 

As of this writing I'm awaiting the CPU Cooler arrival which should be here in the next 48 hours as it has been shipped. 
Then I can install the operating system after that add another 200mm fan to the case, add the missing 3.5" drive caddy, increase the existing 4GB Ram to 64 GB, then populate the first array with drives still torn between SATA or SAS for the first array (zpool). I'm leaning toward 5 drives, I have not settled on 4 TB each or just go 8TB each drive. I really like the idea of the 8TB each. 

Reality (Time / cost, mostly time) will probably dictate SATA 4TB for each drive for the first zpool, but a SAS ZFS array will be installed into a different zpool. 

[B]UNLESS....

[/B]As a thought in the mean time I could rob the Universal Media Server's drives and enclosure and set them up to practice with ZFS. As that is a system not in use right now, I replaced it with a separate headless Plex Server for my Media which is performing better with the differing TV's in the house hold. (which even that system will be updated to a faster than a 2nd gen i7, which I will move that system to serving a RV vs the house)

That idea will allow me to play with that setup then tear it down when the actual drives I want to install purchase / arrives. Which if I go that route , it will change the drives in the true actual first (zpool) array to 8TB SAS drives, as the enclosure from the UMS server only supports 6 thin 2.5" SATA drives.

---

### Post by sgt-mike on 2024-09-16
Finally got the parts needed to crank up and install the base operating system on the NAS/NFS.

What I will order this upcoming week is the LSI SAS HBA, cabling, a lot of five 4TB SAS drives (located them at a great price). 
Edit (9-16-2024) add --- aggh they sold before I could buy them so I located a lot of three at the same price as the lot of 5 , so I ordered 2 lots in order to get 6 drives

I went with the idea to use the SATA ports in a 6 bay 2.5" enclosure utilizing some old scrub drives (500GB laptop drives) to set up a zpool as temporary test.
Just to see what ZFS is like and work out idea's before.[U] I will destroy this pool soon as it was just a test before getting the actual drives I intent to use
[/U]But thus far it does pose a question I have that I will post in another thread in a day or so, as it deals with pool creation not hardware.
```

mike@beastie:~$ zpool iostat -vl teststore              capacity     operations     bandwidth    total_wait     disk_wait    syncq_wait    asyncq_wait  scrub   trim
pool        alloc   free   read  write   read  write   read  write   read  write   read  write   read  write   wait   wait
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
teststore   1.34T   947G      0    239  2.84K  39.9M   30ms    7ms   30ms    3ms    1us    1us    4us    3ms   52ms      -
  raidz1-0  1.34T   947G      0    239  2.84K  39.9M   30ms    7ms   30ms    3ms    1us    1us    4us    3ms   52ms      -
    sda1        -      -      0     49    564  7.98M   30ms    6ms   29ms    3ms    1us    2us    1us    2ms   28ms      -
    sdb1        -      -      0     49    623  7.98M   30ms    7ms   30ms    3ms    2us    1us    1us    3ms   62ms      -
    sdc1        -      -      0     49    575  7.98M   30ms    6ms   29ms    3ms    1us    1us   16us    2ms   50ms      -
    sdd1        -      -      0     45    573  7.98M   32ms    8ms   31ms    4ms    1us    1us    1us    4ms   60ms      -
    sde1        -      -      0     46    572  7.98M   30ms    7ms   29ms    4ms    1us    1us    1us    3ms   63ms      -
----------  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
mike@beastie:~$ zpool list
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
teststore  2.27T  1.34T   947G        -         -     0%    59%  1.00x    ONLINE  -
mike@beastie:~$ zpool status
  pool: teststore
 state: ONLINE
  scan: scrub repaired 0B in 00:00:26 with 0 errors on Sun Sep 15 07:19:36 2024
config:


        NAME        STATE     READ WRITE CKSUM
        teststore   ONLINE       0     0     0
          raidz1-0  ONLINE       0     0     0
            sda1    ONLINE       0     0     0
            sdb1    ONLINE       0     0     0
            sdc1    ONLINE       0     0     0
            sdd1    ONLINE       0     0     0
            sde1    ONLINE       0     0     0
        spares
          sdf1      AVAIL


errors: No known data errors
mike@beastie:~$
mike@beastie:~$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0  63.9M  1 loop /snap/core20/2105
loop1         7:1    0  63.9M  1 loop /snap/core20/2318
loop2         7:2    0    87M  1 loop /snap/lxd/27037
loop3         7:3    0    87M  1 loop /snap/lxd/29351
loop4         7:4    0  40.4M  1 loop /snap/snapd/20671
loop5         7:5    0  38.8M  1 loop /snap/snapd/21759
sda           8:0    0 465.8G  0 disk
&#9492;&#9472;sda1        8:1    0 465.8G  0 part
sdb           8:16   0 465.8G  0 disk
&#9492;&#9472;sdb1        8:17   0 465.8G  0 part
sdc           8:32   0 465.8G  0 disk
&#9492;&#9472;sdc1        8:33   0 465.8G  0 part
sdd           8:48   0 465.8G  0 disk
&#9492;&#9472;sdd1        8:49   0 465.8G  0 part
sde           8:64   0 465.8G  0 disk
&#9492;&#9472;sde1        8:65   0 465.8G  0 part
sdf           8:80   0 465.8G  0 disk
&#9492;&#9472;sdf1        8:81   0 465.8G  0 part
nvme0n1     259:0    0 238.5G  0 disk
&#9500;&#9472;nvme0n1p1 259:1    0     1G  0 part /boot/efi
&#9492;&#9472;nvme0n1p2 259:2    0 237.4G  0 part /

```

During the initial operating system setup I did have a few small challenges which was easily overcome. Luckily I updated the Bios prior to spending any time trying to install the operating system on the NVMe 128gb drive. As I originally only had 4GB of Ram, I quickly upgraded to 32 GB Ram. Right after that when installing the SATA drive I noticed it seems that when the X99-A has NVMe installed it disabled SATA P1 and P2 thus losing two ports, just like MAFoEffen mentioned some boards do. Which is not a issue or compliant. merely a observation. Right now I'm extremely happy with the outcome thus far

[SIZE=4][U][B]All in all this has been absolutely great which I cannot thank @MAFoEffen  enough with the guidance on the main board, processor, case and the detailed listing of components. 
Which I may have strayed from the exact LSI HBA. I think, but the one I have in my cart is a LSI 9300-16i 16 port, which should be close. [/B][/U][/SIZE]

---

### Post by sgt-mike on 2024-09-24
Ok a Update on the progress.

The HBA I had ordered arrived last week was DOA.... no bios screen after post..... nothing. Even when I attempted to find the HBA using multiple methods via CLI nothing kapoot.

 I then went through the return process with them, now waiting on a refund. But in the meantime I'm still down with six 4 TB sas drives that I can't do anything with right now. 

So this past weekend I war gamed out how to quickly fix this. So this  past Monday, I felt generous and decided to give that same vendor a chance at redemption I made a offer although extremely low for two of the same LSI 9300-16i HBA's in the hopes of a good one. Waited 20 hours which brings us to today ...nothing  ... crickets  frustrated I canceled the bid and then placed a order.
so I ordered via ebay:
1- LSI 9003-8i
1- LSI 9003-16i
and a 15 pin 5 drive extension cable (right angle) because when using either the sata power connection or even a straight extension I can't close the case ( my connection between the HBA to drives in the internal 3.5" bays is currently SFF-8643 to SFF 8482 breakout cable which requires the sata power connection). 
Cost was around $58.00 would have been a little bit cheaper if I lived in a state that didn't collect taxes on online sales.

My thought was if the 16i that I ordered today didn't work and the 8i did I could at least check out the drives and re-format them to 512 if need be until I can get a working 16i. 
If both work great I have a spare HBA on hand. 

--------- now in my searching I found a cooler master haf 932 case on auction, which currently doesn't seem to be any activity on but there is still 6 days on it------------
 which is bigger than my current case (haf922) by 1 external 5.25" bay , I need to win that thing which I 'll switch the NFS server (Beastie) into it

That bring me up to this a plan I hatched, currently my media server is old HP 8200 elite ultra - slim with a i7-second gen, works fine for a portable and in the house as a media server. 
But I could re-do this build setup for a replacement media server (here is where the haf 922 comes in, use same processor and motherboard except add a Nvida GPU vs a simple video card)  for the house and move the HP to the RV. 

In my mind there are several up sides in this route ,matching components for both servers except video cards and of course at least a 1200 watt PSU.
But that means I could use the bay's of the haf 922 case (5-5.25" external & 5-3.5" bays internal, as well as the HAF 932 6-5.25" & 5-3.5" drive bays) to host drives to Beastie (the NFS server) effectively almost doubling the cases drive capacity of the HAF 932 case.
 
(now before anyone comes with OHHHH the drives spinning up at the same time I hope all realize that most if not all sas expander cards support staggered spin up, I know that the ones I'm planning on using do support that)

That will change the way I was intending to use the NAS/NFS server to a degree. As Beastie would be used as a true NFS hosting the media to the media server. ( which would only need the 128 gb NVMe drive on the media server)  and run 24/7 versus my intended just when needed.  
Not that I couldn't do the same with the HP, and yeah I could add a mxm nvida card to the HP to use the GPU. But I could never get the drive bays of using another tower case using the HP. And the i7 second gen is good it will be over loaded at some point.

---

### Post by asirimahanama on 2024-09-30
If you're looking for assistance and advice with setting up an NFS (Network File System) Server, I recommend considering the **Machinist X99 RS9** motherboard, which provides robust support for server tasks. This motherboard features the LGA 2011-3 socket, offering high compatibility and performance for your server needs.
For optimal performance, ensure that the necessary ports are correctly configured to facilitate smooth data transfer. You can find more details about the **[Machinist X99 RS]("https://www.tuzkuz.com/blog/unleash-the-power-with-machinist-x99-rs9-x99-motherboard-combo")9** and its specifications [here]("https://www.tuzkuz.com/products/machinist-x99-rs9-x99-motherboard-combo-lga-2011-3-set").
If you have specific questions regarding the NFS setup, feel free to ask!

---

### Post by sgt-mike on 2024-10-04
The Asus X99A that was originally suggested is working well. And by that I do mean it does have some quirks that has been noted on this forum, but they are easily worked around. With the exception of RAM currently I have 96 gb, went today to purchase and install another 32 to get up to 128. Bios never showed the presence of the additional ram, stumped I re-installed several times taking great care to ensure that they was seated properly. Bios never showed the additional ram, which left me unsure if the limitation is (a.) the CPU , (b.) that a dimm slot is broken /defective??, (c.) the latest bios from Asus just doesn't address above 96gb. Actually not a problem regardless 96 should more than plenty to do the task, and is 32gb higher than the original listing of 64gb in the manual before the latest bios upgrade was made available. Personally I suspect (c.) bad DDR4 udimm slot. 

Now the latest recommendation of the Machinist X99 board ... it was considered and was thrown out early on. Why you ask ? Simple m-ATX simply too small, and not enough PCI-e slots . As listed 1 -x16 and 2 -x1, totaling 3 PCI-e with only 4 sata ports. And I'm pretty sure when I reviewed it, there wasn't any onboard graphics, so the only PCI-e x16 slot would have to have a graphics card. So where would I stick a LSI 9300-16i HBA?? in a PCI-e x1 huh no, not too sure anyone makes a SAS capable HBA in a PCI-e x1.

Thus a ATX or -ATX format was needed with as much PCI-e x16 slots as possible. 

With saying that I'm no way attempting to be negative nor ungrateful of the suggestion made by  Asirimahanama [COLOR=#000000]*. *[/COLOR]That might work for some others able to accept the boards limitations or be willing to use a SATA HBA in addition to the onboard 4- SATA ports. Now would it work if I wanted to use it to replace my media server absolutely. But early on the choice of a SAS HBA was made for the NFS, that way I could use SAS or SATA drives from the same HBA, and with enough expanders the LSi 9300-16 can address up to 1024/6 drives. Can't recall exactly the number but it's higher than a 1020 drives. 

Also today ordered the hot swap bay drive modules for the Cooler Master HAF 922 case 5 - 5.25" bays. I chose the 3.5" format because I can fit either 3.5" or 2.5" with adapter. That configuration will allow me 7 drives in the 5.25" bays in addition to the internal 5 3.5" bays (12 drives). Now when I attempt to upgrade the Media server I'll steal those bays in that case to externally provide /power drives to the NFS via a expander.
Which is now pretty much built and in service providing files to my current media server. 
Checked the network throughput and at 900 + Mb/s on a 1 Gig network I was happy. 

I'm using ZFS for the soft raid and enterprise class SAS drives. Will need to adjust 1 pool in it's vdev currently in raidz1 x 3 4TB drives, got another 3 4TB's inbound. My goal for that Pool (storage side) was a vdev with a drive of 5 to 10 drives (wide) in raidZ2 or better. Then dedicate 1 or 2 six or eight TB drives as spares to the Z2/3 vdev. That way when I use greater than 4TB drives to expand the pool in the replacing drives and is expanded fully the spare (s) will be big enough to step in the event of a drive failure. Which will also allow me either spares or additions to the stripped pool or create another pool for other data.
Then I have another vdev configures in ZFS as just a simple stripe or raid 0 to feed the media files to the media server, this was just for the read speed as it was a good bit faster than a raidZ1 or Z2 vdev pool. Yes I'm fully aware that configuration offers NO drive loss protection. That is why the same files are in a raidZ1/2/3 vdev pool, which I'm also looking at understanding the ZFS snapshot commands. 
That backup (snapshot) file will be stored on a external drive (s) USB or if need be do to another server for backup is my thoughts. Not sure how much space snapshots take.  <<< this part is where @The Fu advice is sorely sought which is best WoL backup server and / or external USB drive?

---

### Post by sgt-mike on 2024-10-11
Ok I've shifted around on the cases a bit even though the NFS is sitting in a CM HAF 922 right now , which I've already ordered the drive bay modules for 1 -4 drive x3 - 5.25" slot and a 3 drive x 2 - 5.25" totaling 7 drives external plus the 5 internal bays (12 drives). The hotswap external modules fills the available external drive bays very nicely in the 922 case. In the mean time I had procured another additional HAF 922 case for another system.

Then I seen this on auction. Just have to have that case I thought, as in my mind that would be a better option. Six 5.25" external bays visions of 9 drives external modules total plus 5 internal totaling 14 drives danced in my head.
[https://shopgoodwill.com/item/212043031](https://shopgoodwill.com/item/212043031)
Identified by a Goodwill worker as a HAF 942 case incorrectly, it's really a HAF X case. 
My first and foremost thought and action was to procure it because I seen it had 6 slot 5.25" external which would allow me to place 3 - 3 drive x 2-5.25" bay modules supporting 9 drives externally , plus the 5 internal bays totaling 14 drives. 

While waiting on the case to get here on this upcoming monday (14th Oct) I delved a little more into the case design and features once I won the auction. As for the internals I could stick them in a empty 922 case as a media server depending on what is there, and if it's more capable than my present media server.  Now comes the fly in the ointment .
[B]
Only to find out the bottom two 5.25" slots have a X-dock feature, that threw a kink into the case planning[/B]. :shock: 

Kind of ..... I did notice that the X-dock is removable and is SATA only capable not really a downside but won't support my SAS drives. I do have a couple of SATA drives sitting around, so I could transfer the X-dock device to one of the 922 cases (I think). That is if I'm stuck like glue to my original thoughts. OR I could leave it.

As I ponder this before ordering more of the 3 drive module to fill the 6 bays. That X-dock looks like it would be great for transferring files en-mass and should be way faster than over the network or a USB connected drive. The other advantage is use those two X-dock Hotswap bays to store snapshots of the ZFS pools in my back up strategy . Mount them when I need them  unmount when I don't . 
This causes me to re-think my plans, many ways to do this. Like I mentioned I had already ordered the drive modules and they are nested into one of the 922 cases right now waiting on cabling. 
If I leave the X-dock in place I would only need two of the 3 - drive modules , one bay module I can pull from the 922 case, or simply order two for now. 

That would allow the other 922 to be ready to slave it's drive bays to the NFS once I order the expander cards in the future. I could swap one 3 bay drive module from the 922 case to the Haf X and place the Xdock in the 922 and still achieve the same plan. 

(how many SAS drives do I have on hand right now? - 9 -4TB, either way is achievable / supportable, and will be while before I have to go outside the case.)

What would you do with this self inflected plan upheaval ???? I think I have a initial plan just need a nudge. keep the X-dock in or not?
[https://www.overclockersclub.com/reviews/cooler_master_haf_x/](https://www.overclockersclub.com/reviews/cooler_master_haf_x/)

---

### Post by sgt-mike on 2024-10-13
OK update time again:
The HAF X case with it's internals arrive yesterday. Checked the Motherboard / CPU was hoping for a 4th Gen or later CPU.. nope 3rd gen i7 3770K. Pulled the internals out of the HAF X case. Gingerly installed the NFS internals in. Made a choice that the X-dock module was to be pulled out. Upgraded intake and exhaust fans, and temporarily placed the 4 Drive bay module in just to fill the holes. (I'll shift that 4 drive bay module to the media server build in the now spare HAF 922 case, two expanders and the NFS will have access to those drives as well).

So Monday / Tuesday I guess I'll order two more of the Athena Power 3 drive bay modules from New Egg in order to properly fill the external bays up. Leaving me with 5 internal bays free to add more drives when the time arrives. This time I'll go to ebay or something to find a US supplier/shipper for the two more sff 8463 to sata breakout cables. It's flat taking too long for the shipment from China. Yeah I know I'm impatient ( but 30 days WOW, not a problem if they was spares). But maybe the new order and everything will be here when the cabling from China arrives which will be great.

As madscientist  pointed out I'll look at adding either extra fans in a push / pull bracket configuration, or upgrading the fans on the module case before putting the drives to actual work.

Oh I almost forgot the replacement 16i HBA made it here and is working fine so far. Pulled the 8i HBA and put it on the shelf as a backup.

---

