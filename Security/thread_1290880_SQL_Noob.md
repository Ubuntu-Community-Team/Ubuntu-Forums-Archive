---
title: "SQL Noob"
date: 2009-10-14
forum: Security
---

### Post by Zero++ on 2009-10-14
I just installed a SQL server on my ubuntu machine. I am just using it to play around and learn SQL. What do I need to do to secure my server so i don't get hacked while learning?

---

### Post by cariboo on 2009-10-14
It depends on which database you installed, I know in a default install of MySQL it only listens on 127.0.0.1

---

### Post by Zero++ on 2009-10-14
I installed MYSQL. do i just need to close that in the firewall?

---

### Post by cariboo on 2009-10-14
Mysql listens on port 3306, if you have that port open in your firewall, close it. If you are connecting to the rest of the world through a router, unless you have specifically forwarded the port, you have nothing to worry about.

---

### Post by The Cog on 2009-10-14
> **cariboo907 said:**
> Mysql listens on port 3306, if you have that port open in your firewall, close it. If you are connecting to the rest of the world through a router, unless you have specifically forwarded the port, you have nothing to worry about.

By default, MySQL only listens on localhost, with cannot be connected to from outside the computer, so no firewall is needed.

You may find it easier just to install the **sqlite manager** add-on into firefox. This allows you to create single-file databases and use SQL to edit and query them. Much simpler than driving a multi-user database if all you want to do is practice SQL.

---

