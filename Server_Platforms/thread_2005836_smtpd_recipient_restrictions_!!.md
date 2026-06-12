---
title: "smtpd_recipient_restrictions !!"
date: 2012-06-18
forum: Server Platforms
---

### Post by dchen on 2012-06-18
What are the right smtpd_recipient_restrictions and smtpd_sender_restrictions in main.cf to make the Postfix-Smtp-Dovecot SASL configured under Ubuntu server 12.04 LTS work ?

I'm getting lots of errors below in mail.err every 1 min. and 1 second !

Jun 18 03:26:03 server postfix/smtpd[3726]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit
Jun 18 03:27:04 server postfix/smtpd[3772]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit
Jun 18 03:28:05 server postfix/smtpd[3777]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit
Jun 18 03:29:06 server postfix/smtpd[3790]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit
Jun 18 03:30:07 server postfix/smtpd[3793]: fatal: parameter "smtpd_recipient_restrictions": specify at least one working instance of: check_relay_domains, reject_unauth_destination, reject, defer or defer_if_permit

...

Currently my smtpd_recipient_restrictions and smtpd_sender_restrictions are below:

smtpd_recipient_restrictions = reject_unknown_recipient_domain,permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain

---

