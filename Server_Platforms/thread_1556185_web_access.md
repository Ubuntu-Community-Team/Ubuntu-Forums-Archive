---
title: "web access"
date: 2010-08-19
forum: Server Platforms
---

### Post by ttashi on 2010-08-19
i installed and configured ubuntu server 6. and i configured web server and it is working fine from internal clients. but i cannot access from outside . it has to access using the global ip address of the server.

what and where do i configure this

---

### Post by terazen on 2010-08-19
If you have a global ip on your router and private ip on the server you'll need to setup port forwarding on your router.

---

### Post by DrMelon on 2010-08-19
Also, make sure your domain name is registered properly. Give the DNS servers a chance to refresh too.

---

### Post by ttashi on 2010-08-19
i provided global ip address to the server and it is working fine internally , but cannot access from outside. do i need to register my global ip address in the DNS server, because i want to access the web using global ip address only not domain.

thank for the reply in advance

---

### Post by terazen on 2010-08-20
If you can access a global ip internally but not externally then you have a routing/firewall issue most likely.  You could check logfiles in /var/log/apache2 in case it might be a server issue, but sounds like there is a firewall.

---

### Post by ttashi on 2010-08-20
i checked #iptables -L 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

i also checked the /var/log/apache2 but it has only the log access internally.
i connected a windows with this ip address, i can access and ping from outside, but when i connect my ubuntu server, i cannot access.

---

