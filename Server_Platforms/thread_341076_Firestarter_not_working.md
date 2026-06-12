---
title: "Firestarter not working"
date: 2007-01-18
forum: Server Platforms
---

### Post by shankar1023 on 2007-01-18
Hi

I ve installed firestarter on my ubuntu dapper which going to be a firewall gateway of 15 windows clients.but after I installed, the internet connection went off. and I counln't even ping sites( of course I enabled ping in firestarter).

Now I have removed it but still I am unable to connect internet.

Please help me.

Shan.

---

### Post by shankar1023 on 2007-01-18
hey guys,

I tried this.Just changed iptables.seems working good.Is is correct? need Your help.

sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -s 192.168.1.0/24 -o eth0 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.1.0/24 -m state --state ESTABLISHED,RELATED -i ppp0 -j ACCEPT

---

