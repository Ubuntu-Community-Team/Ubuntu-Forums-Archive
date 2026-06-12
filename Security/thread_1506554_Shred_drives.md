---
title: "Shred drives"
date: 2010-06-10
forum: Security
---

### Post by Ristar on 2010-06-10
im gonna buy a new laptop and desktop and i need to shred (or at least do a low/high level format) the drives before giving them to my parents (because they know about undelete and stuff).

so, what apps can i use in ubuntu to do this?

thanks.

---

### Post by anomie on 2010-06-10
As an alternative to performing this operation "in Ubuntu", you might take a look at [DBAN](http://www.dban.org/). It's an actively developed, widely used utility.

---

### Post by Ristar on 2010-06-10
> **anomie said:**
> As an alternative to performing this operation "in Ubuntu", you might take a look at [DBAN](http://www.dban.org/). It's an actively developed, widely used utility.

thanks for your prompt reply.

i will check it out.

---

### Post by rookcifer on 2010-06-10
Load up the ubuntu live CD, open a root terminal and run:

```
shred -vf -n 1 /dev/sdx

```
where sdx = the name of your drive. 

This will overwrite the drive with one pass of random data (thus making recovery of any data impossible).

Or, you can use the hdparm utility to utilize the built-in secure erase function all modern hard drives have.  You can learn how to do that [here.]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase")

---

### Post by bodhi.zazen on 2010-06-10
> **Ristar said:**
> im gonna buy a new laptop and desktop and i need to shred (or at least do a low/high level format) the drives before giving them to my parents (because they know about undelete and stuff).

so, what apps can i use in ubuntu to do this?

thanks.

You can do all those things if you wish, but writing all zeros to the HD is sufficient

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

---

