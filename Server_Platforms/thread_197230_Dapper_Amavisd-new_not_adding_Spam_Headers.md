---
title: "Dapper: Amavisd-new not adding Spam Headers"
date: 2006-06-15
forum: Server Platforms
---

### Post by ScatterBrain on 2006-06-15
I've setup a Dapper Mail Filerting Gateway based on this howto:

[http://www200.pair.com/mecham/spam/spamfilter20050626.html]("http://www200.pair.com/mecham/spam/spamfilter20050626.html")

I've tried my best to manipulate this howto into the new amavisd-new configuration file scheme put in place by the Debian/Ubunut maintainers [COLOR=Green](Anyone know why did this happen by the way?)[/COLOR]

Everything seems to be working, except that I'm not getting the X-Spam: headers attached to my emails and I like to forward the "detected" e-mails - SPAM or otherwise to particular mailbox, all of the detected mails are going to a quarantine file on the gateway.

Does anyone know how to correct these problems?  I've attached my amavisd.conf file if that helps anyone.

---

### Post by ScatterBrain on 2006-06-15
Never mind...I just needed to put all of my changes into /etc/amavis/conf.d/50-user instead of the /etc/amavis/amavisd.conf.

---

