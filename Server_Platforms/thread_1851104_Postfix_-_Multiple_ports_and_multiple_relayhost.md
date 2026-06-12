---
title: "Postfix - Multiple ports and multiple relayhost"
date: 2011-09-27
forum: Server Platforms
---

### Post by em_ubu on 2011-09-27
Hi,

I know I can have multiple ports listening, but can I have different relay host on each one?
I tried setting up port tcp/26 in master.cf:

26        inet  n       -       -       -       -       smtpd
-o smtpd_sasl_auth_enable=yes
-o smtpd_sasl_password_maps=static:user:p***
-o smtpd_sasl_security_options=noanonymous
-o smtpd_tls_security_level=may
-o header_size_limit=4096000
-o relayhost=[relayhost]:port

Will that work?

Thanks!

---

