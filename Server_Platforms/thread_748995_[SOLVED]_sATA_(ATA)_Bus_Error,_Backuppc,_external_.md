---
title: "[SOLVED] sATA (ATA) Bus Error, Backuppc, external drive"
date: 2008-04-08
forum: Server Platforms
---

### Post by DrJohn999 on 2008-04-08
I installed a Seagate FreeAgent Pro 750 external HD via eSata thru a Vantec eSata PCI host card. I chose to use eSata instead of USB due to the spin-down timeout problem with this drive on USB with Linux systems. I know there's a workaround, but my initial tests showed that, as documented by others too, this drive doesn't have the timeout problem on the eSata interface.

Repartitioned and formatted the drive with Ext3 (no problems there), added it to /etc/fstab (using its UUID to avoid problems with flaky /dev/sda vs. /dev/sdb inconsistencies on boot),  mounting it to /var/lib/backuppc to start using it to back up four WinXP machines.

The system is Gutsy server (up to date) on an ASUS P4B533 w/ 1.5 Gb and a single 110 MB EIDE drive for boot / OS / swap. Never logged any problems on the internal drive.

Backuppc is set on its default schedule and connects to the external machines with rsyncd. Each time backuppc runs a job I see from 5-10 ATA bus errors followed by a "soft reset"  like this:

```
[185553.552456] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[185553.552479] ata3.00: (BMDMA2 stat 0x86c2201)
[185553.552495] ata3.00: cmd 35/00:10:af:6e:02/00:02:00:00:00/e0 tag 0 cdb 0x0 data 270336 out
[185553.552498]          res 51/84:00:be:70:02/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[185553.881295] ata3: soft resetting port
[185554.041005] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[185554.360701] ata3.00: configured for UDMA/33
[185554.360728] ata3: EH complete
[185554.382706] sd 2:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[185554.383357] sd 2:0:0:0: [sdb] Write Protect is off
[185554.383365] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[185554.384378] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Here's fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f44b6167-3a3a-469b-b89c-517170945219 /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/sda5
UUID=39791c39-40b9-4822-bd9a-aa07a1a0b29c none            swap    sw              0       0
#/dev/sdb1
UUID=d8c01c03-a9c8-4771-9b96-fdbc7797be2c /var/lib/backuppc ext3 defaults 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#added for REV drive at /dev/scd1
/dev/scd1       /media/rev0     udf,iso9660 noauto,user,rw,0,0
```

Backuppc's compression level is set to 2, and it does max out the MPU at 80 - 90 % while running. Backuppc's logs show some errors, but these are either file names too long, or various access denied errors from Windoes. No H/W errors reported there.

Manually writing files, ls, cat, and other single commands don't cause these errors. However, the error does show up during extended writing. I recursively copied a few GB from the internal hard drive to the external drive, which took several minutes, and got the same ATA errors.

Before I commit to this backup arrangement long-term, I need to resolve this problem -- I'll have low confidence in the data integrity if the ATA bus pulls errors every time I run backuppc. 

The problem could be the high MPU utilization, but I suspect thait it could be the Vantec  eSata card.  The PCI bus on this MOBO is PCI-II, and the card claims that's compatible.

The drive, BTW, ran on a newer much faster WinXP system with a different  PCI-X eSata card for several months with no apparent problems.

Any helpful suggestions on this one? Example, move the card to a different slot, or change a BIOS PCI bus setting?

---

### Post by mrsteveman1 on 2008-04-08
How long is the eSATA cable? PATA used to have severe bus problems with out of spec cables, like the round ones (crosstalk), or ones way way too long (undervoltage). SATA shouldn't have such problems, but its still possible if its a long cable.

Second, it sounds like those errors only happen when the drive is writing to a specific area on the disk, which may be why random commands don't give you errors but long writes do.  I've seen some similar stuff on another seagate drive i have here, it appears fine, S.M.A.R.T passes all tests, even the extended ones, but specific sectors fail putting errors in the kernel log. These were of course sector errors and not bus errors, but you can't rule out disk problems. 

