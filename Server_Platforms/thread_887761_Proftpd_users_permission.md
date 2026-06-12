---
title: "Proftpd users permission"
date: 2008-08-12
forum: Server Platforms
---

### Post by guidorossi on 2008-08-12
Hi!

I'm running a LAMP server in Ubuntu 8.04 with Apache2 PHP, MySQL and Proftpd

I'm managing the proftpd users in MySQL for an easyest adds and removes.
The problem is that the users I add in MySQL to have access to the FTP server can not upload files to a directory without 777 permission, and the users can not change the chmod to 777 via FTP, so I've got to change permissions via SSH.

How can I give permission to do that via FTP to the users I add via MySQL?

Thanks

---

### Post by davidshq on 2008-08-13
You don't want to set your permissions to 777. You want to create a group that these users fall into and give that directory and its sub-directories group permissions that your users reside in. 777 will be a security nightmare.

---

### Post by sndnichols on 2008-08-13
Have you seen this? [http://www.howtoforge.com/proftpd_mysql_virtual_hosting]("http://www.howtoforge.com/proftpd_mysql_virtual_hosting")

---

