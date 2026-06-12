---
title: "Postfix &amp; email users database how to"
date: 2011-06-14
forum: Server Platforms
---

### Post by bsaidus on 2011-06-14
hello friends ::
I'm newbie in linux word ..:p
so .. I have installed ubuntu 10.04.2 LTS and followd  all the steps from the tutorial from 
[http://www.scribd.com/doc/31128654/Install-Guide-Ubuntu-10-04-LTS-Lucid-Lynx-Server-v1-7](http://www.scribd.com/doc/31128654/Install-Guide-Ubuntu-10-04-LTS-Lucid-Lynx-Server-v1-7)
, postfix and dovecot works fine ...;)

but ...
is there any way to create email accounts (postfix account) without creating linux accounts for each mail account ???
is there any tutorial about this .. ???
enlight me please 

thank you

---

### Post by collisionystm on 2011-06-14
> **bsaidus said:**
> hello friends ::
I'm newbie in linux word ..:p
so .. I have installed ubuntu 10.04.2 LTS and followd  all the steps from the tutorial from 
[http://www.scribd.com/doc/31128654/Install-Guide-Ubuntu-10-04-LTS-Lucid-Lynx-Server-v1-7](http://www.scribd.com/doc/31128654/Install-Guide-Ubuntu-10-04-LTS-Lucid-Lynx-Server-v1-7)
, postfix and dovecot works fine ...;)

but ...
is there any way to create email accounts (postfix account) without creating linux accounts for each mail account ???
is there any tutorial about this .. ???
enlight me please 

thank you


Pretty sure you need a user account for each mail account. Because the user is logging into the box every time they connect to receive or send mail.

---

### Post by bsaidus on 2011-06-14
I think there is a way ....
I was seeking and find this but in french 
[http://doc.ubuntu-fr.org/postfix_mysql_tls_sasl](http://doc.ubuntu-fr.org/postfix_mysql_tls_sasl)
it uses a mysql db to store all emails (postfix users account ) and avoid creating for each email a system account
:)

---

### Post by ruffEdgz on 2011-06-14
Maybe some of these might help:

[http://www.postfix.org/MYSQL_README.html](http://www.postfix.org/MYSQL_README.html) - basic information that postfix supplies

[http://hostingsoftware.net/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=56](http://hostingsoftware.net/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=56) - This looks a lot like the French page but in English

[http://bowe.id.au/michael/isp/postfix-server.htm](http://bowe.id.au/michael/isp/postfix-server.htm) - Its for CentOS but still might apply to your Ubuntu instance

Cheers!

---

### Post by bsaidus on 2011-06-15
thanks my friend...
I'll take a look
:popcorn:

---

