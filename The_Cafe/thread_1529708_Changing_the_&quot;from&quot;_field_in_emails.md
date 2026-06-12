---
title: "Changing the &quot;from&quot; field in emails"
date: 2010-07-12
forum: The Cafe
---

### Post by goseph on 2010-07-12
Hi all!

I have purchased a domain and got gmail to set the "from" field in my sent messages so as to appear to be sent from my purchased domain. Unfortunately, it actually only says "from: [email]me@gmail.com[/email], sent on behalf of [email]me@mydomain.com[/email]"

Is there an email provider or a way in gmail of making it simply say: "from: [email]me@mydomain.com[/email]" ?

Thanks!

Luke

---

### Post by sandyd on 2010-07-12
set up your domain with google apps

---

### Post by urukrama on 2010-07-12
I believe Zoho Mail does that.

---

### Post by WRDN on 2010-07-12
It's up to the program sending the email to set the from and to address (etc) before passing it to another program like sendmail/postfix/exim4. 
For example, if you used the program Mutt to send the emails, you can set the from address by placing following text in the ~/.muttrc file:

```
set from="me@mydomain.com"
```

---

