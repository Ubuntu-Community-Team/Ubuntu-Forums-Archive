---
title: "Dailys don't work for me"
date: 2011-11-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by novatillasku on 2011-11-16
Every day i try with a pendrive to install precise in my older test partition, but every day i found same windows:

[IMG]http://i223.photobucket.com/albums/dd295/sku5/pantallazos/sreen.png[/IMG]

After Ubiquity closed.Any idea?.Thank's!

---

### Post by effenberg0x0 on 2011-11-16
> **novatillasku said:**
> Every day i try with a pendrive to install precise in my older test partition, but every day i found same windows:

After Ubiquity closed.Any idea?.Thank's!

Try a couple threads below.
[ubiquity 2.9.2 Crash]("http://ubuntuforums.org/showthread.php?t=1874553")

---

### Post by P-I H on 2011-11-16
It also works to use Gparted to make an empty partition and use the alternative to Install Ubuntu alongside "existing OS".

---

### Post by jerrylamos on 2011-11-16
> **P-I H said:**
> It also works to use Gparted to make an empty partition and use the alternative to Install Ubuntu alongside "existing OS".

I habitually use Gparted to prepare the test partition, then install either CD Live or Alternate use the "something else" option.

Ubuntu installer "ubiquity" has screwed up partitions for me so I use gparted instead.

In install with more than one hard drive, careful what ubiquity chooses for installing grub.  On my fast tower with 2 drives, Lucid LTS, Meerkat, Narwhal, ... designate the boot hard drive as /dev/sda.  Oneiric Ocelot and Pangolin designate the boot hard drive as /dev/sdb.  Go figure.

Jerry

---

