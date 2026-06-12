---
title: "Postfix Mysql Auth removes domain name"
date: 2010-06-30
forum: Server Platforms
---

### Post by uncleLaz on 2010-06-30
Hi All,

I am having a problem getting postfix to authenticate using Mysql and saslauthd

It is set up mainly as an outgoing smtp server, but when it authenticates a user it drops the domain name from the username.

For example, if I set the username as [email]user.name@mydomain.co.uk[/email], the query fired to mysql is

select password from users where username = 'user.name.co.uk'

It is dropping the @mydomain

Anyone come across this before???

Thanks in advance


Uncle Laz

---

