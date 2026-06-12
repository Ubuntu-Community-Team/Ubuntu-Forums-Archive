---
title: "POSTFIX sending problem through a home server"
date: 2008-12-06
forum: Server Platforms
---

### Post by Twizzle on 2008-12-06
I have set up a home server on which Postfix is installed along with Fetchmail and Zarafa. The plan is to retrieve my email from my ISP (1and1) and store / access it through my server using IMAP. I also want to be able to send email by relaying it through my server to the 1and1 server.

So far retrieving mail is fine. Sending mail via the Zarafa web client is fine. Sending email from my Nokia N95 using Mailfor exchange is fine. BUT sending mail from Thunderbird on my desktop PC does not work and my mail.log shows the following errors:

> Dec  6 08:16:15 thegcs postfix/smtpd[5088]: cannot load Certificate Authority data
Dec  6 08:16:15 thegcs postfix/smtpd[5088]: warning: TLS library problem: 5088:error:0906D066:PEM routines:PEM_read_bio:bad end line:pem_lib.c:746:
Dec  6 08:16:15 thegcs postfix/smtpd[5088]: warning: TLS library problem: 5088:error:0B084009:x509 certificate routines:X509_load_cert_crl_file:PEM lib:by_file.c:280:
Dec  6 08:16:15 thegcs postfix/smtpd[5088]: connect from unknown[192.168.1.100]
Dec  6 08:16:19 thegcs postfix/smtpd[5088]: warning: SASL authentication failure: no secret in database
Dec  6 08:16:19 thegcs postfix/smtpd[5088]: warning: unknown[192.168.1.100]: SASL CRAM-MD5 authentication failed: authentication failure
Dec  6 08:16:19 thegcs postfix/smtpd[5088]: warning: SASL authentication failure: no secret in database
Dec  6 08:16:19 thegcs postfix/smtpd[5088]: warning: unknown[192.168.1.100]: SASL NTLM authentication failed: authentication failure
Dec  6 08:16:19 thegcs postfix/smtpd[5088]: warning: SASL authentication failure: Password verification failed
Dec  6 08:16:19 thegcs postfix/smtpd[5088]: warning: unknown[192.168.1.100]: SASL PLAIN authentication failed: authentication failure
Dec  6 08:16:19 thegcs postfix/smtpd[5088]: warning: unknown[192.168.1.100]: SASL LOGIN authentication failed: authentication failure
Dec  6 08:17:19 thegcs postfix/smtpd[5088]: lost connection after AUTH from unknown[192.168.1.100]
Dec  6 08:17:20 thegcs postfix/cleanup[5100]: F15A325C4BC: message-id=<20081206081719.F15A325C4BC@thegcs.co.uk>
Dec  6 08:17:20 thegcs postfix/qmgr[4623]: F15A325C4BC: from=<double-bounce@thegcs.co.uk>, size=1888, nrcpt=1 (queue active)
Dec  6 08:17:20 thegcs postfix/smtpd[5088]: disconnect from unknown[192.168.1.100]
Dec  6 08:17:20 thegcs postfix/local[5102]: warning: required alias not found: postmaster
Dec  6 08:17:20 thegcs postfix/local[5102]: F15A325C4BC: to=<postmaster@thegcs.co.uk>, orig_to=<postmaster>, relay=local, delay=0.14, delays=0.12/0.01/0/0, dsn=2.0.0, status=sent (discarded)
Dec  6 08:17:20 thegcs postfix/qmgr[4623]: F15A325C4BC: removed


my main.cf is as follows:

> smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtp_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_CAfile = /etc/postfix/cacert.pem

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = thegcs.co.uk, localhost.co.uk, , localhost
relayhost = auth.smtp.1and1.co.uk

smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous

mynetworks = 192.168.1.0/24 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
smtpd_sasl_local_domain = thegcs.co.uk
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
mydomain = thegcs.co.uk

mailbox_command = /usr/bin/zarafa-dagent "$USER"




I assume that there is some sort of problem authorising between my server and my desktop but I am stumped.

Can anyone point me in the right direction please?

---

