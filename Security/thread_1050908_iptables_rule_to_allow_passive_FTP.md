---
title: "iptables rule to allow passive FTP"
date: 2009-01-26
forum: Security
---

### Post by PC_Nerd on 2009-01-26
Hi,

Im running ubuntu 8.04 server edition, iptables:

here is my current firewall setup...

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```


Im stumped on how to allow passive FTP through that firewall.  I thought that the last INPUT chain rule would allow it on any port, but aparently now.

Thanks for any advice,
PC_Nerd

---

### Post by blackgr on 2009-01-26
maybe you should take a look at this. It might help you.
[http://osdir.com/ml/linux.debian.devel.firewall/2006-02/msg00020.html](http://osdir.com/ml/linux.debian.devel.firewall/2006-02/msg00020.html)

---

