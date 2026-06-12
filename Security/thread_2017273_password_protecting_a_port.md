---
title: "password protecting a port"
date: 2012-07-05
forum: Security
---

### Post by netopalis45 on 2012-07-05
I am trying to set up a password protected security camera on my home computer that has its own domain name. To access the camera you go to port 8000 (example localhost:8000). I have created a password protected page that redirects to that port but would like to make it so you can't access the port directly, but have to go through the login page. I don't even know if it is possible to do this but I would like to give it a try if it is. Preferably I would like the only way to get to that specific port to be logging into the page first.

---

### Post by raja.genupula on 2012-07-05
> **netopalis45 said:**
> I am trying to set up a password protected security camera on my home computer that has its own domain name. To access the camera you go to port 8000 (example localhost:8000). I have created a password protected page that redirects to that port but would like to make it so you can't access the port directly, but have to go through the login page. I don't even know if it is possible to do this but I would like to give it a try if it is. Preferably I would like the only way to get to that specific port to be logging into the page first.

Good Idea  , +1 .

---

### Post by cariboo on 2012-07-06
You can't password protect a port, but you deny access to everyone except a specific ip address using iptables.

---

