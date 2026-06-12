---
title: "Banning an ip"
date: 2006-10-25
forum: Server Platforms
---

### Post by davebgimp on 2006-10-25
Checking my server logs, I see that an IP address in India keeps trying to open an ssh session. I'd like to ban it and was wondering if it was possible to designate an IP as banned from making any type of connection (ssh, http, ftp...whatever) with my Ubuntu server.

---

### Post by Old Pink on 2006-10-25
You'd be better off asking at the apache forum, but here you go:

[http://www.debian-administration.org/articles/283](http://www.debian-administration.org/articles/283)

Hope that stops him/her! :D

---

### Post by Eversmann on 2006-10-25
It's easier if you add a rule to your iptables dropping all the packets from that ip.

---

### Post by davebgimp on 2006-10-25
Actually I'm all set now.

I Manually edited /etc/hosts.deny, adding **ALL:[offending IP]**

I also installed DenyHosts which should take care of this automatically from now on.

[http://denyhosts.sourceforge.net](http://denyhosts.sourceforge.net)

---

### Post by Ride Jib on 2006-10-25
What does this have to do with Apache??

iptables drop is probably the best/easiest way to accomplish this.

---

