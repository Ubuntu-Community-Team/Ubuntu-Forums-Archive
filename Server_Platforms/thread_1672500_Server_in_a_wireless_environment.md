---
title: "Server in a wireless environment?"
date: 2011-01-20
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-20
Ok,
I'm setting up my first home server and I have a few questions. My entire house is wireless. I have 3 computers, 1 PS3, and 1 Android Phone. That's 5 devices, ALL of which use WiFi. 

Here is how I want to set up my network (I understand this isn't a technical diagram):

Internet >> Server >> Wireless router >> 5 Devices. 

My goals are to proxy all internet traffic through the server AND use it as a shared file server. 

Will this work? 

Also, my server only has one LAN input and no LAN outs. How do I work with this?

---

### Post by Bucky Ball on 2011-01-21
Internet >> Modem >> Wireless router >> Server (cable from router) + 5 Devices (wireless connection to router).

Ethernet cable to server, all wireless devices as they were (or are). Static IPs would be best in this situation as you can identify machines easily and accurately when using NFS or SSH.

---

### Post by Ranger_Joe on 2011-01-21
Thanks! My question is this:

Is this safer than connecting my server directly to the internet to proxy all my traffic?

---

### Post by Bucky Ball on 2011-01-21
You could probably do that through the router config. BTW: LTS releases recommended for production machines (like servers). Long term support (10.04 LTS = 5 years) and more suited for this purpose. ;)

---

### Post by hawk2010 on 2011-01-21
Well. If you only have one Ethernet interface you can use that to connect to the internet the other on Wireless I'm assuming your using DSL. and using portforwarding ? Then since the server is behind a NAT you will be safe and also you will only be forwarding the ports required. YOu can run squid on the server for the proxy purposes.

---

### Post by Ranger_Joe on 2011-01-21
Ok... this all sounds very good but very advanced for my skill set. First off, I need to get 10.04 installed on this thing. I'll check back in when I've got that done and you guys can help me with the rest.

The help is much appreciated!

---

