---
title: "How to specify ip ranges in squid acl"
date: 2014-01-25
forum: Server Platforms
---

### Post by sububtu on 2014-01-25
[SIZE=3]Hi all....
i running ubuntu server 12.04 .
i had configured squid, whic is working perfectly.I would like to know is there any method to add specific ipranges to squid acl.Ie:
my current config:
acl localnet src 192.168.1.0/24    # RFC1918 possible internal network
But i need to the configuration as:

acl localnet src 192.168.1.0  to 192.168.1.199   

and

acl hostelnet src 192.168.0.200 to 192.168.1.255[/SIZE]

how can i achieve this ? pls help

---

### Post by hassan-h-jaber on 2014-01-25
you can use netmask like 
192.168.0.1/25 =192.168.0.1 to 192.168.0.126

see this :
[http://tuxgraphics.org/toolbox/network_address_calculator_add.html](http://tuxgraphics.org/toolbox/network_address_calculator_add.html)

---

### Post by sububtu on 2014-01-27
> **hassan-h-jaber said:**
> you can use netmask like 
192.168.0.1/25 =192.168.0.1 to 192.168.0.126

see this :
[http://tuxgraphics.org/toolbox/network_address_calculator_add.html](http://tuxgraphics.org/toolbox/network_address_calculator_add.html)

:guitar:thanks. .. :guitar:

---