I would scan the disk for bad blocks with the badblocks program, at least you will know if something is already wrong with the drive before trusting it.

If sectors aren't the problem definitely try moving the card to a different slot, and if that doesn't fix it, move the card and drive to another computer, and stress the drive there to see if the motherboard is acting funny.

---

### Post by DrJohn999 on 2008-04-09
Good advice, Steve, Thanks! Here's what I tried:

 tried checking the disk with
```

/etc/init.d/backuppc stop
umount /dev/sdb1
e2fsck -c -c /dev/sdb1

```
(with root privs).
This performs a "non-destructive read-write test." Immediately upon starting the test the system began to post the same ATA Bus errors. I stopped it after about 5 minutes, not wanting to accumulate even more of these in the syslog.

I then switched the drive over to USB. Upon booting, the system immediately recognized it and mounted it to the same place. Now, running e2fsck produced zero errors. I stopped it again after a few minutes. With a drive this large it would take a very long time to run through the block checks completely.

This pretty much confirmed that it's either the eSata controller card or the motherboard. The cable is exonerated because this drive ran just fine with the same cable on a WinXP Pro system for months (with a NTFS partition, not the current Ext3).

Next, I verified if the known USB timeout problem is present here -- it is. It's described as  'solved' [[COLOR="Blue"]**on this forum thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=494673&highlight=freeagent+pro+usb"). but I'm not convinced (read the whole thread).

So, next I think I'll order up a different eSata-PCI card (Rosewill this time) and see if it works. Meantime I'll play with the USB set up to see if I can get it to work. I'll post again here if I find anything different.

Thanks again,

Dr John

---

### Post by mrsteveman1 on 2008-04-09
I'm curious, have you tried connecting the eSATA cable directly to the motherboards SATA ports? You can in fact do that, but i can't remember if the connector is identical or not.

---

### Post by DrJohn999 on 2008-04-09
Unfortunately this motherboard has no sata ports --- it's too old. THe connectors are not identical, but you can get adapters that bring an internal sata port out on the backside.

It's also occurred to me to look at the log from bootup, and I've found several PCI-related items that may be hints; for example, there's one that suggests I should use "pci=routeirq". I plan to try this.

-- Dr John

---

### Post by DrJohn999 on 2008-04-10
The "pci=routeirq" boot setting makes no difference. 

While waiting for a new eSata PCI card to arrive, I reconnected the drive via USB and implemented a different fix on this forum for the spin-down timeout problem; [[COLOR="Blue"]**read it here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=494673&highlight=%2Fdevice%2Fallow_restart").

This works across reboots so far, and is a better solution than the one mentioned earlier in this thread because it makes use of a udev rule so that the drive gets configured every time its detected.

More next week on the replacement eSata card.

-- Dr John

---

### Post by DrJohn999 on 2008-04-14
The replacement eSata card worked no differently than the first one. Granted, the two cards look about the same and have the same Silicon Image controller chip (although different mask and datecodes). So, I'd conclude that the problem most likely is the motherboard, with a less likely chance that it's the eSata cable which worked fine with a different (Rosewill PCI-x) eSata card. If I revisit this one I'll try another cable, but for now this issue is closed.

-- DrJohn

---

### Post by DrJohn999 on 2008-06-24
A new cable didn't help either. I removed the 750 GB drive and installed it internally as a permanent drive which holds the backuppc pool files ( mounted at /var/lib/backuppc). I then picked up 2 350 GB USB external drives (pocket sized), and now run off an archive copy of today's file state onto one of them while keeping the other offsite.

BackupPC's full pool size is around 950 GB; the physical size on the 750 GB driv eis around 350 GB, and the archive copies (tar.gz) of all of the (five) machines' current files occupy only about 56% of one of the 350 GB removable USB drives. It takes around 330 minutes to create a full archive copy of all of them. Not Bad!

---

