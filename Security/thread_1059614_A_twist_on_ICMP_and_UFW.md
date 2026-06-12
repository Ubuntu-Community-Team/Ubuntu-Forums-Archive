---
title: "A twist on ICMP and UFW"
date: 2009-02-03
forum: Security
---

### Post by sand0z on 2009-02-03
On Ubuntu 8.10 server, I want to deny any attempt of a connection by the server to any other host on the home network. This includes PING as well. I set up a number of rules though ufw, enabled it and rebooted and I can still connect to other machines. In the following output from ufw status, 172.25.25.211 is Ubuntu and 172.25.25.16 is the other host. I can still communicate between the two on port 80 and by ICMP and believe that ufw/iptables is working because the two statements concerning ports 22 and 80 take effect.


To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
80/tcp                     ALLOW   Anywhere
172.25.25.16               DENY    172.25.25.211
172.25.25.211              DENY    172.25.25.16
Anywhere                   DENY    172.25.25.16

Saved iptables rules:

-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 4 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT 

-A ufw-user-input -p tcp -m tcp --dport 22 -j ACCEPT 
-A ufw-user-input -p tcp -m tcp --dport 80 -j ACCEPT 
-A ufw-user-input -s 172.25.25.211/32 -d 172.25.25.16/32 -j DROP 
-A ufw-user-input -s 172.25.25.16/32 -d 172.25.25.211/32 -j DROP 
-A ufw-user-input -s 172.25.25.16/32 -j DROP

What am I overlooking?

Thanks

---

### Post by koenn on 2009-02-04
icmp type 8 is an "echo request", commonly know as "ping". It's apparently allowed per ```
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT
``` I don't know IFW, but I assume Echo  replies will be also allowed, maybe by an iptables rules that accepts "related" traffic by default but isn't shown in the UFW output.
These rules precede your DROP rules, so they take effect before the DROP rule is reached.

---

### Post by tednumber8 on 2009-02-04
Oooo I much prfer using GUFW.

I think it's easier to navigate and select restrictions

---

