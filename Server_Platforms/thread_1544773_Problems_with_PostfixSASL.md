---
title: "Problems with Postfix/SASL"
date: 2010-08-02
forum: Server Platforms
---

### Post by mmxbass on 2010-08-02
I have been faithfully following the postfix/sasl/etc install docs from [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/") and seem to have hit a minor snag with SASL authentication for SMTP. KMail cryptically leaves me with a generic auth fail notice and tailing the mail logs gives me
```
Aug  2 16:24:09 hypno1 postfix/smtpd[10427]: connect from c-76-23-129-55.hsd1.ct.comcast.net[76.23.129.55]
Aug  2 16:24:09 hypno1 postfix/smtpd[10427]: warning: SASL authentication failure: no secret in database
Aug  2 16:24:09 hypno1 postfix/smtpd[10427]: warning: c-76-23-129-55.hsd1.ct.comcast.net[76.23.129.55]: SASL CRAM-MD5 authentication failed: authentication failure
Aug  2 16:24:09 hypno1 postfix/smtpd[10427]: lost connection after AUTH from c-76-23-129-55.hsd1.ct.comcast.net[76.23.129.55]

```

I will provide any config files, db info, etc as requested if anyone could lend a hand.

---

### Post by lisati on 2010-08-03
One idea, from [http://www.irbs.net/internet/postfix/0402/2024.html](http://www.irbs.net/internet/postfix/0402/2024.html) :
> Check master.cf if smtpd runs chrooted.

---

### Post by mmxbass on 2010-08-03
> **lisati said:**
> One idea, from [http://www.irbs.net/internet/postfix/0402/2024.html](http://www.irbs.net/internet/postfix/0402/2024.html) :

I checked that out and it WAS chrooted BUT making it not anymore didn't fix the issue.

---

