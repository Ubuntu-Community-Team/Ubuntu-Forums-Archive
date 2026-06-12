---
title: "Configuring Apache"
date: 2006-08-22
forum: Server Platforms
---

### Post by vilto on 2006-08-22
let us say that i created an apache server......
im behind my school proxy server ...... how do some one from internet can access my website.:confused: ....what r the configurations i have to make......:-k 
lets say my private ip is 10.94.xxx.xxx
and my proxy server ip is 10.65.xxx.xxx

(IM NEW TO LINUX)

---

### Post by Useless on 2006-08-22
You most likely wont be able to have someone connect to you from the outside.  You would need some sort of port redirection and public address from the router to you, and i am assuming that is handled by your WAN administrator on your campus.  Both of the address you gave are in the Reserved Private Address range.  So they are not reachable from the outside.  

You would be able to set up an apache webserver though, but only someone from inside your network will be able to reach it by your machine name or IP address.  Although, be careful, if the IT department is smart...they may catch on and start blocking ports or even contact you if they have an IP address database for who it is registered to.

---

### Post by vilto on 2006-08-25
thanx......this solves my doubt...

---

