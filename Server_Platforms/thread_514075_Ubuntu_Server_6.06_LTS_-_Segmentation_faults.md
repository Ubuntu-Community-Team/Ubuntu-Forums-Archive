---
title: "Ubuntu Server 6.06 LTS - Segmentation faults"
date: 2007-07-31
forum: Server Platforms
---

### Post by vincentthe on 2007-07-31
I've been runnig Ubuntu 6.06 LTS with a Directadmin control panel for some time now. But since this morning some funny behaviour became apparent.

When in the shell it started with "mkdir" giving a segmentation fault, soon after that other system commands like "chmod" also started giving segmentation faults.

This happened once before, also with Ubuntu 6.06 LTS on this same machine. At that time it took us a complete day of testing all hardware and we came up with nothing. The only thing we could do was a clean install.

Hardware: 
SuperMicro 1U SuperServer 5014CT P4 SATA
2 x Seagate 500GB 7200rpm SATA II in Raid 1
2GB DDR2 PC4300
3Ware 8006 SATA Raid controller

Does anyone have any suggestions? Thanks in advance

---

### Post by vincentthe on 2007-07-31
To make things stranger: a copy of the mkdir program from another ubuntu system does work (run from my home dir). Although after some time even this version has been affected and gives segfaults.

All the affected programs are in /bin. The list now includes touch, mkdir, cat, chgrp, chown, rmdir, sleep, syslog...

Are there any known viruses with this behaviour? Or maybe it's a hacker? (1 port 3131 is open which I don't have an explanation for). We have the feeling that if a call to a program is made as root the program "dies". This is not entirely true, but mkdir functioned with a regular user with shell access, but since running it as root it segfaults. This behaviour is not constant since cp, rm, top keep working...

---

### Post by rich.bradshaw on 2007-07-31
Sounds weird, I'd reinstall...

Have you checked for rootkits?

---

### Post by vincentthe on 2007-07-31
Any suggestions on how I should do that? Installing chkrootkit is a bit difficult...

---

