---
title: "Postfix SMTP relay problem with secure authentication"
date: 2006-02-05
forum: Server Platforms
---

### Post by papayiya on 2006-02-05
Hi,

I'm trying to set up PostFix to use an SMTP relay on port 2525 using secure authentication.  Everytime I try and send an email I get the following error:

Feb  5 16:25:09 localhost postfix/smtp[29894]: 7D5E02015E: to=<root@localhost.localdomain>, orig_to=<root>, relay=none, delay=0, status=deferred (Host or domain name not found. Name service error for name=mail.xxxx.com type=A: Host not found, try again)

My main.cf file is this:

biff = no
append_dot_mydomain = no
mydestination =
relayhost = mail.xxxx.com:2525
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

I didn't change anything in my master.cf file.
I set up the sasl_passwd file as follows:

mail.xxxx.com:2525	[email]email@xxx.com[/email]:password

When I try to send an email from the server using sendmail, I get the log error as above.

If you have any idea what I'm doing wrong,
Please let me know,
Thanks,
George

---

