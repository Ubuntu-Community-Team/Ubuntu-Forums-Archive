---
title: "Require Authentication for SMTP Relay with Postfix"
date: 2011-02-24
forum: Server Platforms
---

### Post by zippy123 on 2011-02-24
Hey everyone, having a problem that I can't seem to figure out how to get around. I've got a very basic Postfix setup on Ubuntu 10.04 x64. I have Postfix currently setup to use TLS, and to relay all mail destined for gmail. Everything appears to work fine. But, I would like to require authentication (whomever is sending needs a username and a password to use this relay). Almost everything I can find explains how to set up Postfix to authenticate to someone else's relay, but I need to know how to require authentication on my relay. 

I've tried more combinations of parameters than I can count, and nothing seems to be working. Can anyone offer advice, or a tutorial, or post?

Here is my main.cf:


```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no
readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


myhostname = relay.itv.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = myhost.mydomain.local, ubuntu, localhost.localdomain, localhost, mydomain.local
relayhost =
relay_domains = gmail.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_enforce_tls = no
```

Thanks!

---

### Post by 95yj on 2012-04-25
I know this is an old thread, but I found it searching for the same answer and since no one had responded with a solution, I figured I would post the fix so that others could find the solution when searching.

All that is required to force SASL authentication is to modify the line in main.cf:

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

to remove permit_mynetworks

At this point, the only permit is sasl authenticated so only those authenticating will be able to send mail.

---

### Post by HermanAB on 2012-04-25
...and another old trick is to use "pop before smtp in c":
[http://www.bluelavalamp.net/pop-before-smtp/](http://www.bluelavalamp.net/pop-before-smtp/)

---

