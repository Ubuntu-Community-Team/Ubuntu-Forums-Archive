---
title: "Postfix Mails lost"
date: 2012-12-02
forum: Server Platforms
---

### Post by idlefella on 2012-12-02
Hello everybody

I've a problem with my postfix mail server. I configured my mail server to use an smtp relay host. Because I afterwards changed my dns settings and didn't think of changing my relay host settings on the server, the relay host was not reachable by the server. I got multiple messages in the mail.log which say f.e.:
"Dec  1 20:32:27 Ubuntu-1204-precise-64-minimal postfix/smtp[27401]: warning: relayhost configuration problem"

My problem is now that a lot of mails have been deleted, because the server was not able to send them, also after a lot of retries. 

My question is now if it's possible to recover those mails, when I try to see the queues, they're empty.

Thanks a lot and regards,
idlefella

---

