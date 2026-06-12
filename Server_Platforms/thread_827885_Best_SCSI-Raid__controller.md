---
title: "Best SCSI-Raid  controller"
date: 2008-06-13
forum: Server Platforms
---

### Post by zhark1 on 2008-06-13
Hello!

Which SCSI-RAID controllers work out of the box under Ubuntu 8.04 Server with RAID functionality operational?

Any suggestions would be appreciated.

Regards
Marius.

---

### Post by Titan8990 on 2008-06-13
I couldn't tell you specifically but typically 3ware offers the best support for Linux and Ubuntu.

---

### Post by windependence on 2008-06-14
The 3Ware controllers do work well with Ubuntu if you are going to use SATA drives. for SCSI drives, I have had good luck with the Dell Perc series (LSI) controllers. You may want to stay away from Adaptec because they won't open their driver architecture so that an open source driver can be produced so the drivers that are out there are basically reverse engineered and while they do usually work, you could have problems. Also, just MHO, I don't want to support a company who doesn't support OSS.

-Tim

---

