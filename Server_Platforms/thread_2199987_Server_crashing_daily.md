---
title: "Server crashing daily"
date: 2014-01-17
forum: Server Platforms
---

### Post by tRXxNxc on 2014-01-17
Hopefully someone can help me.  It could be coincidental, but after a recent package upgrade my server started crashing daily.  It seems to crash after 12-14 hours of operation.  I looked at the syslog file and this is what it says.  I have no clue what I'm looking at being a bit of a noob with Linux.

```

Jan 13 17:37:14 Q6600 kernel: [630775.196858] ata7: EH in SWNCQ mode,QC:qc_active 0x1F sactive 0x1F
Jan 13 17:37:14 Q6600 kernel: [630775.196865] ata7: SWNCQ:qc_active 0x1 defer_bits 0x1E last_issue_tag 0x0
Jan 13 17:37:14 Q6600 kernel: [630775.196866]   dhfis 0x1 dmafis 0x1 sdbfis 0x0
Jan 13 17:37:14 Q6600 kernel: [630775.196871] ata7: ATA_REG 0x41 ERR_REG 0x84
Jan 13 17:37:14 Q6600 kernel: [630775.196873] ata7: tag : dhfis dmafis sdbfis sactive
Jan 13 17:37:14 Q6600 kernel: [630775.196877] ata7: tag 0x0: 1 1 0 1  
Jan 13 17:37:14 Q6600 kernel: [630775.196887] ata7.00: exception Emask 0x1 SAct 0x1f SErr 0x300000 action 0x6 frozen
Jan 13 17:37:14 Q6600 kernel: [630775.196891] ata7.00: Ata error. fis:0x21
Jan 13 17:37:14 Q6600 kernel: [630775.196895] ata7: SError: { Dispar BadCRC }
Jan 13 17:37:14 Q6600 kernel: [630775.196899] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:14 Q6600 kernel: [630775.196907] ata7.00: cmd 60/08:00:07:96:c2/00:00:14:00:00/40 tag 0 ncq 4096 in
Jan 13 17:37:14 Q6600 kernel: [630775.196909]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:14 Q6600 kernel: [630775.196913] ata7.00: status: { DRDY ERR }
Jan 13 17:37:14 Q6600 kernel: [630775.196916] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:14 Q6600 kernel: [630775.196919] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:14 Q6600 kernel: [630775.196926] ata7.00: cmd 60/08:08:6f:d2:b0/00:00:0d:00:00/40 tag 1 ncq 4096 in
Jan 13 17:37:14 Q6600 kernel: [630775.196933]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:14 Q6600 kernel: [630775.196936] ata7.00: status: { DRDY ERR }
Jan 13 17:37:14 Q6600 kernel: [630775.196938] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:14 Q6600 kernel: [630775.196940] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:14 Q6600 kernel: [630775.196945] ata7.00: cmd 60/08:10:0f:d3:b0/00:00:0d:00:00/40 tag 2 ncq 4096 in
Jan 13 17:37:14 Q6600 kernel: [630775.196946]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:14 Q6600 kernel: [630775.196948] ata7.00: status: { DRDY ERR }
Jan 13 17:37:14 Q6600 kernel: [630775.196950] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:15 Q6600 kernel: [630775.196952] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:15 Q6600 kernel: [630775.196957] ata7.00: cmd 60/08:18:47:d3:b0/00:00:0d:00:00/40 tag 3 ncq 4096 in
Jan 13 17:37:15 Q6600 kernel: [630775.196958]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:15 Q6600 kernel: [630775.196961] ata7.00: status: { DRDY ERR }
Jan 13 17:37:15 Q6600 kernel: [630775.196963] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:15 Q6600 kernel: [630775.196965] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:15 Q6600 kernel: [630775.196970] ata7.00: cmd 60/08:20:27:d4:b0/00:00:0d:00:00/40 tag 4 ncq 4096 in
Jan 13 17:37:15 Q6600 kernel: [630775.196971]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:15 Q6600 kernel: [630775.196973] ata7.00: status: { DRDY ERR }
Jan 13 17:37:15 Q6600 kernel: [630775.196975] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:15 Q6600 kernel: [630775.196979] ata7: hard resetting link
Jan 13 17:37:15 Q6600 kernel: [630775.196981] ata7: nv: skipping hardreset on

```


