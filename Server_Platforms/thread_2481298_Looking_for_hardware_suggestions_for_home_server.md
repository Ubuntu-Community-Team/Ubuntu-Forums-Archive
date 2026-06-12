---
title: "Looking for hardware suggestions for home server"
date: 2022-11-24
forum: Server Platforms
---

### Post by LHammonds on 2022-11-24
Looking for suggestions for existing hardware systems out there that might fit these requirements:


[LIST]
[*]Capable of running Ubuntu 22.04 LTS operating system 
[*]Efficient power use (ability to power up/down inactive data drives) 
[*]Quiet as possible 
[*]No powerful GPU needed (no GUI will be used) 
[*]Internal drive for OS can be SSD at least 50 GB 
[*]Capability for two external storage for primary data & backups (USB or eSATA) 
[*]Not cost prohibitive - $600 max budget 
[/LIST]

It should be a general-purpose server capable of running as a dedicated database server or a web server or for media streaming, etc.   A Raspberry Pi probably won't cut it.

EDIT: 2022-11-29

I didn't want to piecemeal build anything since its been a while since I last did such research and it usually takes me a long time to get re-acquainted with what pieces works best with other pieces and so on.

I went with the ATOPNUC MA90 + 4TB SSD Crucial MX500.  It has been ordered and is on the way.  $200 below budget. ;)

EDIT: 2022-12-24 - Apparently Amazon mislabeled the size of the MX500 as 4TB when in reality it was 250 GB.   So....apparently NOT gonna be $200 below budget. ;)

Will post here is there is anything interesting about other than "it just works" since we will assume that to be the case (no pun intended).

Topic marked as SOLVED.

Thanks for all the info/suggestions.
LHammonds


Thanks,
LHammonds

---

### Post by TheFu on 2022-11-24
By default, a minimal GPU is needed to boot any Ubuntu Server or Desktop release.  It is possible to specify console-only access, but that cannot be done without a minimal VGA-capable GPU.  It is easier to have one, even if it is the lowest of the low-end GPUs.  

My router doesn't have any GPU. It has a low-power AMD GX-412TC 64-bit CPU (12W). To install and setup anything, I found a BSD release that was pre-setup for serial console support. No Ubuntu Server or Desktop would work without modifying the boot parameters before booting.

I can't help with the other stuff. 22.04 is too new for me, though I do have a few play VMs with it. We both know, that's very different than on real hardware.  

