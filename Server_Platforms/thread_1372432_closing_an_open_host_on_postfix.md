---
title: "closing an open host on postfix"
date: 2010-01-04
forum: Server Platforms
---

### Post by radcom on 2010-01-04
I have read many tutorials and guides on how to apply authentication to SMTP on postfix and so far had no look making it work, I do have authentication on dovecot on the pop3 and IMAP servers
 I have been trying to make this work now for on and off 3 months now and am completely stumped
I am running my own server with a dynamically IP address but I have a DNS service to give me a fixed domain name which works.
as I am on a dynamic IP I can't send email to external accounts as they need to to through a relay host but I cant set that up until there is some form of authentication on the smtp of postfix even if its just plain-text

originality I ran a windows server with hmailserver which was so easy to setup and use

I have postfix, dovecot, sasld installed

below are my postfix main.cf file and I can post my dovecot if needs be
```

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
#smtpd_tls_cert_file = /etc/ssl/certs/server.crt
#smtpd_tls_key_file = /etc/ssl/private/server.key

smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#myhostname = ubuntu-server
myhostname = radcom.endofinternet.net
alias_maps = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = radcom.endofinternet.net, ubuntu-server, localhost.localdomain, localhost, mail.radcom.endofinternet.net
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, check_relay_domains
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium, high
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s

```

---

### Post by noway2 on 2010-01-04
From a quick look I didn't see anything particularly wrong with your file.  Comparing it to mine, which does use authentication on SMTP, the only difference I can see is in the SMTPD_RECIPIENT_RESTRICTIONS.  In my file, I have the following entry "permit_sasl_authenticated".

---

### Post by radcom on 2010-01-04
if I telnet to port 25 I get the following:

EHLO radcom.endofinternet.net
250-radcom.endofinternet.net
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

I am have complete access to the server so can post any additional information you need it just say what you need me to find

---