Any help would be appreciated.  Thanks

Ron

---

### Post by tRXxNxc on 2014-01-17
Hopefully someone can help me.  It could be coincidental, but after a  recent package upgrade my server started crashing daily.  It seems to  crash after 12-14 hours of operation.  I looked at the syslog file and  this is what it says.  I have no clue what I'm looking at being a bit of  a noob with Linux.

```
Jan 13 17:37:14 Q6600 kernel: [630775.196858] ata7: EH in SWNCQ mode,QC:qc_active 0x1F sactive 0x1F
Jan 13 17:37:14 Q6600 kernel: [630775.196865] ata7: SWNCQ:qc_active 0x1 defer_bits 0x1E last_issue_tag 0x0
Jan 13 17:37:14 Q6600 kernel: [630775.196866]   dhfis 0x1 dmafis 0x1 sdbfis 0x0
Jan 13 17:37:14 Q6600 kernel: [630775.196871] ata7: ATA_REG 0x41 ERR_REG 0x84
Jan 13 17:37:14 Q6600 kernel: [630775.196873] ata7: tag : dhfis dmafis sdbfis sactive
Jan 13 17:37:14 Q6600 kernel: [630775.196877] ata7: tag 0x0: 1 1 0 1  
Jan 13 17:37:14 Q6600 kernel: [630775.196887] ata7.00: exception Emask 0x1 SAct 0x1f SErr 0x300000 action 0x6 frozen
Jan 13 17:37:14 Q6600 kernel: [630775.196891] ata7.00: Ata error. fis:0x21
Jan 13 17:37:14 Q6600 kernel: [630775.196895] ata7: SError: { Dispar BadCRC }
Jan 13 17:37:14 Q6600 kernel: [630775.196899] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:14 Q6600 kernel: [630775.196907] ata7.00: cmd 60/08:00:07:96:c2/00:00:14:00:00/40 tag 0 ncq 4096 in
Jan 13 17:37:14 Q6600 kernel: [630775.196909]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:14 Q6600 kernel: [630775.196913] ata7.00: status: { DRDY ERR }
Jan 13 17:37:14 Q6600 kernel: [630775.196916] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:14 Q6600 kernel: [630775.196919] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:14 Q6600 kernel: [630775.196926] ata7.00: cmd 60/08:08:6f:d2:b0/00:00:0d:00:00/40 tag 1 ncq 4096 in
Jan 13 17:37:14 Q6600 kernel: [630775.196933]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:14 Q6600 kernel: [630775.196936] ata7.00: status: { DRDY ERR }
Jan 13 17:37:14 Q6600 kernel: [630775.196938] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:14 Q6600 kernel: [630775.196940] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:14 Q6600 kernel: [630775.196945] ata7.00: cmd 60/08:10:0f:d3:b0/00:00:0d:00:00/40 tag 2 ncq 4096 in
Jan 13 17:37:14 Q6600 kernel: [630775.196946]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:14 Q6600 kernel: [630775.196948] ata7.00: status: { DRDY ERR }
Jan 13 17:37:14 Q6600 kernel: [630775.196950] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:15 Q6600 kernel: [630775.196952] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:15 Q6600 kernel: [630775.196957] ata7.00: cmd 60/08:18:47:d3:b0/00:00:0d:00:00/40 tag 3 ncq 4096 in
Jan 13 17:37:15 Q6600 kernel: [630775.196958]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:15 Q6600 kernel: [630775.196961] ata7.00: status: { DRDY ERR }
Jan 13 17:37:15 Q6600 kernel: [630775.196963] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:15 Q6600 kernel: [630775.196965] ata7.00: failed command: READ FPDMA QUEUED
Jan 13 17:37:15 Q6600 kernel: [630775.196970] ata7.00: cmd 60/08:20:27:d4:b0/00:00:0d:00:00/40 tag 4 ncq 4096 in
Jan 13 17:37:15 Q6600 kernel: [630775.196971]          res 41/84:04:07:96:c2/84:00:14:00:00/40 Emask 0x10 (ATA bus error)
Jan 13 17:37:15 Q6600 kernel: [630775.196973] ata7.00: status: { DRDY ERR }
Jan 13 17:37:15 Q6600 kernel: [630775.196975] ata7.00: error: { ICRC ABRT }
Jan 13 17:37:15 Q6600 kernel: [630775.196979] ata7: hard resetting link
Jan 13 17:37:15 Q6600 kernel: [630775.196981] ata7: nv: skipping hardreset on
```


