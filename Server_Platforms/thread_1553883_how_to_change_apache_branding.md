---
title: "how to change apache branding"
date: 2010-08-15
forum: Server Platforms
---

### Post by fro1269 on 2010-08-15
Whenever i am viewing a directory on my Ubuntu LAMP server that does not have a index.html file it of course tells me


Apache/2.2.14 (Ubuntu) Server at example.com Port 80

How can I modify that branding to say something else? I have tried to google / forum search but I do not think I am using the correct keywords to find the info I am looking for. thanks in advance

---

### Post by bodhi.zazen on 2010-08-15
mod_security will do that for you.

Otherwise, you will need to recompile apache.

See :

[http://www.petefreitag.com/item/505.cfm](http://www.petefreitag.com/item/505.cfm)

so you can set your serer tokens to production, and that will help.

[http://www.mydigitallife.info/2007/07/22/improve-apache-web-server-security-use-servertokens-and-serversignature-to-disable-header/](http://www.mydigitallife.info/2007/07/22/improve-apache-web-server-security-use-servertokens-and-serversignature-to-disable-header/)

---

### Post by fro1269 on 2010-08-17
thanks a bunch! this answered all of my questions. marking as [SOLVED]

---

