---
title: "php mail problem"
date: 2008-12-26
forum: Server Platforms
---

### Post by spikey83 on 2008-12-26
Hi all.

I have just built a server and put ubuntu lamp on it. i've been through the forum, ubuntu community help and other sites and i cannot get sendmail working.

All i'm trying to do is get php mail() function to work.

I have installed sendmail by doing "apt-get install sendmail"

Sendmail path in php.ini is set to "/usr/sbin/sendmail -t -i"

Could someone help me please as i've tried several guides and haven't got any to work yet.

Thanks.
Paul

---

### Post by jonabyte on 2008-12-26
so how do you know it does not work?

You may want to make sure your sever can actually send email by modifying the config files for send mail. For example, you will need some sort of smtp settings set.

---

### Post by spikey83 on 2008-12-27
It was just staying in the que after doing "mail [email]name@domain.com[/email] etc"

I've sorted it now though by using my own isp's smtp with exim4

---

