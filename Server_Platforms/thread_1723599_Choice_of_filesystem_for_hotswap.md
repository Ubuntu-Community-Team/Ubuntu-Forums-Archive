---
title: "Choice of filesystem for hotswap"
date: 2011-04-07
forum: Server Platforms
---

### Post by jorijn on 2011-04-07
Hi,

I'm installing Ubuntu 10.04 server on a HP MediaSmart server. Attached is an eSATA multi-bay with four hotswap disks.

Since these disks are rotating on a daily basis I'm looking for the best filesystem for hot swapping purposes. If there is no choice I'll just stick to ext4 with safe unmount. 

But if its possible I'd like something so I could pull the disk out without damage. In my case it would be safe to assume that the disk hasn't been written to in the last 5 minutes before rotating.

Regards,
Jorijn Schrijvershof

---

### Post by Vegan on 2011-04-07
I use ext4 as it seems to be stable and no problems with large files etc.


Typically hot swap is a feature of high-end controllers.

---

### Post by jorijn on 2011-04-07
Thank you for your reply. I do know that hotswap is supported in my multi-bay device. Its originally meant for Windows Home Server. It grown very slow and we can't hardly work with it anymore. But we always swapped disks without unmounting.

---

### Post by iissmart on 2011-04-07
Are the disks seen as separate devices to the OS or is there some sort of RAID (hardware, software) that you've configured?

---

### Post by disabledaccount on 2011-04-07
> **Vegan said:**
> I use ext4 as it seems to be stable and no problems with large files etc.
Typically hot swap is a feature of high-end controllers.
...Google is using Ext4 - so probably it is stable...
Typically *every* SATA controller supports hot-swap on hardware layer - this is part of SATA/SAS specification - but windows is unable to handle this feature correctly under typical understanding of such functionality - so You must buy some linux-based NAS box or some expensive controller with proprietary software to get such functionality.
Unlike windows linux supports hot-swaping of block devices, what means md-based arrays supports hot-swap too.

> **jorijn said:**
> I do know that hotswap  is supported in my multi-bay device. Its originally meant for Windows  Home Server. It grown very slow and we can't hardly work with it  anymore. But we always swapped disks without unmounting.Array members are not mounted - I know this can be counfusing, but simplest explanation is that from filesystem point of view any array is just single device, even in degraded state.
Mount means "registering" of filesystem, not underlying device(s). So it is completely irrelevant what filesystem You will use. But some filesystems are working good on arrays, some other not necessarily - Ext4 is nearly perfect for stripe-based arrays - as it can co-operate with underlying array layer (unlike ntfs f.e.)

---

### Post by jorijn on 2011-04-07
> **iissmart said:**
> Are the disks seen as separate devices to the OS or is there some sort of RAID (hardware, software) that you've configured?

The reason I'm asking for are four separate disks. They'll be rotating so we always have a fresh copy of our back-ups out of the building.

Thank you for your help all. I guess I'll just stick with ext4 :-)

---

### Post by elico on 2011-04-08
if it's a backup and you are using ext4...
i have found a one software that can help you in any case of ext4 troubles.
i had my ext4 driver just snap out of "having" files so i used:
UFS explorer.

---

