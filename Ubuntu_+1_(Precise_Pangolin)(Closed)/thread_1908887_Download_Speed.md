---
title: "Download Speed"
date: 2012-01-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nepmit on 2012-01-14
Anyone having problems downloading the daily build? It takes 3-4 hrs.I normally download just over 1hr. Are the servers that busy? I've checked my internet speed, it's about 1.5 megs.Thanks.

---

### Post by sammiev on 2012-01-14
> **nepmit said:**
> Anyone having problems downloading the daily build? It takes 3-4 hrs.I normally download just over 1hr. Are the servers that busy? I've checked my internet speed, it's about 1.5 megs.Thanks.

I'm unable to update today so likely a problem at the main server side. I even tried 2 different servers.

---

### Post by cap10Ibraim on 2012-01-14
today I downloaded the daily build and then did the "partial upgrade" thing at normal speeds

---

### Post by nepmit on 2012-01-14
Thanks for both replies. I'm going to our library to download. Their speed is about 6megs.That should tell me something.

---

### Post by sammiev on 2012-01-14
All normal here at this time. :)

---

### Post by bastones on 2012-01-14
Normal here too :). Getting ~300kB/s which is normal. I get around 2.5Mbps on my DSL connection.

---

### Post by jerrylamos on 2012-01-14
> **nepmit said:**
> Anyone having problems downloading the daily build? It takes 3-4 hrs.I normally download just over 1hr. Are the servers that busy? I've checked my internet speed, it's about 1.5 megs.Thanks.

After the initial download I use zsync to update my .iso thusly:

#! /bin/bash
sudo zsync [http://cdimage.ubuntu.com/cdimage/daily-live/20120110/precise-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/cdimage/daily-live/20120110/precise-desktop-i386.iso.zsync)
exit 0

takes a lot less time, frequently well under an hour.

Jerry

---

