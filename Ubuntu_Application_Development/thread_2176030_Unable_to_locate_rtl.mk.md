---
title: "Unable to locate rtl.mk"
date: 2013-09-22
forum: Ubuntu Application Development
---

### Post by mavik1 on 2013-09-22
hi,

I have installed RTL on ubuntu 12.04. I am trying to test weather RTLinux installed properly or not.
i patched patch-3.10.4-rt1.patch.bz2 with linux-3.10.4.tar.xz is this patch is correct one?
locate rtl.mk
displats empty
How to locate rtl.mk file? 

thanx

---

### Post by steeldriver on 2013-09-22
I don't know anything about RTL, but the database used by the 'locate' command generally is only updated once a day - if you want to see more recently added files with 'locate', you will need to update the database manually

```

sudo updatedb

locate 'rtl.mk'

```

---

### Post by mavik1 on 2013-09-24
Updated DB, still unable locate rtl.mk
Where from i can get the file?

Thanx

---

