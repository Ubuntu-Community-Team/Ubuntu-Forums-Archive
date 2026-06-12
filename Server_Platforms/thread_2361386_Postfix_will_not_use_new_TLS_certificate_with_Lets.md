---
title: "Postfix will not use new TLS certificate with Letsencrypt"
date: 2017-05-15
forum: Server Platforms
---

### Post by ryanyoung on 2017-05-15
Experts,

I've been struggling with this issue for a couple weeks, and I'm out of options. I recently switched over my TLS certificate from a paid certificate to Letsencrypt. Unfortunately, even after telling Postfix via the main.cf that the new cert and key are in a new location, the e-mail server is still trying to use the old certificate.

Below is my config, which should be fairly vanilla. I know my issue is simple, but I'm stumped even after perusing through most of the Postfix documentation.

Thanks in advance!

```


smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_loglevel = 2
smtpd_tls_cert_file = /etc/letsencrypt/live/url.com/cert.pem
smtpd_tls_key_file = /etc/letsencrypt/live/url.com/privkey.pem

smtp_use_tls=yes
smtp_tls_security_level = may
smtp_tls_loglevel = 2

smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_CAfile = $smtpd_tls_CAfile
tls_random_source = dev:/dev/urandom


```

---

### Post by ryanyoung on 2017-05-17
Up?

---

