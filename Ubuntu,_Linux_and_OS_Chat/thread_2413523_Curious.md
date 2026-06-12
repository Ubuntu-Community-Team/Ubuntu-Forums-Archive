---
title: "Curious"
date: 2019-02-26
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2019-02-26
Hello Ubuntu forums,


Not a request for help just an opinion.


I was given this desktop and it originally had ***Windows 10*** installed although it would not boot in to ***Windows ***anymore. 

I suspect it had to do with a hard drive failure.

I know that I need a hard drive but is there any life still left in this hard drive.

I'm curious.

Thanks


I installed ***Ubuntu 18.04*** and ran these commands. 

***sudo fdisk -l ***
[I][B] 
sudo badblocks -v /dev/sda > badsectors.txt[/B][/I]


```
***thomas@ASUS-Z87-PRO:~$ sudo fdisk -l***
[sudo] password for thomas: 
Disk /dev/loop0: 12.2 MiB, 12804096 bytes, 25008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 3.3 MiB, 3411968 bytes, 6664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 21 MiB, 22003712 bytes, 42976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 1.6 MiB, 1691648 bytes, 3304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 140 MiB, 146841600 bytes, 286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x120391ca

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 312580095 312578048 149.1G 83 Linux




Disk /dev/loop8: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 91 MiB, 95416320 bytes, 186360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 34.8 MiB, 36503552 bytes, 71296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

***thomas@ASUS-Z87-PRO:~$ sudo badblocks -v /dev/sda > badsectors.txt***
Checking blocks 0 to 156290903
Checking for bad blocks (read-only test): done                                                 
Pass completed, 2130 bad blocks found. (2130/0/0 errors)
***thomas@ASUS-Z87-PRO:~$ ***

```

---

### Post by lisati on 2019-02-26
Wow! 

You might get *some* more life out of it, but I'd recommend not using it for anything important without seriously considering backups on a separate device.

---

### Post by poorguy on 2019-02-26
> **lisati said:**
> Wow! 

You might get *some* more life out of it, but I'd recommend not using it for anything important without seriously considering backups on a separate device.

Hey lisati,

Your ***Wow! ***made me laugh. 

It is pretty bad isn't it although it is working at the moment.

I agree that it isn't reliable at all and I'm thinking about trying out one of those $20.00 SSDs just to see how they run.

All of my computers are old Windows Vista desktops and this one is a new one to me 2013 / 2015 something like that.

I can't complain as it was free my neighbor was just going to throw it away when I happened to walk outside or I would have missed out.

The power supply fan was barely spinning so I replace the fan but it really needs a real power supply than the cheap POS it has.

I'll throw some down some cash and better it up some as it has 8.0 GB of ram in it and that is enough for what I use my computer for.

Thanks for your reply and for making me laugh. ;)


***Not bad for free.***

```
thomas@ASUS-Z87-PRO:~$ inxi -Fxz
System:    Host: ASUS-Z87-PRO Kernel: 4.15.0-45-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.3 (Gtk 3.22.30-1ubuntu1) Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop System: ASUS product: All Series serial: N/A
           Mobo: ASUSTeK model: Z87-PRO v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 2005 date: 06/04/2014
CPU:       Quad core Intel Core i5-4690K (-MCP-) arch: Haswell rev.3 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27986
           clock speeds: max: 3900 MHz 1: 1047 MHz 2: 1109 MHz 3: 1113 MHz 4: 1014 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915 Resolution: 1152x720@59.97hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop version: 4.5 Mesa 18.2.2 Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic
Network:   Card-1: Intel Ethernet Connection I217-V driver: e1000e v: 3.2.6-k port: f080 bus-ID: 00:19.0
           IF: eno1 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9462 Wireless Network Adapter driver: ath9k bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 160.0GB (5.4% used)
           ID-1: /dev/sda model: WDC_WD1600BEVS size: 160.0GB
Partition: ID-1: / size: 146G used: 8.1G (6%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 23.0C mobo: 22.0C
           Fan Speeds (in rpm): cpu: 0 fan-1: 1638 fan-2: 991 fan-3: 0 fan-4: 0 fan-5: 0 fan-6: 0
Info:      Processes: 218 Uptime: 1:08 Memory: 1102.4/7849.0MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
thomas@ASUS-Z87-PRO:~$ 

 
```

