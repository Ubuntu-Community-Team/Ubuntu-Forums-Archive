---
title: "Dovecot gets killed upon starting [12.04]"
date: 2012-12-12
forum: Server Platforms
---

### Post by petarpetrovic on 2012-12-12
I have set up a shiny new mail server on Ubuntu 12.04 LTS by installing the mail-server^ package. I am using MySQL for virtual user & domain info and everything seems to be just fine, except that Dovecot starts and then immediately gets killed by some process.

Here's what the /var/log/mail.log file says:

```
Dec 12 20:01:58 stephania dovecot: master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec 12 20:01:58 stephania dovecot: config: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec 12 20:01:58 stephania dovecot: anvil: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Dec 12 20:01:58 stephania dovecot: log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
```How do I proceed about this? I have tried various things but nothing seems to help.

---

### Post by petarpetrovic on 2012-12-12
This is kind of weird. I've redeployed Ubuntu, but this time 12.10 version, and the problem still persists. I've managed to solve it by installing ssl-cert package, chowning to root:dovecot the ssl-cert-snakeoil.pem and ssl-cert-snakeoil.key and made Dovecot use that instead of its own certificates.

I should also note that Apple Mail doesn't work when Postfix and Dovecot use different set of SSL certificates, so it is advisable to configure both of them to use the snakeoil ones, unless, of course, you obtain your own certificates through some CA.

Maybe this will be useful to someone in the future.

---

