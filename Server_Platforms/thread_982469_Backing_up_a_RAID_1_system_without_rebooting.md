---
title: "Backing up a RAID 1 system without rebooting"
date: 2008-11-14
forum: Server Platforms
---

### Post by nashibuntu on 2008-11-14
My server has four physical disks which are in mirrored pairs using RAID 1. Each of the pairs are partitioned.

I'd like to perform a complete backup of the whole system, partition by partition, using, for example, partimage. If I understand correctly, a partition needs to be unmounted in order to be backed-up, which would normally require shutting down the system and booting partimage from a cd to do the backup.

I don't want to have to shut down the server in order to do the backup. So the question is, is it possible to stop the mirroring of one of the disks, backup the unmounted partitions on the un-mirrored disk, and then start mirroring again - all without rebooting?

Thanks.

---

