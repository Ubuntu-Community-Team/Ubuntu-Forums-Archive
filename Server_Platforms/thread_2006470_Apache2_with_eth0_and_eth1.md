---
title: "Apache2 with eth0 and eth1"
date: 2012-06-19
forum: Server Platforms
---

### Post by gregor171 on 2012-06-19
Hey! Ihave a problem with second eth on apache. Site from eth1 doesn't work, while eth0 works well. Is this problem related to apache or is some other configuration?

Does someone know how to configure server with eth0 and eth1 at the same time (they both have a different IP address).

Thx!


PS: buntu server!

---

### Post by rabbadabb on 2012-06-19
How is your routing configured? Do you have a default route from both interfaces?

---

### Post by gregor171 on 2012-06-19
I think this is default:

```
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.7.150                                            
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.150
```

---

### Post by gregor171 on 2012-06-19
PS:
```
default via 192.168.1.1 dev eth1  metric 100
```

---

### Post by rabbadabb on 2012-06-19
And the route in to the server is for both nets?

---

### Post by SeijiSensei on 2012-06-19
Check that the entries in /etc/apache2/ports.conf and any virtualhost definitions use the "*:80" syntax throughout, e.g., "NameVirtualHost *:80" and "<VirtualHost *:80>".  Also check that any Listen directives do not include an IP address, e.g., "Listen 80" rather than "Listen 192.168.1.1:80".

Also I think you've got some problems here:
> ```
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.7.150                                            
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.150
```

I suspect you need a /24 on the first route.  192.168.1.0/24 is a subnet of 192.168.0.0/16, so traffic on the 192.168.1.0 network is being routed out eth0.  It looks like the eth0 network should be 192.168.7.0/24, not 192.168.0.0/16.

```
192.168.7.0/24 dev eth0  proto kernel  scope link  src 192.168.7.150                                            
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.150
```

---

### Post by gregor171 on 2012-06-19
@rabbadabb
I'll try your solution and let you know if it works. I'm not an expert in networking. I use only NameVirtualHost *:80.

---

