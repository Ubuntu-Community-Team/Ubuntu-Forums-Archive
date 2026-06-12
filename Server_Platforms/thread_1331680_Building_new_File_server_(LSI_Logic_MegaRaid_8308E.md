---
title: "Building new File server (LSI Logic MegaRaid 8308ELP PCI-e )"
date: 2009-11-19
forum: Server Platforms
---

### Post by Schwyl on 2009-11-19
Hey Guys/Gals

ive been using ubuntu server for a few years now with my current mismash fileserver. The wife has given me the ok to spend some money upgrading/building a new one. 

My Biggest question and hopefully someone can answer me.

I have 2 brand new LSI Logic MegaRaid 8308ELP PCI-e  (just found them in the office)

Now what im looking for is if i have an os drive and then these two cards installed each with a raid 5 array consisting of 8 disk's will i be able to use them with ubuntu?

---

### Post by karlson on 2009-11-19
> **Schwyl said:**
> Hey Guys/Gals

ive been using ubuntu server for a few years now with my current mismash fileserver. The wife has given me the ok to spend some money upgrading/building a new one. 

My Biggest question and hopefully someone can answer me.

I have 2 brand new LSI Logic MegaRaid 8308ELP PCI-e  (just found them in the office)

Now what im looking for is if i have an os drive and then these two cards installed each with a raid 5 array consisting of 8 disk's will i be able to use them with ubuntu?

Simplest way to check:

Put the into the server and see if Ubuntu recognizes the cards and loads the driver for it.

More complicated way to check:

[www.lsi.com](www.lsi.com) go to downloads find your card and attempt to download the driver for Linux.  Then check if the driver exists on Ubuntu.

---

