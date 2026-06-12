---
title: "ssmtp frustration"
date: 2016-11-04
forum: Server Platforms
---

### Post by alabamatoy2 on 2016-11-04
Ubuntu 16.04.... If I enter *sudo ssmtp [email]recipient@somewhere.com[/email]* and type some text, then hit ctrl-d I get the following in the syslog:

  ```
Nov  4 15:18:58 garage-security sSMTP[27717]: 550 5.6.0 Invalid header found (see RFC2822 section 3.6) 
```  But if I look at the message I received from cron in the syslog, I see

  ```
Nov  4 15:01:03 garage-security sSMTP[20685]: Sent mail for root@mydomain.com (221 2.3.0 smtp01.wow.cmh.synacor.com closing connection) uid=0 username=root outbytes=761 
```  Both ssmtp and sendmail fail in the same way.  I dont understand why  cron can send email but I cant from the command line - don't they both  use the same config file?  Can someone clue me in?

---

### Post by howefield on 2016-11-04
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

