---
title: "Best method for routing multiple external static IP's"
date: 2010-12-16
forum: Security
---

### Post by R.Bucky on 2010-12-16
I have a block of 5 static ip's and 2 servers that push HTTP and other services. What is the best method of configuring/routing traffic to individual boxes on the network? 

More detail: One of my static IP's is assigned to a dedicated box for an Ubuntu mirror. Another static IP is assigned to a server with all of the HTTP traffic. 

Several configurations function to route traffic appropriately (forwarding proxy or 1-to-1 NAT). However, with 1-to-1 NAT, the box is left open to the world with only the software firewall. Do I really need to place a hardware firewall inline to EVERY server? 

Or, what other methods of routing and firewall would you recommend?

---

### Post by crashed111 on 2010-12-16
If you put a single Linux server in front of the other two you could set it up as a Firewall and run SNORT etc on it. 

You can then use iptables to forward individual ports to a server behind the firewall. If you make that firewall hold all 5 IPs you can then make the forwarding decisions based on IP and Port. 

This way only the port that you want will be forwarded to the systems behind the firewall and they will not be left totally exposed. 

IPTables is still a "Software" firewall but I have found it as good as any hardware firewall.

---

### Post by bodhi.zazen on 2010-12-16
> **R.Bucky said:**
> I have a block of 5 static ip's and 2 servers that push HTTP and other services. What is the best method of configuring/routing traffic to individual boxes on the network? 

More detail: One of my static IP's is assigned to a dedicated box for an Ubuntu mirror. Another static IP is assigned to a server with all of the HTTP traffic. 

Several configurations function to route traffic appropriately (forwarding proxy or 1-to-1 NAT). However, with 1-to-1 NAT, the box is left open to the world with only the software firewall. Do I really need to place a hardware firewall inline to EVERY server? 

Or, what other methods of routing and firewall would you recommend?

Either learn to set up a router (which is difficult and has the problems you cite) or if all you are doing is serving http content, use nginx (or apache) as a reverse proxy.

Other options are to consolidate your web servers (use virtual hosting) or perhaps a load ballancer depending on your needs.

---

### Post by R.Bucky on 2010-12-17
Got it figured out. Configured 1-to-1 NAT for my Ubuntu mirror with software firewall and other precautions and using port forwarding to my primary HTTP box. Works like a charm. If I end up installing another server on my network, I will need to invest in a Watchguard firewall or something similar. 

Thank you for the responses.

---

