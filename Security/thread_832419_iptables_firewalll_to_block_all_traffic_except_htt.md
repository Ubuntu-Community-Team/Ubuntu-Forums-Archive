---
title: "iptables firewalll to block all traffic except http"
date: 2008-06-17
forum: Security
---

### Post by dapim on 2008-06-17
iptables -P INPUT DROP
iptables -A INPUT  -p tcp -m tcp --dport 80 -j ACCEPT


i would like to block everything , except  http traffic, but is not working ???

---

### Post by anindya_m on 2008-06-17
Can you please describe what exactly the machine is doing? Is it a sever or a client?

---

### Post by dapim on 2008-06-17
it's a client, my desktop

---

### Post by anindya_m on 2008-06-17
Ok. The reason why it is not working is you have all incoming UDP traffic blocked. UDP is used for DNS resolution (port 53). Also, since you are a client the http traffic inbound will have the source port 80 (rather than destination). Any outbound traffic is not affected. Try this:

```
sudo iptables -F
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

sudo iptables -P INPUT DROP
sudo iptables -A INPUT -p udp -m udp --sport 53 -j ACCEPT
sudo iptables -A INPUT -p tcp -m tcp --sport 80 -j ACCEPT
```

---

