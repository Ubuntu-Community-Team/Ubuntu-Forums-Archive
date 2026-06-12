---
title: "Mail Server, can't send or receive"
date: 2011-03-05
forum: Server Platforms
---

### Post by Code9 on 2011-03-05
Every time I try to send a message with SquirrelMail, I get: 

```
Message not sent. Server replied:
Syntax error in parameters or arguments
501 5.1.7 Bad sender address syntax
```


Any ideas?

---

### Post by Code9 on 2011-03-05
Help!

---

### Post by hictio on 2011-03-05
Have you checked the logs?
Can you actually send an email if you don't use Squirrelmail? From the command line I mean.
What MTA are you using? Postfix, Sendmail?

---

### Post by Code9 on 2011-03-06
I don't think I can send it from the command line. I have Postfix, Dovecot and SquirrelMail installed. I haven't installed any spam filters or anything just yet.

Where can I find the log files?

---

