---
title: "Reinstall Grub Loader on Ubuntu Configured with Raid 10 MDADM"
date: 2016-06-29
forum: Server Platforms
---

### Post by brian132 on 2016-06-29
I managed to install Ubuntu server on my machine and set up the machine using Raid 10 with the help of MDADM a couple months ago. Yesterday i ran an update on the system and then when restarting the machine I get to the Grub Rescue shell. I have since loaded the Ubuntu Live CD and attempted running Boot-repair as well as running Grub install on the mounted rootfs but Grub fails to install and gives the error that EXT2 file system is not supporter and it cannot embed.

Simply put. I need to be able to load the machine so that I can launch the MYSQL server and extract the database. How i achieve this is irrelevant. If i can use a windows boot loader or another method of extracting the database from the ubuntu live CD then I will be a very happy camper.

Can anyone assist?

---

### Post by howefield on 2016-06-29
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by oldfred on 2016-06-29
Embedding error is either installing grub to a partition or an MBR  on a gpt partitioned drive without a bios_grub. If you booted before, you should not have either of those errors.

This is a typical error:
>  Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force  



There are many types of RAID, and I do not know them well enough to know differences. But some do use MBR as hardware RAID is just seen as one drive, some are BIOS based RAID and install to the /mapper's root not drive's MBR.

This says you install to MBR like any standard install. Is drive MBR or gpt? If gpt you need bios_grub and may then need one on every drive as Boot-Repair tries to install grub to every drive.
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Post link to Boot-Repair's summary report.

---

