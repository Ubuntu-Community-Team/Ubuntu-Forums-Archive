---
title: "How to connect to the internet"
date: 2011-01-09
forum: Server Platforms
---

### Post by BradNowacki on 2011-01-09
Alright i have another question, so im running Ubuntu Server 10.10 still and i finally got a wired connection, but when i use the ifconfig command all i see is the lo(loopback) connection, and i don't know how to enable the eth0 port, any help?

---

### Post by sj1410 on 2011-01-09
check if you see eth0 using 

ifconfig -a

if yes

than assign IP, gateway and DNS. your internet will be enabled.

---

### Post by hashbangfoo on 2011-01-10
so, you have a terminal open, and you do an "ifconfig -a" and you only get the lo...

you can do the following:

sudo dhclient eth0

that should get you an ip, and a route if your router is serving up addresses to clients...

---

