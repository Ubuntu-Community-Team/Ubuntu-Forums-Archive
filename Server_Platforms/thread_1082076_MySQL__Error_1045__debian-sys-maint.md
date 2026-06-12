---
title: "MySQL | Error 1045 | debian-sys-maint"
date: 2009-02-27
forum: Server Platforms
---

### Post by ethos84 on 2009-02-27
Hi guys

I'm getting this error in syslog whenever I reboot the server. (It's one of the last things to happen once it's been restarted).

Feb 27 13:39:19 intranet /etc/mysql/debian-start[4204]: /usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'debian-sys-maint'@'localhost' (using password: YES) when trying to connect

The website is running fine from what I can see. Is this of concern?

Thanks

---

### Post by ethos84 on 2009-03-02
The plot thickens, from what I can see I don't even have a debian-sys-maint account. Even though I installed ubuntu LAMP.

Any ideas guys? :)

---

### Post by NoReflex on 2009-03-02
If your debian-sys-maint account got modifyed you probably won't be able to update mysql using apt-get - since that account is used when performing maintenance by the system. Anyway it's very simple to recreate the user's privileges.
Just login to mysql (using your root account) and type :
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY 'password';

You should be able to find the passoword for debian-sys-maint in : /etc/mysql/debian.cnf
If you want to you can define more granular access rights for this account.

Best wishes,
NoReflex

---

### Post by ethos84 on 2009-03-02
Thanks for the reply NoReflex.

From reading another thread I ran:

GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;

Which seems to have worked (in terms of the account is there and I can auth to mysql with it).

I will reboot when I can to see if I get the error.

Thanks

---

