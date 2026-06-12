---
title: "Postfix troubles"
date: 2014-08-09
forum: Server Platforms
---

### Post by preston3 on 2014-08-09
Hello,

I have installed postfix so my website can send confirmation emails to clients. The problem though is wordpress can not connect to the server even though postfix is running and wordpress is configured to look at the server. what have i done wrong? what do i need to do?

---

### Post by SeijiSensei on 2014-08-09
Are both applications running on the same machine?  Are you using the localhost interface?  By default, Postfix on Ubuntu will only accept requests arriving on 127.0.0.1.  See the [mynetworks](http://www.postfix.org/postconf.5.html#mynetworks) directive in main.cf.

---

### Post by preston3 on 2014-08-11
both are running on the same machine and i believe it is set on the localhost interface.

---

### Post by SeijiSensei on 2014-08-11
What do you see in /var/log/mail.log when you try to send a message?

---

