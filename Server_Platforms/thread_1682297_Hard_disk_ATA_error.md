---
title: "Hard disk ATA error"
date: 2011-02-05
forum: Server Platforms
---

### Post by Xylian on 2011-02-05
Hi,
today I've noticed in the syslog tons of ATA errors of the following type:
```

 ata1.00: status: { DRDY ERR }
 ata1.00: error: { UNC }
 ata1.00: FORCE: xfer_mask set to udma/66
 ata1.00: configured for UDMA/66
 ata1: EH complete
 ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
 ata1.00: BMDMA stat 0x25
 ata1.00: failed command: READ DMA
 ata1.00: cmd c8/00:08:40:05:00/00:00:00:00:00/e0 tag 0 dma 409
6 in
          res 51/40:06:42:05:00/00:00:00:00:00/e0 Emask 0x9 (me
dia error)
 ata1.00: status: { DRDY ERR }
 ata1.00: error: { UNC }
 ata1.00: FORCE: xfer_mask set to udma/66
 ata1.00: configured for UDMA/66
 sd 0:0:0:0: [sda] Unhandled sense code
 sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SE
NSE
 sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descript
or]
 Descriptor sense data with sense descriptors (in hex):
         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
         00 00 05 42 
 sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto re
allocate failed

```

Do you think it is effectively my hard drive (/dev/sda) which is broken or could it be a kernel bug introduced in 2.6.35-25, since I've never seen it before (2.6.35-24 and before)? I've tried also to add the following kernel parameters, since sometime I've read that noacpi helps with this errors:
```

libata.noacpi=1 libata.force=1:short40c,1:udma/66

```
(short40c is right for a short 40-cables cable?)
The errors seems to have reduced a little bit, but the command *hdparm -tT /dev/sda* still does not work anymore (previously it worked) and produces the ATA errors:
```

# hdparm -tT /dev/sda

/dev/sda:
read(2097152) returned 688128 bytes
 Timing buffered disk reads:  read() failed: Input/output error

(the following messages are in /var/log/syslog)
 [...]
 ata1.00: status: { DRDY ERR }
 ata1.00: error: { UNC }
 ata1.00: FORCE: xfer_mask set to udma/66
 ata1.00: configured for UDMA/66
 sd 0:0:0:0: [sda] Unhandled sense code
 sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SE
NSE
 sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descript
or]
 Descriptor sense data with sense descriptors (in hex):
         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
         00 00 05 42 
 sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto re
allocate failed
 sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 00 05 00 00 01 00 00
 end_request: I/O error, dev sda, sector 1346
 Buffer I/O error on device sda, logical block 168
 Buffer I/O error on device sda, logical block 169
 Buffer I/O error on device sda, logical block 170
 Buffer I/O error on device sda, logical block 171
 Buffer I/O error on device sda, logical block 172
 Buffer I/O error on device sda, logical block 173
 Buffer I/O error on device sda, logical block 174
 Buffer I/O error on device sda, logical block 175
 Buffer I/O error on device sda, logical block 176
 Buffer I/O error on device sda, logical block 177
 ata1: EH complete
 ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
 ata1.00: BMDMA stat 0x25
 [...]

```

Any idea? Should I better order a new 2.5" PATA disk?

---

### Post by Vegan on 2011-02-05
ATA disks are starting to become rare as SATA has taken over with sheer volumes.

I have a page targeting Windows users on hard drive reliability and the links are fine for Linux users to get bootable CD disks with respective makers tools.

[http://www.windows-it.tk/papers/disk-reliability.php]("http://www.windows-it.tk/papers/disk-reliability.php")


I am eventually upgrading my server to SATA, the machine I have now is old as the hills. The problem I have is not capacity, the machine is far from saturated.

---

