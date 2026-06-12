---
title: "problem when build LAMP server behind a router"
date: 2010-12-09
forum: Server Platforms
---

### Post by jsqihui on 2010-12-09
I build a LAMP server behind a router.
The current situation is:
1.I could access index.html of apache within the LAN.
2.I could access the vsftp outside of the LAN.
3.I could access the ssh outside of the LAN.

I have configured my router to do reflections(although I don't know it's correct or not.). I think the LAMP works good since I could use it inside the LAN. The configuration of the router is at least partly right because ssh and vsftp work fine(I test by browsing the ip:74.***.***.*** in the lan, not 192.168.1.8 --this also works. ).

I cannot access web service outside the LAN. And the error message is "Oops! Google Chrome could not connect to 74.***.***.***"

Did I miss some configuration of router?Apache2?Ubuntu? I use the ubuntu server 2010.10 version. 

Really appreciate who is concerning on this problem.

--Hui

---

### Post by CharlesA on 2010-12-09
Make sure that your ISP isn't blocking port 80.

---

### Post by restorator on 2010-12-09
Ditto, check that your isp isnt blocking. But if not, did you setup port forwarding? Check to make sure you have the router forwarding requests on port 80 for ip 74.xx.etc to the internal ip of the server.

---

### Post by terriblechild on 2010-12-09
You need to do port forwarding for port 80 (HTTP) and 443 (HTTPs in case  that you use HTTPs). Also to access your public IP from your local  network, you need to have nat loopback enabled.

---

