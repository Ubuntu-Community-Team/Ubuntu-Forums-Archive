---
title: "Ubuntu 7.10 and Emulex drivers"
date: 2007-11-07
forum: Server Platforms
---

### Post by jhenes on 2007-11-07
Hi! 
After running Ubuntu 5.10 on my Compaq servers / MSA1000 SAN for years, I had to update to a supported version - 7.10. After the upgrade one of the drives is impossible to mount and the following errors show up in my logs : 
 
-- 
[ 32.584684] lpfc 0000:02:09.0: 1:1303 Link Up Event x1 received Data: x1 x1 x0 x0 
[ 32.692331] scsi 1:0:0:0: RAID COMPAQ MSA1000 4.48 PQ: 0 ANSI: 4 
[ 32.693659] scsi 1:0:0:1: Direct-Access COMPAQ MSA1000 VOLUME 4.48 PQ: 0 ANSI: 4 
[ 32.694460] scsi 1:0:0:2: Direct-Access COMPAQ MSA1000 VOLUME 4.48 PQ: 0 ANSI: 4 
[ 52.979112] ACPI: PCI Interrupt 0000:07:07.0[A] -> GSI 24 (level, low) -> IRQ 20 
[ 52.981130] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 30 (level, low) -> IRQ 21 
[ 52.981150] cpqphp: Hot Plug Subsystem Device ID: a2f8 
[ 52.981159] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 2 
[ 52.981176] PCI: Using BIOS Interrupt Routing Table 
[ 52.981328] PCI: Using BIOS Interrupt Routing Table 
[ 53.224052] e1000: 0000:07:07.0: e1000_probe: (PCI:66MHz:64-bit) 00:02:a5:42:4a:8d 
[ 53.227116] scsi 1:0:0:0: Attached scsi generic sg0 type 12 
[ 53.227559] scsi 1:0:0:1: Attached scsi generic sg1 type 0 
[ 53.228012] scsi 1:0:0:2: Attached scsi generic sg2 type 0 
[ 53.264427] libata version 2.20 loaded. 
[ 53.273935] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012800 irq 14 
[ 53.274016] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012808 irq 15 
[ 53.274054] scsi2 : pata_serverworks 
[ 53.286253] SCSI device sda: 3727729008 512-byte hdwr sectors (1908597 MB) 
[ 53.286456] sda: Write Protect is off 
[ 53.286463] sda: Mode Sense: 83 00 00 08 
[ 53.287855] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 53.288543] SCSI device sda: 3727729008 512-byte hdwr sectors (1908597 MB) 
[ 53.288938] sda: Write Protect is off 
[ 53.288946] sda: Mode Sense: 83 00 00 08 
[ 53.289306] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 53.289317] sda: sda1 
[ 53.291936] sd 1:0:0:1: Attached scsi disk sda 
[ 53.294258] SCSI device sdb: 1849417856 512-byte hdwr sectors (946902 MB) 
[ 53.294438] sdb: Write Protect is off 
[ 53.294446] sdb: Mode Sense: 83 00 00 08 
[ 53.294779] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 53.297179] SCSI device sdb: 1849417856 512-byte hdwr sectors (946902 MB) 
[ 53.297348] sdb: Write Protect is off 
[ 53.297355] sdb: Mode Sense: 83 00 00 08 
[ 53.297681] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 53.297692] sdb:<6>sd 1:0:0:2: SCSI error: return code = 0x08000002 
[ 53.297874] sdb: Current: sense key: Hardware Error 
[ 53.297882] Additional sense: Internal target failure 
[ 53.297905] end_request: I/O error, dev sdb, sector 0 
[ 53.297914] Buffer I/O error on device sdb, logical block 0 
[ 53.298198] sd 1:0:0:2: SCSI error: return code = 0x08000002 
[ 53.298205] sdb: Current: sense key: Hardware Error 
[ 53.298212] Additional sense: Internal target failure 
[ 53.298224] end_request: I/O error, dev sdb, sector 0 
[ 53.298232] Buffer I/O error on device sdb, logical block 0 
[ 53.298512] sd 1:0:0:2: SCSI error: return code = 0x08000002 
[ 53.298520] sdb: Current: sense key: Hardware Error 
[ 53.298526] Additional sense: Internal target failure 
[ 53.298538] end_request: I/O error, dev sdb, sector 0 
[ 53.298546] Buffer I/O error on device sdb, logical block 0 
[ 53.298826] sd 1:0:0:2: SCSI error: return code = 0x08000002 
[ 53.298834] sdb: Current: sense key: Hardware Error 
[ 53.298840] Additional sense: Internal target failure 
[ 53.298853] end_request: I/O error, dev sdb, sector 0 
[ 53.298860] Buffer I/O error on device sdb, logical block 0 
[ 53.299139] sd 1:0:0:2: SCSI error: return code = 0x08000002 
.. Etc... 
----- 
On the console The message : 
137.999809] rport-0:0-2: blocked FC remote port time out: removing rport  
[ 138.939309] rport-0:0-5: blocked FC remote port time out: removing rport  
[ 139.519012] rport-0:0-3: blocked FC remote port time out: removing rport 
--- 
The funny thing is that "sda" works just fine, but "sdb" does not.  
 
When checking the Hardware via the management systems everything is reported to be ok.... 
 
I am totally lost and hope that some of you might be able to help me. 
 
Best regards, 
 
Johan

---

