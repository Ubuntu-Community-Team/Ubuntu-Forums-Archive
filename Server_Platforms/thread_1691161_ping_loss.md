---
title: "ping loss"
date: 2011-02-19
forum: Server Platforms
---

### Post by Mad_Turnip on 2011-02-19
Hello, i have an IBM Eseries 345 server which i've been using as a router for my home lan and webhosting for some of my projects. Yesterday i moved from one room to another and since then i have 20-40% loss to the internet connection.

Yahoo Messenger is loggin on from 5 to 5 minutes, gmail isn't loading, google also ... Iused cmd from windows desktop with ping -t google.com and i have random timeouts. I restarted the server, changed the switches, cables but still nothing.

On my server is Ubuntu 8.04 LTS with Webmin and Virtualmin. From the ISP there's nothing wrong. With their cable directly connected to my laptop the connection is good. I also login through SSH and ping google, the same timeout - this excludes bad wiring in my LAN.

Anybody has some clues ? Thanks.

---

### Post by terazen on 2011-02-24
Try pinging from the server to the internet, from server to pc, from pc to server, and from pc to internet to see if it can be narrowed down to the server's internal or external side.  Was all of your server's configuration saved so nothing was lost on power off/power on?

---

### Post by Mad_Turnip on 2011-02-25
hi, i tried and found a patch cable faulted. but on the tester it was ok ... pretty strange ...

---

