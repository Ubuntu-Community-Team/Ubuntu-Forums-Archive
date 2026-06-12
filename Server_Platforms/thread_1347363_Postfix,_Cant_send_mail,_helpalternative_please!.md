---
title: "Postfix, Cant send mail, help/alternative please!"
date: 2009-12-06
forum: Server Platforms
---

### Post by Sp322 on 2009-12-06
[SIZE=4][B][U][COLOR=Black]When I try to email from my mail client using ESMTP I get this message from it:

[/COLOR][/U][/B][/SIZE]```
[01] 12/5 09:59:26 220 mail.howcanix.com ESMTP Postfix
[01] 12/5 09:59:26 > EHLO killalla-vpgb97
[01] 12/5 09:59:27 250-mail.howcanix.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-AUTH CRAM-MD5 LOGIN DIGEST-MD5 NTLM PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
[01] 12/5 09:59:27 > AUTH LOGIN
[01] 12/5 09:59:27 250-mail.howcanix.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-AUTH CRAM-MD5 LOGIN DIGEST-MD5 NTLM PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
[01] 12/5 09:59:27 > AUTH LOGIN
[01] 12/5 09:59:27 334 VXNlcm5hbWU6
[01] 12/5 09:59:27 > admin@howcanix.com
[01] 12/5 09:59:27 535 5.7.8 Error: authentication failed: bad protocol / cancel
[01] 12/5 09:59:27   ~ Status: Fatal error, giving up!
[00] 12/5 09:59:27   ~ Status: [-]
[00] 12/5 09:59:27   ~ Status: Closing all streams
[00] 12/5 09:59:27   ~ Status: Creating report...

```[SIZE=4][B][U][COLOR=Black]

And then when I try using POP I get this:

[/COLOR][/U][/B][/SIZE]```

[01] 12/5 10:00:11   ~ Status: Opening connection for delivery...
[01] 12/5 10:00:11 --> Connecting socket [1] with 1 entries to mail.howcanix.com Port:465
[00] 12/5 10:00:16 [POP3 ERROR] 103 - Address invalid.
[01] 12/5 10:00:17   ~ Status: Connected
[01] 12/5 10:00:17 > HELO killalla-vpgb97
[01] 12/5 10:00:17 220 mail.howcanix.com ESMTP Postfix
[01] 12/5 10:00:17 > HELO killalla-vpgb97
[01] 12/5 10:00:17 250 mail.howcanix.com
[01] 12/5 10:00:17 > MAIL FROM:<admin@howcanix.com>
[01] 12/5 10:00:17 250 mail.howcanix.com
[01] 12/5 10:00:17 > RCPT TO:<watchoutforthatduck@googlemail.com> [1/1]
[01] 12/5 10:00:17 250 2.1.0 Ok
[01] 12/5 10:00:18 554 5.7.1 <93-96-107-238.zone4.bethere.co.uk[93.96.107.238]>: Client host rejected: Access denied
[01] 12/5 10:00:18   ~ Status: Stage 3 dispatch done [2/1]
[01] 12/5 10:00:18   ~ Status: Delay of 2s [00:00:02]
[01] 12/5 10:00:18 > QUIT 
[01] 12/5 10:00:18 554 5.5.1 Error: no valid recipients
221 2.0.0 Bye
[01] 12/5 10:00:18   ~ Status: Stage 4 dispatch done [2/1]
[00] 12/5 10:00:18   ~ Status: [-]
[00] 12/5 10:00:18   ~ Status: Closing all streams
[00] 12/5 10:00:18   ~ Status: Creating report...

```[SIZE=4][B][U][COLOR=Black]

SSH Logs/Reports/Useful information


/etc/var/mail.log[/COLOR][/U][/B][/SIZE]

```

Dec  5 09:48:16 howcanix postfix/master[5185]: daemon started -- version 2.5.1, configuration /etc/postfix
Dec  5 09:48:22 howcanix postfix/smtpd[7362]: connect from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]
Dec  5 09:48:22 howcanix postfix/smtpd[7362]: setting up TLS connection from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]
Dec  5 09:48:22 howcanix postfix/smtpd[7362]: Anonymous TLS connection established from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Dec  5 09:48:23 howcanix postfix/smtpd[7362]: disconnect from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]
Dec  5 09:49:00 howcanix postfix/smtpd[7362]: connect from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]
Dec  5 09:49:00 howcanix postfix/smtpd[7362]: setting up TLS connection from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]
Dec  5 09:49:01 howcanix postfix/smtpd[7362]: Anonymous TLS connection established from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Dec  5 09:49:01 howcanix postfix/smtpd[7362]: warning: 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]: SASL LOGIN authentication failed: bad protocol / cancel
Dec  5 09:49:02 howcanix postfix/smtpd[7362]: lost connection after UNKNOWN from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]
Dec  5 09:49:02 howcanix postfix/smtpd[7362]: disconnect from 93-96-107-238.zone4.bethere.co.uk[93.96.107.238]

```


[SIZE=4]**_[COLOR=Black]postconf- n[/COLOR]_**[/SIZE]

```
root@howcanix:~# postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
mydomain = mail.howcanix.com
myhostname = mail.howcanix.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = mail.howcanix.com
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

```

[SIZE=4]_**I followed the guide here:**_[/SIZE]

```
http://flurdy.com/docs/postfix/
```

[SIZE=4]**_I've honestly tried everything I could think of i've been working for about 5 hours on this (im not exaggerating, i've even asked help from one of my linux friends but he doesn't know how to fix sadly :()_**[/SIZE]

---

### Post by Sp322 on 2009-12-06
help please!!!

---

