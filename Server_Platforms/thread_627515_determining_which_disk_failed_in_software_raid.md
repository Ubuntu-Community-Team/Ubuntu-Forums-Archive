---
title: "determining which disk failed in software raid"
date: 2007-11-30
forum: Server Platforms
---

### Post by lee_connell on 2007-11-30
What is the proper way to determine which physical disk has failed in the system?  I know it tells you /dev/sda or /dev/sdb is the failed disk but how would I determine which "physical" disk that is inside the server?

I am running sata II disks in software raid1.

I tried using lshal to get details on the drives like maybe a serial number but that didn't help.  Any suggestions?

---

### Post by mellowd on 2007-11-30
It usually works that the primary sata controller will be sda, secondary sata sdb and so on

---

### Post by lee_connell on 2007-11-30
Thank you this is what I expected, just wasn't sure :)

---

