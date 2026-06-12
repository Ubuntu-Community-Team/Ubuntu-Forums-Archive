---
title: "Requirements of Network, static ip, Spark &amp; OpenFire, Evolution Mail Server"
date: 2010-05-10
forum: Server Platforms
---

### Post by DaveVentresca on 2010-05-10
Ok
  I'm a server n00b, setting up an ubuntu server for the first time. I've read a few tutorials and they all say to use a static ip for the server, which i understand...but have a few questions. 

How do you choose a static ip for your server? 

When editing the /etc/network/interfaces file, all the instructions say is "Change the address,              netmask, and gateway              values to meet the requirements of your network." How do you figure out what the requirements of your network are? 

I want to use Evolution as the mail server and OpenFire/Spark as an IM client.

I'm setting up this server for a friends business and just want to get it working. Those are the only two functions it needs to have for the moment (Spark & Evolution), please help!
  -Dave

---

### Post by cdenley on 2010-05-10
> **DaveVentresca said:**
> How do you figure out what the requirements of your network are? 


That depends on your router. Generally, for home networks, you connect to the router using a web interface to see what IP's it will assign. Your static IP must be on the same network as your router assigns to other systems, but it can't be the same IP that it might assign to another system. For Linksys routers, the router itself uses 192.168.1.1, and it assigns IP's in the range 192.168.1.100 - 192.168.1.254 with the subnet 255.255.255.0. This means for servers, you can assign any IP from 192.168.1.2 - 192.168.1.99. The gateway would be 192.168.1.1, and for DNS, you can usually allow your router to forward queries, so you can use 192.168.1.1.

---

### Post by DaveVentresca on 2010-05-18
Thanks,
  Think I've got that figured out.
  -Dave

---

