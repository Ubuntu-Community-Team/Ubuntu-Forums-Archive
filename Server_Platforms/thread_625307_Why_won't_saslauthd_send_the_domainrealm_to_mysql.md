---
title: "Why won't saslauthd send the domain/realm to mysql?"
date: 2007-11-27
forum: Server Platforms
---

### Post by zcox on 2007-11-27
I used this tutorial to set up a mail server on Ubuntu 7.04:

[http://howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)

Everything is great except for one thing: saslauthd won't send the domain/realm to mysql when authenticating a user for SMTP auth.  Here is my /etc/postfix/sasl/smtpd.conf:

pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: mail_admin
sql_passwd: <real password goes here>
sql_database: mail
sql_select: select password from users where email='%u@%r'

And I have also tried the following for sql_select:

sql_select: select password from users where email='%u@%d'
sql_select: select password from users where email='%u'
sql_select: select password from users where email='%s'

No matter what sql_select is, the following is all I ever get in /var/log/mysql.log:

85 Query       SELECT password FROM users WHERE email = 'username'

The rows in the users.email column are full email addresses, ie 'username@domain.com' so obviously, the authentication check is failing because i don't have sql like SELECT password FROM users WHERE email = 'username@domain.com'.

Does anyone know how to get saslauthd to include the domain in the sql query?  If it helps, here is my /etc/default/saslauthd:

START=yes
OPTIONS="-m /var/spool/postfix/var/run/saslauthd"
PIDFILE="/var/spool/postfix/var/run/${NAME}/saslauthd.pid"
MECHANISMS="pam"
MECH_OPTIONS=""
THREADS=5

Any ideas on what to look at next?

---

### Post by zcox on 2007-11-27
So this was easy: I changed the OPTIONS line in /etc/default/saslauthd to:

OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r"

And now everything works!  Also, the /etc/default/saslauthd that gets installed has an empty OPTIONS line at the very end - make sure you comment it out!

---