Any help would be appreciated.  Thanks

Ron

---

### Post by QIII on 2014-01-17
Hello!

Please use code tags -- see my signature for a link.

Hopefully someone will be along shortly to give you a hand with the crashing issue.

Cheers!

---

### Post by Bucky Ball on 2014-01-17
*Thread moved to **Server Platforms**. *

---

### Post by lisati on 2014-01-17
My $0.02: The "BadCRC" suggest to me that your system seems to be having trouble reading something from one of your drives. 

One thing you might want to check is the SATA cable for your drive(s) (see [here]("http://lime-technology.com/wiki/index.php/The_Analysis_of_Drive_Issues#Drive_interface_issue_.231")).

---

### Post by tomearp on 2014-01-17
[This post]("http://www.itechlounge.net/2013/07/linux-ata-failed-command-read-fpdma-queued/") is worth a read, it suggests that some kernel versions have issues with some hard disk controllers and a work-around is to disable native command queuing.

---

### Post by SeijiSensei on 2014-01-17
> **tomearp said:**
> [This post]("http://www.itechlounge.net/2013/07/linux-ata-failed-command-read-fpdma-queued/") is worth a read, it suggests that some kernel versions have issues with some hard disk controllers and a work-around is to disable native command queuing.

An easy way to test and see if this is the problem is to reboot and select an earlier kernel version, then see if the problem is resolved.

However the errors I see indicate that the drive itself has gone bad.  You can try installing [smartmontools](https://help.ubuntu.com/community/Smartmontools) and using them to test the drive's integrity.

---

### Post by tgalati4 on 2014-01-17
Reseat all of the cables in the machine.  It could be a SATA controller problem on the motherboard, a bad cable as Lisati suggested, or a failing disk drive.  While inspecting the machine, check the capacitors for bulges or leaks.

---

### Post by tRXxNxc on 2014-01-17
Tried turning off NCQ and it still crashed.  I'll try the smartmontools when I get home.  Bummer if it's a bad drive.  It's barely a year old. Thanks.

---

### Post by Doug S on 2014-01-17
Could a moderator put these two threads together? It's confusing.

In addition to all the points already given on the two threads, check the power supply. I assume ata7 means you have several disks and I wonder if the power supply is up to the load.

---

### Post by lisati on 2014-01-18
> **Doug S said:**
> Could a moderator put these two threads together? It's confusing.
Done. It can get confusing, and having multiple threads for the same problem dilutes the community's ability to help.

---

### Post by tRXxNxc on 2014-01-18
Yeah.  Sorry about the 2 threads.  One was moved from the general help to the server section by a moderator.  Examining the motherboard doesn't show any signs of bloated capacitors and Smartmontools didn't show any hdd errors.  I haven't changed the cables yet since I'm trying to systematically do one thing at a time to figure out the cause, but I did make sure they weren't loose.  Hard part is that it won't crash until about 12 hours of operation.  Doing a little more research on my motherboard, I found that the Bios had some issues with SATA errors so I updated the Bios and will hope for the best.  It has currently been up for about 10 hours, so if the pattern continues, then I should know soon.  Thanks for all the helpful advice.  I'll keep you posted.

---

### Post by CharlesA on 2014-01-18
Run a long SMART test to see what is shows.

Also, post what the SMART data returned.

---

### Post by tRXxNxc on 2014-01-19
So far the server hasn't crashed in a day after updating the Bios so hopefully that was the problem.  Strange that it started after some package updates.  Here's the SMART long test data.

```
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      5395         -

```

Will see what happens in the next few days.

---

### Post by tgalati4 on 2014-01-19
Perhaps a kernel update triggered a bug in the BIOS.  The update to the BIOS then fixed the bug.  We shall see.

---

