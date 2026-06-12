---
title: "Does postfix relay mail?"
date: 2009-05-22
forum: Server Platforms
---

### Post by Johnsie on 2009-05-22
Hi, I'm thinking about pointing my MX record to my server and opening port 25 so it can recieve mail. My by biggest fear is that someone from outside would connect and send mail using the postfix smtp server I am running on my machine.

Obviously I dont want random people to be able to use my smtp. Does anyone here know any good ways to make sure this cannot happen.


Thanks alot,

John

---

### Post by dipeshmehta on 2009-05-22
Hello,

You can use authentication for the use of smtp.  Look for a nice howto by falko at howtoforge.com 

Hope this helps.

Dipesh

---

### Post by mellowd on 2009-05-23
It can get quite involved, but it's possible to prevent just about anyone from relaying through your smtp server. Most allow you to set up just a few (or 1) domain to relay for.


Whatever you do though, I would suggest wiring a script that automatically checks the queue every so often (via a cronjob) and emails you any high numbers which would point to a compromise

---

### Post by Dr Small on 2009-05-23
You can setup postfix to relay mail with authentication, if you needed to be able to relay mail to the server from outside of your local network:
[http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582)

But otherwise, if you are only going to be relaying mail from inside the network, there is no need to do this.

---

