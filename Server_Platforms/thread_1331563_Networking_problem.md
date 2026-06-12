---
title: "Networking problem"
date: 2009-11-19
forum: Server Platforms
---

### Post by John_Needs_help on 2009-11-19
Hi,
 
I have just installed the Ubuntu server and I am having difficulty accessing the internet. This is my first time working with Linux.
 
My server has two network cards. Both static.
192.168.42.4 lan
192.168.1.100 wan (connected to the dsl router). 
 
The router address is 192.168.1.254 and this is setup as the gateway address for the network card 192.168.1.100. The external ip address is 89.242.9.243.
 
I can ping the router ip address and the external ip address from the server. I can also ping the server from the LAN computers. I cannot ping [www.google.com]("http://www.google.com"). 
 
It comes back with "unknown host".
 
What is wrong? Why will it not work?
 
Do I have to set up a dns? If so where and how?
 
Thanks,
 
John.

---

### Post by karlson on 2009-11-19
> **John_Needs_help said:**
> Hi,
 
I have just installed the Ubuntu server and I am having difficulty accessing the internet. This is my first time working with Linux.
 
My server has two network cards. Both static.
192.168.42.4 lan
192.168.1.100 wan (connected to the dsl router). 
 
The router address is 192.168.1.254 and this is setup as the gateway address for the network card 192.168.1.100. The external ip address is 89.242.9.243.
 
I can ping the router ip address and the external ip address from the server. I can also ping the server from the LAN computers. I cannot ping [www.google.com]("http://www.google.com"). 
 
It comes back with "unknown host".
 
What is wrong? Why will it not work?
 
Do I have to set up a dns? If so where and how?
 
Thanks,
 
John.

What is your default gateway and /etc/resolv.conf?

Please post output of 
```

netstat -rn

```

---

### Post by John_Needs_help on 2009-11-19
Karlson,
 
Thanks for the help.  I had a look at the /etc/resolv.conf settings.  I thought I had set them up as nameserver 89.242.9.243.  When I checked them again, there was nothing there.  I keyed nameserver 89.242.9.243 back in and reloaded and I am now working.  
 
Thanks,
 
John.

---

