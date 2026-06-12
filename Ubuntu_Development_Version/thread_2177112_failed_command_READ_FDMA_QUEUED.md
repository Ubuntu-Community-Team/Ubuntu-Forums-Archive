---
title: "failed command: READ FDMA QUEUED"
date: 2013-09-27
forum: Ubuntu Development Version
---

### Post by EmilyRose on 2013-09-27
I just installed 13.10 beta1 on my husbands lapto, and added the gnome3-team/gnome3 & gnome3-next repositories to his laptop. After updating and a dist-upgrade it freezes immediatly after login. If I drop to command line and login before attempting anything, I get the following errors as soon as I attempt anything:

[  67.395232] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  67.395311] aa1.0 irq_stat 0x40000000B
[  67.395361] ata1.00: failed command: READ FPDMA QUEUED
[ 67.395394] ata1.00: cmd 60/00:00:00:8b:5f/01:00:00:00:00/40 tag 0 ncq 131072 in
[  67.395394] ata1.00: res 41/40:00:73:8b:5f/00:01:00:00:00/60 Emask 0x409 (media error) <F>
[  67.395471] ata1.00: status: { DRDY ERR }
[  67.395494] ata1.00: error { UNC }
[67.397439] ata1.00: end_request: I/O error, dev sda, sector 6261619

and then it starts over repeating the same thing with occasionally WRITE FPDMA QUEUED in place of READ FPDMA QUEUED. This laptop *was* working fine running OpenSUSE 12.1, having previously had problems with the hard drive setting randomly as read only in Ubuntu 12.04/12.10. But now he wants Steam, and requested to move back to Ubuntu... thoughts? Suggestions?

---

### Post by oldos2er on 2013-09-27
Moved to Ubuntu +1.

---

