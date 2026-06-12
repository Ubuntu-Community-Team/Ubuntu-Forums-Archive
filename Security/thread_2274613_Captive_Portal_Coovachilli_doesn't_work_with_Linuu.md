---
title: "Captive Portal Coovachilli doesn't work with Linuux kernel"
date: 2015-04-21
forum: Security
---

### Post by vincent28 on 2015-04-21
Hi everybody,

I'm setting up a captive portal with Coovachilli 1.3 and FreeRadius on an ubuntu server 14.04 LTS (32 or 64 bits, I tested both) and some of my clients can't access to the authentication web page. These clients work with Ubuntu/Debian or Androïd (so in mobile devices). In opposite, Windows and Mac/iOS clients can log and access to Internet.

I tried all of theses things :

 - Allow ALL the traffic in the firewall client and server
- try differents browers and differents OS (GNU/Linux and even Androïd version)


In packets analyse, I saw with PacketTracer a lot of packets which were captured with a connection from a windows client (HTTP, TCP, Data Packets etc...). But with Ubuntu, Debian, Androïd, nothing.

Do you have any idea concerning my problem please ? I really don't see what is the problem's source ...

Thank you very much,

---

