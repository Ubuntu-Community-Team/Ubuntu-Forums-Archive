---
title: "Rebuilding my storage server at home"
date: 2019-03-11
forum: Server Platforms
---

### Post by mattiash on 2019-03-11
For 2-3 years now my current storage server has done a great job!
It has been rock solid, all I have done to it is to upgrade from 16.04 - 18.04 just because I can.

These are the parts:
* ASUS TUF B450M-PLUS GAMING
* AMD Ryzen 3 2200G 3.7 GHz 6MB
* Corsair 16GB (2x8GB) DDR4 3200Mhz CL16 Vengeance
5 WD Red 2 Tb
* 3 WD Black Enterprise 2 Tb
1 Samsung EVO 850 500 Gb SSD
If need: 1 Samsung 840 250 Gb SSD
Delock PCI-E SATA card
* == new parts
All will be powered with a Crosair 1000 W PSU.

Now I am running madam raid 5 with ext4. Now I want to build something like this:
Storage-disks in RAID10 or 6.
What filesystem?

Second it would be great to use an SSD as "cache" to improve write speed at least.

Any suggestions on what to do?

(Lets hope for nicer answers than the FreeNAS forums...)

---

### Post by TheFu on 2019-03-11
Do you maintain "reasonable" sized file systems that can be backed up 
**or **
do you present a single file system that spans all the RAID devices?

IMHO, the only valid choices for storage file systems today are
* LVM + EXT4
* LVM + XFS
* ZFS
ZFS isn't supported as a boot disk at this point in Ubuntu.  With the CPU and RAM you have, ZFS should be fantastic, though you might want to consider 6 "similar" HDDs to make RAIDz *happier*.  The downside with XFS is that the file system cannot be shrunk.  I've shrunk ext4 a few times with the help of lvreduce.

Most storage systems just don't need 16G of RAM, though it is good for disk buffers. If you don't run ZFS with all the advanced ZFS stuff, then 8G of RAM would be overkill.

As you know, the main consideration for any storage system is how will it be backed up.  Have you a plan for that?

---

### Post by mattiash on 2019-03-12
Thank you @TheFu your answer was so much better than the ones I got at freenas forum.
First off, the system is going on it's own SSD, so ext4 there.
The storage part is what I want suggestions on, so there I got 8 2Tb disks and a 500 Gb SSD, can I run ZFS with that and with my non-etc memory?

Backup is taken care of, I will have a Backblaze-kind-of client that will backup to a cloud service.

I found a great guide how to build my system!
[https://www.deeztek.com/documentation/guides-tips-and-tricks/ubuntu/how-to-install-and-configure-zfs-on-ubuntu-16-04-lts/](https://www.deeztek.com/documentation/guides-tips-and-tricks/ubuntu/how-to-install-and-configure-zfs-on-ubuntu-16-04-lts/)

---

### Post by TheFu on 2019-03-12
The ZFS people love ECC RAM and they have a point, but ZFS will work without it. Nothing will stop it from working.

I'm not a fan of cloudy backups for more than just the most essential stuff, say 5G, provided I've encrypted it BEFORE using any of their tools.  So it is for wedding photos, kids-just-born photos, tax and insurance data.  

Run some numbers on how long it will take to restore 16TB of stuff.  Does your ISP have data caps?  Will the backup service ship new disks with the data for reasonable prices?

After all, backups really aren't the point - it is all about the restore.

---

### Post by SeijiSensei on 2019-03-12
I experimented with XFS a few years back and found it pretty vulnerable to power outages. If you're going to use XFS, I'd make sure the server is connected to an uninterruptible power supply.

---

### Post by Tr1p on 2019-03-12
im using ext4

---

### Post by mattiash on 2019-03-14
So a few days has passed so now I got one question and one answer. :)

The question: Anything to think of before installning Ubuntu Server 18.04.2 on a Ryzen system?

The answer: First off I know that zfs loves ECC memory, and the mb supports it, if the processor can handle it. But ecc memory is just to expesive atm.
As you now have gussed I am  going with zfs RAIDZ2 with using a EVO 850 500 Gb as cache.

---

### Post by aljames2 on 2019-03-14
If you’re going ECC be sure the CPU & MB both support the type of ECC modules (i.e. registered vs. unbuffered).  ECC is best for server grade MBs like supermicro.   Also, I think you’ll find that Intel chips are preferred for ECC as AMD chips aren’t well documented when it comes to ecc.   Whatever you do make sure that all your components are absolutely compatible with ECC otherwise you just have ECC ram operating without the error correction.  For intel you can check ark intel website for cpu support.

I went down the ECC rabbit hole myself not to long ago.  After countless hours of research I realized my data is not mission-critical enough to warrant using ecc.  I feel versioned backups addresses my needs enough because if a file gets corrupted I can restore a clean version of it.

I can’t speak on RAID as I’ve never used/needed it.  Very complex and can be difficult to restore in the real world when a drive dies....depending on the configuration you go with.  Whatever you do, have a backup of everything, and maybe a 2nd backup kept offsite.  RAID is not a backup.

---

### Post by mattiash on 2019-03-17
Thanks for all the answers after a couple of days of headache not being able to install Ubuntu Server on my new hardware that is finally solved, so now I am heading towards RAIDZ2, just need to read up on it, due to that I got limited connection, I got 8 2Tb disks that are the end RAIDz2 goal, but I need to hook up the backup disk momentarily thus I cannot have all 8 disks hooked up.
But hold on... I just realized that with my now working RAID PCI-E card I have 10 SATA III connection. 10 - 9, gives me one free!
8 disks, system SSD - first run - Hook up Backup disk, and after that add the cache SSD!
Hey I got plan! .)

---

### Post by TheFu on 2019-03-17
I have a Ryzen 2 2600 system on an Asus B450-F motherboard.  Only issues I had were getting the CPU and RAM clocked at the advertised speeds without crashing. Once that was dialed in, which took a few hours, everything has been rock solid. Most of the issues were because I hadn't used an AMD CPU in some time (over 10 yrs) and never used UEFI before.
On my ryzen machine:
```
$ uptime
 06:50:41 up 14 days, 19:06,  2 users,  load average: 0.00, 0.02, 0.00
```
It runs great, fully loaded workload on all cores, working very hard for a few hours a day, transcoding videos, using the stock cooler. I think it is the quietest system here.  I do plan to install a 970 EVO before getting the box into final config.  Using NVMe disabled 2 SATA ports, and I have 8 SATA disks to connect. Four are RAID1 in an external array, 2 are internal and some others are USB3 connected for versioned backups.  With the EVO, I don't think the RAID will be necessary anymore. SSD reliability is really good if we don't go cheap according to some storage vendors I've spoken.  My RAID is for virtual machines today, which need the HA.  They are backed up daily, just like regular physical machines, with daily, automatic, versioned, backups.

OTOH, I've heard that the newer Ryzen's with built-in GPUs are picky about some things.  Bleeding edge hardware, which I avoid.  Vaguely recall that 4.19 kernel's are needed.

---

