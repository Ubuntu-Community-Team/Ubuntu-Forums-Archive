---
title: "copy /etc/passwd file from another server?"
date: 2011-04-11
forum: Server Platforms
---

### Post by ipfreak on 2011-04-11
hi all:

with failed the upgrading from 8.04 to 10.04 (the system totally crashed). i decide to reinstall the whole thing. could i copy /etc/passwd from another server to the newly installed server?

---

### Post by SeijiSensei on 2011-04-11
> **ipfreak said:**
> could i copy /etc/passwd from another server to the newly installed server?

Yes, but you also need /etc/group and /etc/shadow as well.  Make sure they have these ownerships and permissions after you've copied them over:

```

-rw-r--r-- 1 root root   1244 2011-03-26 11:51 /etc/group
-rw-r--r-- 1 root root   2528 2011-03-26 11:51 /etc/passwd
-rw-r----- 1 root shadow 1546 2011-03-26 11:51 /etc/shadow

```

---

