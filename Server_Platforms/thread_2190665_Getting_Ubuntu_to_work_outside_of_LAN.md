---
title: "Getting Ubuntu to work outside of LAN"
date: 2013-11-28
forum: Server Platforms
---

### Post by diamonw757 on 2013-11-28
I have just started setting up an Ubuntu server using Virtual Box and I am now running into an issue where I can ping my server(from the domain i set up and the ip address) from within my lan but not outside of it. I have read that this is likely a firewall or port issue and I have tried almost everything that I have found while browsing around. I am using a bridged adapter in virtualbox if that makes any difference. So I guess my real question is, how do i get the address of my server which is a 192.168.1.xxx address to resolve to my public ip? I have also noticed that I can't ping my local machine that the VM is on through the private IP outside of my home network either, so there is obviously something that I don't understand about this whole process in general. I apologize for being a networking newbie in advance. Any help at all is appreciated. If you need to see any of my files specifically let me know and I will post them.

---

### Post by Bucky Ball on 2013-11-28
*Thread moved to **Server Platforms**.*

Welcome. You might have more luck here.

---

### Post by pbrane on 2013-11-28
You need to port forward what ever port your server is listening on. If it's an http or web server port 80 should be forwarded in your router. Also 192.168.x.x addresses are not publicly route-able, so you would need to use the public IP to ping or access the server. By default all ports are closed to incoming WAN traffic on most routers. You should have a static IP assigned to the computer running your server. But you can use the DHCP address to test. I'm not sure about how to handle the IP in a VM though. Probably the IP of the host machine.

And of course the router I'm talking about port forwarding on is your internet router. Some router can block anonymous WAN requests (ping, etc). So check to see if that is enabled. If you post the type of router you have someone can help you if you need it.

---

