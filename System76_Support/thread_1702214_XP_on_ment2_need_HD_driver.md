---
title: "XP on ment2: need HD driver"
date: 2011-03-07
forum: System76 Support
---

### Post by tlroche on 2011-03-07
I'm trying to install wXP SP3 on a new [Meerkat Ion]("http://www.system76.com/product_info.php?cPath=27&products_id=95") (model#=ment2, serial#=356390, order#=12960). I was going to install w7, but my install disk is defective, although it at least recognized the ment2's HD. I have a wXP SP3 install disk which I know to be good (from previous use), but after booting it says

```
Setup has recognized the following mass storage devices in your computer:
<none>
```

I assumed [http://knowledge76.com/](http://knowledge76.com/) would have windows drivers, and it does, but only for the [ment1]("http://knowledge76.com/index.php/Ment1"), [ment3]("http://knowledge76.com/index.php/Ment3"), and [ment4]("http://knowledge76.com/index.php/Ment4"): the [ment2 page]("http://knowledge76.com/index.php/Ment2") has no windows drivers. Furthermore the ment{1,3,4} pages have drivers={Audio, Video, Chipset, LAN}, but not storage. So I'm wondering:

[LIST=1]
[*]'Sup with that?
[*]Where to get a storage driver for the ment2 to use with wXP?
[/LIST]

---

### Post by isantop on 2011-03-07
Go ahead and use the drivers from the Ment4 page, as your system and that have identical specs. 

We don't specifically provide a storage driver, though one of them should get everything working. That said, we don't test our systems with Windows, and if something isn't right, we haven't heard about it yet.

---

### Post by tlroche on 2011-03-09
> **isantop said:**
> Go ahead and use the drivers from the Ment4 page

Done, but ...

> **isantop said:**
> we don't test our systems with Windows, and if something isn't right, we haven't heard about it yet.

... when I slipstreamed the drivers from the [Ment4 page]("http://knowledge76.com/index.php/Ment4") into a wXP image (using [nLite]("http://www.nliteos.com/")) along with some generic Intel SATA drivers, on install it sees the generics but not the ment4 drivers :-(

---

### Post by tlroche on 2011-03-09
Which motherboard does the ment2 have? The [Zotac mobo pages]("http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=78&Itemid=100032&lang=en") have links to drivers, but on opening the Meerkat Ion's system unit I don't see any identifying marks.

---

### Post by isantop on 2011-03-09
According to the information I have, it's a Zotac IONITX-D-E.

What happens if you try to add them post-install?

---

### Post by tlroche on 2011-03-09
> **isantop said:**
> Zotac IONITX-D-E

Hmm ... The [Zotac Intel mobo page]("http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=78&Itemid=100032&lang=en") has

[LIST]
[*][ZOTAC IONITX - A / B / C / D]("http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=124&Itemid=100032&lang=en")
[*][ZOTAC IONITX - F (PCI-E x 16 Slot)]("http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=206&Itemid=100032&lang=en")
[*][ZOTAC IONITX - L]("http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=225&Itemid=100032&lang=en")
[*][ZOTAC IONITX N / O / P]("http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=236&Itemid=100032&lang=en")
[*][ZOTAC IONITX R / S / T / U]("http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=249&Itemid=100032&lang=en")
[/LIST]

> **isantop said:**
> What happens if you try to add them post-install?

Currently there *is* no post-install, since wXP thinks there's nothing to which to install. I boot the Meerkat Ion with the wXP CD via a USB CD drive. The wXP installer (boy does that bring back bad mems :-) probes awhile, then comes up with

```
Setup has recognized the following mass storage devices in your computer:
<none>
```

and refuses to advance past that point: nothing I've chosen makes it happy. By contrast, my w7 install disk is fine with SATA, but it refuses to take its product key, and I'm past the 14-day return window :-(

---

