---
title: "[Postfix] Store and Forward Messages"
date: 2008-10-27
forum: Server Platforms
---

### Post by ngmachado on 2008-10-27
Hi,

Fortunatelly I've setup a Postfix Mail Server correctly. I'm using virtual users in a MySQL database.

I've 3 tables: domain, users and forwards.

```


select * from domain;
mydomain.com

select * from users;
mail | password
admin@mydomain.com | encrypted_password

select * from forwards;
source | destination
@mydomain.com | admin@mydomain.com


```

This way I created a catch-all mail since mydomain.com is a personal domain, so no users. If I send a mail to [email]someone@mydomain.com[/email] I get it in [email]admin@mydomain.com[/email]. 

Now I want to forward all incoming mail to a backup gmail account, so I added the following line in forwards table:

```

select * from forwards;
source | destination
@mydomain.com | admin@mydomain.com
admin@mydomain.com | backup@gmail.com

```

The problem is... messages are forwarded to gmail but they don't stay in my server!!

Can someone give me a hint on how to solve this problem? I'd really appreciate that.

---

