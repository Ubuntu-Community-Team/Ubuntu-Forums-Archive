---
title: "RAID 5 performance"
date: 2010-09-13
forum: Server Platforms
---

### Post by Skaperen on 2010-09-13
In theory, if a write operation is performed to a RAID array, where the size of the operation is the stride times number of data drives (e.g. not count the parity drive), it should not need to read anything ... it would calculate parity and just write all data drives and the parity drive in parallel.

Any idea how to get the kernel to make write requests to RAID devices at this size when that much data is available (e.g. sequential writes)?

I note that EXT4 and XFS filesystems have a setting for this.  Do these filesystems have special device level access to do that?

---

