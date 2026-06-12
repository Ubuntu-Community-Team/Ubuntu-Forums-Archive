---
title: "Ubuntu Server 14.04 - ProFTPd + sql virtual users"
date: 2014-07-04
forum: Server Platforms
---

### Post by dawid.baraniak on 2014-07-04
Hello

I configured an sql auth method for proftpd - exactly as it was described here: [http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-incl-quota-on-ubuntu-12.10](http://www.howtoforge.com/virtual-hosting-with-proftpd-and-mysql-incl-quota-on-ubuntu-12.10).

Using this method everything works really nice, but I can't create virtual "root" user...

I've already disallowed local unix users to log in by uncommenting and modifying this line: ```
AuthOrder mod_sql.c
``` into /etc/proftpd/proftpd.conf file...

What else should I do, if I want use virtual "root" account?


Sorry for my english :/

Thanks in advance
Dawid

---

