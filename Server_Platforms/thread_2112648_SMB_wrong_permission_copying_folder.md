---
title: "SMB wrong permission copying folder"
date: 2013-02-05
forum: Server Platforms
---

### Post by Cruell on 2013-02-05
Hi at all

I need help.
I installed a new Ubuntu server with SMB packets.
I configured it with some users and some group.
I configured some folder for different acces depending on groups.
I configured SMB to create folders only with 0770 permission with parameters create mask = 0770 and directory mask = 0770

When I create e new folder, all have right permission.
When I copy folder from different folders or from windows client, permission is 0750 and folder is not accessible from other group users.
It happen only when i copy folders.
I need that SMB create/copy folders only with 0770 permissions.

Can someone help me?

If it's need, I can post my smb.conf and my testparm results.

--
PS: sorry for my poor english language

---

### Post by Cruell on 2013-02-05
It was che UMASK parameter.
I changed it in file /etc/login.defs from 022 to 002.
That's all

---

