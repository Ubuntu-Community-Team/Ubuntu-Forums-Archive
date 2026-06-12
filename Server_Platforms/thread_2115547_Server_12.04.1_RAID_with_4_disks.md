---
title: "Server 12.04.1 RAID with 4 disks"
date: 2013-02-13
forum: Server Platforms
---

### Post by Lodododo on 2013-02-13
Hello,

I'm trying to setup a NEW Ubuntu install with a raid configuration with 4 disks. I've previously setup a RAID-1 config with 2 disks.

I've got two 1.5 TB Disks and two 80GB disks. I would like to know what kind of RAID I should use (RAID 5?) and how to partition the disks.

Could anyone point me in the right direction?

EDIT: I also have Intel Matrix, should I use that?

---

### Post by darkod on 2013-02-13
With disks of that size, there is not much you can do. RAID arrays are limited to the smallest member size, so if you create raid5 of all four disks, it will only have 80GB partitions as members.

With mdadm SW raid you can use the rest of the 1.5TB disks but I don't see much point configuring it like that.

Probably the best configuration is a raid1 array of the 80GB disks for the OS and some smaller data folders, and separate raid1 array of the big disks for the large data storage.

Note that I am talking about SW raid. If you use HW raid or fakeraid I think it will use only 80GB of the big disks and you won't be able to use the rest.

---

### Post by Lodododo on 2013-02-13
> **darkod said:**
> With disks of that size, there is not much you can do. RAID arrays are limited to the smallest member size, so if you create raid5 of all four disks, it will only have 80GB partitions as members.

With mdadm SW raid you can use the rest of the 1.5TB disks but I don't see much point configuring it like that.

Probably the best configuration is a raid1 array of the 80GB disks for the OS and some smaller data folders, and separate raid1 array of the big disks for the large data storage.

Note that I am talking about SW raid. If you use HW raid or fakeraid I think it will use only 80GB of the big disks and you won't be able to use the rest.

Thanks alot

---

### Post by Lodododo on 2013-02-13
Great, when I try to setup the raid configuration the SDB shows up, but the SDD doesn't, then I want to make a new partition and it says it's going to remove the raid devices, but it doesn't

---

### Post by darkod on 2013-02-13
Make sure you have no fakeraid meta data on any disks. If they were used in raid earlier traces remain. It confuses the installer since it considers them part of raid. Formatting doesn't remove meta data.

If you really have meta data on any disk, for example sdd, you can remove it from ubuntu live mode with:
sudo dmraid -Er /dev/sdd

PS. Are you talking about software raid or not?

---

### Post by Lodododo on 2013-02-13
> **darkod said:**
> Make sure you have no fakeraid meta data on any disks. If they were used in raid earlier traces remain. It confuses the installer since it considers them part of raid. Formatting doesn't remove meta data.

If you really have meta data on any disk, for example sdd, you can remove it from ubuntu live mode with:
sudo dmraid -Er /dev/sdd

PS. Are you talking about software raid or not?

Thanks, fixed it.

---

