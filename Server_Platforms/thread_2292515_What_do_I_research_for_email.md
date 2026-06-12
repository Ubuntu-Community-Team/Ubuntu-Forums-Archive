---
title: "What do I research for email"
date: 2015-08-28
forum: Server Platforms
---

### Post by jason_gibson2 on 2015-08-28
I am currently running a small server which direct boots to Kodi for htpc purposes. In the background it is functioning as my file server, transmission client, kvm host, and minecraft server. I would like to set up the ability for the server to email me when there is a problem of some kind. I can write scripts well enough to do that but I don't know where to start to give it the ability to send email. Preferably from my gmail address to my outlook address? Which packages primarily? I can google and read man pages I just don't know where to start for this. Any help or suggestions?

---

### Post by TheFu on 2015-08-28
[http://blog.jdpfu.com/2011/08/16/readers-ask-about-hosting-email](http://blog.jdpfu.com/2011/08/16/readers-ask-about-hosting-email)

Outbound email usually must be sent through an ISP email gateway with an authenticated connection. Direct port 25 outbound connections are usually blocked to prevent spamming.

It may be possible to have the MTA send to gmail using port 465/tcp and SMTPS - some people here do that, but if it happens too much, gmail is known to block those senders.

Anyway - hope that link helps even though it is about hosting email, not just sending outbound.

---

### Post by PaulW2U on 2015-08-28
*Thread moved to **Server Platforms**.*

---

### Post by jason_gibson2 on 2015-08-28
Found an article on ssmtp. Worked great.

---

