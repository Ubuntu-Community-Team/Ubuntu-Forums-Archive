---
title: "Tips for managing users?"
date: 2008-09-17
forum: Server Platforms
---

### Post by madhartigan on 2008-09-17
I'm wondering if anyone could summarize the typical commands used to manage users.

I'm interested in being able to list all of the users that exist on the server.  I've created some users while following some tutorials and I don't remember some of the users I created and I'd like to clean them out.

So, if anyone is able to provide a list of useful user management commands I'd really appreciate it!!

---

### Post by baudday on 2008-09-17
```
cat /etc/passwd | cut -d: -f1
```

---

### Post by alastair on 2008-09-17
> **madhartigan said:**
> I'm interested in being able to list all of the users that exist on the server.  I've created some users while following some tutorials and I don't remember some of the users I created and I'd like to clean them out.


It's a little sad maybe, but the "cat /etc/passwd" is the one I'd use to look over the list of users (assuming they're standard unix accounts) ... see your first reply.

For adding users, or modifying them, see :

adduser
moduser

and associated man pages.

Alastair

---

### Post by RealPSL on 2008-09-19
I guess we should throw in the deluser to remove them. Keep in mind that you can also do this from the GUI with System > Administration > Users and Groups.

---

