---
title: "Convert P2V: kernel panic not syncing vfs unable to mount root fs on unknown-block 0,"
date: 2018-04-07
forum: Virtualisation
---

### Post by maxburn on 2018-04-07
I have a 16.04LTS running on an intel NUC that seems happy there. I'm trying to P2V to my ESXi6.5u1 machine. The machine is up to date with apt-get update etc. Conversion seems to go fine though I did make the memory and disk sizes a little smaller, but still way bigger than it needs. Booting that VM gets me kernel panic not syncing vfs unable to mount root fs on unknown-block 0,0.

Tried to boot advanced options and it shows one for upstart and another for recovery mode. They all boot to the same error. Following some guides online I hit C to go to command line and for example "df -h" results in error: can't find command 'df'. Every command I'm finding online to troubleshoot this is not found. 

What should I do?

Edit1: Deleted the VM and converted it again, only this time selecting SATA disks instead of the suggested SCSI, which would match the source machine. Same exact problem.
Edit2: Third time through I found a warning message about resizing boot, set that to the same size but still got same error. 

[IMG]https://i.imgur.com/ubdTOoc.png[/IMG]

---

### Post by ajgreeny on 2018-04-07
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

