---
title: "Iptables issues"
date: 2009-03-22
forum: Server Platforms
---

### Post by Xmister on 2009-03-22
So, the situation is that my server is under some kind of attack, I think DDos, so I configured iptables the following ways:
```
#!/bin/bash
iptables -F
iptables -X
iptables -N ssh
iptables -N apache
iptables -N bind
iptables -N blacklist

#Blacklist lanc
iptables -A blacklist -m recent --name blacklist --set
iptables -A blacklist -j DROP

#SSH lanc
#Ha blacklistes akkor dobás
iptables -A ssh -m recent --update --name blacklist --seconds 600 --hitcount 1 -j DROP
#Ha nem, akkor percenkent 3at engedunk neki
iptables -A ssh -m recent --update --name ssh --seconds 60 --hitcount 3 -j blacklist
#Eloszor jar erre
iptables -A ssh -m recent --set --name ssh
iptables -A ssh -j ACCEPT

#Apache lanc
#Ha blacklistes akkor dobás
iptables -A apache -m recent --update --name blacklist --seconds 600 --hitcount 1 -j DROP
#Ha nem, akkor percenkent 3at engedunk neki, majd mehet a blacklistbe
iptables -A apache -m recent --update --name apache --seconds 60 --hitcount 3 -j blacklist
#Eloszor jar erre
iptables -A apache -m recent --set --name apache
iptables -A apache -j ACCEPT

#Bind lanc
#Ha blacklistes akkor dobás
iptables -A bind -m recent --update --name blacklist --seconds 600 --hitcount 1 -j DROP
#Ha nem, akkor percenkent 3at engedunk neki, majd mehet a blacklistbe
iptables -A bind -m recent --update --name bind --seconds 60 --hitcount 10 -j blacklist
#Eloszor jar erre
iptables -A bind -m recent --set --name bind
iptables -A bind -j ACCEPT

#Input lanc
iptables -P INPUT DROP
iptables -A INPUT -i lo -j ACCEPT #Localt engedjuk mar
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport 4040 -m state --state NEW -j ssh
iptables -A INPUT -p tcp -m tcp -m multiport --dports 82,81 -m state --state NEW -j apache

```

As you can see, the last line, now not the 80 port goes to apache chain, but 82 and 81 for testing. This way everything OK.
BUT!!!
When I change either of the ports to 80, neither of them will drop.
The same thing when I only user 80 without multiport.
Could someone tell me why iptables dosen't like port 80?
Or how I can make this work?

The weird thing is that this worked well yesterday, and since I woke up in the morning it's not.

Please help...

---

