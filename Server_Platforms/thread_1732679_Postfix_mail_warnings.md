---
title: "Postfix mail warnings"
date: 2011-04-18
forum: Server Platforms
---

### Post by MightyMe on 2011-04-18
A while back I started to get a couple of warnings each day in /var/log/mail.warn which looks like

```
Apr 18 05:49:18 Server1 postfix/smtpd[20349]: warning: 201.245.187.181: hostname corporativos_245187-181.etb.net.co verification failed: Name or service not known
```

Is this attempts to send SPAM mail which my server is blocking or is this something else I should look into? I have set up a secure mail server according to the Ubuntu Server guide with TLS and all that.

---

### Post by Doug S on 2011-04-18
Yes, it is most likely an attempt to deliver an undesired e-mail from some undesired source.
The actual warning message is (I think) because the forward and reverse name look ups did not work. Upon the new connection from 201.245.187.181 Postsifx first does a name server lookup and gets the answer "corporativos_245187-181.etb.net.co". Then postfix does a name server lookup of "corporativos_245187-181.etb.net.co", but the reply is something like "No such name". Typically we expect a legitimate MTA (Mail Transport Agent) to have forward and reverse name lookups work properly. Postfix makes the log entry, but still allows the connection (at least with the default postfix settings).
If you also look at your mail.log file for the same time, you should also see some entries, and a note if the mail actually got delivered. On my system, if the destination is address is valid, the e-mail does get through.

---

### Post by MightyMe on 2011-04-19
Thanks for the clarification. I glad it looks like my mail server is set up properly.

---

