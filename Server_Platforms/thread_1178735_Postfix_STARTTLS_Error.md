---
title: "Postfix STARTTLS Error"
date: 2009-06-04
forum: Server Platforms
---

### Post by trentscott4 on 2009-06-04
I followed the Ubuntu guide at [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) on installing Postfix and Dovecot.  As far as I can tell, the mail server is operational.

However, from Evolution I receive the following error, "STARTTLS command failed: TLS not available due to local problem."

Here are the relevant parts from my main.cf file:

> # TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

Anyone who can help is greatly appreciated!

---

### Post by LepeKaname on 2009-06-05
This is what I have in my main.cf:

```
# TLS parameters
smtpd_use_tls = yes
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/sasl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/sasl/smtpd.key
smtpd_tls_CAfile = /etc/postfix/sasl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_note_starttls_offer = yes
tls_random_source = dev:/dev/urandom
```

---

