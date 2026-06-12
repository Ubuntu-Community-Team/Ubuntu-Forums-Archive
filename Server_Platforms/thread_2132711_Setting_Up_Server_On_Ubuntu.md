---
title: "Setting Up Server On Ubuntu"
date: 2013-04-05
forum: Server Platforms
---

### Post by BmanTheBoss on 2013-04-05
Haiee I am working for my school setting up MinecraftEDU for use as a learning tool. I have the program installed (MinecraftEDU) on a few computers and have set up a server for this. The server computer is running Ubuntu Desktop 12.10. I have the server running, but I can't connect to it from another computer. I talked to another person at another school, and he said there was a way to do it without port forwarding. He wouldn't tell me the login for the internet settings, and I don't like Hamachi. I am wondering what I am going to do to set up the server so it works. The server runs and everything, but I don't have a port or anything set up because I can't get the login. The guy said something about opening a port in ufw, but I can't see how that would help. Can someone help me?

---

### Post by BmanTheBoss on 2013-04-05
Bump

---

### Post by Azrayal on 2013-04-05
Have you checked if the Ubuntu server has the ports blocked via a firewall? 
Also are the computers all on the same network/subnet? 

Also if you take the game out of the equation can the computers actually see each other on the network, tested via a ping?

---

### Post by BmanTheBoss on 2013-04-05
> **Azrayal said:**
> Have you checked if the Ubuntu server has the ports blocked via a firewall? 
I will try allowing the port through UFW
> **Azrayal said:**
> Also are the computers all on the same network/subnet? 
Yes, they all are connected to the same internet network (by either Ethernet or Wi-Fi)
> **Azrayal said:**
> Also if you take the game out of the equation can the computers actually see each other on the network, tested via a ping?
I will try to ping the server computer when I go back Monday

---

### Post by BmanTheBoss on 2013-04-05
Bump

---

### Post by Iowan on 2013-04-05
[http://ubuntuforums.org/showthread.php?t=885580]("http://ubuntuforums.org/showthread.php?t=885580")
Note, in particular, the #8 DON'T.

---

### Post by BmanTheBoss on 2013-04-07
bump

---

### Post by conradin on 2013-04-07
Have you set up ssh?
Or, how is it you are trying to connect to this server?

hows your firewall?
```

sudo ufw  status verbose


```

Is there anysort of networking hardware / configurations we need to know about?
ie, youre behind a router, in a DMZ, or VPN?
or is this a straight shot to the internet? 

wait, is this your server or someone elses?
if its yours, use port forwarding. if its someone elses, you could do a portscan on thier server, but i would think they would just tell you the port. 
After re-reading your post, I'm confused about what is actually happening over there. Whose server is this? Do you have physical access? 
if you have physical access, can you become root, or sudo?


once you have everything runing, this is a good hardening tutorial.
[http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics)

---

### Post by BmanTheBoss on 2013-04-07
This is my server but I have no access to the login for portforwarding. The internet network is routed through the schools website which is routed to a large ISP only for schools. I do have physical access to the computer. I will check the firewall tomorrow.

---

### Post by Bucky Ball on 2013-04-07
*Thread moved to **Server Platforms**.*

Wait 24 hours before bumping. Thanks. ;)

---

### Post by BmanTheBoss on 2013-04-08
Haiee I got the server to work so nobody needs to comment on this anymore thanks for the help

---

### Post by Bucky Ball on 2013-04-08
Good news. Edit first post, click 'Go Advanced' and change the prefix [ubuntu] to [Solved]. Thanks.

---

