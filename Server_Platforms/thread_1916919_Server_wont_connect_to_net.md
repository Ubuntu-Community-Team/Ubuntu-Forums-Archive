---
title: "Server wont connect to net"
date: 2012-01-29
forum: Server Platforms
---

### Post by 53peterp on 2012-01-29
I have a server with Ubuntu 10.04LTS that I have been running for some time, no problems connecting to the net, updating Ubuntu etc. I also have a billion router that I upgraded the firmware on and since then something has changed and I have not been able to connect to the internet from the server. Using the domain address I can get to the server externally so incoming works fine just can't connect out. Any help would greatly appreciated.

---

### Post by spynappels on 2012-01-29
Has the firmware upgrade messed with NAT settings or firewall rules? Either could create the symptoms you describe.

---

### Post by 2F4U on 2012-01-29
I assume that you are able to reach the server from inside your network? If yes, would it be possible that the router is blocking the servers connection to the internet, maybe as a result of an updated firewall rule?

---

### Post by 53peterp on 2012-01-29
Hi **spynappels** and **2F4U** yes I have no problem connecting to the server inside the network. On the router I have a static ip and am using port forwarding for port 80 the router says "Port ranges forwarded internally will be the same as Externally." On the server I am using a GUI to control the firewall and it say port 80 is open. How do I check the complete list of rules Maybe the GUI is not showing a new one if it has been added by the router. **spynappels** whats the best way to check the NAT settings?
 
Thank you both for your help so far Guys

---

### Post by 53peterp on 2012-04-10
Just to let you know,
 
 problem fixed the gateway ip was wrong in the /etc/network/interfaces file

---

