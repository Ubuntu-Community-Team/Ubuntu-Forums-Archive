---
title: "samba permissions question"
date: 2009-12-15
forum: Security
---

### Post by keevill on 2009-12-15
I have configured a  basic simple samba file server with  users and just 2 groups.
Problem is when a new file or folder is created by either linux or win clients, only the creator of it can have full read/write access.
I can run sudo chmod -R 755 filename to restore R/W permissions for all users but this is every time a new file is created.
What can I do to resolve this pls?

---

### Post by Sarmacid on 2009-12-15
If the file is readable and writable by people on the same group, then you should create another group and add all users. Another thing you could do is set up a cron job to change permissions on files in a certain folder.

---

### Post by keevill on 2009-12-15
> **Sarmacid said:**
> If the file is readable and writable by people on the same group, then you should create another group and add all users. Another thing you could do is set up a cron job to change permissions on files in a certain folder.

It's only RW by the creator - Read only by all others

---

