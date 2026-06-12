---
title: "Pool/Cluster/Span disks across multiple servers?"
date: 2009-01-06
forum: Server Platforms
---

### Post by bkann on 2009-01-06
Hi -

I'm wondering if anyone knows of a way to cluster disks across multiple machines and make them appear (eg., to a Windows client) as a single volume.  This would be somewhat similar to what Windows can do with DFS, but I don't need the replication capabilities.

For example, say I have server1 and server2, each with both a 20GB and a 320GB drive.  Ideally, I'd like to install the systems on the 20GB drives.  Can I then set them up such that there will be a 640GB volume that Windows clients can map to (I recognize I'm presupposing Samba)?

Apologies for what I'm sure is a very freshman question.  Many thanks in advance for your suggestions!

---

### Post by Vegan on 2009-01-06
You can mount disks with the NFS and that is the most common approach. Large corporate clusters are made that way.

---

