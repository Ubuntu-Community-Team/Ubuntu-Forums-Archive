---
title: "Hard drive performance problem"
date: 2008-08-12
forum: Server Platforms
---

### Post by b0ertje on 2008-08-12
Hello everybody,

I have a weird problem on on of my servers and can't quite explain what is causing it. I did search the forums and the web and found many problems with similar symptoms, however the cause seems to be different. If I didn't search thoroughly enough please feel free to point me to threads where my problem has been discussed already!

So I'm having a server at a site that has two ide drives attached to it, both on their own channel. They are configured in raid1 mode via software and on top of the created md0 volume there is lvm taking care of the actual partitions. The setup itself works fine. Unfortunately, my HDD performance is pretty weak and I desperately need to improve it somehow. But I don't know why it's that slow in the first place. Here is some output.

**dmesg (ata1) and hdparm info/timing:**
```
[   35.710103] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   35.931188] ata1.00: ATA-7: ST3500630A, 3.AAF, max UDMA/100
[   35.931258] ata1.00: 976773168 sectors, multi 16: LBA48 
[   36.022606] ata1.00: configured for UDMA/100

/dev/sda:

 Model=ST3500630A                              , FwRev=3.AAF   , SerialNo=            9QG994P7
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

 Timing cached reads:   362 MB in  2.00 seconds = 181.01 MB/sec
 Timing buffered disk reads:   78 MB in  3.14 seconds =  24.86 MB/sec

```

**dmesg (ata2) and hdparm info/timing:**
```
[   35.710160] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   36.243080] ata2.00: ATA-7: ST3500630A, 3.AAF, max UDMA/100
[   36.243149] ata2.00: 976773168 sectors, multi 16: LBA48 
[   36.326196] ata2.00: configured for UDMA/100

/dev/sdb:

 Model=ST3500630A                              , FwRev=3.AAF   , SerialNo=            9QG994S5
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

 Timing cached reads:   352 MB in  2.01 seconds = 175.31 MB/sec
 Timing buffered disk reads:  104 MB in  3.13 seconds =  33.17 MB/sec

```

The performance sometimes even is only a fith of the above far below 10MB/s in buffered reads. As far as I read it DMA is enabled on both drives so I wonder what could cause this bad performance. The drives are new, the cables are new. And as a comparison on another, much older machine (dapper) I get much better numbers:

```

/dev/hda:
 Timing cached reads:   2576 MB in  2.00 seconds = 1287.92 MB/sec
 Timing buffered disk reads:  172 MB in  3.02 seconds =  57.03 MB/sec

/dev/hdb:
 Timing cached reads:   2596 MB in  2.00 seconds = 1297.92 MB/sec
 Timing buffered disk reads:  168 MB in  3.03 seconds =  55.41 MB/sec

/dev/hdc:
 Timing cached reads:   2584 MB in  2.00 seconds = 1291.92 MB/sec
 Timing buffered disk reads:  170 MB in  3.01 seconds =  56.44 MB/sec

/dev/hdd:
 Timing cached reads:   2712 MB in  2.00 seconds = 1355.92 MB/sec
 Timing buffered disk reads:  212 MB in  3.03 seconds =  69.92 MB/sec

/dev/sda:
 Timing cached reads:   2588 MB in  2.00 seconds = 1293.92 MB/sec
 Timing buffered disk reads:  156 MB in  3.02 seconds =  51.72 MB/sec

```

Can somebody help me to track this down? I'm not to experienced with the new libata and hdparm seems to have a lot of trouble with it.

---

### Post by promodus on 2008-08-13
Maybe try a spare?

Also possibly try a different HD Cable.

