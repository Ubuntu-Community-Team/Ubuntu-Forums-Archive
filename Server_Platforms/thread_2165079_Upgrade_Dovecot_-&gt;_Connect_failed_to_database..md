---
title: "Upgrade Dovecot -&gt; Connect failed to database."
date: 2013-08-03
forum: Server Platforms
---

### Post by vincent4 on 2013-08-03
Hello,

I just did an upgrade of Ubuntu 11.04 to 11.10 and now I have problems with the mail server I would to like fix before upgrading to Ubuntu 12.04.

The version of Dovecot has been upgraded to 2.0 and I was using 1.0 on Ubuntu 11.04. Now I have this error:

```
tail -f /var/log/mail.log
Aug  3 03:04:27 ve dovecot: auth: Error: mysql(127.0.0.1): Connect failed to database (email): Can't connect to MySQL server on '127.0.0.1' (4) - waiting for 125 seconds before retry

```
I have also warning messages in /var/log/mail.log:
```
Aug  3 03:10:47 ve dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:896: add auth_ prefix to all settings inside auth {} and remove the auth {} section completely
Aug  3 03:10:47 ve dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:934: passdb pam {} has been replaced by passdb { driver=pam }
Aug  3 03:10:47 ve dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1010: passdb sql {} has been replaced by passdb { driver=sql }
Aug  3 03:10:47 ve dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1047: userdb passwd {} has been replaced by userdb { driver=passwd }
Aug  3 03:10:47 ve dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1071: userdb static {} has been replaced by userdb { driver=static }
Aug  3 03:10:47 ve dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:1109: auth_user has been replaced by service auth { user }

```

I can connect to the database:
```
root@ve:/etc/dovecot# mysql -u email_admin -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 559
Server version: 5.1.69-0ubuntu0.11.10.1 (Ubuntu)


Copyright (c) 2000, 2013, Oracle and/or its affiliates. All rights reserved.


Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.


Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.


mysql>
```


I can connect, so I don't understand why Dovecot can't connect. Any idea ?

Thank you.

---

### Post by vincent4 on 2013-08-04
Resolved. The lo interface was down !
```

ifconfig lo up

```fixed it

---

