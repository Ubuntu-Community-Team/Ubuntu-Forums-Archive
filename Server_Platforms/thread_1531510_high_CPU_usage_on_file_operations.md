---
title: "high CPU usage on file operations"
date: 2010-07-15
forum: Server Platforms
---

### Post by boran_blok on 2010-07-15
I am experiencing a very high CPU load on disk operations and I was wondering if this is normal.

For instance copying 3.3 GB of files to another directory takes around 3 minuts (approx 20 MB/sec) and causes the following top:

```
 3368 ben       20   0 13936  928  724 D 54.9  0.2   0:12.71 cp
 3350 root      20   0     0    0    0 S 11.9  0.0   0:20.30 flush-8:32
   28 root      20   0     0    0    0 S 10.6  0.0   2:33.49 kswapd0
```

There is also very high CPU load when copying files to and from the disks using samba. (Which I think is not due to samba but rather due to the I/O CPU usage)
This is how top looks then:
```
 3349 ben       20   0 94764 4172 2964 R 82.3  0.9   0:08.26 smbd
 3370 root      20   0     0    0    0 S  9.6  0.0   0:00.78 flush-8:32
   28 root      20   0     0    0    0 S  6.0  0.0   2:46.61 kswapd0
```

It looks like DMA is enabled, this is the output from dmesg | grep DMA

```
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 100 pages reserved
[    0.000000]   DMA zone: 3827 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1624 pages used for memmap
[    0.000000]   DMA32 zone: 117112 pages, LIFO batch:31
[    0.000000] Policy zone: DMA32
[    1.359896] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.390462] ata1: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff900 irq 22
[    1.390512] ata2: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff980 irq 22
[    1.390562] ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 22
[    1.390611] ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 22
[    1.413280] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.413326] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.900579] ata5.00: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-116  0122, E1.22, max UDMA/66
[    1.940603] ata5.00: configured for UDMA/66
[    2.102204] ata1.00: ATA-7: Maxtor 6L300S0, BANC1G10, max UDMA/133
[    2.102354] ata2.00: ATA-7: Maxtor 6L300S0, BANC1G10, max UDMA/133
[    2.105548] ata2.00: configured for UDMA/133
[    2.105869] ata1.00: configured for UDMA/133
[    2.123644] ata4.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    2.127705] ata4.00: configured for UDMA/133
```

One one hand the performance I am seeing is not abysmal (20 mb/sec local, 25 mb/sec write speed and 45 mb/sec read speed using samba)
On the other hand this hardware did a lot better when it was a windows box (80 mb/sec read/write speed using file sharing) so I know it can do better and that is a bit frustrating.

Right now the file system is ext3 for the data disks and ext4 for the OS disk woud changing filesystems on the data disks help ? (To JFS or XFS for instance)


Some basic stats of the machine:
OS: Ubuntu Server 10.04 (Linux version 2.6.32-21-server (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010)
CPU: AMD Sempron(tm) LE-1150
Memory: 512 MB DDR2 (Single channel)
OS disk: Memory stick 4GB
Data disk 1: 1.5 TB
Data disk 2: raid 1 array of 2 300 GB disks
Network connection: onboard gigabit ethernet 

I do not know exactly how I would get more specific info (without opening the case) if this is needed let me know.

---

