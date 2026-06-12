---
title: "ata1 messages."
date: 2010-10-07
forum: Server Platforms
---

### Post by mkanada on 2010-10-07
Hi.

I'm using for some years one server with Ubuntu 8.04 server. Some time ago some messages appeared in logs.

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: BMDMA stat 0x65
ata1.00: cmd c8/00:08:9f:81:07/00:00:00:00:00/e6 tag 0 dma 4096 in
         res 51/40:08:9f:81:07/00:00:00:00:00/e6 Emask 0x9 (media error)
ata1.00: status: { DRDY ERR }
ata1.00: error: { UNC }
ata1.00: configured for UDMA/100

The server continues working without any problem, but I don't know if these messages are one signal of some future disaster.

What means these messages, and there is something that I need to do?

---

### Post by P4man on 2010-10-07
Id run smartmontools. Could be a drive dying.

---

### Post by psusi on 2010-10-07
Yep, you have at least one bad sector, check the SMART numbers and back up your data because it looks like that drive is on the way out.

---

