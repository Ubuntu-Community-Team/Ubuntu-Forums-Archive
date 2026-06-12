---
title: "Odd MySQL user problems"
date: 2009-12-13
forum: Server Platforms
---

### Post by tr33m4n on 2009-12-13
Hello there,

I've recently rebuilt my server due to an upgrade going wrong. I backed up all my sites etc and successfully restored them. However for some odd reason all the sites a struggling to connect to the MySQL database which is running on the same server. I believe its a user permission problem, but I do not know how to resolve it.

I have several cms's using the same database, username and password for MySQL and all return the same 'Access denied for user 'doyle'@'localhost' (using password: YES).' error. I have tried setting up a new cms using the root account and all seems fine, the cms installs. However when trying to use another user, which i have given the required abilities on the database to create, edit etc, it returns the error :S

Can anyone help?

Many thanks
Dan

---

### Post by tr33m4n on 2009-12-14
Ah, not to worry, it wasn't mysql, I hadn't re-enable the rewrite mod on apache... d'oh!

---

