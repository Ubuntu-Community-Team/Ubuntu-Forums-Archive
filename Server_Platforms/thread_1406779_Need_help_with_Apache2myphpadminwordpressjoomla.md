---
title: "Need help with Apache2/myphpadmin/wordpress/joomla"
date: 2010-02-14
forum: Server Platforms
---

### Post by tad1073 on 2010-02-14
I am trying to build a local intranet, I can access phpmyadmin from localhost (Ubuntu 9.10 Server) but not from the clients (Ubutnu 10.04 alpha 2, Ubuntu 9.10 Desktop, W7 & WXP) and the  same with apache, all computers are on the same network.

I can not ping the host from clients, but can ping clients from host.

Permissions?...Firewall?...etc.

```
:~$ sudo ufw status
[sudo] password for thomas: 
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       192.168.1.0/29
22                         ALLOW       192.168.1.0/29
21                         ALLOW       192.168.1.0/29

```

---

### Post by tad1073 on 2010-02-15
bump

---

### Post by bluefrog on 2010-02-15
forget my post

---

### Post by tad1073 on 2010-02-15
255.255.255.248=192.168.1.0/29 cidr

---

