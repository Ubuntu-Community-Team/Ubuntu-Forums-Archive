---
title: "Ubuntu freezes when copying from RAID5 to other device"
date: 2009-05-17
forum: Server Platforms
---

### Post by kaspar128 on 2009-05-17
My company uses an old Hewlett/Packard proliant ML350(G2) as fileserver(samba/proftpd/pptpd/rsync/ssh etc..). I installed Ubuntu8.10 (intrepid Ibex-server edition) on it and it is running for a few months now. It uses a RAID5 with the ext3 filesystem as system root.
We needed more diskspace for our work so i mounted 2 extra ide-disks(also ext3 formatted) in it. Everything runs smoothly but whenever I transfer files from the RAID5 device to an IDE-drive, the whole system freezes!!

The RAID5 is maintained by a PCI(hardware) device, the "Smart Array 5i/532-controller".
At first I thought it was due to a powershortage(the server is running 3 scsi-raids + 2 ide's), but that doesn't seem to be the problem. The logfiles don't give any information either.
The traffic of all drives over the LAN(samba) and WAN (rsync over ssh) easily exceeds several gigabytes per day and this doesn't give any trouble at all. But when i copy 200mb-file from /dev/cciss/c0d0p1 to, for example, /dev/sda1 it always results in a complete freeze/hard-lock a few seconds after the copying-process starts.
Copying from one of the IDEdrives to the RAID5-drive works without any problems
please help....

---

### Post by kaspar128 on 2009-05-19
I fiddled a bit with hdparm but no solution so far. It only happens with large files, so it probably has something to do with memory or buffering. I read somewhere that, in that case, you can try to adjust settings in the kernel.
But I don't know how to do this or where to start. 
Does anyone have some clues or some commands to dig a little deeper?

I haven't found a way to get more info of the RAID5-device but this is the output of 'hdparm -i' of the two ide-disks:
```

/dev/sda:

 Model=WDC WD1600AAJB-00PVA0                   , FwRev=00.07H00, SerialNo=     WD-WMAP99868948
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


/dev/sdb:

 Model=WDC WD2000JB-32EVA0                     , FwRev=15.05R15, SerialNo=WD-WMAEH1030734
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=390721968
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode


```
Output of lspci:
```

root@proliant:~# lspci
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 06)
00:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:05.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:06.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
00:0f.0 ISA bridge: Broadcom CSB5 South Bridge (rev 92)
**00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 92)**
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 05)
00:0f.3 Host bridge: Broadcom CSB5 LPC bridge
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
**02:04.0 RAID bus controller: Compaq Computer Corporation Smart Array 5i/532 (rev 01)**

```

edit:
hmmmm, now the whole system crashed/freezed 2 times when I respectively:
(1) performed a large 'rsync' via ssh over internet to /dev/sda1,
(2) tried a  e2fsck on /dev/sda1,

is something wrong with the driver of this device, or the disc itself?
```

*-disk:0
                description: ATA Disk
                product: WDC WD1600AAJB-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 00.0
                serial: WD-WMAP99868948
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fa0dce0f

```

---

### Post by kaspar128 on 2009-06-12
Hooray, i can copy without crashing. The problem hadn't anything to do with the raid5 but with the ata-drivers/modules. I messed around for ages but when I changed the order of the modules loaded, the problem seemed solved.
before:
```
root@proliant:~# lsmod | grep -i ^libata
libata                176032  3 ata_generic,pata_acpi,pata_serverworks
```
after:
```
root@proliant:~# lsmod | grep -i ^libata
libata                176032  3 pata_serverworks,ata_generic,pata_acpi
```
This solved the freezing of the system while writing to disk. The only problem now is that file transfer is very slow. Only a few Mb per second. Turns out DMA on the drives is disabled:
```
root@proliant:~# dmesg | grep DMA
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[   12.467620] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[   12.467627] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[   12.640289] ata1.00: ATAPI: Compaq  CRD-8402B, 1.03, max MWDMA2
[   12.680281] ata1.00: configured for MWDMA2
[   12.895275] ata2.00: ATA-7: WDC WD1600AAJB-00PVA0, 00.07H00, max UDMA/100
[   12.896403] ata2.01: ATA-6: WDC WD2000JB-32EVA0, 15.05R15, max UDMA/100
[   12.896435] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   12.896444] ata2.01: simplex DMA is claimed by other device, disabling DMA

```
After some googling it seems that the ata_generic, or the pata_acpi-module is 'claiming' the 'simplex DMA', or something. When I blacklist on of those, DMA comes available again but then the system crashes/freezes immediately after large file transfers. Even on a 'hdparm -Tt /dev/sda'. So basically i'm stuck now with two very slow drives.. It looks like they just can't handle the DMA-mode. 

hdparm -d1 /dev/sda
always results in:

```
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
```

I know my story looks a bit messy but any help would be highly appreciated :-)

---

