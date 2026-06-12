---
title: "Disk errors after upgrade..."
date: 2014-09-21
forum: Server Platforms
---

### Post by KillerKelvUK on 2014-09-21
I was happily running 4x 2TB Seagate ST2000DM001's as a raid10 via a PCIe SATA rev3.0 controller (JBOD) [Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller (rev 10)].

I  needed more space so replaced the disks with 4TB Seagate ST4000VN000's in a raid6 using the same PCIe controller and immediately saw the following errors.  I reconnected the disks via the onboard SATA controllers and the errors no longer report, fsck says the disks are okay and thus far the array seems stable.  I'd rather not reconnect the disks again to check but I'm assuming the PCIe controller has a problem with the disk or maybe the 4TB/capacity...is this is a reasonable assumption...little out of my league here?!

:(  Kelv

```

Sep 22 00:06:50 blackserver kernel: [   65.745132] ata10.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x0 action 0x6 frozen
Sep 22 00:06:50 blackserver kernel: [   65.745140] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745146] ata10.00: cmd 60/08:00:b8:0d:04/00:00:38:01:00/40 tag 0 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745146]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745149] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745151] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745156] ata10.00: cmd 60/08:08:c0:0d:04/00:00:38:01:00/40 tag 1 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745156]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745158] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745160] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745165] ata10.00: cmd 60/08:10:c8:0d:04/00:00:38:01:00/40 tag 2 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745165]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745167] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745169] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745174] ata10.00: cmd 60/08:18:d0:0d:04/00:00:38:01:00/40 tag 3 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745174]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745176] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745178] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745192] ata10.00: cmd 60/08:20:d8:0d:04/00:00:38:01:00/40 tag 4 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745192]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745193] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745194] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745196] ata10.00: cmd 61/00:28:00:90:89/04:00:03:00:00/40 tag 5 ncq 524288 out
Sep 22 00:06:50 blackserver kernel: [   65.745196]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745197] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745198] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745199] ata10.00: cmd 61/80:30:00:94:89/02:00:03:00:00/40 tag 6 ncq 327680 out
Sep 22 00:06:50 blackserver kernel: [   65.745199]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745200] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745201] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745203] ata10.00: cmd 61/80:38:80:a6:89/01:00:03:00:00/40 tag 7 ncq 196608 out
Sep 22 00:06:50 blackserver kernel: [   65.745203]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745204] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745205] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745207] ata10.00: cmd 60/08:40:60:4d:04/00:00:b3:01:00/40 tag 8 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745207]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745208] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745209] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745210] ata10.00: cmd 60/08:48:08:0d:04/00:00:38:01:00/40 tag 9 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745210]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745211] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745212] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745214] ata10.00: cmd 60/08:50:10:0d:04/00:00:38:01:00/40 tag 10 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745214]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745215] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745216] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745218] ata10.00: cmd 60/08:58:18:0d:04/00:00:38:01:00/40 tag 11 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745218]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745219] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745220] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745221] ata10.00: cmd 60/08:60:20:0d:04/00:00:38:01:00/40 tag 12 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745221]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745222] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745223] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745225] ata10.00: cmd 60/08:68:28:0d:04/00:00:38:01:00/40 tag 13 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745225]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745226] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745227] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745229] ata10.00: cmd 60/08:70:30:0d:04/00:00:38:01:00/40 tag 14 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745229]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745230] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745231] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745232] ata10.00: cmd 60/08:78:38:0d:04/00:00:38:01:00/40 tag 15 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745232]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745233] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745234] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745236] ata10.00: cmd 60/08:80:40:0d:04/00:00:38:01:00/40 tag 16 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745236]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745237] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745238] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745240] ata10.00: cmd 60/08:88:48:0d:04/00:00:38:01:00/40 tag 17 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745240]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745241] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745242] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745243] ata10.00: cmd 60/08:90:50:0d:04/00:00:38:01:00/40 tag 18 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745243]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745244] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745245] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745247] ata10.00: cmd 60/08:98:58:0d:04/00:00:38:01:00/40 tag 19 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745247]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745248] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745249] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745251] ata10.00: cmd 60/08:a0:60:0d:04/00:00:38:01:00/40 tag 20 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745251]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745252] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745252] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745254] ata10.00: cmd 60/08:a8:68:0d:04/00:00:38:01:00/40 tag 21 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745254]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745255] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745256] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745258] ata10.00: cmd 60/08:b0:70:0d:04/00:00:38:01:00/40 tag 22 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745258]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745259] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745260] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745262] ata10.00: cmd 60/08:b8:78:0d:04/00:00:38:01:00/40 tag 23 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745262]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745263] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745263] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745265] ata10.00: cmd 60/08:c0:80:0d:04/00:00:38:01:00/40 tag 24 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745265]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745266] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745267] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745269] ata10.00: cmd 60/08:c8:88:0d:04/00:00:38:01:00/40 tag 25 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745269]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745270] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745271] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745273] ata10.00: cmd 60/08:d0:90:0d:04/00:00:38:01:00/40 tag 26 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745273]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745274] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745274] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745276] ata10.00: cmd 60/08:d8:98:0d:04/00:00:38:01:00/40 tag 27 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745276]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745277] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745278] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745280] ata10.00: cmd 60/08:e0:a0:0d:04/00:00:38:01:00/40 tag 28 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745280]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745281] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745282] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745283] ata10.00: cmd 60/08:e8:a8:0d:04/00:00:38:01:00/40 tag 29 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745283]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745284] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745285] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:06:50 blackserver kernel: [   65.745287] ata10.00: cmd 60/08:f0:b0:0d:04/00:00:38:01:00/40 tag 30 ncq 4096 in
Sep 22 00:06:50 blackserver kernel: [   65.745287]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:06:50 blackserver kernel: [   65.745288] ata10.00: status: { DRDY }
Sep 22 00:06:50 blackserver kernel: [   65.745291] ata10: hard resetting link
Sep 22 00:06:50 blackserver kernel: [   66.072851] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:06:50 blackserver kernel: [   66.074379] ata10.00: configured for UDMA/133
Sep 22 00:06:50 blackserver kernel: [   66.074484] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074486] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074488] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074490] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074492] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074496] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074499] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074501] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074503] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074505] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074507] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074509] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074511] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074513] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074515] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074517] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074519] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074521] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074523] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074524] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074526] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074528] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074530] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074532] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074534] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074536] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074538] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074539] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074541] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074543] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074545] ata10.00: device reported invalid CHS sector 0
Sep 22 00:06:50 blackserver kernel: [   66.074555] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074557] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074559] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074560] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074564] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074565]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074580]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074582] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074583] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074583] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074584] Read(16): 88 00 00 00 00 01 38 04 0d b8 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074589] end_request: I/O error, dev sdg, sector 5234757048
Sep 22 00:06:50 blackserver kernel: [   66.074597] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074598] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074598] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074599] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074600] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074600]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074603]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074605] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074605] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074606] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074607] Read(16): 88 00 00 00 00 01 38 04 0d c0 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074610] end_request: I/O error, dev sdg, sector 5234757056
Sep 22 00:06:50 blackserver kernel: [   66.074612] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074613] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074614] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074614] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074615] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074616]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074619]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074620] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074621] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074622] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074622] Read(16): 88 00 00 00 00 01 38 04 0d c8 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074625] end_request: I/O error, dev sdg, sector 5234757064
Sep 22 00:06:50 blackserver kernel: [   66.074627] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074628] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074628] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074629] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074630] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074630]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074633]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074635] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074635] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074636] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074637] Read(16): 88 00 00 00 00 01 38 04 0d d0 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074640] end_request: I/O error, dev sdg, sector 5234757072
Sep 22 00:06:50 blackserver kernel: [   66.074642] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074643] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074644] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074644] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074645] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074645]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074649]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074650] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074651] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074651] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074652] Read(16): 88 00 00 00 00 01 38 04 0d d8 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074655] end_request: I/O error, dev sdg, sector 5234757080
Sep 22 00:06:50 blackserver kernel: [   66.074660] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074660] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074661] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074662] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074662] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074663]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074666]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074668] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074668] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074669] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074669] Read(16): 88 00 00 00 00 01 38 04 0d 08 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074673] end_request: I/O error, dev sdg, sector 5234756872
Sep 22 00:06:50 blackserver kernel: [   66.074675] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074675] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074676] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074677] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074677] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074678]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074690]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074691] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074692] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074692] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074693] Read(16): 88 00 00 00 00 01 38 04 0d 10 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074696] end_request: I/O error, dev sdg, sector 5234756880
Sep 22 00:06:50 blackserver kernel: [   66.074698] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074699] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074700] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074700] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074701] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074702]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074705]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074706] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074707] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074708] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074708] Read(16): 88 00 00 00 00 01 38 04 0d 18 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074712] end_request: I/O error, dev sdg, sector 5234756888
Sep 22 00:06:50 blackserver kernel: [   66.074714] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074723] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074724] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074724] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074725] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074726]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074729]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074730] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074731] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074732] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074732] Read(16): 88 00 00 00 00 01 38 04 0d 20 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074736] end_request: I/O error, dev sdg, sector 5234756896
Sep 22 00:06:50 blackserver kernel: [   66.074737] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074738] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074739] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074739] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074740] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074740]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074744]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074745] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074746] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074746] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074747] Read(16): 88 00 00 00 00 01 38 04 0d 28 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074750] end_request: I/O error, dev sdg, sector 5234756904
Sep 22 00:06:50 blackserver kernel: [   66.074752] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074753] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074754] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074754] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074755] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074755]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074759]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074760] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074761] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074761] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074762] Read(16): 88 00 00 00 00 01 38 04 0d 30 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074767] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074768] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074768] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074769] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074770] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074770]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074773]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074775] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074775] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074776] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074777] Read(16): 88 00 00 00 00 01 38 04 0d 38 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074781] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074782] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074783] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074783] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074784] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074784]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074788]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074789] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074789] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074790] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074791] Read(16): 88 00 00 00 00 01 38 04 0d 40 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074795] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074796] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074797] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074797] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074798] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074798]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074802]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074803] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074804] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074804] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074805] Read(16): 88 00 00 00 00 01 38 04 0d 48 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074810] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074811] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074811] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074812] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074813] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074813]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074816]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074818] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074818] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074819] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074820] Read(16): 88 00 00 00 00 01 38 04 0d 50 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074824] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074825] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074826] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074826] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074827] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074827]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074831]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074832] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074833] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074833] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074834] Read(16): 88 00 00 00 00 01 38 04 0d 58 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074838] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074839] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074840] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074840] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074841] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074841]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074845]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074846] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074847] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074847] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074848] Read(16): 88 00 00 00 00 01 38 04 0d 60 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074853] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074854] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074855] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074855] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074856] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074856]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074860]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074861] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074861] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074862] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074863] Read(16): 88 00 00 00 00 01 38 04 0d 68 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074868] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074868] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074869] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074870] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074870] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074871]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074874]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074876] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074876] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074877] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074877] Read(16): 88 00 00 00 00 01 38 04 0d 70 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074882] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074883] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074883] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074884] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074885] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074885]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074888]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074890] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074890] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074891] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074891] Read(16): 88 00 00 00 00 01 38 04 0d 78 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074896] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074897] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074897] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074898] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074899] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074899]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074902]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074904] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074904] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074905] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074905] Read(16): 88 00 00 00 00 01 38 04 0d 80 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074911] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074911] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074912] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074912] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074913] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074914]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074917]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074918] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074919] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074920] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074920] Read(16): 88 00 00 00 00 01 38 04 0d 88 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074925] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074926] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074927] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074927] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074928] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074928]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074932]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074933] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074933] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074934] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074935] Read(16): 88 00 00 00 00 01 38 04 0d 90 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074940] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074940] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074941] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074942] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074942] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074943]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074946]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074948] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074948] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074949] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074949] Read(16): 88 00 00 00 00 01 38 04 0d 98 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074954] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074955] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074956] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074956] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074957] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074957]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074961]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074962] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074963] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074963] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074964] Read(16): 88 00 00 00 00 01 38 04 0d a0 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074969] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074969] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074970] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074971] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074971] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074972]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074975]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074977] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074977] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074978] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074978] Read(16): 88 00 00 00 00 01 38 04 0d a8 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074983] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074984] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 00:06:50 blackserver kernel: [   66.074985] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074985] Sense Key : Aborted Command [current] [descriptor]
Sep 22 00:06:50 blackserver kernel: [   66.074986] Descriptor sense data with sense descriptors (in hex):
Sep 22 00:06:50 blackserver kernel: [   66.074986]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074989]         00 00 00 00 
Sep 22 00:06:50 blackserver kernel: [   66.074991] sd 9:0:0:0: [sdg]  
Sep 22 00:06:50 blackserver kernel: [   66.074991] Add. Sense: No additional sense information
Sep 22 00:06:50 blackserver kernel: [   66.074992] sd 9:0:0:0: [sdg] CDB: 
Sep 22 00:06:50 blackserver kernel: [   66.074993] Read(16): 88 00 00 00 00 01 38 04 0d b0 00 00 00 08 00 00
Sep 22 00:06:50 blackserver kernel: [   66.074999] ata10: EH complete
Sep 22 00:07:23 blackserver kernel: [   98.662670] ata10.00: exception Emask 0x0 SAct 0xf00000 SErr 0x0 action 0x6 frozen
Sep 22 00:07:23 blackserver kernel: [   98.662678] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:07:23 blackserver kernel: [   98.662684] ata10.00: cmd 60/08:a0:98:0d:51/00:00:03:00:00/40 tag 20 ncq 4096 in
Sep 22 00:07:23 blackserver kernel: [   98.662684]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:23 blackserver kernel: [   98.662687] ata10.00: status: { DRDY }
Sep 22 00:07:23 blackserver kernel: [   98.662689] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:07:23 blackserver kernel: [   98.662694] ata10.00: cmd 61/00:a8:00:18:f0/02:00:00:00:00/40 tag 21 ncq 262144 out
Sep 22 00:07:23 blackserver kernel: [   98.662694]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:23 blackserver kernel: [   98.662697] ata10.00: status: { DRDY }
Sep 22 00:07:23 blackserver kernel: [   98.662699] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:07:23 blackserver kernel: [   98.662703] ata10.00: cmd 61/f8:b0:00:1a:f0/01:00:00:00:00/40 tag 22 ncq 258048 out
Sep 22 00:07:23 blackserver kernel: [   98.662703]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:23 blackserver kernel: [   98.662706] ata10.00: status: { DRDY }
Sep 22 00:07:23 blackserver kernel: [   98.662708] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:07:23 blackserver kernel: [   98.662712] ata10.00: cmd 61/08:b8:e0:28:77/00:00:03:00:00/40 tag 23 ncq 4096 out
Sep 22 00:07:23 blackserver kernel: [   98.662712]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:23 blackserver kernel: [   98.662715] ata10.00: status: { DRDY }
Sep 22 00:07:23 blackserver kernel: [   98.662719] ata10: hard resetting link
Sep 22 00:07:23 blackserver kernel: [   98.990385] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:07:23 blackserver kernel: [   98.992070] ata10.00: configured for UDMA/133
Sep 22 00:07:23 blackserver kernel: [   98.992170] ata10.00: device reported invalid CHS sector 0
Sep 22 00:07:23 blackserver kernel: [   98.992174] ata10.00: device reported invalid CHS sector 0
Sep 22 00:07:23 blackserver kernel: [   98.992176] ata10.00: device reported invalid CHS sector 0
Sep 22 00:07:23 blackserver kernel: [   98.992178] ata10.00: device reported invalid CHS sector 0
Sep 22 00:07:23 blackserver kernel: [   98.992186] ata10: EH complete
Sep 22 00:07:55 blackserver kernel: [  130.656889] ata8.00: exception Emask 0x0 SAct 0x3f8000 SErr 0x0 action 0x6 frozen
Sep 22 00:07:55 blackserver kernel: [  130.656897] ata8.00: failed command: READ FPDMA QUEUED
Sep 22 00:07:55 blackserver kernel: [  130.656903] ata8.00: cmd 60/08:78:20:79:a8/00:00:03:00:00/40 tag 15 ncq 4096 in
Sep 22 00:07:55 blackserver kernel: [  130.656903]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:55 blackserver kernel: [  130.656906] ata8.00: status: { DRDY }
Sep 22 00:07:55 blackserver kernel: [  130.656909] ata8.00: failed command: READ FPDMA QUEUED
Sep 22 00:07:55 blackserver kernel: [  130.656914] ata8.00: cmd 60/60:80:a0:4b:f6/00:00:00:00:00/40 tag 16 ncq 49152 in
Sep 22 00:07:55 blackserver kernel: [  130.656914]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:07:55 blackserver kernel: [  130.656916] ata8.00: status: { DRDY }
Sep 22 00:07:55 blackserver kernel: [  130.656918] ata8.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:07:55 blackserver kernel: [  130.656923] ata8.00: cmd 61/e0:88:00:50:fa/01:00:00:00:00/40 tag 17 ncq 245760 out
Sep 22 00:07:55 blackserver kernel: [  130.656923]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:55 blackserver kernel: [  130.656926] ata8.00: status: { DRDY }
Sep 22 00:07:55 blackserver kernel: [  130.656928] ata8.00: failed command: READ FPDMA QUEUED
Sep 22 00:07:55 blackserver kernel: [  130.656932] ata8.00: cmd 60/18:90:d0:29:77/00:00:03:00:00/40 tag 18 ncq 12288 in
Sep 22 00:07:55 blackserver kernel: [  130.656932]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:55 blackserver kernel: [  130.656935] ata8.00: status: { DRDY }
Sep 22 00:07:55 blackserver kernel: [  130.656937] ata8.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:07:55 blackserver kernel: [  130.656941] ata8.00: cmd 61/08:98:28:18:6f/00:00:03:00:00/40 tag 19 ncq 4096 out
Sep 22 00:07:55 blackserver kernel: [  130.656941]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:55 blackserver kernel: [  130.656944] ata8.00: status: { DRDY }
Sep 22 00:07:55 blackserver kernel: [  130.656946] ata8.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:07:55 blackserver kernel: [  130.656950] ata8.00: cmd 61/08:a0:88:1b:6f/00:00:03:00:00/40 tag 20 ncq 4096 out
Sep 22 00:07:55 blackserver kernel: [  130.656950]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:55 blackserver kernel: [  130.656952] ata8.00: status: { DRDY }
Sep 22 00:07:55 blackserver kernel: [  130.656954] ata8.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:07:55 blackserver kernel: [  130.656959] ata8.00: cmd 61/08:a8:d0:20:6f/00:00:03:00:00/40 tag 21 ncq 4096 out
Sep 22 00:07:55 blackserver kernel: [  130.656959]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:07:55 blackserver kernel: [  130.656961] ata8.00: status: { DRDY }
Sep 22 00:07:55 blackserver kernel: [  130.656966] ata8: hard resetting link
Sep 22 00:07:55 blackserver kernel: [  130.984625] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:07:55 blackserver kernel: [  130.986438] ata8.00: configured for UDMA/133
Sep 22 00:07:55 blackserver kernel: [  130.986590] ata8.00: device reported invalid CHS sector 0
Sep 22 00:07:55 blackserver kernel: [  130.986595] ata8.00: device reported invalid CHS sector 0
Sep 22 00:07:55 blackserver kernel: [  130.986598] ata8.00: device reported invalid CHS sector 0
Sep 22 00:07:55 blackserver kernel: [  130.986600] ata8.00: device reported invalid CHS sector 0
Sep 22 00:07:55 blackserver kernel: [  130.986602] ata8.00: device reported invalid CHS sector 0
Sep 22 00:07:55 blackserver kernel: [  130.986604] ata8.00: device reported invalid CHS sector 0
Sep 22 00:07:55 blackserver kernel: [  130.986605] ata8.00: device reported invalid CHS sector 0
Sep 22 00:07:55 blackserver kernel: [  130.986615] ata8: EH complete
Sep 22 00:08:26 blackserver kernel: [  161.635956] ata10.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x0 action 0x6 frozen
Sep 22 00:08:26 blackserver kernel: [  161.635964] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.635970] ata10.00: cmd 61/08:00:88:95:50/00:00:03:00:00/40 tag 0 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.635970]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.635974] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.635976] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.635981] ata10.00: cmd 61/e0:08:00:68:fa/01:00:00:00:00/40 tag 1 ncq 245760 out
Sep 22 00:08:26 blackserver kernel: [  161.635981]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.635983] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.635986] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.635990] ata10.00: cmd 60/08:10:68:0c:e4/00:00:00:00:00/40 tag 2 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.635990]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.635993] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.635995] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.635999] ata10.00: cmd 60/08:18:80:92:50/00:00:03:00:00/40 tag 3 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.635999]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636002] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636004] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636008] ata10.00: cmd 60/08:20:48:9d:50/00:00:03:00:00/40 tag 4 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636008]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636011] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636013] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636017] ata10.00: cmd 60/08:28:38:9e:50/00:00:03:00:00/40 tag 5 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636017]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636020] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636022] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636026] ata10.00: cmd 60/08:30:68:9f:50/00:00:03:00:00/40 tag 6 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636026]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636028] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636030] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636035] ata10.00: cmd 60/08:38:a0:a2:50/00:00:03:00:00/40 tag 7 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636035]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636037] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636039] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636044] ata10.00: cmd 60/08:40:f0:a2:50/00:00:03:00:00/40 tag 8 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636044]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636046] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636048] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636053] ata10.00: cmd 60/08:48:18:a3:50/00:00:03:00:00/40 tag 9 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636053]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636055] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636057] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636062] ata10.00: cmd 60/08:50:e0:ad:50/00:00:03:00:00/40 tag 10 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636062]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636064] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636066] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636071] ata10.00: cmd 60/08:58:f0:b2:50/00:00:03:00:00/40 tag 11 ncq 4096 in
Sep 22 00:08:26 blackserver kernel: [  161.636071]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636073] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636075] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636080] ata10.00: cmd 61/08:60:38:94:50/00:00:03:00:00/40 tag 12 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636080]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636082] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636084] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636089] ata10.00: cmd 61/20:68:e0:65:fa/02:00:00:00:00/40 tag 13 ncq 278528 out
Sep 22 00:08:26 blackserver kernel: [  161.636089]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636091] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636093] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636098] ata10.00: cmd 61/18:70:20:94:50/00:00:03:00:00/40 tag 14 ncq 12288 out
Sep 22 00:08:26 blackserver kernel: [  161.636098]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636100] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636102] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636107] ata10.00: cmd 61/08:78:58:94:50/00:00:03:00:00/40 tag 15 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636107]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636109] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636111] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636116] ata10.00: cmd 61/18:80:80:94:50/00:00:03:00:00/40 tag 16 ncq 12288 out
Sep 22 00:08:26 blackserver kernel: [  161.636116]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636118] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636120] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636125] ata10.00: cmd 61/08:88:a8:94:50/00:00:03:00:00/40 tag 17 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636125]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636127] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636129] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636134] ata10.00: cmd 61/08:90:c8:94:50/00:00:03:00:00/40 tag 18 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636134]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636136] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636138] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636142] ata10.00: cmd 61/08:98:30:95:50/00:00:03:00:00/40 tag 19 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636142]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636145] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636147] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636151] ata10.00: cmd 61/08:a0:58:95:50/00:00:03:00:00/40 tag 20 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636151]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636154] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636156] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636160] ata10.00: cmd 61/08:a8:78:95:50/00:00:03:00:00/40 tag 21 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636160]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636163] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636165] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636169] ata10.00: cmd 61/10:b0:a0:e3:54/00:00:03:00:00/40 tag 22 ncq 8192 out
Sep 22 00:08:26 blackserver kernel: [  161.636169]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636172] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636174] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636178] ata10.00: cmd 61/08:b8:80:9a:50/00:00:03:00:00/40 tag 23 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636178]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636180] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636182] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636187] ata10.00: cmd 61/08:c0:d8:9a:50/00:00:03:00:00/40 tag 24 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636187]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636189] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636191] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636196] ata10.00: cmd 61/08:c8:08:bb:50/00:00:03:00:00/40 tag 25 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636196]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636198] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636200] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636205] ata10.00: cmd 61/08:d0:58:bb:50/00:00:03:00:00/40 tag 26 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636205]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636207] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636209] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636214] ata10.00: cmd 61/08:d8:f8:ca:50/00:00:03:00:00/40 tag 27 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636214]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636216] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636218] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636223] ata10.00: cmd 61/08:e0:50:cb:50/00:00:03:00:00/40 tag 28 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636223]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636225] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636227] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636232] ata10.00: cmd 61/08:e8:90:98:50/00:00:03:00:00/40 tag 29 ncq 4096 out
Sep 22 00:08:26 blackserver kernel: [  161.636232]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636234] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636236] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:08:26 blackserver kernel: [  161.636240] ata10.00: cmd 61/10:f0:48:aa:50/00:00:03:00:00/40 tag 30 ncq 8192 out
Sep 22 00:08:26 blackserver kernel: [  161.636240]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:08:26 blackserver kernel: [  161.636243] ata10.00: status: { DRDY }
Sep 22 00:08:26 blackserver kernel: [  161.636248] ata10: hard resetting link
Sep 22 00:08:26 blackserver kernel: [  161.963708] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:08:26 blackserver kernel: [  161.965395] ata10.00: configured for UDMA/133
Sep 22 00:08:26 blackserver kernel: [  161.965527] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965531] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965533] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965535] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965537] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965539] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965541] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965543] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965544] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965546] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965548] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965550] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965552] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965555] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965557] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965559] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965561] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965562] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965564] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965566] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965568] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965570] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965572] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965574] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965576] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965578] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965579] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965581] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965583] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965585] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965587] ata10.00: device reported invalid CHS sector 0
Sep 22 00:08:26 blackserver kernel: [  161.965603] ata10: EH complete
Sep 22 00:09:12 blackserver kernel: [  207.614938] ata10.00: NCQ disabled due to excessive errors
Sep 22 00:09:12 blackserver kernel: [  207.614945] ata10.00: exception Emask 0x0 SAct 0xf00 SErr 0x0 action 0x6 frozen
Sep 22 00:09:12 blackserver kernel: [  207.614950] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:09:12 blackserver kernel: [  207.614956] ata10.00: cmd 61/20:40:e0:ed:00/00:00:01:00:00/40 tag 8 ncq 16384 out
Sep 22 00:09:12 blackserver kernel: [  207.614956]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:09:12 blackserver kernel: [  207.614959] ata10.00: status: { DRDY }
Sep 22 00:09:12 blackserver kernel: [  207.614961] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:09:12 blackserver kernel: [  207.614966] ata10.00: cmd 61/00:48:00:ee:00/02:00:01:00:00/40 tag 9 ncq 262144 out
Sep 22 00:09:12 blackserver kernel: [  207.614966]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:09:12 blackserver kernel: [  207.614969] ata10.00: status: { DRDY }
Sep 22 00:09:12 blackserver kernel: [  207.614971] ata10.00: failed command: READ FPDMA QUEUED
Sep 22 00:09:12 blackserver kernel: [  207.614976] ata10.00: cmd 60/20:50:e0:f1:00/00:00:01:00:00/40 tag 10 ncq 16384 in
Sep 22 00:09:12 blackserver kernel: [  207.614976]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:09:12 blackserver kernel: [  207.614978] ata10.00: status: { DRDY }
Sep 22 00:09:12 blackserver kernel: [  207.614980] ata10.00: failed command: WRITE FPDMA QUEUED
Sep 22 00:09:12 blackserver kernel: [  207.614985] ata10.00: cmd 61/e0:58:00:f0:00/01:00:01:00:00/40 tag 11 ncq 245760 out
Sep 22 00:09:12 blackserver kernel: [  207.614985]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:09:12 blackserver kernel: [  207.614987] ata10.00: status: { DRDY }
Sep 22 00:09:12 blackserver kernel: [  207.614993] ata10: hard resetting link
Sep 22 00:09:12 blackserver kernel: [  207.942663] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:09:12 blackserver kernel: [  207.944258] ata10.00: configured for UDMA/133
Sep 22 00:09:12 blackserver kernel: [  207.944364] ata10.00: device reported invalid CHS sector 0
Sep 22 00:09:12 blackserver kernel: [  207.944367] ata10.00: device reported invalid CHS sector 0
Sep 22 00:09:12 blackserver kernel: [  207.944369] ata10.00: device reported invalid CHS sector 0
Sep 22 00:09:12 blackserver kernel: [  207.944372] ata10.00: device reported invalid CHS sector 0
Sep 22 00:09:12 blackserver kernel: [  207.944379] ata10: EH complete
Sep 22 00:09:48 blackserver kernel: [  243.569979] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:09:48 blackserver kernel: [  243.569987] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:09:48 blackserver kernel: [  243.569994] ata10.00: cmd 35/00:e0:00:94:09/00:01:01:00:00/e0 tag 21 dma 245760 out
Sep 22 00:09:48 blackserver kernel: [  243.569994]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:09:48 blackserver kernel: [  243.569997] ata10.00: status: { DRDY }
Sep 22 00:09:48 blackserver kernel: [  243.570002] ata10: hard resetting link
Sep 22 00:09:48 blackserver kernel: [  243.897764] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:09:48 blackserver kernel: [  243.899301] ata10.00: configured for UDMA/133
Sep 22 00:09:48 blackserver kernel: [  243.899405] ata10.00: device reported invalid CHS sector 0
Sep 22 00:09:48 blackserver kernel: [  243.899413] ata10: EH complete
Sep 22 00:10:19 blackserver kernel: [  274.569098] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:10:19 blackserver kernel: [  274.569105] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:10:19 blackserver kernel: [  274.569110] ata10.00: cmd 35/00:00:00:b4:09/00:04:01:00:00/e0 tag 7 dma 524288 out
Sep 22 00:10:19 blackserver kernel: [  274.569110]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:10:19 blackserver kernel: [  274.569113] ata10.00: status: { DRDY }
Sep 22 00:10:19 blackserver kernel: [  274.569118] ata10: hard resetting link
Sep 22 00:10:19 blackserver kernel: [  274.896751] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:10:19 blackserver kernel: [  274.898373] ata10.00: configured for UDMA/133
Sep 22 00:10:19 blackserver kernel: [  274.898506] ata10.00: device reported invalid CHS sector 0
Sep 22 00:10:19 blackserver kernel: [  274.898517] ata10: EH complete
Sep 22 00:10:50 blackserver kernel: [  305.520100] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:10:50 blackserver kernel: [  305.520108] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:10:50 blackserver kernel: [  305.520114] ata10.00: cmd 35/00:f0:00:d4:09/00:03:01:00:00/e0 tag 29 dma 516096 out
Sep 22 00:10:50 blackserver kernel: [  305.520114]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:10:50 blackserver kernel: [  305.520117] ata10.00: status: { DRDY }
Sep 22 00:10:50 blackserver kernel: [  305.520122] ata10: hard resetting link
Sep 22 00:10:50 blackserver kernel: [  305.847868] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep 22 00:10:50 blackserver kernel: [  305.849588] ata10.00: configured for UDMA/133
Sep 22 00:10:50 blackserver kernel: [  305.849692] ata10.00: device reported invalid CHS sector 0
Sep 22 00:10:50 blackserver kernel: [  305.849701] ata10: EH complete
Sep 22 00:10:54 blackserver anacron[1753]: Job `cron.daily' started
Sep 22 00:10:54 blackserver anacron[3951]: Updated timestamp for job `cron.daily' to 2014-09-22
Sep 22 00:11:23 blackserver kernel: [  338.517533] ata10: limiting SATA link speed to 3.0 Gbps
Sep 22 00:11:23 blackserver kernel: [  338.517541] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:11:23 blackserver kernel: [  338.517545] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:11:23 blackserver kernel: [  338.517551] ata10.00: cmd 35/00:00:00:e4:0a/00:02:01:00:00/e0 tag 13 dma 262144 out
Sep 22 00:11:23 blackserver kernel: [  338.517551]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:11:23 blackserver kernel: [  338.517554] ata10.00: status: { DRDY }
Sep 22 00:11:23 blackserver kernel: [  338.517559] ata10: hard resetting link
Sep 22 00:11:23 blackserver kernel: [  338.845287] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 320)
Sep 22 00:11:23 blackserver kernel: [  338.847128] ata10.00: configured for UDMA/133
Sep 22 00:11:23 blackserver kernel: [  338.847229] ata10.00: device reported invalid CHS sector 0
Sep 22 00:11:23 blackserver kernel: [  338.847237] ata10: EH complete
Sep 22 00:11:54 blackserver kernel: [  369.532597] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:11:54 blackserver kernel: [  369.532612] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:11:54 blackserver kernel: [  369.532619] ata10.00: cmd 35/00:00:40:e6:0a/00:04:01:00:00/e0 tag 22 dma 524288 out
Sep 22 00:11:54 blackserver kernel: [  369.532619]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:11:54 blackserver kernel: [  369.532622] ata10.00: status: { DRDY }
Sep 22 00:11:54 blackserver kernel: [  369.532627] ata10: hard resetting link
Sep 22 00:11:54 blackserver kernel: [  369.860370] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 320)
Sep 22 00:11:54 blackserver kernel: [  369.862077] ata10.00: configured for UDMA/133
Sep 22 00:11:54 blackserver kernel: [  369.862210] ata10.00: device reported invalid CHS sector 0
Sep 22 00:11:54 blackserver kernel: [  369.862221] ata10: EH complete
Sep 22 00:12:31 blackserver kernel: [  406.558728] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:12:31 blackserver kernel: [  406.558736] ata10.00: failed command: WRITE DMA
Sep 22 00:12:31 blackserver kernel: [  406.558742] ata10.00: cmd ca/00:58:b8:56:77/00:00:00:00:00/e3 tag 4 dma 45056 out
Sep 22 00:12:31 blackserver kernel: [  406.558742]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:12:31 blackserver kernel: [  406.558745] ata10.00: status: { DRDY }
Sep 22 00:12:31 blackserver kernel: [  406.558750] ata10: hard resetting link
Sep 22 00:12:31 blackserver kernel: [  406.886478] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 320)
Sep 22 00:12:31 blackserver kernel: [  406.888299] ata10.00: configured for UDMA/133
Sep 22 00:12:31 blackserver kernel: [  406.888401] ata10.00: device reported invalid CHS sector 0
Sep 22 00:12:31 blackserver kernel: [  406.888411] ata10: EH complete
Sep 22 00:13:02 blackserver kernel: [  437.509855] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:13:02 blackserver kernel: [  437.509862] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:13:02 blackserver kernel: [  437.509868] ata10.00: cmd 35/00:e0:00:84:0b/00:01:01:00:00/e0 tag 4 dma 245760 out
Sep 22 00:13:02 blackserver kernel: [  437.509868]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:13:02 blackserver kernel: [  437.509871] ata10.00: status: { DRDY }
Sep 22 00:13:02 blackserver kernel: [  437.509877] ata10: hard resetting link
Sep 22 00:13:02 blackserver kernel: [  437.837596] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 320)
Sep 22 00:13:02 blackserver kernel: [  437.839354] ata10.00: configured for UDMA/133
Sep 22 00:13:02 blackserver kernel: [  437.839457] ata10.00: device reported invalid CHS sector 0
Sep 22 00:13:02 blackserver kernel: [  437.839465] ata10: EH complete
Sep 22 00:13:34 blackserver kernel: [  469.396156] ata10: limiting SATA link speed to 1.5 Gbps
Sep 22 00:13:34 blackserver kernel: [  469.396164] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:13:34 blackserver kernel: [  469.396169] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:13:34 blackserver kernel: [  469.396175] ata10.00: cmd 35/00:20:e0:3d:0c/00:02:01:00:00/e0 tag 15 dma 278528 out
Sep 22 00:13:34 blackserver kernel: [  469.396175]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Sep 22 00:13:34 blackserver kernel: [  469.396178] ata10.00: status: { DRDY }
Sep 22 00:13:34 blackserver kernel: [  469.396183] ata10: hard resetting link
Sep 22 00:13:34 blackserver kernel: [  469.723889] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
Sep 22 00:13:34 blackserver kernel: [  469.725673] ata10.00: configured for UDMA/133
Sep 22 00:13:34 blackserver kernel: [  469.725777] ata10.00: device reported invalid CHS sector 0
Sep 22 00:13:34 blackserver kernel: [  469.725785] ata10: EH complete
Sep 22 00:14:05 blackserver kernel: [  500.435178] ata10.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Sep 22 00:14:05 blackserver kernel: [  500.435185] ata10.00: failed command: WRITE DMA EXT
Sep 22 00:14:05 blackserver kernel: [  500.435192] ata10.00: cmd 35/00:00:00:54:0c/00:04:01:00:00/e0 tag 0 dma 524288 out
Sep 22 00:14:05 blackserver kernel: [  500.435192]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Sep 22 00:14:05 blackserver kernel: [  500.435195] ata10.00: status: { DRDY }
Sep 22 00:14:05 blackserver kernel: [  500.435200] ata10: hard resetting link
Sep 22 00:14:05 blackserver kernel: [  500.762901] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 310)
Sep 22 00:14:05 blackserver kernel: [  500.764618] ata10.00: configured for UDMA/133
Sep 22 00:14:05 blackserver kernel: [  500.764721] ata10.00: device reported invalid CHS sector 0
Sep 22 00:14:05 blackserver kernel: [  500.764730] ata10: EH complete

```

---

### Post by Michael_McKenney on 2014-09-22
You went from 4 x 2 TB to 4 x 4 TB in RAID 10.  Did you backup your data and break the array then added the 4 drives and recreated the RAID 10 array?   I can't find much about that controller.  Did you RAID configuration have the array at 8 TB?  Did you upgrade the BIOS and RAID controller first?   How did you configure the array in Ubuntu?  Invalid sector 0 could be a bad drive, boot sector virus on the drive, or the drivers can't access the array properly?   How did you add the drives to the array to begin with after you removed the old drives?

---

### Post by KillerKelvUK on 2014-09-22
All software raid.

Original was 4 x 2 TB in RAID 10 running via the SATA controller...went to 4 x 4 TB in RAID 6...my actual migration path was to leave the original disks & RAID alone and build a the new array on the on-board SATA and I just used rsync to copy the data over.  Once this was done I wanted to test the new array using the separate SATA controller so just stopped the array, remove the soft config so Ubuntu wouldn't know of it and disconnected the disks and moved the new disks onto the PCIe controller card.  It was only then when the above errors occurred, as soon as I reverted the connections the errors ceased and haven't represented since.

I've since found [http://www.itechlounge.net/2013/07/linux-ata-failed-command-read-fpdma-queued/](http://www.itechlounge.net/2013/07/linux-ata-failed-command-read-fpdma-queued/) which notes the errors are to do with NCQ support and suggest a fix...I checked and my original 2TB array used NCQ and my new array via the on-board SATA uses NCQ also so this really seems like a problem with my PCIe controller than anything else?

---

### Post by Michael_McKenney on 2014-09-22
Many motherboards don't let you use both on-board RAID controllers at the same time.  You will get RAID errors.   If you want more than one RAID array, you need to get a PCIe SATA RAID controller.  I use the LSI Logic 8708EM2 SATA/SAS RAID 128 MB battery cached controller at home on my main workstation.  I have SAS drives on it.  It can handle many RAID arrays at one time.  I have three sets of disks in RAID 1.

---

