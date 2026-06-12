---
title: "how to block https traffic with Squid"
date: 2011-04-04
forum: Security
---

### Post by mkhurram92 on 2011-04-04
hi there

i have install squid on ubuntu in my environment and everything is going well but even after blocking some site they are open like

[https://www.facebook.com](https://www.facebook.com)
[https://www.youtube.com](https://www.youtube.com)

So how i can block these site with Squid or any other software ???

Please Guide

---

### Post by bodhi.zazen on 2011-04-04
> **mkhurram92 said:**
> hi there

i have install squid on ubuntu in my environment and everything is going well but even after blocking some site they are open like

[https://www.facebook.com](https://www.facebook.com)
[https://www.youtube.com](https://www.youtube.com)

So how i can block these site with Squid or any other software ???

Please Guide

I would use iptables:

```
sudo iptables -A OUTPUT --dport 443 -j DROP
```

Although that will block legitimate https traffic as well.

If you want to go site - by - site you can use squid to black list all https and white list allowed sites.

Look at tools such as squidguard.

---

### Post by mkhurram92 on 2011-04-04
Hi thanks for ur reply !

U mean I have to create an acl block it and have to putt all https site URL in that acl ???
I think I already done it but no result :(

---

### Post by bodhi.zazen on 2011-04-04
> **mkhurram92 said:**
> Hi thanks for ur reply !

U mean I have to create an acl block it and have to putt all https site URL in that acl ???
I think I already done it but no result :(

Yes that is what you do.

If it is not working, are you running https through squid ?

---

### Post by mkhurram92 on 2011-04-04
> **bodhi.zazen said:**
> Yes that is what you do.

If it is not working, are you running https through squid ?

I really don't know about that I m running https through squid or not :(

Can u guide me how I can check that ????

Thanks for help

---

### Post by AlexanderDGreat on 2011-11-01
Any follow up how to know if I'm running HTTPS on Squid?

---

### Post by mkhurram92 on 2011-11-01
> **AlexanderDGreat said:**
> Any follow up how to know if I'm running HTTPS on Squid?

Well AlexanderDGreat

If you are able to tell then pls tell me ???

---

