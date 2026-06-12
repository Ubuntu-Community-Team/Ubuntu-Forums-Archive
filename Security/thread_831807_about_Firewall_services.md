---
title: "about Firewall services"
date: 2008-06-17
forum: Security
---

### Post by voltage on 2008-06-17
Dear Expert,

     currently i were using the Ubuntu 8.04 LTS Server Edition. so may i know :- 

     1 ) how to find that the firewall service is active.
     2 ) how to find that the port 3306 is block.
     3 ) if the port 3306 is block how to unblock.

Thank and please advice.

---

### Post by cdenley on 2008-06-17
1. The "firewall service" (iptables) is always running. If there is a way to turn it besides recompiling the kernel, I don't know it. By default, it will allow everything, so you might consider that disabled.

2. Use this command from another computer.
```

nmap <server ip> -p 3306

```
You can also check your current rules
```

sudo iptables -L

```
A default install that filters nothing will give this output
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

3. If you want to allow incoming traffic on TCP port 3306
```

sudo iptables -I INPUT -p tcp --dport 3306 -j ACCEPT

```
If you want to allow everything by clearing all rules
```

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -t nat -P PREROUTING ACCEPT
sudo iptables -t nat -P POSTROUTING ACCEPT
sudo iptables -t nat -P OUTPUT ACCEPT
sudo iptables -F
sudo iptables -t nat -F

```
These changes will not be persistent if you have a service that loads pre-configured rules at boot time.

---

