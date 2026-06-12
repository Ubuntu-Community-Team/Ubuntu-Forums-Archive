---
title: "New Ubuntu Server Install - Need VPN access to port 8080"
date: 2010-06-13
forum: Server Platforms
---

### Post by diego898 on 2010-06-13
Hello, there is a new server on the vpn we have here. I have installed liferay+tomcat and when I navigate to [http://localhost:8080/](http://localhost:8080/) I can see the welcome page. I need to be able to access the server from its static ip from within the vpn which is 192.168.X.X:8080. How can I accomplish this?

Thanks

---

### Post by spynappels on 2010-06-14
You need to give some more details.
What VPN are you using? In routed or bridged mode?
Can you access any other services on the server?
Have iptables been applied to the server?

---

### Post by xsandz on 2010-06-14
One thing is not clear to me. You have told that u r being able to see the welcome page of tomcat at localhost:8080 and that means the server is installed locally to your machine. But u have told that u hv to hv the access the server VPN through its static IP. So its not clear to me that for wat purpose do u need the access the server

One thing more that you cannot access a server through its private IP. u need to know its corresponding public IP if it resides in a different network. Because every incoming and outgoing traffic goes thrugh NAT (Network Address Translation Table) where the mapping takes place between private and public IP.

---

