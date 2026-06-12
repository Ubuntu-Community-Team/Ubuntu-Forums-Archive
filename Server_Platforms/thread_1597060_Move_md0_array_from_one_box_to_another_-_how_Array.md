---
title: "Move md0 array from one box to another - how? Array shows up..."
date: 2010-10-14
forum: Server Platforms
---

### Post by zsouthboy on 2010-10-14
I've been poking at the options in mdadm and dmraid for 2 hours now and don't see exactly what I need. (and trying things I'm not 100% sure of would be silly)

2 drive raid1 array. moved to another box running the same version of Ubuntu. (10.04)

I've googled and googled and can't find anyone else with this same task - what am I missing? The array is physically fine and doesn't need rebuilding, unless in this context it does somehow.

The two devices are sdb and sdc. 

Output of mdadm -Es:
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=97e83cac:4d76d392:e368bf24:bd0fce41

```

So the array is somehow visible, but I don't see what my next step needs to be.

Any help would be appreciated.

---

### Post by zsouthboy on 2010-10-14
Tada!

I didn't do anything and it magically showed up the next time I rebooted (after having installed mdadm and mdraid, I assume something recognizes it during boot) and it mounted perfectly.

---

