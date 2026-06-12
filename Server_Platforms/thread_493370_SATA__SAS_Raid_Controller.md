---
title: "SATA / SAS Raid Controller"
date: 2007-07-05
forum: Server Platforms
---

### Post by lwh on 2007-07-05
Hi

Need to build a new server, that can handle allot of cheep stoage, and i'm thinking in sataII storage, (8 to 12 500G disks in 2 raid groups one Raid 5 and Raid 10)

Currently I have one Intel 8 Port sataII controller running i one server, the only issue with this controller is that Im no been able to get the Intel Managemen software for the raid controller to work on Ubuntu and therefore need to take the server offline to rebuild when a drive fails :-(

For my next server I like to be able to use the management softeware for the hardware raid controller, and rebuild failed drives online.

Does anyone know which brand or controller I should take a Look at ?
Intel / 3Ware /Adaptec /promise ?

I Thinki I'm going for at Intel Hardware raid controller, Just got the Intel Management Web tool to work on my SRCS28X, NO more power down to replace diskes and rebuild..

---

### Post by t4thfavor on 2007-07-06
I have a 4 port sata controller from promise that says it has management software for Linux (web based.) Since I have not used it yet I can not guarentee it will work. But its worth a try.

---

### Post by lwh on 2007-07-12
[QUOTE=t4thfavor;2977125]I have a 4 port sata controller from promise QUOTE]

What is the name of this controller ?
Many cheep sata raid controller is not real hardware raid, which means that heavy I/O on the controller  takes CPU usage. 
[http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html")

---

