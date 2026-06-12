---
title: "Lucid Server x64 On RAID"
date: 2010-07-20
forum: Server Platforms
---

### Post by peridian on 2010-07-20
Hi,

My Foxconn motherboard has an onboard RAID setup, so I have two 500GB drives in a mirror.

Lucid during install sees the drives, but is unable to install (keeps throwing a Cannot create partition ## on drive)

a) During disk detection, it comes back saying it has detected RAID devices, do I want to activate?  I assume this is actually referring to some sort of software managed RAID, since the hardware is already sorted.

b) If there was an old install of CentOS on here from some time ago, could that mess setting up new partitions?

Essentially, all I need to do is a clean install of Server, but it keeps complaining.

Any help is appreciated.

Regards,
Rob.

---

### Post by peridian on 2010-07-21
Hi,

Quick update, it seems it did not like using the ext4 system that I asked for, so when I switched all of them to ext2, it did not complain.

However, the new problem seems to be that it fails to mount the / root onto the relevant partition.

Regards,
Rob.

---

