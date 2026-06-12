---
title: "sending local mails to isp account with postfix -&gt; 5.7.1 status=bounced"
date: 2021-07-26
forum: Server Platforms
---

### Post by jori gel on 2021-07-26
Hi folks, trying to send local emails to my isp account with postfix and I get the upper error. Even canonical_mapping of the sender's name didn't help.  main.cf: --- begin relayhost = [smtp.ewe.net]:587 smtp_use_tls = yes smtpd_sasl_auth_enable = yes smtp_sasl_security_options = smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt --- end  anybody an idea what to do? regards   jori

---

