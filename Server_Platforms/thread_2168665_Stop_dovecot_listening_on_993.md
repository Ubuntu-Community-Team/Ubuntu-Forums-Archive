---
title: "Stop dovecot listening on 993"
date: 2013-08-18
forum: Server Platforms
---

### Post by miles3 on 2013-08-18
Hi,

I have setup dovecot via the mail-stack-delivery route. I'm using TLS connections and want to disable IMAPS because it isn't/won't be used. I have changed my /etc/dovecot/dovecot.conf file to have the line:

```
protocols = imap
```

and restarted dovecot. That has removed the pop3 listeners quite nicely but dovecot is still listening for IMAPS connections on port 993.

---

### Post by miles3 on 2013-08-20
Solved:

edit **/etc/dovecot/conf.d/10-master.conf**:

```
inet_listener imaps {
    address = none
  }
```

---

