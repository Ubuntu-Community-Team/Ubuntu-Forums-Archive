---
title: "global mail alias"
date: 2010-11-17
forum: Server Platforms
---

### Post by calixtine on 2010-11-17
Is there a way to set a global mail alias along the line of /etc/aliases that maps all mail headed to root (or any other system user for that matter) to another user or an external e-mail address? For instance :

```
root: me@example.com
logcheck: root
```

A bit of background : on the servers that I maintain I install nullmailer, point it at my ISP's smtp server as a smarthost and then configure stuff like logcheck & cron-apt with my e-mail address. It would be alot easier just to set one alias for everything, I'm sure I used to do this on debian .. but that was a while ago.

thanks in advance

---

### Post by calixtine on 2010-11-22
Just to reply to my own thread .. ahem.

Although it's not a direct answer to my original question, it works : Nullmailer itself allows you to specify a single address in /etc/nullmailer/adminaddr file to which all internal mail will be re-directed, which solves my problem.

---

