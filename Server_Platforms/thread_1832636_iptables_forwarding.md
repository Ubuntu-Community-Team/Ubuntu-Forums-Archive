---
title: "iptables forwarding"
date: 2011-08-25
forum: Server Platforms
---

### Post by Frizianz on 2011-08-25
Hi there,

Wanting to try get a port forwarding system going, except not from the router into a private address with nat, but more across the internet, from two public IP addresses

Basically my ISP blocks incoming port 80 traffic, but i have access to a vps which i can write an iptables rule to forward port 80 traffic on the vps to my IP on port 85.

So like this.

Client Accessing Server
|
|
| Connection on port 80
|
|
VPS - VPS Forwards this connection onto port 85
|
|
| Forwarded packet to my IP:85
|
|
Webserver on port 85

Anyone got any ideas on how to write the iptables rule for this?

---

### Post by allwimb on 2011-08-25
Have a look at this link it might help you:
[http://www.hackorama.com/network/portfwd.shtml](http://www.hackorama.com/network/portfwd.shtml)

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

