---
title: "iptables port forwarding on host not executed for vm guest access via NAT"
date: 2010-11-09
forum: Virtualisation
---

### Post by ecp on 2010-11-09
Hi,

i have the following setup: An Ubuntu 10.04 server is running an apache webserver and several virtualbox guests. For various reasons the webserver listens on port 8081 and a port forward using iptables is used to bring the service to port 80. For any external clients accessing the server this setup works correctly.

However when I try to access the web services from a virtualbox guest (e.g.  Ubuntu Desktop) i can't get access to the host's services. However if the web server is configured to listen to port 80 everything works right - so it seems that the iptables port forwarding is not setup properly to be engaged by guests accessing the host service via NAT. My actual iptables-command for port-forwarding looks like this:

 ** iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 80 -j REDIRECT --to-port 8081**

Neither removing "-i eth0" nor adding another command with "-i lo" does help. Is there a way to also use iptables for this or can this be done only with the VirtualBox internal port forwarding mechanism (so this would be have to be configured for each guest machine separately). Any ideas?

By the way: With the actual forwarding rule i have to open port 80 and 8081 to public - is there a way to just open 8081 if the request has been send through port 80 ?

---

