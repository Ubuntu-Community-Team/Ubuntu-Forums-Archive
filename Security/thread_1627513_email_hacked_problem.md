---
title: "email hacked problem"
date: 2010-11-21
forum: Security
---

### Post by yashar on 2010-11-21
hello,
sorry this is not related to os but i dont know where else i could post it.

today i was ask to assist to solve this issue:

MR.john send email from web page of mail.company.com from [email]john@company.com[/email] to [email]nancy@anothercompany.com[/email] , but nancy received an abuse file attachment from [email]john.company@rocketmail.com[/email] which deleted all data.

this happen for all email addresses of company.com and not always. the company.com admin is fired and then these happened!! ;)

they checked email address aliases, used new os, reset routers but the problem is still there, any suggestion?

---

### Post by e79 on 2010-11-21
I would personally look at the mail server configuration, not the client and make sure there is no suspects user-forwards/MTA-relays. Also make sure your DNS MX records are still pointing where they should.

just my $0.02

---

### Post by yashar on 2010-11-21
thank you, mx is correct but i need to check email config more

---

### Post by HermanAB on 2010-11-22
Yup, you need to get into the mail server.

---

