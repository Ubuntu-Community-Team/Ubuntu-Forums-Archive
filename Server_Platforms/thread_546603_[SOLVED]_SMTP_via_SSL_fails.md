---
title: "[SOLVED] SMTP via SSL fails"
date: 2007-09-09
forum: Server Platforms
---

### Post by cjsimmons on 2007-09-09
I've just converted my mail server from a Windows box to Ubuntu Server 7.04. I've got most of it up and running bar a few bugs here and there. Nothing to worry about except that I can't send mail using SSL.

I've followed [this guide]("http://flurdy.com/docs/postfix/") to get it all up and running, using posfix and courier and just decided to add authentication to the server.

They way I have it now is that I can send mail with out SSL, but can't with SSL. Also, if I try to connect using using the domain rather then the IP address I can't do either.

Would this have anything to do with restrictions in /etc/postfix/main.cf??

Let me know if you need any more info or any files, I'm only new to this, and I'm still learning. Any help would be greatly appreciated.

----
UPDATE: I've decided to set up my mail clients to use my ISP's outgoing mail server. It's all working great now.
----

---

