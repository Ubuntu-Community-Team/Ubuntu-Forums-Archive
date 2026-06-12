---
title: "Problem setting up SMTP Postfix - cannot connect to server"
date: 2014-04-29
forum: Server Platforms
---

### Post by Bouzanis on 2014-04-29
I am trying to set up a mail server with Ubuntu 12.04 on a cloud VPS. I am using Postfix/Dovecot. I can read and send email through webmin or ssh - no problem. I can read mail through imap from anywhere. However, I cannot send email over SMTP - login fails. There is no firewall on my server and I can connect to the mail server with telnet, but I cannot login.

I guess it is a problem with the authentication settings, but i cannot figure it out for a few days now.

My main cf is 

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


myhostname = mail.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = example.com
mydestination = mail.example.com, localhost.localdomain, localhost, example.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = ipv4
mydomain = mail.example.com
allow_percent_hack = no
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain reject_unknown_recipient_domain reject_unauth_pipelining permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = 
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
tls_random_source = dev:/dev/urandom
# smtp_generic_maps = hash:/etc/postfix/generic
virtual_alias_domains = example.com
virtual_alias_maps = hash:/etc/postfix/virtual
home_mailbox = Maildir/
smtpd_tls_security_level = may


The master cf has:

smtp      inet  n       -       -       -       -       smtpd

ehlo mail.domain.com gives:
[FONT=Menlo]
[/FONT]
[FONT=Menlo]250-PIPELINING[/FONT]
[FONT=Menlo]250-SIZE 10240000[/FONT]
[FONT=Menlo]250-VRFY[/FONT]
[FONT=Menlo]250-ETRN[/FONT]
[FONT=Menlo]250-STARTTLS[/FONT]
[FONT=Menlo]250-AUTH PLAIN[/FONT]
[FONT=Menlo]250-AUTH=PLAIN[/FONT]
[FONT=Menlo]250-ENHANCEDSTATUSCODES[/FONT]
[FONT=Menlo]250-8BITMIME[/FONT]
[FONT=Menlo]250 DSN[/FONT]


Mac Mail says "cannot connect to the SMTP on the default ports". 

Can somebody advise please?

---

