---
title: "DNS Server is not accessable from out side local network"
date: 2010-12-13
forum: Server Platforms
---

### Post by cbarron on 2010-12-13
I can access my dns server from the local network via ssh....but I can not from outside the local. Did I miss something? Any help would be great.

---

### Post by msandoy on 2010-12-13
You need to forward the correct ports from your router to the DNS server IP. It seems your server already has the correct ports open.

---

### Post by cbarron on 2010-12-13
yeah the ports are forwarded correctly as best I can tell......the dns server is not "inservice" yet it is just attached to the network for setup....I get a connection refused when trying to access it from outside the local network

---

### Post by msandoy on 2010-12-13
Make sure port 53 in the router is enabled for both UDP and TCP, and pointing to your DNS server. You need both.

---

### Post by James78 on 2010-12-14
Also, if your DNS server is acccessible from the outside, make sure it's properly secured. Wouldn't want to allow people to piggyback off of your server and use it for attacks too right?
[http://www.cymru.com/Documents/secure-bind-template.html](http://www.cymru.com/Documents/secure-bind-template.html)

---

### Post by chrislynch8 on 2010-12-14
Make sure ssh is listening on the external IP address of the DNS server if it is connected directly to the Internet, or that you have port forwarding setup if your DNS server is behind a router/firewall.

Rgds
Chris

---

### Post by windependence on 2010-12-14
Explain why you would need your internal DNS server open to the world, or even why you think you need a DNS server at all?
 
-Tim

---

### Post by cbarron on 2010-12-14
well the dns is a venture more than a necessity. as far as having it open to the whole world that will only be temporary....as I said it is not "in service" yet as a server. Someone I know who is more profficient at dns than I am wants to set it up ....thats why the temporary access to the outside world

---

### Post by cbarron on 2010-12-15
bump

---

### Post by msandoy on 2010-12-15
Since the server is not yet "in service", how are you trying to connect to it? Are you trying to connect with SSH? Remember, SSH uses port 22 by default, DNS uses 53.
Just to get some more info, please do a nmap inside the local network, on the server IP, and do a nmap on your external IP.

---

### Post by cbarron on 2010-12-16
After some more digging I found that the router had not "taken" the port opening I had given it. After a power cycle its all good

Thanks for the help all

---

