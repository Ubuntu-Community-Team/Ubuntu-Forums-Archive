---
title: "SMTPD SASL Auth Issues"
date: 2012-08-25
forum: Server Platforms
---

### Post by Johnny-Gear on 2012-08-25
Hi All,

I have done a lot of searching and can't seem to figure this out.

I  have setup a mail server; components are as follows: Ubuntu 12.04  Server, Courier, MySQL, Amavisd-new, SpamAssassin, ClamAV, SASL, TLS,  Postgrey and Roundcube

I can login to Courier and Roundcube.
I can send mail(including to external recipients).
I can recieve mail.

As far as I can tell everything is working, except for SMTPD authentication.

saslfinger -s output below:

```

saslfinger - postfix Cyrus sasl configuration Sun Aug 26 04:24:18 EST 2012
version: 1.0.4
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.9.3
System: Ubuntu 12.04.1 LTS \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/x86_64-linux-gnu/libsasl2.so.2 (0x00007fbf13fcc000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s


-- listing of /usr/lib/sasl2 --
total 20
drwxr-xr-x  2 root root  4096 Jul 22 15:06 .
drwxr-xr-x 65 root root 12288 Aug 25 21:07 ..
-rw-r--r--  1 root root     1 May  4 14:15 berkeley_db.txt

-- listing of /etc/postfix/sasl --
total 12
drwxr-xr-x 2 root root 4096 Aug 26 04:21 .
drwxr-xr-x 3 root root 4096 Aug 26 01:38 ..
-rw-r--r-- 1 root root  308 Aug 26 04:21 smtpd.conf




-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet   n       -       -       -       -       smtpd
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




amavis      unix    -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20

127.0.0.1:10025 inet    n       -       -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
        -o local_header_rewrite_clients=

 -o content_filter=
        -o receive_override_options=no_header_body_checks

submission inet n       -       n       -       -       smtpd
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous

-- mechanisms on localhost --
250-AUTH PLAIN LOGIN CRAM-MD5 DIGEST-MD5


-- end of saslfinger output --



```Any help would be appreciated as I have been at this for hours, and can't seem to work it out.

EDIT:

Here are some relevant logs:
```

Aug 26 16:42:08 host postfix/smtpd[26752]: connect from localhost[127.0.0.1]
Aug 26 16:42:08 host postfix/smtpd[26752]: Anonymous TLS connection established from localhost[127.0.0.1]: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
Aug 26 16:42:08 host postfix/smtpd[26752]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 554 5.7.1 <localhost[127.0.0.1]>: Client host rejected: Access denied; from=<user@domain.com> to=<root@domain.com> proto=ESMTP helo=<host.domain.com>

Aug 26 16:42:08 host postfix/smtpd[26752]: sql auxprop plugin using mysql engine

```Regards,

JG

---

### Post by Johnny-Gear on 2012-08-26
slightly updated master.cf config; can be seen below i new saslfinger output:

```

saslfinger - postfix Cyrus sasl configuration Mon Aug 27 00:00:27 EST 2012
version: 1.0.4
mode: server-side SMTP AUTH

-- basics --
Postfix: 2.9.3
System: Ubuntu 12.04.1 LTS \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/x86_64-linux-gnu/libsasl2.so.2 (0x00007fbcc393f000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s


-- listing of /usr/lib/sasl2 --
total 20
drwxr-xr-x  2 root root  4096 Jul 22 15:06 .
drwxr-xr-x 65 root root 12288 Aug 25 21:07 ..
-rw-r--r--  1 root root     1 May  4 14:15 berkeley_db.txt

-- listing of /etc/postfix/sasl --
total 12
drwxr-xr-x 2 root root 4096 Aug 26 04:21 .
drwxr-xr-x 3 root root 4096 Aug 26 23:27 ..
-rw-r--r-- 1 root root  308 Aug 26 04:21 smtpd.conf




-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1


-- active services in /etc/postfix/master.cf --
#                       (yes)   (yes)                   (yes)           (never)         (100)
smtp            inet    n                       -               -               -               -               smtpd
pickup          fifo    n                       -               -               60              1               pickup
        -o content_filter=
                -o receive_override_options=no_header_body_checks
cleanup         unix    n                       -               -               -               0               cleanup
qmgr            fifo    n                       -               n               300             1               qmgr
tlsmgr          unix    -                       -               -               1000?           1               tlsmgr
rewrite         unix    -                       -               -               -               -               trivial-rewrite
bounce          unix    -                       -               -               -               0               bounce
defer           unix    -                       -               -               -               0               bounce
trace           unix    -                       -               -               -               0               bounce
verify          unix    -                       -               -               -               1               verify
flush           unix    n                       -               -               1000?           0               flush
proxymap        unix    -                       -               n               -               -               proxymap
proxywrite      unix    -                       -               n               -               1               proxymap
smtp            unix    -                       -               -               -               -               smtp
relay           unix    -                       -               -               -               -               smtp
showq           unix    n                       -               -               -               -               showq
error           unix    -                       -               -               -               -               error
retry           unix    -                       -               -               -               -               error
discard         unix    -                       -               -               -               -               discard
local           unix    -                       n               n               -               -               local
virtual         unix    -                       n               n               -               -               virtual
lmtp            unix    -                       -               -               -               -               lmtp
anvil           unix    -                       -               -               -               1               anvil
scache          unix    -                       -               -               -               1               scache
maildrop        unix    -                       n               n               -               -               pipe
        flags=DRhu user=mail argv=/usr/bin/maildrop -d ${recipient}
uucp            unix    -                       n               n               -               -               pipe
        flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail          unix    -                       n               n               -               -               pipe
        flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp           unix    -                       n               n               -               -               pipe
        flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -                       n               n               -               2               pipe
        flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman         unix    -                       n               n               -               -               pipe
        flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py ${nexthop} ${user}
amavis          unix    -                       -               -               -               2               smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20
127.0.0.1:10025 inet    n                       -               -               -               -               smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
submission      inet    n                       -               n               -               -               smtpd
        -o smtpd_sasl_auth_enable=yes
        -o smtpd_tls_auth_only=yes
        -o smtpd_tls_security_level=encrypt
        -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
        -o smtpd_sasl_security_options=noanonymous,noplaintext
        -o smtpd_sasl_tls_security_options=noanonymous
        -o milter_macro_daemon_name=ORIGINATING
smtps           inet    n                       -               -               -               -               smtpd
        -o smtpd_tls_wrappermode=yes
        -o smtpd_sasl_auth_enable=yes
        -o smtpd_tls_auth_only=yes
        -o smtpd_client_restrictions=permit_sasl_authenticated,reject
        -o smtpd_sasl_security_options=noanonymous,noplaintext
        -o smtpd_sasl_tls_security_options=noanonymous
        -o milter_macro_daemon_name=ORIGINATING

-- mechanisms on localhost --
250-AUTH PLAIN LOGIN CRAM-MD5 DIGEST-MD5


-- end of saslfinger output --

```

Still have same issues though.. Don't know why it tells me no mechanism available when there clearly are..

JG

---

### Post by Indian Summer on 2012-11-03
> **Johnny-Gear said:**
> 
-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

I think maybe auxprop_plugin should be "sql" rather than "mysql"?

---

