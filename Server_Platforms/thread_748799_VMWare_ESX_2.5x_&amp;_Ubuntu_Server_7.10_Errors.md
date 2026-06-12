---
title: "VMWare ESX 2.5x &amp; Ubuntu Server 7.10 Errors"
date: 2008-04-07
forum: Server Platforms
---

### Post by mrhyd3 on 2008-04-07
I recently had major corruption on my Ubuntu Server 7.10 install.  I'm running it in a VMWare Esx 2.5.x.  I installed another NEW VM with a different ISO downloaded directly from NET, not from CD and noticed upon installation, I'm receiving the same kind of errors, and I mean a ton of them scrolling down the console......

[4495953.290037] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[4495953.290764] ata1.00: (BMDMA stat 0x26)
[4495953.290878] ata1.00: cmd a0/01:00:00:00:00/00:00:00:00/a0 tag 0 cdb 0x46 data 32 in


It only appears when I there's heavy disk IO...

Any help would be nice, thank you!

---

### Post by mrhyd3 on 2008-04-07
I may have found an issue.  It would appear that it ONLY happens when the CDROM (IDE) is connected.  I will continue to test and report back...

---

