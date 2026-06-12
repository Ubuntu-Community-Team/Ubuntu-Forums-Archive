---
title: "Ununtu 8.04 raid controller LSI 1068E SAS/SATA"
date: 2008-06-10
forum: Server Platforms
---

### Post by Sb0y on 2008-06-10
Hello ALL. I have just install ubuntu server edition from CD and system not find any disks :D
On server machine installed RAID controller LSI 1068E SAS/SATA.

I go to google and find drivers on official LSI site, but only for Red Hat and SUSE.

How I can solve my problem? Please help =)
---
Andrei

---

### Post by Sb0y on 2008-06-12
We Going Up!!!

---

### Post by pgjensen on 2008-06-24
I am getting the following errors with this card via linux:

ata_id[####]: main: HDIO_GET_IDENTITY failed for '/dev/.tmp-8-32'
etc
etc
etc


i can cfdisk and create a partition on the drives (dunno if it lasts or not), but when I go to format it says device busy or in use.

works 100% in windows.

hooked via external EBOD (extended bunch of disks) and everything should be communicated via the LSI SAS card directly.

---

