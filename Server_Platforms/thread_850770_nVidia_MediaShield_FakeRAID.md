---
title: "nVidia MediaShield FakeRAID"
date: 2008-07-05
forum: Server Platforms
---

### Post by duiu on 2008-07-05
I just got the parts for a home file and print server that I'm going to make. I have yet to assemble them or install any software. Here is the parts list:
[I]
Motherboard: ASUS M2N-MX SE PLUS AM2/AM2+ Socket
Processor: AMD Sempron LE-1100 1.9ghz Single Core
RAM: A-DATA 2GB-stick
HDD: Two WD Caviar Green 1TB
PowerSupply: CoolerMaster 550W 80+ Certified
Network IFace: Encore ENLGA-1320 10/100/1000mbps
[/I]
Anyway, the motherboard has two SATA ports and a fakeRAID via nVidia MediaShield. It can do RAID 0/1/JBOD. I was planning on using a RAID 1 so that my first 1TB drive is mirrored onto the second drive. I encountered some problems:
[LIST=1]
[*]ASUS thinks that the only operating system in the world is Windows, and only provides windows drivers for the MediaShield RAID
[*]The RAID is not an actual RAID, it's a fakeRAID (see [here]("https://help.ubuntu.com/community/FakeRaidHowto")).
[*]The RAID control falls on the CPU, not a RAID card.
[/LIST]
So I was wondering if I should stick with this fakeRAID or use a Linux software RAID. Any suggestions or links for how to do either of these would be appreciated. Additionally, is my processor good enough to handle running a software/fake RAID? 

Thanks

duiu

Oh yeah, more information about the parts I'm using can be found [here]("http://www.productwiki.com/dialupinternetuser/lists/gbl_tap_server/").

---

### Post by fjgaude on 2008-07-06
Even though I'm a software raid guy I would recommend with your setup to **not** raid anything. Just have the two drives as indepentant, but use one for backup, using **rsync**, **grsync**, or **unison**.

Both your CPU and memory would come under strain using either **mdadm** or fakeraid. And likely couldn't actually handle the through-put of these modern, fast drives. That's my opinion. <sigh>

OTOH, you could simply give raid0 or raid1 a try and see how fast it is, and what not. You will have to understand how to get **grub** on both drives so the machine will still boot if one drive fails. There are how-tos for this, but it is not simple.

Good luck but do let us know how you are doing.

---

### Post by Nfzgrld on 2008-07-06
Linux is pretty much an all or nothing proposition when it comes to RAID. In other words, from the OS's point of view, it's either real RAID, or it's just another ATA device. Fortunately, there's a solution. Forget the hardware fakeRAID deal, and just go with the Linux software RAID. It actually is real RAID and I can tell you it works great. I have a server running 4 250Gig IDE drives configured under Ubuntu 8.04 server as RAID 0. The performance and integrity of that array is awesome!

---

### Post by fjgaude on 2008-07-06
I know what you mean... look at these data for 4-drive mdadm raid5:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), CPU fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec

```

But duiu's setup is nothing like mine... all he can do is give it a try and see how he likes it.

---

### Post by duiu on 2008-07-06
Well, I'm fairly new to Ubuntu, so some of this RAID stuff is seeming pretty complicated. I'd go for the backup solution, but one thing is holding me back: With rsync, unison, or grsync, is there a way that I can create a boot disk or have a complete drive mirror or some similar solution so that I can just restore the backup or put in another drive and not have to worry about re-installing and/or reconfiguring the OS, similar to how you can do that with with Arcronis TrueImage?

---

### Post by windependence on 2008-07-06
To clone a drive real fast and real easy without ugly software:

```
sudo dd if=/dev/hda of=/dev/hdb bs=4096 conv=notrunc,noerror
```

Where /dev/hda is your source drive and /devhdb is your target. **CAUTION: reversing the drives with have disasterous consequences. Don't say I didn't warn you.**

-Tim

---

### Post by fjgaude on 2008-07-06
Once you have cloned the main drive, which for those big drives will take awhile, you might want to keep the backup data partition up to date using rsync. It only copied files that have changed since the last update.

A command like this would do the trick:

```
sudo rsync -r -n -t -p -o --delete /home/data/ /media/backup/
```

Such assumes you have your backup drive mounted on /media/backup. The options will preserve time, owner, permissions, groups, and delete anything on the backup folder that is not on the source folder.

You likely will want to study the man rsync pages to get more understanding.

---

### Post by windependence on 2008-07-06
You might want to put fjgaude's command in cron to run every so often, freshening your backup. That way you will always have up to date backups.

-Tim

---

### Post by fjgaude on 2008-07-07
You might wish to study these links to learn about what it takes to use **cron**:

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

We learn something new everyday, eh?

---

### Post by duiu on 2008-07-07
Ok, I'll look at those links.

If I use dd to clone a drive, can I have both of the drives connected to the computer still, or would the computer get confused? If I can, I think I'll just use that one file in /etc that does scheduled stuff, I can't think of it's name at the moment.

---

### Post by fjgaude on 2008-07-07
Sure, both disks will show up in your computer... use your BIOS to point to the prime one, the one that you wish to boot from.

Then you can auto mount the backup drive in /etc/fstab file, after you have made a mountpoint for it. Understand?

If you have the prime drive fault, and if you have been making often backups you can just point to the secondary drive and it will boot. Lots of ways to go here... it's up to judgment... you could still go the raid1 route if you think about it enough.

---

### Post by duiu on 2008-07-07
Awesome, thanks!

---

### Post by silver on 2008-07-08
> **Nfzgrld said:**
> Linux is pretty much an all or nothing proposition when it comes to RAID. In other words, from the OS's point of view, it's either real RAID, or it's just another ATA device. Fortunately, there's a solution. Forget the hardware fakeRAID deal, and just go with the Linux software RAID. It actually is real RAID and I can tell you it works great. I have a server running 4 250Gig IDE drives configured under Ubuntu 8.04 server as RAID 0. The performance and integrity of that array is awesome!

Can this be configured to run as a RAID-5 ? I'm looking to rebuild my system using 3 x 500GB WD RE2's. I want to dual-boot Linux and Win XP x64 on a RAID-5. I hope that each will also be running VM. The system is using the following :

Asus M2N-E motherboard
AMD 4600+ x2 proc
8GB DDR-II
ATI 3870 512MB video card

---

### Post by fjgaude on 2008-07-08
Yes, raid5, raid6, raid10, from **mdadm**.

See **man madam** and this link:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

---

### Post by silver on 2008-07-09
Very, very informative. Thanks for the link.

---

### Post by BobMUK on 2008-07-30
> Can this be configured to run as a RAID-5 ? I'm looking to rebuild my system using 3 x 500GB WD RE2's.

> Yes, raid5, raid6, raid10, from mdadm.

Actually not quite right:
RAID 6 requires a minimum of 4 drives, Silver's 3 disks won't be enough. 
RAID 10 requires an even-number of drives so he can't do that either (and of course just using 2 of them would make it RAID 1).

---

### Post by fjgaude on 2008-07-30
Lost my head, thanks for the corrections.

---

