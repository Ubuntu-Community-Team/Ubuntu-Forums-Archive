---
title: "ufw not allowing port access - iptables show ok"
date: 2009-12-30
forum: Security
---

### Post by R.Bucky on 2009-12-30
I have not been able to access my ssh for the last couple of days. I use a non-standard port. I checked iptables using iptables -L, which shows 
```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:*port* 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:*port*

```
When I disable ufw, port access is no problem. [The *port* is my attempt at masking the real port number.] What am I missing?

---

### Post by bodhi.zazen on 2009-12-31
How did you configure ufw ?

Keep in mind, order of your rules in iptables is critical.

To give you a more specific answer please post your output from the following commands (sorry, a fragment of your iptables rules simply does not cut it :) )

```
sudo iptables -l -v
sudo ufw status
```

Last, ssh uses tcp, so no need for the udp rule =)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

---

### Post by R.Bucky on 2009-12-31
[SOLVED] - As it turns out, the issue was with my Comcast business class router. For some reason, the "Enable Smart Packet Detection" button was enabled, which somehow botched the whole deal. UFW was not at fault. Interesting fix to this issue.

---

