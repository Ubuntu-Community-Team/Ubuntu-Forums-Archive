---
title: "Setting privilages for mysql users"
date: 2008-12-10
forum: Server Platforms
---

### Post by ShaolinF on 2008-12-10
Hi Guys

I have 3 users on my mysql server with full privilages. The problem is if I log in with any one of these accounts I am able to see ALL tables regardless of who made them. Is there any way I can change this so that users can only see the tables they have created ?

---

### Post by Coreigh on 2008-12-10
I am not a MySQL expert but I believe it is something like this:
```

deny all privileges on somedb.tablename to 'someuser' identified by 'passwrd';

```

I usually use a GUI like phpmyadmin, somehow I think I understand what I'm doing better if I can see it.

The mysql website has pretty good documentation, you can probably find a specific answer there with some reading.

---

### Post by Iowan on 2008-12-11
No expert here either, but a user with GRANT privileges can GRANT or REVOKE privileges to SHOW, SELECT... to name a couple.  I can't say the HELP command has provided me with much information.  Privileges can be limited to databases, tables, or (maybe) fields.

---

