---
title: "Network Pooled Storage"
date: 2007-03-13
forum: Server Platforms
---

### Post by arvindkst on 2007-03-13
Hi,

Does anyone know if you can integrate multiple HDD/Partitions on different machines into one large virtual drive. Something like RAID 5 but via the network.

Like DRBD but not for mirroring but to create a virtual pooled drive without any additional hardware requirements.

Thanks in advance.

---

### Post by lamalex on 2007-03-13
that's an interesting concept. I'd be curious to find out of that's possible. What would be the advantage of this other than simplicity? If one server was offline would your entire array be down?

---

### Post by arvindkst on 2007-03-13
Agreed, I am hoping that the solution will have certain degree of redundancy. Like OCFS offers for Oracle RAC. It does the same thing but the filesystem is only oracle compatible.

---

### Post by arvindkst on 2007-03-13
Something like iSCSI ...,etc

---

### Post by Frosty Cold Drink on 2007-03-13
I think you want [Coda File System]("http://www.coda.cs.cmu.edu/") or [OpenAFS]("http://www.openafs.org/").

---

### Post by arvindkst on 2007-03-14
Will give it a try and respond.

Thank you for the help.

---

