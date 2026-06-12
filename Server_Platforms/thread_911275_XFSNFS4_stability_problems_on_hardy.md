---
title: "XFS/NFS4 stability problems on hardy"
date: 2008-09-05
forum: Server Platforms
---

### Post by pgfault on 2008-09-05
I've been getting fileserver hangs on a regular basis.  Symptoms include very slow response time, kswapd running at 100%, and eventually all the nfsd processes in disk wait state.  System uptime averages about 1-3 days. Sometimes this occurs during a rsync, sometime it occurs out of the blue.

Configuration:
Dell 1950, dual Xeon 5420, 16GB RAM, 2 internal SAS drives, SAS6/E
Dell MD1000 array w/ 15x300GB SAS drives.
No swap.
Software RAID1 /dev/md0 on internal drives (ext3)
Software RAID6 /dev/md1 on external drives
LVM on top of /dev/md1
XFS and ext3 filesystems on LVM
Exported via NFS4 with sec=krb5, and NFS3.
Approx 200 nfs4 clients, a handful of nfs3.
OS: hardy 64-bit, all current updates

I've swapped the array and SAS6/E card onto another 1950 with the same results, which leads me to believe it's kernel related and not motherboard/cpu/memory.

Some of the call trace is attached. There are many more similar traces stored in /var/log/kern.log, each of the related to xfs.

While ctrl-alt-del will make some progress toward a shutdown, I usually have to hard reset the system.

To regain some stability I'm leaning toward moving data off XFS and onto Ext3.

---

