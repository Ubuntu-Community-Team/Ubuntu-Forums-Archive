---
title: "Very old scanner and a virtualized Ubuntu?"
date: 2019-01-14
forum: Virtualisation
---

### Post by eskoboy on 2019-01-14
I have a very fine and very old (over 20 years) scanner. After lot of testing during many days I can’t start it. Therefore a principal question: is it principally possible to use this kind of old scanner (HP 5370C) in a Oracle Virtualbox Ubuntu (with Win 10 host)?
Earlier I used my scanner in win 7 with XP window but had to change my computer. Now I have tested this with Virtualbox 4.2, 5.2 and 6.0, and with Ubuntu 16.04 and 18.04 (12.04 don’t success, yet). I have extension packs installed and used quest additions, too. I could get USB access to my keyboard, mouse and USB-hard-disk, but to access the scanner failed.
I tested the Hyper-v possibilities to virtualisation of Ubuntu in Win 10, but there seems to be impossible to use USB’s.
If it is principally possible, I will continue with testing. But if not, I have to buy a new scanner. The dual boot system I will not use. So is this kind of combination principally possible?
Thanks for comments.

---

### Post by SeijiSensei on 2019-01-14
You would probably have to create a custom "filter" in VirtualBox for a device that old, and even then there's no guarantee it will work with Linux out-of-the-box.

If you boot directly into Linux, say from a USB stick using the "Try Ubuntu" mode, can you access the scanner?

I have an HP Scanjet 4850 which isn't in the [list of supported scanners]("https://www.chiark.greenend.org.uk/doc/libsane/supported.html").  I ended up buying a license for [VueScan]("https://www.hamrick.com/") so I can access the scanner from Linux.

---

### Post by eskoboy on 2019-01-14
Thanks. I have to test this "Try Ubuntu" mode. After that I will know more.

---

### Post by eskoboy on 2019-01-17
Yes, Ubuntu 16.04 can use my scanner, when starting in "Try Ubuntu" mode from an USB stick. I can use it this way, too, if we can not find more. But would it as well be possible to use the scanner in Oracle Virtualbox with Ubuntu? Is this a problem to Virtualbox, to Win 10, or still to Ubuntu?

---

