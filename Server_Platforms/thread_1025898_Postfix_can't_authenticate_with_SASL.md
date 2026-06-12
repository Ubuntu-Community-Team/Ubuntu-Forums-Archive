---
title: "Postfix can't authenticate with SASL"
date: 2008-12-30
forum: Server Platforms
---

### Post by Bluebell392 on 2008-12-30
Postfix doesn't seem to work with sasl, no matter which method of authentication I try. I believe that the settings are correct, and sasl auth is enabled.

---

### Post by Drezard on 2008-12-30
Can u post configs?

---

### Post by Dr Small on 2008-12-30
Have you read my guide for securing Postfix SMTP with SASL?
[http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582)

---

### Post by Bluebell392 on 2008-12-30
Using saslfinger - client side:```
saslfinger - postfix Cyrus sasl configuration Tue Dec 30 17:05:54 PST 2008
version: 1.0.4
mode: client-side SMTP AUTH

-- basics --
Postfix: 2.5.1
System: Ubuntu 8.04.1 \n \l

-- smtp is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7d49000)

-- active SMTP AUTH and TLS parameters for smtp --
smtp_sasl_password_maps = /etc/sasldb2.db
smtp_sasl_security_options = noanonymous


-- listing of /usr/lib/sasl2 --
total 700
drwxr-xr-x  2 root root  4096 2008-12-30 11:12 .
drwxr-xr-x 47 root root 12288 2008-12-30 11:05 ..
-rw-r--r--  1 root root 13568 2008-04-09 14:50 libanonymous.a
-rw-r--r--  1 root root   862 2008-04-09 14:49 libanonymous.la
-rw-r--r--  1 root root 12984 2008-04-09 14:50 libanonymous.so
-rw-r--r--  1 root root 12984 2008-04-09 14:50 libanonymous.so.2
-rw-r--r--  1 root root 12984 2008-04-09 14:50 libanonymous.so.2.0.22
-rw-r--r--  1 root root 15834 2008-04-09 14:50 libcrammd5.a
-rw-r--r--  1 root root   848 2008-04-09 14:49 libcrammd5.la
-rw-r--r--  1 root root 15320 2008-04-09 14:50 libcrammd5.so
-rw-r--r--  1 root root 15320 2008-04-09 14:50 libcrammd5.so.2
-rw-r--r--  1 root root 15320 2008-04-09 14:50 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 46332 2008-04-09 14:50 libdigestmd5.a
-rw-r--r--  1 root root   871 2008-04-09 14:49 libdigestmd5.la
-rw-r--r--  1 root root 43020 2008-04-09 14:50 libdigestmd5.so
-rw-r--r--  1 root root 43020 2008-04-09 14:50 libdigestmd5.so.2
-rw-r--r--  1 root root 43020 2008-04-09 14:50 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 13574 2008-04-09 14:50 liblogin.a
-rw-r--r--  1 root root   842 2008-04-09 14:49 liblogin.la
-rw-r--r--  1 root root 13268 2008-04-09 14:50 liblogin.so
-rw-r--r--  1 root root 13268 2008-04-09 14:50 liblogin.so.2
-rw-r--r--  1 root root 13268 2008-04-09 14:50 liblogin.so.2.0.22
-rw-r--r--  1 root root 30016 2008-04-09 14:50 libntlm.a
-rw-r--r--  1 root root   836 2008-04-09 14:49 libntlm.la
-rw-r--r--  1 root root 29236 2008-04-09 14:50 libntlm.so
-rw-r--r--  1 root root 29236 2008-04-09 14:50 libntlm.so.2
-rw-r--r--  1 root root 29236 2008-04-09 14:50 libntlm.so.2.0.22
-rw-r--r--  1 root root 13798 2008-04-09 14:50 libplain.a
-rw-r--r--  1 root root   842 2008-04-09 14:49 libplain.la
-rw-r--r--  1 root root 13396 2008-04-09 14:50 libplain.so
-rw-r--r--  1 root root 13396 2008-04-09 14:50 libplain.so.2
-rw-r--r--  1 root root 13396 2008-04-09 14:50 libplain.so.2.0.22
-rw-r--r--  1 root root 22126 2008-04-09 14:50 libsasldb.a
-rw-r--r--  1 root root   873 2008-04-09 14:49 libsasldb.la
-rw-r--r--  1 root root 18080 2008-04-09 14:50 libsasldb.so
-rw-r--r--  1 root root 18080 2008-04-09 14:50 libsasldb.so.2
-rw-r--r--  1 root root 18080 2008-04-09 14:50 libsasldb.so.2.0.22
-rw-r--r--  1 root root   104 2008-12-30 11:50 sample.conf
-rw-r--r--  1 root root   104 2008-12-30 11:50 smtpd.conf

-- listing of /etc/postfix/sasl --
total 8
drwxr-xr-x 2 root root 4096 2008-09-09 16:55 .
drwxr-xr-x 3 root root 4096 2008-12-30 12:27 ..


-- permissions for /etc/sasldb2.db --
lrwxrwxrwx 1 root root 12 2008-12-30 12:28 /etc/sasldb2.db -> /etc/sasldb2

-- permissions for /etc/sasldb2.db.db --
lrwxrwxrwx 1 root root 12 2008-12-30 12:28 /etc/sasldb2.db.db -> /etc/sasldb2

/etc/sasldb2.db.db is up to date.

-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       n       -       -       smtpd
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
smtp      unix  -       -       -       -       -       smtp
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


-- end of saslfinger output --
```
Using saslfigner - server side:```
saslfinger - postfix Cyrus sasl configuration Tue Dec 30 17:06:51 PST 2008
version: 1.0.4
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.5.1
System: Ubuntu 8.04.1 \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7d52000)

-- active SMTP AUTH and TLS parameters for smtpd --
smtpd_sasl_auth_enable = yes


-- listing of /usr/lib/sasl2 --
total 700
drwxr-xr-x  2 root root  4096 2008-12-30 11:12 .
drwxr-xr-x 47 root root 12288 2008-12-30 11:05 ..
-rw-r--r--  1 root root 13568 2008-04-09 14:50 libanonymous.a
-rw-r--r--  1 root root   862 2008-04-09 14:49 libanonymous.la
-rw-r--r--  1 root root 12984 2008-04-09 14:50 libanonymous.so
-rw-r--r--  1 root root 12984 2008-04-09 14:50 libanonymous.so.2
-rw-r--r--  1 root root 12984 2008-04-09 14:50 libanonymous.so.2.0.22
-rw-r--r--  1 root root 15834 2008-04-09 14:50 libcrammd5.a
-rw-r--r--  1 root root   848 2008-04-09 14:49 libcrammd5.la
-rw-r--r--  1 root root 15320 2008-04-09 14:50 libcrammd5.so
-rw-r--r--  1 root root 15320 2008-04-09 14:50 libcrammd5.so.2
-rw-r--r--  1 root root 15320 2008-04-09 14:50 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 46332 2008-04-09 14:50 libdigestmd5.a
-rw-r--r--  1 root root   871 2008-04-09 14:49 libdigestmd5.la
-rw-r--r--  1 root root 43020 2008-04-09 14:50 libdigestmd5.so
-rw-r--r--  1 root root 43020 2008-04-09 14:50 libdigestmd5.so.2
-rw-r--r--  1 root root 43020 2008-04-09 14:50 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 13574 2008-04-09 14:50 liblogin.a
-rw-r--r--  1 root root   842 2008-04-09 14:49 liblogin.la
-rw-r--r--  1 root root 13268 2008-04-09 14:50 liblogin.so
-rw-r--r--  1 root root 13268 2008-04-09 14:50 liblogin.so.2
-rw-r--r--  1 root root 13268 2008-04-09 14:50 liblogin.so.2.0.22
-rw-r--r--  1 root root 30016 2008-04-09 14:50 libntlm.a
-rw-r--r--  1 root root   836 2008-04-09 14:49 libntlm.la
-rw-r--r--  1 root root 29236 2008-04-09 14:50 libntlm.so
-rw-r--r--  1 root root 29236 2008-04-09 14:50 libntlm.so.2
-rw-r--r--  1 root root 29236 2008-04-09 14:50 libntlm.so.2.0.22
-rw-r--r--  1 root root 13798 2008-04-09 14:50 libplain.a
-rw-r--r--  1 root root   842 2008-04-09 14:49 libplain.la
-rw-r--r--  1 root root 13396 2008-04-09 14:50 libplain.so
-rw-r--r--  1 root root 13396 2008-04-09 14:50 libplain.so.2
-rw-r--r--  1 root root 13396 2008-04-09 14:50 libplain.so.2.0.22
-rw-r--r--  1 root root 22126 2008-04-09 14:50 libsasldb.a
-rw-r--r--  1 root root   873 2008-04-09 14:49 libsasldb.la
-rw-r--r--  1 root root 18080 2008-04-09 14:50 libsasldb.so
-rw-r--r--  1 root root 18080 2008-04-09 14:50 libsasldb.so.2
-rw-r--r--  1 root root 18080 2008-04-09 14:50 libsasldb.so.2.0.22
-rw-r--r--  1 root root   104 2008-12-30 11:50 sample.conf
-rw-r--r--  1 root root   104 2008-12-30 11:50 smtpd.conf

-- listing of /etc/postfix/sasl --
total 8
drwxr-xr-x 2 root root 4096 2008-09-09 16:55 .
drwxr-xr-x 3 root root 4096 2008-12-30 12:27 ..




-- content of /usr/lib/sasl2/smtpd.conf --
log_level: 3
pwcheck_method: auxprop
mech_list: PLAIN LOGIN CRAM-MD5 DIGEST-MD5
auxprop_plugin: sasldb


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       n       -       -       smtpd
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
smtp      unix  -       -       -       -       -       smtp
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

-- mechanisms on localhost --
250-AUTH CRAM-MD5 DIGEST-MD5 PLAIN NTLM LOGIN


-- end of saslfinger output --
```
I have a book on setting up a working Linux email server, complete with SMTP, IMAP, POP, webmail, procmail, spamassassian, and clamav.

---

