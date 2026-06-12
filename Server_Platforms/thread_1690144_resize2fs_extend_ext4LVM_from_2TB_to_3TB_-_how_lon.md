---
title: "resize2fs: extend ext4/LVM from 2TB to 3TB - how long?"
date: 2011-02-17
forum: Server Platforms
---

### Post by pneumatic on 2011-02-17
So the "online" feature of resize2fs isn't really "online" - it just disables all access to the partition while the resize runs.

That horrible fact aside... can someone tell me about how long it is going to take in order to grow 2TB to 3TB under the context of ext4 on an LVM which is sitting on a RAID6 of 1TB/7200rpm disks?

Is this going to take a week?  A day?  5 hours?  Can I cancel it?

As a suggestion, the "online" feature should be removed unless it can be modified to do the resize without interrupting service.

---

