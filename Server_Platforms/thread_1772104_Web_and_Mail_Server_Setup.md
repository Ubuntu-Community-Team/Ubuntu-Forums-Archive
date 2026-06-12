---
title: "Web and Mail Server Setup"
date: 2011-05-31
forum: Server Platforms
---

### Post by snoopy12533 on 2011-05-31
Hi I am looking for any useful information that can help get me upand running.  I am looking to host my own website and mail server from the server that I just set up.  I currently have the webserver up and running with ddclient and dyndns and everything is functioning perfectly except that I am not using my domain that i registered throw my comcast business account.  My biggest hurdle is that I unfortunately have a dynamic ip.  I have been looking into transferring my domain to dyndns but i would lose the exchange mail server through comcast so i need to set up my own mailserver.  I am not very familiar with linux I have used it off and on over the last 10 years so I apologize for acting like a noob.  What others steps do I have to perform on my server to get a mail sever up and running.

---

### Post by ruffEdgz on 2011-05-31
The first thing I would say to do would be to get a static IP if you can since you won't have to worry about your dynamic IP address changing on you when you least expect it. Of course, that will cost some extra money with your comcast business account (i looked into it myself and wasn't sold myself doing it through them so I went with an outside hosting company).

Its hard to really give you exactly what you need to do when it comes to mail configuration but the services that are available can help you complete some of the rest. I found a Ubuntu wiki on mail servers that might be able to help:
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

Link on how postfix works:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Another link on Email Services:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html)

Hope this helps.

---

