---
title: "cant get to ssh/22 from the outside"
date: 2007-08-15
forum: Server Platforms
---

### Post by mixersoft on 2007-08-15
I have a fresh install, ran apt-get ssh openssh-server, and can ssh to myself from the LAN. however, I can't access it from outside the network for remote administration.

My server is behind an ADSL modem and then a wifi router with port forwarding AND DMZ set and enabled to the ipaddress of the server. I ran nmap against port 22 of the router WAN ipaddress (x.x.x.x) and got this result,

from inside the network:

[COLOR="Blue"]Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-08-15 20:02 CST
Interesting ports on x.x.x.x:
PORT   STATE SERVICE
22/tcp open  ssh[/COLOR]

and from outside ( I ssh'ed to a remote server to run)

[COLOR="Red"]Starting Nmap 4.11 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-08-15 12:03 UTC
Interesting ports on x.x.x.x:
PORT   STATE    SERVICE
22/tcp filtered ssh[/COLOR]

This is the output from iptables -L
[COLOR="Blue"]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/COLOR]  


Am I doing something blatantly wrong here, or is my port 22 being block outside my scope? If the latter, can I switch ssh to a different port??

TIA.

---

### Post by shad0w_walker on 2007-08-15
I'm afraid to say its quite likely that your ISP is doing the filtering. Alot of ISPs run through proxies or other firewalls and block all the common server ports, especially ones that offers web hosting packages, etc.

It might be an idea to give your ISP a call and see if this is the case and if they can change it (Doubtful but worth a try)

---

