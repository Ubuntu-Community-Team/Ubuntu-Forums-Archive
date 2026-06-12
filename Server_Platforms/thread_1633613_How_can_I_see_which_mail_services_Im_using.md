---
title: "How can I see which mail services Im using?"
date: 2010-11-29
forum: Server Platforms
---

### Post by fro1269 on 2010-11-29
Hello ,

I recently became responsible for a server running Ubuntu 10.04. I am trying to figure out how its outbound mail service is setup. Everything is working fine now, I just want to document how it is setup so if I need to rebuild the box I can do so without too much trouble when the pressure is on. It is a pretty basic setup, the only outbound mail gets sent from php scripts, the server does not receive incoming messages. Is there a place I can look to see what service is sending outgoing messages?

---

### Post by HermanAB on 2010-11-29
This will show the banners of the running services:
$ telnet serveripaddress 25
$ telnet serveripaddress 110
$ telnet serveripaddress 143

---

### Post by SeijiSensei on 2010-11-29
Out of the box, it's likely to be running [Postfix]("http://www.postfix.org/").  Look for an /etc/postfix directory, or take a look at /var/log/mail.log.

---

