---
title: "Raring:  Sandisk 8 GB sdhc card is now read only."
date: 2013-03-07
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-03-07
Weird thing happened today.  It semms that my sandisk 8 gb sdhc card decided to become read only.  Prior to this happening I was able to copy and paste anything from the sandisk to the hdd.  The only thing I did today was install the Mar. 7th daily iso for ubuntu 13.04.  When I attempted to copy .mozilla from sandisk it refused to.  Fortunately I have another backup so I reinstalled 12.10 and used gparted to delete sandisk partition and create a new one...now I have a blank sandisk and get a read only message when I try to copy anything to it.  So how do I get this sandisk to allow me to read to it again.  I did try changing permissions, but it wouldn 't give me permission.  :(

Henry

---

### Post by QIII on 2013-03-07
*Moved to **Ubuntu + 1***

---

### Post by cole.mickens on 2013-03-07
What hardware? My SD cards consistently get out of wack on my MBA even in OS X because of a faulty controller or contacts, apparently it's a known-ish issue for MBAs, maybe your hardware has a similar issue. My solution was to check the switch and plug-replug the card in until it's recognized correctly.

(I assume you did check the hardware read-only switch on the SD card itself?)

---

### Post by Hewjr100 on 2013-03-07
Yep I checked the switch, and the funny thing was when I remounted it the folder icons were normal, until I tried to copy .mozilla from my ubuntu backup folder, then all of a sudden all my folders on the sd card had a "lock" emblem on them?

Henry

---

### Post by dimeboy99 on 2013-05-15
I have a similar problem in that the SD card isn't mounting at all from what I can tell, at least df -h doesn't show it. Working on a HP Pavilion and wondering what the controller is supposed to be for the SD card slot. I upgraded the kernel to 3.9.0 but that didn't change anything. Any ideas and what lspci should show what for a SD card slot?

---

