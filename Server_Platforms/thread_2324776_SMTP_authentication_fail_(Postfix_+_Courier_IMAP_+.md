---
title: "SMTP authentication fail (Postfix + Courier IMAP + MySQL)"
date: 2016-05-16
forum: Server Platforms
---

### Post by 573v4n4770 on 2016-05-16
My objective is a smtp server with authentication. My previous test failed at every configuration. As far as I can go to isolate the problem is:
```
sudo testsaslauthd -s smtp -u test@example.com -p test
size read failed
```
The logs are:
tail -f /var/log/mysql/mysql.log```

160516  9:28:39    86 Connect   mail@localhost on maildb
                   86 Init DB   maildb
                   86 Query     SELECT password FROM mailbox WHERE username = 'test@example.com'
                   86 Query     SELECT password FROM mailbox WHERE username = 'test@example.com'
```
tail -f /var/log/auth.log```

May 16 09:28:39 correio sudo: stevanatto : TTY=pts/0 ; PWD=/home/stevanatto ; USER=root ; COMMAND=/usr/sbin/testsaslauthd -s smtp -u test@example.com -p test
May 16 09:28:39 correio sudo: pam_unix(sudo:session): session opened for user root by stevanatto(uid=0)
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - option verbose is set to "1"
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - option crypt is set to "1"
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_close_db() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_sm_authenticate() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_open_db() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_open_db() returning 0.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_check_passwd() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_format_string() called
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_quick_escape() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - SELECT password FROM mailbox WHERE username = 'test@example.com'
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_check_passwd() returning 6.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_sql_log() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_sql_log() returning 0.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_converse() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_open_db() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_check_passwd() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_format_string() called
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - pam_mysql_quick_escape() called.
May 16 09:28:39 correio saslauthd[1832]: pam_mysql - SELECT password FROM mailbox WHERE username = 'test@example.com'
May 16 09:28:39 correio sudo: pam_unix(sudo:session): session closed for user root
```
From MySql server comes:```

    username     password     name     maildir     quota     local_part     domain     created     modified     active
     test@example.com     {crypt}ed6SBJHPP43Ek     test@example.com/      0      test     example.com     2016-05-16 09:14:57     2016-05-16  09:14:57      1
```
The configurations are:
sudo vi /etc/pam.d/smtp```

auth required pam_mysql.so user=mail passwd=my_pass host=127.0.0.1 db=maildb table=mailbox usercolumn=username passwdcolumn=password verbose=1 crypt=1
account sufficient pam_mysql.so user=mail passwd=my_pass host=127.0.0.1 db=maildb table=mailbox usercolumn=username passwdcolumn=password verbose=1 crypt=1
```
Did I goofed somewhere ?

---

### Post by Seb_Boffen on 2016-05-16
My smtp:

auth    required   pam_mysql.so user=mail_admin passwd=password host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1
account sufficient pam_mysql.so user=mail_admin passwd=password host=127.0.0.1 db=mail table=users usercolumn=email passwdcolumn=password crypt=1

I followed this guide: [https://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](https://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04)

---

### Post by 573v4n4770 on 2016-05-16
I had seen this tutorial before. I adapted this tutorial in my configuration files with no success.
Again, help me.

---

### Post by Seb_Boffen on 2016-05-19
This is my /etc/postfix/sasl/smtpd.conf:

pwcheck_method: saslauthd
auxprop_plugin: sql
mech_list: PLAIN LOGIN 
allow_plaintext: true
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail_admin
sql_passwd: password
sql_database: mail
sql_select: select password from users where email = [EMAIL="'%u@%r'"]'%u@%r'[/EMAIL]
saslauthd_path: /var/spool/postfix/var/run/saslauthd/mux

pam_mysql_check_passwd() returning 6 as far as I can see this is a password failiure code, please make sure using phpmyadmin to set the users email password using the encrypt setting and not the password setting.

---

### Post by 573v4n4770 on 2016-05-21
You are right. The return message "size read failed" means password wrong too. I create the user with postfixadmin and that create the password with another format. When I installed phpmyadmin and edited manually the password and it works. Problem SOLVED.
Now I will go to my next problem. Thank you.

Problem SOLVED.

---

### Post by Seb_Boffen on 2016-05-22
Welcome, At the top under thread tools you can mark the thread as solved.

---

