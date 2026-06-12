---
title: "Combining folders"
date: 2007-10-02
forum: Server Platforms
---

### Post by KevinIsntHere on 2007-10-02
I am trying to set up a file server using multiple hard drives and computers.  I have access to many computers and many small hard drives.  I want to use the hard drive space on all of the computers to create one large shared directory.

My original plan was to put three/four hard drives in each computer, with Ubuntu, set up a RAID 0 or RAID 5 configuration on each computer.  These computers would all have a shared folder that would be mounted on a server computer.  This server computer would create a share that contains all of the files on the computers with the RAID drives.  I basically want to create a RAID 0 configuration using shared folders off many computers.  

Unfortunately, I don't know how to do this.  I would appreciate any tips that you may have.

Thanks in advance.

---

### Post by kidders on 2007-10-03
Hi there,

One option would be to use ATA over Ethernet to do exactly what you suggested ... RAID 0 over RAID 5 ... although it might be worth giving some thought to failure scenarios. Spreading one filesystem over multiple hard disks on several different computers *drastically* increases the risk of data loss.

Assuming for a moment that you have disk space to burn, consider...[LIST]
[*]Four PCs, each with four approximately identical disk partitions, each on its own physical disk.
[*]Each PC could construct a RAID 5 array. Three of them would expose theirs to the fourth over AoE.
[*]The fourth PC would build a new RAID 5 array out of the three remote arrays and the local one.
[*]The result could tolerate the loss of an entire PC, or any individual hard disk (but not both), without losing any data.
[*]The "fourth" PC could expose the top-level array to your network over NFS, Samba or similar.[/LIST]Some variation on the theme -- depending on the level of reliability required -- would do the trick, imo. AoE is typically used on an industrial scale to build ultra-reliable multi-exabyte SANs, but it works perfectly well on a smaller scale.

---

