---
title: "Can I apply permission to windows files the same way i can in linux?"
date: 2007-08-09
forum: Windows
---

### Post by mykalreborn on 2007-08-09
i see linux has a very nice way of adding permission to files and folders. i was wondering if there is any way of doing that with windows. does it have anything to do with the format of the partition (ntfs for instance), or can it be done with some kind of software?
thanks!

---

### Post by rich.bradshaw on 2007-08-09
NTFS does support some permissions, but not enough to do anything useful with...

Basically Windows is a lot behind when it comes to security, and this is one example of that.

---

### Post by ddrichardson on 2007-08-09
As the above poster says not to the filesystem itself. You can achieve a fair degree of protection with well configured policies though.

---

### Post by mykalreborn on 2007-08-09
but is there some kind of administering software? but not something like you see in some internet cafes, which get rid of all the gui and just show you a desktop with 5 applications. and definetly not deepfreeze. :P

---

### Post by ddrichardson on 2007-08-09
poledit - its installed with server 2003 but i think is on the addons folder with xp.

---

### Post by blastus on 2007-08-09
[quote=mykalreborn]Can I apply permission to windows files the same way i can in linux?[/quote]

With NTFS you can. Just right-click on any directory/file.

[quote=rich.bradshaw]NTFS does support some permissions, but not enough to do anything useful with...

Basically Windows is a lot behind when it comes to security, and this is one example of that.[/quote]

Wrong. NTFS supports more fine grained permissions than ext3. If Windows lags behind Linux in security it is NOT because of NTFS.

---

