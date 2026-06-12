---
title: "USB HDD Encryption between Ubuntu 14.04 &amp; Windows"
date: 2015-01-21
forum: Security
---

### Post by chris260 on 2015-01-21
Hi All, 

Can anyone recommend a product/solution that will allow me to encrypt either an entire drive or (preferably) a single partition on a USB HDD drive, I want to be able to use this drive between Windows and Linux (Ubuntu 14.04 LTS).

For example on a 2TB drive a 500GB encrypted partition for my personal files and the rest unencrypted music & videos etc, all the solutions I have found so far are Windows based.

Failing this, just an encryption solution for Linux / Ubuntu would be better than nothing.

All advice gratefully received.

Thanks

C

---

### Post by TheFu on 2015-01-21
ZIP is cross-platform. Just use a really long passphrase - 30+ characters because the brute force tools for encrypted ZIP files can do like a billion attempts/sec.

A few years ago, I tried to accomplish this with truecrypt and failed. It was at the partition level. Couldn't get Linux to access it at all.
Google found [this thread]("http://arstechnica.com/civis/viewtopic.php?t=1245367") from Ars forums. Interesting read.

---

### Post by chris260 on 2015-01-21
Thanks TheFu, I'll take a look at some of those starting with ZIP (which I didn't even consider) & Trupax as I have some older Truecrypt containers too - It will have to wait until tonight as the corp network here is blocking that download :rolleyes:

C

---

