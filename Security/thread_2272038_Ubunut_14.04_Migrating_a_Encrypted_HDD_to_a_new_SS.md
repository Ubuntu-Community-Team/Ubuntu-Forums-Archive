---
title: "Ubunut 14.04 Migrating a Encrypted HDD to a new SSD"
date: 2015-04-03
forum: Security
---

### Post by phil1607 on 2015-04-03
Hey Guys,

google wasn't really helpful and ubuntuusers.de also wasn't able to answer my question...

I have a Netbook on wich i installed Ubuntu 14.04 in the Installation progress I've chosen to encrypt the whole thing.
I've recently bought a new SSD and what I basically want to do is to Migrate everything 1:1 to the new SSD.

Unfortunately most migrating tools only support unencrypted harddrives so: How can I decrypt my current HDD, migrating everything 1:1 to the new SSD and set a boot password on the new SSD?

Cheers!

---

### Post by HermanAB on 2015-04-03
Well, if you can connect both disks and a CD or USB stick, then boot Linux on the CD or USB stick and use dd (data definition) to copy the disk.

---

### Post by cariboo on 2015-04-03
You could also try [Clonezilla]("http://clonezilla.org/"), I've used it many times to clone a hard drive.

---

### Post by HermanAB on 2015-04-04
Yup, basically dd is a one liner and Clonezilla will wrap a whole GUI around that one liner to pretty it up, for those who stubbornly refuse to read a man page...

---

