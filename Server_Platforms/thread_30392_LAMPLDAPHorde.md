---
title: "LAMP/LDAP/Horde"
date: 2005-04-28
forum: Server Platforms
---

### Post by philipacamaniac on 2005-04-28
Are there any good tutorials out there on setting up a LAMP server, with Horde and OpenLDAP? I'm trying out test scenarios to see how feasible a migration from Windows 2000 would be.

I'm familiar with Linux, but not so much familiar with Linux server configuration. I have installed every package I think I'll need, including Webmin, but I just can't find any good tutorials or wiki pages. I'll also be trying to setup Samba as a Domain Controller, and also jabberd as an IM server, both using OpenLDAP as a central directory.


Basically, I need Linux to have all the functionality of my Windows 2000 server setup. I know this totally possible, but how do I do it? Is there a good migration book, maybe?

---

### Post by blueplazma on 2005-04-29
There's about a million LAMP tutorials if you search google, but I believe the Ubuntu packages are apache2, libapache2-php4, and mysql-server.  It could be libapache2-php also, I'm not positive.  Anyhow, OpenLDAP isn't too bad to set up, I just did it myself actually.  LDAP Systems Administration by Gerald Carter is an excellent book.  There's a lot of good tutorials out there that explain how to integrate one system or another with LDAP, but I found that the book really ties it all together.  If you can't pick that up, I will tell you that it's quite easy to set up LDAP for user authentication through courier and postfix.  I found the book helpful in conjunction with the postfix documentation.

---

