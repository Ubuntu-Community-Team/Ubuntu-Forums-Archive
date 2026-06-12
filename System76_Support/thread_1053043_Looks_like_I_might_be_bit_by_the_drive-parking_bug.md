---
title: "Looks like I might be bit by the drive-parking bug"
date: 2009-01-28
forum: System76 Support
---

### Post by compholio on 2009-01-28
I have a SERP3 and I'm starting to see some drive errors and a steady-on activity light under conditions where there should be minimal drive access (causing my laptop to slow to a crawl).  smartctl indicates that there have been 3196 errors with the drive (though it seems to think they are not serious since they do not show up in the "Health" check) and /var/log/messages has a reasonably large number of the following:
```
Jan 28 08:59:12 ubuntu kernel: [  341.844716] ata3.00: configured for UDMA/133
Jan 28 08:59:12 ubuntu kernel: [  341.844746] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan 28 08:59:12 ubuntu kernel: [  341.844754] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan 28 08:59:12 ubuntu kernel: [  341.844763] Descriptor sense data with sense descriptors (in hex):
Jan 28 08:59:12 ubuntu kernel: [  341.844769]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 28 08:59:12 ubuntu kernel: [  341.844786]         03 ab 0d 89 
Jan 28 08:59:12 ubuntu kernel: [  341.844794] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan 28 08:59:12 ubuntu kernel: [  341.844808] end_request: I/O error, dev sda, sector 61541769
Jan 28 08:59:12 ubuntu kernel: [  341.844839] ata3: EH complete
Jan 28 08:59:12 ubuntu kernel: [  341.848222] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jan 28 08:59:12 ubuntu kernel: [  341.848381] sd 2:0:0:0: [sda] Write Protect is off
Jan 28 08:59:12 ubuntu kernel: [  341.848965] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 28 08:59:12 ubuntu kernel: [  341.849591] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jan 28 08:59:12 ubuntu kernel: [  341.849840] sd 2:0:0:0: [sda] Write Protect is off
Jan 28 08:59:12 ubuntu kernel: [  341.850147] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

So, I'm thinking that I might be bit by Ubuntu's drive-parking bug and dramatically reduced the usable life of my drive.  I've no experience with HD problems in the past, so does anyone have recommendations of things to check before I go pick up a new drive?

---

### Post by thomasaaron on 2009-01-28
Check the size of your log files...

/var/log/syslog
/var/log/messages

There is a bug that causes them to grow incredibly fast.

We're not sure what it is yet, but one tech here now thinks it has to do with mounting samba shares in fstab. Have you played with that any?

---

### Post by compholio on 2009-01-28
My entire /var/log/ folder is 35M and this installation is over a year old.  While I do have some samba shares in fstab I do not have them mounted normally, so I doubt that's an issue.  The only logs that appear to have issues when the drive starts acting up are dmesg, kern.log, and messages with roughly the same information (in previous message).  I haven't encountered in the past where the drive appears to be on the way out (my drives have always been either "totally dead" or working fine) but it looks like the drive has been encountering a lot of errors (according to smartctl and /var/log/messages), so it "seems" like it's dying.

Reasonably relevant SMART info:
```
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1052
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       3
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       153864140
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6340
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1201
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       3182
189 High_Fly_Writes         0x003a   096   096   000    Old_age   Always       -       4
190 Airflow_Temperature_Cel 0x0022   072   043   045    Old_age   Always   In_the_past 28 (Lifetime Min/Max 25/28)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       351
193 Load_Cycle_Count        0x0022   001   001   000    Old_age   Always       -       523210
194 Temperature_Celsius     0x001a   028   057   000    Old_age   Always       -       28 (0 12 0 0)
195 Hardware_ECC_Recovered  0x0012   093   065   000    Old_age   Always       -       33075342
197 Current_Pending_Sector  0x0010   070   070   000    Old_age   Offline      -       625
198 Offline_Uncorrectable   0x003e   070   070   000    Old_age   Always       -       625
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0000   100   253   000    Old_age   Offline      -       0
254 Unknown_Attribute       0x0000   001   001   000    Old_age   Offline      -       66

```

---

### Post by thomasaaron on 2009-01-28
To be honest, I don't know what to think of smartctl. It's useful in some ways, but I've had it report brand new drives as being old-age and pre-fail. So, it seems a bit quirky to me.

But those errors in your /var/log/messages look like it could be developing some bad sectors. It could be that your filesystem, after all this time, has some glitches in it that fsck isn't fixing.

I'd make sure everything important is backed up and keep an eye on it. If it were mine, I'd re-image it. Re-formatting might take care of the problem. If it doesn't, we can work on getting you a new drive.

---

### Post by compholio on 2009-01-28
I'm out of warranty at this point, but if you sell drives separately then I'd have no problem purchasing a new one through you guys.  I'm tempted to just pick up an external USB drive, copy everything off, put in a new drive and use this as an excuse for a fresh 64-bit install (I'm on an upgrade of the original 32-bit install right now).

---

### Post by thomasaaron on 2009-01-28
Unfortunately, we don't sell drives separately. You can probably get a killer deal off of newegg anyway.

---

### Post by compholio on 2009-01-29
> **thomasaaron said:**
> Unfortunately, we don't sell drives separately. You can probably get a killer deal off of newegg anyway.

Too bad :(  Well, my current drive appears to be a Seagate Momentus ST980813ASG - which their website says is a 2.5", 7200 RPM, SATA 3 Gb/s drive.  Since I'm looking at replacing it I figure I might as well get a decent size drive, is there any reason that a Western Digital Scorpio WD3200BJKT (also 2.5", 7200 RPM, and SATA 3 Gb/s) won't work in this box?  (I've run into problems with some computers in the past where "not all drives are created equal" as far as the BIOS is concerned.)

---

### Post by thomasaaron on 2009-01-29
We've not tested with it in particular, but I see no reason why it shouldn't work.

---

### Post by compholio on 2009-01-29
Alrighty, thanks!

---

