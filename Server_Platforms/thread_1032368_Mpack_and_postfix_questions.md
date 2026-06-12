---
title: "Mpack and postfix questions"
date: 2009-01-06
forum: Server Platforms
---

### Post by jtesolin on 2009-01-06
Good day,

We are using post fix on our server, we have it correctly set up to send mail from bash scripts.

Is there a way to change the reply-to address? 

Also, mail keeps getting sent to [email]username@gmail.com[/email], is that because for mydestination, I have the localhost information?


mydestination = [email]myaddress@gmail.com[/email], localhost.localdomain, localhost
myusername@Black Pearl [email]ebusinesssupport@gmail.com[/email]

mpack -s "Subject here" backup.zip [email]altaddress@gmail.com[/email]

---

