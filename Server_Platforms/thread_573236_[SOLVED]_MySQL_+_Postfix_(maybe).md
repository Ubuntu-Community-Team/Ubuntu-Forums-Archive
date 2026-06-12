---
title: "[SOLVED] MySQL + Postfix (maybe)"
date: 2007-10-11
forum: Server Platforms
---

### Post by KevinM1 on 2007-10-11
I just installed the new MySQL server update, and noticed that:

1. Root's account was remade without a password.

2. I have root as the user for my machine's host name.

To clarify -- my machine's host name is **mail**.  It currently has **root** as **mail's** user within the mysql database's user table.

The first part I can change, but I'm concerned about the second.  I'm not sure if it just popped up because of the update, or if it has something to do with Postfix (I have an almost default Postfix setup, so I never explicitly told it to use the database).

I'd like to remove it, but I'm afraid it'll mess things up.  Any ideas?

---

### Post by KevinM1 on 2007-10-11
> **KevinM1 said:**
> I just installed the new MySQL server update, and noticed that:

1. Root's account was remade without a password.

2. I have root as the user for my machine's host name.

To clarify -- my machine's host name is **mail**.  It currently has **root** as **mail's** user within the mysql database's user table.

The first part I can change, but I'm concerned about the second.  I'm not sure if it just popped up because of the update, or if it has something to do with Postfix (I have an almost default Postfix setup, so I never explicitly told it to use the database).

I'd like to remove it, but I'm afraid it'll mess things up.  Any ideas?

I removed the root user via phpMyAdmin, but I can still log into the database as root.  I thought it was a cookie issue, but I can still get in as root even after clearing my cookies.  Is there any terminal-based mysqladmin voodoo I can do to permanently remove root?  I already have another password protected root user with a different user name, so I certainly don't want the generic, password*less*, root user hanging around.

EDIT: Picture of my current users (my super secret root username blacked out): [http://www.nightslyr.com/mysqlusers.png](http://www.nightslyr.com/mysqlusers.png)
Picture showing that I can still login as root, despite not having a generic root user: [http://www.nightslyr.com/mysqlroot.png](http://www.nightslyr.com/mysqlroot.png)

---

### Post by KevinM1 on 2007-10-11
That was odd.  I still had a root@localhost account that wasn't viewable in phpMyAdmin.  It's gone now, though.

---

