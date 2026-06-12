---
title: "Server slows down while moving between partitions"
date: 2010-12-30
forum: Server Platforms
---

### Post by elico on 2010-12-30
im using ubuntu server 64 bit on intel atom410D.
when im using my SATA DRIVE as AHCI mode while i moving 4 GB files from one partition to another my server is getting so slow that it will take me to login on ssh 2 minutes.
so i have seen a thing or two about a bug on it.
i changed the AHCI mode to IDE mode and now it seems to work better.

anyone got into it?
thanks

---

### Post by jbrown96 on 2010-12-30
It's because your disk is completely saturated. It's thrashing between reading and writing. Separate partitions doesn't matter because it's one hard drive.
When you login a Linux terminal, there are several files read: Bash or whatever your shell is, your .bashrc and system shell profiles, and and perhaps a few other things (MOTD, mail, etc.). All of those are very small reads, but they are at separate locations on disk, which causes seeking. On a busy disk that can be really slow, especially on what seems to be a netbook. AHCI or IDE don't have anything to do with. Maybe insofar as one technology is theoretically superior, but with a slow CPU, terrible chipset, and a cheap, slow hard drive, AHCI/IDE is the least of your worries.


If you update your kernel to 2.6.37 (when it's released in a few weeks) and do some minor customization of cgroups, then you can largely fix this problem. The system will remain far more responsive.

---

### Post by elico on 2010-12-31
i now all this stuff already.
well i have a very strong machine but what is good for me on that machine that it gives me what i need  and also low power consumption.
it's about 40W aginst 500W (the stronger machine).
i need very little from the machine: routing\gateway+pppoe \ apache \ torrent downloading \ storage \ mail.
this machine can do it with no problem.
the only problem is this specific state so what ever if on ide mode it's working fine.. im ok with it.
my down\up speed from the server is something like 200-250Mbps so im ok with it.
thanks.
i will think about some better long term solution.

---

