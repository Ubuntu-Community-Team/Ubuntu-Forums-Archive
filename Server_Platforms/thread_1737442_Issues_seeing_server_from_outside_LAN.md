---
title: "Issues seeing server from outside LAN"
date: 2011-04-23
forum: Server Platforms
---

### Post by Tiersin on 2011-04-23
I have been in the process of redoing my server and i've ran into an issue where I can access it fine from local machines, but even with all the correct ports forwarded on my router, I can not access my server. I'm running Ubuntu 10.10 x64 desktop.

Currently I am testing it with an openSSH and apache2. I can access the web server and ssh server just fine locally. The reason I believe its a server issue is that if I try to access my site from the outside, and I forward the ports, it find the server and tries to connect, but cant. If I disable the port forwarding it cant find it at all. 

Any ideas what may be going on in this situation? I have a static ip set and heres the ifconfig report:

eth0      Link encap:Ethernet  HWaddr 00:08:54:53:9f:ea  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe53:9fea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24034785 (24.0 MB)  TX bytes:1424268 (1.4 MB)
          Interrupt:16 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4271 (4.2 KB)  TX bytes:4271 (4.2 KB)

---

### Post by Mosabama on 2011-04-23
how do you test the connection from outside the network? 
cause most of home routers do not allow that you try to connect from the network back to the network it self .. the router will drop it.

"Assuming that all configurations are correct" try to ask someone to connect from outside for you, or you try to go out and test it.

---

### Post by CharlesA on 2011-04-23
Test to see if the ports are open with something like this: [http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by Mosabama on 2011-04-23
> **CharlesA said:**
> Test to see if the ports are open with something like this: [http://canyouseeme.org/](http://canyouseeme.org/)

Cool

---

