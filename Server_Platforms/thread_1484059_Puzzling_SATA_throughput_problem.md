---
title: "Puzzling SATA throughput problem"
date: 2010-05-15
forum: Server Platforms
---

### Post by iversonm on 2010-05-15
I am building a two machine cluster, and I have a real problem with SATA throughput on a new server I am configuring.

I have two HP DL120 G5s each with 2 1TB SATA drives. The first machine is about 6 months old, and is running 9.10 server, and is performing fine. Below is the output of hdparm:

```
$ sudo hdparm -tT /dev/sda; sudo hdparm -tT /dev/sdb

/dev/sda:
 Timing cached reads:   3982 MB in  2.00 seconds = 1990.98 MB/sec
 Timing buffered disk reads:  370 MB in  3.01 seconds = 123.09 MB/sec

/dev/sdb:
 Timing cached reads:   3950 MB in  2.00 seconds = 1975.56 MB/sec
 Timing buffered disk reads:  368 MB in  3.01 seconds = 122.45 MB/sec

```
The second machine, which is brand new, I installed 10.04 server on. (I intend to upgrade the first machine after I get the second up and running.) However, the disks are running at 1/5 of the speed of the first machine, as shown below:

```
/dev/sda:
 Timing cached reads:   4764 MB in  2.00 seconds = 2382.51 MB/sec
 Timing buffered disk reads:   74 MB in  3.02 seconds =  24.53 MB/sec

/dev/sdb:
 Timing cached reads:   4732 MB in  2.00 seconds = 2366.23 MB/sec
 Timing buffered disk reads:   92 MB in  3.10 seconds =  29.72 MB/sec

```

The disks are different brands on the two machines, (Seagate in the 1st, Samsung on the 2nd) but they are both similar 7200 rpm disks, as shown below. I could imagine a 5 to 10% difference between the two, but not a 5x performance difference.

```
 sudo hdparm -i /dev/sda

/dev/sda:

 Model=SAMSUNG, FwRev=1AA01109, SerialNo=S13PJ1EQ313339
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=32767kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

 sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST31000528AS, FwRev=CC35, SerialNo=9VP1HQ7L
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode


```

I reviewed all of the boot messages in dmesg, and can find no significant difference between the two machines.

Does anyone have any ideas on the root cause of my problem?

---

### Post by iversonm on 2010-05-16
No ideas? 

I think I'm going to try a fresh install to see if that clears up the problem.

---

### Post by vkcaspervk on 2010-05-16
Mines a bit stranger, I built 2 identical computers...

AMD 965, ASUS M4N82 DELUXE, 4 gigs ram, both Hitachi Hard Drives..

Wife's computer...
> Timing cached reads:   7798 MB in  2.00 seconds = 3900.15 MB/sec
Timing buffered disk reads:  364 MB in  3.01 seconds = 121.03 MB/secMy Computer...
> Timing cached reads:   6772 MB in  2.00 seconds = 3386.47 MB/sec
Timing buffered disk reads:  252 MB in  3.03 seconds =  83.18 MB/secTalked to Asus, they claimed it was the board, got the new board, same issue, swapped Hard drives with wife, My computer STILL has a slow speed... So its not the board or the hard drive... At this point I think its the CPU? Tho AMD claimed it cant be the CPU... 
: Shruggs :

I had really bad I/O waits at times, I throttled my SATA to 150 via a jumper and it seems to be better, tho still have slower speeds. Who knows...

---

### Post by lavinog on 2010-05-16
> **iversonm said:**
> 
The disks are different brands on the two machines, (Seagate in the 1st, Samsung on the 2nd) but they are both similar 7200 rpm disks, as shown below. I could imagine a 5 to 10% difference between the two, but not a 5x performance difference.


I am thinking this is the reason.

I know seagate has had firmware updates for some drives that drastically improve performance.
Different manufacturers have different algorithms that may be better than others.

Also check the jumper settings on the back.  Some drives ship with the jumper set to limit to 1.5 gb/s instead of 3

EDIT:
Also the samsung has AdvancedPM enabled, while the seagate doesn't

---

### Post by iversonm on 2010-05-16
> **lavinog said:**
> I am thinking this is the reason.

I know seagate has had firmware updates for some drives that drastically improve performance.
Different manufacturers have different algorithms that may be better than others.

Also check the jumper settings on the back.  Some drives ship with the jumper set to limit to 1.5 gb/s instead of 3

EDIT:
Also the samsung has AdvancedPM enabled, while the seagate doesn't

It doesn't look like the firmware is upgradable on the samsung. 

Also APM doesn't appear to make a difference:

```
$ sudo hdparm -B 255 /dev/sda

/dev/sda:
 setting Advanced Power Management level to disabled
 APM_level	= off
$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   4798 MB in  2.00 seconds = 2399.83 MB/sec
 Timing buffered disk reads:   66 MB in  3.00 seconds =  21.97 MB/sec

```

---

### Post by NullHead on 2010-05-16
I say double check those jumpers. All my new Seagate drives shipped with the 1.5GB/S clip on. They were also fairly difficult to get off.

---

### Post by lavinog on 2010-05-16
> **NullHead said:**
> They were also fairly difficult to get off.
I find using a single staple bent at the end to be fairly effective to remove them.

---

### Post by cascade9 on 2010-05-16
> **lavinog said:**
> I find using a single staple bent at the end to be fairly effective to remove them.

I find a dart is the easier thing. Probably not something most house have hanging around though ;)

---

### Post by iversonm on 2010-05-17
Problem solved. The problem was that I updated the machine BIOS, but did not update the associated BMC firmware update.

After the change, this is what I get:

```
$sudo hdparm -tT /dev/sda; sudo hdparm -tT /dev/sdb

/dev/sda:
 Timing cached reads:   4688 MB in  2.00 seconds = 2344.86 MB/sec
 Timing buffered disk reads:  292 MB in  3.00 seconds =  97.29 MB/sec

/dev/sdb:
 Timing cached reads:   4610 MB in  2.00 seconds = 2305.68 MB/sec
 Timing buffered disk reads:  294 MB in  3.01 seconds =  97.64 MB/sec

```

---

### Post by lavinog on 2010-05-17
Glad you got it fixed.
I am not very familiar with BMC, but why was it only affecting one drive?  Was there a changelog for the firmware update that mentioned this issue?
EDIT:  I guess that can be a common problem.

---

### Post by iversonm on 2010-05-20
> **lavinog said:**
> Glad you got it fixed.
I am not very familiar with BMC, but why was it only affecting one drive? 

It wasn't affecting one drive. I have two identical machines, one with Seagate drives, and one with Samsung drives.

The first machine hit transfer rates around 120MB/s, but the second machine was a paltry 24MB/s.

The firmware fix got the speed of the second machine up to 100MB/s, which is much closer to the performance of the first machine.

---

