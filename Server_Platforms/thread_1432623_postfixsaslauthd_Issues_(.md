---
title: "postfix/saslauthd Issues ("
date: 2010-03-18
forum: Server Platforms
---

### Post by pcrumm on 2010-03-18
Hello all,

I am trying to configure postfix to auth using saslauthd but thus far am unsuccessful. Attempting to authenticate returns an error 535 -- /var/log/mail.log outputs the following:
```
Mar 18 04:21:07 demosthenes postfix/smtpd[27633]: warning: c-69-181-194-81.hsd1.ca.comcast.net[69.181.194.81]: SASL login authentication failed: authentication failure
Mar 18 04:21:07 demosthenes postfix/smtpd[27633]: > c-69-181-194-81.hsd1.ca.comcast.net[69.181.194.81]: 535 5.7.8 Error: authentication failed: authentication failure

```Prior to this (verbose logging is enabled) successful negotiation is shown -- both the username and the password are correct.

I've included saslfinger (server-side) below. Let me know if you need any more information.
```
saslfinger -s
saslfinger - postfix Cyrus sasl configuration Thu Mar 18 04:32:48 UTC 2010
version: 1.0.4
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.5.1
System: Ubuntu 8.04.4 LTS \n \l

-- smtpd is linked to --
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00007f3f23f22000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes


-- listing of /usr/lib64/sasl2 --
total 924
drwxr-xr-x  2 root root  4096 Feb 28 22:39 .
drwxr-xr-x 58 root root 20480 Feb 28 22:39 ..
-rw-r--r--  1 root root 19196 Jun 23  2009 libanonymous.a
-rw-r--r--  1 root root   862 Jun 23  2009 libanonymous.la
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2.0.22
-rw-r--r--  1 root root 22186 Jun 23  2009 libcrammd5.a
-rw-r--r--  1 root root   848 Jun 23  2009 libcrammd5.la
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 60688 Jun 23  2009 libdigestmd5.a
-rw-r--r--  1 root root   871 Jun 23  2009 libdigestmd5.la
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 19366 Jun 23  2009 liblogin.a
-rw-r--r--  1 root root   842 Jun 23  2009 liblogin.la
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2.0.22
-rw-r--r--  1 root root 38980 Jun 23  2009 libntlm.a
-rw-r--r--  1 root root   836 Jun 23  2009 libntlm.la
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2.0.22
-rw-r--r--  1 root root 19406 Jun 23  2009 libplain.a
-rw-r--r--  1 root root   842 Jun 23  2009 libplain.la
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2.0.22
-rw-r--r--  1 root root 29764 Jun 23  2009 libsasldb.a
-rw-r--r--  1 root root   873 Jun 23  2009 libsasldb.la
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2.0.22
-rw-r--r--  1 root root 33576 Jun 23  2009 libsql.a
-rw-r--r--  1 root root   971 Jun 23  2009 libsql.la
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2.0.22

-- listing of /usr/lib/sasl2 --
total 924
drwxr-xr-x  2 root root  4096 Feb 28 22:39 .
drwxr-xr-x 58 root root 20480 Feb 28 22:39 ..
-rw-r--r--  1 root root 19196 Jun 23  2009 libanonymous.a
-rw-r--r--  1 root root   862 Jun 23  2009 libanonymous.la
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2.0.22
-rw-r--r--  1 root root 22186 Jun 23  2009 libcrammd5.a
-rw-r--r--  1 root root   848 Jun 23  2009 libcrammd5.la
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 60688 Jun 23  2009 libdigestmd5.a
-rw-r--r--  1 root root   871 Jun 23  2009 libdigestmd5.la
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 19366 Jun 23  2009 liblogin.a
-rw-r--r--  1 root root   842 Jun 23  2009 liblogin.la
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2.0.22
-rw-r--r--  1 root root 38980 Jun 23  2009 libntlm.a
-rw-r--r--  1 root root   836 Jun 23  2009 libntlm.la
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2.0.22
-rw-r--r--  1 root root 19406 Jun 23  2009 libplain.a
-rw-r--r--  1 root root   842 Jun 23  2009 libplain.la
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2.0.22
-rw-r--r--  1 root root 29764 Jun 23  2009 libsasldb.a
-rw-r--r--  1 root root   873 Jun 23  2009 libsasldb.la
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2.0.22
-rw-r--r--  1 root root 33576 Jun 23  2009 libsql.a
-rw-r--r--  1 root root   971 Jun 23  2009 libsql.la
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2.0.22

-- listing of /etc/postfix/sasl --
total 12
drwxr-xr-x 2 root root 4096 Mar 18 03:52 .
drwxr-xr-x 3 root root 4096 Mar 18 03:48 ..
-rw-r--r-- 1 root root  235 Mar 18 04:21 smtpd.conf




-- content of /etc/postfix/sasl/smtpd.conf --
check_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: mail
sql_select: select password from users where email = '%u'

-- content of /etc/postfix/sasl/smtpd.conf --
check_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: mail
sql_select: select password from users where email = '%u'


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
45678	inet 	n	-	n	-	-	smtpd -v	
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN


-- end of saslfinger output --

```
Additionally, my user table looks something like this:
```
mysql> DESC mail.users;
+----------+-------------+------+-----+----------+-------+
| Field    | Type        | Null | Key | Default  | Extra |
+----------+-------------+------+-----+----------+-------+
| email    | varchar(80) | NO   | PRI | NULL     |       | 
| password | varchar(20) | NO   |     | NULL     |       | 
| quota    | int(10)     | YES  |     | 10485760 |       | 
+----------+-------------+------+-----+----------+-------+
3 rows in set (0.00 sec)

```
Email looking something like 'test@domain.com' and password looking something like 'password' (I am not encrypting it, it's plaintext).

For what it's worth, I had been trying to follow [this tutorial](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04) but evidentially something went awry that I can't find.

Thanks for any and all assistance.

---

### Post by pcrumm on 2010-03-18
Giving this a bump.

---

### Post by pcrumm on 2010-03-19
I've done some toying and now testsaslauthd works fine, however, postfix still doesn't seem to want to. I've attached another saslfinger below. Thoughts?

```
saslfinger -s
saslfinger - postfix Cyrus sasl configuration Fri Mar 19 06:21:41 UTC 2010
version: 1.0.4
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.5.1
System: Ubuntu 8.04.4 LTS \n \l

-- smtpd is linked to --
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0x00007f935dd5e000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = smtpd
smtpd_sasl_type = cyrus
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes


-- listing of /usr/lib64/sasl2 --
ls: cannot access /usr/lib64/sasl2/smtpd.conf: No such file or directory
total 924
drwxr-xr-x  2 root root  4096 Mar 19 05:38 .
drwxr-xr-x 58 root root 20480 Feb 28 22:39 ..
-rw-r--r--  1 root root 19196 Jun 23  2009 libanonymous.a
-rw-r--r--  1 root root   862 Jun 23  2009 libanonymous.la
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2.0.22
-rw-r--r--  1 root root 22186 Jun 23  2009 libcrammd5.a
-rw-r--r--  1 root root   848 Jun 23  2009 libcrammd5.la
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 60688 Jun 23  2009 libdigestmd5.a
-rw-r--r--  1 root root   871 Jun 23  2009 libdigestmd5.la
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 19366 Jun 23  2009 liblogin.a
-rw-r--r--  1 root root   842 Jun 23  2009 liblogin.la
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2.0.22
-rw-r--r--  1 root root 38980 Jun 23  2009 libntlm.a
-rw-r--r--  1 root root   836 Jun 23  2009 libntlm.la
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2.0.22
-rw-r--r--  1 root root 19406 Jun 23  2009 libplain.a
-rw-r--r--  1 root root   842 Jun 23  2009 libplain.la
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2.0.22
-rw-r--r--  1 root root 29764 Jun 23  2009 libsasldb.a
-rw-r--r--  1 root root   873 Jun 23  2009 libsasldb.la
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2.0.22
-rw-r--r--  1 root root 33576 Jun 23  2009 libsql.a
-rw-r--r--  1 root root   971 Jun 23  2009 libsql.la
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2.0.22
l?????????  ? ?    ?        ?            ? smtpd.conf

-- listing of /usr/lib/sasl2 --
ls: cannot access /usr/lib/sasl2/smtpd.conf: No such file or directory
total 924
drwxr-xr-x  2 root root  4096 Mar 19 05:38 .
drwxr-xr-x 58 root root 20480 Feb 28 22:39 ..
-rw-r--r--  1 root root 19196 Jun 23  2009 libanonymous.a
-rw-r--r--  1 root root   862 Jun 23  2009 libanonymous.la
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2
-rw-r--r--  1 root root 15888 Jun 23  2009 libanonymous.so.2.0.22
-rw-r--r--  1 root root 22186 Jun 23  2009 libcrammd5.a
-rw-r--r--  1 root root   848 Jun 23  2009 libcrammd5.la
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2
-rw-r--r--  1 root root 19184 Jun 23  2009 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 60688 Jun 23  2009 libdigestmd5.a
-rw-r--r--  1 root root   871 Jun 23  2009 libdigestmd5.la
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2
-rw-r--r--  1 root root 48448 Jun 23  2009 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 19366 Jun 23  2009 liblogin.a
-rw-r--r--  1 root root   842 Jun 23  2009 liblogin.la
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2
-rw-r--r--  1 root root 16432 Jun 23  2009 liblogin.so.2.0.22
-rw-r--r--  1 root root 38980 Jun 23  2009 libntlm.a
-rw-r--r--  1 root root   836 Jun 23  2009 libntlm.la
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2
-rw-r--r--  1 root root 32368 Jun 23  2009 libntlm.so.2.0.22
-rw-r--r--  1 root root 19406 Jun 23  2009 libplain.a
-rw-r--r--  1 root root   842 Jun 23  2009 libplain.la
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2
-rw-r--r--  1 root root 16336 Jun 23  2009 libplain.so.2.0.22
-rw-r--r--  1 root root 29764 Jun 23  2009 libsasldb.a
-rw-r--r--  1 root root   873 Jun 23  2009 libsasldb.la
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2
-rw-r--r--  1 root root 21528 Jun 23  2009 libsasldb.so.2.0.22
-rw-r--r--  1 root root 33576 Jun 23  2009 libsql.a
-rw-r--r--  1 root root   971 Jun 23  2009 libsql.la
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2
-rw-r--r--  1 root root 27904 Jun 23  2009 libsql.so.2.0.22
l?????????  ? ?    ?        ?            ? smtpd.conf

-- listing of /etc/postfix/sasl --
total 12
drwxrwxrwx 2 root root 4096 Mar 18 03:52 .
drwxr-xr-x 3 root root 4096 Mar 18 03:48 ..
-rw-rw-rw- 1 root root  246 Mar 19 05:34 smtpd.conf




-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: auxprop
mech_list: PLAIN LOGIN
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1, localhost
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: mail
sql_select: select password from users where email = '%u'

-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: auxprop
mech_list: PLAIN LOGIN
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1, localhost
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: mail
sql_select: select password from users where email = '%u'


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
45678	inet 	n	-	-	-	-	smtpd -v	
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN


-- end of saslfinger output --

```

---

