---
title: "client can't connect to mail server"
date: 2010-11-19
forum: Server Platforms
---

### Post by Linux&amp;Gsus on 2010-11-19
I followed this tutorial:
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)
Minus the Quota for the mailboxes, since I don't really care about that. But I don't think that should cause any problems in the configuration.
The server is in my local network.

I tried to connect with Thunderbird and Kmail. Kmal brings up an error message eventually, saying something about a time-out.
Squirrelmail says:
```
ERROR: Connection dropped by IMAP server.
```

The log files say:
mail.log & mail.info
```
Nov 19 20:57:20 server1 imapd: LOGIN FAILED, user=me@example.com, ip=[::1]
Nov 19 20:57:20 server1 imapd: authentication error: Input/output error

```

mail.warn & mail.err
```
Nov 19 20:57:20 server1 imapd: authentication error: Input/output error
```

I could send myself a "Welcome" message, as described in the tutorial and the message arrived. Though, haven't tried to send a message to outside.

I searched everything & everywhere only to see that more people have that same error message come up with Squirrelmail. From my understanding some have fixed the issue but I couldn't actually find a solution to this.

Does anyone know how to fix this?

---

### Post by Linux&amp;Gsus on 2010-11-20
Anyone got any hints?

---

