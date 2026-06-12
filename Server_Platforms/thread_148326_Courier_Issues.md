---
title: "Courier Issues"
date: 2006-03-21
forum: Server Platforms
---

### Post by Blairboy on 2006-03-21
Ok, finally fixed a bunch of stuff, but there's only one problem left to fix: I can send mail, but can't retrieve it from the inbox. When I try to log in through squirrelmail, I get these errors. Is something wrong with courier or what?


Mar 21 18:20:25 localhost imaplogin: Connection, ip=[::ffff:127.0.0.1]
Mar 21 18:20:25 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Mar 21 18:20:25 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=user
Mar 21 18:20:25 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=password
Mar 21 18:20:25 localhost imaplogin: authdaemon: starting client module
Mar 21 18:20:25 localhost imaplogin: authdaemon: REJECT
Mar 21 18:20:30 localhost imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Mar 21 18:20:30 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGOUT
Mar 21 18:20:30 localhost imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]

Also, from mail.err:
Mar 21 14:07:35 localhost authdaemond.mysql: authmysql: MYSQL_CRYPT_PWFIELD and MYSQL_CLEAR_PWFIELD not set in /etc/courier/authmysqlrc.
Mar 21 13:50:08 localhost authdaemond.mysql: Bad line in /etc/courier/authdaemonrc: MYSQL_SERVER localhost

And here's my authmysqlrc:
MYSQL_SERVER		localhost
MYSQL_USERNAME		user
MYSQL_PASSWORD		password
#MYSQL_CRYPT_PWFIELD	crypt
MYSQL_CLEAR_PWFIELD	clear

---

### Post by Blairboy on 2006-03-21
By the way, didn't mean to cross post, but I saw this forum after I already posted it in Desktop Support.  Sorry.

---

