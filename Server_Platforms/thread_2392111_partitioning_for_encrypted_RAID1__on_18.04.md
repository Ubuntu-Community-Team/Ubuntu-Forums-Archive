---
title: "partitioning for encrypted RAID1 / on 18.04"
date: 2018-05-16
forum: Server Platforms
---

### Post by mfleming on 2018-05-16
I use an Ubuntu server with an encrypted RAID1 root partition. I have been doing this for many years, but am trying now to put together a new server running 18.04, and it won't boot. It has a Ryzen 2400G and cheapo MSI motherboard set for UEFI boot only. There are two identical 2 GB SATA disks. Most of each disk is used for the RAID1 encrypted root partition. Each disk also has 100 MB set aside for another RAID1 partition which is not encrypted and mounts /boot. On one disk is a 200 MB FAT32 partition with /boot/efi mount point. The other disk has an unmounted 200 MB FAT32 partition. There are no other disks in the computer.

I used the "alternative installation" iso to install 18.04, which completed without complaint. But it won't boot -- I get a purple, then black screen. I tried running boot repair, and it said it fixed the problem, but then still wouldn't boot. 

I'm assuming that the partition table is just wrong -- I'll be the first to admit I don't understand UEFI. Having /boot and /boot/efi on two different partitions seems questionable, but installation wouldn't complete without it.

Thanks very much in advance for any advice/assistance.

Matthew Fleming

---

