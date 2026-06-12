---
title: "Postfix ignoring sender username"
date: 2016-03-05
forum: Server Platforms
---

### Post by ScorpioTiger on 2016-03-05
Still struggling to set up outgoing email for Magento. I've installed Postfix and configured it to relay to our Rackspace hosted email.

My configuration for relaying is;
relayhost = secure.emailsrvr.com:587
smtp_sasl_auth_enable=yes
smtp_sasl_password_maps=hash:/etc/postfix/sasl_passwd
smtp_sasl_mechanism_filter = AUTH LOGIN
smtp_sasl_security_options =
smtp_use_tls = yes

The contents of /etc/postfix/sasl_passwd are;
secure.emailsrvr.com [EMAIL="administrator@mydomain.com"]administrator@mydomain.com[/EMAIL]:mypassword

When I try to send an email from Magento (by performing a password change), I'm not getting the email and in the Postfix log, I'm getting;

Mar  5 22:46:05 Magento2 postfix/qmgr[15654]: C111D144031: from=<www-data@mydomain.com>, size=671, nrcpt=1 (queue active)
Mar  5 22:46:06 Magento2 postfix/smtp[15827]: C111D144031: to=<my.name@mydomain.com>, relay=secure.emailsrvr.com[173.203.187.10]:587, delay=2109, delays=2108/0/0.93/0.21, dsn=5.1.0, status=bounced (host secure.emailsrvr.com[173.203.187.10] said: 550 5.1.0 <www-data@mydomain.com>: Sender address rejected: User unknown in relay recipient table (in reply to RCPT TO command))
Mar  5 22:46:06 Magento2 postfix/cleanup[15825]: C7DD2144039: message-id=<20160306034606.C7DD2144039@magento>
Mar  5 22:46:06 Magento2 postfix/qmgr[15654]: C7DD2144039: from=<>, size=2613, nrcpt=1 (queue active)
Mar  5 22:46:06 Magento2 postfix/bounce[15828]: C111D144031: sender non-delivery notification: C7DD2144039
Mar  5 22:46:06 Magento2 postfix/qmgr[15654]: C111D144031: removed
Mar  5 22:46:08 Magento2 postfix/smtp[15827]: C7DD2144039: to=<www-data@mydomain.com>, relay=secure.emailsrvr.com[173.203.187.10]:587, delay=1.5, delays=0.01/0/1.1/0.43, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 128761800F6)

I've specified the sending email account to use (administrator@mydomain.com), but for some reason the user name is being changed to "www-data" which I'm thinking is maybe the account that Magento is running under? Why is this being overridden when I've explicitly stated the username?

---

### Post by sandyd on 2016-03-05
Moved to *Server Platforms.*

---

