---
title: "Convert vmware image back into a physial partition"
date: 2008-02-07
forum: Virtualisation
---

### Post by insanek on 2008-02-07
Hi,

Is it possible to convert a vmware image back into a physical partition that can be booted from?

I realise you can convert a physical partition into a vmware image, but is it possible to reverse this?

-thanks

---

### Post by bdamon on 2008-02-07
You might try using Partimage to make a copy of the partition. Systemrescuecd would have all the tools you need to backup the partition, mbr and partition table so you could restore it back to a physical disk.  

Ben

---

