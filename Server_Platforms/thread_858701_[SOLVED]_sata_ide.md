---
title: "[SOLVED] sata ide"
date: 2008-07-13
forum: Server Platforms
---

### Post by gishaust on 2008-07-13
hello

I am setting up a new server with a master sata hdd. but I have a ide hdd i wanted as a slave for back up purposes. the mother border has the option for sata and ide. i am going to install 8.04 server. is it possible to run sata and ide or am I creating issues for myself?

gishaust

---

### Post by windependence on 2008-07-14
Shouldn't be a problem. Your board may detect the ATA first though so be sure to install the OS on the proper drive and set the bios to boot that drive.

-Tim

---

### Post by Krupski on 2008-07-14
> **gishaust said:**
> hello

I am setting up a new server with a master sata hdd. but I have a ide hdd i wanted as a slave for back up purposes. the mother border has the option for sata and ide. i am going to install 8.04 server. is it possible to run sata and ide or am I creating issues for myself?

gishaust

Both drives will work just fine.

Although you don't NEED to do this, you may (in the future) want to convert IDE to SATA or vice-versa. The company "Addonics" makes really neat little adapter boards which go from SATA to IDE, IDE to SATA, USB to SATA, etc... almost any combination you can think of. Here's a ([LINK]("http://www.addonics.com/products/io")) to their I/O products.

-- Roger

---

### Post by gishaust on 2008-07-14
thanks for the information

---