---

### Post by jdeca57 on 2019-02-26
I'm told the average life of a hard disk is 5 years and even if I used computers longer than that there will come an end to the life of the disk. I really wouldn't like to work with that computer unless you store data on the cloud. That's what I'm doing now. With fast internet that makes more and more sense. Because eventually, that disk will fail. After replacing it all your work will still be there. Recently I put an SSD as a replacement for an hard disk in my laptop. No loss of data, of course and I can hardly believe the time it takes to boot. Putting some new components in a PC makes a lot of difference.

---

### Post by poorguy on 2019-02-26
> **jdeca57 said:**
>  Recently I put an SSD as a replacement for an hard disk in my laptop.  No loss of data, of course and I can hardly believe the time it takes to  boot. Putting some new components in a PC makes a lot of difference. 		

Hey jdec,

I agree.

I've heard that SSDs are an excellent upgrade and I agree putting some new components in a PC makes a lot of difference and that is my plan for this since I have zero dollars in it and it is a worthy project imo.

I will be looking at newegg and see what kinda deals I can find.


Thanks for the reply.

---

### Post by QIII on 2019-02-26
As a general rule:  Rust lasts for decades.  If you have data that you really want to secure and save, put it on mechanical hard drives.  You can pull them out of machines, set them on shelves and come back to your data a few years later.

SSDs suffer from what is sometimes called "voltage leakdown", "charge leakdown".  An un-powered consumer SSD can potentially start losing data in three weeks -- enterprise level drives (counter-intuitively) start to lose data in 7 days.  Either would probably be unusual, but what about a month or two?  Don't put them on a shelf and don't shut down the machine they are in for long.  Also have the data "dance" occasionally if you can.

Early SSDs were not very robust and longevity was considered unacceptably low.  That has changed.  SSDs nowadays enjoy longevity much closer to mechanical drives -- although, as said, that assumes you don't leave them powered off long enough to leak charge and ruin data.

My recommendation?  Run on SSDs and do all backups or long-term storage on HDDs.  The machine I am on right now has 3 NVMe devices and two 2.5" SSDs holding VMs.  I frequently back up to a server with hard drives and the machine is pretty much always powered on.

---

### Post by lammert-nijhof on 2019-02-27
I beat you easily. I live in the Dominican Republic and we are really poor with respect to availability of modern hardware. My disks are ancient and according to most pundits, past their due dates. 
Here is my **2008** HP dc5850:

