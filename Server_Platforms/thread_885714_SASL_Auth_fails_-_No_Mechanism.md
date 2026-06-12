---
title: "SASL Auth fails - No Mechanism"
date: 2008-08-10
forum: Server Platforms
---

### Post by kvn290 on 2008-08-10
I'm hoping someone can help.  After about two weeks of research and trial with ONLY errors, I'm stumped.

I have a mail server utilizing Postfix + Courier IMAP + Cyrus SASL + MySQL.

All functionality works perfectly, with the exception of my relayhost.  I can login via Evolution or Squirrelmail, and I can receive email.  The problem: when I send from a client the email gets to the server, gets processed ok (using auxprop in smtpd.conf), but fails on the relay to my relayhost (using relayhost because my IP is dynamic).

I receive the following error:

Aug 10 11:34:37 xxxxxx postfix/smtp[7218]: warning: SASL authentication failure: No worthy mechs found
Aug 10 11:57:13 xxxxxx postfix/smtp[7330]: 427274E44D: to=<XXXXXXXXXX@yahoo.com>, relay=XXXXXXXXXX.com[xxx.xxx.xxx.xxx]:25, delay=41129, delays=41128/0.04/1.2/0, dsn=4.7.0, status=deferred (SASL authentication failed; cannot authenticate to server XXXXXXXXX.com[xxx.xxx.xxx.xxx]: no mechanism available)

I have installed/reinstalled libsasl2, libsasl2-2, libsasl-modules-sql.

SYSTEM SETUP BELOW:

saslfinger -c
saslfinger - postfix Cyrus sasl configuration Sun Aug 10 11:47:45 EDT 2008
version: 1.0.4
mode: client-side SMTP AUTH

-- basics --
Postfix: 2.5.1
System: Ubuntu 8.04.1 \n \l

-- smtp is linked to --
	libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7dc4000)

-- active SMTP AUTH and TLS parameters for smtp --
relayhost = [XXXXXXXXXX.com]
smtp_sasl_auth_enable = yes
smtp_sasl_mechanism_filter = plain, login
smtp_sasl_password_maps = hash:/etc/postfix/relay_passwd
smtp_tls_note_starttls_offer = no
smtp_use_tls = no


-- listing of /usr/lib/sasl2 --
total 800
drwxr-xr-x  2 root root  4096 2008-08-10 11:30 .
drwxr-xr-x 57 root root 16384 2008-08-09 12:00 ..
-rw-r--r--  1 root root 13568 2008-04-09 17:50 libanonymous.a
-rw-r--r--  1 root root   862 2008-04-09 17:49 libanonymous.la
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so.2
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so.2.0.22
-rw-r--r--  1 root root 15834 2008-04-09 17:50 libcrammd5.a
-rw-r--r--  1 root root   848 2008-04-09 17:49 libcrammd5.la
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so.2
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 46332 2008-04-09 17:50 libdigestmd5.a
-rw-r--r--  1 root root   871 2008-04-09 17:49 libdigestmd5.la
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so.2
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 13574 2008-04-09 17:50 liblogin.a
-rw-r--r--  1 root root   842 2008-04-09 17:49 liblogin.la
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so.2
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so.2.0.22
-rw-r--r--  1 root root 30016 2008-04-09 17:50 libntlm.a
-rw-r--r--  1 root root   836 2008-04-09 17:49 libntlm.la
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so.2
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so.2.0.22
-rw-r--r--  1 root root 13798 2008-04-09 17:50 libplain.a
-rw-r--r--  1 root root   842 2008-04-09 17:49 libplain.la
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so.2
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so.2.0.22
-rw-r--r--  1 root root 22126 2008-04-09 17:50 libsasldb.a
-rw-r--r--  1 root root   873 2008-04-09 17:49 libsasldb.la
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so.2
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so.2.0.22
-rw-r--r--  1 root root 23696 2008-04-09 17:50 libsql.a
-rw-r--r--  1 root root   971 2008-04-09 17:49 libsql.la
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so.2
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so.2.0.22
-rw-r--r--  1 root root   260 2008-08-06 21:25 smtpd.conf

-- listing of /usr/local/lib/sasl2 --
total 800
drwxr-xr-x  2 root root  4096 2008-08-10 11:30 .
drwxr-xr-x 57 root root 16384 2008-08-09 12:00 ..
-rw-r--r--  1 root root 13568 2008-04-09 17:50 libanonymous.a
-rw-r--r--  1 root root   862 2008-04-09 17:49 libanonymous.la
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so.2
-rw-r--r--  1 root root 12984 2008-04-09 17:50 libanonymous.so.2.0.22
-rw-r--r--  1 root root 15834 2008-04-09 17:50 libcrammd5.a
-rw-r--r--  1 root root   848 2008-04-09 17:49 libcrammd5.la
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so.2
-rw-r--r--  1 root root 15320 2008-04-09 17:50 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 46332 2008-04-09 17:50 libdigestmd5.a
-rw-r--r--  1 root root   871 2008-04-09 17:49 libdigestmd5.la
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so.2
-rw-r--r--  1 root root 43020 2008-04-09 17:50 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 13574 2008-04-09 17:50 liblogin.a
-rw-r--r--  1 root root   842 2008-04-09 17:49 liblogin.la
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so.2
-rw-r--r--  1 root root 13268 2008-04-09 17:50 liblogin.so.2.0.22
-rw-r--r--  1 root root 30016 2008-04-09 17:50 libntlm.a
-rw-r--r--  1 root root   836 2008-04-09 17:49 libntlm.la
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so.2
-rw-r--r--  1 root root 29236 2008-04-09 17:50 libntlm.so.2.0.22
-rw-r--r--  1 root root 13798 2008-04-09 17:50 libplain.a
-rw-r--r--  1 root root   842 2008-04-09 17:49 libplain.la
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so.2
-rw-r--r--  1 root root 13396 2008-04-09 17:50 libplain.so.2.0.22
-rw-r--r--  1 root root 22126 2008-04-09 17:50 libsasldb.a
-rw-r--r--  1 root root   873 2008-04-09 17:49 libsasldb.la
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so.2
-rw-r--r--  1 root root 18080 2008-04-09 17:50 libsasldb.so.2.0.22
-rw-r--r--  1 root root 23696 2008-04-09 17:50 libsql.a
-rw-r--r--  1 root root   971 2008-04-09 17:49 libsql.la
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so.2
-rw-r--r--  1 root root 23140 2008-04-09 17:50 libsql.so.2.0.22
-rw-r--r--  1 root root   260 2008-08-06 21:25 smtpd.conf

