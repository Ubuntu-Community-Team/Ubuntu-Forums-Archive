---
title: "which type of static ip used in server??"
date: 2016-06-23
forum: Server Platforms
---

### Post by ashutosh11 on 2016-06-23
i m new on Ubuntu server.I had setup my server perfectly.I had set a static ip 192.168.1.23 to my server and i had also purchase the static ip 103.52.79.198 that i set to my router and on other part like DNS,Virtualmin and port forwarding i set 192.168.1.23  ip .Now my problem is that my website run on the device that are connected to my router.But i want to run my website on global network. How to do that? plzzz help me urgently....

---

### Post by howefield on 2016-06-23
Thread moved to the "*Server Platforms*" forum.

---

### Post by Habitual on 2016-06-23
You'll need to forward traffic from 103.52.79.198:80 to 192.168.1.23:80 in your router's admin area.

---

