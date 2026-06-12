---
title: "Install Ubuntu Server 20.04 on mdm RAID 1"
date: 2020-04-24
forum: Server Platforms
---

### Post by deder on 2020-04-24
I'm trying to install Ubuntu Server on a machine with 2 SSDs using RAID 1. Whenever I create the mdm array I get the error "If you put all disks into RAIDs or LVM VGs, there will be nowhere to put the boot partition", however whenever I try creating any kind of partition first like in this guide [https://ubuntu.com/server/docs/installation-advanced](https://ubuntu.com/server/docs/installation-advanced) the option for creating a Software RAID is grayed out and I can't select it.
Is there something else that I'm missing?

---

### Post by darkod on 2020-04-25
The option might be grayed out if you try using disks instead of partitions. So because you already have partitions it might not allow you to create raid1.

But that is OK, you should use mdadm with partitions anyway.

Good practice for any boot disks is to create first very small 1MiB partition with NO filesystem (unformatted). That one is used in case of legacy boot with gpt disks.
Then one 250-300MiB partition formatted as fat32. That one will be the UEFI partition for UEFI boot.

After that create other partitions as needed. For example, if you want one large raid1 array you create just one more partition. Also unformatted. With mdadm the filesystem is on the md device, so do NOT format the partitions that will make up the array.

Better practice would be smaller partition for root, and the rest for bigger raid1 for data. Especially on a server. That way you could even format the root and reinstall without losing any data.

But it is up to you how you do your design. Also, now there are various installers, like the -live-server- ISO so it starts to get confusing when you simply say the installer is giving you problems. We can't know which one exactly. For servers, I still continue to use the good old -server- ISO, not the newer one.

PS. If possible I would still continue to use legacy boot with gpt disks on ubuntu servers. I still try to avoid EFI boot whenever possible. For me it makes no sense because despite the raid the EFI files will be on one disk only. If that disk dies you lose the UEFI partition content. With legacy boot grub it is not so. You can have it on all disks and it can boot from any.

---

### Post by deder on 2020-04-25
I figured it out, it's a bug in the new installer. I had to dig through the old versions to find 18.04.2, which uses the old installer.
The old installer worked just fine and I was able to upgrade to 20.04

---

