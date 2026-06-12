---
title: "Ubuntu server want to destroy my storage :("
date: 2010-03-22
forum: Server Platforms
---

### Post by zenetx on 2010-03-22
Please help, i wanna try to install ubuntu server on my poweredge 1955 with emc storage, but on the partitioning step it says:

"the following partitions will be fomarted:

...<here goes all the lvms in the storage>..."  :evil::evil:

I already tried all the options in the partitioning step without sucess

:mad::mad::mad:

---

### Post by gobbledigook on 2010-03-22
the simple answer to this is to disconnect the storage whilst you do your ubuntu install...

---

### Post by R.Bucky on 2010-03-23
Not an expert on LVMS, but the point of that config is to use many disks as one "partition." If you have attached disks, it makes sense that the install wants to write to it.

---

### Post by zenetx on 2010-03-23
well..i cant disconnect the storage from only one blade and i have like 6 blades on production that cannot be turned off ... but maybe i can disable it on bios in this blade... my fear is ubuntu will not recognize it after install...i will try and post the results later..thx guys :)

---

