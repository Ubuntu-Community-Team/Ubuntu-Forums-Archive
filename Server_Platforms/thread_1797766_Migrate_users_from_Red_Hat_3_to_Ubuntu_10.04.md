---
title: "Migrate users from Red Hat 3 to Ubuntu 10.04"
date: 2011-07-05
forum: Server Platforms
---

### Post by frist44 on 2011-07-05
Hi,

I'm trying to migrate users from an old Red Hat 3 box. The box is mainly used for FTP and as a result, has a crap load of user/passwords that aren't well documented.

I followed this article:

[http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/)

This appended the user data into the new machine

/etc/passwd
/etc/group
/etc/shadow
/etc/gshadow

One thing I did notice is that the Red hat user IDs start at 500, and Ubuntu starts at 1000. I tested one user by modifying this value, but it still didn't work.

When I try to login as one of these users to the FTP server, I get:

530 Login incorrect.

The process sits at "verfying password" for longer than I expect and then comes back and says the above.

Any thoughts?

---

### Post by frist44 on 2011-07-05
I figured it out. Turns the shell on the Redhat box was /sbin/nologin and that doesn't exist on the new server. So once I gave it the right shell, it worked fine.

---

