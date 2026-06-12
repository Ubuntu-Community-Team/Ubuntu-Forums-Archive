---
title: "Granting Access Privileges"
date: 2009-03-04
forum: Server Platforms
---

### Post by iambinaya@gmail.com on 2009-03-04
I am running Ubuntu 8.10 as a server in a LAN with 20 Mac clients.There is a shared folder called PRODUCTION which two users can access.My problem is that, when user 1 creates a folder in PRODUCTION, user 2 only gets read access.How can i resolve this issue so that whenever a user 1 creates a folder in PRODUCTION, user 2 gets both read and write access?Your help is highly appreciated.

---

### Post by lykwydchykyn on 2009-03-04
What service are you running to share the folder?  SAMBA? NFS?  NetATalk?

---

### Post by iambinaya@gmail.com on 2009-03-04
it is Samba

---

### Post by lykwydchykyn on 2009-03-04
Assuming both users are members of the "users" group, you can add this to the share definition for PRODUCTION:
```

force group = users
force create mode = 775
force directory mode = 775

```

That will make sure that all created files are assigned to the "users" group, and all created files and folders will have read/write access for the group.  

You can, of course, configure the security differently for the "others" part if you want to.  775 will give read access to any user on the system, that may not be what you want.

---

### Post by iambinaya@gmail.com on 2009-03-04
That perfectly works....Thanks Heaps.

---

