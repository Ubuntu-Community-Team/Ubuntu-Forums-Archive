---
title: "Server software RAID"
date: 2013-04-12
forum: Server Platforms
---

### Post by mea405 on 2013-04-12
Hi,

Server configuration: supermicro X9SCL-IIF, LSI9211-4i, 12 SATA HDD 3GB

I first put on the Ubutnu server with the software RAID.
Could you please advise the correct configuration.
Initially I tried to install the server on [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html).
RAID array is successfully created, it got a system, but GRUB does not get up. All my attempts to fix it failed. 
So I thought that maybe it makes sense to change the configuration of the RAID, create some auxiliary partition?

I tried to install 12.04 and 12.10 server.

Please help!

---

### Post by darkod on 2013-04-12
The first important thing you need for SW raid is the controller to have pass through mode for the disks. The raid shouldn't be on the controller, it will be created by the ubuntu server OS.

When you reached the partitioning step did you select Manual? Did it show all 12 disks as separate?

For such a big array it's best to make a small array for /boot, so that the boot files are kept at the start. You will also need to use gpt table on disks of 3TB and that requires a small 1MiB bios_grub partition so that grub2 can install.

First of all, confirm all disks are seen as pass through on the controller.
Second, explain a little bit how you plan to organize the disks/raid so we can help with advice. Do you plan only one huge array? What raid level?

What will you use the server for, only network shares?

And the best version to use is 12.04.2 LTS because it's LTS and has 5 years support.

---

### Post by mea405 on 2013-04-12
> **darkod said:**
> the first important thing you need for sw raid is the controller to have pass through mode for the disks. The raid shouldn't be on the controller, it will be created by the ubuntu server os.

When you reached the partitioning step did you select manual? Did it show all 12 disks as separate?
**Yes!**

> **darkod said:**
> for such a big array it's best to make a small array for /boot, so that the boot files are kept at the start. You will also need to use gpt table on disks of 3tb and that requires a small 1mib bios_grub partition so that grub2 can install.

First of all, confirm all disks are seen as pass through on the controller.
Second, explain a little bit how you plan to organize the disks/raid so we can help with advice. Do you plan only one huge array? What raid level?

What will you use the server for, only network shares?

And the best version to use is 12.04.2 lts because it's lts and has 5 years support.
The server will be used to back up user data. 
Originally planned to create one large array. Perhaps it makes sense to drive separate  partition for /boot, can be for the system ... 
Just what I wanted to hear comments correctly, stable server configuration.

Thank you,

---

### Post by darkod on 2013-04-12
I would configure a raid1 array for / but using all 12 disks is too much. You can use partitions on 4 disks for example.

As for the main array, what type of user data are we talking about? Each user having it's own home folder, or simply folders for music, videos, photos, etc, that will be used by all users.

---

### Post by mea405 on 2013-04-13
As you and advised I created a small RAID1 disk. But installing the GRUB again failed. Here are the contents of the log.

---

### Post by darkod on 2013-04-13
If the disks have gpt table, do they have the small bios_grub partition that I mentioned? For grub2 to install on gpt disks, it needs a small 1MiB partition with no filesystem (raw format) and that has the bios_grub flag set.

You can prepare that in advance booting into live mode with the desktop live cd. After you prepare the partitions you can do the server install.

---

