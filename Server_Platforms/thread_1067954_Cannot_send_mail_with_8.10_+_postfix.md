---
title: "Cannot send mail with 8.10 + postfix"
date: 2009-02-12
forum: Server Platforms
---

### Post by Glock24 on 2009-02-12
I'm setting up a mail server for a small company with Ubuntu 8.10 and postfix.

Everything is working, but I cannot send mail, I get errors like this:

```
Feb 12 11:25:28 mail postfix/smtp[4709]: 7C53F35BAC: to=<johndoe@gmail.com>, relay=alt2.gmail-smtp-in.l.google.com[209.85.221.184]:25, delay=946, delays=0.12/0.01/946/0, dsn=4.4.2, status=deferred (lost connection with alt2.gmail-smtp-in.l.google.com[209.85.221.184] while receiving the initial server greeting)

Feb 12 11:30:26 mail postfix/smtp[5081]: A6ECB35BB3: lost connection with alt1.gmail-smtp-in.l.google.com[72.14.221.114] while receiving the initialserver greeting
```

Those are test emails to a google account, and as you can see, the messages are not delivered. Local delivery works, but sending to a remote host does not.

Am I missing some parameter in the config file? Any hints or ideas?

Thank you.

Is there something I'm missing in the server configuration?

---

### Post by HermanAB on 2009-02-12
Most mail server trouble are due to a bad DNS configuration.  Ensure that you have A, PTR and MX records.

Cheers,

Herman

---

### Post by Glock24 on 2009-02-13
I'll check that.

Thank you.

---

