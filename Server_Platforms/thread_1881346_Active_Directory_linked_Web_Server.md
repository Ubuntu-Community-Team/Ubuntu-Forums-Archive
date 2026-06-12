---
title: "Active Directory linked Web Server"
date: 2011-11-15
forum: Server Platforms
---

### Post by DanHorniblow on 2011-11-15
Hi, I would like to create a web server which can do the following:
[LIST]
[*]Migrate users from active directory running on Windows server 2008 with likewise or something similar
[*]Create hosting space for each user
[*]give ftp access to each users hosting space
[*]create a MySQL database for each user wich they can control via phpmyadmin
[*]When a user changes their password in AD it will update on the Ubuntu box
[/LIST]

Is all of this possible?

I have set up a few ubuntu LAMP servers before but nothing this complicated.

Any information would be appreciated.

Cheers Dan

---

### Post by SeijiSensei on 2011-11-15
Rather than updating the password on the Ubuntu box, you could [authenticate]("http://httpd.apache.org/docs/2.2/howto/auth.html") against the AD server with LDAP for the web sites with [mod_authnz_ldap]("http://httpd.apache.org/docs/2.2/mod/mod_authnz_ldap.html").

If you need to authenticate normal users as well, for instance to log into the FTP sites, you could try using [pam_ldap]("http://www.padl.com/OSS/pam_ldap.html").

MySQL is a different beast as it has its own method of authentication.  You'd need to create accounts within MySQL for each user who will have a database.

If you need to do this repeatedly or often, you're probably best off writing a bash script to create the accounts given a list of usernames.

---

