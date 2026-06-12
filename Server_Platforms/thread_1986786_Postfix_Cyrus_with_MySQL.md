---
title: "Postfix Cyrus with MySQL"
date: 2012-05-25
forum: Server Platforms
---

### Post by game1 on 2012-05-25
Hi,
I have Postfix on my Ubuntu 12.04. Authentication is provided by Cyrus SASL. I try to authenticate users via Mysql database.

I allways get this error in /var/log/mail.log:
**SASL PLAIN authentication failed: no mechanism available**

This is my smtpd.conf configuration:
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: PLAIN CRAM-MD5 DIGEST-MD5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: root
sql_passwd: fT8Eqfdsf5
sql_database: postfix
sql_select: SELECT password FROM users WHERE user = "abc"

Thank you for help!

---

### Post by game1 on 2012-05-27
I tried authentification via PAM and it works. Postfix also communicates with the MySQL database witout problems. Just Cyrus SASL doesnt want to work. ;(

---

