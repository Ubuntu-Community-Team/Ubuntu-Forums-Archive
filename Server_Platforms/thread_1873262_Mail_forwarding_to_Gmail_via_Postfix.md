---
title: "Mail forwarding to Gmail via Postfix"
date: 2011-11-01
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-11-01
Have mailforwarding setup at [www.zoneedit.com](www.zoneedit.com) as:-

[email]me@mydomain.com[/email] > [email]myname@gmail.com[/email]

Would like to setup wildcard forwarding whereby setup becomes:-

*@mydomain.com > [www.mydomain.com](www.mydomain.com) > [email]myname@gmail.com[/email]

This would allow any name you like @mydomain.com to be forwarded to the single gmail.account.

This would be the sole function in Postfix, the redirection of mail.

Do-able in Postfix - if so suggestions please?

TIA

---

### Post by lisati on 2011-11-01
Apologies, I had a detailed reply typed up but accidentally cleared it before submitting. It is definitely "do-able". Among the options is [check_recipient_access]("http://www.postfix.org/postconf.5.html#check_recipient_access").

---

### Post by ChrisRChamberlain on 2011-11-01
lisati

Thanks for your reply - would appreciate any further info you have.

---

### Post by lisati on 2011-11-01
If I have understood what you want to do properly, it is a form of address rewriting within Postfix, which is described here: [http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html)

---

### Post by ChrisRChamberlain on 2011-11-01
Thanks again lisati

This article also seems to cover what is required

[http://www.debuntu.org/2006/05/05/45-how-to-postfix-and-virtual-hosts]("http://www.debuntu.org/2006/05/05/45-how-to-postfix-and-virtual-hosts")

Not familiar with the use of the word 'hash:'

```
virtual_alias_maps = hash:/etc/postfix/virtual
``` here

---

