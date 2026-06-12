---
title: "Bringing my RAID back"
date: 2008-07-12
forum: Server Platforms
---

### Post by Bernd_C on 2008-07-12
[FONT="Tahoma"]
Hi all,

So at the beginning of the year, I built my first server for all the every growing amount of data that I don't want to carry around on my laptop.  Recognizing my laziness when it comes to backups, I opted to build a RAID5 server instead of just putting a NAS on my network.  Having touched a Unix system for over 10 years, I felt this would be a great occasion to get my feet wet again.  It all worked fine for a few months until...

Coming home from work one day, I walked into my apartment hearing the RAID card sounding the alarm.  Well, that's why you want to have the redundancy of RAID5.  A drive dies, you replace it and rebuild - done.  So I rebooted and went into the RAID card's BIOS and learnt that 2 drives had failed.  Now 2 drives from two different manufacturers failing within a 10 hour window seemed strange.  So I went ahead, put the two drives back online and ran the consistency checker.  Two days later, it was done stating that it had fixed it.

Starting the machine again, I got a boot disk error.  Booting from the Ubuntu installer CD, I found that while I can see the physical drive created by the RAID card, I had no such luck regarding the partitions I had created.

Any suggestions what I can do?

This is the hardware I used:
[INDENT]MoBo: Foxconn WinFast 6100k8ma
CPU: AMD Athlon 64 3700+ (Toledo)
RAM: Buffalo DD4003-1GB/BR
HDD: LSI MegaRAID i4 (RAID5), 2x WD5000AAJB, 2x ST3500630A
[/INDENT]

I had updated the MegaRAID firmware to N661 and created one big partition plus the swap partition.  I am uncertain whether I formated them in ext2 or ext3.  As OS, I installed Ubuntu 6.06.1 LTS.

I plan to put another HDD into the machine connecting it directly to the MoBo so I can run the machine from it.

Whatever you think may work, I glad to try.
[/FONT]

---