```
bertadmin@HP-Host-d5:~$ inxi -Fxz
System:    Host: HP-Host-d5 Kernel: 4.15.0-45-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: MATE 1.20.1 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: desktop System: Hewlett-Packard product: HP Compaq dc5850 Microtower serial: N/A
           Mobo: Hewlett-Packard model: 3029h serial: N/A
           BIOS: Hewlett-Packard v: 786F6 v03.14 date: 11/15/2011
CPU:       Quad core AMD Phenom II X4 B97 (-MCP-) 
           arch: K10 rev.3 cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 25537
           clock speeds: max: 3200 MHz 1: 800 MHz 2: 800 MHz 3: 2000 MHz
           4: 800 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 8400 GS Rev. 3] bus-ID: 02:00.0
           Display Server: x11 (X.Org 1.19.6 ) driver: nvidia
           Resolution: 1680x1050@60.26hz
           OpenGL: renderer: GeForce 8400GS/PCIe/SSE2
           version: 3.3.0 NVIDIA 340.107 Direct Render: Yes
Audio:     Card-1 NVIDIA High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 02:00.1
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic
Network:   Card: Broadcom and subsidiaries NetXtreme BCM5754 Gigabit Ethernet PCIE
           driver: tg3 v: 3.137 bus-ID: 3f:00.0
           IF: enp63s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1948.4GB (0.4% used)
           ID-1: /dev/sda model: ST500DM002 size: 500.1GB
           ID-2: /dev/sdb model: ST320LT020 size: 320.1GB
           ID-3: /dev/sdc model: WDC_WD1002FBYS size: 1000.2GB
           ID-4: /dev/sdd model: SPCC_Solid_State size: 128.0GB
Partition: ID-1: / size: 39G used: 6.3G (17%) fs: zfs dev: N/A
           ID-2: swap-1 size: 8.39GB used: 0.13GB (2%)
           fs: swap dev: /dev/sdd5
RAID:      Device-1: /dev/archives - ONLINE components: online: sdc4
           Info: raid: zfs-no-raid size: 540G available: 176G allocated: 364G
           Device-2: /dev/hp-data - ONLINE components: online: sda2 sdb2 sdc3
           Info: raid: zfs-no-raid size: 636G available: 403G allocated: 233G
           Device-3: /dev/log components: N/A
           Info: raid: zfs-no-raid size: - available: - allocated: -
           Device-4: /dev/cache components: N/A
           Info: raid: zfs-no-raid size: - available: - allocated: -
           Device-5: /dev/systems - ONLINE components: online: sdd6
           Info: raid: zfs-no-raid size: 50.5G available: 33.4G allocated: 17.1G
           Device-6: /dev/vms - ONLINE components: online: sda1 sdb1 sdc2
           Info: raid: zfs-no-raid size: 488G available: 227G allocated: 261G
           Device-7: /dev/log components: N/A
           Info: raid: zfs-no-raid size: - available: - allocated: -
           Device-8: /dev/cache components: N/A
           Info: raid: zfs-no-raid size: - available: - allocated: -
Sensors:   System Temperatures: cpu: 68.0C mobo: 43.0C gpu: 0.0:90C
           Fan Speeds (in rpm): cpu: 0 fan-1: 0 fan-3: 1505 fan-4: 1673
Info:      Processes: 511 Uptime: 10:26 Memory: 5321.3/7961.2MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```
Note that the system runs and boots from zfs. It boots from a 50 GB zfs datapool, that is shared between 3 host systems (Xubuntu or Ubuntu Mate, 18.04 or 18.10); one for Virtualbox, one for VMware and one for QEMU/KVM. The Virtualbox host Ubuntu Mate boots in 21 seconds from a lz4 compressed "systems" datapool on my $21 SPCC SSD connected through a $8 Chinese SATA-3 PCIe card. Its speed is limited to 400 MB/s by my 2008 PCIe 2.0 motherboard. 

Data (hp-data) and virtual machines (vms) are striped over 3 old HDDs. Those datapools are supported by a SSD cache for reads and by a SSD log to speed up all synchronous writes. 

[LIST]
[*]Memory cache hit rates now ~93%, mostly ~90% (space used: 1.99 GB for 3.53 compressed GB)
[*]SSD Cache hit rates now       ~4%, mostly ~ 20% (space used: 5.3 GB for 11.1 compressed GB)
[/LIST]
The HDD are really old:
```

[I]3.5" sda 500 GB Seagate
head flying hours: 5 years 10 month and 16 days
bad sectors: 1
[/I][I]2.5" sdb 320 GB Seagate
[/I][I]head flying hours: 1 years 6 month and 21 days (refurbished?)
bad sectors: 0
[/I][I]3.5" sdc 1 TB WD Black
head flying hours: 6 years 8 month and 1 days 
[/I][I]bad sectors: 0
[/I]
```
**Note that those 3 old disks share the load and they are off-loaded by the 2-level caching with accumulated hit rates of ~92% **(90% + 20% of the remaining 10%). That SDD cache seems of limited use in normal operation, since the VM will run almost completely from the memory cache :). However during initial operation and booting it makes a significant difference. I run five Ubuntu 19.04 VMs. After rebooting the Host, those VM boot in 45-60 seconds from the 3 striped HDDs. But after a while the SSD cache starts to get filled and then the boot times are reduced to 15 - 24 seconds. 

