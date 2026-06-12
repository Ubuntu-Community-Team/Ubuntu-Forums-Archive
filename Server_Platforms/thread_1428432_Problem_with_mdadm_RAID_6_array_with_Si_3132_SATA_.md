---
title: "Problem with mdadm RAID 6 array with Si 3132 SATA Controller"
date: 2010-03-12
forum: Server Platforms
---

### Post by xianthax on 2010-03-12
I've recently started having an issue with an mdadm RAID 6 array that been operational for about 2500 hours.

Intermittently during write operations the array stalls, dropping to almost 0 write speed for 10-30 seconds.  When this occur one or both of the 2 drives attached to a 2 port Silicon Image si3132 SATA-II controller "locks up" with its activity light locked on.  This just started occurring within the last week and didn't seem to coincide with any update that i noticed.  The array has just recently passed 12.5% full.  The size of the write does not seem to make any difference and it seems completely random.  Some times copying a 5 GB dataset results in no slow down other times a torrent downloading to the array at 50kb/sec does cause a slow down and vise versa.

The array consists of 8 WD 1.5TB drives, 6 attached to the ICH9R south bridge, and 2 attached to a si3132 based PCI express card.  The array is formatted as a single ext4 partition.

Checking SMART data for all drives shows no errors.  Testing read speed with hdparm reports what i would expect (100mb/sec for each drive, ~425mb/sec for the array).

The only thing i did notice is that udma6 is enabled for all the ICH9R drives while only udma5 is enabled for the si3132 drives.  Write cache is enabled for all the disks.  Attempting to set the si3132 drive to udma6 results in an IO error from hdparm.

The si3132 drive is using the sata_sil24 driver.

Nothing of interest appears in the kern or syslog.  During this time top shows very high wait time.

The s13132 controller appears to have the original firmware from 2006 loaded, there are some firmware updates available on the Silicon Image website for this controller that now appear to offer separate firmwares for RAID operation (some sort of hybrid controller/software thing the controller supports) and a separate firmware for standard IDE use.

Has anyone had similar issues with this controller?  Is a firmware update a reasonable course of action?  If so which firmware is best supported by the linux driver?  

I know i'm not using its raid features but i've dealt with controllers that needed to be in raid mode for ahci to be active and for linux to work well with them.  I'm bit ify at the idea of just trying it and finding out as it could knock 2 disks of my array out of action.  

Cheers,

Xian

---

### Post by liuguang on 2010-04-11
Hi, 
Very glad to see your article.
 
[1] Sil3132 is from SiliconImage. Because you used "sata_sil24 driver", similar controller Sil3124 might help resolve your problem.  Although I give you this suggestion, I am a completely new to Ubuntu Raid setup.
 
[2] I am very interested in your setup on Raid6. 
     My requirements are: I need to set up a Raid6 on Ubuntu9.10.
 
     >> Now my Ubuntu9.10 has already been installed into a WD 1.5TB drive[A].
     >> One Sil3132 is plugged into motherboard's slot.
     >> Two SATA hard drives[B and C] are connected to Sil3132.
     >> Another two SATA drives[D and E] are plugged into motherboard's SATA ports.
     
     >> Now I want to build these four drives[B,C,D and E] into Raid6 under Ubuntu9.10.
 
           But I am a newer to linux. I would like your detailed steps on how to build Raid6.
 
           Thanks in advance!
 
      >> I am looking forward to seeing your step by step reply.
           Thanks again!
 
Best Regards!

---

### Post by Vegan on 2010-04-11
I suggest immediately updating any firmware as generally it has fixes for all manor of problems. I do not like the motherboard RAID one bit, get a real RAID card.

---