-- listing of /etc/postfix/sasl --
total 24
drwxr-xr-x 2 root root 4096 2008-08-10 01:44 .
drwxr-xr-x 3 root root 4096 2008-08-10 02:13 ..
-rw-r--r-- 1 root root  260 2008-08-10 01:41 smtpd.conf
-rw-r--r-- 1 root root  240 2008-08-10 01:41 smtpd.conf.orig
-rw-r--r-- 1 root root  328 2008-08-09 23:23 smtpd.conf.sasl
-rw-r--r-- 1 root root  260 2008-08-10 01:41 smtpd.conf.works


-- permissions for /etc/postfix/relay_passwd --
-rw------- 1 root root 37 2008-08-10 00:09 /etc/postfix/relay_passwd

-- permissions for /etc/postfix/relay_passwd.db --
-rw------- 1 root root 12288 2008-08-10 00:10 /etc/postfix/relay_passwd.db

/etc/postfix/relay_passwd.db is up to date.

-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       n       -       -       smtpd
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
amavis	unix	-	-	-	-	2	smtp
	-o smtp_data_done_timeout=1200
	-o smtp_send_xforward_command=yes
	-o disable_dns_lookups=yes
	-o max_use=20
127.0.0.1:10025	inet	n	-	-	-	-	smtpd
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

-- mechanisms on XXXXXXXX.com --
250-AUTH LOGIN PLAIN


-- end of saslfinger output --



/etc/postfix/main.cf
myorigin = XXXXXX.net

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtpd_helo_required = yes
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_delay_reject = yes
disable_vrfy_command = yes

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit

smtpd_data_restrictions = reject_unauth_pipelining

readme_directory = no

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.XXXXXXX.net
mydestination =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
content_filter = amavis:[127.0.0.1]:10024

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

# Relay
relayhost = [XXXXXXXXX.com]
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/relay_passwd
smtp_sasl_sercurity_options =
#smtp_sasl_tls_security_options =
smtp_sasl_mechanism_filter = plain, login
#smtp_password_maps = hash:/etc/postfix/relay_passwd

# SMTP-AUTH
sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes

# TLS Encryption
smtpd_tls_auth_only = no
#smtp_use_tls = yes
smtp_use_tls = no
smtpd_use_tls = yes
#smtpd_use_tls = no
#smtp_tls_note_starttls_offer = yes
smtp_tls_note_starttls_offer = no
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

/etc/postfix/relay_passwd
XXXXXXX.com user:password

/etc/postfix/sasl/smtpd.conf
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: xxxx
sql_passwd: xxxxxxxxx
sql_database: xxxxxx
sql_select: select clear from users where id='%u@%r' and enabled = 1


SASL works from client to server, but fails from server to relay.  Thanks in advance for your help!

---

### Post by kvn290 on 2008-08-15
I tried compiling Cyrus SASL with --enable-login and various other flags.  Still no joy!  Does anyone have any suggestions?

---

### Post by kvn290 on 2008-11-08
Ok folks, I'm giving this a bump because I am still suffering from the same issue, although I have narrowed the problem down.

Relayhost function is not working for me.  Postfix is NOT chroot'd.  SMTP AUTH is working fine (have thoroughly tested) but I am required to use a relayhost as my IP is dynamic.  This is where the problem comes into play...

I think that bug 257096 is in play in the this case, but i'm not sure. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=257096](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=257096)

I'll explain:

main.cf
...
relayhost = [relayhost.somewhere.com]
smtp_sasl_password_maps = hash:/etc/postfix/relay_password
...

relay_password
[relayhost.somewhere.com] user:password

SASL AUTH fails in the case due to "NO mechanism available".

If i change to the following:

main.cf
...
relayhost = <ipaddress> (the actual IP of my relay with no <> characters)
smtp_sasl_password_maps = hash:/etc/postfix/relay_password
...

relay_password
[<ipaddress>] user:password  (notice i left the brackets...removing them results in the same error as above)

SASL AUTH fails because it can't find a matching entry in the relay_password.db (created with postmap command).  The point of this?  If i don't use an IP address, SASL won't even attempt to authenticate.  If I do use an IP in the relayhost field, SASL at least tries to authenticate.  But I can't create an appropriate relay_password.db file. If I match the brackets in both files....immediately receive "no mechs available" error. 

So....this is where i'm stuck.  Does anyone else have this problem?  Does anyone know of a possible solution?

Thanks!!!

---

