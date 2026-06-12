---
title: "Reducing an LVM PV partition"
date: 2008-07-31
forum: Server Platforms
---

### Post by Adam Atlas on 2008-07-31
I have a hard drive which is currently entirely occupied by an LVM Physical Volume partition. I need to add a small partition at the end -- but a plain IBM/DOS-style partition, not an LVM logical volume. I resized one of the logical filesystems and its logical volume to make room, and there are indeed enough free extents for my purposes, but pvresize(8) says, under Restrictions, "pvresize will refuse to shrink PhysicalVolume if it has allocated extents after where its new end would be. In the future, it should relocate these elsewhere in the volume group if there is sufficient free space, like pvmove does." That's what I'm trying to do essentially, but pvmove itself doesn't seem to be what I'm looking for, as I can't figure out if it can be told to move extents on one physical volume into a restricted range on the *same* volume instead of to a different physical volume. Is there a workaround for that?

---

