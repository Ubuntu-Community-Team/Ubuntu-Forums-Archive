---
title: "[SOLVED] cannot get 220 banner-POSTFIX"
date: 2008-02-15
forum: Server Platforms
---

### Post by Daveyboy on 2008-02-15
Hello all,

I tried configuring postfix as per;

[https://help.ubuntu.com/pdf/ubuntu/C/serverguide.pdf](https://help.ubuntu.com/pdf/ubuntu/C/serverguide.pdf)

I am using ubuntu 6.06. I am at a loss as to why it will not work. I cannot telnet to port 25 successfully, it just gives a flashing prompt. Here are my logs;

mail.warn

> Feb 15 06:41:59 pickle postfix/master[10433]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Feb 15 06:42:59 pickle postfix/smtpd[15214]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, $
Feb 15 06:43:00 pickle postfix/master[10433]: warning: process /usr/lib/postfix/smtpd pid 15214 exit status 1
Feb 15 06:43:00 pickle postfix/master[10433]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Feb 15 06:44:00 pickle postfix/smtpd[15216]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, $
Feb 15 06:44:01 pickle postfix/master[10433]: warning: process /usr/lib/postfix/smtpd pid 15216 exit status 1



/etc/postfix/main.cf

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = pickle.xxxx.ca
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = pickle.xxxx.ca,pickle.xxxx,localhost
relayhost =
mynetworks = 192.168.32.0/24,  127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
myorigin = /etc/mailname


---

### Post by Daveyboy on 2008-02-15
okay so, i figured out the problem, 

I had to add;

reject_unauth_destination
 
to

smtpd_recipient_restrictions = 

so it now looks like;

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination


restarted postfix and now works.

---

