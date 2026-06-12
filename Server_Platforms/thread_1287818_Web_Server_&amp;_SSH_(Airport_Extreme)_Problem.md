---
title: "Web Server &amp; SSH (Airport Extreme) Problem"
date: 2009-10-10
forum: Server Platforms
---

### Post by mobbbx on 2009-10-10
Hi,

I'm trying to setup a web server and SSH on my ubuntu server. My current network setup is:

internet --> Linksys BECMU10 (cable modem) --> airport extreme --> ubuntu server

However, i am unable to access the webpage and SSH from WAN.

What i've tried so far:
 [LIST]
port forward 80 and 22 on airport extreme via airport utility
[/LIST]
[LIST]
reserved a DHCP ip for ubuntu server (10.0.1.201) via airport utility
[/LIST]
[LIST]
enabled NAT Port Mapping Protocol
[/LIST]
[LIST]
nmap on ubuntu server (10.0.1.201) shows port 22, 80 and 3306 open
[/LIST]
[LIST]
nmap on Linksys BECMU10 (192.168.100.1) shows port 21 and 80 open
[/LIST]
[LIST]
nmap on airport extreme (10.0.1.1) does not show port 22 and 80 open even though i've setup port forward for 22  and 80
[/LIST]

Since what i've done did not allow me to access the webserver from WAN, i changed my network setup to:
Internet --> Linksys BECMU10 --> ubuntu server
 
After the new setup, nmap on BECMU10 shows port 80 open and ubuntu shows that port 22, 80 and 3306 open. However, i still cannot access and SSH ubuntu server from WAN. 

Any help is greatly appreciated!

---

