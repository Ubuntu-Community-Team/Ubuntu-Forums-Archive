---
title: "FIREWALL Configuration"
date: 2011-01-28
forum: Server Platforms
---

### Post by mohan8653 on 2011-01-28
i'm using ubuntu 10.10 server and php,mysql and apache2 installed.

How to configuration the firewall in my server

---

### Post by datamove on 2011-01-28
open port 80/tcp for incoming traffic . :) 

something like *iptables -A INPUT --dport 80 -j ACCEPT* or see man iptables for better info.

---

### Post by YesWeCan on 2011-01-28
I use iptables but it is complicated. Ufw is simpler: [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

Note that ubuntu installs with no firewall rules enabled so it is wide open. The first thing you should do is erect a wall. Then put selective holes in it for the ports you need.

---

