---
title: "File encryption on an already encrypted /home partition"
date: 2017-01-03
forum: Security
---

### Post by CosmicFlux on 2017-01-03
Hi,

Quick query:

Is there any added benefit to having added encryption on an individual file or directory on an already encrypted partition.

My thnking is when you login, the data on the partition is decrypted BUT the file or directory will need further decryption. So, if your partition is compromised you will have an added layer of protection? 

Overkill, I know, but does this work?

Regards,

CF

---

### Post by Fire_Chief on 2017-01-03
Sure, this works just fine. As you noted, the partition encryption does not protect individual files from viewing (for example, if a folder is shared on the network). However the file level encryption would guard against viewing the file within the share (per file decryption key or password required).

---

### Post by CosmicFlux on 2017-01-03
Great! Thanks for the clarification on this.

CF

---