ZFS is using the SSD as a real cache and not as integral part of your storage like StoreMI, but they are looking at changing that. That current SSD caching is optimized for servers, that sometimes run for years without being rebooted.

---

### Post by mastablasta on 2019-02-27
> **lammert-nijhof said:**
> I beat you easily. I live in the Dominican Republic and we are really poor with respect to availability of modern hardware. My disks are ancient and according to most pundits, past their due dates. 
Here is my **2008** HP dc5850:


you don't have to live in Dominican Republic to be considered poor. i have a PC i put together back in 2004 with a single core AMD. also i refuse to replace something that works. had to replace the disk as it would no longer boot reliably. also later on GPU died, so i replaced that as well. 

> **QIII said:**
> 
SSDs suffer from what is sometimes called "voltage leakdown", "charge leakdown".  An un-powered consumer SSD can potentially start losing data in three weeks -- enterprise level drives (counter-intuitively) start to lose data in 7 days.  Either would probably be unusual, but what about a month or two?  Don't put them on a shelf and don't shut down the machine they are in for long.  Also have the data "dance" occasionally if you can.


:O

i learn something new every day.

---

### Post by poorguy on 2019-02-27
> **QIII said:**
> As a general rule:  Rust lasts for decades.  If you have data that you really want to secure and save, put it on mechanical hard drives.  You can pull them out of machines, set them on shelves and come back to your data a few years later.

I agree I have done the same and do have some old drives that are used only for storage and never any issues with accessing data when needed.
> **QIII said:**
> SSDs suffer from what is sometimes called "voltage leakdown", "charge leakdown".  An un-powered consumer SSD can potentially start losing data in three weeks -- enterprise level drives (counter-intuitively) start to lose data in 7 days.  Either would probably be unusual, but what about a month or two?  Don't put them on a shelf and don't shut down the machine they are in for long.  Also have the data "dance" occasionally if you can.

Early SSDs were not very robust and longevity was considered unacceptably low.  That has changed.  SSDs nowadays enjoy longevity much closer to mechanical drives -- although, as said, that assumes you don't leave them powered off long enough to leak charge and ruin data.

My recommendation?  Run on SSDs and do all backups or long-term storage on HDDs.  The machine I am on right now has 3 NVMe devices and two 2.5" SSDs holding VMs.  I frequently back up to a server with hard drives and the machine is pretty much always powered on.
I always wondered about data loss on SSDs occurred or not as I've never had any problems with data loss on usb thumb drives but usb thumb drives may not be the same although I'm not certain.

The NVMe drives / devices seem to be better performance wise over a standard SSD from what I've read and the cost for them is reasonable.

Yeah I'll have to do some more investigation about NVMe although I'm going to try a cheap $20.00 SSD just to see how it's performance is and for what I use my computer for a small SSD will work.

QIII you seem to have a lot of experience with these type of drives.


Thanks for your reply.

---

