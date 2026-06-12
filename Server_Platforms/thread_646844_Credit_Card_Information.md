---
title: "Credit Card Information"
date: 2007-12-21
forum: Server Platforms
---

### Post by reuben005 on 2007-12-21
See i've used some 3rd party softwares(like download managers etc) on my windows XP and realised that most of them do not encrypt passwords in the registry... and anyone who knows where to look can find the password or credit card information in the registry... 

the concern i have is that since ubuntu is open source, the code will probably be available easily. so anyone who knows where to look will be able to see what the encryption process is, and they'll be able to see credit card infor etc from the registry. 

please let me know whether my concern is genuine and if so, how can we improve on it.

---

### Post by mellowd on 2007-12-21
There is no registry in linux

---

### Post by p_quarles on 2007-12-21
> **reuben005 said:**
> See i've used some 3rd party softwares(like download managers etc) on my windows XP and realised that most of them do not encrypt passwords in the registry... and anyone who knows where to look can find the password or credit card information in the registry... 

the concern i have is that since ubuntu is open source, the code will probably be available easily. so anyone who knows where to look will be able to see what the encryption process is, and they'll be able to see credit card infor etc from the registry. 

please let me know whether my concern is genuine and if so, how can we improve on it.
All of the popular encryption algorithms are widely available to anyone who wants to study them. That doesn't mean they can be broken into without a cluster of supercomputers. 

Generally speaking, the openness of GPL and other open-source code makes it *more* secure rather than less. See the sticky note on this topic (in this forum) for more info.

---

### Post by koenn on 2007-12-21
> There is no registry in linux
... and sane programmers would encrypt passwords if they need to be stored anywhere. With open source programs, you can actually check that they do. 

most (if not all) encryption algoritms and their implementation are commonly known. They don't rely on being secret for being secure : they rely on (secret) keys.
Because the encryption algoritms and their implementation are commonly known, they can be checked, tested, and improved upon.

---

