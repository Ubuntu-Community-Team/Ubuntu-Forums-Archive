---
title: "postfix not sending emails - please help"
date: 2010-01-18
forum: Server Platforms
---

### Post by dattu on 2010-01-18
dear folks,

i'm not a techie but have tried my best to solve the issue without success. I have a static IP from local ISP and my computer is configured with 192.168.1.2 (LAN IP).

I have installed ubuntu server 9.04 and want to send emails from my server for which I've configured postfix. But I dont know what to do next.

My questions are:

1. Do i need to install DNS server for using postfix? If not, what should I install to send emails from this server?
2. Do I need to forward any particular port in my router?
3. If I dont have a fully qualified domain, what are the configurations I need to do to send emails?

please help!!!a

---

### Post by munky99999 on 2010-01-18
> 1. Do i need to install DNS server for using postfix?
Not a dns server no.

> 2. Do I need to forward any particular port in my router?
smtp uses port 25. 

> 3. If I dont have a fully qualified domain, what are the configurations I need to do to send emails?
Without a fqdn you're email will be like munky@66.65.55.1


9/10 times though it most likely wont be your problem. Most ISPs block port 25 to squash potential spam coming from their network.

That's probably the problem.

---

