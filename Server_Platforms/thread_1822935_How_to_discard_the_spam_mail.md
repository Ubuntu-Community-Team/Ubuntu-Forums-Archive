---
title: "How to discard the spam mail?"
date: 2011-08-11
forum: Server Platforms
---

### Post by Jeffersyuan2011 on 2011-08-11
Dear sir,
I had setup postfix and spam assassin, and in my environment, I forward the incoming email to my exchange server.
Everything works now, in my mail box, I can receive the email with subject ******SPAM*****.
but is there a solution, when spam assassin finished the scan and mark spam, if the score is very high, may be stop to forward it to exchange, for example, send it to a special email box?

Thanks.
Jeffers

---

### Post by SeijiSensei on 2011-08-12
[MailScanner]("http://www.mailscanner.info/") can be configured to do a variety of things with messages depending on their SpamAssassin scores including forwarding them to a specific account or putting them into quarantine.

---

