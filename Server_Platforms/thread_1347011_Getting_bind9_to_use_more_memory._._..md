---
title: "Getting bind9 to use more memory. . ."
date: 2009-12-05
forum: Server Platforms
---

### Post by pi.boy.travis on 2009-12-05
Hi!

I have a bind9 DNS caching server setup on my network.  However, it won't use more than 17mb of memory. . .  I think it is because cache items are expiring too quickly.  How can I change this behavior?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-12-05
I did it with the datasize option.  Problem solved.

---

### Post by pi.boy.travis on 2009-12-05
Nope.  The memory is stuck at 17mb again.  What else can I do?

---

