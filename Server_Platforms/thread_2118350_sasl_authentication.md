---
title: "sasl authentication"
date: 2013-02-20
forum: Server Platforms
---

### Post by Elnison on 2013-02-20
everytime I login in telnet localhost 587 I get this error 

```
root@mail:~# telnet localhost 587
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.hmd-c.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-mail.hmd-c.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
auth plain 23432frfergd= (password hide)
535 5.7.8 Error: authentication failed: another step is needed in authentication


```

help my guys! thanks!

---

### Post by Elnison on 2013-02-20
saslfinger -s
```
-- basics --
Postfix: 2.9.3
System: Ubuntu 12.04.2 LTS \n \l

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/i386-linux-gnu/libsasl2.so.2 (0xb7633000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes


-- listing of /usr/lib/sasl2 --
total 20
drwxr-xr-x  2 root root  4096 Jan 14 11:28 .
drwxr-xr-x 69 root root 12288 Feb 20 14:49 ..
-rw-r--r--  1 root root     1 May  4  2012 berkeley_db.txt

-- listing of /etc/postfix/sasl --
total 12
drwxr-xr-x 2 root root 4096 Feb 21 11:42 .
drwxr-xr-x 3 root root 4096 Feb 21 11:34 ..
-rw-r--r-- 1 root root  261 Feb 21 11:42 smtpd.conf




-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=no
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous
  -o smtpd_sasl_tls_security_options=noanonymous
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=no
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous
  -o smtpd_sasl_tls_security_options=noanonymous
pickup    fifo  n       -       -       60      1       pickup
 -o content_filter=
        -o receive_override_options=no_header_body_checks
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

-- mechanisms on localhost --
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN


-- end of saslfinger output --

```


postconf -n
```
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = $myhostname, localhost, localhost.localdomain, localhost.$myhostname
myhostname = mail.hmd-c.com
mynetworks = 127.0.0.0/8 [::1]/128
mynetworks_style = host
myorigin = hmd-c.com
readme_directory = no
recipient_delimiter = +
relayhost = [smtpdsl4.pldtdsl.net]:587
smtp_generic_maps = hash:/etc/postfix/generic
smtp_helo_timeout = 60s
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org,reject_rbl_client blackholes.easynet.nl,reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = permit_mynetworks,check_relay_domains,permit_sasl_authenticated,reject_non_fqdn_recipient, reject_unknown_recipient_domain,reject_unauth_destination, check_policy_service inet:127.0.0.1:10023,permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender,reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000

```

---

