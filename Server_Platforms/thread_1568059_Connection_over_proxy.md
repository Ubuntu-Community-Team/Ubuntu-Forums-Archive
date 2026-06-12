---
title: "Connection over proxy"
date: 2010-09-04
forum: Server Platforms
---

### Post by fc90 on 2010-09-04
I have a problem with connecting over a proxy.

I would use w3m (for first tests) to connect to the internet.
I set http_proxy to [http://192.168.1.254:80](http://192.168.1.254:80)   (my proxy adress).
Also I see that w3m has in its settings the correct proxy settings.

But I could'nt load any page...

The proxy don't require any username and password. But the MAC and the IP must be ok (they are ok).

Must I configure something else?

Hope someone can help me. I'm running ubuntu server 10.04 LTS.

---

### Post by clrg on 2010-09-04
Does the proxy server work when you use it from another client?

---

### Post by fc90 on 2010-09-04
yes...but that is an windows client, that has an other IP and MAC...

But it is an idee to fake the mac on it, and try if it works.

---

### Post by fc90 on 2010-09-04
I tested it: Proxy works from Win with faking MAC.

---

### Post by clrg on 2010-09-04
If I understand correctly, you are using the proxy server to hide your mac address?

If so, that's unnecessary. Only someone in the same subnet as you will see your mac address. If you want to see the mac addresses of other clients, run

```
arp -a
```

---

### Post by fc90 on 2010-09-04
no. I don't want to hide the MAC.

The server only accepts me when I have a registred MAC and a for this registred IP.
If I have something else it won't work.

But that is not the problem. I have registred the MAC of my network adapter and also have set the IP correctly.

When I try it under Windows it works. It must be an problem in my linux config.

---

