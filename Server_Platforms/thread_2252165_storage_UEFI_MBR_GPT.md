---
title: "storage UEFI MBR GPT"
date: 2014-11-09
forum: Server Platforms
---

### Post by Vegan on 2014-11-09
I have been testing Windows and so far all desktop variants still want MBR to install. Windows Server 2012 R2 wants GPT. This all on a UEFI box.

All it means is larger disks are installed as secondary, no big deal

so I was thinking what to do with an older rig, with 5 drive bays and wanting a low cost backup server

I have used SAMBA in the past but I am not so good at figuring out how to deal with disks more easily, maybe I need more shell scripts?

I own a single ST3000DM001 which is too big for MBR etc.

Now I know Linux can cope, but what kind of solutions are available these days?

---

### Post by oldfred on 2014-11-09
All recent 64 bit versions of both Windows & Ubuntu install in UEFI boot mode from gpt partitioned drives.
If drive is MBR then you can only install in BIOS boot mode. If drive is over 2.2TiB then you must use gpt to fully use entire drive.

Most Windows 7 on DVD choose BIOS/MBR be default but you can copy to flash drive and do some updates to make it an UEFI install disk.

---

### Post by houstonbofh on 2014-11-10
You may want to look at nas4free. It is a FreeBSD based appliance distribution designed to make a multi-disk storage server that is easy to manage.  It supports MBR and GPT.  It boots off a thumb drive, so all drives can be pure data.  It also means you can use 4TB and 4TB drives in no-UEFI machines.  It will also do ZFS or MDadmin for the drives.
[www.nas4free.org](www.nas4free.org)

---

