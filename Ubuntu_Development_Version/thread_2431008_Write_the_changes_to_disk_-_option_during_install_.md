---
title: "Write the changes to disk - option during install of daily iso"
date: 2019-11-10
forum: Ubuntu Development Version
---

### Post by jidar on 2019-11-10
While attempting to install the daily iso I downloaded on Friday I noticed that the installer provides some feedback that got me to stop the install process and post here.



So I made a test case and did a install with another disk attached to a VM, which does not produce the same results:



In this second image, I did a install to "vda" and rebooted into the install iso, and went to do a install to "vdb", in this second case the partition table for "vda" does not appear to be changed. Can anybody help explain what's going on here?

Edit: To make things clear, in the first image I'm attempting to install to a disk and it complains about changing partition tables for _other_ disks (this would be bad!)

---

### Post by oldfred on 2019-11-10
Do you have a swap partition on every drive? It will try to mount and may reformat swap partitions if found. Some have posted that UUID of swap was changed and caused issues booting a different install. Not sure if that was Ubuntu or another distribution.

Otherwise what are those partitions?

When I installed it, I told it to use one partition as / , not to use swap which I did have, so it would use swap file and to use ESP on sdb, which it ignored and used ESP on sda anyway.

---

### Post by jidar on 2019-11-10
> **oldfred said:**
> Do you have a swap partition on every drive? It will try to mount and may reformat swap partitions if found. Some have posted that UUID of swap was changed and caused issues booting a different install. Not sure if that was Ubuntu or another distribution.

Otherwise what are those partitions?

When I installed it, I told it to use one partition as / , not to use swap which I did have, so it would use swap file and to use ESP on sdb, which it ignored and used ESP on sda anyway.

There's 5 other disks in the system, in the image - sda is the install disk, [cdgh] are either unformatted or part of a another zpool. There are no swap devices

---

### Post by jidar on 2019-11-11
I'll note that each disk listed in the first screenshot is a gpt style  disk. I also tried to reproduce this in a VM with two disks but was  unable to.. it's a really strange statement

---

### Post by sudodus on 2019-11-11
I have noticed the same output or something similar, but was working in a dedicated computer for testing, so I did not react very much.

I think you have found a bug. That warning about writing to several drives is probably wrong, but it is scary in a real case when you install alongside a drive with some valuable partition.

I think the partition table is only modified in the drive where you actually create or edit a partition.

---

