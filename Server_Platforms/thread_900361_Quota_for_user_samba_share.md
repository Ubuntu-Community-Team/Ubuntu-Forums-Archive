---
title: "Quota for user samba share"
date: 2008-08-25
forum: Server Platforms
---

### Post by shizakapayou on 2008-08-25
I have a samba/LDAP domain controller running Ubuntu Server 8.04 64-bit.  The install has one large /home partition, which is around 2 TB in size.  On this partition, each user has a shared space at /home/ldaphome/username.  This space gets mapped as a network drive in Windows, and is only accessible by the user.

What I'd like is to place a quota on these user folders, so that one user can't monopolize the whole partition.  However, I don't want to use a user quota for the partition, because other shares exist on this partition as well for group projects.  I'd basically like to limit the user space to 30 GB or so.

What's my best course for this?  I've seen quota, but it appears to only affect the entire partition.  I've also seen a bit on smbcquota, but I'm coming up empty on that one.

---

### Post by cheikhou on 2012-01-05
hello ,
Have you solved your problem  ? and how you did it !!! i'm real interested.

---

### Post by lisati on 2012-01-05
Thread closed: necromancy.

Please start your own thread.

---

