---
title: "MYSQL/PHP password problems"
date: 2008-05-15
forum: Server Platforms
---

### Post by psynophile on 2008-05-15
I've recently set up a test server for myself running Ubuntu 8 and for the life of me, I can't figure this one out.

I have phpmyadmin and phpbb3 running. I can log in to mysql using mysql -p on the command line. phpmyadmin absolutely will not log in. If I clear the root password and re-set it. It will allow me to log in. After an hour or so, same thing happens.

PHPBB3 is running with a different mysql user and has permissions for the phpbb3 database that it needs. It's mysql account seems to be fine (the pages and posts display fine), but if I try to log in as any user, I get denied.

Any help at all would really, really be appreciated.

---

### Post by psynophile on 2008-05-16
Sorry to bump, but I really need to get this going. The only thing that I can think of that hasn't been proven yet is that the root mysql user has the same password as the system's root password. Is there any know issues about this?

---

### Post by hyper_ch on 2008-05-17
I think you PMA configuration is not ok...

and by default mysql will be installed without root password.

---

