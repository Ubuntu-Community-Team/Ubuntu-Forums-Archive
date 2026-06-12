---
title: "SAMBA Freezing"
date: 2015-10-22
forum: Server Platforms
---

### Post by Billy_Martinez on 2015-10-22
I'm trying to copy files to a SAMBA share from a Windows 2008 server, and for some reason the SAMBA share keeps on freezing. I keep on getting errors from Windows explorer while its copying the files that it can't access the share. It ask me if I want to try again, and when I click ok it starts working for a while and then eventually freezes again. 

Any suggestions?

---

### Post by Billy_Martinez on 2015-10-23
This is my config file

*[global]*
*   workgroup = techs*



*[Fech]*
*path = /mnt/files/Tech*
*valid users = bill*
*read only = no*

*[print]*
*load printers = No*
*printing = bsd*
*printcap name = /dev/null*
*disable spoolss = Yes*


While I was coping a large file, the copy process froze and I got this message in the log file. 

*[2015/10/23 14:43:40.716677,  0] ../source3/param/loadparm.c:3188(lp_do_parameter)*
*  Global parameter load printers found in service section!*
*[2015/10/23 14:43:40.716861,  0] ../source3/param/loadparm.c:3188(lp_do_parameter)*
*  Global parameter printcap name found in service section!*
*[2015/10/23 14:43:40.716936,  0] ../source3/param/loadparm.c:3188(lp_do_parameter)*
*  Global parameter disable spoolss found in service section!*
*[2015/10/23 14:43:40.717005,  0] ../source3/param/loadparm.c:2376(service_ok)*
*  WARNING: No path in service print - making it unavailable!*

---

