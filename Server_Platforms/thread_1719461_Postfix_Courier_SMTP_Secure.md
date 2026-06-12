---
title: "Postfix Courier SMTP Secure"
date: 2011-04-01
forum: Server Platforms
---

### Post by imagine7xy on 2011-04-01
Hello, I am getting an issue when trying to send out email on 465	secure SMTP with a Postfix + Courier with MySQL virtual users. I am able to connect with IMAP secure and download, and I can also send mail on Port 25 unsecured. I am trying to use SASL for the outgoing. When I try to telnet port 465 its refused. When I try to send a message I get this in the /var/log/mail.log

> Apr  2 00:24:34 Lucid postfix/smtpd[3714]: connect from pool-74-111-178-60.pitbpa.fios.verizon.net[74.111.178.60]
Apr  2 00:24:34 Lucid postfix/smtpd[3714]: warning: SASL authentication problem: unknown password verifier
Apr  2 00:24:34 Lucid postfix/smtpd[3714]: warning: SASL authentication failure: Password verification failed
Apr  2 00:24:34 Lucid postfix/smtpd[3714]: warning: pool-74-111-178-60.pitbpa.fios.verizon.net[74.111.178.60]: SASL PLAIN authentication failed: no mechanism available
Apr  2 00:24:34 Lucid postfix/smtpd[3714]: warning: SASL authentication problem: unknown password verifier
Apr  2 00:24:34 Lucid postfix/smtpd[3714]: warning: pool-74-111-178-60.pitbpa.fios.verizon.net[74.111.178.60]: SASL LOGIN authentication failed: no mechanism available
Apr  2 00:24:35 Lucid postfix/smtpd[3714]: disconnect from pool-74-111-178-60.pitbpa.fios.verizon.net[74.111.178.60]

Here are copies of other files, please help! How can I turn up logging, I can't seem to figure anything out here.

[/etc/postfix/sasl/smtpd.conf]("http://74.111.178.60/random/smtpd.conf")
[/etc/postfix/main.cf]("http://74.111.178.60/random/main.cf")
[/etc/postfix/master.cf]("http://74.111.178.60/random/master.cf")
[/etc/default/saslauthd]("http://74.111.178.60/random/saslauthd")
[/etc/pam.d/smtp]("http://74.111.178.60/random/smtp")

---

### Post by seannon on 2011-04-02
I am not sure where to go about it yet, but according to your logs it is trying to verify username/password info, I am working on a similar setup right now, but my issues are so far limited to getting IPv6 to work... I will post back if I see anything further...

---

