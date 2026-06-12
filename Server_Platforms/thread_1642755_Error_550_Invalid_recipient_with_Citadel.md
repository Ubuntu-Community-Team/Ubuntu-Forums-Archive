---
title: "Error 550 Invalid recipient with Citadel"
date: 2010-12-10
forum: Server Platforms
---

### Post by jmehdi on 2010-12-10
I've installed citadel on ubuntu 10.10 server. I can send emails but not receive.
I get this error when I send emails to my server:

SMTP error from remote mail server after RCPT TO:<admin@mydomain.fr>:
    host mail.mydomain.fr [xx.xxx.xxx.xxx]: 550 Invalid recipient:
    [email]admin@mydomain.fr[/email]

In "Edit site-wide configuration" I have:
Node name: myserver
FQDN: mydomain.fr

I made a mistake after install by setting node name to mydomain.fr, but I've fixed it by putting the hostname.


sendcommand seems ok:
$ sudo sendcommand "QDIR [email]admin@mydomain.fr[/email]"
200 admin @ mydomain.fr

but if I use telnet:
telnet mydomain.fr 25
...
mail from: [email]sdf@yahoo.com[/email]
250 sender ok
rcpt to: [email]admin@mydomain.fr[/email]
550 Invalid recipient: [email]admin@mydomain.fr[/email]

I don't understand....
Is it a misconfiguration of citadel? or is the problem related to my DNS config?

---

