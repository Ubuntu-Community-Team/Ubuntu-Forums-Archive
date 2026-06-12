---
title: "BTRFS mirror as Root with separate boot"
date: 2011-09-13
forum: Server Platforms
---

### Post by fnordistus on 2011-09-13
Hello dudes.
Actually i run ubuntu natty on a md raid1.
i bought two SSD drives each 120GB and now i try to move the root partition to those btrfs mirror
the problem is grub actually doesnt support multiple BTRFS devices as boot, So my idea was adding a separate md drive just for the /boot partition.
So the boot partition is able to access the btrfs root.
i copied the boot files to those md drive consisting of sdn and /sdo, and installed grub to those drives. but i have no clue how to edit those grub.cfg at /boot so it starts btrfs from sdn or sdo.
thanks in advance

---

