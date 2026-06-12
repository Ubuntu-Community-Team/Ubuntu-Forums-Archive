---
title: "How To Force Rewrite and Redirect Url"
date: 2015-04-24
forum: Server Platforms
---

### Post by hunterlove22 on 2015-04-24
[FONT=Helvetica Neue]I have a url:[/FONT]
[FONT=Helvetica Neue][http://domain.com/i.php?c=PT](http://domain.com/i.php?c=PT) and I Rewrote it to [http://domain.com/PT](http://domain.com/PT)successfully. But When I browse [http://domain.com/i.php?c=PT](http://domain.com/i.php?c=PT), it wont redirect to[http://domain.com/PT](http://domain.com/PT). Is there anyway to both redirect and rewrite it?[/FONT]
[FONT=Helvetica Neue]My .htaccess:

> [FONT=Verdana]RewriteEngine On[/FONT][/FONT]
RewriteCond %{QUERY_STRING} ^c=([a-zA-Z][a-zA-Z])$
RewriteRule ^/index.php$ /%1%2? [R=301,L]
[FONT=Helvetica Neue][FONT=Verdana]RewriteRule ^([a-zA-Z][a-zA-Z])$  i.php?c=$1$2 [NC,L][/FONT][/FONT][FONT=Helvetica Neue]
[/FONT]

---

### Post by hunterlove22 on 2015-04-24
Please anyone helps me.

---

### Post by matt_symes on 2015-04-24
Thread moved to **Server Platforms**.

@OP. You may have more luck getting an answer in this sub forum.

---

### Post by nerdtron on 2015-04-24
Doesn't the rewrite rules placed on the vhosts config file?

---

### Post by hunterlove22 on 2015-04-24
> **nerdtron said:**
> Doesn't the rewrite rules placed on the vhosts config file?

Nope. Just .htaccess only. It's shared hosting.

---

### Post by hunterlove22 on 2015-04-25
Please anyone helps me.

---

