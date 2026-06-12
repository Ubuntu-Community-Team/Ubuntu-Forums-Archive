---
title: "apt-mirror - Memory isn't freed up upon completion."
date: 2007-10-21
forum: Server Platforms
---

### Post by chris.zeman on 2007-10-21
I created an Ubuntu mirror on our local server so I can easily deploy (what I hope will be) 50-100 Ubuntu workstations in an energy-management control system at work. My memory usage went to about 96% during the mirroring process, which seems logical, but the memory wasn't freed up once the process had completed. I let it go for about a day but the memory usage stayed at 96% until I finally rebooted the server.

I just ran the daily apt-mirror cron job twice to see what the memory usage would end up at, and it jumped from about 12 to 23% on the first run. It stayed at 23% for the second run, and none of the memory has been freed up yet. Is this a bug or just something I might be doing wrong?

I don't know if the server specifications matter or not, but I'll err on the side of caution and make sure I include any potentially helpful information.
```
Processors 1 
Model Intel(R) Pentium(R) 4 CPU 1.80GHz 
CPU Speed 1.79 GHz 
Cache Size 256.00 KB 
System Bogomips 3590.36 
PCI Devices - Ethernet controller: Intel Corporation 82801DB PRO/100 VE 
- Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface 
- IDE interface: Intel Corporation 82801DB 
- ISA bridge: Intel Corporation 82801DB/DBL 
- Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM 
- PCI bridge: Intel Corporation 82801 PCI Bridge 
- (3x) USB Controller: Intel Corporation 82801DB/DBL/DBM 
- USB Controller: Intel Corporation 82801DB/DBM 
- VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device 
 
IDE Devices none 
SCSI Devices - ATA WDC WD1600BB-56R (Direct-Access) 
- ATA WDC WD1600BB-56R (Direct-Access) 
- COMPAQ CD-ROM LTN486S (CD-ROM) 
 
USB Devices none 

Type                  Percent Capacity      Free           Used           Size 
Physical Memory                   23%      1.52 GB      462.01 MB      1.97 GB 
- Kernel + applications            8%                   168.66 MB   
- Buffers                          4%                    73.83 MB   
- Cached                          11%                   219.52 MB   
Disk Swap                          0%      5.78 GB        0.00 KB      5.78 GB 

```

Thank you,
Chris

---

