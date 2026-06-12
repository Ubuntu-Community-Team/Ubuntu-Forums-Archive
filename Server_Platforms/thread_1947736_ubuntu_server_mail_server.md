---
title: "ubuntu server mail server"
date: 2012-03-27
forum: Server Platforms
---

### Post by augustkk on 2012-03-27
Hi, new to ubuntu.  I'm trying to set up a mail server following this how to:

[http://flurdy.com/docs/postfix/#config-simple](http://flurdy.com/docs/postfix/#config-simple)

I'm at the part that says MTA Postfix

I'm to edit this file: /etc/mailname

and put in smpt.domain.name

and in here: /etc/postfix/main.cf

I'm to put:
mail.example.com   and
myorigin=example.com

I'm not sure what to put in these values.

Any help greatly appreciated

---

### Post by nsnidanko on 2012-03-28
In the /etc/mailname put your server's FQDN. As for **myorigin**, depending on what function your server will be doiing i.e relaying email for or via someone else, etc. But to be safe put FQDN of the server as well. So basically all email comming from the server will be from someuser@myorigindomain[B].

[/B]

---

