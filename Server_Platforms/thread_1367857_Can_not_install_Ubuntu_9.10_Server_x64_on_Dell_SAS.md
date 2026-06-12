---
title: "Can not install Ubuntu 9.10 Server x64 on Dell SAS6/IR"
date: 2009-12-30
forum: Server Platforms
---

### Post by mrgaolei on 2009-12-30
I have two Dell PowerEdge R410 Server.
They are difference RAID card.

One of Server is Dell SAS 6 /IR of Two 300GB SAS HardDisk RAID 1 mode.
Install Ubuntu 9.10 Server x64, everything seems OK, But when installation finished, after first reboot, there is BusyBox error only, the interface tell me Can not found Harddisk.
When I Install Ubuntu 9.10 Server x86, everything OK.

Other one of Server is other RAID card, and it's All OK(both x86 x64).

---

### Post by mhanson on 2009-12-30
It seems that there is no 64bit driver for that card or that the driver has a bug. I believe that card has an LSI based chipset. Check wich LSI chipset that is and then cross reference it with x64 compatability in the kernel you are using. You should be able to either find a solution or will have to wait fo development and use 32bit in the meantime.

---

