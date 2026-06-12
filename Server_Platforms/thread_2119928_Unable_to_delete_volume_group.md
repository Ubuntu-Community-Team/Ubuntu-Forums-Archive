---
title: "Unable to delete volume group"
date: 2013-02-25
forum: Server Platforms
---

### Post by tpradeep on 2013-02-25
When i try to remove stack-volumes group..it gets stuck as shown

 lvm vgremove stack-volumes
Do you really want to remove volume group "stack-volumes" containing 1 logical volumes? [y/n]: y
Do you really want to remove active logical volume volume-d9e29e91-d281-43ed-82c7-d28b0890de79? [y/n]: y

Any idea how to remove this ?

---

### Post by darkod on 2013-02-25
Have you tried removing the LV first?

And made sure the LV is not mounted?

Of course, removing it will destroy all data on it, I hope you are aware of that. If you only want to remove a physical disk/partition from the LVM so that you can use it for something else, you need to move all data from that physical device fist using LVM tools, then remove it from the VG. Otherwise the data on it will be lost.

---

