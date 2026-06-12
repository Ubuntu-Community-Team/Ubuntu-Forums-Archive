---
title: "help With DHCP Server"
date: 2010-02-05
forum: Server Platforms
---

### Post by MattFinck21 on 2010-02-05
i got and ubuntu cloud cluster running and a node. the problem is i cant discover it. i think its the dhcp because i cant get a ip address from the server(on the cluster). my server looks like this. 

     eth1(internet)|
                   |
                   |
                Cluster
                   |
                 eth0 -----Node

---

### Post by kiranmurari on 2010-02-08
Hi,

       First thing to see would be if the dhcp server is running or not.
Can you post the output of the following command:
```
$ ps ax | grep dhcp
```If the dhcp server is not running then, we need to take look at the dhcp configuration file (/etc/dhcp3/dhcpd.conf) Can you post the contents of that file.

---

