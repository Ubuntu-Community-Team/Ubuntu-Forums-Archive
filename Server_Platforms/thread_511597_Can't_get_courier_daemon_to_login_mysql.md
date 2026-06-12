---
title: "Can't get courier daemon to login mysql?"
date: 2007-07-28
forum: Server Platforms
---

### Post by ittybitty9bees on 2007-07-28
Hi.

I have recently installed and configured PostFix and Courier....Postfix is working perfectly, but courier is having problems with pop.  When it tries to login to mysql to authenticate...its login attempt for the user 'mail_admin' fails.   I tried logging into mysql manually as the mail_admin user and everything works fine, so I don't understand why courier can't log in?

this is my authmysqlrc file  which tries to login as  mail_admin@localhost   

MYSQL_SERVER localhost
MYSQL_USERNAME mail_admin
MYSQL_PASSWORD <<my password>>
MYSQL_PORT 3306
MYSQL_DATABASE mail
MYSQL_USER_TABLE users
MYSQL_CRYPT_PWFIELD password
#MYSQL_CLEAR_PWFIELD password
MYSQL_UID_FIELD 5000
MYSQL_GID_FIELD 5000
MYSQL_LOGIN_FIELD email
MYSQL_HOME_FIELD "/home/vmail"
MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')
#MYSQL_NAME_FIELD
MYSQL_QUOTA_FIELD quota


andy my logs tell me this....

Jul 28 00:08:59 dev authdaemond: failed to connect to mysql server (server=localhost, userid=mail_admin): Access denied for user 'mail_admin'@'localhost' (using password: YES)
Jul 28 00:08:59 dev courierpop3login: authentication error: Input/output error


what could be the problem??

Thanks

---

### Post by ittybitty9bees on 2007-07-28
Got it to work, whitespace at the end of the config lines....ergh

---