**Deals and thoughts for today:**
BTW, for $120, a Ryzen 5 5600g (both Amazon and Microcenter) provides nearly 20K passmarks of performance and an integrated GPU that is faster than an nvidia 1030GT/ DDR5 GPU.  
Also, the WD Black 8TB HDD (5 yr warranty) is cheap ($140) today and tomorrow (BestBuy and directly from WD's online store and WD_BLACK™ Amazon store ).  None of my WD-Black drives have failed or even shown any relocated sectors in over 10 yrs of continuous use. For example: Power_On_Hours 109706 (12.52 yrs)!  Talk about getting my money's worth from storage!  I'm looking to replace it because at 1TB, it is eating a SATA port with too low capacity.

The Ryzen 5600G doesn't support DDR5 nor PCIe 4x, which keeps the price down. 3x PCIe is plenty fast, IMHO.  I have twin Asus B450 ROG Motherboards with intel NICs.  I'd probably get an Asus B550 today to pair with the Ryzen 56xx (65W), being certain to get the Intel 2.5Gbps NIC, not the Realtek variant. Since I switched from higher power use CPUs, the household electric bill shows the savings each month. I expected about $5/month in savings going from a 125W --> 65W CPU, but it is much more than that. We have about US average electric pricing here. Last month was $63.88 for the entire house. I paid more 20+ yrs ago living in a small 1 brd apartment just a few miles from here.  That's with 4 computers on 24/7 and over 40TB of storage, but multiple networks. 

Those 2 are black Friday deals. Actually ordered both already.  There are cheaper HDDs on a TB/$ basis, but the entrance price was 2x higher and she-who-must-be-obeyed wouldn't let me spend more in total. ;)  [https://edwardbetts.com/price_per_tb/](https://edwardbetts.com/price_per_tb/) has daily updates for NewEgg storage prices. There are similar pages for Amazon and other online retailers.

As for turning off HDDs.  I think that depends on the HDD capabilities.  I'm not a fan and actively take steps to keep the HDDs spinning 24/7/365. I believe that spinning up and down causes more wear than spinning constantly all the time. There are different opinions on that.  I do know that some external WD USB drives always spin down and that those don't last as long, plus accessing anything on those devices seems to have a 20sec delay if they have to power up.  If you are going to make the server a NAS too, then the WD Red Plus and Pro are worth looking at.  The "Plus" is 3 yr warranty. The "Pro" is 5 yr warranty, but known to perform worse except for RAID0 or RAID1. Avoid RAID 5/6 with the "Pro" according to the reading I did today.  I'm trialing some WD-Gold used drives now.  It has been about 18 months on 3 of those - after some arrived with reallocated sectors, which I immediately returned, the replacements were all clean and have been working well with no SMART errors. These were $45 for 4TB Gold drives, which was hard to pass up. YMMV.

If I'm selling the system and the client is extremely cost focused, then I'd get some 3 yr warranty crap drives for data and a lower-tier $50 SSD for the OS. Those should last at least 3 yrs.  I want 5+ yrs from every storage device and probably won't replace the computer CPU/RAM/MB for 10 yrs.

---

### Post by LHammonds on 2022-11-25
Thanks for the info.   The guy has a Dell PowerEdge 2850 with six 73 GB drives which are no longer any good.  I either have to get replacement drives for it or get a newer system.  He already has two 4TB external USB 3.0 drives used for data and backup.

If I can get a new system that is quiet, less power-hungry AND capable of holding all his data, it would be a win-win situation.  My budget is $600.

I've lived in the virtual machine world for so long, I am out of touch with current single-machine servers. ;)

This is what I have found so far:

$499 - [HUNSN IM03-I5 4200U-16G128G1TB Industrial Mini PC](https://www.newegg.com/p/1VK-01U9-009D8)
 * Intel Core I5 4200U 1.6 GHz
 * 16 GB RAM DDR3
 * 128 GB mSATA SSD
 * 1 TB HDD
 * 1x VGA
 * 1x HDMI
 * 1x Gigabit ethernet port
 * 2.4G/5G Dual Wifi / Bluetooth 4.0/4.2
 * 4x USB 3.0
 * 2x USB 2.0
 * Fanless (100% quiet)
 * 5.5 lbs
 * Power consumption: 15W
 * First available: April 16, 2019

$115 - [ATOPNUC MA90 mini computer](https://www.newegg.com/atopnuc-amd-a9-series/p/2SW-007N-00007)
 * AMD A9 9400 3.2 Ghz
 * 8 GB DDR4 RAM
 * 128 GB SSD M.2 SATA3
 * can extend with a single 2.5" internal SATA3 HDD/SSD
 * 1x gigabit ethernet port
 * 2.4G/5G Dual Wifi / Bluetooth 5.0
 * 2x HDMI
 * 2x USB 3.0
 * 2x USB 2.0
 * Fanless (100% quiet)
 * Weight: 0.66 lbs
 * Power consumption: ?W
 * First available: November 11, 2022

$563 - [Meerkat 11th Gen Intel](https://system76.com/desktops/meerkat#specs) by System76
 * Intel i3-1115G4 4.1 GHz
 * 8 GB DDR4 RAM (64 GB Max)
 * 500 GB M.2 PCIe Gen4 NVMe
 * can extend with a single 2.5" internal SATA3 HDD/SSD (if you selected tall case)
 * 1x Gigabit ethernet port
 * Wifi 6 / Bluetooth 5.2
 * 1x HDMI 2.0b
 * 1x Display Port 1.2 via USB 3.1 Type-C (Thunderbolt)
 * 3x USB 3.1 Type-A
 * Power consumption: 90W
 * First available: 2017?

$319 - [Beelink 8th Gen Mini PC B08PBKLNKG](https://www.amazon.com/i5-8279U-Processor%EF%BC%88up-4-1Ghz%EF%BC%89-Beelink-Ethernet/dp/B08PBKLNKG/ref=sr_1_11)
 * Intel i5-8279U 4.1 GHz
 * 16 GB DDR4 RAM (32 GB Max)
 * 500 GB M.2 PCIe NVMe SSD (2TB Max)
 * Wifi 5 / Bluetooth 5.0
 * 2x HDMI
 * 1x Gigabit Ethernet port
 * 4x USB 3.0
 * 1x USB 3.1 Type-C (Thunderbolt)
 * Weight: 1.28 lbs
 * Power consumption: 57W
 * NOTE: Comes with Win11 Pro pre-installed

$270 - [4TB SSD Crucial MX500](https://www.newegg.com/crucial-4tb-mx500/p/N82E16820156282)

Thanks,
LHammonds

---

### Post by TheFu on 2022-11-25
You couldn't pay me to use a PowerEdge 2850. That's from 2005-ish - it is loud and power hungry.  Heck, get 2 Ryzen 5 desktops and have them use block replication between primary and secondary systems.  If he wants to pay for new to get warranty storage, fine.  $600 isn't enough for 2 systems, but it will easily get 1 - probably for $450-ish assuming he doesn't have a case and PSU lying around.

Do you have a Microcenter nearby?  They drop at least $20 off on a MB+CPU bundle.  

Or do you prefer ordering from a single provider - say Amazon?  I bet in 15-30 minutes, we can come up with a config around a ryzen 5600g.    [https://pcpartpicker.com/list/3h6Kgb](https://pcpartpicker.com/list/3h6Kgb) is a start.  No CPU fan is needed, it is included and works fine.  This is a 19800 passmark systemhttps://www.cpubenchmark.net/cpu.php?cpu=AMD+Ryzen+5+5600G&id=4325  with 32GB RAM, good NVMe, 3 Intel Network ports (2.5Gbps & 2x1Gbps),  Add an ATX case and probably pick a different Seasonic 500W PSU.  Seasonics are quiet and have worked for a long time here - over a decade easily.  PCPartPicker says it is $590, but that's much too high with the deals today and you likely have other stuff that can be reused.   I have the same G.Skill 3200Mhz RAM in my Ryzens. Works well, provided the set is matched.  $85 for 32GB?  Wow.  I should get some new and sell my lower capacity DDR4 RAM.  I like to use Intel NICs for many reasons and actively avoid Realtek.
No GPU needed thanks to the built-in Radeon in the 5600G.  Not high end, but saves spending $180 on a GPU and will easily handle server needs, including 4K video playback.

For 100% redundancy, build two. Better than a server with dual PSUs.  Plus, they sip power in comparison and would be 5x faster, if not more with a 1TB NVMe inside.
It would be worth reading the B550 motherboard manual to see how the the m.2 slots can be used.  There are some limitations depending on NVMe/SATA choice and if a 16x GPU is added.  Also, only has 4 internal SATA ports, so I added an eSATA-PM adapter to hook up an external array.  Internal, I'm using a cheap Roswell plastic 4 drive hot-swap cage that fits in 3x5.25in ports that most mid-tower cases provide.  After a year, the Roswell fan started making noise, so it was swapped with a very quiet Noctua fan. I'm addicted to these front-loading drive-swap cages.

---

### Post by TheFu on 2022-11-25
Those CPUs aren't up to the task of transcoding video as needed, which is likely in a home.  Say you have 4K BluRay and want to play it on a 1080p device. Transcoding from h.265@4k to h.264@1080p is required.  All the other stuff for the NAS and VMs would be fine on almost anything these days. It really is the Plex or Jellyfin transcoding that pushes the CPU.

BTW, my post with 32G of RAM seems like overkill. 16G would be fine.

* AMD A9 9400 is 1300 passmarks.  You'd hate life on that system.  It is slower than a $200 chromebook from 2012.
* Core i5-4200U is 2000 passmarks.  Meh.

Maybe some information on the specific workloads would be helpful?  I replaced a 3500 Passmark system with that Ryzen due to transcoding issues ... and lifetime problems were just starting to happen.  Heck, if you can pick up the MB+CPU+RAM, you can have it.  It has a P45-DS3L MB, broken realtek Gige NIC, and a Pentium G3250 [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3250+%40+3.20GHz&id=2346](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3250+%40+3.20GHz&id=2346) - appears the passmark team as re-worked all their numbers. It isn't 3500 anymore - Just 1900 now.  I had the wrong passmark version in my mind. They seem to change annually and break any prior memories.

A new Core i3 would be cheap and fast, BTW.  Same for a Ryzen 3 5300g around $99 (the 5600G is $120 today for 50+% more performance) [https://www.cpubenchmark.net/cpu.php?cpu=AMD+Ryzen+3+5300G&id=4392](https://www.cpubenchmark.net/cpu.php?cpu=AMD+Ryzen+3+5300G&id=4392) is 13000 passmarks.

I'm pushing more capable CPUs, since nobody complains that something is too fast.

---

### Post by LHammonds on 2022-11-25
As far as I know, the server is primarily for media storage and sharing via NextCloud with a handful of family members.  That means MariaDB, Apache and maybe the talk app.

Don't think it will be doing Plex or transcoding to TVs.

While researching this hardware, it gives me ideas for cheap, distributed TV-attached units for use with Xibo (a free signage system)

LHammonds

---

### Post by TheFu on 2022-11-25
I run Nextcloud with Talk.  If they use video streaming, more power is needed, but not much.  Before using Talk, I had a play version of NC on a r-pi v2. Worked fine with NFS storage for most of it.  We'd get 6 people into the same audio chat without problems.  When I moved it to a Pentium, anything was possible.  That G3250 system was $126 for the MB, CPU, and RAM in 2015.  

I was moving from an AMD E-350 APU and pulled the 4TB HDD out and dropped it into the Pentium system.  The E350 APU just didn't provide sufficient performance for my NAS, Calibre, Nextcloud, Wallabag stuff.  At the time, I started using it for NFS to serve media around the house too.  the main needs was really GigE networking.  

About a year ago, I was forced to split Wallabag from the Nextcloud VM due to divergent software stacks.  Wallabag ended up inside an LXD 20.04 container with the required versions of mariaDB and php.  NC is still in the same KVM-VM.  I need to move nextcloud into a 20.04 container when I move from 18.04 soon.   For internal needs, I'm loving lxd managed containers, but they don't like my NFS mounted HOME directories.  As a work-around, I create a local deployment account for managing LXD stuff.  Really shouldn't need this, but sigh ... the snap package team doesn't listen and lxd is only provided as a snap.  LXD/lxc containers are almost like separate VMs, but 10x less overhead and much faster.  Plus, containers work with any Linux kernel since 2.6 and don't have specific hardware requirements.  Only stuff like VPNs can't go into a container.  Anything tied to kernel modules will require disabling the primary security aspect of Linux Containers which is running a virtual root account that typically has zero privileges on the host system.  Sadly, Docker containers don't do this by default. Docker does make it possible to create root-less containers with extra effort.  LXD does this by default.

---

### Post by LHammonds on 2022-11-25
I'm really leaning towards the ATOPNUC MA90 for $115 and getting the $270 4TB SSD so internal storage can hold the data and the external USBs are 100% backup only.

That would be less than $400 for a functional replacement for the Dell PowerEdge...but without the RAID and without the jet power engine noise and without the excessive energy costs. ;)

LHammonds

---

### Post by ian-weisser on 2022-11-25
> **TheFu said:**
> LXD/lxc containers are almost like separate VMs, but 10x less overhead and much faster.

I really like LXD performance. I have containers for a Minecraft server, NextCloud server, NAS, backups, media server, home automation, and a couple experimentals...all running on a 10-year-old motherboard and a teeny little Phenom II CPU. And each behaves like an ordinary, independent server that I already know how to use.

As I prepare to migrate that server to the next generation of hardware, I'm thinking about consolidating down to a 4-year-old laptop motherboard for it. The motherboard outlasted the plastic case. Far more powerful, sips power, and doesn't even need a fan. I'm considering putting Ubuntu Core on it, since all my services are containerized anyway.

---

### Post by #&amp;thj^% on 2022-11-25
> **ian-weisser said:**
>  I'm considering putting Ubuntu Core on it, since all my services are containerized anyway.
Sorry for the drive by but, @ian-weisser could you keep us posted when this all comes together, I and others as well find it very user friendly to see proven applications at work. (Helps with the right choice making)
I follow a few Users here and you are near the top for relevant and correct information provided.
No pressure just a thought.

---

### Post by mIk3_08 on 2022-11-25
> **LHammonds said:**
> As far as I know, the server is primarily for media storage and sharing via NextCloud with a handful of family members.  That means MariaDB, Apache and maybe the talk app.
Don't think it will be doing Plex or transcoding to TVs.
While researching this hardware, it gives me ideas for cheap, distributed TV-attached units for use with Xibo (a free signage system)

LHammonds How about the dual socket motherboard will you still consider to build one for your home server? Though this is a bit pricey but you will be contented with the performance. Anyway this is just my suggestion. There are also some I saw on the web that is cheap and affordable but the quality, I don't know yet. Hope it give you an idea. Regards and cheers.

---

### Post by MAFoElffen on 2022-11-26
I just went through this myself... In the past I always had Server Metal. I have 3 Dell 2900's, a T440 and a T740. They used lots of power, sounded like aircraft taking off with all the fans, and took forever to get through the server startup checks. Then I went to a MicroServer Board for a Optiplex 6420 workstation. Used less power, was not as noisy, but still had quite a few server check booting.

I planned for something else this time. Took my time and collected parts, when I could save up for them. Intel socket LGA1200 mini ITX footprinted board. Intel i910900 (integrated graphics). Very small footprint. Very quiet. Doesn't take much power. Lots of USB 3.2 ports. An 1TB NVME drive. an 500GB SSD and an 8TB SATA. I'm happy.

---

### Post by mIk3_08 on 2022-11-26
> **MAFoElffen said:**
> I just went through this myself... In the past I always had Server Metal. I have 3 Dell 2900's, a T440 and a T740. They used lots of power, sounded like aircraft taking off with all the fans, and took forever to get through the server startup checks. Then I went to a MicroServer Board for a Optiplex 6420 workstation. Used less power, was not as noisy, but still had quite a few server check booting.

I planned for something else this time. Took my time and collected parts, when I could save up for them. Intel socket LGA1200 mini ITX footprinted board. Intel i910900 (integrated graphics). Very small footprint. Very quiet. Doesn't take much power. Lots of USB 3.2 ports. An 1TB NVME drive. an 500GB SSD and an 8TB SATA. I'm happy. Thanks for sharing MAFoElffen. Idea saved already. Again, Thanks a lot. Regards and cheers

---

### Post by aljames2 on 2022-11-26
A few years back I built a small box to be my pfSense router.  This all cost $170 at the time.  Not overkill, small footprint (but not NUC small), low power, quiet:

ASRock J3355M Intel Dual-Core Processor J3355 (up to 2.5GHz) Micro ATX Motherboard / CPU Combo

Crucial Retail Package 8GB (2 x 4GB) DDR3L 1866 (PC3L 14900) Desktop Memory Model CT2K51264BD186DJ

Rosewill - Black & Silver, 0.8mm SGCC Steel Slim Micro ATX Computer Case with ATX12V Flex 300W Power Supply - R379-M

---

### Post by mIk3_08 on 2022-11-26
> **aljames2 said:**
> pfSense router.  Thanks aljames2 for the reminder. Security is very important. Security is very hard and complicated but even a small and tiny piece device can help. And of course Linux Ubuntu community is aware of it and that is their primary priority. Regards and cheers.

---

### Post by LHammonds on 2022-11-29
I didn't want to piecemeal build anything since its been a while since I last did such research and it usually takes me a long time to get re-acquainted with what pieces works best with other pieces and so on.

I went with the ATOPNUC MA90 + 4TB SSD Crucial MX500.  It has been ordered and is on the way.  $200 below budget. ;)

Will post here is there is anything interesting about other than "it just works" since we will assume that to be the case (no pun intended).

Topic marked as SOLVED.

Thanks for all the info/suggestions.
LHammonds

---

### Post by TheFu on 2022-11-29
> **aljames2 said:**
> A few years back I built a small box to be my pfSense router.  This all cost $170 at the time.  Not overkill, small footprint (but not NUC small), low power, quiet:

Around 2015, I got a PCEngines APU2 for pfSense.  $140 for the SBC, case, PSU. I added an SDHC card to run it for about a year, but upgraded to an mSATA SSD later.  Also switched from pfSense to OPNSense 3+ yrs ago.  The APU2: [https://www.pcengines.ch/apu2.htm](https://www.pcengines.ch/apu2.htm)  I have the 4GB of RAM version - 3 Intel GigE NICs.  My home NFS system running Nextcloud was on completely different hardware, but never used more than 3GB of RAM.  12W max power draw. Fanless.  AMD-v supported.  These SBCs are industrial devices. The metal case is part of the CPU cooling solution.
Since COVID, supplies have been limited, but they are expecting new versions to be available in the next 2 weeks. Some models have SPF network connectors to support lengthy optical cable runs.
If more ports are needed, add a cheap switch for each of the 3 LAN ports on the APU2 device.  I'm using (3) 8-port switches to have physically separate networks, but have the router do firewalling between each and to the internet.

---

### Post by #&amp;thj^% on 2022-11-29
> **TheFu said:**
> Around 2015, I got a PCEngines APU2 for pfSense.  $140 for the SBC, case, PSU. I added an SDHC card to run it for about a year, but upgraded to an mSATA SSD later.  Also switched from pfSense to OPNSense 3+ yrs ago.  The APU2: [https://www.pcengines.ch/apu2.htm](https://www.pcengines.ch/apu2.htm)  I have the 4GB of RAM version - 3 Intel GigE NICs.  My home NFS system running Nextcloud was on completely different hardware, but never used more than 3GB of RAM.  12W max power draw. Fanless.  AMD-v supported.  These SBCs are industrial devices. The metal case is part of the CPU cooling solution.
Since COVID, supplies have been limited, but they are expecting new versions to be available in the next 2 weeks. Some models have SPF network connectors to support lengthy optical cable runs.
If more ports are needed, add a cheap switch for each of the 3 LAN ports on the APU2 device.  I'm using (3) 8-port switches to have physically separate networks, but have the router do firewalling between each and to the internet.

Just ordered but on back order this little beauty: [https://corpshadow.biz/combo-kits/apu2d4-black-combo-kit#/9-enclosure_type-not_labelled/145-memory_storage_-none](https://corpshadow.biz/combo-kits/apu2d4-black-combo-kit#/9-enclosure_type-not_labelled/145-memory_storage_-none)
My set-up is close to the way you set-up, close but not identical, Firewalls, Load Balancer, VPN-Router. 
I'm glad LHammonds is good sport here.

---

### Post by MAFoElffen on 2022-12-01
Alibi...

As I got in an Amazon order this morning, a tip I take for granted because I have done this for all my machines for the past 13 years... I buy 6" USB extensions for all my front USB ports. 3' USB extensions for all my back USB ports. If a server board has onboard USB ports, I run them outside the case with a USB extension cable. I mark all my cables. (It's a habit.)

These serve two purposes. I'm getting older, and getting harder to get under desks and behind server racks. These make it easy to get to ports. The most important thing, is that plugging things into these extension cables saves the pins in the USB ports of the actual machines.

---

### Post by TheFu on 2022-12-01
> **MAFoElffen said:**
>  
These serve two purposes. I'm getting older, and getting harder to get under desks and behind server racks. These make it easy to get to ports. The most important thing, is that plugging things into these extension cables saves the pins in the USB ports of the actual machines.

Which is why my rack is on wheels and has only 3 external connectors - 2 power and 1 COAX for the ISP.  Everything else self-contained on the rack.  Ok, perhaps not everything.  There are 2 GigE network cables that go into the wiring closet to serve the rest of the house too, but those have plenty of "give" and are on the side of the rack that doesn't move more than a few inches.  My $75 steel bread rack for systems is well-spent money ... perhaps 25 yrs ago.  Not expensive like a server rack, but still fits the generic needs to hold equipment, papers, and plenty of areas to do clean cable management.
$87 [https://www.amazon.com/Amazon-Basics-Adjustable-Shelving-Organizer/dp/B07281KYSS](https://www.amazon.com/Amazon-Basics-Adjustable-Shelving-Organizer/dp/B07281KYSS) is a little shorter, less wide and not as deep. They make them half-height too.  Mine is over 6ft tall.  Put some rubber indoor/outdoor carpet on each level to handle vibrations.  If I were better organized, I'd only need 50% of the flat space it provides.

---

### Post by LHammonds on 2022-12-01
That bread-stand-on-wheels scares me as a tipping hazard.

The ATOPNUC arrived and oh boy, its the size and weight of a hamburger!  I'm ditching ALL the PowerEdge crap I've been holding onto just to save my decrepit old back from more wear-n-tear.

The video output for the ATOPNUC is HDMI and none of my OLD monitors are HDMI so I cannot check it out unless everyone goes to bed so I can use the living room TV to get it initialized for SSH usage.  Seems to be pre-loaded with Ubuntu 20.04.  Hopefully it does not have the GUI desktop installed.  I'll get 22.04.1 server installed one way or another.

**EDIT #1:** The ATOPNUC did indeed have the desktop GUI installed.  Here are the details straight out of the box:

Ubuntu 20.04.1 LTS, 5.4.0-42-generic kernel, 512 MB boot partition, 118 GB root partition
after an update:
Ubuntu 20.04.5 LTS, 5.15.0-56-generic kernel, 512 MB boot partition, 118 GB root partition

**EDIT #2:** Performing in-place upgrade to 22.04...
Ubuntu 22.04.1 LTS, 5.15.0-56-generic kernel, 512 MB boot partition, 118 GB root partition

LHammonds

---

### Post by MAFoElffen on 2022-12-01
Easy fix...
```

sudo apt install ubuntu-server ubuntu-server-minimal
sudo apt remove libx11* libqt* 

```
Will convert the Edition to Server with no GUI, the only thing that command does not do is convert it back from Network Manager to networkd, but that is just a 1 line edit in NetPlan and 5 more commands.
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl enable systemd-networkd 
sudo systemctl enable systemd-resolved
sudo systemctl start systemd-resolved

```
But then doing a 'do-release-upgrade'... It's shorter (process-wise) just to do an install fresh.

---

### Post by TheFu on 2022-12-02
> **LHammonds said:**
> That bread-stand-on-wheels scares me as a tipping hazard.

Mine isn't gonna tip, but I do put the heaviest stuff on the bottom 2 shelves. I suppose if I put everything on the top shelf (EVERYTHING) and pulled from the top really hard, then it might tip, but I doubt it.  Not even close.  More stable than a Ford Bronco by far!

---

