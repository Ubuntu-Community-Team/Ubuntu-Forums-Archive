---
title: "postfix"
date: 2011-04-04
forum: Server Platforms
---

### Post by Vegan on 2011-04-04
So I have postfix setup as an internet site, what else do I need to get the mail working?

---

### Post by domu on 2011-04-04
nothing if you just want to send emails, with the proviso that your outgoing emails might get blocked by outside servers because they don't come from a recognised mail server.

try it thus:```

echo "this is a test"|mail -s "Test subject" your@mailaddress.net
```

and see if you receive it!

---

### Post by Vegan on 2011-04-04
sent that to my hotmail account, nothing

---

### Post by usatonycuba on 2011-04-05
> **Vegan said:**
> So I have postfix setup as an internet site, what else do I need to get the mail working?

 More info will be helpful like your Incoming and Outgoing Mail Server Settings ... I guess ..

 On the other hand, Hot-mail does not receive email from your email sever, because it recognizes as span .. do you have static IP, valid registered domain? ...

 You can check those link's

[http://ubuntuforums.org/showthread.php?t=614257](http://ubuntuforums.org/showthread.php?t=614257)

[URL="http://www.emailaddressmanager.com/tips/mail-settings.html"]http://www.emailaddressmanager.com/tips/mail-settings.html
[/URL]

---

### Post by fonsi2099 on 2011-04-06
Do I need Postfix?? I am using ubuntu as a personal desktop.
Thank you :)

---

### Post by usatonycuba on 2011-04-06
> **fonsi2099 said:**
> Do I need Postfix?? I am using ubuntu as a personal desktop.
Thank you :)
Don't  follow you....
Postfix is a mail transfer agent (MTA) program, if you choose to use (set) an MAIL server, you should have one (MTA) I meant.

---

