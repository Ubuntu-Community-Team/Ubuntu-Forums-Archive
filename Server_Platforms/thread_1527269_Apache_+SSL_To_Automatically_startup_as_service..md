---
title: "Apache +SSL To Automatically startup as service."
date: 2010-07-09
forum: Server Platforms
---

### Post by infamous-online on 2010-07-09
Hello all, 

The problem I'm having is quite simple. I've been custom compiling apache for years without problems until now, and the problem I'm having seems to be over my head. I've never built SSL into any of my builds because at the time I didn't need it then. but now I have to, since I'll be dealing with sensitive records and such that will require ssl. I can't get apache started automatically as a service with ssl enabled. Without ssl the startup script works just fine, but how can modify the apachectl script so the server can process non secure and secure layers aka ssl at the same time?

---

### Post by cdenley on 2010-07-09
Does your SSL key require a password? If so, then apache cannot start until you enter the password.
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/582963](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/582963)
If you have a password but don't need it, remove it.
[http://www.madboa.com/geek/openssl/#key-removepass](http://www.madboa.com/geek/openssl/#key-removepass)

---

