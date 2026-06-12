---
title: "mail server configuration problem"
date: 2010-06-16
forum: Server Platforms
---

### Post by i.sinister on 2010-06-16
good morning/day/evening/night everybody.
i need help in setting up mail server. i have 3 domain names **foo.com**, **bar.com**,**bar.com.de**. there is a mx-record just for **foo.com - mail.foo.com**. i am sending emails from **bar.com**/**com.de** using that email server. And emails always go to spam. I guess its because email contains links back to the **bar.com/com.de**, but email server used to sent was **mail.foo.com**. plus if to open original email at the mailbox there will be SPF error or neutral status reported (it changes). is there a way to configure email server to make sure email are trusted or i should setup 3 different email servers for each domain?

thank you

---

### Post by Bachstelze on 2010-06-16
> **i.sinister said:**
> good morning/day/evening/night everybody.
i need help in setting up mail server. i have 3 domain names **foo.com**, **bar.com**,**bar.com.de**. there is a mx-record just for **foo.com - mail.foo.com**. i am sending emails from **bar.com**/**com.de** using that email server. And emails always go to spam. I guess its because email contains links back to the **bar.com/com.de**, but email server used to sent was **mail.foo.com**. plus if to open original email at the mailbox there will be SPF error or neutral status reported (it changes). is there a way to configure email server to make sure email are trusted or i should setup 3 different email servers for each domain?

thank you

Watch your mail logs, maybe you'll have some warnings there. If you want, send an email to firas AT fkraiem org, I'll tell you what SpamAssassin says about it.

---

