---
title: "Partition recommendations for an Ubuntu server running VMware Server?"
date: 2011-03-28
forum: Server Platforms
---

### Post by GOSSSAMER on 2011-03-28
Hi All,
I presently have an Ubuntu server 64-bit running VMware Server 2.0 in a test lab. 
The server was created using the default partitioning method during the installation. So I have what I think is just one huge 300GB partition along with what I hear is a uselessly large swap partition. 
I keep reading that theres an advantage to creating dedicated partitions, especially for the the VM datastore. 
If the advantages are true then I would like to re-partition the drive. 
 
What do you guys recommend? 
 
What partitions should I define and how big should the be?

---

### Post by GOSSSAMER on 2011-03-29
What do you guys think of this config?

/ - 30 G
/boot - 300 Megs - this just for kernel, <-- is this big enough?
/swap - 16 G <-- I keep reading on how this may be to big. 2GB being the max
/var - the rest of the drive for VMs, logs and database stuff

---

### Post by GOSSSAMER on 2011-05-06
anyone?

---

### Post by samosamo on 2011-05-06
I always just use defaults BUT... I would create an additional one just for the VM datastore (RAID10 recommended).

---

