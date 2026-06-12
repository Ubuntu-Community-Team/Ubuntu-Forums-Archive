---
title: "chmod for member of owning group"
date: 2008-02-11
forum: Server Platforms
---

### Post by AaronLS on 2008-02-11
If a directory shows GroupA as the owning group, and when I run the command "groups" and it shows that I am a member of that group, then should I be able to chmod that directory?

When I try to chmod the directory from 775 to 777, it says:
chmod: WARNING: can't change cache

Where "cache" is the name of the directory.

Thanks.

---

### Post by k_grdn on 2008-02-11
Hi,

Only the owner/creator or root can change the permissions, su chown the folder then you will be able to change permissions, alas you are the owner.

Regards,

k_grdn

---