Another utility for benchmarking drives, bonnie++
[http://www.coker.com.au/bonnie++/](http://www.coker.com.au/bonnie++/)

apt-get install bonnie++

---

### Post by b0ertje on 2008-08-13
Thanks for your reply. I don't think a spare can improve performance. The cables also work flawlessly. In the end, UDMA5 seems to be enabled and I had no performance issues on windows. I think it's some problem with the new libata though I don't have enough in-depth knowledge to prove that - I desperately need to fix it though :(

In case it helps, here is the bonnie test output with filesize double the ram:

```

Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ide.hardy        1G  7038  36 14385  18  5361   4 10500  30 31172  13 255.6   2
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  8831  44 +++++ +++ 10530  46  7428  48 +++++ +++  9132  46

```

And for comparison reasons, the one from the dapper machine I mentioned in my previous post:

```

Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ide.dapper       1G 31632  91 46546  17 20523   5 25635  74 41344   4 153.2   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  2487  97 +++++ +++ +++++ +++  2550  98 +++++ +++  7710  99

```

And a last one done on a fast hardy server machine with sata-drives:

```

Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
sata.hardy       8G 63671  93 67269  15 33862   5 54115  68 79544   7 358.6   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++

```

One can clearly see the issues in the numbers. Now how to track that down?

---

### Post by b0ertje on 2008-08-19
is nobody here running ubuntu server and able to help me track this down? :(

---

### Post by Krupski on 2008-08-19
> **b0ertje said:**
> is nobody here running ubuntu server and able to help me track this down? :(

Sorry... I run Server, but I use SATA drives...

---

### Post by fjgaude on 2008-08-19
The low readings could be caused by errors in the RAM... have you tested your RAM lately?

To have software raid1 be as fast as the individual drives you have to have good CPU and RAM, fast enough to keep up with the drives' demands.

---

### Post by b0ertje on 2008-08-22
Hi again and thanks for you suggestions.

I guess the RAM is ok, I tested it two months ago. However I did change the RAM and double it's amount to be sure.

hdparm did get a little faster, not much:

```

# for i in a b ; do hdparm -Tt /dev/sd$i ; done

/dev/sda:
 Timing cached reads:   368 MB in  2.01 seconds = 183.39 MB/sec
 Timing buffered disk reads:  146 MB in  3.02 seconds =  48.34 MB/sec

/dev/sdb:
 Timing cached reads:   360 MB in  2.00 seconds = 179.95 MB/sec
 Timing buffered disk reads:  150 MB in  3.03 seconds =  49.55 MB/sec

```

And here is the bonnie-run. Since you have the overhead from sw-raid, lvm and the filesystem itself when using it I wouldn't put too much into it. It did improve quite a bit with more RAM but it is still way lower then e.g. machine ide.dapper in my previous posts:

```

Version 1.03b       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ide.hardy        2G 14941  80 32680  47  8957   7 15386  54 57707  24 276.8   2
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 17241  91 +++++ +++ 21589  97 20297  97 +++++ +++ 21189  96

```

The problem remains that the raw speeds of the disks themselves as observed with hdparm are too low and that causes a lot of other problems in the OS at the top. I rechecked all the hw involved so I guess this might be a kernel, namely libata-issue. How could I further track it down?

No guru around here? ;-)

---

### Post by Mrwasab1 on 2008-08-22
Are you using ATA 100 or 133 cables? are they both master drives? what speed are the disks and how big are they?

What sort of performance were you expecting to get from a software RAID 1? usually software RAID 1's are slower as the PCI bus is saturated with multiple copies of the same data as it attempts to mirror. 

Usually the bigger the disks the worse a software RAID 1 will perform, this is probably where hardware RAID come in very useful, as the extra data is managed by the RAID controller and does not have to go over the PCI bus.

also what RAM do you have and how is it configured? if its DDR are they in the correct DIMMS?


im no guru, but these are things ive encountered in the past that can hopefully help you

---

### Post by windependence on 2008-08-22
I agree with Mr. wasabi. Look at all the overhead you have. LVM on top of software RAID and then only on ATA drives? RAID 1 is certainly not know for performance even if it's hardware RAID. Do you reall even NEED RAID or are you counting on it for backup. If so, get yourself another drive and back up to that. RAID is never a substitute for good backups. Better yet, get one more drive and set up RAID 5 if you really think you need it.

-Tim

---

### Post by windependence on 2008-08-22
Sorry, double post.

-Tim

---

### Post by fjgaude on 2008-08-22
Seems your CPU and memory are very slow:

```
Timing cached reads:   368 MB in  2.01 seconds = 183.39 MB/sec

```
This number, 183.39 MB/sec, is lower than anything I've ever seen.

I personally don't think the CPU is able to correctly keep up with what the array is requiring.

Your hdparm tests are run with nothing going on in the backgroune, eh?

---

### Post by b0ertje on 2008-08-23
> **Mrwasab1 said:**
> Are you using ATA 100 or 133 cables? are they both master drives? what speed are the disks and how big are they?

also what RAM do you have and how is it configured? if its DDR are they in the correct DIMMS?

Thanks for your suggestions. The Cables are ATA133 and both drives are single master on seperate channels. This should be the optimal setting. The DDR-RAM is correct and running with 100Mhz*2 - it is an older Athlon. Like I said the hardware is ok and worked flawlessly with other systems. I don't have any other problems than disk performance on Ubuntu server.

> **Mrwasab1 said:**
> What sort of performance were you expecting to get from a software RAID 1?

> **windependence said:**
> I agree with Mr. wasabi. Look at all the overhead you have. LVM on top of software RAID and then only on ATA drives? RAID 1 is certainly not know for performance even if it's hardware RAID.

It isn't the performance of the filesystem as seen in the bonnie tests that is really troubling me. It is the numbers from hdparm. This is the raw speed of the disks sda and sdb - a layer below (software-)raid, lvm and the fs. That should be a lot better imho.

---

### Post by b0ertje on 2008-08-23
> **fjgaude said:**
> This number, 183.39 MB/sec, is lower than anything I've ever seen.

That's what I think too, that is so low I can hardly believe it ;)

CPU and RAM are not too fast but fair enough. It's an Athlon running at 1,25Ghz and 1GB of DDR RAM. The drives are brand new. Mainboard is an Elitegroup K7S5A which proved to have a solid performance in the old days. I should mention that I do get a lot better numbers on an old laptop with slower CPU, slower and less RAM and a poor 2,5" HDD. And - unfortunately - I did get a lot better numbers when Windows was on that machine.

> **fjgaude said:**
> Your hdparm tests are run with nothing going on in the backgroune, eh?

nope, the box is just idling.

---

### Post by fjgaude on 2008-08-23
You have the lastest BIOS update for your motherboard?

---

### Post by b0ertje on 2008-08-25
Yes, the bios is up to date.
The HDs are only making trouble on Ubuntu so I don't think this problem is related to hardware not being set up correctly.

---

