---
title: "postfix help"
date: 2006-03-27
forum: Server Platforms
---

### Post by zovres on 2006-03-27
Hi, I am running a mail server and I am having an issue. I want people to be able to receive mail but not send from my server (I want them to use the smtp server of their provider so they just can't spam from my server).
I tried to comment out smtpd in master.cf and I was happy to see that I could not use the smtp server anymore but I soon realized that nobody could receive any mail either.
I also tried restricting smtpd to just certain ips but then postfix would not receive emails if they were not coming from these ips.
I have googled like crazy without luck. I would like to know why smtpd affect receiving (it seemed to me that smtp was for sending only). Lastly if someone could point me the parameter that I can change to disable sending from the server, it would help me not help the spammers (and I have a bunch).

Any help apreciated !

Thanks

Ben

---

