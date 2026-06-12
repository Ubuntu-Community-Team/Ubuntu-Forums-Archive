---
title: "Multi RAID with SSD config for build server"
date: 2010-08-20
forum: Server Platforms
---

### Post by bedge on 2010-08-20
We have new G7 with 2 X5680 3.3GHz i7's and 48 GB RAM. The question is, how to config the storage for max benefit as a an Ubuntu build server.

It came with 2 RAID cards:

p410i with a max of 8 devices - not the fastest controller
p812 with a max of 8 devices - a very fast controller

I have 14 disks and 2 SSD to populate any way I want.

What's the best config for a build server?

I'm puzzled about how to configure the RAID controllers for maximum benefit.

I'm thinking that I should put one SSH on each controller, then configure a RAID with the 7 disks on each controller so that Linux sees 2 RAID vols, and 2 SSD. 
That will let me use flashcache to create two SSD cached volumes.

eg:
flashcache_load cachedev /dev/sdc /dev/sdb
Load the existing cache on /dev/sdc, calling the flashcache volume cachedev.

Where sdc is an SSD and sdb is a RAID vol.

Then, use lvm to aggregate these into one VG.

Or, do I use the 2 SSDs in a RAID for the OS and aggregate the other 2 RAIDs for the build storage?

Or?

There are a lot of options on how to set this up. I'd appreciate any suggestions.

---

