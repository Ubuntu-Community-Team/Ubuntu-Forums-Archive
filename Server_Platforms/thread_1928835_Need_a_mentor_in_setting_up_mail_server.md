---
title: "Need a mentor in setting up mail server"
date: 2012-02-20
forum: Server Platforms
---

### Post by devxdev on 2012-02-20
Basically I am lost, I just bought a new server to replace a server that was incompatable with Ubuntu. It was solely my mail server running Mercury32. Simple to install but lacked security/help/documentation that I require.
Right now my entire mail server has been down for almost a week due to a hacking spree, I've been constantly blocking by IP but he's behind a proxy so it's different constantly. Its really hurting my rep, because I host SMTP relaying for a few non profit churches/schools. But that's another story long story short there windows does NOT offer a solution for me.

My status right now is, I have postfix installed, ?configed? As well as Dovecot. I have gone from start to end on both of their help.Ubuntu.com/..... docs.
I can telnet localhost 25, 110, etc, as well as the secure ports. ehlo does not give errors.
But if I try to login via thunderbird I keep getting the plaintext login not allowed.

Also where do I specify that my SMTP relays smtp.comcast.net?
Need any more details like postfix/Dovecot -n or what ever other magical commands just let me know. I'm oof ATM I'm on mobile or I would just post it. 
Please note I am an intermediate user, but I do know how to use google so go ahead and be technical I love to learn :D

---

### Post by acc61287 on 2012-02-21
> **devxdev said:**
> Basically I am lost, I just bought a new server to replace a server that was incompatable with Ubuntu. It was solely my mail server running Mercury32. Simple to install but lacked security/help/documentation that I require.
Right now my entire mail server has been down for almost a week due to a hacking spree, I've been constantly blocking by IP but he's behind a proxy so it's different constantly. Its really hurting my rep, because I host SMTP relaying for a few non profit churches/schools. But that's another story long story short there windows does NOT offer a solution for me.

My status right now is, I have postfix installed, ?configed? As well as Dovecot. I have gone from start to end on both of their help.Ubuntu.com/..... docs.
I can telnet localhost 25, 110, etc, as well as the secure ports. ehlo does not give errors.
But if I try to login via thunderbird I keep getting the plaintext login not allowed.

Also where do I specify that my SMTP relays smtp.comcast.net?
Need any more details like postfix/Dovecot -n or what ever other magical commands just let me know. I'm oof ATM I'm on mobile or I would just post it. 
Please note I am an intermediate user, but I do know how to use google so go ahead and be technical I love to learn :D

May be I can help you, but I'm not ubuntu geek:)
I'm using PostfixAdmin, postfix, dovecot, squirrelmail, webmin (for monitoring) apache2 for web hosting
try to read this link then ask a question:)
[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)
[http://postfixmail.com/blog/index.php/postfixadmin-on-ubuntu-9-10/](http://postfixmail.com/blog/index.php/postfixadmin-on-ubuntu-9-10/)
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

---

### Post by devxdev on 2012-02-21
Thanks for the links the second one looks like it might help a lot I guess I forgot to mention in the first post that I already have my web server on a different machine (no help needed with regards to apache/MySQL/php work with those on a daily basis). I'll update agin if I need more help

---

### Post by acc61287 on 2012-02-21
> **devxdev said:**
> Thanks for the links the second one looks like it might help a lot I guess I forgot to mention in the first post that I already have my web server on a different machine (no help needed with regards to apache/MySQL/php work with those on a daily basis). I'll update agin if I need more help

I thought you're configuring single machine, because in my case I'm only using 1 server (our company had no budget:D).

---

### Post by HermanAB on 2012-02-22
You could install Citadel.  It takes about 20 minutes.  It does everything and supports all secure (and insecure) mail protocols.

---

### Post by Holdolin on 2012-02-22
> **HermanAB said:**
> You could install Citadel.  It takes about 20 minutes.  It does everything and supports all secure (and insecure) mail protocols.

Thanks for the idea.  I know I wasn't the one originally looking for this answer, but was myself wanting to set up a mail server. The extras it provides are icing on the cake  :)

---

### Post by devxdev on 2012-03-19
> **HermanAB said:**
> You could install Citadel.  It takes about 20 minutes.  It does everything and supports all secure (and insecure) mail protocols.

Thanks sorry for the late reply, I'll hop on that in the AM

---

