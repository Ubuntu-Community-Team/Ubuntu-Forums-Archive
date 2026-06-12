---
title: "Assign website to ip address"
date: 2014-03-19
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-03-19
I ahve a server with 2 ip addresses. All the websites are in separate folders in /var/www/ eg /var/www/website1 /var/www/website2
The nameservers point some of the websites on ip address12.34.56.78 and some on ip address 90.78.56.34
The websites on ip address 12.34.56.78 all work and the websites on ip address 90.78.56.34 dont work
How do I configure the websites to be on ip addres 90.78.56.34?

---

### Post by TheFu on 2014-03-19
What is your routing table?
```
route
```

---

### Post by astarmathsandphysics on 2014-03-19
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         111.90.150.1    0.0.0.0               UG    100     0        0 eth0
localnet        *               255.255.255.0           U         0      0        0 eth0

I see now why routing might be the problem but I don't know how to fix it.

using
ip route show 
in terminal gives  

default via 111.90.150.1 dev eth0  metric 100 
111.90.150.0/24 dev eth0  proto kernel  scope link  src 111.90.150.92

---

