---
title: "Postfix - Address Rewrite"
date: 2009-05-08
forum: Server Platforms
---

### Post by PJDouglas on 2009-05-08
Hi,

Just installed postfix and need to rewrite the sender address before it sends mail to the smarthost.

Postfix is configured to send mail straight to the smart host. There is no local delivery of mail.

Need to rewrite the sender address for all outbound mail. 

I have tried, 'remote_header_rewrite_domain = mydomain.com' which didn't work.

What is the correct syntax for rewrite the sender address for all outbound mail?
 

Many Thanks

Paul.

---

### Post by sidcypher on 2009-05-08
this may be what I am needing...

I am trying to forward all my outgoing through my ISP's smtp..

since dynamic is blacklisted..and no mail is delivered then...

---

