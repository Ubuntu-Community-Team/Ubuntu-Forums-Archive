---
title: "server start"
date: 2007-01-25
forum: Server Platforms
---

### Post by tinman on 2007-01-25
Hello All,

I have recently installed LAMP on my pc and have everything running smoothly, with much persistance! It all works wonderfully inside my LAN and now I am trying to get this final linkup with Zoneedit and my domain name. I dont fully have the client working though, although I am thinking I have time to work on that and my IP will remain the same in the mean time. My ISP does not allow me to use port 80 so the reason for Zoneedit. Correct me if I am wrong but when I filled out my app. for them I gave them my router IP and zoneclient will update this when it changes. No worries, but I can not for the life of me get the two working together-Zoneedit and my router. I am supposed to port forward port 80, correct, to my server IP, even though my ISP doesnt allow it or forward it with another port? Then do I have to configure my Apache.conf file to listen? Any suggestions would be greatly appreciated! :D

---

### Post by encompass on 2007-01-27
not very secure for long periods... but I would try droping all firewalls on the router and do something called a "virtual server" makes it so all data to your router ip is sent to that systems internal IP.  Once that works... learn your port forwarding.

---

### Post by Brazen on 2007-01-27
> **encompass said:**
> ...something called a "virtual server" ...

I think you mean a "DMZ."  A DMZ is where all traffic to a router goes to one server.  A "virtual server" is something entirely different.

---

### Post by encompass on 2007-01-28
They call it a virtual server on many routers.  And your right dmz is the formal term.. what is it... demilitarized zone.  right?

---

