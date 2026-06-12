---
title: "Configure /etc/hosts from PC to Internal Web Server."
date: 2017-04-30
forum: Server Platforms
---

### Post by sethanath2 on 2017-04-30
Hi,

I am experimenting with Ubuntu Server at home. I notice I can see my new web page using someone else's ISP, but not from my own. I believe I need to configure my PC's "/etc/hosts" in order to route to my Ubuntu server within the same LAN.
I tried the following but it does not work. Rebooting did not help either.

127.0.0.1          localhost
127.0.1.1          erick-ASROCK
**192.168.1.70    zethanath.tk**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

I hope someone can help.

Thank you so much.

---

### Post by TheFu on 2017-05-01
What is the external name for the website?
What name does the website use in the nginx/apache configuration?  
Those are what need to be inside your /etc/hosts.  You can put multiple names on the same line.

```
192.168.1.70  zethanath.tk www.zethanath.tk server.zethanath.tk
```
is an example.

---

