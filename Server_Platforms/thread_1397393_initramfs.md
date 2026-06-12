---
title: "initramfs"
date: 2010-02-03
forum: Server Platforms
---

### Post by webdirector on 2010-02-03
Hi, I added a new HD and made a mistake and now the system comes up in initramfs and yes I did not make a backup of my websites is there any way for me to recover them ? 

I have tried repairing my ubuntu installation with the boot CD option but that did not work

is there any way to at least not loose the /var/www folders ?

Thanks for help

---

### Post by Lars Noodén on 2010-02-03
> **webdirector said:**
> Hi, I added a new HD and made a mistake and now the system comes up in initramfs and yes I did not make a backup of my websites is there any way for me to recover them ? 

I have tried repairing my ubuntu installation with the boot CD option but that did not work

is there any way to at least not loose the /var/www folders ?


The best way is to keep /var/www in a separate partition, that way if you rebuild the rest of the system, you can leave that part of the disk unchanged.

To try to salvage your existing setup, use the live cd and then mount the partition containing the directory /var/www

---

