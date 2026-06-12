---
title: "Will my theoretical throughput speed be limited by the server backplane?"
date: 2024-02-08
forum: Server Platforms
---

### Post by Heeter on 2024-02-08
Hi All,

I have a Dell R720 server that I am refurbishing and upgrading. I did some research and found that the PCIe version on the 3 risers are ver3.0.

I got my hands on 8 x 4TB SAS 12Gb/s Hard drives. Also scored a couple of different PERC H730 12Gb/s raid PCIe Ver3.0 from the local used parts shop. One is a 1Gig Cache, other is a 2Gig Cache.

Was thinking about something, will the backplane or the cables be a limiting factor for 12Gb/s? I have no info on the BP that is in the R720 right now.

Does 1Gig cache or 2 Gig Cache Raid card really make a difference?

Regards

---

### Post by Heeter on 2024-02-09
Hi Guys,

Quick update.

Finally found a site that I can input drive throughput testing numbers, have been doing some math and am seeing that this internal PERC H710 mini running on it's dedicated PCIeV3 slot has more than enough bandwidth room for over 32 HDDs in this configuration.

Regards

---

### Post by TheFu on 2024-02-10
If you want greater performance, use SSDs.  There are PCIe cards that will hold 4 NVMe SSDs. Here's one with 4 NVMe slots for $53: [https://www.amazon.com/ASUS-M-2-X16-V2-Threadripper/dp/B07NQBQB6Z](https://www.amazon.com/ASUS-M-2-X16-V2-Threadripper/dp/B07NQBQB6Z)  PCIe v3 x16 adapter. Will work in a x8 PCIe slot too. Four M.2 slots provide up to 128 Gbps of bandwidth for the card.

If you deploy ZFS on the 4TB drives and use a top quality SSD for the ZFS log cache.  Of course, any use of cache will be highly dependent on the workload. With ZFS, it is generally best to add more system RAM.

Always remember with HDDs, there is the actual read speed, the actual write speed, and then there is the theoretical bus bandwidth.  No HDD comes close to the theoretical bus bandwidth since SATA-I or USB2 limitations.  Consumer spinning rust exceptionally turned may get to 200 MB/s, but usually it is 150MB/s or less (1200 Mbps) per drive.  Four of those is still slower than a single gen3 SSD, by far - about a 10x factor.  The very fastest SAS drives top out at 554 MB/s (4400 Mbps), but you don't have those, since they are 20TB. 

There's always theoretical bandwidth and then there's real world. These can be vastly different.

---

### Post by MAFoElffen on 2024-02-12
IFAIK, the ASUS Hyper M.2 X16 PCIe 3.0 X4 Expansion Card requires a motherboard with bifurcation. And they are picky which slot it resides in. The R720 does not have have bifurcation capabilities.

But... Both my server and my workstation, I have these cards in them, which have onboard bifurcation: [M.2 Key SSD Expansion Card ANM24PE16 4-Port PCIe3.0 X16 With PLX8748 Controller]("https://www.aliexpress.us/item/3256801158360351.html?spm=a2g0o.order_list.order_list_main.11.69f71802aJejuT&gatewayAdapt=glo2usa")
The limitation is on the PCIe Gen 3 bus. That is 16GBs for x16, which is rated at 1 GBs per lane. I have a T720 which supports 24 SAS drives, plus 2 3.5" HDD's, internally on the internal SAS backplane of the PERC Card... To add the extra 2 drive, I used the drive expansion kit from on of my T2400s.

I config/run them all as single RAID 0 arrays in the PERC, to pass the single drives through, because those PERCs do not do JBOD... then use them as ZFS RAIDZ3 members. There is a BIOS Hack flash image to convert PERC RAID Cards into HBA's... So you can just do JBOD with them and use them as HBAs.

EDIT: Watch which PERC Cards you have... Mine are limited at a 2TB max size per drive. Anything larger gets recognized as only 2TB. Newer PERC Cards support the larger drives. And that is NOT published clearly in the specs. I had to find out the hard way, by it not working as I expected it to, and having to ask on the Dell EMC Support.

---

