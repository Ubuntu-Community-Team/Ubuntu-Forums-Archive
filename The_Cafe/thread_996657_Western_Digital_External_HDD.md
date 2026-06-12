---
title: "Western Digital External HDD ?"
date: 2008-11-29
forum: The Cafe
---

### Post by armageddon08 on 2008-11-29
I've purchased a WD External/Portable HDD. It is a 160 GB HDD, but shows up only 149 gigs. Is that normal ?

---

### Post by cariboo on 2008-11-29
Yes it is.

Jim

---

### Post by hessiess on 2008-11-29
The filesystem which tells the OS where files are located tackes up some space on the disk, and some manufactures use 1GB = 1000 MB, when it is actually 1GB = 1024 MB.

---

### Post by Newuser1111 on 2008-11-29
> **armageddon08 said:**
> Is that normal ?Yes.

---

### Post by armageddon08 on 2008-11-29
> **cariboo907 said:**
> Yes it is.

Jim

> **hessiess said:**
> The filesystem which tells the OS where files are located tackes up some space on the disk, and some manufactures use 1GB = 1000 MB, when it is actually 1GB = 1024 MB.

> **Newuser1111 said:**
> Yes.

But....should it be taking >10GB of space. Is there a hidden partition or something ?

---

### Post by qazwsx on 2008-11-29
Sounds right
Just calculate 
160/(1.024)^3=149.012

---

### Post by manicman on 2008-11-29
Yes it's Normal. Hard Drives Manufactures us the SI standard for GB which is 1GB = 1000MB or 10^9 Bytes. Where as most OS's Tend to go with 1GB = 1024MB or 2^30 Bytes. You can distinguish between the two by using Gibibytes where 1Gib = 1024Mib.

Your Hard Disk is correct as
160GB = ~149GiB

Technically Hard Drive Manufactures are more in the right the then the OS's as there compiling with SI standards.

---

### Post by mips on 2008-11-29
> **armageddon08 said:**
> But....should it be taking >10GB of space. Is there a hidden partition or something ?

No, that is the size of a 160GB HD. See explanation above.

I have a internal 160GB WD and it's size is 149GB.

---

### Post by handy on 2008-11-29
File systems always shrink the useful size to varying degrees as well.  

Varying due to their differing block sizes?

---

