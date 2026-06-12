---
title: "Courier POP and Postfix headache - need medicine"
date: 2007-04-23
forum: Server Platforms
---

### Post by Ray Paradise on 2007-04-23
I have a Postfix server up and running on my Ubuntu workstation. I can send e-mail to my maildir mailbox so I know the MX, DNS and Postfix settings are correct. I can't seem to open port 110 in order to make a POP3 connection though. Can someone walk me through this (I am relatively new to Linux but am really enjoying the transition from Windows!!)? BTW, here is my main.cf config:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.tone40enterprises.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.tone40enterprises.com, localhost.localdomain, localhost, tone40enterprises.com
relayhost = 
mynetworks = 75.144.27.173, 127.0.0.0/8 
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_doamain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
inet_protocols = all
virtual_alias_domains = tone40enterprises.com
virtual_alias_maps = hash:/etc/postfix/virtual

---

### Post by Ray Paradise on 2007-04-23
This is possibly the bug I'm running into:

[https://bugs.launchpad.net/ubuntu/+source/courier/+bug/28552](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/28552)

Any ideas on how to fix this?

-Ray

---

