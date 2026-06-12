---
title: "Webmin problem - can't access port 10000 remotely"
date: 2009-09-18
forum: Server Platforms
---

### Post by stefda on 2009-09-18
I am running Ubuntu 8.04 server with Webmin installed. It was working fine on the port 10000 and I could load it from anywhere in my browser. Now I get Network Timeout!

netstat -taupn shows (lines with port 10000):

tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      29968/perl
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           29968/perl

ps aux | grep 29968 outputs:
root     29968  0.0  1.4  69300 15264 ?        Ss   10:07   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf

I can telnet myip on port 10000 from the ssh terminal directrly from the server but if I telnet from my WinXP local machine I get "Could not open connection to the host, on port 10000: Connect failed".

I run nmap on the server with output "10000/tcp open  snet-sensor-mgmt"

IPTables are uninstalled (not sure whether I can have other firewall installed).

route command outputs:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
94.136.50.0     *               255.255.254.0   U     0      0        0 eth0
default         94.136.51.254   0.0.0.0         UG    100    0        0 eth0

I am desperate! Please someone help!

---

### Post by stefda on 2009-09-18
Update:

I stopped Webmin and installed vsftp, strarted on port 10000 and still cannot telnet from remote machine. I am assuming the port is closed. How do I open it? Why is it closed if it worked before?

Thanks for your suggestions!

---

### Post by ukripper on 2009-09-18
Check your iptables chain:
```
sudo iptables -L
```

Are running any firewall at all?

---

### Post by stefda on 2009-09-19
ukripper thanks!

I found out my ISP might actually be blocking all ports except for 21, 22, 80 and 443. Luckily enough I won't be staying with this ISP for long.

---

### Post by R.Bucky on 2009-09-19
Webmin is that last program that should be open to someone outside your LAN. There are other ways of checking things or configuration aside from Webmin. Yikes!

---

