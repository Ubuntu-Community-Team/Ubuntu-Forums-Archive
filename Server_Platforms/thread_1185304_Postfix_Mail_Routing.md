---
title: "Postfix Mail Routing"
date: 2009-06-12
forum: Server Platforms
---

### Post by PJDouglas on 2009-06-12
Hi,

I have Postfix setup as a mail relay which is working fine.

All mail sent from our exchange server (192.168.1.1) to postfix for address rewriting is then sent to a smarthost (128.2.1.1).

Test mails I have sent have been delivered according to the logs but I am not receiving the auto reply back.

Presumably, I need to set up a mail route for all mail received from the smarthost (128.2.1.1) to be delivered back to our exchange (192.168.1.1).

Not sure how to do this.

How do I set up a mail route to deliver all mail from 128.2.1.1 to 192.168.1.1?

Many Thanks

Paul.

---

