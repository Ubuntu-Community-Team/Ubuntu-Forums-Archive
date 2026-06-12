---
title: "Looking for help making a transparent firewall"
date: 2010-04-14
forum: Security
---

### Post by Darin722 on 2010-04-14
I'm involved in a project to help students set up a network security training lab using vmware. I want to simulate (in a very rough way) scanning through a poorly configured router or firewall.  The easiest way I can think of to simulate this is to use a linux vmware image with two virtual nic cards to act as a firewall with the attacker on the outside network and a domain controller, web server, and database server on the inside network.

I would like to start students off with a firewall script that exposes everything on their internal network to the attacker.  Is there an easy way to (mis)configure iptables to do this?.

The model I'm trying to replicate is something like this.
Attackers were on a 10.10.x.x network, defenders were on a 192.168.x.x network.  As an attacker I could nmap 192.168.x.x and see every machine and every service on the defenders side even if they moved a service to an unexpected location.

Can anyone offer some suggestions as to how I can implement a similar configuration using a linux image as firewalls/routers in vmware?

Much thanks in advance.

---

### Post by bodhi.zazen on 2010-04-14
> **Darin722 said:**
> I would like to start students off with a firewall script that exposes everything on their internal network to the attacker.  Is there an easy way to (mis)configure iptables to do this?.

iptables is easy

```
sudo iptables -F
sudo iptables -X
sudo iptables -F -t nat
sudo iptables -X -t nat

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

You will probably need to configure your servers, especially mysql, to accept connections (other then localhost).

---

