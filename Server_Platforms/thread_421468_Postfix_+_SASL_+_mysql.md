---
title: "Postfix + SASL + mysql"
date: 2007-04-24
forum: Server Platforms
---

### Post by abondi on 2007-04-24
I configured my web server (Ubuntu 7.04) following main instructions from [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/").

I can send and receive email.

Now I tried to apply also the SASL part of the tutorial, and here's the problem: I can't send mail, my server keeps asking the password for login to smtp server.

But, looking at mysql logs, it doesn't do any query to decide if the username/password is correct (I enabled login feature, I see other queries) and the postfix log output is: 

```
Apr 24 18:35:36 novilab postfix/smtpd[21132]: connect from unknown[192.168.0.200]
Apr 24 18:35:38 novilab postfix/smtpd[21132]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory

```

I searched for the solution, but I didn't find the right answer. Attached there is my saslfinger -s output.

Thank you!!!
Andrea

---

### Post by abondi on 2007-04-26
I tried some other options... Still don't work.

Found that the /var/log/auth.log shows this:

```
Apr 26 12:14:53 novilab postfix/smtpd[28512]: sql_select option missing
Apr 26 12:14:53 novilab postfix/smtpd[28512]: auxpropfunc error no mechanism available 
Apr 26 12:14:53 novilab postfix/smtpd[28512]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 

```

But I can't figure out why! As you see, my saslfinger -s output shows that sql_select option is displayed...
Please help, I don't want to become an open relay server! :)
```

saslfinger - postfix Cyrus sasl configuration gio apr 26 12:21:21 CEST 2007
version: 1.0.1
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.3.8
System: Ubuntu 7.04 \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7d49000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_use_tls = yes


-- listing of /usr/lib/sasl2 --
total 824
drwxr-xr-x   2 root root  4096 2007-04-26 12:10 .
drwxr-xr-x 153 root root 40960 2007-04-26 11:13 ..
-rw-r--r--   1 root root 13640 2007-01-09 11:33 libanonymous.a
-rw-r--r--   1 root root   855 2007-01-09 11:33 libanonymous.la
-rw-r--r--   1 root root 13240 2007-01-09 11:33 libanonymous.so
-rw-r--r--   1 root root 13240 2007-01-09 11:33 libanonymous.so.2
-rw-r--r--   1 root root 13240 2007-01-09 11:33 libanonymous.so.2.0.22
-rw-r--r--   1 root root 15942 2007-01-09 11:33 libcrammd5.a
-rw-r--r--   1 root root   841 2007-01-09 11:33 libcrammd5.la
-rw-r--r--   1 root root 15704 2007-01-09 11:33 libcrammd5.so
-rw-r--r--   1 root root 15704 2007-01-09 11:33 libcrammd5.so.2
-rw-r--r--   1 root root 15704 2007-01-09 11:33 libcrammd5.so.2.0.22
-rw-r--r--   1 root root 47348 2007-01-09 11:33 libdigestmd5.a
-rw-r--r--   1 root root   864 2007-01-09 11:33 libdigestmd5.la
-rw-r--r--   1 root root 43884 2007-01-09 11:33 libdigestmd5.so
-rw-r--r--   1 root root 43884 2007-01-09 11:33 libdigestmd5.so.2
-rw-r--r--   1 root root 43884 2007-01-09 11:33 libdigestmd5.so.2.0.22
-rw-r--r--   1 root root 13650 2007-01-09 11:33 liblogin.a
-rw-r--r--   1 root root   835 2007-01-09 11:33 liblogin.la
-rw-r--r--   1 root root 14036 2007-01-09 11:33 liblogin.so
-rw-r--r--   1 root root 14036 2007-01-09 11:33 liblogin.so.2
-rw-r--r--   1 root root 14036 2007-01-09 11:33 liblogin.so.2.0.22
-rw-r--r--   1 root root 30516 2007-01-09 11:33 libntlm.a
-rw-r--r--   1 root root   829 2007-01-09 11:33 libntlm.la
-rw-r--r--   1 root root 29876 2007-01-09 11:33 libntlm.so
-rw-r--r--   1 root root 29876 2007-01-09 11:33 libntlm.so.2
-rw-r--r--   1 root root 29876 2007-01-09 11:33 libntlm.so.2.0.22
-rw-r--r--   1 root root 13938 2007-01-09 11:33 libplain.a
-rw-r--r--   1 root root   835 2007-01-09 11:33 libplain.la
-rw-r--r--   1 root root 14036 2007-01-09 11:33 libplain.so
-rw-r--r--   1 root root 14036 2007-01-09 11:33 libplain.so.2
-rw-r--r--   1 root root 14036 2007-01-09 11:33 libplain.so.2.0.22
-rw-r--r--   1 root root 22150 2007-01-09 11:33 libsasldb.a
-rw-r--r--   1 root root   856 2007-01-09 11:33 libsasldb.la
-rw-r--r--   1 root root 18372 2007-01-09 11:33 libsasldb.so
-rw-r--r--   1 root root 18372 2007-01-09 11:33 libsasldb.so.2
-rw-r--r--   1 root root 18372 2007-01-09 11:33 libsasldb.so.2.0.22
-rw-r--r--   1 root root 23812 2007-01-09 11:33 libsql.a
-rw-r--r--   1 root root   964 2007-01-09 11:33 libsql.la
-rw-r--r--   1 root root 23352 2007-01-09 11:33 libsql.so
-rw-r--r--   1 root root 23352 2007-01-09 11:33 libsql.so.2
-rw-r--r--   1 root root 23352 2007-01-09 11:33 libsql.so.2.0.22
-rw-r--r--   1 root root   270 2007-04-26 12:10 smtpd.conf




-- content of /usr/lib/sasl2/smtpd.conf --
log_level: 7
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

-- content of /etc/postfix/sasl/smtpd.conf --
log_level: 7
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       n       300     1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
587       inet  n       -       n       -       -       smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes

relay     unix  -       -       -       -       -       smtp
        -o fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH LOGIN PLAIN CRAM-MD5 NTLM DIGEST-MD5
250-AUTH=LOGIN PLAIN CRAM-MD5 NTLM DIGEST-MD5


-- end of saslfinger output --
```

Thank you very much!
Andrea

---

### Post by abondi on 2007-04-26
After some other attempts, I tried to do:

```
cp /etc/sasldb2 /var/spool/postfix/etc/
chown -R postfix:postfix /var/spool/postfix
postfix reload 
```

Now the error message is changed... It's not "unable to open Berkeley db /etc/sasldb2: No such file or directory" anymore but now ubuntu says:

```
Apr 26 17:19:02 novilab postfix/smtpd[15298]: connect from unknown[192.168.0.200]
Apr 26 17:19:04 novilab postfix/smtpd[15298]: warning: unknown[192.168.0.200]: SASL LOGIN authentication failed: authentication failure
```

Still, the second part of my message hasn't changed, it still doesn't do any mysql query and can't load _sasl_plugin_load.
So, the real problem is not solved... :( 

Thank for anyone's help...
Andrea

---

### Post by deuce868 on 2007-04-26
Check out postfixadmin and their instructions for getting it going. I've used that setup for a while now and it works pretty nicely for postfix/mysql/sasl.

[http://bliki.rimuhosting.com/space/knowledgebase/linux/mail/postfixadmin+on+debian+sarge](http://bliki.rimuhosting.com/space/knowledgebase/linux/mail/postfixadmin+on+debian+sarge)

---

### Post by abondi on 2007-04-27
For anybody interested in the solution, the wrong setting is:

```
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
```

and the correct one is:

```
smtpd_sasl_path = smtpd 
```

Bye
Andrea

[www.andreabondi.it](www.andreabondi.it)

---

### Post by olpe on 2007-07-04
I found the same problem :) The solution differs a bit, but thank you for showing the way!!

---

