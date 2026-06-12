---
title: "Disk Usage"
date: 2009-11-24
forum: Virtualisation
---

### Post by Zatara214 on 2009-11-24
While running Windows 7 (or any other OS, really, but in this case it's 7) under VMware on an Ubuntu host, my disk usage is through the roof constantly.  I can barely use my host OS, never mind my guest.  I have a Sager NP8660 laptop with a P8600 processor, which is really quite a quick machine.  I know it shouldn't be doing this.  Are there any options that are enabled by default that I can disable to increase the speed a bit?

---

### Post by fjgaude on 2009-11-24
Try using only one core if you are now using more than that. With all the testing I've done, one works better than two or more.

---

### Post by dcstar on 2009-11-24
> **Zatara214 said:**
> While running Windows 7 (or any other OS, really, but in this case it's 7) under VMware on an Ubuntu host, my disk usage is through the roof constantly.  I can barely use my host OS, never mind my guest.  I have a Sager NP8660 laptop with a P8600 processor, which is really quite a quick machine.  I know it shouldn't be doing this.  Are there any options that are enabled by default that I can disable to increase the speed a bit?

[LIST=1]
[*]You have not allocated enough RAM for each VM
[*]You don't have sufficient swap and or RAM on the host
[/LIST]

---

### Post by Zatara214 on 2009-12-01
I'm using only one processor, as ACPI I/O slows down the machine significantly.  Also, I have 1400 MB of RAM allocated to Windows 7 out of 4 GB total, which should be plenty.  The swap is system managed, so it should also be fine.  I could probably disable it if I wanted to with 1400 MB RAM.

VirtualBox seems to have MUCH better I/O performance, but lacks DirectX and Aero abilities.  I'm thinking there must be a way to improve the performance in VMware.  It's got to have something to do with the virtual disk format.  VirtualBox uses a less compatible but higher performance format, whereas VMware uses higher compatibility, allowing for easier transfer of data between hosts.  Is there a way to switch which disk format you're using?

---

