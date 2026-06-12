---
title: "Ubuntu Daily ISO"
date: 2016-01-27
forum: Ubuntu Development Version
---

### Post by travis-falkenberg on 2016-01-27
I thought I would try Ubuntu 16.04 but the daily ISO doesn't work as it should.

It starts with the normal purple Ubuntu splash but ends up as an Xubuntu system.

I'm sure I've downloaded the correct ISO's from both 26th and 27th January. Both files appear to be the same ISO.

---

### Post by sudodus on 2016-01-27
Please specify the link (web address) of the file that you have downloaded!

For the 64-bit version you can try either of

[20160127/xenial-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/20160127/xenial-desktop-amd64.iso) (fixed to today's date) and [current/xenial-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso) ('current' date)

You find the corresponding md5sum at

[http://cdimage.ubuntu.com/daily-live/20160127](http://cdimage.ubuntu.com/daily-live/20160127) and/or [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current)

or the corresponding files for the 32-bit version, where you substitute amd64 --> i386

I have a current copy of the amd64 version of the iso file, and it starts standard Ubuntu.

---

### Post by travis-falkenberg on 2016-01-27
The links you provided are the ones I've downloaded. Filesize is 1.5 GB (1,499,627,520 bytes)
The MD5 sum of the file (9a0943197041c6d36cd9e040ec70a5fd) does not match whats indicated in the MD5SUMS file.
*** my bad did a MD5 of the 26th January file *** MD5 is correct.
I'm downloading again but it appears to be the same file as I already have.

*** Something weird going on here. If I use the USB in my laptop it boots into Ubuntu OK. If I use my desktop it boots as an Ubuntu splash screen but finishes as an Xubuntu system. ...

OK! here's what I found.
 I used MultiSystem to make my usb. If I boot this on my laptop then all is OK. If I boot on my Desktop (running Xubuntu 15.10) the Purple Ubuntu splash screen comes up but the system ends up booting into an Xubuntu session with the normal options to try Xubuntu or Install. There are no other versions of Ubuntu/Xubuntu etc on the USB made by MultiSystem.
If I use a DVD or another method of making the USB then the system boots correctly into Ubuntu.

Strange but true. Certainly had me confused!

---

### Post by sudodus on 2016-01-27
If the md5sum is correct, the file is correct, you need not download it again.

The Ubuntu iso file does not contain the program packages for Xubuntu's desktop environment (xfce4), so your Ubuntu in Multisystem must find it somewhere else (in itself, in another USB drive or in an installed system).

---

### Post by QDR06VV9 on 2016-01-27
> **sudodus said:**
> If the md5sum is correct, the file is correct, you need not download it again.

The Ubuntu iso file does not contain the program packages for Xubuntu's desktop environment (xfce4), so your Ubuntu in Multisystem must find it somewhere else (in itself, in another USB drive or in an installed system).
+1 Yep!
I have used Multisystem for years with nothing like this occurring!?
Maybe a report to Multisystem's with this.

---

### Post by travis-falkenberg on 2016-01-27
OK Iv'e found out what happens.

All Daily ISO's of the various flavours, Ubuntu, Xubuntu, Kubuntu etc., have the same name eg. xenial-desktop-amd64.iso
When booting from a USB created with Multisystem it starts out OK using the boot splash of the system on the USB.
Sometime during this process Multisystem will check the root directories of all mounted disks, including windows partitions, and if it finds an ISO with the same name that it is booting from it will switch to that ISO and continue as normal. If this happens to be a different flavour of Ubuntu it will simply boot into that version.
I tried this with the Xubuntu and Kubuntu iso's in the root of various disks which are mounted on start.

I'll report this to Multisystem as it happens on two different computers here.

---

### Post by MikeMecanic on 2016-01-27
> **travis-falkenberg said:**
> All Daily ISO's of the various flavours, Ubuntu, Xubuntu, Kubuntu etc., have the same name eg. xenial-desktop-amd64.iso.

You must rename the ISO file when download is complete.  I have a bunch of ISO that have the name of the flavor and the date of the build.

Take care,

---

