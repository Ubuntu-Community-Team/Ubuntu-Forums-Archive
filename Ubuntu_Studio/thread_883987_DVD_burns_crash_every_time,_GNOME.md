---
title: "DVD burns crash every time, GNOME"
date: 2008-08-08
forum: Ubuntu Studio
---

### Post by archangel74 on 2008-08-08
please help...I am getting tired of wasting DVD+R's.  either using 
gnomebaker or write to disk, there is always an error.  if there is no error then it takes 5 hours to burn both DVD and CD.  I have DVDrecord and cdrecord installed. I have an ATAPI LiteOn 20x DVD+R. i am using sony dvd+r 16x disks.  The model number for the liteon is DH-20A4P08C.  In addition, I am running a AMD64, 4200+, MSI motherboard, 512MB, 333khz.

the error I get in Gnomebaker is:
Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p Archangel -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-archangel/gnomebaker-KF28EU | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/sr0: "Current Write Speed" is 7.4x1352KBps.
:-[ WRITE@LBA=c80h failed with SK=6h/ASC=28h/ACQ=00h]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
/dev/sr0: closing track
/dev/sr0: closing disc


I have the same issue with K3b or Brasero.
Can anyone point me in the right direction.  I am still new to ubuntu.

Charles aka Archangel

---

### Post by RumorsOfWar on 2008-11-09
I have the same issue using Xubuntu. Oddly enough, burning in Gnome turned out great for me...  
Try this thread: [http://ubuntuforums.org/showthread.php?t=851707](http://ubuntuforums.org/showthread.php?t=851707)

---

### Post by chavon20 on 2008-11-09
I've experienced the same problem burning to DVD's, though no problem burning to CD's.  I have used the same DVD's as you (Sony DVD+R x16), I have received some advice that DVD-R type DVD's might be more cooperative?  I haven't tried it myself though...

---

