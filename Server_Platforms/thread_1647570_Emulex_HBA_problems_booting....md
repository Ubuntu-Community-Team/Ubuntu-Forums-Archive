---
title: "Emulex HBA problems booting..."
date: 2010-12-17
forum: Server Platforms
---

### Post by CheetoBandito on 2010-12-17
I cannot boot my 10.04 Server edition box with an Emulex card and fibre running to a storagetek array.  Unplugging the fibre connection and plugging back in once booted is fine.  Once booted I can mount the partition and everything is great.  /dev/sdb and /dev/sdc are the two devices assigned automatically, sdb mounts just fine and sdc is the one that's causing the boot problem.  The console streams with bad sector errors, etc upon boot from sdc.

I've looked into ignoring the device path and I'm aware of how to get the path from udevadm, but I'm reading that the ignore option has been removed from udev.  Is this true and/or am I approaching the problem correctly?  Thoughts?

---

### Post by CheetoBandito on 2010-12-20
bump

---

