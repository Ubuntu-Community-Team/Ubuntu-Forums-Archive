---
title: "Unique number?"
date: 2007-11-25
forum: Server Platforms
---

### Post by Dudsmacka2 on 2007-11-25
I'm in the process of writing run-level scripts to notify a central server when a node hits certain conditions.

I'm looking for some type of unique value I could read of the nodes (ubuntu machines).

I don't want to use either MAC addresses or hostnames - just in case they were to ever change.  I'd rather not read the CPU-ID.  

I was thinking along the lines of possibly reading the serial number of a formatted hard drive.  I don't know if this is doable - I know windows will give each format a unique number - but I don't know if linux had anything like that.

Is there anything unique about the linux install I could retrieve?

---

### Post by MJN on 2007-11-25
I was going to suggest the UUID of the first partition of the disk (e.g. **udevinfo -q env -n /dev/hda1 |grep ID_FS_UUID**) however that suffers from the problem you've addressed with MAC addresses in that it would change should the drive be changed due to failure.

In fact, you're more likely to change a drive than a network card given the relative failure rates of the two so it is arguably worse than using a MAC address.

I'm more inclined to suggest the one-time generation of a UUID _for the machine_ i.e. not relying in the uniqueness of any one device within in as in theory anything could be subject to replacement.

There are many UUID generators available in various forms - Google for whatever form might suit you best (e.g. Python module etc).

Mathew

---

