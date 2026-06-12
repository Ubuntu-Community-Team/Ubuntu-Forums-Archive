---
title: "Kernel errors from mdraid component volumes??"
date: 2009-08-23
forum: Server Platforms
---

### Post by shirsch on 2009-08-23
After a recent kernel upgrade, I've been getting ugly error messages that I believe are the result of the initrd environment trying to fathom the partition table from disks that are part of a Raid5 array.  The errors are complaints about block limits being past the end of the device, which makes sense in the context of a drive that's < 1/3 the size of the "real" volume (as seen when the md driver is present).  Once the md driver loads, things are just fine and the volume is intact and usable.

How can I get the kernel to not probe the RAID components, but wait until the md driver is up?

---

