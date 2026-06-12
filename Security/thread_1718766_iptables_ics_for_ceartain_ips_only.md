---
title: "iptables ics for ceartain ips only"
date: 2011-03-31
forum: Security
---

### Post by sebkinne on 2011-03-31
10chars

---

### Post by uRock on 2011-03-31
Moved to Security Discussions sub-forum.

---

### Post by Ocxic on 2011-03-31
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
should be:
sudo iptables -A POSTROUTING -t nat -o eth1 -j MASQUERADE
where "-o eth1" is the interface connected to your internet connection.

just replace 192.168.1.0/24 with the IP of the computer you want to have access, others will be ignored.

---

### Post by sebkinne on 2011-03-31
10chars

---

### Post by Ocxic on 2011-03-31
your iptables-save command still has this rule in it:
-A POSTROUTING -o eth0 -j MASQUERADE

be sure to remove it

---

### Post by sebkinne on 2011-03-31
10chars

---

### Post by Ocxic on 2011-03-31
you want to masquerade the internet to provide NAT translation for your network, you don't need to masquerade wlan0 so remove that one.

and i just figured it out: use this

iptables -t nat -A POSTROUTING -s 192.168.1.10 -o eth0 -j MASQUERADE

and remove other rules for masquerading./ the above rule should only provide NAT for the ip you specify.

---

### Post by sebkinne on 2011-03-31
Thanks!
That command worked, just as I needed it :)

Best,
Sebkinne

---

