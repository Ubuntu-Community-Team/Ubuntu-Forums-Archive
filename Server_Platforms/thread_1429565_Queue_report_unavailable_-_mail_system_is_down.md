---
title: "Queue report unavailable - mail system is down"
date: 2010-03-14
forum: Server Platforms
---

### Post by dre361224 on 2010-03-14
Hey everyone,

I've been going at this for hours on end and not coming to any solutions :(. I'm trying set up my system so that I can send emails from PHP. I was first trying to use sendmail, no success there, and now I'm trying postfix with not much more success...

Here's my mail.err log file contents:
```
Mar 14 08:52:25 drescnc postfix/master[968]: fatal: bind 0.0.0.0 port 25: Address already in use
Mar 14 08:53:49 drescnc postfix/postqueue[977]: fatal: Queue report unavailable - mail system is down
Mar 14 08:57:19 drescnc postfix[979]: error: to submit mail, use the Postfix sendmail command
Mar 14 08:57:19 drescnc postfix[979]: fatal: the postfix command is reserved for the superuser
Mar 14 08:57:35 drescnc postfix/postfix-script[981]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Mar 14 09:09:38 drescnc postfix/master[1248]: fatal: bind 0.0.0.0 port 25: Address already in use
Mar 14 09:24:36 drescnc postfix/master[1354]: fatal: bind 0.0.0.0 port 25: Address already in use
Mar 14 09:24:49 drescnc postfix/postqueue[1359]: fatal: Queue report unavailable - mail system is down
```I'm not too sure what that error means and can't seem to find much on the internet either...

Here's my main.cf file contents:
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
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = drescnc.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = drescnc.com, localhost.drescnc.com, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8, 192.168.0.0/16, 99.240.135.129/32
relay_domains = $mydestination
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
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

```Please, any help would be very appreciated. :)

Dre

---

