---
title: "Postfix sending spam"
date: 2015-01-15
forum: Server Platforms
---

### Post by jorden4 on 2015-01-15
Hi guys,

I have a postfix server that is constantly sending out spam. Below is my main.cf.

>   GNU nano 1.3.10                                          File: /etc/postfix/main.cf


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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.cr
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = *my domain*
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = *my domain*, localhost.*mydomain*, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


virtual_maps = hash:/etc/postfix/virtusertable


mydestination = /etc/postfix/local-host-names
message_size_limit = 20971520




---

### Post by SeijiSensei on 2015-01-15
You need to provide some log files like /var/log/mail.log.  Show an entry that records a spam being sent, and show us a sample spam message.  Include all the message headers so we can trace its entire path.

This machine is clearly not visible on the Internet, since "mynetworks" only allows connections from 127.0.0.1, the "localhost" interface on the machine itself.  The only "spam" it could be sending has to be generated on the machine itself.

---

### Post by kpatz on 2015-01-15
Postfix may be "sending" the spam, but something is feeding the spam to Postfix.  Are any services on the server exposed to the Internet, i.e. is it a web server?  Perhaps it got hacked and some spambot PHP pages got installed.

If possible, you may want to disconnect the server from the internet, or at least shut down Postfix until you figure out the problem.

---

### Post by TheFu on 2015-01-15
> **kpatz said:**
> If possible, you may want to disconnect the server from the internet, or at least shut down Postfix until you figure out the problem.

+1 - when did it start happening? What changed? Can you restore the backup from just before that time?
At a minimum, you can use the backup to see what else may have changed on the system that you may not have realized.

---

