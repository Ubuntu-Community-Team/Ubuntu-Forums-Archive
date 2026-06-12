---
title: "POSTFIX feature Help"
date: 2007-09-03
forum: Server Platforms
---

### Post by ftk_031 on 2007-09-03
Does any body there who implement the feature like eMPF in postfix or is there any way to implement something who can send mail to whom ie. restricting the sender to mail anywhere. Please even hints can be highly appreciated.

---

### Post by kwambus on 2007-09-03
Not sure exactly what you need here. However Postfix is extremely configurable when it comes to rules for incoming and outgoing mail messages. It's a large topic, and since I am not sure exactly what you need, I can only point you at the Postfix configuration file "main.cf" you will find this file in /etc/postfix/ normally.

"smtpd_recipient_restrictions" may be a place to start for you. As I said there is huge scope in Postfix to configure it to exactly what you need, unless you can be more exact I would point you at the Postfix documentation installed on your system or/and [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

---

