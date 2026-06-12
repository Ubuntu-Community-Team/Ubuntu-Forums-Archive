---
title: "Reject fake email from"
date: 2013-11-27
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-11-27
Hy. I have using ubuntu server with postfix/dovecot. Mail server has address mail.andortipo.ro and i have receive spam mail with "from" [email]anything@andortipo.ro[/email]. Can i reject this fake email's?

---

### Post by nerdtron on 2013-11-27
Post the contents of your postfix configuration.
Do you have these lines on you config?
```
smtpd_recipient_restrictions = permit_mynetworks, reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unlisted_recipient, permit_sasl_authenticated, reject_unauth_destination
smtpd_reject_unlisted_recipient = yes
smtpd_reject_unlisted_sender = yes
smtpd_sender_restrictions = permit_mynetworks, reject_sender_login_mismatch, permit_sasl_authenticated



```

---

