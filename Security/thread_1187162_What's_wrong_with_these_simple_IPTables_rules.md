---
title: "What's wrong with these simple IPTables rules?"
date: 2009-06-14
forum: Security
---

### Post by Gustavo Narea on 2009-06-14
Hello, everybody.

I've spent an enormous amount of time trying to find what's wrong with these simple IPTables rules, but I haven't found the answer. Here they are (copied from [https://help.ubuntu.com/community/IptablesHowTo):](https://help.ubuntu.com/community/IptablesHowTo):)
```

*filter
:INPUT ACCEPT [368:102354]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [92952:20764374]
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
-A INPUT -j DROP
COMMIT
```

This is what I get:
```
gustavo:~$ sudo iptables -F
gustavo:~$ sudo iptables-restore < /etc/iptables.config
iptables-restore: line 11 failed
```

And I can't even add them individually:
```
gustavo:~$ sudo iptables -F
gustavo:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 1525 packets, 121K bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 988 packets, 124K bytes)
 pkts bytes target     prot opt in     out     source               destination
gustavo:~$ sudo iptables -A INPUT -i lo -j ACCEPT
gustavo:~$ sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables: No chain/target/match by that name
gustavo:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 1952 packets, 160K bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 1410 packets, 187K bytes)
 pkts bytes target     prot opt in     out     source               destination
```

I'm using Ubuntu Jaunty on a VPS.

Thanks in advance!

---

### Post by lovinglinux on 2009-06-14
> **Gustavo Narea said:**
> 
```

 pkts bytes target     prot opt in     out     source               destination
gustavo:~$ sudo iptables -A INPUT -i lo -j ACCEPT
gustavo:~$ sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables: No chain/target/match by that name

gustavo:~$ sudo iptables -L -v

Chain INPUT (policy ACCEPT 1952 packets, 160K bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 1410 packets, 187K bytes)
 pkts bytes target     prot opt in     out     source               destination
```

According to the output above, the problem is in the following rule:

```
 sudo iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```

I suggest you try adding the protocol and the interface to the rule, like this:

```
sudo iptables -A INPUT -i eth0 -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -i eth0 -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

### Post by bodhi.zazen on 2009-06-14
There is nothing wrong I can see with your iptables rules.

I ma going to guess that the problem is with your VPS.

Openvz needs some adjustments to use the match (-m)

This is done on the host and the guest is re-booted.

It is an edit to /etc/vz/vz.conf

Here is how I do it with Openvz 

[http://forum.openvz.org/index.php?t=msg&goto=28807&](http://forum.openvz.org/index.php?t=msg&goto=28807&)

scroll down to my post.

If you use another system, probably similar issue.

---

### Post by Gustavo Narea on 2009-06-14
Lovinglinux: Unfortunately it didn't work :(

bodhi.zazen: It makes sense. I had a similar problem with another OpenVZ-powered VPS. I'm contacting my provider.

Thank you both!

---

### Post by Gustavo Narea on 2009-06-14
bodhi.zazen: You were right! Thanks once again!

---

### Post by bodhi.zazen on 2009-06-14
happy it worked out for you. That was very kind of your VPS provider to adjust the config file, better then most will do for you, stay with them ;)

---

### Post by kevdog on 2009-06-14
What is openvz and VPS?

---

### Post by bodhi.zazen on 2009-06-14
> **kevdog said:**
> What is openvz and VPS?

VPS = Virtual Private Server aka [fivebean](http://fivebean.com/) etc

VPS can be provided on several platforms, including, but not limited to, OpenVZ .

OpenVZ = [http://wiki.openvz.org/](http://wiki.openvz.org/)

Openvz is a virtualization technology, I think of openvz containers as chroot jails (a bit more complex that that, but should give you the general idea).

See also 
[http://www.parallels.com/products/virtuozzo/](http://www.parallels.com/products/virtuozzo/)
and VMWare (ESX) [http://www.vmware.com/products/vi/esx/](http://www.vmware.com/products/vi/esx/)

---

