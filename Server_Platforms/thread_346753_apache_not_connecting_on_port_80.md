---
title: "apache not connecting on port 80"
date: 2007-01-26
forum: Server Platforms
---

### Post by tr333 on 2007-01-26
i have a webserver sitting inside a LAN behind a netgear router.  I can set apache to listen to port 81, and everything works fine using port forwarding on the router.  when i try to get apache to listen on port 80, i can only connect from inside the lan and not from outside the router.  i have tried enabling port forwarding for port 80 on the router, but this doesnt seem to change anything...
i have no rules setup for iptables on the server, so i have no idea where the connection through port 80 is being blocked.  is this a problem with netgear routers where port 80 is being blocked, or would it be a problem with my server install?

---

### Post by phossal on 2007-01-26
It definitely *isn't* a blanket problem with Netgear routers. I use one with port forwarding to 80. You could quickly download a copy of Tomcat to your desktop, add a JAVA_HOME export to your .bashrc, and edit the Tomcat server.xml file to listen on 80, instead of 8080. It would take about ten minutes, and help you split the problem between your Apache config, and *everything else *. It would take about 10 minutes.

[Here's a simple way to get Tomcat, if you're up for that.]("http://ubuntuforums.org/showthread.php?t=332674")

Otherwise, there are a *lot* of things that could be wrong. If you can't put better boundaries on the problem, it's point and shoot.

---

### Post by az on 2007-01-26
> **tr333 said:**
> so i have no idea where the connection through port 80 is being blocked.  is this a problem with netgear routers where port 80 is being blocked, or would it be a problem with my server install?

Many ISPs block port 80 unless you pay for a business connection.  Are you running this from home on a residential connection?

---

### Post by phossal on 2007-01-26
> **azz said:**
> Many ISPs block port 80 unless you pay for a business connection.  Are you running this from home on a residential connection?

What? He's resolving the port with his router. How would his ISP affect that?

[Edit] I'm not implying that you're wrong. I really have never heard of such a problem.

---

### Post by chrisfay on 2007-01-26
azz is correct. You are almost definately blocked by your ISP.

>  I can set apache to listen to port 81, and everything works fine using port forwarding on the router. when i try to get apache to listen on port 80, i can only connect from inside the lan and not from outside the router.

This is the best way to test it; if you can get through to your machine via an alternate non-standard port, but not 80, you can almost gurantee the ISP is filtering the ports. 

> What? He's resolving the port with his router. How would his ISP affect that?

Not on port 80; requests aren't even reaching the router unless he uses another port.

---

### Post by tr333 on 2007-01-26
i just checked on google, and it seems that my isp (optusnet.com.au) is blocking port 80 (among other ports, smtp, https, etc).  at least they dont block ssh (port 22)...

i have a dyndns.org address to connect to the server from outside the lan (isp gives dynamic ip addresses) and was wondering if there's a way to connect myaddress.dyndns.org to myserverip:81? (connect the dynamic dns address on port80 to port81 on my router).  is there a free port forwarding service similar to the dyndns service?


EDIT:  I just realised that the standard agreements for internet use with this isp are distributed in DOC format, and since i'm on a mac without ms-office i dont trust that i will be able to read them properly :mad:

---

### Post by az on 2007-01-26
> **tr333 said:**
> 
i have a dyndns.org address to connect to the server from outside the lan (isp gives dynamic ip addresses) and was wondering if there's a way to connect myaddress.dyndns.org to myserverip:81? (connect the dynamic dns address on port80 to port81 on my router).  is there a free port forwarding service similar to the dyndns service?


Dyndns offers webhop.  You can webhop from oneplace.webhop.com to anotherplace.dyndns.org:81 for example.

But, for example, if you work in a hospital or another institution that blocks a lot of ports, people trying to access oneplace.webhop.com will still end up trying to connect to anotherplace.dyndns.org:81 and will not reach you because they still cannot use port 81.

---

### Post by tr333 on 2007-01-26
> **azz said:**
> Dyndns offers webhop.  You can webhop from oneplace.webhop.com to anotherplace.dyndns.org:81 for example.

But, for example, if you work in a hospital or another institution that blocks a lot of ports, people trying to access oneplace.webhop.com will still end up trying to connect to anotherplace.dyndns.org:81 and will not reach you because they still cannot use port 81.

Thanks.  Never knew about that service...  seems to be exactly what i need.

---

