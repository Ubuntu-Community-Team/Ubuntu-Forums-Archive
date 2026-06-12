---
title: "resetting the owners of /var"
date: 2007-03-29
forum: Server Platforms
---

### Post by Bultot on 2007-03-29
Ok, stupid action.. I tried to chown /var/www -R and I did chown at /var -R ](*,)

Is there a way to reset the /var owners recursive?
 I've installed Ubuntu server 6.10 LAMP

---

### Post by GoBieN on 2007-03-29
Oops, double post.

---

### Post by GoBieN on 2007-03-29
I don't believe there is a rollback option. You could just let do a chown -R root /var again (and then again your chown for /var/www). But you will probably have to check if everything is still working. For example /var/db/mysql should be owned by the mysql user. You could just chmod 777 the whole /var dir, but thats not good admin behavior, and comes with huge security risks.

---

