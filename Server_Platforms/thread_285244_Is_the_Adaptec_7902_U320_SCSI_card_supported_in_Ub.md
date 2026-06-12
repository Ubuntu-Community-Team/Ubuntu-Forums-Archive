---
title: "Is the Adaptec 7902 U320 SCSI card supported in Ubuntu 6.06.1?"
date: 2006-10-26
forum: Server Platforms
---

### Post by hamishrobertson on 2006-10-26
Hello

Does anyone know if the Adaptec 7902 is supported in 6.06.1 server edition? I'm about to buy a motherboard with this SCSI card and I would like to know that it will work before I spend heaps of cash!

Is there a full compatibility list for Ubuntu somewhere?

Many, many thanks
Hamish

---

### Post by foxylad on 2006-10-26
Yes, there is a hardware compatibility list. But if this is going to be server, then you probably don't need a display adaptor - if the motherboard doesn't have a generic adaptor built in, get the cheapest display card you can. 

Servers are generally "headless", with no monitor attached except for install. This is good because you don't need to load up all those XWindows, Gnome and other GUI packages, which just take up hard drive space and add vulnerability.

If on the other hand you want a desktop machine that doubles as a server, I'd do a normal install and add the particular server packages you need.

---

### Post by hamishrobertson on 2006-10-27
Where is the compatibility list?

SCSI is a hardware controller for drives, not a graphics card.

Many thanks
Hamish

---

