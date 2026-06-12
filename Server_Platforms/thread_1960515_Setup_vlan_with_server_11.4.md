---
title: "Setup vlan with server 11.4"
date: 2012-04-17
forum: Server Platforms
---

### Post by Kc5jmr on 2012-04-17
I am in need of help here is what we have.
Single Internet connection (dhcp) for ip addressing from ISP roadrunner
A network using 192.168.0.x.  Church office
B network using10.10.10.x  church school
C a fax server for both networks

What I need is for the two networks to share one rr connection but not se each other, I also need them to be able to see the fax server for all received fax .  I have a catalyst 2950 smart switch to work with as well as separate dhcp servers for both networks.  Right now we manage to just share the Internet with the use of 3 befsr41 router but we can't work the fax server into it yet.  Any ideas will do but I am a newbie with Ubuntu server.  I have managed to get a base install on a system for samba but that is bout it.

Robert

---

### Post by sj1410 on 2012-04-18
you need a ubuntu based firewall which can restrict use between this 2 networks still allowing them to share internet and fax. iptables is the solution for your requirement. but it would be a lot tricky to set it up. If you can afford a cheap commercial service for this than have a look at it

[http://www.pisces.net.in/p/effortless-linux-based-firewall.html](http://www.pisces.net.in/p/effortless-linux-based-firewall.html)

---

