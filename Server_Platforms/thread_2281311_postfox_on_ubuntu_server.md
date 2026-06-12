---
title: "postfox on ubuntu server"
date: 2015-06-06
forum: Server Platforms
---

### Post by FCNBYwP on 2015-06-06
Good day,
I have a ubuntu server at work 10.04 Lucid.
I have osticket and wordpress installed on it.

I want to be able to receive email notifications from osticket and wordpress.
I have installed postfix but the server is still unable to send emails apparently. 
I am not receiving anything
[http://paste.ubuntu.com/11602172/](http://paste.ubuntu.com/11602172/) config on postfix

Regards,
Bero

---

### Post by coffeecat on 2015-06-06
*Thread moved to **Server Platforms**.*

I have removed the Lubuntu thread title prefix which I guess must have been added by mistake. Ubuntu server is Ubuntu. Lubuntu is one of the desktop Ubuntu flavours.

Also - 10.04 has now passed end of life. You need to upgrade to a supported version.

---

### Post by SeijiSensei on 2015-06-06
Here's a simple test.  Open a terminal and run the command:
```
telnet alt1.gmail-smtp-in.l.google.com 25
```
If you can connect, you'll see GMail reply with its "banner" like this:
```

Trying 74.125.24.27...
Connected to alt1.gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP s1si2787214wiy.52 - gsmtp

```
If you don't see that, you'll need to talk to your ISP and make sure they are not filtering traffic to remote SMTP servers.

To close the telnet session, hold down the Ctrl key and type the "]" character.  Then type "quit" at the prompt.

---

