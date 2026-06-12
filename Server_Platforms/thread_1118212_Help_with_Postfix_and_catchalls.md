---
title: "Help with Postfix and catchalls"
date: 2009-04-06
forum: Server Platforms
---

### Post by Sneezer on 2009-04-06
I need some help with my postfix configuration. As it stands now, I can send and receive email without problems. I currently only have a catchall set for all email, however a friend of mine now wants an email address on my server. When I try to setup the virtual postmap file, it will always send all the email to my catch all.

Here's my virtual file:
```
# cognac source
friend@friend1.com friend
@domain1.info      catchall
@domain2.net      catchall
@domain3.com   catchall
```

All emails to [email]friend@friend1.com[/email] will still be routed to catchall.

My postfix main.cf file:

```
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_protocols = all
mailbox_size_limit = 0
mydestination = domain3.com, domain2.net, domain1.info, friend1.com, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
smtp_host_lookup = native
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = 
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
virtual_alias_domains = domain3.com,domain1.info,domain2.net,friend1.com
virtual_alias_maps = hash:/etc/postfix/virtual
```

(I'm a newbie messing with server administration, so if the configuration is off in anyway, let me know please, thanks!!)

---

