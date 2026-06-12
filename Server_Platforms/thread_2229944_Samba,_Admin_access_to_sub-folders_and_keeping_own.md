---
title: "Samba, Admin access to sub-folders and keeping ownership"
date: 2014-06-16
forum: Server Platforms
---

### Post by mraray on 2014-06-16
Hi Everyone,

I have a situation where a network share has a number of subfolders. Each subfolder has different users and groups. example:

Share ->
folder1 (user1/group1)
folder2 (user2/group2)
folder3 (user3/group3)
...

Is there a way that an admin user (different to the users listed above) can have access to the share, and the subfolders with full write/read permissions... and... for writes by the admin user to match the sub-folder permissions. for example if the admin user wrote or created a file in folder1 then the file would be owned by the owner of folder1 (ie, user1/group1 in  this case).

Any advice would be greatly appreciated

Many thanks in advance.

---

### Post by bab1 on 2014-06-16
> **mraray said:**
> Hi Everyone,

I have a situation where a network share has a number of subfolders. Each subfolder has different users and groups. example:

Share ->
folder1 (user1/group1)
folder2 (user2/group2)
folder3 (user3/group3)
...

Is there a way that an admin user (different to the users listed above) can have access to the share, and the subfolders with full write/read permissions... and... for writes by the admin user to match the sub-folder permissions. for example if the admin user wrote or created a file in folder1 then the file would be owned by the owner of folder1 (ie, user1/group1 in  this case).

Any advice would be greatly appreciated

Many thanks in advance.
Although there is a *force user * and a *force group * parameter available in Samba , they are used on a per share basis.  You also should not create shares inside of other shares (nested).

---

