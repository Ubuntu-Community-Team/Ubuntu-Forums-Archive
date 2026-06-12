---
title: "Show username when there is SASL authentication failure"
date: 2018-09-28
forum: Server Platforms
---

### Post by kladizkov on 2018-09-28
I'm using postfix and cyrus-sasl.


When ever there is an authentication failure it reports in maillog below line.


postfix/smtpd[27669]: warning: unknown[185.xxx.xxx.xxx]: SASL LOGIN authentication failed: authentication failure


How can I make it so that it will also report the username that failed in the log file ( like SASL LOGIN authentication failed: authentication failure for alice )?

---

### Post by kladizkov on 2018-10-14
Any one?

---

