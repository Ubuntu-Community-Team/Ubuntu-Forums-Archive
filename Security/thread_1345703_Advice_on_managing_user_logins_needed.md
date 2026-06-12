---
title: "Advice on managing user logins needed"
date: 2009-12-04
forum: Security
---

### Post by tapas_mishra on 2009-12-04
I want to disable the user logging in on a system say for example every day after 17:00 hours no one should be allowed to login on the system authentication method is local no LDAP or NIS exists how can this be done.

---

### Post by lloyd_b on 2009-12-04
> **tapas_mishra said:**
> I want to disable the user logging in on a system say for example every day after 17:00 hours no one should be allowed to login on the system authentication method is local no LDAP or NIS exists how can this be done.

The simplest way to to have a cron job create/delete a file named "/etc/nologin".  If this file exists, any user trying to log in will be shown the contents of the file, and the login fails.

"man 5 nologin" in a terminal window for more information.

Lloyd B.

---

