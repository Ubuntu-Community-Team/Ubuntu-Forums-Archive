---
title: "DVD Burn Problems - Input Output etc"
date: 2008-09-28
forum: Ubuntu Studio
---

### Post by 426matt on 2008-09-28
Hello, I have a problem with burning of DVD's with my system. I have two burners, and neither of them will work. I have had Hardy Heron installed for around 6 months now and have not had a problem until recently. Now, when I try to burn I just get error messages with the LG 4163B, or I get what appears to be a burn with the Pioneer DVR-212, but the disc is no good, has errors on it and wont work.

I get input/output error with GnomeBaker, and with K3b I get a disc error and output of:

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-21-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4163B A106 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

PIONEER DVD-RW  DVR-212 1.24 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]
Burned media
-----------------------
DVD+R

K3bIsoImager
-----------------------
mkisofs print size result: 2250290 (4608593920 bytes)
Pipe throughput: 34738176 bytes read, 34733696 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 4.1x1352KBps.
    1114112/4608593920 ( 0.0%) @0.0x, remaining 344:37 RBU 100.0% UBU   2.9%
    1114112/4608593920 ( 0.0%) @0.0x, remaining 551:24 RBU 100.0% UBU 100.0%
    1114112/4608593920 ( 0.0%) @0.0x, remaining 758:11 RBU 100.0% UBU 100.0%
    1114112/4608593920 ( 0.0%) @0.0x, remaining 1033:53 RBU 100.0% UBU 100.0%
    1114112/4608593920 ( 0.0%) @0.0x, remaining 1240:40 RBU 100.0% UBU 100.0%
    1114112/4608593920 ( 0.0%) @0.0x, remaining 1447:26 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=220h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/scd1: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd1=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2250290 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
2250290
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.02% done, estimate finish Sun Sep 28 21:42:15 2008
  0.04% done, estimate finish Sun Sep 28 21:42:15 2008
  0.07% done, estimate finish Sun Sep 28 21:42:15 2008
  0.09% done, estimate finish Sun Sep 28 21:42:15 2008
  0.11% done, estimate finish Sun Sep 28 21:42:15 2008
  0.13% done, estimate finish Sun Sep 28 21:42:15 2008
  0.16% done, estimate finish Sun Sep 28 21:42:15 2008
  0.18% done, estimate finish Sun Sep 28 21:42:15 2008
  0.20% done, estimate finish Sun Sep 28 21:42:15 2008
  0.22% done, estimate finish Sun Sep 28 21:49:44 2008
  0.25% done, estimate finish Sun Sep 28 21:49:03 2008
  0.27% done, estimate finish Sun Sep 28 21:48:29 2008
  0.29% done, estimate finish Sun Sep 28 21:48:00 2008
  0.31% done, estimate finish Sun Sep 28 21:47:36 2008
  0.33% done, estimate finish Sun Sep 28 21:47:14 2008
  0.36% done, estimate finish Sun Sep 28 21:46:55 2008
  0.38% done, estimate finish Sun Sep 28 21:46:39 2008
  0.40% done, estimate finish Sun Sep 28 21:46:24 2008
  0.42% done, estimate finish Sun Sep 28 21:46:11 2008
  0.44% done, estimate finish Sun Sep 28 21:45:59 2008
  0.47% done, estimate finish Sun Sep 28 21:45:49 2008
  0.49% done, estimate finish Sun Sep 28 21:45:39 2008
  0.51% done, estimate finish Sun Sep 28 21:45:30 2008
  0.53% done, estimate finish Sun Sep 28 21:45:22 2008
  0.56% done, estimate finish Sun Sep 28 21:45:14 2008
  0.58% done, estimate finish Sun Sep 28 21:45:08 2008
  0.60% done, estimate finish Sun Sep 28 21:45:01 2008
  0.62% done, estimate finish Sun Sep 28 21:44:55 2008
  0.64% done, estimate finish Sun Sep 28 21:44:50 2008
  0.67% done, estimate finish Sun Sep 28 21:44:44 2008
  0.69% done, estimate finish Sun Sep 28 21:44:40 2008
  0.71% done, estimate finish Sun Sep 28 21:46:56 2008
  0.73% done, estimate finish Sun Sep 28 21:46:47 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-click/k3bBgUOnc.tmp -rational-rock -hide-list /tmp/kde-click/k3bCJQtEa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-click/k3baOA8Ga.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-click/k3bzDtkib.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-click/k3bbJC6ca.tmp -rational-rock -hide-list /tmp/kde-click/k3bDkHrZb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-click/k3bdxu4ja.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-click/k3bDGGJPb.tmp 

I have a dual boot system with Windows XP, and burners work fine there.

Is anybody able to help, as I am at my wits end at the moment. I want to use Linux, but am on my 3rd distro, all with different problems. Ubuntu was looking like the one I was going to stay with. 

Thanks in advance for any help

---

