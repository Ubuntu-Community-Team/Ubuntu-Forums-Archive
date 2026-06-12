---
title: "Partition table for virtualization system"
date: 2012-07-06
forum: Server Platforms
---

### Post by doktoreas on 2012-07-06
Hello everybody,

I have an Ubuntu Server machine and I need to use it for creating virtual machines (with KVM). After reading some docs to understand which is the best partition table for this situation, I came to this:

1 Ext2 for boot
1 Swap Space
1 VG with: 
1 LV for the host system (about 10% of the total space)
1 LV for each VM I need to create.

What do you suggest? Should I create an ext4 partition for the host system and use VG only for the VM?

Thx
L.

---