### Post by poorguy on 2019-02-27
> **mastablasta said:**
> 

                     [IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **QIII**                     [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=13840839#post13840839")                 
                 SSDs suffer from what is sometimes called  "voltage leakdown", "charge leakdown".  An un-powered consumer SSD can  potentially start losing data in three weeks -- enterprise level drives  (counter-intuitively) start to lose data in 7 days.  Either would  probably be unusual, but what about a month or two?  Don't put them on a  shelf and don't shut down the machine they are in for long.  Also have  the data "dance" occasionally if you can.

:O

i learn something new every day.
That's why I like Ubuntu forum I'm always learning new stuff.

---

### Post by jdeca57 on 2019-02-27
I did read [https://www.anandtech.com/show/9248/the-truth-about-ssd-data-retention]("https://www.anandtech.com/show/9248/the-truth-about-ssd-data-retention") and that dates from 2015.

The last paragraph:

> All in all, there is absolutely zero reason to worry about SSD data retention in typical client environment. Remember that the figures presented here are for a drive that has already passed its endurance rating, so for new drives the data retention is considerably higher, typically over ten years for MLC NAND based SSDs. If you buy a drive today and stash it away, the drive itself will become totally obsolete quicker than it will lose its data. Besides, given the cost of SSDs, it's not cost efficient to use them for cold storage anyway, so if you're looking to archive data I would recommend going with hard drives for cost reasons alone.

Now I'm not storing SSD on shelves for a longer period but I can attest that I have SSD drives that are shut down during the vacation and that may be a month. Afterwards, they simply work so I tend to believe the article I quoted but as I said earlier at a certain point drives will fail and a cloud solution is simply the way one should prefer. Do it like Dropbox and have a copy on your local drive so that even if there is a temporary problem with the connection you still have a copy locally.

For me that works, ;-)

---

### Post by poorguy on 2019-02-27
I read a lot of reviews about failed SSDs after a few months and some within one year regardless of cost or brand or size. 

I read that SSDs can run pretty hot under normal use and wonder how much that contributes to the failure of SSDs.

Hard to determine the accuracy of the reviews or the type of environment the SSDs are / were used.

One thing for certain is when sellers have them on sale for real cheap prices they sell out fast.

Regardless of which type drive is purchased the performance gain is excellent based on what I've read.

---

### Post by lammert-nijhof on 2019-02-28
> **mastablasta said:**
> you don't have to live in Dominican Republic to be considered poor.

I intended to say, that we are poor with respect to the possibility to buy modern hardware. E.g. Ryzen motherboards like the B350/B450 you can't find here in the local computer shops. 

I also keep my PCs a long time, we still use a 2003 Pentium 4 HT (3.0 Ghz). I bought it 2nd hand around 2009 and used it myself till early 2014, when I replaced it with the HP dc5850. Now it is used mainly by visiting (grand)children. It has 2 x 1 GB 400 Mhz memory and 2 x 40 GB IDE disks (each a whopping 60 MB/s). In January I striped and compressed (ratio 1.7) the disks using BTRFS (effective throughput 2 x 60 x 1.7 = ~200 MB/s) and that Peppermint 9 system now boots in 45 seconds. 
In the past at work I would go for the coffee machine after powering on such a system with Windows XP, but now that Pentium is too fast for that :)

That is one of my current hobbies, getting the best performance from (old) systems using state-of-the-art software.

---

### Post by poorguy on 2019-02-28
> **lammert-nijhof said:**
> I intended to say, that we are poor with respect to the possibility to buy modern hardware. E.g. Ryzen motherboards like the B350/B450 you can't find here in the local computer shops.
Most local PC Shops where I live suck and don't have anything cool like back in the good old days although I can buy all kinds of cool PC Parts off ebay for really good prices if you are willing to search.

> **lammert-nijhof said:**
> I also keep my PCs a long time, we still use a 2003 Pentium 4 HT (3.0  Ghz). 
I used one of those for years with Windows XP and when Windows XP EOL came about I installed Linux on it and used it awhile longer and gave it to someone who used it for another few years.
> **lammert-nijhof said:**
>  Peppermint 9 system now boots in 45 seconds.         
***Peppermint*** is an excellent Linux distro for elderly hardware and from my experience usually works OOTB.

As already mentioned if the computers you have are capable and working why not use what you already own I do and have never been disappointed.

---

### Post by jdeca57 on 2019-02-28
> **poorguy said:**
> I read a lot of reviews about failed SSDs after a few months and some within one year regardless of cost or brand or size. 

I read that SSDs can run pretty hot under normal use and wonder how much that contributes to the failure of SSDs.

Hard to determine the accuracy of the reviews or the type of environment the SSDs are / were used.

One thing for certain is when sellers have them on sale for real cheap prices they sell out fast.

Regardless of which type drive is purchased the performance gain is excellent based on what I've read.
Well I recently bought a Kingston drive and on the package they mention a 3 year warranty. In each case European law forces the reseller to offer a 2 year warranty on products so I'm reasonably certain that if it fails shortly I'll get a new one but of course that isn't what I want. Performance is indeed excellent, it seems a brand new machine.

A single grief: an Ubuntu installation doesn't take the SSD in account so you are responsible for settings like swappiness or putting fstrim in a cron job.

---

### Post by deadflowr on 2019-02-28
fstrim is a systemd service set to run once a week by default.
No need to set a cron job for it.

---

### Post by jdeca57 on 2019-02-28
> **deadflowr said:**
> fstrim is a systemd service set to run once a week by default.
No need to set a cron job for it.

Thanks. I'll delete that cron job so one grief less. ;-)

---

### Post by poorguy on 2019-02-28
So once I get an SSD installed and Ubuntu 18.04 installed and updated do I need to optimize and set up or change the sappiness as I've read about or is that all done automatically.

Is there a link that can be posted to tell me what is needed to do for a new SSD.

---

### Post by mastablasta on 2019-03-01
well these guys usually have good documentation: [https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

in Ubuntu some things are already optimised: [https://askubuntu.com/questions/908513/how-to-optimise-ssd-to-increase-lifetime](https://askubuntu.com/questions/908513/how-to-optimise-ssd-to-increase-lifetime)

---

### Post by poorguy on 2019-03-01
> **mastablasta said:**
> well these guys usually have good documentation: [https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

in Ubuntu some things are already optimised: [https://askubuntu.com/questions/908513/how-to-optimise-ssd-to-increase-lifetime](https://askubuntu.com/questions/908513/how-to-optimise-ssd-to-increase-lifetime)

Thanks for the links mastablasta.


[I][B]
Update[/B][/I]
Just got done viewing the links you posted and they look to be what I need.

Thanks again.

Now all I need to do is to decide on an SSD to purchase.

***Ubuntu forum rocks***. :guitar:

---

### Post by poorguy on 2019-03-03
OK here's what I ordered and I figured this would be a good start and sure can't complain about the price.

[https://www.newegg.com/Product/Product.aspx?Item=N82E16820326766](https://www.newegg.com/Product/Product.aspx?Item=N82E16820326766)


Thanks


Life is good.

poorguy ;-)

---

### Post by mastablasta on 2019-03-04
i am always surprised at how expensive these things are here in Europe and also how cheap they are in the USA. 

that's like 16,65 EUR.

here the chepaest one is 120 GB Kingston which costs 22,20 EUR + 5 EUR shipping.

And average monthly salary is roughly about 2/3 of US. so lower salaries, pricier commodities. that's how we roll...

---

### Post by jdeca57 on 2019-03-04
> **mastablasta said:**
> i am always surprised at how expensive these things are here in Europe and also how cheap they are in the USA. 

that's like 16,65 EUR.

here the chepaest one is 120 GB Kingston which costs 22,20 EUR + 5 EUR shipping.

And average monthly salary is roughly about 2/3 of US. so lower salaries, pricier commodities. that's how we roll...
Well Europe is the land of taxes, we pay 21% VAT and of course in the US there is also a sales tax but it is less. And the forced warranty also has to do with prices...

---

### Post by poorguy on 2019-03-05
I'm glad I'm can afford to purchase what I need / want and unfortunately paying taxes is part of it.

If this SSD last as long or half as long as some of the mechanical HDD I have from my Windows Xp computers then I'll be happy.

This will be my first SSD so a new learning experience and adventure.

---

