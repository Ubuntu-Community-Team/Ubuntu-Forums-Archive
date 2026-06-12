---
title: "Postfix and DynDns"
date: 2008-05-27
forum: Server Platforms
---

### Post by ArrantSquid on 2008-05-27
Alright, so for the past 2 weeks I've been trying to configure webmin/virtualmin with a free DynDns account and I'm at my wits end. I've gotten as far as being able to receive emails, but not send them and now I can send emails, but not receive them. Here's the output of postconf -n.

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = lotek.homelinux.com, localhost.homelinux.com, , localhost.localdomain, localhost
mynetworks = 127.0.0.0/8 192.168.1.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_mechanism_filter = plain, login
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_note_starttls_offer = yes
smtp_tls_per_site = hash:/etc/postfix/tls_per_site
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = no
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport
virtual_alias_maps = hash:/etc/postfix/virtual

```

here's my transport file:
```

.lotek.homelinux.com :
lotek.homelinux.com :
*       smtp:[smtp.gmail.com]:587

```

I'm using gmail to route it because sbc requires authentication. I just don't know what I'm doing wrong. It's especially frustrating since I haven't had much experience with mail servers before. Any help would be appreciated and I'm sorry if I'm being daft.

---

