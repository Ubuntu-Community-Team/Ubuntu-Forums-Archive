---
title: "Hostapd : how to disable access to local network"
date: 2021-03-24
forum: Security
---

### Post by packstlaurent on 2021-03-24
Hello all, 

 I want to create a wifi hotspot for guests to share my internet connection. 
I succeeded to create a hotspot with hostapd by following various tutorials on the net Cool ! My guests have internet!
But…. The issue is that guest connected to the wifi hotspot are able to reach my local network. I want to protect my local network. 

The network is like this  :
Box <-> Ethernet <-> Server with Wifi <-> Hotpost wifi <-> guest wifi client 

I couldn't find anything convincing on the net. 

My local network subnet is on 192.168.1.0/24
The guest subnet is on 192.168.4.0/24
The router with internet connection is 192.168.1.1

I tried to create filter rules with iptable on the hostapd server but without success.
```

#accept connection from wifi to router
iptables -A INPUT -i wlan0 -s 192.168.4.0/24 -d 192.168.1.1 -j ACCEPT
-j ACCEPT
#disable connection from wifi to local network
iptables -A INPUT -i wlan0 -s 192.168.4.0/24 -d 192.168.1.0/24 -j DROP
```


 If anyone can help me? 
Thank you, 

Regards,
Pack

---

### Post by Doug S on 2021-03-25
I think you need to apply your 2nd rule to the FORWARD chain, instead of the INPUT chain.
Your 1st rule is useless, as the router is not the destination, but rather a step along the way.
You might also need to allow a return path, depending on your default rule, i.e. if it is DROP.
So, I am saying this (I invented an interface name, change it your actual interface name):

```
iptables -A FORWARD -i eth0 -o wlan0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i wlan0 -o eth0 -s 192.168.4.0/24 -d 192.168.1.0/24 -j DROP
```

You will have to determine where these rules should be placed within your current rule set, or give us your entire rules set.

---

### Post by packstlaurent on 2021-03-29
Hi Doug, 

It works like a charm. Thank you very much !

Regards, 

Pack

---

