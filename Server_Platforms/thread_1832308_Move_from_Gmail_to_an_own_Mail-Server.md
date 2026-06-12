---
title: "Move from Gmail to an own Mail-Server"
date: 2011-08-24
forum: Server Platforms
---

### Post by optikfluffel_ on 2011-08-24
Hi :)
I've running my mails from 3 domains on Google Apps for several time, but I think it's time to set up my own Mail-Server now. I have a vServer and want to migrate my existing mails after setting it up. Now I have 2 questions.
1. Which components do I need / do you prefer for a mail-server(imap, smpt, webinterface)?
2. How do I get all my existing Mails in there?

Hope you can help me with that :)

---

### Post by allwimb on 2011-08-25
Under GNU/Linux I think the best solution is Postfix + courrier + amavisd-new + spamassassin + clamAv. check this link : [http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

About getting all existing mails do you mean the mail accounts or the mails ?

if it's mail accounts you'll have to recreate them. if it's mails you'll probably need to configure a mail client such as Thunderbird and get the mails into a database.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by robgr85 on 2011-08-25
Will allow You to modify mx dns records to point at Your server?

---

