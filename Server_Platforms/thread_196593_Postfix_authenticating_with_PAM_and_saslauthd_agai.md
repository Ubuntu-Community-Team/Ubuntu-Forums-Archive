---
title: "Postfix authenticating with PAM and saslauthd against a MySQL database"
date: 2006-06-14
forum: Server Platforms
---

### Post by Randomskk on 2006-06-14
Hey
I host a server where I deal with email for several domains and several users. I recently swapped to Dapper, and have follow this How-To to get virtual domains etc working with Postfix:
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

The MySQL database works, the web mail works (for sending and receiving), and delivering mail with IMAP or POP3 works.
However, I cannot send email via SMTP at all, and the primary error seems to be this in the logs:
[QUOTE=auth.log]
postfix/smtpd[...]: sql_select option missing
postfix/smtpd[...]: auxpropfunc error no mechanism available
postfix/smtpd[...]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql[/QUOTE]
[QUOTE=syslog]
postfix/smtpd[...]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied[/QUOTE]

Postfix is running chrooted to /var/spool/postfix, and there is a mux socket in /var/spool/postfix/var/run/saslauthd/mux:
[QUOTE=ls /var/spool/postfix]
drwxr--r-- 3 root    root     4.0K Jun  7 21:17 var[/QUOTE]
[QUOTE=ls /var/spool/postfix/var]
drwxr--r-- 3 root sasl 4.0K Jun  7 21:17 run[/QUOTE]
[QUOTE=ls /var/spool/postfix/var/run]
drwx--x--- 2 root sasl 100 Jun 13 23:03 saslauthd[/QUOTE]
[QUOTE=ls /var/spool/postfix/var/run/saslauthd]
srwxrwxrwx 1 root root 0 Jun 13 23:03 mux
-rw------- 1 root root 0 Jun 13 23:03 mux.accept
-rw------- 1 root root 5 Jun 13 23:03 saslauthd.pid[/QUOTE]

The 'postfix' user, by the way, is also in the sasl group.

[QUOTE=/etc/postfix/sasl/smtpd.conf]
pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true[/QUOTE]

[QUOTE=/etc/postfix/mysql-virtual_domains.cf]
user = xxx
password = xxx
dbname = mail
table = domains
select_field = 'virtual'
where_field = domain
hosts = 127.0.0.1[/QUOTE]

[QUOTE=/etc/postfix/mysql-virtual_email2email.cf]
user = xxx
password = xxx
dbname = mail
table = users
select_field = email
where_field = email
hosts = 127.0.0.1[/QUOTE]

[QUOTE=/etc/postfix/mysql-virtual_forwardings.cf]
user = xxx
password = xxx
dbname = mail
table = forwardings
select_field = destination
where_field = source
hosts = 127.0.0.1[/QUOTE]

[QUOTE=/etc/postfix/mysql-virtual_mailbox_limit_maps.cf]
user = xxx
password = xxx
dbname = mail
table = users
select_field = quota
where_field = email
hosts = 127.0.0.1[/QUOTE]

[QUOTE=/etc/postfix/mysql-virtual_mailboxes.cf]
user = xxx
password = xxx
dbname = mail
table = users
select_field = CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')
where_field = email
hosts = 127.0.0.1[/QUOTE]

[QUOTE=/etc/postfix/mysql-virtual_transports.cf]
user = xxx
password = xxx
dbname = mail
table = transport
select_field = transport
where_field = domain
hosts = 127.0.0.1[/QUOTE]

The error seems to be SQL related, so those are the six SQL files that Postfix uses.
I've googled for the error and found other people with it, but the common solution there was to add "postfix" to the "sasl" group, which didn't help much.
Running postfix with -v doesn't help much either.
If there's any other info or config files you need, feel free to ask.

I guess my question, then, is what is causing the error and how can I fix it?

Thanks for any help

---

### Post by Randomskk on 2006-06-15
bump.. :(

---

### Post by Randomskk on 2006-06-15
Update: taking postfix out of chroot and it all works.
However this isn't really a solution I'm pleased with, although I guess it shows where to start looking for a real solution.



EDIT: ok, fixed, I needed to:
# chmod a+x /var/spool/postfix/var
# chmod a+x /var/spool/postfix/var/run
# chgrp root /var/spool/postfix/var/run

and now it works perfectly, chrooted! 
woo :D

---

### Post by robbybartlett on 2006-12-21
In Edgy, I do not have var underneath /var/spool/postfix

Did you have to create those directories as well as chmod them, or did they already exist?

Cheers

---

