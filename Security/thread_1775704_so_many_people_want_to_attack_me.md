---
title: "so many people want to attack me?"
date: 2011-06-05
forum: Security
---

### Post by luofeiyu on 2011-06-05
my system:ubuntu 1.04+firestarter
please see my attachment:the event (red alarm),
so many people want to attack me??
how can i do?

---

### Post by raja.genupula on 2011-06-05
i am not aware of your problem , but if we close that unwanted port then we can protect the system from intruders . 

         i think these can help you , dont mind if not helpful 

[http://www.mysql-apache-php.com/basic-linux-security.htm](http://www.mysql-apache-php.com/basic-linux-security.htm)

[http://www.velocityreviews.com/forums/t224471-port-scan-attack-what-action-to-take.html](http://www.velocityreviews.com/forums/t224471-port-scan-attack-what-action-to-take.html)

---

### Post by Soul-Sing on 2011-06-05
its one ip address.

---

### Post by Soul-Sing on 2011-06-05
i should in the first place purge firestarter, and install ufw or gufw. firestarter isn't maintained for several years now.
ufw: sudo ufw enable
gufw: take a look at the graph.interface: deny from.

are you running a server?

---

### Post by HermanAB on 2011-06-05
Howdy,

If you are running a server, then you can use a rule like this to protect it against most attacks:

# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

---

### Post by crispy_420 on 2011-06-07
Maybe a hardware firewall only passing ports required to the system would be a good choice.

---

