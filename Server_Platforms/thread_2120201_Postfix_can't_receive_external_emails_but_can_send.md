---
title: "Postfix can't receive external emails but can send external emails"
date: 2013-02-25
forum: Server Platforms
---

### Post by Elnison on 2013-02-25
hi guys 
please help out here. No logs when I try to send from yahoo or gmail in my server.

my postconf -n 
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
home_mailbox = Maildir/
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = $myhostname localhost.$mydomain localhost
myhostname = mail.hmd-c.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 10.0.0.0/24
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

my master.cf

```

smtp       inet  n       -       -       -       -       smtpd
submission inet  n       -       -       -       -       smtpd -o smtpd_sasl_auth_enable=yes -o smtpd_tls_auth_only=no -o smtpd_client_restrictions=permit_sasl_authenticated -o smtpd_sasl_security_options=noanonymous -o smtpd_sasl_tls_security_options=noanonymous
smtps      inet  n       -       -       -       -       smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes -o smtpd_tls_auth_only=no -o smtpd_client_restrictions=permit_sasl_authenticated -o smtpd_sasl_security_options=noanonymous -o smtpd_sasl_tls_security_options=noanonymous
pickup     fifo  n       -       -       60      1       pickup -o content_filter= -o receive_override_options=no_header_body_checks
cleanup    unix  n       -       -       -       0       cleanup
qmgr       fifo  n       -       n       300     1       qmgr
tlsmgr     unix  -       -       -       1000?   1       tlsmgr
rewrite    unix  -       -       -       -       -       trivial-rewrite
bounce     unix  -       -       -       -       0       bounce
defer      unix  -       -       -       -       0       bounce
trace      unix  -       -       -       -       0       bounce
verify     unix  -       -       -       -       1       verify
flush      unix  n       -       -       1000?   0       flush
proxymap   unix  -       -       n       -       -       proxymap
proxywrite unix  -       -       n       -       1       proxymap
smtp       unix  -       -       -       -       -       smtp
relay      unix  -       -       -       -       -       smtp -o smtp_fallback_relay=
showq      unix  n       -       -       -       -       showq
error      unix  -       -       -       -       -       error
retry      unix  -       -       -       -       -       error
discard    unix  -       -       -       -       -       discard
local      unix  -       n       n       -       -       local
virtual    unix  -       n       n       -       -       virtual
lmtp       unix  -       -       -       -       -       lmtp
anvil      unix  -       -       -       -       1       anvil
scache     unix  -       -       -       -       1       scache
maildrop   unix  -       n       n       -       -       pipe flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp       unix  -       n       n       -       -       pipe flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail     unix  -       n       n       -       -       pipe flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp      unix  -       n       n       -       -       pipe flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n       n       -       2       pipe flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman    unix  -       n       n       -       -       pipe flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py ${nexthop} ${user}
amavis     unix  -       -       -       -       2       smtp -o smtp_data_done_timeout=1200 -o smtp_send_xforward_command=yes -o disable_dns_lookups=yes -o max_use=20
127.0.0.1:10025 inet n   -       -       -       -       smtpd -o content_filter= -o local_recipient_maps= -o relay_recipient_maps= -o smtpd_restriction_classes= -o smtpd_delay_reject=no -o smtpd_client_restrictions=permit_mynetworks,reject -o smtpd_helo_restrictions= -o smtpd_sender_restrictions= -o smtpd_recipient_restrictions=permit_mynetworks,reject -o smtpd_data_restrictions=reject_unauth_pipelining -o smtpd_end_of_data_restrictions= -o mynetworks=127.0.0.0/8 -o smtpd_error_sleep_time=0 -o smtpd_soft_error_limit=1001 -o smtpd_hard_error_limit=1000 -o smtpd_client_connection_count_limit=0 -o smtpd_client_connection_rate_limit=0 -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

```

other info, my ISP block port 25 they just they gave their relayhost which points to their smtp server.

---

### Post by Vishal Agarwal on 2013-02-26
> my ISP block port 25 they just they gave their relayhost which points to their smtp server.

Usually most of the ISP  close 25 port to stop spamming. you can use port 465, or 587 to send your emails.
Post some of mail.log of sending mail outside.

---

### Post by Elnison on 2013-02-26
here's the log when I send outside

```

Feb 27 08:03:17 mail postfix/qmgr[18253]: A7043B80A08: from=<user@domain.com>, size=765, nrcpt=1 (queue active)
Feb 27 08:03:17 mail postfix/smtpd[25677]: disconnect from localdomain.localhost[127.0.0.1]
Feb 27 08:03:17 mail amavis[13852]: (13852-03) FWD via SMTP: <user@domain.com> -> <user@yahoo.com>,BODY=7BIT 250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as A7043B80A08
Feb 27 08:03:17 mail amavis[13852]: (13852-03) Passed CLEAN, LOCAL [127.0.0.1] [127.0.0.1] <user@domain.com> -> <user@domain.com>, Message-ID: <20130227000312.6451FB802DC@mail.domain.com>, mail_id: xgSfwaMMZxQY, Hits: 1.974, size: 318, queued_as: A7043B80A08, 743 ms
Feb 27 08:03:17 mail postfix/smtp[25674]: 6451FB802DC: to=<user@yahoo.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=12, delays=11/0.02/0/0.74, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as A7043B80A08)
Feb 27 08:03:17 mail postfix/qmgr[18253]: 6451FB802DC: removed
Feb 27 08:03:21 mail postfix/smtp[25678]: A7043B80A08: to=<user@yahoo.com>, relay=smtpdsl4.pldtdsl.net[210.213.253.193]:587, delay=3.7, delays=0.07/0.02/2.3/1.3, dsn=2.0.0, status=sent (250 ok:  Message 76418089 accepted)
Feb 27 08:03:21 mail postfix/qmgr[18253]: A7043B80A08: removed

```

any ideas guys?

---

### Post by confusedstingray on 2013-02-26
have you tried testing from out side your network 
try  mxtoolbox.com 
while trying this see what your syslog is saying 
also do you have a firewall  between your mail server and the internet
is it set to allow mail to your server

---

### Post by Elnison on 2013-02-26
yeah i've tried sending emails from yahoo and gmail to my server but still I can't receive messages.
my syslog and mail.log gives me nothing. I don't know why.
I didn't set any firewall. My plan is set the mail servers first before the firewall.

---

### Post by Elnison on 2013-02-26
I didn't have any problems sending and receiving mails inside my network. The problem is that I can't receive any emails coming from outside. There's nothing in syslog or mail.log.

---

### Post by Elnison on 2013-02-27
I think I found my problem when I dig mx domain.com I get this
```

domain.com.              3600    IN      MX      10 mail.domain.com.
```

but when I use dig mx mail.domain.com I get this
```

mail.hmd-c.com.         3493    IN      A    (no IP)
```

no A record pointing to my server. How can I fix this? do I need to install bind9? or contact GoDaddy.com?

---

### Post by lisati on 2013-02-27
> **Elnison said:**
> I think I found my problem when I dig mx domain.com I get this
```

domain.com.              3600    IN      MX      10 mail.domain.com.
```

but when I use dig mx mail.domain.com I get this
```

mail.hmd-c.com.         3493    IN      A    (no IP)
```

no A record pointing to my server. How can I fix this? do I need to install bind9? or contact GoDaddy.com?

I think the answer is touched on in your [other thread]("http://ubuntuforums.org/showthread.php?t=2117636"): you need to point the A record for mail.domain.com to the server that's hosting your server. I'm not familiar with GoDaddy's options; maybe someone more knowledgable might be able to step in and offer a suggestion.

---

