---
title: "Trouble with SMTPS"
date: 2013-10-27
forum: Server Platforms
---

### Post by zachary_miller on 2013-10-27
This is my first post on the forums and just recently got my first Linux cert so thank you for your help and patience.

I have a postfix, dovecot email server running. I have several issues but the one currently at hand is smtps. I have spent several weeks, and countless re-imaging sessions trying to get this one fixed. Embarrassing. I have tried a combination of things from many websites. I really appreciate your help!

I have tried changing the standard port 25 to 465. Here are my config files and the error down below. It shows I am still trying to connect through 25. Comcast my provider blocks 25 where I live per the tech support specialist I talked to on the phone.

**Master**
```

# (yes) (yes) (yes) (never) (100)
# ================================================== ========================
#smtp inet n - - - - smtpd
#smtp inet n - - - 1 postscreen
#smtpd pass - - - - - smtpd
#dnsblog unix - - - - 0 dnsblog
#tlsproxy unix - - - - 0 tlsproxy
#submission inet n - - - - smtpd
# -o syslog_name=postfix/submission
# -o smtpd_tls_security_level=encrypt
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
smtps inet n - n - - smtpd
# -o syslog_name=postfix/smtps
-o smtpd_tls_wrappermode=yes
-o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING

```

**Main**
```

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/cert./iRedMail_CA.pem
smtpd_tls_key_file = /etc/ssl/private/iRedMail.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = min.testserver.net
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
myorigin = min.testserver.net
mydestination = $myhostname, localhost, localhost.localdomain, localhost.$myhostname
relayhost = outbound.mailhop.org:465
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
virtual_alias_domains =
allow_percent_hack = no
swap_bangpath = no
mydomain = testserver.net
mynetworks_style = host
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_reject_unlisted_recipient = yes
smtpd_reject_unlisted_sender = yes
smtpd_sender_restrictions = permit_mynetworks, reject_sender_login_mismatch, permit_sasl_authenticated
delay_warning_time = 0h
maximal_queue_lifetime = 4h
bounce_queue_lifetime = 4h
proxy_read_maps = $canonical_maps $lmtp_generic_maps $local_recipient_maps $mydestination $mynetworks $recipi
ent_bcc_maps $recipient_canonical_maps $relay_domains $relay_recipient_maps $relocated_maps $sender_bcc_maps
$sender_canonical_maps $smtp_generic_maps $smtpd_sender_login_maps $transport_maps $virtual_alias_domains $vi
rtual_alias_maps $virtual_mailbox_domains $virtual_mailbox_maps $smtpd_sender_restrictions
smtp_data_init_timeout = 240s
smtp_data_xfer_timeout = 600s
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_helo_hostname, reject
_invalid_helo_hostname, check_helo_access pcre:/etc/postfix/helo_access.pcre
queue_run_delay = 300s
minimal_backoff_time = 300s
maximal_backoff_time = 4000s
enable_original_recipient = no
disable_vrfy_command = yes
home_mailbox = Maildir/
allow_min_user = no


sasl_psswd-
outbound.mailhop.org:465 username:userpsswd
```


