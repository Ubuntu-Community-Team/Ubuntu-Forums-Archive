---
title: "Ubuntu Server. Static IP Changed"
date: 2009-11-28
forum: Server Platforms
---

### Post by jeromemt on 2009-11-28
I use ubuntu 9.04 server. My static ip changed. I can access ispconfig and phpmyadmin, but i can't access my web sites. I don't find any options for this problem.

---

### Post by Aearenda on 2009-11-28
Not really sure what your question is - if you want to know where a static IP address is set, it's in /etc/network/interfaces.
Something like this should let you edit it at the console: ```
sudo nano /etc/network/interfaces
```

---

### Post by wojox on 2009-11-28
Port forwarding on your router?

---

### Post by lisati on 2009-11-28
> **jeromemt said:**
> I use ubuntu 9.04 server. My static ip changed. I can access ispconfig and phpmyadmin, but i can't access my web sites. I don't find any options for this problem.

Are you referring to an IP on your own network our the one with which you connect to the internet?

---

### Post by Aearenda on 2009-11-28
Or maybe ACLs in your Apache configs, or your firewall config? Tell us more!

---

### Post by jeromemt on 2009-11-28
thank you for your help.
i found my problem. i'm using everydns. i forgot it.

---

### Post by Iowan on 2009-11-28
Is it [SOLVED]?
(Thread Tools) :p

---

### Post by xx58 on 2009-11-28
:rolleyes:I have exactly same problem, after I set up Static IP Address, I cannot connect to Web?
You write you resolve your problem and you forget you use " EveryDNS". What that mean and where is solution?

---

