---
title: "Ubuntu Based Web Filter"
date: 2011-05-18
forum: Server Platforms
---

### Post by josh.scott on 2011-05-18
I need some help. I've never done anything like this before so I'm not even sure where to start. 
I am looking to build a Ubuntu based web filter. What we would like it to do is block access to certain sites for our company. We have had several employees get caught spending hours on end on gambling sites so we would like to restrict access to websites on a per user basis. 

What I am looking for is a piece of software or suite of software that can filter websites based on a blacklist/whitelist or category based scenario. I need to be able to authenticate users. For example I would like it so that when the CEO logs in he can go to whatever website he wants, while most other staff members are blocked from accessing things in the blacklist or categories.

I remember from a recent trip to a hospital that they had all internet traffic re-routed to their landing page and that you had to agree to specific terms on that page before you could do anything else. Something like that might be useful as well.

Any suggestions would be much appreciated.

---

### Post by Frizianz on 2011-05-18
Best thing would be to have a squid proxy server and run everything through it. Have it so you have to authenticate with the proxy server in turn you can then add different rules on a per user basis.

---

### Post by jaimerosario on 2011-05-20
[http://ubuntuforums.org/showthread.php?t=1725352&highlight=proxy+dansguardian+squid]("http://ubuntuforums.org/showthread.php?t=1725352&highlight=proxy+dansguardian+squid")

---

