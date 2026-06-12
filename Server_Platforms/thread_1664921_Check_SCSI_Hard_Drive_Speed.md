---
title: "Check SCSI Hard Drive Speed"
date: 2011-01-11
forum: Server Platforms
---

### Post by bsntech on 2011-01-11
OK - something must be wrong here.

When checking my SATA drives, I get 124 MB/s throughput when doing:

sudo hdparm -t /dev/sda

But if I check a SCSI hard drive - Ultra320 drives - it only shows 32 MB/s!  Something must not be right as I was under the impression these drives should put out 10 times that amount - 320 MB/s:

sudo hdparm -t /dev/cciss/c0d0

Apparently hdparm must not work for SCSI drives?

Anyone know how to check SCSI drive performance?

---

### Post by disabledaccount on 2011-01-12
> **bsntech said:**
> OK - something must be wrong here.
But if I check a SCSI hard drive - Ultra320 drives - it only shows 32 MB/s!  Something must not be right as I was under the impression **these drives should put out 10 times that amount - 320 MB/s:**

Apparently hdparm must not work for SCSI drives?
...and who told you this? :rolleyes:

What SCSI drives you have?

This is common misunderstanding of hdd performance testing. Linear transfer "test"(reading/writing physically continous file) has nothing to do with performance, as such situation almost never happens in reality. The key value that performance depends on is seek time - and your 140MB/s 7200rpm shiny SATA drive will die in IOPS tests ;)
This is also the reason why new SSDs are outperforming fastest HDDs - they have seek times <1ms.

You can try seeker - easy tool for simple testing. Complete picture of performance can be obtained only from much more complex test, like those offered by iozone.

---

### Post by Skadork on 2011-01-12
> **tomazzi said:**
> ...and who told you this? :rolleyes:

What SCSI drives you have?

This is common misunderstanding of hdd performance testing. Linear transfer "test"(reading/writing physically continous file) has nothing to do with performance, as such situation almost never happens in reality. The key value that performance depends on is seek time - and your 140MB/s 7200rpm shiny SATA drive will die in IOPS tests ;)
This is also the reason why new SSDs are outperforming fastest HDDs - they have seek times <1ms.

You can try seeker - easy tool for simple testing. Complete picture of performance can be obtained only from much more complex test, like those offered by iozone.


What is the best way to check performance of iops? I'd like to run some test on a raid5 config I have.

---

### Post by disabledaccount on 2011-01-12
delete

---

### Post by disabledaccount on 2011-01-12
delete

---

### Post by disabledaccount on 2011-01-12
< Problems with database - previous posts are broken >

Here You have some overview :)
(some of my old tests)
Personally I prefer IOzone - it has great flexibility and many capabilities

---

### Post by bsntech on 2011-01-12
Nice graphs there!

I do know that the SCSI drives must be working faster than the SATA drives.  I have three SCSI drives in a hardware RAID-5 array and it takes about 18 seconds to boot the system into the GUI (this array is my backup array that I'll use to do full backups of the real system partition).

Compare that to about 30 seconds or more for a standalone SATA drive.  Definitely not an apples-to-apples comparison but that is a 33% difference.

---

### Post by Skadork on 2011-01-12
> **tomazzi said:**
> < Problems with database - previous posts are broken >

Here You have some overview :)
(some of my old tests)
Personally I prefer IOzone - it has great flexibility and many capabilities


That's awesome, thank you!  After I posted originally i started digging around and found *fio*.  

What gets me is I have no idea how to compare my results to what is "acceptable" or "good" with similar setups.  Do you have any suggestions for that?  I found: [http://en.wikipedia.org/wiki/IOPS](http://en.wikipedia.org/wiki/IOPS)  which at least gives me some numbers to compare to, but I'd like to have better comparison.

---

### Post by disabledaccount on 2011-01-12
> **Skadork said:**
> What gets me is I have no idea how to compare my results to what is "acceptable" or "good" with similar setups.  Do you have any suggestions for that?Well, this is problematic - ofc You can find many test results on  the net, but they have been made with different versions of testing  software/OS kernel/hw drivers/file systems etc - and therefore this not  good reference. Generally "raw" tests (bypassing file system layer) are useless, because in reality each particular FS with different configuration of queuing and caching algoritms will give totally different results running on the same hardware.
Sad but true - this not so simple as it would appear, therefore I'm ROFL seeing HD-Tach/HD-Tune/Crystal_Disk_Benchmark "competitions" :)

Those 3D charts above gives pretty good overview of how your hardware will behave under different load types, as only internal drive cache is working.

---

