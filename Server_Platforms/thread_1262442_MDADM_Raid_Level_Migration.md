---
title: "MDADM Raid Level Migration"
date: 2009-09-09
forum: Server Platforms
---

### Post by snuffy47 on 2009-09-09
Does MDADM allow to change a RAID 1 2 disk setup to RAID 5 3 disk setup and how hard is it?

---

### Post by tgrimley on 2009-09-09
> **snuffy47 said:**
> Does MDADM allow to change a RAID 1 2 disk setup to RAID 5 3 disk setup and how hard is it?

As far as I know, not directly.  It is possible to do without losing data (but there is risk!!! if a drive fails during some stages of this process, you're dead in the water).  For the sake of explanation, I have 3 disks sda, sdb, sdc and two arrays (md0 = raid1 from sba&sdb; md1 from all three).  Do it as follows:
1). fail and remove drive sdb from your array (md0 is now running degraded)
2). insert sdc (if you have hot swaps, other wise do this first)
3). create a 3 disk raid5 array md1 with the two disks sdb and sdc and the word "missing"
4). copy data from degraded md0 to degraded md1
5). wipe sda, remark it as a linux raid partition, and then add it to md1 which will begin rebuilding

should be all done!

I've done this several times without incident, but as I said the best practice is to HAVE A BACKUP and also to BACKUP YOUR DATA prior to this as it will be vulnerable to disk failure throughout this process.  Depending on your array size and your disk speeds, etc, should take about as long as rebuilding twice (the copy and the rebuild).

---

### Post by snuffy47 on 2009-09-10
thnx

---