**Dovecot**
```

HostKey /etc/ssh/ssh_host_dsa_key

listen = *
mail_plugins = quota
protocols = pop3 imap imaps sieve
mail_uid = 2000
mail_gid = 2000
first_valid_uid = 2000
last_valid_uid = 2000
log_path = /var/log/dovecot.log
mail_debug = no
auth_verbose = no
auth_debug = no
auth_debug_passwords = no
# Possible values: no, plain, sha1.
auth_verbose_passwords = no

ssl = required
verbose_ssl = no
ssl_cert = </etc/ssl/certs/iRedMail_CA.pem
ssl_key = </etc/ssl/private/iRedMail.key

mail_location = maildir:/%Lh/Maildir/:INDEX=/%Lh/Maildir/
auth_default_realm =
auth_mechanisms = PLAIN LOGIN


Error(min.testserver.net)-
and the error when I try to send an email from my mobile device or roundcube.

Oct 27 13:12:06 min postfix/cleanup[14229]: 010B08A0E5F: message-id=<cak1h71avtlfu7xu8psk9pxm.1382901115
507@email.android.com>
Oct 27 13:12:06 min postfix/qmgr[14198]: 010B08A0E5F: from=< bill@testserver.net >, size=550, nrcpt=1 (queue active)
Oct 27 13:12:07 min postfix/smtpd[14237]: connect from min.testserver.net[127.0.0.1]
Oct 27 13:12:07 min postfix/smtpd[14237]: 095F08A0EA3: client= min.testserver.net[127.0.0.1]
Oct 27 13:12:07 min postfix/cleanup[14229]: 095F08A0EA3: message-id=<cak1h71avtlfu7xu8psk9pxm.1382901115
507@email.android.com>
Oct 27 13:12:07 min postfix/qmgr[14198]: 095F08A0EA3: from=<bill@testserver.net>, size=1515, nrcpt=1 (queue active)
Oct 27 13:12:07 min postfix/smtpd[14237]: disconnect from min.testserver.net[127.0.0.1]
Oct 27 13:12:07 min amavis[1346]: (01346-11) Passed CLEAN, MYUSERS LOCAL [##.###.##.###] [##.###.##.###] <bill@testserver.net> -> <test-email-destination@yahoo.com>, Message-ID: <cak1h71avtlfu7xu8psk9pxm.1382901115507@
email.android.com>, mail_id: BMEA1km-ADqc, Hits: -10, size: 550, queued_as: 095F08A0EA3, 754 ms
Oct 27 13:12:07 min postfix/smtp[14234]: 010B08A0E5F: to=<test-email-destination@yahoo.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=2.4, delays=1.5/0.02/0.01/0.82, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1] :10025): 250 2.0.0 Ok: queued as 095F08A0EA3)
Oct 27 13:12:07 min postfix/qmgr[14198]: 010B08A0E5F: removed
Oct 27 13:12:47 min postfix/smtp[14215]: connect to outbound.mailhop.org[###.##.###.##]:25: Connection timed out
Oct 27 13:12:47 min postfix/smtp[14216]: connect to outbound.mailhop.org[###.##.###.##]:25: Connection timed out
Oct 27 13:12:47 min postfix/smtp[14213]: connect to outbound.mailhop.org[###.##.###.##]:25: Connection timed out
Oct 27 13:12:48 min postfix/smtp[14216]: B20628A0E95: to=<test-email-destination@yahoo.com>, relay=none, delay=3035, delays=2975/0.07/60/0, dsn=4.4.1, status=deferred (connect to outbound.mailhop.org[204.13.248.72]:25: Connection timed out)
Oct 27 13:12:48 min postfix/smtp[14214]: connect to outbound.mailhop.org[###.##.###.##]:25: Connection timed out
Oct 27 13:12:48 min postfix/smtp[14215]: DA8E68A0E9E: to=<test-email-destination@yahoo.com>, relay=none, delay=3015, delays=2955/0.06/60/0, dsn=4.4.1, status=deferred (connect to outbound.mailhop.org[###.##.###.##]:25: Connection timed out)
Oct 27 13:12:48 min postfix/error[14245]: 095F08A0EA3: to=<test-email-destination@yahoo.com>, relay=none, delay=41, delays=0.05/41/0/0.11, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to outbound.mailhop.org[###.##.###.##]:25: Connection timed out)
Oct 27 13:12:48 min postfix/error[14244]: 1514F8A0E9B: to=<test-email-destination@yahoo.com>, relay=none, delay=3025, delays=2965/60/0/0.12, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to outbound.mailhop.org[###.##.###.##]:25: Connection timed out)
```

---

### Post by sandyd on 2013-10-27
moved to seperate thread

---

