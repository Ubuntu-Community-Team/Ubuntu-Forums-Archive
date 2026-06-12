---
title: "Can't reach FQDN internally."
date: 2012-03-06
forum: Server Platforms
---

### Post by pepsifx357 on 2012-03-06
This is kinda a noob moment for me, but I can't seem to reach my website internally.  I can if I use it's netbios name or local ip though.  I'm not sure if this is specific enough to get answers, but I'm guessing the local DNS server is the problem?

Could anyone help me out on this?

---

### Post by papibe on 2012-03-06
Hi pepsifx357.

The ability to connect to a machine from your local network using its public name, or IP, is called **NAT loopback** (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")). Unfortunately most consumer routers don't support it.

The easiest way to test your setup using its public name is to go to a Internet cafe, public library, or even better, a friend's house. Another alternative is to use your pnone/tablet 3G connection (not WiFi).

Hope it helps.
Regards.

---

### Post by Sergius14 on 2012-03-07
Your issue is typical...

As already said, most consumer routers don't allow you to have a dns helper / dns rewrite, etc.

What you can do is to edit the local /etc/hosts file and insert there a local translation ip - fqdn on each PC/Server.

It would be the really easiest way without going anyplace.

---

### Post by pepsifx357 on 2012-03-08
I can understand consumer stuff, but we're on a comcast business connection using their modem with a static IP.

Basically it's Lan->Server->Comcast-Modem

---

### Post by Habitual on 2012-03-08
> **Sergius14 said:**
> ...edit the local /etc/hosts file ...

```
127.0.0.1 pepsifx357.com
or
Pri.vat.eIP pepsifx357.com

```now pepsifx357.com will resolve to your local machine.

Other systems, edit /etc/hosts and use 

```
Pri.vat.eIP pepsifx357.com
```

---

