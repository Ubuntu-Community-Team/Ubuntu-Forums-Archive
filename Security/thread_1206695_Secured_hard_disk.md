---
title: "Secured hard disk"
date: 2009-07-07
forum: Security
---

### Post by mhdbnoimi on 2009-07-07
Hi All,

I've portable backup hard disk formated as ext3.

**[COLOR="Red"]How I can make my hard disk secured (locking by password or something else)?[/COLOR]**

Note:
I was using [truecrypt](www.truecrypt.org) for protecting my partitions but I it's not suitable for protecting whole hard disk.

---

### Post by Dave_Connor on 2009-07-07
You can reinstall Ubuntu with an alternet disc and are able to setup disk encryption on that drive with dm-crypt and luks. The problem with Truecrypt since it is not built into the kernel it can't encrypt swap and that issue can be very bad since swap isn't encrypted and can lead to possible ways of getting into the system with the encryption key may be stored in swap.

---

### Post by HermanAB on 2009-07-07
Here is some info:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by mhdbnoimi on 2009-07-08
[quote="Dave"]You can reinstall Ubuntu with an alternet disc[/quote]
I don't need to reinstall ubuntu because I'm using backup hard disk which is don't has swap partition.

---

### Post by mhdbnoimi on 2009-07-09
[quote="Herman"]Here is some info:[/quote]
Thank you for link above, but the protecting way you've write isn't easy and complicated to me. is there any practical way for protecting ?

---

### Post by markedisonchua on 2009-07-09
Encryption in TrueCrypt is bit standard, but not fullproof

---

### Post by juancarlospaco on 2009-07-10
-BIOS password
-GRUB password
-Encrypted installation

---

### Post by Piro24 on 2009-07-10
Some hard-disks have a "master-password" that you might be able to change, possibly in the BIOS, they vary from model to model.

However, I remember an article in 2600 that pretty much showed at least 10 ways around it, most of which required physical access, so it does add another layer of security.

---

### Post by mhdbnoimi on 2009-07-11
[quote="Piro"]However, I remember an article in 2600 that pretty much showed at least 10 ways around it[/quote]
Actually I used openSuSE before and I could protect my hard disk through formating it as encrypted hard disk for that whenever I want to read/write data from this hard disk openSuSE asks me about a password for mounting this hard disk. So I want to know if there is any tool just like openSuSE can encrypting whole hard disk.

---

### Post by juancarlospaco on 2009-07-12
Encrypted Installation, see Alternative install CD .

---

