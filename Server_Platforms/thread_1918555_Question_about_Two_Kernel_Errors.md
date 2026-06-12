---
title: "Question about Two Kernel Errors"
date: 2012-02-01
forum: Server Platforms
---

### Post by dieselchair on 2012-02-01
Hello this is my first time posting to the Ubuntu forums.

A few months ago i was inspired to buy a server not having a single clue what i would be getting into or what to use it for. Now several months later I've learned more about servers and linux than i could have ever hoped for. Ive been using linux for over a year now for mostly fun but this server has kind of forced me to dig in and really learn about linux.

My question is about 2 kernel errors that showed up in logwatch. 

this is what i get when i run ```
 dmesg | grep -i error 
```

```
[    9.835117] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   10.354409] Contact your BIOS vendor to see if the E752x error registers can be safely un-hidden

```

The server is running fine no noticeable lag or other issues.
My question is how can i fix these errors and where can i learn more about them?

Running the latest Ubuntu server
Dell Poweredge 2850
2 Xeon 64bit single core processors
4gb Ram
2 Raid Arrays 
Two 70gb hard drives in raid 1
Four 147gb hard drives in raid 5
with DRAC 4

---

### Post by SeijiSensei on 2012-02-01
The first entry isn't an error.  When the machine boots, the primary filesystem is mounted read-only until the boot process completes, at which time it is remounted as writable.  The entry you list is the report that the remount has taken place.  The "errors" line only indicates what would have happened (remounted as read-only) if errors were detected in the filesystem.

I have no idea about the second error, though it doesn't sound all that serious, and you don't detect any problems with the machine.  I'd read the lines right above that one to get some context for the message.

---

### Post by dieselchair on 2012-02-01
Thank you for your help

I took a look at the lines above the second messeage and this is what was there
```
[   12.777710] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.785126] lp: driver loaded but no devices found
[   12.799287] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   12.821312] EDAC MC: Ver: 2.1.0 Jan  3 2012
[   12.839647] Contact your BIOS vendor to see if the E752x error registers can be safely un-hidden
[   12.857811] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20110112/video-1139)
[   12.857935] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0d/LNXVIDEO:00/input/input3
[   12.858062] ACPI: Video Device [EVGA] (multi-head: no  rom: yes  post: no)

```

Im guessing its something to do with edac mc.

---

