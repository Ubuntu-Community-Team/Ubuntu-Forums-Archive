---
title: "Trying to figure out what went wrong"
date: 2011-12-28
forum: Server Platforms
---

### Post by wmcduff on 2011-12-28
Our website went down over Christmas, so I'm in today doing the post-mortem on the server, so to speak.  Actually got the site half-up, but having problems, and don't know the error codes well enough to it not to be mostly gobbledygook.  My theory at the moment is that the MySQL database corrupted due to sectors of the hard drive failing, but...

From syslog:


```
Dec 28 06:37:10 www kernel: [594901.898204] ata2.00: configured for UDMA/133
Dec 28 06:37:10 www kernel: [594901.898220] sd 1:0:0:0: [sda] Result: hostbyte=DID
_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Dec 28 06:37:10 www kernel: [594901.898229] sd 1:0:0:0: [sda] Sense Key : Medium E
rror [current] [descriptor]
Dec 28 06:37:10 www kernel: [594901.898238] Descriptor sense data with sense descr
iptors (in hex):
Dec 28 06:37:10 www kernel: [594901.898269]         72 03 11 04 00 00 00 0c 00 0a 
80 00 00 00 00 00 
Dec 28 06:37:10 www kernel: [594901.898340]         06 8f d6 9f 
Dec 28 06:37:10 www kernel: [594901.898374] sd 1:0:0:0: [sda] Add. Sense: Unrecove
red read error - auto reallocate failed
Dec 28 06:37:10 www kernel: [594901.898385] end_request: I/O error, dev sda, secto
r 110089887
Dec 28 06:37:10 www kernel: [594901.898401] ata2: EH complete
Dec 28 06:37:10 www kernel: [594901.898662] sd 1:0:0:0: [sda] 156250000 512-byte h
ardware sectors (80000 MB)
Dec 28 06:37:10 www kernel: [594901.923322] sd 1:0:0:0: [sda] Write Protect is off
Dec 28 06:37:10 www kernel: [594901.923328] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00
 00
Dec 28 06:37:10 www kernel: [594901.925206] sd 1:0:0:0: [sda] Write cache: enabled
, read cache: enabled, doesn't support DPO or FUA
Dec 28 06:37:10 www kernel: [594901.935124] sd 1:0:0:0: [sda] 156250000 512-byte h
ardware sectors (80000 MB)
Dec 28 06:37:10 www kernel: [594901.935312] sd 1:0:0:0: [sda] Write Protect is off
Dec 28 06:37:10 www kernel: [594901.935318] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00
 00
Dec 28 06:37:10 www kernel: [594901.959755] sd 1:0:0:0: [sda] Write cache: enabled
, read cache: enabled, doesn't support DPO or FUA
Dec 28 06:37:12 www kernel: [594903.702453] ata2.00: exception Emask 0x0 SAct 0x0 
SErr 0x0 action 0x0
Dec 28 06:37:12 www kernel: [594903.702479] ata2.00: BMDMA stat 0x24
Dec 28 06:37:12 www kernel: [594903.702508] ata2.00: cmd c8/00:08:ff:e2:8f/00:00:0
0:00:00/e6 tag 0 dma 4096 in
Dec 28 06:37:12 www kernel: [594903.702513]          res 51/40:00:ff:e2:8f/00:00:0
0:00:00/e6 Emask 0x9 (media error)
Dec 28 06:37:12 www kernel: [594903.702551] ata2.00: status: { DRDY ERR }
Dec 28 06:37:12 www kernel: [594903.702572] ata2.00: error: { UNC }
Dec 28 06:37:12 www kernel: [594903.894785] ata2.00: configured for UDMA/133
Dec 28 06:37:12 www kernel: [594903.894798] ata2: EH complete
Dec 28 06:37:14 www kernel: [594905.216354] ata2.00: exception Emask 0x0 SAct 0x0 
SErr 0x0 action 0x0
Dec 28 06:37:14 www kernel: [594905.216376] ata2.00: BMDMA stat 0x24
Dec 28 06:37:14 www kernel: [594905.216402] ata2.00: cmd c8/00:08:ff:e2:8f/00:00:0
0:00:00/e6 tag 0 dma 4096 in
Dec 28 06:36:12 www kernel: [594759.720703] ata2.00: exception Emask 0x0 SAct 0x0 
SErr 0x0 action 0x0
Dec 28 06:36:22 www kernel: [594759.720730] ata2.00: BMDMA stat 0x24
Dec 28 06:36:22 www kernel: [594759.720759] ata2.00: cmd c8/00:18:7f:d3:8f/00:00:0
0:00:00/e6 tag 0 dma 12288 in
Dec 28 06:36:22 www kernel: [594759.720762]          res 51/40:00:7f:d3:8f/00:00:0
0:00:00/e6 Emask 0x9 (media error)
```

Seemed to loop from there.  Also, when trying to run ```
mysqld start
```

```
111228 11:18:10 [Note] Plugin 'FEDERATED' is disabled.
111228 11:18:10  InnoDB: Initializing buffer pool, size = 8.0M
111228 11:18:10  InnoDB: Completed initialization of buffer pool
InnoDB: Error: tried to read 512 bytes at offset 0 512.
InnoDB: Was only able to read -1.
111228 11:18:19  InnoDB: Operating system error number 5 in a file operation.
InnoDB: Error number 5 means 'Input/output error'.
InnoDB: Some operating system error numbers are described at
InnoDB: http://dev.mysql.com/doc/refman/5.1/en/operating-system-error-codes.html
InnoDB: File operation call: 'read'.
InnoDB: Cannot continue operation.
```

Do you think I'm on the right track?  Any suggestions on what to do?

---

### Post by rubylaser on 2011-12-28
Looks like a failed hard drive.  Have you run smartmontools against it?  I assume you have your code and database backed up.  If so, I'd just throw in a new hard drive and get to reinstalling the OS.  If you don't have a good backup, you'll want to try gddrescue, or some other recovery tool.

---

### Post by wmcduff on 2011-12-28
Weird thing is the hard drive is up and hosting the other website (which runs off a postgresql database).  Partial HD failure?

---

### Post by rubylaser on 2011-12-28
Likely bad sectors as you originally wrote.  That's why I asked about running smartmontools. I'd run a longtest and then view the results once it completes.

---

### Post by wmcduff on 2011-12-30
smartmontools had the drive pass the short and fail the long.  We cloned the drive successfully last night (barely), and the new hard drive is running beautifully.  Thanks for the help!

---

### Post by rubylaser on 2011-12-30
No problem, I'm glad you got it figured out and working again :)

---

