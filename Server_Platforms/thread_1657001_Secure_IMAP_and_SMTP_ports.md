---
title: "Secure IMAP and SMTP ports"
date: 2010-12-31
forum: Server Platforms
---

### Post by DarthScape on 2010-12-31
Using Dovecot and Postfix on Zentyal latest, I want to change the port number for people accessing secure imap and smtp. ie port 668 instead of 25 for smtp. Where can I change that, and will it effect webmail access from Roundcube?

---

### Post by James78 on 2010-12-31
I don't guarantee my method of doing this, however I believe it WILL work (try it out, you can always revert it if it fails).

Edit your /etc/services file, in it find the entry for smtp, change the port number.

This is one way, however it may not be the best way. Me, preferably, I'd actually just change it in the config files instead.

No, there shouldn't be any reason for it to affect webmail access.

Change Postfix port number (SMTP)
[http://www.linuxmail.info/postfix-change-port/](http://www.linuxmail.info/postfix-change-port/)

Dovecot (head down to the "Service structure" section)
[http://qmail.jms1.net/dovecot.shtml](http://qmail.jms1.net/dovecot.shtml)

---

