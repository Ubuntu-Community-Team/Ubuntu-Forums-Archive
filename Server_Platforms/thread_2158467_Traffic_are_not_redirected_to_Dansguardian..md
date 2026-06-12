---
title: "Traffic are not redirected to Dansguardian."
date: 2013-06-29
forum: Server Platforms
---

### Post by sayedahmad on 2013-06-29
Hi!


I have ubuntu server 12.04 configured with NAT in iptables to let user to access internet but recently I decided to to have some content filtering so I searched a lot and I found Dansguardian helpful for me.
I installed dansguardian, squid3 and I configured dansguardian.conf file according to there menual with squid.conf my server ip and iptables configuration is as follow.


eth0=182.50.190.135      #internet Interface
eth1=192.168.1.1           #local interface


IPtables rules are:




iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE


iptables -t nat -A OUTPUT -d localhost -p tcp --dport 80 -j REDIRECT --to-ports 8080


iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128




iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3128 -j REDIRECT --to-port 8080


Problem:
when I set dansguardian ip (192.168.1.1) and port (8080)  manually in client internet explorer dansguardian is working but iptables cannot redirect traffic to dansguardian automatically  I mean without menually setting the ip and port it is not working.


I am searching this problem almost a weak but I cannot figure it out if you have any idea please help.

---

