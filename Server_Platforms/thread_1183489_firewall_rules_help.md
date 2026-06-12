---
title: "firewall rules help"
date: 2009-06-10
forum: Server Platforms
---

### Post by fouadk on 2009-06-10
hi everyone...

i have a server that is a dhcp and a dns...the dns forward queries to other dns servers...thats how we get internet...

what i want to do is make my server drop all connections made to him from a specific MAC address so that particular computer lose internet connection...

is that doable???

please help
Thanks in advance

---

### Post by gombadi on 2009-06-10
> 
what i want to do is make my server drop all connections made to him from a specific MAC address so that particular computer lose internet connection...

is that doable???


Depending on what you use to configure iptables will depend how you set the rule. If you use the command line then you can use a line similar to the following to drop all packets from a particular mac address -
```

iptables -A INPUT -m mac --mac-source 00:1c:e1:75:fa:f4 -j DROP

```

You can add extra conditionals to restrict the rule if you want.

---

### Post by fouadk on 2009-06-10
thanks a lot that was very helful

---

