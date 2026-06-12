---
title: "Can't access MySQL after changing Host from 'localhost' to 'any'"
date: 2012-02-22
forum: Server Platforms
---

### Post by poohpeer on 2012-02-22
Hi Guys.

I tried to grant access to the DB from any IP and changed the Host for user root from localhost to any. Now I can't access the DB using mysql client.
It says: ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).

What should I do?
Thanks

---

### Post by poohpeer on 2012-02-22
Thanks for help. Used  mysqld_safe --skip-grant-tables to fix it

UPDATE mysql.user SET Host='localhost' where user='root';
FLUSH PRIVILEGES;

Now, what should I set in Host to have access from anywhere?

---

### Post by Iowan on 2012-02-22
What did you try? 
Do you really want "root" to be able to login from anywhere? I usually SSH into the box and login from there.
(I vaguely remember something about * as the host).

---

### Post by elico on 2012-02-23
this "%"

---

### Post by Iowan on 2012-02-23
> **elico said:**
> this "%"...or maybe it was "%"... ;)

---

