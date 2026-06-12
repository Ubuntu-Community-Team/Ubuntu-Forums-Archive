---
title: "file server; hypervisor and many desktops on one PC"
date: 2024-03-31
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2024-03-31
Don't worry about servers, you don't need them (unless you share a lot of data frequently with your family) remember KISS.

My server is the default (minimal install) of Ubuntu 24.04 LTS. Of course I should have used Ubuntu server, but I'm lazy. To get the server functionality I've added a hypervisor; the latest Virtualbox 7.15 and the advanced filesystem; OpenZFS 2.2.2 to stores all my data and VMs. All my desktops are in VMs and I have the following main desktop VMs:

- Social Media (Xubuntu 24.04 LTS) to run my Email, WhatsApp; FB-messenger; Skype; Transmission and KDE-Connect.  The only OS with open ports!  Host OS and all other VMs are closed for inbound traffic..
- Banking (Ubuntu 16.04 ESM) encrypted by Virtualbox, used EXCLUSIVELY for banking, to be used for another 2 year;
- Multimedia (Ubuntu 24.04 Unity LTS), maybe I switch to Budgie, because it seems slightly more reliable.  In the past I used Ubuntu Studio 20.04, but I avoid any KDE flavor, due to somewhat worse reliability :(
- Experiments and App try-out (Ubuntu 24.04 LTS), the only desktop that mighty get somewhat contaminated by the try-outs and experiments. But rolling back the VM using OpenZFS can avoid it. 
- My jukebox (Windows XP Home), installed and activated in March 2010, it survived 2 VBox owners; 3 desktops and 4 CPUs!  It plays the wma copies of my LPs and CDs with WoW and TrueBass effects. 
- Just in case I need it; (Windows 11 Pro).

Every VM gets the access to the data on the server it needs. I'm lazy, so I use Virtualbox shared folders, but if you are fanatic about it, you could use Samba (Windows networking) for sharing data. I often run 2 Linux VMs and occasionally 3.  In case of Windows 11, I only have space for 1 Linux VM, e.g Xubuntu for Social Media.

The 2019 hardware was very cheap ($349). It has a Ryzen 3 2200G, the 2nd slowest Ryzen ever; 16GB DDR4; 512GB nvme-SSD (3400/2300MB/s) and I reused a small sata-SSD and HDDs. 

The VM are very responsive, because they are run mainly from a 4GB (lz4 compressed) memory cache (L1ARC) and partly from nvme-SSD. Xubuntu (4 cores) boots in <7 seconds and Windows XP (1 core) needs 25 seconds. The other Ubuntu VMs boot in less than 12 seconds, while Windows 11 (4 cores) needs anything between 35 and 60 seconds dependent on the content of the memory cache.

 In 2023 the 2 HDDs (1TB and 500GB) failed after 10 power-on years, so I  bought a new 2TB HDD, the first part of my mid-life upgrade.  After 5 years it is time for a modest mid life upgrade to 32GB DDR4 and a Ryzen 5 5600G(T).

---

### Post by TheFu on 2024-04-01
I have two Ryzen 5600G systems. No regrets at all.  I had a B450 motherboard that previously had a Ryzen 2600. The upgrade was to remove the nvidia 1030 GT and a CPU swap.  That was about 3 yrs ago. No issues with the AMD iGPU after moving to a 5.10+ kernel.  40% CPU gain for $120 (that was the 
Ryzen 5600G cost then).  I sold 16GB of 3200Mhz RAM and the 2600 CPU to a friend for $80, so the upgrade was $40 (in my mind).  The RAM was just sitting around and wasn't a matched set with any others.  Ryzen is really picky about RAM.

The Ryzen 5600X is $100 now.  The 5600G is $119.  Which to get depends on your current dedicated GPU and how happy you are with it.  If your motherboard can take it.  Some of the Ryzen 2000 series motherboards didn't get firmware updates to support the Ryzen 5000 series. Definitely do that firmware update BEFORE anything else.  You might be able to get one more CPU upgrade from the same AM4 MB in 3 yrs.

You didn't mention RAM at all.  16G would be fine for what you've described.  I kept hitting that limit and put in 32GB to support a little headroom.

```
istar (Ubuntu 20.04 64bit / Linux 5.15.0-101-generic)                                           Uptime: 9 days, 0:58:37

CPU  [  1.7%]   CPU \     1.7%  nice:     0.0%  ctx_sw:    4K     MEM -   70.4%     SWAP -   19.7%     LOAD    12-core
MEM  [ 70.4%]   user:     1.4%  irq:      0.0%  inter:   3863     total:  30.7G     total:   4.10G     1 min:    1.48
SWAP [ 19.7%]   system:   0.4%  iowait:   8.1%  sw_int:  1882     used:   21.6G     used:     828M     5 min:    0.84
                idle:    90.1%  steal:    0.0%                    free:   9.10G     free:    3.29G     15 min:   0.57
```

That's with 5 VMs and 5 LXC containers running.   Guess I added a few more systems since I was hitting the 16G RAM limit.  The system has 37TB of storage connected across 9 devices. A few 8TB, but most are 4TB except the NVMe SSD which holds the OS and all VMs/Containers.
```
$ inxi -D
Drives:    Local Storage: total: 37.13 TiB used: 30.24 TiB (81.4%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO 500GB size: 465.76 GiB 
           ID-2: /dev/sda vendor: HGST (Hitachi) model: HUS726T4TALA6L4 size: 3.64 TiB 
           ID-3: /dev/sdb vendor: HGST (Hitachi) model: HMS5C4040ALE640 size: 3.64 TiB 
           ID-4: /dev/sdc vendor: HGST (Hitachi) model: HMS5C4040ALE640 size: 3.64 TiB 
           ID-5: /dev/sdd type: USB vendor: Western Digital model: WD easystore 25FB size: 7.28 TiB 
           ID-6: /dev/sde type: USB vendor: Western Digital model: WD easystore 25FB size: 7.28 TiB 
           ID-7: /dev/sdf type: USB vendor: Western Digital model: WD40 EFRX-68WT0N0 size: 3.64 TiB 
           ID-8: /dev/sdg type: USB vendor: Seagate model: ST332062 0AS size: 298.09 GiB 
           ID-9: /dev/sdh vendor: Western Digital model: WD8002FZWX-00BKUA0 size: 7.28 TiB 
```

Doesn't ZFS like RAM?

I don't see anything wrong with what you've done or plan to do.  May be useful to add a 2-port NIC, but that's more useful for security nerds who want connections to different LANs without using tagging as the only fake-security.

---

### Post by lammert-nijhof on 2024-04-02
You have a nice collection of storage!  Currently I'm happy with my 512GB nvme-SSD (3400/2300MB/s) and 2TB HDD (192MB/s) cached by a 128GB sata-SSD (L2ARC; ~530MB/s).  All storage and all caches are lz4 compressed.  I'm a collector so I have all Windows Releases in a VM and all Ubuntu LTS Releases.  So some VMs are happy with a few MBs of memory, like DR-DOS; Windows 1.04 and Windows for Workgroups 3.11 and others minimally need 4GB like Windows 11 Pro. 

I bought my motherboard from Newegg for $59.99 and it is a ASRock B450 HDV Rel 4.0.  I upgraded the BIOS 1 or 2 years ago to support the Ryzen 5 5600G. The BIOS release has been advised by ASRock support, but I postponed the CPU upgrade itself. 

I did mention the 16GB DDR4. You are right, it is enough, but you constantly have to calculate or guess, whether you can start an additional VM. So I want to upgrade to 32GB, also because I like a 2x bigger memory cache (L1ARC; 8GB), so it can also serve less frequently used VMs.   Locally I will buy this month 2x 16GB DDR4 (3000 MHz) for $84. equal in frequency to my current 2x 8GB (3000 MHz). Originally I bought 3000 MHz, because according to the ASRock specs CPU and Motherboard combination was limited to 2993 MHz. If I buy through Ebay or Newegg I have to add ~20% for import duty and ~20% for international transport costs to the US prices. 

I'm happy with my network security, because my PCs are behind a 2nd WiFi router at the back of the house. That router is closed for inbound traffic and admin access is only possible with the MAC addresses of my laptop or desktop.

---

### Post by TheFu on 2024-04-02
I tried to double my RAM from 2x8GB to 4x8GB and that didn't work too well.  The system became unstable and would crash until I slowed it down to 2666 Mhz.  The 2 RAM kits were identical SKUs from the same vendor.  The stability was directly related to the Mhz of the RAM.  Anything over 2666 would crash a few times a week.  Beware.   I ended up selling 2x8GB to a friend and buying a 2x16G matched pair which has been perfectly stable at 3200 Mhz.  I have two nearly identical Ryzen systems (just the storage and workloads are different).

```
$ sudo inxi -m
Memory:
  RAM: total: 30.71 GiB used: 23.72 GiB (77.2%) 
  Array-1: capacity: 128 GiB slots: 4 EC: None 
  Device-1: DIMM_A1 size: No Module Installed 
  Device-2: DIMM_A2 size: 16 GiB speed: 3200 MT/s 
  Device-3: DIMM_B1 size: No Module Installed 
  Device-4: DIMM_B2 size: 16 GiB speed: 3200 MT/s 

```

I hope your unmatch extra RAM works, but if it doesn't, be ready to slow it down and sell the 2 pairs off to someone else while you get a single "matched 32GB" set.

The HDDs are because I'm lazy to delete stuff that I should.  I can't imagine more than 8TB is stuff I actually want to keep (TV Series and maybe 50 movies), the rest is junk (probably).  Who needs 
Up_the_Creek/
Yor_the_Hunter_From_the_Future/
Zapped/
Zombie_Apocalypse_Redemption/
Zoolander_2/
?   Not me.  That's just the end of the list on 1 drive.  BTW, 50% is used for a delayed rsync mirror (backup?). The backups are actually on USB connected storage.  The EasyStore USB connections "disappear" after a few weeks sometimes and it takes a reboot to get them back.  I think it is a USB connector or USB controller (on the disk-side) causing the problems, but both EasyStores have the same issue.  Seems like a design flaw.

---

### Post by smithloo on 2024-04-06
I'm Smithloo.  I'm working for computer and web development company. This is our website [link building agency]("https://www.qualitybacklink.net"). 
I want to know more about [COLOR=#000000]5 VMs and 5 LXC containers running[/COLOR]
can anyone can help me answer it?
is that right [https://documentation.ubuntu.com/lxd/en/stable-5.0/explanation/containers_and_vms/](https://documentation.ubuntu.com/lxd/en/stable-5.0/explanation/containers_and_vms/) ?

---

### Post by gezzer2 on 2024-04-07
i have two home systems that are identical both were purchased when i got my pension payout and will most likely be the last systems the wife and i have.
both system have been upgraded to the max as most of the upgrades were relatively cheap.

both systems are HP 24" all in ones in white.
all components in the systems are laptop components so everything runs with low wattage and power usage.

Ryzen 7 5825u zen 3. 15W to 35W. these CPU's have 16mb of L3 cache. 8C/16T 2GHz to 4.5GHz.
both system use the Ryzen's onboard GPU.

64GB DDR4 3200. thats the max the system can take. the RAM was purchased while on offer at a Amazon Prime sale.
the memory that they replaced was used to upgrade 13" dell latitudes 3380's to 16GB each with some spare.

both systems are fitted with 1TB Intel M2 type SSD's and both systems have 2x external caddies with 1x 1TB and 1x 500GB HDD's.
the 500GB for file backup the 1TB for storage ISO's and software all of the HDD's have been used in our other systems over the years.

these systems are overkill for the use we have them for but for the fist time i have systems i have to keep up with instead of trying to get the systems to keep up with me.
my system runs Ubuntu 22.04.4 LTS with Gnome boxes having Ubuntu 24.04 beta and Windows 10 running in VM.
my wife's system uses Windows 11 Home.

also my Ubuntu 22.04.4 has had its Vmax map increased from 65530 to 262144.
cache pressure reset from the default 100 to 50.
and system swap, which is on a 8GB micro sd card has reduced swappiness set to 10.
systemd setup as an internal caching/resolving server which works wonderfully.
 
all in all im happy with the systems and setup but i doubt it will stop me playing about with them ..

---

### Post by lammert-nijhof on 2024-04-09
My cheap motherboard has only 2 RAM slots, so I have to buy 2 new 16GB  RAM Modules. I will sell the old RAM. The 3000MHz modules are locally on offer on a 5 minutes ride by bike or car, so I will stick to that 3000MHz, also because I want to  use it for a few months with the 2200G. Besides I expect the difference  in PC performance with 3000 or 3200 Mhz RAM is not that large in  practice. I expect less than half of the difference of 6.7% in RAM speed.  My other upgrade to a 5600G will easily beat it, because the 5600G CPU is 3x faster.

---

