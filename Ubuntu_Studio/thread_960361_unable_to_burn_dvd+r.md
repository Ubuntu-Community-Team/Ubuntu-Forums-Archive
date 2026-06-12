---
title: "unable to burn dvd+r"
date: 2008-10-27
forum: Ubuntu Studio
---

### Post by tbugge on 2008-10-27
i have tried a couple of times to burn an ISO file on to a dvd+r but every time it fails :( I have had success using a dvd+rw. Here's the log:

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-21-generic
Devices
-----------------------
TSSTcorp CD/DVDW SH-S162L TS01 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 16.4x1352KBps.
          0/4676345856 ( 0.0%) @0x, remaining ??: ?? RBU 100.0% UBU   0.0%
          0/4676345856 ( 0.0%) @0x, remaining ??: ?? RBU 100.0% UBU   0.0%
          0/4676345856 ( 0.0%) @0x, remaining ??: ?? RBU 100.0% UBU   0.0%
          0/4676345856 ( 0.0%) @0x, remaining ??: ?? RBU 100.0% UBU   0.0%
          0/4676345856 ( 0.0%) @0x, remaining ??: ?? RBU 100.0% UBU   0.0%
          0/4676345856 ( 0.0%) @0x, remaining ??: ?? RBU 100.0% UBU   0.0%
          0/4676345856 ( 0.0%) @0x, remaining ??: ?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error

Anybody can tell me what im doing wrong? I have tried various burning programs, all with the same failure.

thanks :)

---

### Post by KillerKellerjr on 2008-11-10
I too have the same problem, unable to burn to a DVD+R.  I could do it about 2 weeks ago, apparently one of the updates I have applied killed it.  I can burn to DVD+RW with no problem, just not DVD+R.  This is a major problem for me as I burn DVD's all the time, someone please help us as I this must be a big problem I would think.  My errors are identical to those above and it fails in all other burning programs too.  Let us know any other details you may need.

Thanks

---

