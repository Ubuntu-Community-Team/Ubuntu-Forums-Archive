---
title: "Server Ubuntu8.10- I Can't send mail with Postfix"
date: 2009-04-14
forum: Server Platforms
---

### Post by van-thuc on 2009-04-14
Hi Everyone, I need your help, Please!

mail.log file is empty, but auth.log has prolem

"... postfix/smtpd[2108]: auxprofunc error no mechanism available
 ...._sasl_plugin_load failed on sasl_auxprop_plug_init for plugin:sql"

and this is syslog file

Apr 14 22:22:35 svr73 postfix/smtp[2603]: connect to alt1.gmail-smtp-in.l.google.com[209.85.218.19]:25: Connection timed out
Apr 14 22:24:05 svr73 postfix/smtp[2604]: connect to alt4.gmail-smtp-in.l.google.com[209.85.199.114]:25: Connection timed out
Apr 14 22:24:05 svr73 postfix/smtp[2604]: 9460118A266: to=<bvidinli@gmail.com>, relay=none, delay=370250, delays=370100/0.02/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[209.85.199.114]:25: Connection timed out)

what must i do to fix the problem ??

---

### Post by iponeverything on 2009-04-14
I don't know this error is but I don't think it is related to your problem.

```
"... postfix/smtpd[2108]: auxprofunc error no mechanism available
...._sasl_plugin_load failed on sasl_auxprop_plug_init for plugin:sql"

```

can you ping alt4.gmail-smtp-in.l.google.com? Is other outside connectivity working on the server? The connection timeouts on port 25 with google appear to be your issue.

---

### Post by snakdoc on 2009-04-15
problem is google doesn't accept mail on part 25 that i know of pretty sure uses 587 and ssl ;)

---

