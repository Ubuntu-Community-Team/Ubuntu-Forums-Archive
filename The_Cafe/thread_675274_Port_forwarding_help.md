---
title: "Port forwarding help"
date: 2008-01-22
forum: The Cafe
---

### Post by jgrabham on 2008-01-22
OK, I just set up citadel on an old PC, and going off a network PC 10.0.0.12:8504 works fine.  It is behind an ADSL modem router  The problem is that going Internet_IP:8504 gives a firefox no server page.  

The forwarding table in my router says 

ID 	Ext. Port 	Private Port 	Port Type 	Host IP Address 	
1 	80 	~ 	80 	8504 	TCP 	10.0.0.12 	
2 	8504 	~ 	8504 	8504 	TCP 	10.0.0.12 	
3 	443 	~ 	443 	8504 	TCP 	10.0.0.12

(Internet_IP:80 gives me the routers web interface, just as 10.0.0.2 does)

Whats going wrong, why cant I connect via the internet?

---

