---
title: "mailx how add ISP as SMTP"
date: 2008-10-04
forum: Server Platforms
---

### Post by Shwick2 on 2008-10-04
Ubuntu 8.04

How do I configure mailx to use my ISP's SMTP server?  Also I have to enter a username/password.

---

### Post by pdwerryhouse on 2008-10-04
mailx is only a local mail user agent. It will drop all outgoing mail into the mail queue used by your system's mail transport agent  (postfix by default on ubuntu), and it is this which does the heavy-lifting work of sending the mail out.

So, to configure postfix to use your ISP's SMTP server, put this in /etc/postfix/main.cf:

```
relayhost = isp.smtp.server.domain.name
```

and then reload postfix with:

```
postfix reload
```

---

### Post by Shwick2 on 2008-10-04
thanks got it working

---

