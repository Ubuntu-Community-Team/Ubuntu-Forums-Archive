---
title: "iptables question."
date: 2012-11-29
forum: Security
---

### Post by AsherSevyn on 2012-11-29
I am setting up a new squid daemon to run on my server. I want to make sure that everyone inside my network can access squid but I want to make sure everyone on the internet is blocked. 

eth0 is connected to my internal LAN via: 192.168.0.5/255.255.255.0
eth1 is connected to the internet via: 1.1.1.1/255.255.255.248
Squid listens on port 3124

Is this the correct syntax for doing that?:

iptables -F
iptables -t nat -F
iptables -X
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 3124 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

As you can probably see I prefer to block everything except for what I'm actually using.  

The tricky part is I'm not sure how to block everyone on the net but allow everyone on my local network access to squid.

Thanks in advance.

---

### Post by chadk5utc on 2012-11-30
Hi 
You are correct it is better to block all and then only allow the port/services you need In/Out. A good way to look at firewalls is that which is not explicitly allowed is implicitly denied. You can create a local only rule to allow your subnet like so:
# allow source  192.168.0.5/255.255.255.0
iptables -A INPUT -j ACCEPT -m state --state ESTABLISHED,RELATED
iptables -A INPUT -j ACCEPT -m state --state NEW -p tcp --source  192.168.0.5/255.255.255.0
iptables -A OUTPUT -j ACCEPT -m state --state ESTABLISHED,RELATED

keep in mind how many ip addresses you really need on your network and change the subnet for this 255.255.255.0 allows 254 and 255.255.255.248 allows 6?? which breaks down like this:
192.168.0.0 Network ID
192.168.0.1 First Usable IP
192.168.0.6 Last Usable IP
192.168.1.7 Bcast
if you dont need that many try another use this for help [http://www.subnet-calculator.com/](http://www.subnet-calculator.com/)
Less will be better IMO. 
here's a good reference: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
or another some find a little easier to grasp than iptables: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by SeijiSensei on 2012-11-30
Also you can specify the network(s) that are allow to use the cache in squid.conf.

```
acl mynetworks src 192.168.1.0/24 172.16.0.0/16
http_access mynetworks allow
http_access deny all

```

---

### Post by AsherSevyn on 2012-12-03
I am setting up a new squid daemon to run on my server.  I want to make sure that everyone inside my network can access squid but I want to make sure everyone on the internet is blocked. 

eth0 is connected to my internal LAN via: 192.168.0.5/255.255.255.0
eth1 is connected to the internet via: 1.1.1.1/255.255.255.248
Squid listens on port 3124

So far I have the following script for my iptables.

iptables -F
iptables -t nat -F
iptables -X
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -A INPUT -p tcp --dport 3124 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

Is this correct? Will this allow all my LAN users access to squid while blocking outward attempts from the net to my server?
 
Thanks in advance!

-Ash

---

### Post by chadk5utc on 2012-12-03
This thread was started 4 days ago and is still open
[http://ubuntuforums.org/showthread.php?t=2089648](http://ubuntuforums.org/showthread.php?t=2089648)

---

### Post by cariboo on 2012-12-03
Please don't create multiple threads on the same subject. I have merged your two threads.

---

