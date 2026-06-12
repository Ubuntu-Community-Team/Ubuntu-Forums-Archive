---
title: "Attaching Fibre Channel LUNs"
date: 2023-09-21
forum: Server Platforms
---

### Post by hxman on 2023-09-21
Hello,

We are running 22.04 of Ubuntu server and was wondering what the best way is to rescan your FC links and hopefully see the LUN from the SAN?
I can already see that the 2 HBA's are online and logging into the array and storage is now allocated to that specific host.

Thanks

---

### Post by darkod on 2023-09-21
I don't understand. If the zoning is correct and the HBAs are already logging into the SAN, then any LUN assigned to that initiator should show up as if it was local hard disk.

Did you check for example what lsblk shows?
```
lsblk
```

---

