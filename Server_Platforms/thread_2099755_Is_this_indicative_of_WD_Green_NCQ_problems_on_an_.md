---
title: "Is this indicative of WD Green NCQ problems on an mdadm RAID5?"
date: 2012-12-30
forum: Server Platforms
---

### Post by stasiana on 2012-12-30
I have an nVidia nForce430 controller and I had 4 2TB WD Green HDs (WD20EARS) in an mdadm RAID5 configuration with the drives' default settings and never had a problem. Then about a year ago I switched them to Windows 7 mirror volumes. Recently I decided to go back to a Ubuntu mdadm RAID5 configuration. 

The RAID array now keeps failing with one drive dropping out almost immediately after it finishes rebuilding. It's not a specific drive in the array because I've now seen two different drives drop out on separate rebuilds.

I've "fixed" the 8 second Intellipark possibility with wdidle3. No change. 

SMART data all says OK. It's not cable because there are no CRC errors.

Scanning for bad blocks reports none on any of the drives.

I see the following in dmesg. Notice the NCQ, frozen and timeout messages. I see that the NCQ queue depth is set to 31 on all these drives. Is this log indicative of an NCQ problem?

```

[33061.856168] ata7: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
[33061.856181] ata7: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
[33061.856181]   dhfis 0x1 dmafis 0x1 sdbfis 0x0
[33061.856189] ata7: ATA_REG 0x40 ERR_REG 0x0
[33061.856193] ata7: tag : dhfis dmafis sdbfis sactive
[33061.856197] ata7: tag 0x0: 1 1 0 1  
[33061.856216] ata7.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
[33061.856223] ata7.00: failed command: WRITE FPDMA QUEUED
[33061.856236] ata7.00: cmd 61/01:00:08:08:00/00:00:00:00:00/40 tag 0 ncq 512 out
[33061.856236]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[33061.856242] ata7.00: status: { DRDY }
[33061.856253] ata7: hard resetting link
[33061.856257] ata7: nv: skipping hardreset on occupied port
[33062.324058] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[33062.340352] ata7.00: configured for UDMA/133
[33062.340370] ata7.00: device reported invalid CHS sector 0
[33062.340394] sd 6:0:0:0: >[sdd]  
[33062.340399] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[33062.340404] sd 6:0:0:0: >[sdd]  
[33062.340408] Sense Key : Aborted Command [current] [descriptor]
[33062.340415] Descriptor sense data with sense descriptors (in hex):
[33062.340419]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[33062.340437]         00 00 00 00 
[33062.340446] sd 6:0:0:0: >[sdd]  
[33062.340451] Add. Sense: No additional sense information
[33062.340456] sd 6:0:0:0: >[sdd] CDB: 
[33062.340459] Write(10): 2a 00 00 00 08 08 00 00 01 00
[33062.340475] end_request: I/O error, dev sdd, sector 2056
[33062.340484] end_request: I/O error, dev sdd, sector 2056
[33062.340488] md: super_written gets error=-5, uptodate=0
[33062.340498] md/raid:md0: Disk failure on sdd1, disabling device.
[33062.340498] md/raid:md0: Operation continuing on 3 devices.
[33062.340537] ata7: EH complete
[33062.421866] RAID conf printout:
[33062.421882]  --- level:5 rd:4 wd:3
[33062.421889]  disk 0, o:1, dev:sdb1
[33062.421893]  disk 1, o:1, dev:sdc1
[33062.421897]  disk 2, o:0, dev:sdd1
[33062.421901]  disk 3, o:1, dev:sde1
[33062.428914] RAID conf printout:
[33062.428919]  --- level:5 rd:4 wd:3
[33062.428923]  disk 0, o:1, dev:sdb1
[33062.428927]  disk 1, o:1, dev:sdc1
[33062.428930]  disk 3, o:1, dev:sde1

```

---

