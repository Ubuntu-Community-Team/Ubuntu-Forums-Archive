---
title: "internet problem"
date: 2013-06-25
forum: Server Platforms
---

### Post by bendzy72 on 2013-06-25
Hi ppl..
I have a problem and hope can here find solution..
i have install ubuntu server and in lan all is ok.. 4 pc with windows can connect with ip address.. 
problem is that no one from outside can connect..
if you need more info i will write..
thanks for help

---

### Post by Cheesemill on 2013-06-25
You need to go into your router settings and set up port forwarding for specific ports to your servers internal IP address.
I can't give any more detailed information as the method varies from router to router but you can find more details at...
[http://portforward.com/english/routers/port_forwarding/](http://portforward.com/english/routers/port_forwarding/)

---

### Post by trundlenut on 2013-06-25
Once you have setup port forwarding don't be suprised if a lot of people apprently in China suddenly try and access your server.

I would give careful thought to which ports you open to outside world.  I opened port 22 (ssh) to the world on a server and was getting over 1000 failed login attempts per hour.

---

### Post by bendzy72 on 2013-06-26
Hi Cheesemill..
thank your for answer.. i tried with ports but nothing..
I have fritzbox 6340 and my isp is kabel bw ( i am in deutschland).
when i run ifconfig wheri is my ip 192.168.178.32. 
when in browser write 192.168.178.1 i get my box..
when i try what is my ip i get 46.5.2.219.it is dynamic... i think that is from provider..
server wont run all time.. that is only for lernet purpose for my tochter.. she must make file sharing, web server and other stuff what you can understand better then we.. we have tried all but no answer yet..
anyway thank you for answer

---

### Post by bendzy72 on 2013-06-26
thanks for your help but nothing.. still no access on net

---

### Post by trundlenut on 2013-06-30
your ISP may block ports such as port 80 to stop you running a server at home

---

