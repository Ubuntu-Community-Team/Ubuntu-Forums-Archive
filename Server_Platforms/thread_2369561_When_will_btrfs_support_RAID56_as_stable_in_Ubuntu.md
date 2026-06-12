---
title: "When will btrfs support RAID56 as stable in Ubuntu?"
date: 2017-08-24
forum: Server Platforms
---

### Post by cwempe on 2017-08-24
Hello,

I want to build a home NAS with the following specs:

[LIST]
[*]Ubuntu Server 16.04
[*]2x SSDs in RAID (for OS and VMs)
[*]6x 8TB HDD RAID6
[LIST]
[*]btrfs (if possible)
[/LIST]
[/LIST]
I know btrfs-RAID56 is not stable at the moment. But there should be a patch to fix the issues.
[https://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg66472.html](https://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg66472.html)

Now my questions:

[LIST]
[*]Will this patch make RAID56 "stable" or are there more issues left?
[*]How long will it take until the patch is tested (enough)?
[*]If I understand correctly, the patch will be included in future kernel versions:
[*=1]Will these be available in Ubuntu 16.04 or would I need to install an unsupported kernel?
[*=1]Or will an updated btrfs package be sufficient?
[/LIST]
Thanks

---

### Post by TheFu on 2017-08-24
Don't know, but [https://www.phoronix.com/scan.php?page=news_item&px=Red-Hat-Deprecates-Btrfs-Again](https://www.phoronix.com/scan.php?page=news_item&px=Red-Hat-Deprecates-Btrfs-Again) is worth a read.

I wouldn't deploy anything on BTRFS.

SuSE came out with an announcement of strong support for BTRFS, including their roadmap for supported features.

---

