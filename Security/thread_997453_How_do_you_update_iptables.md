---
title: "How do you update iptables"
date: 2008-11-29
forum: Security
---

### Post by shqip on 2008-11-29
Anybody! I want to upgrade from version v1.3.8 to the latest one.  By the way, what does this command mean to you guys.   sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT  Does it mean please leave the back door open?   Thanks

---

### Post by kevdog on 2008-11-29
This is not a security risk.  If you read up on ip packets, part of the header of these packets are established connections.  The firewall as you reported does not allow any new connections, however once a connection is established, it does allow for further packets from the source to be passed.  If your not allowing any new packets in on the firewall this isn't an issue.  If you are allowing open ports, I'm betting you want to further allow packets once a connection is established.  

You can experiment and simply comment these lines and see what happens.  Ive done this by mistake and it took me a long time to realize what I had done.

---

### Post by lovinglinux on 2008-11-30
You actually need that rule to be able to browse the Internet. If you remove it, you won't be able to see any web site.

What happens is that when you try to access a web site, your machine send a packet with the connection request and the site respond with another packet acknowledging your connection intent, then the connection is established and data transfer takes place. If you remove that rule, you won't be able to receive the web site response, so the connection will never be established and you won't get the web site content.

---

### Post by shqip on 2008-11-30
...

---

### Post by markharding557 on 2008-11-30
I would leave your version be if it needs upgrading i'm sure ubuntu would soon send it with updates

---

### Post by cariboo on 2008-11-30
For more info on packet filtering look here:

file:///usr/share/doc/iptables/html/packet-filtering-HOWTO.html

Just paste the above link in your browser address bar, also look at:

```
man iptables
```

Jim

---

### Post by shqip on 2008-12-06
Thank you

---

### Post by anthro398 on 2008-12-07
> **shqip said:**
> iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT 

This is one of the first rules in all of my firewalls.  This prevents the overhead associated with comparing a packet from an existing connection with the long list of rules following this rule.  It's pretty common practice, I think.  Of course, I set kernel parameters with syctl first, then build user defined chains, filter out bad packets, etc.

---

### Post by beyboo on 2008-12-07
My philosophy is to get the work done.

I use Firestarter and set the basic rules. Works well for me.

---

