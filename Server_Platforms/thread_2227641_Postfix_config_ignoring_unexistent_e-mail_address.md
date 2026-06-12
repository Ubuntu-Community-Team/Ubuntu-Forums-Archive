---
title: "Postfix config ignoring unexistent e-mail address"
date: 2014-06-03
forum: Server Platforms
---

### Post by avaserver on 2014-06-03
How can i make postfix to ignore non-existing (or wrong) e-mail addresses when sending mail to many e-mail addresses at once (BCC).
I want to make a mail marketing campaign and i dont know if all the mails from my database are real or realy exist.

For example if want to send a mail to 20 mail addresses and the address number 15 is a wrong address, how can i make postfix to ignore that address and continue to send to next email addresses from the list.

Actually my postfix stucks when an e-mail address is wrong and i can`t send or receive e-mails from thunderbird from that accound (e.g. [email]office@mydomain.com[/email]).
I have to postconf -d ALL then restart postfix to make it work again.

Please advice !
Thanks in advance. Good day !

---

