---
title: "SMTP Server/Opportunistic TLS/ Internal and External Delivery"
date: 2008-06-24
forum: Server Platforms
---

### Post by tthompson164 on 2008-06-24
I have been trying to build an STMP server that employs "opportunistic" TLS, as one of our clients requies it.  I have spent most of the week trying to get either Postfix or Exim4 working but the problem I always ends up being a relay issue.  I need ths server to send to external domains as well as deliver to one of two local domains hosted on an Exchange server.  The How To's I have tried either don't address the relay issue or I just don't understand what I'm reading.  Can anyone help me with a good tutorial and/or some advice and help?
TIA.....I am at a loss at this point.

---

### Post by gtdaqua on 2008-06-25
Try [Zimbra](http://www.zimbra.com/"). It uses TLS for SMTP and supports Secure POP3 and IMAP. Its pretty easy to setup and administer. 

There is a free version which is good indeed for production environments.
You can relay mails to external or internal exchange servers. You can also granularly restrict relaying.

---

### Post by windependence on 2008-06-25
I agree with gtdaqua.

Just make sure if you want a smooth install, you use the supported version of Ubuntu which is Ubuntu 6.06 LTS (Dapper). You can get it running on 8.04, but it is not as easy as it is on 6.06.

-Tim

---

