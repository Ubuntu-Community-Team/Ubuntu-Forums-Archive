---
title: "server 9.04, Need help with blocking port"
date: 2009-08-25
forum: Security
---

### Post by Menesty on 2009-08-25
I have install ngnix server it run on port 80, and jetty on port 8080, and apache on port 9090, I whant block port 8080 and 9090 form internet access, I mean all request shoud come to frontend ngnix it will proxy to apache:9090 or jetty:8080 but I do not what that user can direct access to this port only for local host 127.0.0.1.
thanx for help.

---

### Post by denver on 2009-08-25
You have 2 options:

1. Configure apache and jetty to only listen for incomming connections on 127.0.0.1 (localhost)

2. 
```
iptables -I INPUT -p tcp --dport 8080 -i ! lo -j DROP
iptables -I INPUT -p tcp --dport 9090 -i ! lo -j DROP
```
This blocks all incomming connections from all interfaces except the loopback interface (localhost).

Option 1 is better because it does not depend on a firewall rule being in place.

---

### Post by Menesty on 2009-08-25
thanx

---

### Post by bodhi.zazen on 2009-08-25
> **denver said:**
> You have 2 options:

1. Configure apache and jetty to only listen for incomming connections on 127.0.0.1 (localhost)

2. 
```
iptables -I INPUT -p tcp --dport 8080 -i ! lo -j DROP
iptables -I INPUT -p tcp --dport 9090 -i ! lo -j DROP
```This blocks all incomming connections from all interfaces except the loopback interface (localhost).

Option 1 is better because it does not depend on a firewall rule being in place.

Outstanding advice , thank you.

---

