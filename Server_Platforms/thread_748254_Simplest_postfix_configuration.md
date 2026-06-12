---
title: "Simplest postfix configuration"
date: 2008-04-07
forum: Server Platforms
---

### Post by pietrob71 on 2008-04-07
I have my linuxbox with ubuntu 7.10 as webserver and I need to send email from my server trough php. I would like to know the minimum postfix configuration to do that, using my Gmail account as smtp server.

I'm googled around for an howto but I've founded a lot of complicated howto about virtual users ect. I would like to use postfix only for send mail trough my Gmail account as smtp server.

Thanks in advance

Pietro

---

### Post by HermanAB on 2008-04-07
So don't use Postfix - use 'nullmailer'.  Google will find it.

Cheers,

Herman

---

### Post by zazuge on 2008-04-24
I have gone trought that long ago ,now I can send and recive from my gmail account.
her's my main.cf
```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
disable_dns_lookups = yes
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
masquerade_domains = /etc/mailname
maximal_backoff_time = 1000s
minimal_backoff_time = 100s
mydestination = localhost,localhost.localdomain,localdomain
myhostname = my-desktop
mynetworks = 192.168.1.0/24 192.168.0.0/24
mynetworks_style = subnet
myorigin = localhost
notify_classes = resource, software, bounce, delay, policy,protocol,
queue_run_delay = 60s
recipient_delimiter = +
relay_domains = 
relayhost = smtp.gmail.com:587
sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay
smtp_generic_maps = hash:/etc/postfix/generic
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/smtp_auth
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_sender_dependent_authentication = yes
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_loglevel = 2
smtp_tls_note_starttls_offer = yes
smtp_tls_per_site = hash:/etc/postfix/tls_per_site
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
smtpd_sasl_auth_enable = no
smtpd_sasl_local_domain = $myhostname
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
tls_random_source = dev:/dev/urandom

```
the difficult part is the certificate generation but I can't help you with that :-p,sorry.

---

