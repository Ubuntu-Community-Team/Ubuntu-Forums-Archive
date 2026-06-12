---
title: "What should i change in postfix?"
date: 2011-10-12
forum: Server Platforms
---

### Post by niqmk on 2011-10-12
Hi,

I'd tried my postfix sending my email (my current networks: 192.168.1.130) and works perfect. But when I tried to send in different network (Let's say 43.223.2.33) it can't deliver. Tried telnet my domain (like telnet mydomain.com 25) it won't work.

What should I change?

Here's my main.cf

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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myorigin = /etc/mailname
myhostname = mydomain.com
local_recipient_maps =
mydestination = localhost, localhost.localdomain, $myhostname
relayhost = [smtp.telkom.net]:25
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
default_transport = smtp
relay_transport = smtp
html_directory = /usr/share/doc/postfix/html
inet_protocols = ipv4
home_mailbox = Maildir/
smtpd_client_restrictions = permit_mynetworks
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes

smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_not_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes

```

Thanks

---

### Post by SwitchLink on 2011-10-14
I see a few things that might be an issue:

myhostname = mydomain.com
mynetworks = 127.0.0.0/8, 192.168.1.0/24
smtpd_client_restrictions = permit_mynetworks



As far as I understand, the myhostname should be = hostname.mydomain.com.  Where hostname is equal to the machine's hostname, which should also be the same as your mx record.

The mynetworks is correct as it restricts relaying to the local machine and the 192.168.1.0/24 network.

I don't have sasl enabled on my server, but I suspect your sasl restrictions or mynetworks setting might be rejecting requests - that is if there is not a firewall or dns problem preventing you from actually getting to the box.

When you say, send in a different domain it can't deliver - do you mean that if you try to connect from a different domain it doesn't connect, or it won't let you send once you are connected?

---

