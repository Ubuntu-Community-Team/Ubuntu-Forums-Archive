---
title: "Partial software RAID ?"
date: 2009-08-19
forum: The Cafe
---

### Post by Devport on 2009-08-19
I have a 1000GB harddisk and a smaller 80GB harddisk. Now I would like to create a RAID 0 over the first 80 GB of both harddisks, but still be able to use the remaining ~920GB without any RAID - which would look like :

```

1000GB HD + 80GB HD :

  80GB -> RAID 0 Both HDs
~920GB -> no RAID 1000GB HD only

```

Are existing software raid tools able to do it ?

---

### Post by Bachstelze on 2009-08-19
You can do that using the standard Linux software RAID (mdadm). In mdadm, the base volumes used to build the RAID arrays are partitions, not drives, so you can very well create a 80 GB partition on your 1 TB hard drive and use that along with the 80 GB partitions that you will have on your 80 GB drives to make a 160 GB RAID-0, for example, or a 80 GB RAID-1, or...

---

### Post by Devport on 2009-08-19
> **HymnToLife said:**
> You can do that using the standard Linux software RAID (mdadm). In mdadm, the base volumes used to build the RAID arrays are partitions, not drives, so you can very well create a 80 GB RAID partition on yout 1 TB hard drive and use that along with the 80 GB partitions that you will have on your 80 GB drives.

Oh man that would be great - so I will go ahead and learn software raid !

Thx.

---

