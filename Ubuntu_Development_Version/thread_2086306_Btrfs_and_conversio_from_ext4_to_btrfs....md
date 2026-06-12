---
title: "Btrfs and conversio from ext4 to btrfs..."
date: 2012-11-20
forum: Ubuntu Development Version
---

### Post by zika on 2012-11-20
Has anybody tried btrfs on RR? Is there any advantage?
Has anybody tried conversion from etx4 to btrfs? Any problems?
[https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3](https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3)

---

### Post by dino99 on 2012-11-20
you might read the test made by phoronix : ext4 is the best

---

### Post by kansasnoob on 2012-11-20
I'm more than a bit turned off after experiencing data loss with ext4 :(

If you care about the data you're saving you'll use ext3 :)

---

### Post by fjgaude on 2012-11-20
> **kansasnoob said:**
> I'm more than a bit turned off after experiencing data loss with ext4 :(

If you care about the data you're saving you'll use ext3 :)

What brought about the data loss?

I've used ext4 since it came out and have yet to have issues with it. My database is 80GB on a Plextor SSD, backed onto an WD VelicoRaptor HDD online, then offline to an ordinary Seagate HHD, and finally to an HDD on a netbook. Have an APC UPS for online data protection.

---

### Post by kurt18947 on 2012-11-20
> **fjgaude said:**
> What brought about the data loss?

I've used ext4 since it came out and have yet to have issues with it. My database is 80GB on a Plextor SSD, backed onto an WD VelicoRaptor HDD online, then offline to an ordinary Seagate HHD, and finally to an HDD on a netbook. Have an APC UPS for online data protection.

There was an issue with LibreOffice documents disappearing and being unrecoverable with ext4.  I don't know if that has been addressed or not.

---

### Post by kansasnoob on 2012-11-20
> **fjgaude said:**
> What brought about the data loss?

I've used ext4 since it came out and have yet to have issues with it. My database is 80GB on a Plextor SSD, backed onto an WD VelicoRaptor HDD online, then offline to an ordinary Seagate HHD, and finally to an HDD on a netbook. Have an APC UPS for online data protection.

It's well documented:

[http://www.h-online.com/open/news/item/Stable-Linux-kernel-hit-by-ext4-data-corruption-bug-Update-1736110.html](http://www.h-online.com/open/news/item/Stable-Linux-kernel-hit-by-ext4-data-corruption-bug-Update-1736110.html)

And:

[https://lkml.org/lkml/2012/10/24/14](https://lkml.org/lkml/2012/10/24/14)

I like truly stable stuff so I use ext3 :)

---

### Post by fjgaude on 2012-11-20
"Apparently, the data corruption bug was hard to track down as it only manifests itself if a system is rebooted twice in a relatively short period of time."

Thanks for the links... hope it gets fixed one of these days, sooner than later. <smile>

---

