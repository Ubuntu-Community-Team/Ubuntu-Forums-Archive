---
title: "What tool will show the relationships between a physical disk and logical volumes?"
date: 2009-02-21
forum: Server Platforms
---

### Post by MountainX on 2009-02-21
I can't tell which logical volumes are associated with which physical disks. Is there a utility that will help me find out? Thanks.

---

### Post by x33a on 2009-02-21
use gparted.

system -> administration -> partition editor.

or, alt+f2, gparted.

---

### Post by MountainX on 2009-02-22
> **x33a said:**
> use gparted.

system -> administration -> partition editor.

or, alt+f2, gparted.

I have that open. It doesn't tell me what I need to know as far as I can see.

For example, I need to know which disk (i.e., sda through sdg as they are currently enumerated) the following volume belongs to:
```
/dev/mapper/sdf1_crypt
```
(and it is **_not_** sdf, as it was when I installed the system!)
I can't go by size because all (or most of) my physical disks are the exact same model.

---

### Post by x33a on 2009-02-22
try 

1. df -h
2. lshw.
3. fdisk -l.

actually, i don't have a logical partition, but i think gparted should have shown the mount points.

---

### Post by MountainX on 2009-02-22
> **x33a said:**
> try 

1. df -h
2. lshw.
3. fdisk -l.

actually, i don't have a logical partition, but i think gparted should have shown the mount points.

Thank you. I have been using gparted, df and fdisk. None of them give the needed info. But I will try lshw next. It looks like it might show the info I need (logical name mapped to physical ID).

I'm trying to match the items in each column. As you can see, I have many of them matched now, but I cannot tell which device hosts /dev/mapper/sdf1_crypt. It could be sda, sdb or sdd (all of which are identical drives).

```

/dev/sda	
/dev/sdb	
/dev/sdc	/dev/sdc1
/dev/sdd	
/dev/sde	/dev/mapper/sdc1_crypt
/dev/sdf	/dev/mapper/sda2_crypt
/dev/sdf	/dev/sdf1
/dev/sdg	/dev/mapper/sdb_VolGrp-lvTmp
/dev/sdg	/dev/mapper/sdb_VolGrp-lvVar
unknown	        /dev/mapper/sdf1_crypt

```

---

