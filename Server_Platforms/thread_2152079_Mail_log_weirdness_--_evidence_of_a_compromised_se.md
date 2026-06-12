---
title: "Mail log weirdness -- evidence of a compromised server?"
date: 2013-06-06
forum: Server Platforms
---

### Post by compartment on 2013-06-06
I'm running the latest LTS version of Ubuntu on my hosting provider's cloud VPS service. I recently noticed a series of weird, spammy looking messages in my server's mail.log file. Tech support at my hosting provider says it does not appear to be compromised; are they wrong? I've had good experiences with them in the past, but I really doubt their assessment on this issue.


Here is a random example of what shows up when I run the command ```
grep -v notification mail.log.4 | grep \ to\= | head -1:
```
```
May 10 09:36:18 mono postfix/smtp[16752]: 7FE39198497: to=[REMOVED EMAIL ADDRESS FOR WEBMASTER at SEO DOMAIN], relay=[REMOVED SPAMMY URL and IPv4 ADDRESS]:25, delay=1.4, delays=0.02/0.01/0.88/0.48, dsn=2.0.0, status=sent (250 OK id=1UajkQ-0000sB-4j)
```


I shouldn't actually copy/paste the email addresses and URLs here, but trust me that they are super sketchy looking: SEO, weight loss, "golf tips 4 u", and unrecognized hotmail/gmail accounts. Am I misreading my mail logs, or is my server sending out emails to these super sketchy-looking addresses? 


These show up at a rate of only 5 to 10 a day; I would expect more outbound traffic if my machine was now moonlighting as an evil spam robot.

---

### Post by CharlesA on 2013-06-06
Sounds like the mail server might be configured incorrectly..

You could try checking with a tool like this:
[http://www.mailradar.com/openrelay/](http://www.mailradar.com/openrelay/)

---

