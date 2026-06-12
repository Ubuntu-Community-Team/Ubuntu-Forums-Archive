---
title: "The internet went out last night due to a faulty power supply on the main line."
date: 2010-03-17
forum: Server Platforms
---

### Post by waloshin on 2010-03-17
So now that it's working the Server can't be seen from the internet. I see that the router changed all the ip address so I changed the fort port forwarding on the router and still not working. 

And the external ip address has not changed.

So what happened and how to fix it. 

Ubuntu Server 9.10

---

### Post by KB1JWQ on 2010-03-17
From another machine on the network, can you hit the proper port on the server's internal IP?  If so, the port forward isn't doing what you think it's doing, or your external IP has changed.  If not, then the service is likely not listening, or the server isn't at the IP you think it is.

---

### Post by waloshin on 2010-03-17
In my routers DHCP Client List my laptop is the only one listed not my sevrer.

There is nothing wrong with the cable as on the servers end you can see the green and orange lights blinking at the ethernet cable. 

So what would cause this?

^

---

### Post by KB1JWQ on 2010-03-18
A link light doesn't mean it's having the DHCP conversation correctly.

Does the server think it's getting an IP?  Is one statically coded?  

Time for basic troubleshooting!

Paste the output of ifconfig on the server.

---

### Post by waloshin on 2010-03-18
> **KB1JWQ said:**
> A link light doesn't mean it's having the DHCP conversation correctly.

Does the server think it's getting an IP?  Is one statically coded?  

Time for basic troubleshooting!

Paste the output of ifconfig on the server.

Wow I feel like an Idiot, the machine is headless so I guess it was stuck on the grub boot loader. 
:rolleyes:

---

