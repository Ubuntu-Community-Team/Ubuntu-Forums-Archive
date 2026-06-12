---
title: "Accessing vmware server from the Internet"
date: 2009-10-23
forum: Server Platforms
---

### Post by iyoung on 2009-10-23
Hi all,

I have Vmware server 2.01 installed on Ubuntu Server 9.04. From our internal network all works as expected, I can access the console and virtual machines Ok. To allow access from the internet, I set up port forwarding on our router. I opened ports 902,903,8222 and 8333. Unfortunately I can't access the console and therefore virtual machines from the internet. 

I've set up a laptop to packet sniff the connection between the router and the Vmware server host and I can see packets being sent to the server but no responses. It only responds to requests from it's own network. 'ufw status' gives a status of inactive and 'iptables -L' gives three empty chains with policies of ACCEPT. From this I conclude I have no firewall running on the server.

How can I make this setup respond to packets from any network? 

Thanks in advance

Ian

---

### Post by openfly on 2009-10-23
Two ghetto work arounds...

1.  openvpn.
2.  tunneling to the system via remote x or vnc.

---

