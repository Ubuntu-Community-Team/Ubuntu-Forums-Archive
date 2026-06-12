---
title: "Raid Controller - Suggestions"
date: 2007-05-30
forum: Server Platforms
---

### Post by jsaumer on 2007-05-30
Hello,

I am looking for some suggestions for making a ubuntu FTP server.

I will want to put a raid on the server, and I am wondering what raid controller everyone would recommend.

Also, what version of ubuntu server would everyone recommend for this project. 

I am open to any and all suggestions.

Thanks,
jsaumer

---

### Post by John_W on 2007-05-30
I'm using a [[COLOR="Red"]LSI MegaRAID SATA 150-4 Card[/COLOR]]("http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sata/megaraid_sata_1504/index.html") with four 750GB SATA drives in a RAID-5 array. It's a standard PCI card. That setup gives me over 2 TerraBytes of storage.

I'm also using Ubuntu Feisty 7.04 desktop version. The LSI RAID card works right out-of-the-box with Ubuntu. 

I'm pretty new to LINUX and you can read about my problems partitioning 2TiB [[COLOR="Red"]HERE[/COLOR]]("http://ubuntuforums.org/showthread.php?t=447894").
The problem has been resolved though. :) 

Good Luck!

---

### Post by obimeister on 2007-05-30
How much is your budget? IMO its no use to buy 0-300eur fake raid cards, just use software raid. But if you got more money then all 3Ware hardware raid controllers would be probably ok.

---

### Post by Brazen on 2007-05-30
I have had excellent experience with LSI raid cards, and as obimeister said, stay away from the fake raid controllers.  You will be wasting your money and linux software raid will work better anyway.

As for what server distro to recommend... well there's only one meant for production use, so that would be Ubuntu Dapper Server, of course!

---

