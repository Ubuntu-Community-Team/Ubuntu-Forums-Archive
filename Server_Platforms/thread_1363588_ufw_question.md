---
title: "ufw question"
date: 2009-12-24
forum: Server Platforms
---

### Post by kjacks on 2009-12-24
I recently setup OpenVPN on my 9.04 server and want to route all VPN traffic to the internet.  The OpenVPN site gave an example of how to do this using iptables but I want to stick with ufw since that what I've been using.  

Can anyone help me find the ufw equivalent to this iptables rule?

iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

---

### Post by bodhi.zazen on 2009-12-24
I do not think you can do that directly.

Edit /etc/ufw/before.rules

add this line:

```
-A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

See [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

