---
title: "Postfix -forward email if user is not existed."
date: 2008-12-29
forum: Server Platforms
---

### Post by qirun on 2008-12-29
Hello,

I just wondering if Postfix can handle any incoming email from local network, and if the user is not existed it would try to look on the external mail server.
Let say we have postfix server that serving 5 user in our local network (domain localmail.xyz.com). And by the time oe or more user are trying to send an email to non-existences user, th postfix wold try to forward the email through  smtp.xyz.com which is hosted on the different server (paid hosting server).

Is it possible to do?

Thanks for your help...

---

### Post by volkswagner on 2008-12-29
This can be done with alias.  How you implement it will depend how you set up your mail server.

I used the [Flurdy]("http://flurdy.com/docs/postfix/") how to.  The alias entries go into the mysql database under aliases.

You can send the mail to any internal user or external address.

---

### Post by qirun on 2008-12-29
Thanks, So I need to concentrate on the mysql and alias. Hope this info will give some light...

My postfix configuration must be simple.

I have a domain name example.org and as default the smtp is also example.org
Then I have my own internal mail server that work on postfix. and assigned it as gateway.example.org therefore the mx also is gateway.example.org.
I activate the relay to my external mx which is example.org.

I dont want to create the whole user on my own postfix server as feel that is way to much.The external user that work direct on the example.org is about twice of the number that postfix served.

But if this thing not gonna work I might need to create the whole external user on the internal machine and then forward the email.

This is my first time I setting up the postfix. So definitely I'm just noob.

Cheers...

---

