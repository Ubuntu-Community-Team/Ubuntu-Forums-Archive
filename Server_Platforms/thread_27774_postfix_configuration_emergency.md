---
title: "postfix configuration emergency"
date: 2005-04-17
forum: Server Platforms
---

### Post by ubuntu_demon on 2005-04-17
Hi,

I need to run a mailserver as an emergency backup for a friend of mine. His mailserver is already down for a couple of days so I have to get it up as soon as possible.

I've never run a mailserver. I need to be able to receive mail. I configured postfix using

$ sudo dpkg-reconfigure postfix

these are the settings I made :
```

internet site
/var/mail/myusername
mailname = mydomain
other destinations to accept mail for : localhost.localdomain, localhost, mydomain , myfriendsdomain
force synchronous updates = yes
mail relay networks =  127.0.0.0/8
mailbox size limit =  51200000
local address extension character = blank

```

In firestarter I opened port 25. And I also checked it out using [www.grc.com](www.grc.com) and it was stealth.

when I mail username@mydomain using gmail I don't see new mails appearing in mutt and I don't see the mailbox growing in /var/mail/username

---

### Post by speedman on 2005-04-17
[QUOTE=demon666_nl]In firestarter I opened port 25. And I also checked it out using [www.grc.com](www.grc.com) and it was stealth.[/QUOTE]

Perhaps your ISP filters SMTP (port 25) as an anti-spam measure.

> when I mail username@mydomain using gmail I don't see new mails appearing in mutt and I don't see the mailbox growing in /var/mail/username

tail -f /var/log/mail.log


Regards,

SM

---

### Post by ubuntu_demon on 2005-04-17
[QUOTE=speedman]Perhaps your ISP filters SMTP (port 25) as an anti-spam measure.



tail -f /var/log/mail.log


Regards,

SM[/QUOTE]
 stupid me .. you are completely right!
my ISP sucks :S

---

